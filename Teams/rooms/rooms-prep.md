---
title: "Prepare your Environment"
ms.author: dstrome
author: dstrome
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: b4e0ad1e-12e5-4130-aec1-d8c9cd3a5965
ms.collection: 
  - M365-collaboration
description: Learn about how to prepare your infrastructure for deploying Microsoft Teams Rooms so that you can take advantage of all of the features.
ms.custom: seo-marvel-apr2020
---
 
# Prepare your environment

This section contains an overview of the steps required to prepare your environment so that you can use all of the features of Microsoft Teams Rooms.
  
1. Prepare a resource account for each Microsoft Teams Rooms console. See [Deploy Microsoft Teams Rooms](rooms-deploy.md) for details.
    
2. Ensure that there is a working network/Internet connection for the device to use.
  
3. In order to improve your experience, Microsoft collects data. To allow Microsoft to collect data, allow these sites:

   - Telemetry client endpoint: https://vortex.data.microsoft.com/
   - Telemetry settings endpoint: https://settings.data.microsoft.com/
    
### Create and test a resource account

A  *resource account*  is an account that the Microsoft Teams Rooms client uses to access features from Exchange, like calendar, and to connect to Microsoft Teams. See [Deploy Microsoft Teams Rooms](rooms-deploy.md) for details.
  
### Check network availability

In order to function properly, Microsoft Teams Rooms  must have access to a wired network that meets these requirements:
  
- Access to your Active Directory or Azure Active Directory (Azure AD) instance, as well as Microsoft Exchange and Microsoft Teams.

- Access to a server that can provide an IP address using DHCP. Microsoft Teams Rooms cannot be configured with a static IP address at the first unit startup.

- Access to HTTP ports 80 and 443.

- TCP and UDP ports configured as described in [Port and protocol requirements for servers](/skypeforbusiness/plan-your-deployment/network-requirements/ports-and-protocols) for on-premise Skype for Business Server implementations, or [Microsoft 365 and Office 365 URLs and IP address ranges](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US) for Microsoft Teams.

If your network runs through a proxy, you'll need the proxy address or script information as well.
    
> [!IMPORTANT]
> Microsoft Teams Rooms does not support proxy authentication as it may interfere with regular operations of the room. Ensure that Microsoft Teams Rooms have been exempted from proxy authentication before going into production.

> [!IMPORTANT]
> Be sure to use a wired 1 Gbps network connection to assure you will have the needed bandwidth.

> [!NOTE]
> Software updates for Microsoft Teams Rooms are automatically downloaded from the Microsoft Store for Business. See [Prerequisites for Microsoft Store for Business and Education](/microsoft-store/prerequisites-microsoft-store-for-business) to verify that the room console will be able to access the store and self-update.
  
### Certificates

Your Microsoft Teams Rooms device uses certificates for Exchange Web Services, Microsoft Teams or Skype for Business, network usage, and authentication. If the related servers use public certificates, which is the case for online and some on-premises deployments, there should be no further action required on the part of the admin to install certificates. If, on the other hand, the certificate authority is a private CA then the device needs to trust that CA. This means having the CA + CA chain certificates installed on the device. Adding the device to the domain may perform this task automatically.
  
You will install certificates the same way you would for any other Windows client.

> [!IMPORTANT]
> If your proxy server utilizes internally signed certificates, you must install the internal certificate chain, including the root CA, on the Microsoft Teams Rooms device.
  
> [!NOTE]
> Certificates may be required in order to have Microsoft Teams Rooms use Skype for Business Server.
  
### Proxy

Microsoft Teams Rooms is designed to inherit Proxy settings from the Windows OS. Access the Windows OS in the following manner:
  
1. In the Microsoft Teams Rooms UI, click on the Settings gear icon where you'll be prompted for the local Administrator password on the device (the default password is **sfb**).
2. Tap on **Settings** followed by tapping on the **Go to Windows** button and then tapping on the **go to Admin Sign In** button and then clicking the **Administrator** button (if the computer is domain joined choose **Other User,** then use .\admin as the user name).
3. In the **Search Windows** box bottom left type in regedit (either long press the screen or right click and choose **Run as administrator**).
4. Click on the HKEY_USERS folder (you'll see a list of machine user SIDs) ensure the root folder HKEY_USERS is selected.
       
5. Click on File and then choose **Load Hive.**
6. Browse to the **C:\Users\Skype** folder and type in the File name box NTUSER.dat and press the open button

7. You'll be prompted for a Key Name for your newly loaded Hive; type in Skype (you should now see the registry settings for the Skype User).
 
8. Open the Skype key and browse to HKEY_USERS\Skype\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings then ensure these settings are entered: 
    
    ```console
    [HKEY_USERS\Skype\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings]
    "MigrateProxy"=dword:00000001
    "ProxyEnable"=dword:00000001
    "ProxyServer"="xx.xx.xx.xx:8080"
    ```
    
    If ProxyServer doesn't exist you may have to add this key as a string, change the xx.xx.xx.xx:8080 to the ip/host and port of your Proxy server.
 
    If the customer is using a PAC file the configuration would look like the example below:

     ```console
    [HKEY_USERS\Skype\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings]
    "MigrateProxy"=dword:00000001
    "ProxyEnable"=dword:00000001
    "AutoConfigURL"=http://contosoproxy.corp.net/proxy.pac
    ```
    
9. Once you are finished making your changes highlight the Skype User key (root folder for Skype) and choose unload Hive from the Registry file menu (you'll be prompted for confirmation - select **Yes**).
    
10. You can now close the registry editor and type logoff into the Windows search box.
    
11. Back at the sign-in screen, choose the **Skype** user. If all the previous steps were successful, the Microsoft Teams Rooms device will sign-in successfully.
    
See the [Network Security](./security.md#network-security) article for full details on FQDNs, ports, and IP address ranges required for Microsoft Teams Rooms.
  
### Admin group management

If you choose to join a domain (Azure Active Directory or Active Directory), you can use Microsoft Endpoint Manager, Group Policy, or Local Computer Management to set a Security Group as local administrator just like you would for a Windows PC in your domain. Anyone who is a member of that security group can enter their credentials and unlock Settings.
  
> [!NOTE]
> If your Microsoft Teams Rooms device loses trust with the domain (for example, if you remove the Microsoft Teams Rooms from the domain after it is domain joined), you won't be able to authenticate into the device and open up Settings. The workaround is to log in with the local Admin account. 
  
## Local accounts

### Microsoft Teams Rooms Local User Account

Teams Rooms includes a passwordless local account named "Skype". This account is used to sign in to Windows to launch the Teams Rooms app. It is not supported to apply a password to this account. See [Microsoft Teams Rooms Security](security.md) for more information.
  
### "Admin" - Local Administrator Account

Microsoft Teams Rooms default password is set to "sfb". The Password can be changed locally via Admin mode or in the AutoUnattend.xml file (use the Windows System Image manager from ADK to make the change to the xml file).
  
> [!CAUTION]
> Be sure to change the Microsoft Teams Rooms password as soon as possible. 
  
The Local admin password is not included as a choice during Setup.

You can read more about the Admin account in the [Microsoft Teams Rooms Security](security.md) article.
  
### Machine Account

Much like any Windows device, the machine name can be renamed by right-clicking in **Settings** \> **About** \> **Rename PC**.
  
If you would like to rename the computer after joining it to a domain, use [Rename-Computer](/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7.2), a PowerShell command, followed by the computer's new name.
  
## Related topics

[Plan Microsoft Teams Rooms](rooms-plan.md)

[Microsoft Teams Rooms requirements](requirements.md)
  
[Deploy Microsoft Teams Rooms](rooms-deploy.md)
  
[Configure a Microsoft Teams Rooms console](console.md)
  
[Manage Microsoft Teams Rooms](rooms-manage.md)

[Prerequisites for Microsoft Store for Business and Education](/microsoft-store/prerequisites-microsoft-store-for-business)
