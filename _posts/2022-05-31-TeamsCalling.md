---
title: Avaya Calling for MS Teams
date: 2022-05-31 08:00:00 +/-0800
categories: [Avaya, Microsoft]
tags: [avaya,microsoft,teams,workplace]
---

# Avaya Calling for MS Teams

## Configuration in Avaya Spaces

To use Avaya Calling for MS Teams you first need an Avaya Spaces Account. Therefore a admin should add the company under **Manage Companies** at https://accounts.avayacloud.com.

![](/assets/img/2022-05-31-08-33-15.png)

Under the tab **Domains** you have to add and verify your company domain.

![](/assets/img/2022-05-31-08-33-42.png)

> 1. The domain has to be the same used as the Microsoft 365 domain.
> 2.	The domain must be verified with a TXT entry on company DNS where the domain is registered.
{: .prompt-warning }

Next on the tab **Apps** you need to add a new App called **Avaya Calling for Teams**.

![](/assets/img/2022-05-31-08-35-03.png)

In the **Public Settings** you need to enter the **public available** AADS server.

![](/assets/img/2022-05-31-08-35-15.png)

```json
{
  "Client_Settings_File_Address": [
    {
      "Profile_Name": "Production",
      "Client_Settings_File_Url": "https://<AADS-FQDN>/acs/resources/configurations"
    }
  ]
}
```

## MS Teams Admin Center

The Avaya Calling App need access to the Office 365 contacts. Therefore a MS Teams admin needs to upload the Avaya Calling Manifest File to **Teams apps > Manage apps** (**Upload**).

![](/assets/img/2022-05-31-08-36-33.png)

![](/assets/img/2022-05-31-08-36-40.png)

After uploading the App is available to all MS Teams users in the company.

Next you need to give the Avaya Calling App permissions to read the contacts. Under the App the admin needs to change to **Permissions** by clicking on **Review Permissions**.

![](/assets/img/2022-05-31-08-36-57.png)

In the upcoming PopUp Window, you will see the permissions needed and you need to click **Accept** to grant those permissions to the Avaya Calling App.

![](/assets/img/2022-05-31-08-37-08.png)

## MS Teams

In MS Teams you can add the Avaya Calling App by clicking on **More Apps**, find the Avaya Call app and click on **Add**.

![](/assets/img/2022-05-31-08-37-24.png)

![](/assets/img/2022-05-31-08-37-32.png)

After the app is added, you can open the app on the side bar and a Avaya Call login window will appear. Here you need to enter the login credentials for you AADS server.

![](/assets/img/2022-05-31-08-37-41.png)

Is the login successful, the user has accesss to the contacts and favorites added to the Workplace Client.

![](/assets/img/2022-05-31-08-37-52.png)

![](/assets/img/2022-05-31-08-37-57.png)

You can make a call while clicking on the Phone or Video icon. Here the installed Workplace Client should open and starts dialing.
When you click on the chat icon a new chat in MS Teams will start.

The user has also access to the Office 365 contacts and they can be called in the same way like the Avaya contacts.

![](/assets/img/2022-05-31-08-38-15.png)