---
title: AudioCodes SBC Telekom Magenta
date: 2022-11-22 10:25:00 +/-0800
categories: [Audiocodes, SBC, Telekom]
tags: [audiocodes,sbc,telekom]
---

# AudioCodes SBC Telekom Magenta

Navigate to your SBC Login Page. Login and switch to **Signaling & Media**

## Proxy Set

Click **Proxy Sets**

![](/assets/img/2022-11-21-14-02-31.png)

Click **+ New** to create a new Proxy Set

![](/assets/img/2022-11-21-14-04-07.png)

Give the new **Proxy Set** a name; e.g. **PS_Telekom**

![](/assets/img/2022-11-21-14-04-24.png)

Click **SBC IPv4 SIP Interface**

![](/assets/img/2022-11-21-14-04-47.png)

Choose your SIP Interface e.g. **#0 [SIPInterface_0]**

![](/assets/img/2022-11-21-14-05-02.png)

On **Redundancy Mode** choose **Homing**

![](/assets/img/2022-11-21-14-05-31.png)

Enable **Proxy Hot Swap**

![](/assets/img/2022-11-21-14-05-42.png)

Below choose **SRV** for the **DNS Resolve Method**

![](/assets/img/2022-11-21-14-05-57.png)

Click **APPLY**

![](/assets/img/2022-11-21-14-06-09.png)

With the newly created Proxy Set selected, click on **Proxy Address 0 items**

![](/assets/img/2022-11-21-14-06-54.png)

Click **+ New** to add a new Proxy Address

![](/assets/img/2022-11-21-14-07-05.png)

In the **Proxy Address** text field add **tel.t-online.de**

![](/assets/img/2022-11-21-14-07-22.png)

For the **Transport Type** choose **UDP**

![](/assets/img/2022-11-21-14-07-33.png)

Click **APPLY**

![](/assets/img/2022-11-21-14-07-44.png)

## IP Profile

In **CODERS & PROFILES** click on **IP Profiles**

![](/assets/img/2022-11-21-14-09-54.png)

Click **+ New** to add a new IP Profile

![](/assets/img/2022-11-21-14-10-07.png)

Give the IP Profile a name; e.g. **IPP-Telekom**

![](/assets/img/2022-11-21-14-10-19.png)

Change the settings as in the table below and leave the rest as default.

|               |              |
|--------------|-----------:|
|SBC Media Security Mode|Not Secured|
|Remote Multiple 18x|Not Supported|
|Remote Early Media Response Type|183|
|Remote Early Media RTP Detection Mode|By Media|
|Signaling DiffServ|48|
|Remote REFER Mode|Handle Locally|

Click **APPLY**

![](/assets/img/2022-11-21-14-10-50.png)

## IP Group

Under **CORE ENTITIES** choose **IP Groups**

![](/assets/img/2022-11-21-14-11-11.png)

Click **+ New** to add a new **IP Group**

![](/assets/img/2022-11-21-14-11-25.png)

Give the IP Profile a name; e.g. **IPG-Telekom**

![](/assets/img/2022-11-21-14-11-38.png)

[OPTIONAL] Change the **Topology Location** to **Up**

![](/assets/img/2022-11-21-14-11-48.png)

Choose the **Proxy Set** we created before; e.g. **PS_Telekom**

![](/assets/img/2022-11-21-14-12-00.png)

![](/assets/img/2022-11-21-14-12-07.png)

Unter IP Profile choose the newly created IP Profile; e.g. **IPP-Telekom**

![](/assets/img/2022-11-21-14-12-22.png)

![](/assets/img/2022-11-21-14-12-29.png)

For the **Media Realm** choose the **DefaultRealm**; If you added a separated one, choose this one.

![](/assets/img/2022-11-21-14-12-39.png)

![](/assets/img/2022-11-21-14-12-45.png)

In the SIP Group Name text field add **tel.t-online.de**

![](/assets/img/2022-11-21-14-12-55.png)

For Inbound Message Manipulation Set add 1

![](/assets/img/2022-11-21-14-13-06.png)

For Outbound Message Manipulation Set add 2

![](/assets/img/2022-11-21-14-13-16.png)

Click **APPLY**

![](/assets/img/2022-11-21-14-13-28.png)

## Accounts

Under **SIP DEFINITIONS** click on **Accounts**

![](/assets/img/2022-11-21-14-15-05.png)

Click **+ New** to add a new Account

![](/assets/img/2022-11-21-14-15-15.png)

Give the new account a name.

![](/assets/img/2022-11-21-14-15-25.png)

As **Served IP Group** choose the one we created; e.g. **IPG_Telekom**

![](/assets/img/2022-11-21-14-15-35.png)

![](/assets/img/2022-11-21-14-15-42.png)

As **Serving IP Group** choose the one we created; e.g. **IPG_Telekom**

![](/assets/img/2022-11-21-14-15-57.png)

![](/assets/img/2022-11-21-14-16-08.png)

In the **Host Name** text field enter **tel.t-online.de**

![](/assets/img/2022-11-21-14-16-19.png)

In the **Contact User** text field enter your E.164 phone number and choose under **Register** **Regular**

![](/assets/img/2022-11-21-14-16-33.png)

Under **User Name** and **Password** enter your Telekom credentials.

![](/assets/img/2022-11-21-14-16-44.png)

Click **APPLY**

![](/assets/img/2022-11-21-14-16-59.png)

## Message Manipulation

Under **MESSAGE MANIPULATION** click on **Message Manipulations**

![](/assets/img/2022-11-21-14-17-22.png)

Click **+ New** to add a new Message Manipulation

![](/assets/img/2022-11-21-14-17-39.png)

In the Name text field enter **check if first PAI is a number**

![](/assets/img/2022-11-21-14-17-52.png)

If you want to user the **Editor** click on it. Follow the below table and add the needed Message Manipulations.

![](/assets/img/2022-11-21-14-18-02.png)

## List of Message Manipulation

|ID|Name|Manipulation Set ID|Message Type|Condition|Action Subject|Action Type|Action Value|Row Role|
|---|---|---|---|---|---|---|---|---|
|0|check if first PAI is a number|2|Any.Request|Header.P-Asserted-Identity.0 !contains '+49'|Header.P-Asserted-Identity.0|Remove||Use Current Condition|
|1|check if first PAI is a number|2|Any.Request|header.p-asserted-identity.1 !contains '+49'|header.p-asserted-identity.1|Remove||Use Current Condition|
|2|rewrite PAI a sip-uri|2|Any.Request|header.p-asserted-identity.URL.Type == '2'|header.p-asserted-identity.url|Modifiy|'sip:'+Header.P-Asserted-Identity.URL.User+'@tel.t-online.de'|Use Current Condition|
|3|Add P-Early-Media|2|Any.Request||Header.P-Early-Media|Add|'supported'|Use Current Condition|
|4|from trunk domain|2|Any.Request||header.from.url.host|Modifiy|'tel.t-online.de'|Use Current Condition|
|5|restore original calling|2|Invite|header.x-orig-A exists|header.from.url.user|Modifiy|header.x-orig-A|Use Current Condition|
|6|remove x-orig-A|2|||header.x-orig-A|Remove||Use Current Condition|
|7|Call Forward|2|Invite|Header.Diversion exists|Header.From.Url.User|Modifiy|Header.Diversion.Url.User|Use Current Condition|
|8|Call Forward|0|||Header.Diversion.Url.Host|Modifiy|Param.IPG.Dst.Host|Use Previous Condition|
|9|Call Transfer|2|Invite|Header.Referred-By exists|Header.From.Url.User|Modifiy|Header.Referred-By.Url.User|Use Current Condition|
|10|Call Transfer|2|||Header.Referred-By.Url.Host|Modifiy|Param.IPG.Dst.Host|Use Previous Condition|
|11|Reject Cause|2|Any.Response|Header.Request-Uri.MethodType=='480' OR Header.Request-Uri.MethodType=='503' OR Header.Request-Uri.MethodType=='603'|Header.Request-Uri.MethodType|Modifiy|'486'|Use Current Condition|
|12|Normalize Contact|2|Invite.Request||Header.Contact.URL|Normalize||Use Current Condition|
|13|Normalize SDP|2|Any.Request|Body.sdp exists|Body.sdp|Normalize||Use Current Condition|
|14|removeCrypto18x|2|Any.Response|Body.sdp regex '(.*)(\|2\^31)(.*)'|Body.sdp|Modifiy|$1+$3|Use Current Condition|
|15|Normalize Contact Header|2|Any.Request||Header.Contact|Normalize||Use Current Condition|

## INI File
```ini
[ IpProfile ]
FORMAT Index = ProfileName, IpPreference, CodersGroupName, IsFaxUsed, JitterBufMinDelay, JitterBufOptFactor, IPDiffServ, SigIPDiffServ, RTPRedundancyDepth, CNGmode, VxxTransportType, NSEMode, IsDTMFUsed, PlayRBTone2IP, EnableEarlyMedia, ProgressIndicator2IP, EnableEchoCanceller, CopyDest2RedirectNumber, MediaSecurityBehaviour, CallLimit, DisconnectOnBrokenConnection, FirstTxDtmfOption, SecondTxDtmfOption, RxDTMFOption, EnableHold, InputGain, VoiceVolume, AddIEInSetup, SBCExtensionCodersGroupName, MediaIPVersionPreference, TranscodingMode, SBCAllowedMediaTypes, SBCAllowedAudioCodersGroupName, SBCAllowedVideoCodersGroupName, SBCAllowedCodersMode, SBCMediaSecurityBehaviour, SBCCryptoGroupName, SBCRFC2833Behavior, SBCAlternativeDTMFMethod, SBCSendMultipleDTMFMethods, SBCReceiveMultipleDTMFMethods, SBCAssertIdentity, AMDSensitivityParameterSuit, AMDSensitivityLevel, AMDMaxGreetingTime, AMDMaxPostSilenceGreetingTime, SBCDiversionMode, SBCHistoryInfoMode, EnableQSIGTunneling, SBCFaxCodersGroupName, SBCFaxBehavior, SBCFaxOfferMode, SBCFaxAnswerMode, SbcPrackMode, SBCSessionExpiresMode, SBCRemoteUpdateSupport, SBCRemoteReinviteSupport, SBCRemoteDelayedOfferSupport, SBCRemoteReferBehavior, SBCRemote3xxBehavior, SBCRemoteMultiple18xSupport, SBCRemoteEarlyMediaResponseType, SBCRemoteEarlyMediaSupport, EnableSymmetricMKI, MKISize, SBCEnforceMKISize, SBCRemoteEarlyMediaRTP, SBCRemoteSupportsRFC3960, SBCRemoteCanPlayRingback, EnableEarly183, EarlyAnswerTimeout, SBC2833DTMFPayloadType, SBCUserRegistrationTime, ResetSRTPStateUponRekey, AmdMode, SBCReliableHeldToneSource, GenerateSRTPKeys, SBCPlayHeldTone, SBCRemoteHoldFormat, SBCRemoteReplacesBehavior, SBCSDPPtimeAnswer, SBCPreferredPTime, SBCUseSilenceSupp, SBCRTPRedundancyBehavior, SBCPlayRBTToTransferee, SBCRTCPMode, SBCJitterCompensation, SBCRemoteRenegotiateOnFaxDetection, JitterBufMaxDelay, SBCUserBehindUdpNATRegistrationTime, SBCUserBehindTcpNATRegistrationTime, SBCSDPHandleRTCPAttribute, SBCRemoveCryptoLifetimeInSDP, SBCIceMode, SBCRTCPMux, SBCMediaSecurityMethod, SBCHandleXDetect, SBCRTCPFeedback, SBCRemoteRepresentationMode, SBCKeepVIAHeaders, SBCKeepRoutingHeaders, SBCKeepUserAgentHeader, SBCRemoteMultipleEarlyDialogs, SBCRemoteMultipleAnswersMode, SBCDirectMediaTag, SBCAdaptRFC2833BWToVoiceCoderBW, CreatedByRoutingServer, UsedByRoutingServer, SBCFaxReroutingMode, SBCMaxCallDuration, SBCGenerateRTP, SBCISUPBodyHandling, SBCISUPVariant, SBCVoiceQualityEnhancement, SBCMaxOpusBW, SBCEnhancedPlc, LocalRingbackTone, LocalHeldTone, SBCGenerateNoOp, SBCRemoveUnKnownCrypto, SBCMultipleCoders, DataDiffServ, SBCMSRPReinviteUpdateSupport, SBCMSRPOfferSetupRole, SBCMSRPEmpMsg, SBCRenumberMID, SBCAllowOnlyNegotiatedPT, RTCPEncryption;
IpProfile 0 = "IPP-Telekom", 1, "AudioCodersGroups_0", 0, 10, 10, 46, 48, 0, 0, 2, 0, 0, 0, 0, -1, 1, 0, 0, -1, 1, 4, -1, 1, 1, 0, 0, "", "", 0, 0, "", "", "", 0, 2, "", 0, 0, 0, 0, 1, 0, 8, 300, 400, 1, 2, 0, "", 0, 0, 1, 3, 0, 2, 2, 1, 3, 0, 0, 2, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 2, 2, 1, 1, 0, 0, 300, -1, -1, 0, 0, 0, 0, 0, 0, 0, -1, -1, -1, -1, -1, 0, "", 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, -1, -1, 0, 0, 0, 0, 1, 2, 0, 0, 0, 2;
[ \IpProfile ]

[ ProxySet ]
FORMAT Index = ProxyName, EnableProxyKeepAlive, ProxyKeepAliveTime, ProxyLoadBalancingMethod, IsProxyHotSwap, SRDName, ClassificationInput, TLSContextName, ProxyRedundancyMode, DNSResolveMethod, KeepAliveFailureResp, GWIPv4SIPInterfaceName, SBCIPv4SIPInterfaceName, GWIPv6SIPInterfaceName, SBCIPv6SIPInterfaceName, MinActiveServersLB, SuccessDetectionRetries, SuccessDetectionInterval, FailureDetectionRetransmissions, AcceptDHCPProxyList;
ProxySet 1 = "PS_Telekom", 0, 60, 0, 1, "DefaultSRD", 0, "", 1, 1, "", "", "SIPInterface_0", "", "", 1, 1, 10, -1, 0;
[ \ProxySet ]

[ IPGroup ]
FORMAT Index = Type, Name, ProxySetName, VoiceAIConnector, SIPGroupName, ContactUser, SipReRoutingMode, AlwaysUseRouteTable, SRDName, MediaRealm, InternalMediaRealm, ClassifyByProxySet, ProfileName, MaxNumOfRegUsers, InboundManSet, OutboundManSet, RegistrationMode, AuthenticationMode, MethodList, SBCServerAuthType, OAuthHTTPService, EnableSBCClientForking, SourceUriInput, DestUriInput, ContactName, UsernameAsClient, PasswordAsClient, UsernameAsServer, PasswordAsServer, UUIFormat, QOEProfile, BWProfile, AlwaysUseSourceAddr, MsgManUserDef1, MsgManUserDef2, SIPConnect, SBCPSAPMode, DTLSContext, CreatedByRoutingServer, UsedByRoutingServer, SBCOperationMode, SBCRouteUsingRequestURIPort, SBCKeepOriginalCallID, TopologyLocation, SBCDialPlanName, CallSetupRulesSetId, TeamsRegistrationMode, Tags, SBCUserStickiness, UserUDPPortAssignment, AdmissionProfile, ProxyKeepAliveUsingIPG, SBCAltRouteReasonsSetName, TeamsLocalMediaOptimization, TeamsLocalMOInitialBehavior, SIPSourceHostName, TeamsDirectRoutingMode, TeamsLocalMOSite, UserVoiceQualityReport, ValidateSourceIP;
IPGroup 1 = 0, "IPG_Telekom", "PS_Telekom", "", "tel.t-online.de", "", -1, 0, "DefaultSRD", "DefaultRealm", "", 1, "IPP-Telekom", -1, 1, 2, 0, 0, "", -1, "", 0, -1, -1, "", "", "", "", "", 0, "", "", 0, "", "", 0, 0, "default", 0, 0, -1, 0, 0, 1, "", -1, 0, "", 0, 0, "", 0, "", 0, 0, "", 0, "", 0, 0;
[ \IPGroup ]

[ ProxyIp ]
FORMAT Index = ProxySetId, ProxyIpIndex, IpAddress, TransportType, Priority, Weight;
ProxyIp 0 = "1", 0, "tel.t-online.de", 0, 0, 0;
[ \ProxyIp ]

[ Account ]
FORMAT Index = AccountName, ServedTrunkGroup, ServedIPGroupName, ServingIPGroupName, Username, Password, HostName, ContactUser, Register, RegistrarStickiness, RegistrarSearchMode, RegEventPackageSubscription, ApplicationType, RegByServedIPG, UDPPortAssignment, ReRegisterOnInviteFailure, AcceptDHCPConfiguration;
Account 0 = "+4930123456789", -1, "IPG_Telekom", "IPG_Telekom", "email@t-online.de", "$1$0oKyp6ahuKq9", "tel.t-online.de", "+4930123456789", 1, 0, 0, 0, 2, 0, 0, 0, 0;
[ \Account ]

[ MessageManipulations ]
FORMAT Index = ManipulationName, ManSetID, MessageType, Condition, ActionSubject, ActionType, ActionValue, RowRole;
MessageManipulations 0 = "check if first PAI is a number", 2, "Any.Request", "Header.P-Asserted-Identity.0 !contains '+49'", "Header.P-Asserted-Identity.0", 1, "", 0;
MessageManipulations 1 = "check if first PAI is a number", 2, "Any.Request", "header.p-asserted-identity.1 !contains '+49'", "header.p-asserted-identity.1", 1, "", 0;
MessageManipulations 2 = "rewrite PAI a sip-uri", 2, "Any.Request", "header.p-asserted-identity.URL.Type == '2'", "header.p-asserted-identity.url", 2, "'sip:'+Header.P-Asserted-Identity.URL.User+'@tel.t-online.de'", 0;
MessageManipulations 3 = "Add P-Early-Media", 2, "Any.Request", "", "Header.P-Early-Media", 0, "'supported'", 0;
MessageManipulations 4 = "from trunk domain", 2, "Any.Request", "", "header.from.url.host", 2, "'tel.t-online.de'", 0;
MessageManipulations 5 = "restore original calling", 2, "Invite", "header.x-orig-A exists", "header.from.url.user", 2, "header.x-orig-A", 0;
MessageManipulations 6 = "remove x-orig-A", 2, "", "", "header.x-orig-A", 1, "", 0;
MessageManipulations 7 = "Call Forward", 2, "Invite", "Header.Diversion exists", "Header.From.Url.User", 2, "Header.Diversion.Url.User", 0;
MessageManipulations 8 = "Call Forward", 0, "", "", "Header.Diversion.Url.Host", 2, "Param.IPG.Dst.Host", 1;
MessageManipulations 9 = "Call Transfer", 2, "Invite", "Header.Referred-By exists", "Header.From.Url.User", 2, "Header.Referred-By.Url.User", 0;
MessageManipulations 10 = "Call Transfer", 2, "", "", "Header.Referred-By.Url.Host", 2, "Param.IPG.Dst.Host", 1;
MessageManipulations 11 = "Reject Cause", 2, "Any.Response", "Header.Request-Uri.MethodType=='480' OR Header.Request-Uri.MethodType=='503' OR Header.Request-Uri.MethodType=='603'", "Header.Request-Uri.MethodType", 2, "'486'", 0;
MessageManipulations 12 = "Normalize Contact", 2, "Invite.Request", "", "Header.Contact.URL", 7, "", 0;
MessageManipulations 13 = "Normalize SDP", 2, "Any.Request", "Body.sdp exists", "Body.sdp", 7, "", 0;
MessageManipulations 14 = "removeCrypto18x", 2, "Any.Response", "Body.sdp regex '(.*)(\|2\^31)(.*)'", "Body.sdp", 2, "$1+$3", 0;
MessageManipulations 15 = "Normalize Contact Header", 2, "Any.Request", "", "Header.Contact", 7, "", 0;
[ \MessageManipulations ]
```