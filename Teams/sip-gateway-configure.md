---
title: Configure SIP Gateway
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 09/30/2021
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
ms.reviewer: crowe
search.appverid: MET150
f1.keywords:
- NOCSH
- ms.teamsadmincenter.directrouting.overview
description: Learn how to configure SIP Gateway.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Configure SIP Gateway

This article explains how to configure SIP Gateway so that your organization can use compatible SIP phones with Microsoft Teams. Be sure to read [Plan for SIP Gateway](sip-gateway-plan.md) first.

## Enable SIP Gateway for your tenant

There are two ways you can enable SIP Gateway for your tenant: by using a PowerShell cmndlet, or in the Teams admin center.

### Enable SIP Gateway by using a PowerShell cmndlet

To enable SIP Gateway by using a PowerShell cmndlet, see [Set-CsTeamsCallingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/set-csteamscallingpolicy?view=skype-ps). [Do we need to explain what they need to do with this?]

### Enable SIP Gateway in the Teams admin center

To enable SIP Gateway in the Teams admin center, follow these steps:

1. Go to the [Teams admin center](https://admin-teams.microsoft.net/)

2. At the left, under **Voice**, select **Calling policies**.

3. At the right under **Manage policies**, select the appropriate calling policy assigned to users or, if necessary, create a new calling policy and assign it to the required users.

4. Select **Manage policies**, select a policy, and then select **Edit**.

5. Turn on the setting for **SIP devices can be used for calls**, and then select **Save**.

## Support a multi-language user interface

The IP phone user interface can display information in many languages. The language setting affects the phones interface, including softkeys and sign-in/sign-out system messages.

### Set the UI language

Setting the language is done in the provisioning server, using DHCP server, or manually by appending a code string in the URL as in the following examples.

How to set German for Polycom, AudioCodes, and Yealink phones:
- http://emea.ipp.sdg.teams.microsoft.com/lang_de

How to set Japanese for Cisco phones:
- http://emea.ipp.sdg.teams.microsoft.com/lang_ja/$PSN.xml 

#### Supported languages

|Language name|Language code]
|-------------|-------------|
|English (default)|en       |
|Spanish      |es           |
|Japanese     |ja           |
|German       |de           |
|French       |fr           |
|Portuguese   |pt           |

> [!Note]
> - Japanese is not supported by Yealink and partially supported by Polycom VVX.
> - The system defaults to English if the selected language is not supported by the SIP endpoint.
> - When the **lang_xx** parameter is not set via the provisioning URL, English is used as the default language.
> - If **Sign in to make an emergency call** text is not translated to other languages, an abbreviated version in English only will be presented on **Press Sign In** on the following IP phone models due to a screensize limitations:
>   - Poly VVX 150, VVX 201
>   - Cisco CP-6821, CP-7811, CP-7821, CP-7841, CP-7861
>   - Voice mail softkey label is hardcoded with **VM** text across all languages for Poly VVX because of a limitation of string length.


## Verify that SIP Gateway is available for your tenant

1. Log in to the [Teams admin center](https://admin-teams.microsoft.net/).

2. At the left, select **Teams devices** and see if the **SIP devices** tab is visible. If it is, the SIP Gateway service is enabled for your tenant.

## Reset each SIP phone to factory defaults

Each SIP device used with SIP Gateway must be reset to its factory default settings. Users should see the device manufacturer’s instructions to find out how.

## Configure SIP Gateway provisioning server for each SIP device

For each SIP device, configure the following SIP Gateway provisioning server URL: 
- EMEA: [http://emea.ipp.sdg.teams.microsoft.com](http://emea.ipp.sdg.teams.microsoft.com)
- Americas: [http://noam.ipp.sdg.teams.microsoft.com](http://noam.ipp.sdg.teams.microsoft.com)

> [!NOTE]
> - Only compatible SIP devices can be onboarded to SIP Gateway. Users who work from home must manually configure the provisioning server URL above into their SIP device. To do that, they must perform either of the following steps:
>   - Open a browser window, enter the device’s IP address, and configure the provisioning server’s URL. 
>   - Under **Settings** or **Advanced settings** on the device, set the provisioning server’s URL.
> - Cisco IP phones must be flashed to multiplatform firmware before they can be onboarded. Read this guide to learn how: [Cisco firmware conversion guide](https://www.cisco.com/c/en/us/products/collateral/collaboration-endpoints/unified-ip-phone-7800-series/guide-c07-742786.html)| 
> - Some Yealink models also require a license to migrate from Skype for Business firmware to SIP.

## Port requirements

Make sure the firewall on your network opens traffic to Office 365 and Teams as specified in [Office 365 URLs and IP address ranges](https://docs.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges). Also open UDP ports in the range 49152 to 53247 and TCP port 5061 for IP range 52.112.0.0/14 to 52.120.0.0/14.

## Enroll SIP devices

An administrator can provision SIP devices in the Teams admin center either individually, or in batches by uploading a csv file that contains a list of devices to be provisioned. To do that, follow these steps:

1. Log in to the [**Teams admin center**](https://admin.teams.microsoft.net/).

2. Select **Teams devices** > **SIP devices**.

3. At the upper right, select **Actions** > **Provision devices**.

4. Under **Waiting on activation**, do either of the following:

- To provision one device:

   a. Select the MAC address of a SIP device, and then select **Edit**.

   b. In the **Edit MAC addresses** pane under **MAC address**, enter the MAC address of the device, and then select **Apply**.

- To provision many devices at once:

    a. At the right, select **Export** (the Microsoft Excel icon). 

    b. In the downloaded csv file, enter the **MAC ID**, **Verification Code**, **Assigned**, and **Location**.

   c. Under **Waiting on Activation**, select **Upload**, select **Select a file**, and select the csv file.


Under **Waiting on activation** in the steps above, an administrator can select **Generate verification code** to generate a one-time verification code for each onboarded device. An administrator can enroll that onboarded device by dialing a feature code followed by the verification code. For example, if the feature code for enrollment is *55*, and the verification code is *123456*, the administrator would dial *5512345* to enroll the device. Once the device is successfully enrolled, it shows up in the Teams admin center inventory and is enabled for remote sign-in. **(Please walk me through these steps so I can describe them better.)**

> [!NOTE]
> A SIP device must be onboarded before it can be enrolled.

## Remote sign-in

**TBD**

## Pair a device and sign in through a web authorization app

To pair a SIP phone after the user authenticates his or her corporate credentials, the user must:

1. Press **Sign-in** on the SIP phone to display the authorization URL and pairing code [**Is this the one-time verification code that we discuss above?**]. The pairing code is time-sensitive. If it expires, the user must press **Back** on the phone and start the sign-in process again.

2. Navigate to the authorization URL on the user's desktop or mobile browser and use corporate credentials to log in.

3. Enter the pairing code displayed on the SIP phone into the web authorization app to pair the SIP phone with the user's account. On a successful sign-in, which might take a while, the SIP phone will display the phone number and username if the device supports that. 

> [!NOTE]
> The location of the device shown on the Azure Active Directory web authorization app is the SIP Gateway datacenter to which the device is connected. SIP phones in scope are not OAuth-capable, so SIP Gateway authenticates the user through the web authorization app and then pairs the device with the user’s credentials. Learn more here: [Microsoft identity platform and the OAuth 2.0 device authorization grant flow](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-device-code).

## Sign out

To sign out, a user can:

- Press **Sign-Out** on the SIP phone and follow the steps described on the SIP phone. Only manual sign-in and sign-out are supported.

To sign out a device remotely on the Teams admin center, an administrator can:

1. Log in to the [**Teams admin center**](https://admin.teams.microsoft.net/).

2. Select **Teams devices** > **SIP devices**.

3. At the right, select the device, and then select **Sign out**. **(Is that right? I can't see it in the UI because I don't have any devices on my test page.)**

## Other considerations

SIP Gateway authenticates SIP Phones with Azure Active Directory, so if your tenant uses conditional access for devices in the corporate network, then it should exclude the following IP addresses: 
- North America:
    - East US: 52.170.38.140
    - West US: 40.112.144.212
-   EMEA region:
    - North EU: 40.112.71.149
    - North EU: 40.112.71.149
    - West EU: 40.113.112.67
-   APAC region:
    - APAC cluster 1: <IP address>
    - APAC cluster 2: <IP address>

For more information, see [IP address ranges](https://docs.microsoft.com/en-in/azure/active-directory/conditional-access/location-condition#ip-address-ranges)

## View and monitor your SIP devices

Teams administrators can view and monitor their SIP device inventory in the Teams admin center after the devices' users sign in at least once. Here's how:

1. Log in to the [Teams admin center](https://admin-teams.microsoft.net/).

2. Select **Teams devices** > **SIP devices**. All signed-in SIP devices are listed on the right.

## Sync policy changes to SIP devices to enforce policies

User details and policies will be fetched to SIP devices when users sign in. Any policy changes thereafter for signed-in users will be synced to the device within one hour. Sync will be triggered with registration refresh. [What does this mean?]

## Restart a SIP device

1. Log in to the [Teams admin center](https://admin-teams.microsoft.net/).

2. Select **Teams devices** > **SIP devices**. 

3. On the right, select the SIP device that you want to restart, and then select **Restart**.

## Report problems to Microsoft

- To report problems, contact [Microsoft Support](https://support.microsoft.com)