---
title: AudioCodes SBC PowerShell REST API
date: 2022-11-21 10:25:00 +/-0800
categories: [Audiocodes, SBC, Microsoft, Powershell]
tags: [microsoft,audiocodes,sbc,powershell]
---

# AudioCodes SBC PowerShell REST API

If you are using an Audiocodes SBC and you have a dynamic IP Address, you need to change the NAT Address from time to time. As for Voice with MS Teams Direct Routing the correct IP Address is important.

Here is a little script I wrote to see if your public IP address is different from the one configured and if so it will change it via REST API.

```powershell
$LF = "`r`n";

# AudioCodes SBC Data
$ip = "SBC IP Address"
$username = "<Username>"
$password = "<Passwort>"

# NAT Settings
$srcPortStart = "<Src Port Start>"
$srcPortEnd = "<Src Port Start>"

# Get Public IP
$mypublicip = (Invoke-WebRequest -uri "http://ifconfig.me/ip").Content

# Build CLI Incremental String
$cliData =  "configure network$LF nat-translation 0$LF src-interface-name `"IF-WAN`"$LF target-ip-address `"$mypublicip`"$LF src-start-port `"$srcPortStart`"$LF src-end-port `"$srcPortEnd`"$LF activate"

# CLI URL
$URLFull = "http://{0}/api/v1/files/cliScript" ` -f $ip
$URLIncremental = "http://{0}/api/v1/files/cliScript/incremental" ` -f $ip

# REST API Authentication
$authHash = [Convert]::ToBase64String( ` [Text.Encoding]::ASCII.GetBytes( ` ("{0}:{1}" -f $username,$password)))

# INI File Body
$boundary = [System.Guid]::NewGuid().ToString(); 
$bodyLines = (
    "--$boundary",
("Content-Disposition: form-data; name=`"file`";" + `
" filename=`"file.txt`""),
"Content-Type: application/octet-stream$LF", $cliData,
"--$boundary--$LF"
) -join $LF

# Get Full INI File
$response = Invoke-RestMethod -Uri $URLFull -Method Get ` -Headers @{Authorization=("Basic {0}" -f $authHash)} ` 
#$response

# Get target-ip-address
$targetIPString = ($response  |  Select-String -Pattern "target-ip-address `"\d{1,3}(\.\d{1,3}){3}`"" -AllMatches).Matches.Value

# Check and Set New Public IP
if($targetIPString) {
    $targetIP = ($targetIPString  |  Select-String -Pattern "\d{1,3}(\.\d{1,3}){3}" -AllMatches).Matches.Value
    if($targetIPString -ne $mypublicip) {
        $changeIP = Invoke-RestMethod -Uri $URLIncremental -Method Put ` -Headers @{Authorization=("Basic {0}" -f $authHash)} ` -ContentType "multipart/form-data; boundary=$boundary" ` -Body $bodyLines
        $changeIP | ConvertTo-Json
    }
} 
```