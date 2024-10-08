---
title: Prepare your Environment
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: altsou
ms.date: 08/21/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.assetid: b4e0ad1e-12e5-4130-aec1-d8c9cd3a5965
description: Learn about how to prepare your infrastructure for deploying Microsoft Teams Rooms so that you can take advantage of all of the features.
ms.custom: seo-marvel-apr2020
---

# Prepare your environment

This section contains an overview of the steps required to prepare your environment so that you can use all of the features of Microsoft Teams Rooms.
  
1. Prepare a resource account for each Microsoft Teams Rooms device. See [Deploy Microsoft Teams Rooms](rooms-deploy.md) for details
    
2. Ensure that there's a working network/Internet connection for the device to use with access to all required URLs and IPs, further guidance can be found here: [Network Security](security.md#network-security)
  
3. In order to improve your experience, Microsoft collects data. To allow Microsoft to collect data, allow these sites:

   - Telemetry client endpoint: `https://vortex.data.microsoft.com/`
   - Telemetry settings endpoint:` https://settings.data.microsoft.com/`
    
## Create and test a resource account

A  *resource account*  is an account that the Microsoft Teams Rooms device uses to access features such as: Teams for Calling and Meetings and SharePoint for Whiteboards and PowerPoint files. See [Deploy Microsoft Teams Rooms](rooms-deploy.md) for details.
  
## Confirm network configuration

In order to function properly, Microsoft Teams Rooms devices must have access to a network that meets these requirements:
  
- Access to: Microsoft Teams, SharePoint/OneDrive, Pro Management Portal, Microsoft Store, Windows Update, Intune, Entra ID, & Microsoft Common destinations. Open required ports to the required destinations documented in [Teams Rooms Network Security](/microsoftteams/rooms/security?tabs=Windows#network-security)

- Review network bandwidth and quality of service (QoS) requirements: [QoS on Teams Devices](/microsoftteams/devices/qos-on-teams-devices)

- If your organization utilizes a proxy, you need the proxy address or proxy autoconfiguration (PAC) file url

- If your organization utilizes certificates for network access, you need the certificates for a successful setup


> [!IMPORTANT]
> Be sure to use a network connection with enough bandwidth (we recommend 10 mbps up/down per Teams Room) to ensure your meetings perform well.


### Certificates

Your Microsoft Teams Rooms device uses certificates for Microsoft Teams, network usage, and authentication. If the related servers use public certificates, which is the case for online, there should be no further action required on the part of the admin to install certificates. If, on the other hand, the certificate authority is a private CA then the device needs to trust that CA. This means having the CA + CA chain certificates installed on the device. Certificates can be installed via Intune for your Teams Rooms devices or via OEM tooling.


### Proxy

> [!IMPORTANT]
> Microsoft Teams Rooms does not support proxy authentication as it may interfere with regular operations of the room. Ensure that Microsoft Teams Rooms have been exempted from proxy authentication before going into production. If your proxy server utilizes internally signed certificates, you must install the internal certificate chain, including the root CA, on the Microsoft Teams Rooms device.

#### Proxy for Teams Rooms on Windows

This guidance is for manual configuration. This can also be automated using Intune configurations on your devices ensure these configurations are consistent across a large scale deployment.

##### Skype User Registry Hive

1. In the Microsoft Teams Rooms UI, select on the Settings gear icon where you'll be prompted for the local Administrator password on the device (the default password is **sfb**)
2. Tap on **Settings** followed by tapping on the **Go to Windows** button and then tapping on the **go to Admin Sign In** button and then clicking the **Administrator** button (if the computer is Entra ID joined choose **Other User,** then use .\admin as the user name)
3. In the **Search Windows** box bottom left type in regedit (either long press the screen or right select and choose **Run as administrator**)
4. Select on the HKEY_USERS folder (you'll see a list of machine user SIDs) ensure the root folder HKEY_USERS is selected
5. Select on File and then choose **Load Hive**
6. Browse to the **C:\Users\Skype** folder and type in the File name box NTUSER.dat and press the open button
7. You'll be prompted for a Key Name for your newly loaded Hive; type in Skype (you should now see the registry settings for the Skype User)
8. Open the Skype key and browse to HKEY_USERS\Skype\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings then ensure these settings are entered: 
    
    ```console
    [HKEY_USERS\Skype\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings]
    "MigrateProxy"=dword:00000001
    "ProxyEnable"=dword:00000001
    "ProxyServer"="xx.xx.xx.xx:8080"
    ```
    
    If ProxyServer doesn't exist you may have to add this key as a string, change the xx.xx.xx.xx:8080 to the ip/host and port of your Proxy server.
 
    A completed configuration would look like this example:

     ```console
    [HKEY_USERS\Skype\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings]
    "MigrateProxy"=dword:00000001
    "ProxyEnable"=dword:00000001
    "AutoConfigURL"=http://contosoproxy.corp.net/proxy.pac
    ```
    
9. Once you're finished making your changes highlight the Skype User key (root folder for Skype) and choose unload Hive from the Registry file menu (you'll be prompted for confirmation - select **Yes**)
10. You can now close the registry editor and reboot your Teams Room 
    
##### Windows System Proxy

1. In the Microsoft Teams Rooms UI, select on the Settings gear icon where you'll be prompted for the local Administrator password on the device (the default password is **sfb**)
2. Tap on **Settings** followed by tapping on the **Go to Windows** button and then tapping on the **go to Admin Sign In** button and then clicking the **Administrator** button (if the computer is Entra ID joined choose **Other User,** then use .\admin as the user name)
3. In the **Search Windows** box bottom left type in 'Settings'
4. Select 'Network & internet'
5. Select 'Proxy'
6. Configure your proxy IP or proxy PAC file
7. Close Settings and reboot your Teams Room

##### Pro Management Agent Proxy

1. In the Microsoft Teams Rooms UI, select on the Settings gear icon where you'll be prompted for the local Administrator password on the device (the default password is **sfb**)
2. Tap on **Settings** followed by tapping on the **Go to Windows** button and then tapping on the **go to Admin Sign In** button and then clicking the **Administrator** button (if the computer is Entra ID joined choose **Other User,** then use .\admin as the user name)
3. In the Windows ***Search*** field (bottom-left section of the screen), enter **cmd** (either long press the screen or right select, and choose ***Run as administrator***).
4. Run the following command (double quotes at end of command are important):

   - If using single ***proxy server***: `bitsadmin /Util /SetIEProxy LOCALSYSTEM MANUAL_PROXY <proxyserver>:<port> ""`

     *Example:*

     ```cmd
     bitsadmin /Util /SetIEProxy LOCALSYSTEM MANUAL_PROXY contosoproxy.corp.net:8080 ""
     ```

   - If using a ***pac*** file: `bitsadmin /Util /SetIEProxy LOCALSYSTEM AUTOSCRIPT <pac file url>`

     *Example:*

     ```cmd
     bitsadmin /Util /SetIEProxy LOCALSYSTEM AUTOSCRIPT http://contosoproxy.corp.net/proxy.pac
     ```

#### Proxy on Teams Rooms on Android

Proxy settings on Teams Rooms on Android vary by device manufacturer. Consult OEM documentation for how to best configure Teams Rooms on Android devices for a network with a proxy.

## Tenant Restrictions

For organizations which utilize the [tenant restrictions](/entra/identity/enterprise-apps/tenant-restrictions) features of Entra ID, this is supported on some Teams Devices if your organization utilizes the proxy deployment variant of tenant restrictions with header injection.

#### Teams Rooms on Windows

To support tenant restrictions, ensure you have your proxy configuration on your Teams Rooms device completed per this Learn document and ensure the Teams Rooms on Windows device has the replacement SSL certificates installed on it to trust the header injected web traffic.

#### Teams Rooms on Android

Tenant restrictions is not supported today on Teams Rooms on Android devices.  Consult with your Android device OEM for potential workarounds.

## Admin group management

If you choose to join a Teams Rooms on Windows device to a domain (Microsoft Entra ID or Active Directory), you can use Microsoft Intune, Group Policy, or Local Computer Management to set a Security Group as local administrator just like you would for a Windows PC in your domain. Anyone who is a member of that security group can enter their credentials and unlock Settings.
  
> [!NOTE]
> If your Microsoft Teams Rooms device loses trust with the domain (for example, if you remove the Microsoft Teams Rooms from the domain after it is domain joined), you won't be able to authenticate into the device and open up Settings. The workaround is to log in with the local Admin account. 

## Local accounts for Teams Rooms on Windows

### Local 'Skype' User Account

Teams Rooms includes a passwordless local account named "Skype". This account is used to sign in to Windows to launch the Teams Rooms app. It isn't supported to apply a password to this account. See [Microsoft Teams Rooms security](security.md) for more information.
  
### Local "Admin" User Account

> [!CAUTION]
> Be sure to change the Microsoft Teams Rooms password as soon as possible. 

Microsoft Teams Rooms default password is set to "sfb". The password can be changed in several ways:

- Recommended: [Configuring LAPS on Teams Rooms on Windows](/microsoftteams/rooms/laps-authentication)
- Intune: [Set-LocalUser](/powershell/module/microsoft.powershell.localaccounts/set-localuser)
- Locally: [Change or reset your Windows password](https://support.microsoft.com/windows/change-or-reset-your-windows-password-8271d17c-9f9e-443f-835a-8318c8f68b9c)

You can read more about the Admin account in the [Microsoft Teams Rooms security](security.md) article.
  
### Machine Account

Much like any Windows device, the machine name can be renamed by right-clicking in **Settings** \> **About** \> **Rename PC**.
  
If you would like to rename the computer after joining it to a domain, use [Rename-Computer](/powershell/module/microsoft.powershell.management/rename-computer), a PowerShell command, followed by the computer's new name.
  
## Related articles

[Plan Microsoft Teams Rooms](rooms-plan.md)

[Deploy Microsoft Teams Rooms](rooms-deploy.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)

[Teams Rooms Security](/microsoftteams/rooms/security)
