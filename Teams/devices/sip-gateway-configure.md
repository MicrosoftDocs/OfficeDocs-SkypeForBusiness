---
title: Configure SIP Gateway
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: chasing
ms.date: 08/08/2024
ms.topic: article
audience: admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - highpri
  - Tier1
search.appverid: MET150
f1.keywords:
- NOCSH
- ms.teamsadmincenter.directrouting.overview
description: Learn how to configure SIP Gateway.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
---

# Configure SIP Gateway

This article explains how to configure SIP Gateway so that your organization can use compatible SIP devices with Microsoft Teams. To find out what SIP Gateway can do for your organization and what hardware, software, and licenses your organization needs for it, read [Plan for SIP Gateway](sip-gateway-plan.md).

### Before you can configure SIP Gateway, do the following:

- **Reset SIP devices to factory default settings.** You or your organization's users must reset each SIP device used with SIP Gateway to its factory default settings. To find out how to do that, see the manufacturer’s instructions.

- **Open your firewall to Microsoft 365 and Teams.** Open your network's firewall to Microsoft 365 and Teams traffic as described in [Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges). Firewall rules are needed for outbound traffic only.

- **Make sure the SIP devices are not behind a proxy.** Ensure that http/s traffic bypasses any corporate http/s proxy.

- **Open the UDP port.** Open UDP port in the range 49152 to 53247 for IP ranges 52.112.0.0/14 and 52.122.0.0/15.

- **Open the TCP port.** Open TCP port 5061 for IP ranges 52.112.0.0/14 and 52.122.0.0/15.

### The following sections describe what you must do as an administrator to configure SIP Gateway.

- [Verify that SIP Gateway is available for your organization](#verify-that-sip-gateway-is-available-for-your-organization).

- [Enable SIP Gateway for the users in your organization](#enable-sip-gateway-for-the-users-in-your-organization).

- [Set the SIP Gateway provisioning server URL](#set-the-sip-gateway-provisioning-server-url).

### This article also describes how to:

- [Enroll SIP devices either individually or in batches for your convenience](#provision-and-enroll-sip-devices-as-common-area-phones).  

- [View and monitor your SIP devices.](#view-and-monitor-sip-devices)

- [Enable support for a multi-language user interface.](#set-a-sip-devices-ui-language)

## Verify that SIP Gateway is available for your organization

1. Sign in to the [Teams admin center](https://admin.teams.microsoft.com/).

2. At the left, select **Teams devices** and see if the **SIP devices** tab is visible. If it is, the SIP Gateway service is enabled for your organization.

## Enable SIP Gateway for the users in your organization

You can enable SIP Gateway for your organization in either of two ways: by using the Teams admin center, or by using a PowerShell cmdlet.

### By using Teams admin center

To enable SIP Gateway in the Teams admin center, follow these steps:

1. Go to the [Teams admin center](https://admin.teams.microsoft.com/)

2. At the left, under **Voice**, select **Calling policies**.

3. At the right under **Manage policies**, select the appropriate calling policy assigned to users or, if necessary, create a new calling policy and assign it to the required users.

4. Select **Manage policies**, select a policy, and then select **Edit**.

5. Turn on the setting for **SIP devices can be used for calls**, and then select **Save**.

### By using PowerShell

You can also enable SIP Gateway by using the PowerShell [Set-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy) cmdlet. To enable users for SIP devices, select a policy, and set the `-AllowSIPDevicesCalling` attribute to `True`. The default value is `False`, so users will not be able to use their SIP devices unless you enable them.

> [!NOTE]
> Policy propagation may take up to 24 hours.

## Set the SIP Gateway provisioning server URL

You can set the SIP Gateway provisioning server's URL in your Dynamic Host Configuration Protocol (DHCP) server. Users who work remotely must configure it manually.

### Using DHCP

For each SIP device, set one of the following SIP Gateway provisioning server URLs: 

- EMEA: `http://emea.ipp.sdg.teams.microsoft.com`
- Americas: `http://noam.ipp.sdg.teams.microsoft.com`
- APAC: `http://apac.ipp.sdg.teams.microsoft.com`

Add SIP devices to your Teams organization by configuring the above SIP Gateway provisioning server URL in your DHCP server. To learn more about DHCP server, see [Deploy and manage DHCP](/training/modules/deploy-manage-dynamic-host-configuration-protocol). Also, you can use DHCP option 42 to specify the Network Time Protocol (NTP) server, and DHCP option 2 to specify the offset from Coordinated Universal Time (UTC) in seconds. The devices in your organization will be routed to the SIP Gateway provisioning server. Successfully provisioned SIP phones will display the Teams logo and a soft button for sign-in.

Ensure SIP devices are on the minimum supported firmware version for onboarding. During onboarding, SIP Gateway will push the default configuration and authentication user interface to the device. To find out the required firmware version for SIP devices, see [Plan for SIP Gateway](sip-gateway-plan.md).

### Manually

Users who work remotely must manually configure the provisioning server URL into their SIP device by using the following steps:

1. Open **Settings** on the device and get the device's IP address.

2. Open a browser window, enter the device’s IP address, log in (if necessary) and configure the provisioning server’s URL in the device's web utility.

3. Under **Settings** or **Advanced settings** on the web utility, enter the provisioning server URL shown above.

> [!NOTE]
> - Only compatible SIP devices can be onboarded to SIP Gateway. 
> - Cisco IP phones must be flashed to multiplatform firmware before they can be onboarded. To learn how, see [Cisco firmware conversion guide](https://www.cisco.com/c/en/us/products/collateral/collaboration-endpoints/unified-ip-phone-7800-series/guide-c07-742786.html).
> - For Yealink and Alcatel-Lucent Enterprise phones, use option 66.
> - For Cisco, Poly, and AudioCode phones, use option 160. 
> - For Cisco devices, append **/$PSN.xml** to the provisioning server URL.

## Configure conditional access

Conditional Access is a Microsoft Entra feature that helps ensure that devices that access your Microsoft 365 resources are properly managed and secure. SIP devices are not managed by Intune hence stricter conditional access checks are applied to them. SIP Gateway authenticates SIP devices with Microsoft Entra ID, so if your organization uses Conditional Access for devices in the corporate network, you should do one of the following: 

1. Exclude your site public IP addresses and the following SIP Gateway service IP addresses from Conditional Access checks:

   - North America:
     - East US: 52.170.38.140
     - West US: 40.112.144.212
   - EMEA region:
     - North EU: 40.112.71.149
     - West EU: 40.113.112.67
   - APAC region:
     - Australia East: 20.92.120.71
     - Australia Southeast: 13.73.115.90

2. Exclude the Teams app from Conditional Access checks.

For more information, see [IP address ranges](/azure/active-directory/conditional-access/location-condition#ip-address-ranges).

## Provision and enroll SIP devices as common area phones

> [!NOTE]
> A SIP device must be onboarded to SIP Gateway before it can be enrolled.

To streamline your tasks, you can enroll SIP devices in the Teams admin center either one at a time or in batches. Here's how:

1. Log in to the [**Teams admin center**](https://admin.teams.microsoft.com).

2. Select **Teams devices** > **SIP devices**.

3. At the upper right, select **Actions** > **Provision devices** and follow one of these steps:

   - **To provision one device:**

     1. Under **Waiting on activation**, select **Add**.

     1. On the **Add MAC addresses** pane, enter the **MAC address** and **Location** of the device, and then select **Apply**.
     
     1. Under **Waiting on activation**, select the device you just added, and then select **Generate verification code**.
     
     1. On the **Provision devices** pane, under **Verification code**, note the verification code for the SIP device.

   - **To provision many devices:**

     1. Under **Waiting on activation**, at the right, select **Export** (the Microsoft Excel icon).
     
     1. On the **Provision devices** pane, under **Upload multiple MAC addresses**, select **download a template**.
     
     1. Save **Template_Provisioning.csv** to your computer and fill in the **MAC id** and **Location** fields.
    
     1. On the **Provision devices** pane, select **Upload multiple MAC addresses**. 

     1. At the right on the **Upload MAC addresses** pane, select **Select a file**, and select the **Template_Provisioning.csv** file that contains your data.

     1. On the **Provision devices** pane, under **Waiting on activation**, select a device and then select **Generate verification code** to generate a one-time verification code for each provisioned device. Note the verification code for each SIP device.

4. On the SIP device, dial the enrollment feature code followed by the verification code. On the SIP device, dial the enrollment feature code \*55* (used by SIP Gateway for enrollment one-time-verification code validation), followed by the verification code that is generated in Teams Admin Center for this particular device. For example, if the verification code is 123456, dial \*55\*123456 to enroll the device.

5.  On the **Provision devices** pane, under **Waiting for sign in**, select **Signed out**.

6. In the **Sign in a user** dialog, the authentication URL and pairing code will be displayed.

7. Navigate to the authentication URL on the user's desktop or mobile browser and use corporate credentials to log in.

8. Enter the pairing code displayed in the **Sign in a user** dialog into the web authentication app to pair the SIP phone with the user's account. On a successful sign-in, which might take a while, the SIP phone will display the phone number and username, if the device supports it.

## How to sign in and sign out

Only local sign-in is supported for users’ personal devices. To sign out a device from the Admin center, follow these steps:

1. Log in to the [**Teams admin center**](https://admin.teams.microsoft.com).

2. Select **Teams devices** > **SIP devices**.

3. At the right, select a SIP device, and then select **Sign out**.

### Zero Touch Common Area Phone sign in

You can remotely sign in common area phones to SIP Gateway without any physical intervention on the device.

1. Ensure that [bulk sign in pre-requisites](/microsoftteams/sip-gateway-configure#bulk-sign-in-prerequisites) are in place.

2. Open the [SIP remote login portal](https://aka.ms/sipremotelogin) in a browser tab.

3. Authenticate with common area phone credentials that you want to associate with the device.

4. Select appropriate device region. You can use NOAM, EMEA, or APAC.

5. Enter the MAC address of device in XX-XX-XX-XX-XX-XX format. 

### User pairing and sign-in

To pair a SIP device after the user authenticates using corporate credentials, a user must:

1. Press **Sign-in** on the SIP phone to display the authentication URL and pairing code. The pairing code is time-sensitive. If it expires, the user must press **Back** on the phone and start the sign-in process again.

2. Navigate to the authentication URL on the user's desktop or mobile browser and use corporate credentials to log in.

3. Enter the pairing code displayed on the SIP phone into the web authentication app to pair the SIP phone with the user's account. On a successful sign-in, which might take a while, the SIP phone will display the phone number and username, if the device supports it.

> [!NOTE]
> The location of the device shown on the Microsoft Entra web authentication app is the SIP Gateway datacenter to which the device is connected. SIP phones in scope are not OAuth-capable, so SIP Gateway authenticates the user through the web authentication app and then pairs the device with the user’s credentials. Learn more here: [Microsoft identity platform and the OAuth 2.0 device authorization grant flow](/azure/active-directory/develop/v2-oauth2-device-code).

> [!NOTE]
> We are introducing a new authentication experience progressively for SIP Gateway compatible devices. Users with the new experience will see a [new authentication URL](https://aka.ms/siplogin).

### Sign-out

To sign out, a device user can:

- Press **Sign-Out** on the SIP device and follow the steps described on the device. 

To sign out a device on the Teams admin center:

1. Log in to the [**Teams admin center**](https://admin.teams.microsoft.com).

2. Select **Teams devices** > **SIP devices**.

3. At the right, in the **SIP devices** pane, select the device.

4. On the device's **Details pane**, select the **Details** tab, and at the upper right on the **Actions** menu, select **Sign out**. 

## Bulk sign in

Bulk sign ins enable you to sign in with shared accounts on SIP devices in batches of up to 100 devices each but with a limit of 3 concurrent batches per region.

Bulk sign-in is very helpful and can be used in these scenarios.

- **Activating new SIP devices** When you want to activate and deploy new SIP devices within 3 days (or 72 hours) of onboarding to SIP gateway.
- **Devices that are signed out** To sign in devices that got signed out for any reason, within 7 days (or 168 hours) of being signed out. In this scenario, you don't have to add the tenant ID to the provisioning URL as in Step 2 below.

### Bulk sign in prerequisites

1. You must add your site public IP address or ranges to the [trusted IPs for the tenant](/microsoftteams/manage-your-network-topology) in Teams admin center at least 24 hours prior to running the bulk sign in cmdlets.
2. You must add your organization's tenant ID to the provisioning URL for the devices.

   > [!NOTE]
   > The examples below are for the North America region.

   - For Alcatel-Lucent Enterprise, AudioCodes, and Yealink IP phones use: `http://noam.ipp.sdg.teams.microsoft.com/tenantid/<your-tenant-ID-guid>`
   - For Cisco IP phones use: `http://noam.ipp.sdg.teams.microsoft.com/tenantid/<your-tenant-ID-guid>/$PSN.xml`
   - For analog devices that connect to AudioCodes ATAs use: `http://noam.ipp.sdg.teams.microsoft.com/tenantid/<your-tenant-ID-guid>/mac.ini`

   > [!IMPORTANT]
   > For Cisco ATA replace mac.ini with mac.cfg.
   > For Poly ATA replace mac.ini with $mac.cfg.

3. You must install Microsoft Teams Power Shell 5.6.0 or later.

   > [!NOTE]
   > The bulk sign in cmdlets aren't included with previous versions.

4. You must apply [CommonAreaPhone policy](/microsoftteams/set-up-common-area-phones) to the accounts that are part of a bulk sign in request.
5. The accounts must not have Multi Factor Authentication (MFA) enabled.
6. The accounts must have a phone number assigned.
7. The accounts must have the SIP device calling policy assigned. [AllowSIPDevicesCalling policy](/microsoftteams/sip-gateway-configure)
8. You must use an account that has the **Global Administrator, Privileged Authentication Administrator or the Authentication Administrator** role to run the cmdlets.

   > [!IMPORTANT]
   > Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

1. The **BulkSignIn** attribute must be set to `Enabled` in [TeamsSipDevicesConfiguration](/powershell/module/teams/set-csteamssipdevicesconfiguration)

   > [!NOTE]
   > As a best practice, try running bulk sign in cmdlet at least 1 hour and at most 70 hours after device provisioning.

### How to create a bulk sign in request

1. Create a CSV file that will be used with two columns: **Username** and **HardwareId**.
  
   - **Username** column: Put in the list of Microsoft Entra user names or user principal names (UPNs) to use to associate with the device's MAC address found in the **HardwareId** column.
   - **HardwareId** column: List the MAC address for each IP phone in this format: xx-xx-xx-xx-xx-xx or xx-xx-xx-xx-xx-xx:xxx (where the last three digits are the ATA port number. For analog devices, the port numbers start from 001.) An example for a MAC address without the ATA port number would be: 1A-2B-3C-D4-E5-F6. An example for a MAC address for an analog device would be: 1A-2B-3C-D4-E5-F6:001
   - **Example CSV**:
  
     |Username|HardwareId|
     |:--------|:--------|
     |FirstFloorLobbyPhone1@contoso.com|1A-2B-3C-D4-E5-F6|
     |SecondFloorLobbyPhone2@contoso.com|2A-3B-4C-5D-6E-7F|

2. Set up the PowerShell environment, as described in [Deploy frontline static teams at scale with PowerShell for frontline workers](/microsoft-365/frontline/deploy-teams-at-scale), and get Microsoft Teams PowerShell module 5.6.0.

3. Run the following:

   ```PowerShell
   Import-Module MicrosoftTeams
   $credential = Get-Credential   // Enter your admin’s email and password 
   Connect-MicrosoftTeams –Credential $credential
   $newBatchResponse = New-CsSdgBulkSignInRequest  -DeviceDetailsFilePath  .\Example.csv  -Region APAC
   ```

The `DeviceDetailsFilePath` parameter specifies the location of the CSV you created and saved. The `Region` parameter specifies the SIP gateway provisioning region where the devices are being deployed. The values are: APAC, EMEA, NOAM.

4. To check the status of a bulk sign-in batch, run the following:

   ```PowerShell
   $newBatchResponse = New-CsSdgBulkSignInRequest  -DeviceDetailsFilePath  .\Example.csv  -Region APAC
   $newBatchResponse.BatchId
   $getBatchStatusResponse = Get-CsSdgBulkSignInRequestStatus -Batchid $newBatchResponse.BatchId
   $getBatchStatusResponse | ft
   $getBatchStatusResponse.BatchItem
   ``` 

### Bulk sign in error messages
To help you troubleshoot and fix common issues, these are common error messages that you might see and what you should do to fix it.

| Error message | Potential solution |
|:-----|:-----|
|**User not found in tenant.**|Check the username or User Principal Name (UPN) is correct.|
|**User missing phone number assignment.**|Verify the user has a phone number assigned.|
|**User missing `AllowSIPDevicesCalling` policy assignment**| Verify that `AllowSIPDevicesCalling` policy is set to **Enabled**. See prerequisite 7.|
|**User missing CAP policy assignment.**|Verify that the account has `CommonAreaPhone` policy assigned. See prerequisite 4|
|**Device not found in records.**|Check if the device was correctly provisioned to SIP Gateway, and the region parameter in bulk sign in request is correct.|
|**BulkSignIn Tag missing for the device**| Check to see if the device provisioning URL has the correct tenant ID.|
|**Device is offline.**|The device can't be found because it's powered off or disconnected from network. Reconnect the device and try it again.|
| **Public IP not configured as Trusted IP.**|The tenant ID listed in the provisioning URL isn't correct or the public IP address of the device isn't listed as a trusted IP address in Teams admin center. See prerequisite 1.|
|**Bulk Sign-in deadline expired.**|The device hasn't been signed in to within 72 hours of provisioning (or 168 hours).|
| **Duplicate devices found for bulk sign-in.**|Verify the MAC addresses you included in the CSV file are correct and there aren't duplicated addresses. IP addresses of the duplicate devices are returned.|
|**Input hardware-ID is of wrong format**|Verify the hardware-ID format. See `How to create a bulk sign in request`.|
|**On-premises AD configuration failure.** |Contact your on-premises Active Directory team.|
|**On-premises AD throttling detected**|Try it again but with a smaller number of devices in the batch. Depending on network connectivity, large batches will take more time to complete and may get stuck.|
|**The Password writeback service failed to set a password on the tenant's local directory.**|The user account that is used for the device must not have **User must change password at next login** or **User's password can't be changed** selected, `OR` have the minimum password age must set to a value more than 0. Verify the password options aren't selected and the minimum password age is set to 0 and try again.|

## View and monitor SIP devices

You can view and monitor your SIP device inventory in the Teams admin center after the devices' users sign in at least once. Here's how:

1. Log in to the [Teams admin center](https://admin.teams.microsoft.com/).

2. Select **Teams devices** > **SIP devices**. All signed in SIP devices are listed on the right.

## Restart a SIP device

1. Log in to the [Teams admin center](https://admin.teams.microsoft.com).

2. Select **Teams devices** > **SIP devices**. 

3. On the right, select the SIP device that you want to restart, and then select **Restart**.


> [!NOTE]
> - Removing a SIP device from your tenant is currently unavailable in the Teams admin center. 
> - Command execution depends on device availability, and it may not match the execution status shown in the Teams admin center. If you try to enable SIP gateway on a device that doesn't support it, the command won't be executed.

## Sync policy changes to SIP devices to enforce policies

User details and policies will be fetched to SIP devices when users sign in. Any policy changes thereafter for signed-in users will be synced to the device within one hour. Devices must have their registration refreshed with the SIP Gateway periodically. SIP phones depend on Call Redirect, so the admin must set the `AllowCallRedirect` attribute in `Set-CsTeamsCallingPolicy` to `Enabled`.

## Set a SIP device's UI language

A SIP device can usually display information in many languages. Setting its UI language affects its interface, including softkeys and sign-in/sign-out system messages. Setting the UI language is done in the provisioning server, using DHCP server, or manually by appending a code string in the URL as in the following examples.

How to set German for Polycom, AudioCodes, Alcatel-Lucent Enterprise, and Yealink phones:
- `http://emea.ipp.sdg.teams.microsoft.com/lang_de`

How to set Japanese for Cisco phones:
- `http://emea.ipp.sdg.teams.microsoft.com/lang_ja/$PSN.xml` 

### Supported languages

|Language name|Language code|
|-------------|-------------|
|English (default)|en       |
|Spanish      |es           |
|Japanese     |ja           |
|German       |de           |
|French       |fr           |
|Portuguese   |pt           |

> [!Note]
> Japanese is not supported by Yealink and partially supported by Polycom VVX.
> 
> - The system defaults to English if the selected language is not supported by the SIP endpoint.
> 
> - When the **lang_xx** parameter is not set via the provisioning URL, English is used as the default language.
> 
> - If **Sign in to make an emergency call** text is not translated to other languages, an abbreviated version in English only will be presented on **Press Sign In** on the following IP phone models due to a screensize limitations:
> 
>   - Poly VVX 150, VVX 201
>   - Cisco CP-6821, CP-7811, CP-7821, CP-7841, CP-7861
>    
> - Voice mail softkey label is hardcoded with **VM** text across all languages for Poly VVX because of a limitation of string length.

## Microsoft Teams and IPv6

SIP Gateway only supports IPv4. Microsoft Teams service and client support both IPv4 and IPv6. If you want to control communications to Microsoft Teams, use the IP address ranges in [Microsoft 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges).

## Emergency calling

SIP Gateway supports dynamic emergency calling (dynamic E911) for compatible SIP devices that share network attributes over the wire. These attributes are provisioned in the Teams admin center and can be a combination of local IP and subnet length, or chassis ID and network port number. For devices that do not share location attributes, or if the location is not resolved dynamically for any reason, SIP Gateway will continue to support emergency calling based on registered addresses. Currently, registered addresses are not supported for Direct Routing scenarios. For more information about emergency calling, see [Plan and manage emergency calling](/microsoftteams/what-are-emergency-locations-addresses-and-call-routing).

> [!NOTE]
> Compatible Cisco SIP IP phones only support dynamic location discovery over LLDP. 

## Report problems to Microsoft

To report problems, contact [Microsoft Support](https://support.microsoft.com).
