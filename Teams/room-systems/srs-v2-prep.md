---
title: "Prepare your Environment"
ms.author: jambirk
author: jambirk
ms.reviewer: davgroom
manager: serdars
ms.date: 2/16/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b4e0ad1e-12e5-4130-aec1-d8c9cd3a5965
ms.collection: M365-voice
description: "This article explains the infrastructure preparations for deploying Microsoft Teams Rooms."
---
 
# Prepare your environment

This section contains an overview of the steps required to prepare your Skype for Business environment so that you can use all of the features of Microsoft Teams Rooms.
  
1. Prepare a device account for each Microsoft Teams Rooms console. See [Deploy Microsoft Teams Rooms](room-systems-v2.md) for details.
    
2. Ensure that there is a working network/Internet connection for the device to use. 
    
   - It must be able to receive an IP address using DHCP (note: Microsoft Teams Rooms cannot be configured with a static IP address at the first unit startup)
    
   - It must have these ports open (in addition to opening the normal ports for Skype for Business media):
    
   - HTTPS: 443
    
   - HTTP: 80
    
   - If your network runs through a proxy, you'll need the proxy address or script information as well.
    
     > [!NOTE]
     > Microsoft Teams Rooms does not support HDCP input, which has been observed to cause issues with HDMI ingest functionality (video, audio). Take care to ensure that switches connected to Microsoft Teams Rooms have HDCP options turned off. 
  
3. In order to improve your experience, Microsoft collects data. To collect data, we need these sites whitelisted:
    
   - Telemetry client endpoint: https://vortex.data.microsoft.com/
    
   - Telemetry settings endpoint: https://settings.data.microsoft.com/
    
### Create and test a device account

A  *device account*  is an account that the Microsoft Teams Rooms client uses to access features from Exchange, like calendar, and to enable Skype for Business. See [Deploy Microsoft Teams Rooms](room-systems-v2.md) for details.
  
### Check network availability

In order to function properly, the Microsoft Teams Rooms device must have access to a wired network that meets these requirements:
  
- Access to your Active Directory or Azure Active Directory (Azure AD) instance, as well as your Microsoft Exchange and Skype for Business servers.
- Access to a server that can provide an IP address using DHCP. Microsoft Teams Rooms cannot be configured with a static IP address.
- Access to HTTP ports 80 and 443.
- TCP and UDP ports configured as described in [Port and protocol requirements for servers](/skypeforbusiness/plan-your-deployment/network-requirements/ports-and-protocols) for on-premise Skype for Business implementations, or [Office 365 URLs and IP address ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US) for Skype for Business online implementations.

> [!IMPORTANT]
> Be sure to use a wired 1 Gbps network connection to assure you will have the needed bandwidth.
  
### Certificates

Your Microsoft Teams Rooms device uses certificates for Exchange Web Services, Skype for Business, network usage, and authentication. If the related servers use public certificates, which is the case for Online and some On-Premises deployments, there should be no further action required on the part of the admin to install certificates. If, on the other hand, the certificate authority is a private CA (typical for On-Premises deployments) then the device needs to trust that CA which means having the CA + CA chain certificates installed on the device. Adding the device to the domain may perform this task automatically.
  
You will install certificates the same way you would for any other Windows client. 
  
> [!NOTE]
> Certificates may be required in order to have Microsoft Teams Rooms use Skype for Business Server.
  
### Proxy

Microsoft Teams Rooms is designed to inherit Proxy settings from the Windows OS. Access the Windows OS in the following manner:
  
1. In the Microsoft Teams Rooms UI, click on the Settings gear icon where you'll be prompted for the local Administrator password on the device (the default password is **sfb**).
2. Tap on **Settings** followed by tapping on the **Go to Windows** button and then tapping on the **go to Admin Sign In** button and then clicking the **Administrator** button (if the computer is domain joined choose **Other User,** then use .\admin as the user name).
3. In the **Search Windows** box bottom left type in regedit (either long press the screen or right click and choose **Run as administrator**).
4. Click on the HKEY_USERS folder (you'll see a list of machine user SIDs) ensure the root folder HKEY_USERS is selected.
       
5. Click on File and then choose **Load Hive.**
6. Browse the to the **C:\Users\Skype** folder and type in the File name box NTUSER.dat and press the open button

7. You'll be prompted for a Key Name for your newly loaded Hive; type in Skype (you should now see the registry settings for the Skype User).
 
8. Open the Skype key and browse to HKEY_USERS\Skype\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings then ensure these settings are entered: 
    
    [HKEY_USERS\Skype\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings]
    
    "MigrateProxy"=dword:00000001
    
    "ProxyEnable"=dword:00000001
    
    "ProxyServer"="xx.xx.xx.xx:8080"
    
    If ProxyServer doesn't exist you may have to add this key as a string, change the xx.xx.xx.xx:8080 to the ip/host and port of your Proxy server.
    
9. Once you are finished making your changes highlight the Skype User key (root folder for Skype) and choose unload Hive from the Registry file menu (you'll be prompted for confirmation - select **Yes** ).
    
10. You can now close the registry editor and type logoff into the Windows search box.
    
11. Back at the sign-in screen, choose the **Skype** user. If all the previous steps were successful, the Microsoft Teams Rooms device will sign-in successfully.
    
To use this application, you must be able to connect to the endpoints described below. To see the IP addresses, expand the IP address section below the table describing the traffic flow.
  
**Firewall Proxy Host Name/Port Examples**

|Purpose|Source or Credentials|Source Port|Destination|CDN|ExpressRoute for Office 365|Destination IP|Destination Port|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Authentication and identity  <br/> |See [Office 365 authentication and identity](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_Identity) <br/> |||
|Portal and shared  <br/> |See [Office 365 portal and shared](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_Portal-identity) <br/> |||
|SIP Signaling  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |\*.contoso.com  <br/> |No  <br/> |Yes  <br/> |[Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443  <br/> |
|Persistent Shared Object Model (PSOM) connections web conferencing  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |\*.contoso.com  <br/> |No  <br/> |Yes  <br/> |[Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443  <br/> |
|HTTPS downloads  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |\*.contoso.com  <br/> |No  <br/> |Yes  <br/> |[Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443  <br/> |
|Audio  <br/> |Client Computer or Logged on user  <br/> |TCP/UDP 50,000-50019  <br/> |\*.contoso.com  <br/> |No  <br/> |Yes  <br/> |[Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443, UDP 3478, TCP/UDP 50,000-59,999  <br/> |
|Video  <br/> |Client Computer or Logged on user  <br/> |TCP/UDP 50,020-50039  <br/> |\*.contoso.com  <br/> |No  <br/> |Yes  <br/> |[Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443, UDP 3478, TCP/UDP 50,000-59,999  <br/> |
|Desktop Sharing  <br/> |Client Computer or Logged on user  <br/> |TCP/UDP 50,040-50059  <br/> |\*.contoso.com  <br/> |No  <br/> |Yes  <br/> |[Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443, 50,000-59,999  <br/> |
|Lync Mobile push notifications for Lync Mobile 2010 on iOS devices. You don't need this for Android, Nokia Symbian or Windows Phone mobile devices.  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |\*.contoso.com  <br/> |No  <br/> |Yes  <br/> |[Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 5223  <br/> |
|Skype Telemetry  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |skypemaprdsitus.trafficmanager.net  <br/> pipe.skype.com  <br/> |No  <br/> |No  <br/> |N/A  <br/> |TCP 443  <br/> |
|Skype client quicktips  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |quicktips.skypeforbusiness.com  <br/> |No  <br/> |No  <br/> |N/A  <br/> |TCP 443  <br/> |
   
> [!NOTE]
> The wildcard for contoso.com and broadcast.skype.com represents a long list of nodes that are exclusively used for Office 365. 
  
### Create provisioning packages

You will use provisioning packages to authenticate to Exchange Server or Skype for Business Server.
  
### Admin group management

After domain joining, you can use Group Policy or the Local Computer Management to set a Security Group as local administrator just like you would for a Windows PC in your domain. Anyone who is a member of that security group can enter their credentials and unlock Settings.
  
> [!NOTE]
> If your Microsoft Teams Rooms device loses trust with the domain (for example, if you remove the Microsoft Teams Rooms from the domain after it is domain joined), you won't be able to authenticate into the device and open up Settings. The workaround is to log in with the local Admin account. 
  
## Local accounts

### Microsoft Teams Rooms Local User Account

The Device Account does not typically use a password. It is possible to give it a password, but there are consequences, including a possibility that users might get locked out of the console application when that password expires. Consequently, the administrator should take are to ensure that the password is not allowed to expire.
  
### "Admin" - Local Administrator Account

Microsoft Teams Rooms default password is set to "sfb". The Password can be changed locally by going to Windows Settings \> Go to Windows or in the AutoUnattend.xml file (use the Windows System Image manager from ADK to make the change to the xml file).
  
> [!CAUTION]
> Be sure to change the Microsoft Teams Rooms password as soon as possible. 
  
You can also manage the Local Administrator password by setting up a group policy where domain admins are made local admins.
  
The Local admin password is not included as a choice during Setup.
  
### Machine Account

Much like any Windows device, the Machine Name can be renamed by right clicking in Settings \> About \> Rename PC.
  
 If you would like to rename the computer after joining it to a domain, use the Rename-Computer PowerShell command followed by the computer's new name.
  
## See also

[Plan Microsoft Teams Rooms](skype-room-systems-v2-0.md)

[Microsoft Teams Rooms requirements](requirements.md)
  
[Deploy Microsoft Teams Rooms](room-systems-v2.md)
  
[Configure a Microsoft Teams Rooms console](console.md)
  
[Manage Microsoft Teams Rooms](skype-room-systems-v2.md)
