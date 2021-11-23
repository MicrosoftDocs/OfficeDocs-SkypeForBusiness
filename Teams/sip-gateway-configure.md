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

This article explains how to configure SIP Gateway so that your organization can use compatible SIP devices with Microsoft Teams. To find out what SIP Gateway can do for your organization and what hardware, software, and licenses are required for it, read [Plan for SIP Gateway](sip-gateway-plan.md).

Before you can configure SIP Gateway, do the following:

- **Reset SIP devices to factory default settings.** You or your users must reset each SIP device used with SIP Gateway to its factory default settings. To find out how to do that, see the manufacturer’s instructions.

- **Open your firewall to Microsoft 365 and Teams.** Open your network's firewall to Microsoft 365 and Teams traffic as described in [Office 365 URLs and IP address ranges](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges).

- **Make sure the SIP devices are not behind a proxy.** Ensure that http/s traffic bypasses any corporate http proxy.

- **Open the UDP ports.** You must also open the UDP ports in the range 49152 to 53247 and TCP port 5061 for IP range 52.112.0.0/14 to 52.120.0.0/14.

The following sections describe the tasks that you must perform as an administrator to configure SIP Gateway.

1. [Verify that SIP Gateway is available for your organization](#verify-that-sip-gateway-is-available-for-your-tenant).

2. [Enable SIP Gateway for the users in your organization](#enable-sip-gateway-for-the-users-in-your-tenant).

3. [Set the SIP Gateway provisioning server URL](#for-each-sip-device-set-the-sip-gateway-provisioning-server-url).

This article also describes how to:

- [Enroll SIP devices either individually or in batches for your convenience](#enroll-sip-devices).  

- [View and monitor your SIP devices.](#view-and-monitor-sip-devices)

- [Enable support for a multi-language user interface.](#support-a-multi-language-user-interface)

## Verify that SIP Gateway is available for your organization

1. Sign in to the [Teams admin center](https://admin-teams.microsoft.net/).

2. At the left, select **Teams devices** and see if the **SIP devices** tab is visible. If it is, the SIP Gateway service is enabled for your organization.

## Enable SIP Gateway for the users in your organization

There are two ways you can enable SIP Gateway for your organization: by using the Teams admin center or by using the Set-CsTeamsCallingPolicy PowerShell cmdlet.

### By using Teams admin center

To enable SIP Gateway in the Teams admin center, follow these steps:

1. Go to the [Teams admin center](https://admin-teams.microsoft.net/)

2. At the left, under **Voice**, select **Calling policies**.

3. At the right under **Manage policies**, select the appropriate calling policy assigned to users or, if necessary, create a new calling policy and assign it to the required users.

4. Select **Manage policies**, select a policy, and then select **Edit**.

5. Turn on the setting for **SIP devices can be used for calls**, and then select **Save**.


### By using PowerShell

You can also enable SIP Gateway by using the [Set-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallingpolicy?view=skype-ps) cmdlet. To enable users for SIP devices, select a policy, and set the **AllowSIPDevicesCalling** attribute to **$true**. The default value is **$false**, so users will not be able to use their SIP devices unless you enable them.


## Set the SIP Gateway provisioning server URL

### Administrators

For each SIP device, you must set one of the following SIP Gateway provisioning server URLs: 

- EMEA: `http://emea.ipp.sdg.teams.microsoft.com`
- Americas: `http://noam.ipp.sdg.teams.microsoft.com`
- APAC: `http://apac/ipp.sdg.teams.microsoft.com`

Add SIP devices to your Teams organization by configuring the above SIP Gateway provisioning server URL in your DHCP server. **[HOW? I still can't figure this part out from pp. 5-6 in the source document. They're not written in step-by-step "here's how to do it" style. I think admins need step-by-step instructions for this.** The devices in your organization will be routed to the SIP Gateway provisioning server. Successfully provisioned SIP phones will display the Teams logo and a soft button for sign-in.

To provision each SIP device, also do the following:
- Update the SIP device's firmware if required. To find out the minimum supported firmware version for all SIP devices, refer to [Plan for SIP Gateway](sip-gateway-plan.md)
- Default configuration for the device to be used with SIP Gateway. **[What does this mean?]**
-	SIP Gateway authentication UX. **[What does this mean?]**

### Remote users

Users who work remotely must manually configure the provisioning server URL into their SIP device by using the following steps:

1. Open **Settings** on the device and get the device's IP address.

2. Open a browser window, enter the device’s IP address, log in (if necessary) and configure the provisioning server’s URL in the device's web utility.

3. Under **Settings** or **Advanced settings** on the web utility, enter the provisioning server URL shown above.

> [!NOTE]
> - Only compatible SIP devices can be onboarded to SIP Gateway. 
> - Cisco IP phones must be flashed to multiplatform firmware before they can be onboarded. To learn how, see [Cisco firmware conversion guide](https://www.cisco.com/c/products/collateral/collaboration-endpoints/unified-ip-phone-7800-series/guide-c07-742786.html)| 
> - Some Yealink models also require a license to migrate from Skype for Business firmware to SIP.


## Configure conditional access

Conditional Access is an Azure Active Directory (Azure AD) feature that helps ensure that devices that access your Office 365 resources are properly managed and secure. SIP Gateway authenticates SIP devices with Azure AD, so if your organization uses Conditional Access for devices in the corporate network, it should exclude the following IP addresses:

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

For more information, see [IP address ranges](https://docs.microsoft.com/azure/active-directory/conditional-access/location-condition#ip-address-ranges).

## Enroll SIP devices
> [!NOTE]
> A SIP device must be onboarded to SIP Gateway before it can be enrolled.

To streamline your tasks, you can enroll SIP devices in the Teams admin center either one at a time or in batches. **[Are "provision" and "enroll" the same? I changed them all to "enroll" in this section, but the UI mentions "provision".]** Here's how:

1. Log in to the [**Teams admin center**](https://admin.teams.microsoft.net/).

2. Select **Teams devices** > **SIP devices**.

3. At the upper right, select **Actions** > **Provision devices** and follow one of these steps:

  - **To enroll one device:**

     a. Under **Waiting on activation**, select **Add**.

     b. On the **Add MAC addresses** pane, enter the **MAC address** and **Location** of the device, and then select **Apply**.
     
     c. Under **Waiting on activation**, select the device you just added, and then select **Generate verification code**.
     
     d. On the **Provision devices** pane, under **Verfication code**, note the verification code for the SIP device.

   - **To enroll many devices:**

     a. Under **Waiting on activation**, at the right, select **Export** (the Microsoft Excel icon).
     
     b. n the **Provision devices** pane, under **Upload multiple MAC addresses**, select **download a template**.
     
     c. Save **Template_Provisioning.csv** to your computer and fill in the **MAC id** and **Location** fields.
    
     d. On the **Provision devices** pane, select **Upload multiple MAC addresses**. 

     e. At the right on the **Upload MAC addresses** pane, select **Select a file**, and select the **Template_Provisioning.csv** file that contains your data.

     f. On the **Provision devices** pane, under **Waiting on activation**, select a device and then select **Generate verification code** to generate a one-time verification code for each provisioned device. Note the verification code for each SIP device.

4. On the SIP device, dial the enrollment feature code followed by the verification code. For example, if the enrollment feature code is *55* and the verification code is *123456*, dial *5512345* to enroll the device.

5.  On the **Provision devices** pane, under **Waiting for sign in**, select **Signed out**.

6. In the **Sign in a user** dialog, copy or note the SIP device's pairing code.

7. Go to [https://microsoft.com/devicelogin](https://microsoft.com/devicelogin), and under **Enter code**, enter the SIP device's pairing code, and then select **Next**.

8. On the Microsoft **Sign in** page, in the **Email or phone** field, enter the email address or phone number for the SIP device, and then select **Next**.

9. On the **Password** page, enter the password for the email address or phone number for the SIP device, and then select **Sign in**.

10. On the **Are you trying to sign in to Teams SIP devices gateway** page, select **Continue**.

## How to sign in and sign out

Only local sign-in is supported for users’ personal devices. To sign out a device from the Admin center, follow these steps:

1. Log in to the [**Teams admin center**](https://admin.teams.microsoft.net/).

2. Select **Teams devices** > **SIP devices**.

3. At the right, select a SIP device, and then select **Sign out**.


### Remote user pairing and sign in

**[Are these steps covered above in "Enroll SIP devices"?]**

To pair a SIP device after the user authenticates using corporate credentials, a user must:

1. Press **Sign-in** on the SIP phone to display the authentication URL and pairing code. The pairing code is time-sensitive. If it expires, the user must press **Back** on the phone and start the sign-in process again.

2. Navigate to the authentication URL on the user's desktop or mobile browser and use corporate credentials to log in.

3. Enter the pairing code displayed on the SIP phone into the web authentication app to pair the SIP phone with the user's account. On a successful sign-in, which might take a while, the SIP phone will display the phone number and username, if the device supports it.

> [!NOTE]
> The location of the device shown on the Azure Active Directory web authentication app is the SIP Gateway datacenter to which the device is connected. SIP phones in scope are not OAuth-capable, so SIP Gateway authenticates the user through the web authentication app and then pairs the device with the user’s credentials. Learn more here: [Microsoft identity platform and the OAuth 2.0 device authorization grant flow](https://docs.microsoft.com/azure/active-directory/develop/v2-oauth2-device-code).

### Sign out

To sign out, a device user can:

- Press **Sign-Out** on the SIP device and follow the steps described on the device. 

To sign out a device on the Teams admin center:

1. Log in to the [**Teams admin center**](https://admin.teams.microsoft.net/).

2. Select **Teams devices** > **SIP devices**.

3. At the right, in the **SIP devices** pane, select the device.

4. On the device's **Details pane**, select the **Details** tab, and at the upper right on the **Actions** menu, select **Sign out**. 


## View and monitor SIP devices

You can view and monitor your SIP device inventory in the Teams admin center after the devices' users sign in at least once. Here's how:

1. Log in to the [Teams admin center](https://admin-teams.microsoft.net/).

2. Select **Teams devices** > **SIP devices**. All signed-in SIP devices are listed on the right.

## Restart a SIP device

1. Log in to the [Teams admin center](https://admin-teams.microsoft.net/).

2. Select **Teams devices** > **SIP devices**. 

3. On the right, select the SIP device that you want to restart, and then select **Restart**.

## Sync policy changes to SIP devices to enforce policies

User details and policies will be fetched to SIP devices when users sign in. Any policy changes thereafter for signed-in users will be synced to the device within one hour. Sync will be triggered with registration refresh. [What does this mean?]


## Set a SIP device's UI language

A SIP device can usually display information in many languages. Setting its UI language affects its interface, including softkeys and sign-in/sign-out system messages. Setting the UI language is done in the provisioning server, using DHCP server, or manually by appending a code string in the URL as in the following examples.

How to set German for Polycom, AudioCodes, and Yealink phones:
- `http://emea.ipp.sdg.teams.microsoft.com/lang_de`

How to set Japanese for Cisco phones:
- `http://emea.ipp.sdg.teams.microsoft.com/lang_ja/$PSN.xml` 


### Supported languages

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

## Emergency calling

[Disclaimer about emergency calling]

## Report problems to Microsoft

To report problems, contact [Microsoft Support](https://support.microsoft.com).