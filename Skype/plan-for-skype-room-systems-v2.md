---
title: Plan for Skype Room Systems v2
ms.prod: SKYPEFORBUSINESS
ms.assetid: b4e0ad1e-12e5-4130-aec1-d8c9cd3a5965
---


# Plan for Skype Room Systems v2
[]This article explains the relevant planning considerations for deploying Skype Room Systems v2, the next generation of Skype Room Systems. 
 Skype Room Systems v2 is Microsoft's latest conferencing solution designed to transform your meeting room into a rich, collaborative Skype for Business experience. Users will enjoy its familiar Skype for Business interface and IT administrators will appreciate an easily deployed and managed Windows 10 Skype Meeting app. Skype Room Systems v2 is designed to leverage existing equipment like LCD panels for ease of installation to bring Skype for Business into your meeting room.
  
    
    

Skype Room Systems v2 uses a purpose-built UWP app which acts as the Skype Meeting user interface. It runs on a Surface Pro 4 in a console mode (once deployed the UWP app is the only app that will run on the device) and it requires its own device account on your Skype for Business implementation. It leverages existing equipment like LCD panels and relatively inexpensive peripheral cameras and microphones to provide a quality meeting room experience. Software is updated via both Windows store and Windows Update.
Before you being preparing your environment, be sure you have the necessary hardware and software. For more information, see  [Skype Room Systems v2 requirements](skype-room-systems-v2-requirements.md). 
  
    
    

Skype Room Systems v2 is Microsoft's latest conferencing solution designed to transform your meeting room into a rich, collaborative Skype for Business experience. Users will enjoy its familiar Skype for Business interface and IT administrators will appreciate an easily deployed and managed Windows 10 Skype Meeting app. Skype Room Systems v2 is designed to leverage existing equipment like LCD panels for ease of installation to bring Skype for Business into your meeting room. **Built for Skype for Business**
- One-touch join of Skype Meetings
    
  
- Skype Meeting experience optimized for rooms with screen-filling HD video and HD wideband audio
    
  
- All participants can connect to the Skype Meeting using their device of choice from wherever they may be located
    
  
- Invite people from your directory where you can instantly see their availability or via a phone call
    
  
- Supports Skype for Business PSTN Conferencing and PSTN Calling to replace the stand-alone conference phone in your room
    
  
 **Transform Any Meeting Room**
- Dedicated Skype Meeting app optimized for center of table touch controller and large front of room display
    
  
- Re-use existing investments in your front of room display or projectors
    
  
- Works in all types of meeting spaces from huddle spaces to large conference rooms
    
  
- Certified Skype for Business audio and video devices are available for various room sizes
    
  
- Built-in wired ingest for to project desktop sharing to the room and to the Skype Meeting
    
  
- In-app user selection of meeting room audio and video USB devices U1
    
  
- Dual-Screen support (for legacy system parity) U2
    
  
- Themability (built-in themes and the ability to set custom theme) U2
    
  
 **Easy to Deploy, Simple to Manage**
- Always-on appliance that will automatically wake up the displays when it detects people in the room
    
  
- Simple deployment and updating of the UWP (Universal Windows Platform) Skype Meeting App
    
  
- Windows AppLocker locks down the device to the Skype Meeting app
    
  
- Monitored and managed as a Windows 10 Enterprise device via Intune and SCCM (MDM)
    
  
- Enterprise-grade reliability
    
  
- Low training effort of end-users due to familiar Skype user interface
    
  
- Integrated room console status reporting for customers using Microsoft Operations Management Suite (see  [Plan Skype Room Systems v2 management with OMS](plan-skype-room-systems-v2-management-with-oms.md)) U1
    
  
- Ability to Give Feedback for public builds U2
    
  
- Improved Telemetry around meeting join reliability U2
    
  
- Additional OMS reporting U2
    
  
- Ability for IT Admin to configure devices remotely U2
    
  
U1 - Feature introduced in Update 1 (SW Ver. 2.0.2.0).U2- Feature introduced in Update 2 (SW Ver. 3.0.0.0). 
## Preparing your Skype for Business Environment

This section contains an overview of the steps required to prepare your environment so that you can use all of the features of Skype Room Systems v2.
  
    
    

1. Prepare a device account for each Skype Room Systems v2 console. See  [Deploy Skype Room Systems v2](deploy-skype-room-systems-v2.md) for details.
    
  
2. Ensure that there is a working network/Internet connection for the device to use. 
    
  - It must be able to receive an IP address using DHCP (note: Skype Room Systems v2 cannot be configured with a static IP address at the first unit startup)
    
  
  - It must have these ports open (in addition to opening the normal ports for Skype for Business media):
    
  - HTTPS: 443
    
  
  - HTTP: 80
    
  
  - If your network runs through a proxy, you'll need the proxy address or script information as well.
    
  

    > [!NOTE]
      > Skype Room Systems v2 does not support HDCP input, which has been observed to cause issues with HDMI ingest functionality (video, audio). Take care to ensure that switches connected to Skype Room Systems v2 have HDCP options turned off. 
3. In order to improve your experience, Microsoft collects data. To collect data, we need these sites whitelisted:
    
  - Telemetry client endpoint: https://vortex.data.microsoft.com/
    
  
  - Telemetry settings endpoint: https://settings.data.microsoft.com/
    
  

### Create and test a device account

A  *device account*  is an account that the Skype Room Systems v2 client uses to access features from Exchange, like calendar, and to enable Skype for Business. See [Deploy Skype Room Systems v2](deploy-skype-room-systems-v2.md) for details.
  
    
    

### Check network availability

In order to function properly, the Skype Room Systems v2 device must have access to a wired network that meets these requirements:
  
    
    

- Access to your Active Directory or Azure Active Directory (Azure AD) instance, as well as your Microsoft Exchange and Skype for Business servers.
    
  
- Access to a server that can provide an IP address using DHCP. Skype Room Systems v2 cannot be configured with a static IP address.
    
  
- Access to HTTP ports 80 and 443.
    
  
- TCP and UDP ports configured as described in  [Port requirements for Lync Server 2013](https://technet.microsoft.com/en-us/library/gg398798%28v=ocs.15%29.aspx) for on premise Skype for Business implementations, or [Office 365 URLs and IP address ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US) for Skype for Business online implementations.
    
  

> [!IMPORTANT]
> Be sure to use a wired 1 Gbps network connection to assure you will have the needed bandwidth. 
  
    
    


### Certificates

Your Skype Room Systems v2 device uses certificates for Exchange Web Services, Skype for Business, network usage, and authentication. If the related servers use public certificates, which is the case for Online and some On-Premises deployments, there should be no further action required on the part of the admin to install certificates. If, on the other hand, the certificate authority is a private CA (typical for On-Premises deployments) then the device needs to trust that CA which means having the CA + CA chain certificates installed on the device. Adding the device to the domain may perform this task automatically.
  
    
    
You will install certificates the same way you would for any other Windows client. 
  
    
    

> [!NOTE]
> Certificates may be required in order to have Skype Room Systems v2 use Skype for Business Server. 
  
    
    


### Proxy

Skype Room Systems v2 is designed to inherit Proxy settings from the Windows OS. Access the Windows OS in the following manner:
  
    
    

1. In the Skype Room Systems v2 UI, click on the Settings gear icon where you'll be prompted for the local Administrator password on the device (the default password is "sfb").
    
  
2. Tap on "Settings" followed by tapping on the "Go to Windows" button and then tapping on the "got to Admin Sign In" button and then clicking the "Administrator" button (if the computer is domain joined choose "Other User," then use .\\admin as the user name).
    
  
3. In the "Search Windows" box bottom left type in regedit (either long press the screen or right click and choose "Run as administrator").
    
  
4. Click on the HKEY_USERS folder (you'll see a list of machine user SIDs) ensure the root folder HKEY_USERS is selected.
    
    You'll be prompted for a Key Name for your newly loaded Hive; type in Skype (you should now see the registry settings for the Skype User).
    
  
5. Click on File and then choose "Load Hive."
    
  
6. Browse the to the following folder "C:\\Users\\Skype" and type in the File name box NTUSER.dat and press the open button
    
  
7. Open the Skype key and browse to HKEY_USERS\\Skype\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Internet Settings then ensure these settings are entered: 
    
    [HKEY_USERS\\Skype\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Internet Settings]
    
    "MigrateProxy"=dword:00000001
    
    "ProxyEnable"=dword:00000001
    
    "ProxyServer"="xx.xx.xx.xx:8080"
    
    If ProxyServer doesn't exist you may have to add this key as a string, change the xx.xx.xx.xx:8080 to the ip/host and port of your Proxy server.
    
  
8. Once you are finished making your changes highlight the Skype User key (root folder for Skype) and choose unload Hive from the Registry file menu (you'll be prompted for confirmation - select **Yes** ).
    
  
9. You can now close the registry editor and type logoff into the Windows search box.
    
  
10. 
    
  
Back at the sign-in screen, choose the **Skype** user. If all the previous steps were successful, the Skype Room Systems v2 device will sign-in successfully.
  
    
    
To use this application, you must be able to connect to the endpoints described below. To see the IP addresses, expand the IP address section below the table describing the traffic flow.
  
    
    

**Firewall Proxy Host Name/Port Examples**


|**Purpose**|**Source or Credentials**|**Source Port**|**Destination**|**CDN**|**ExpressRoute for Office 365**|**Destination IP**|**Destination Port**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Authentication and identity  <br/> |See  [Office 365 authentication and identity](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_Identity) <br/> |||
|Portal and shared  <br/> |See  [Office 365 portal and shared](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_Portal-identity) <br/> |||
|SIP Signaling  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |*.contoso.com  <br/> |No  <br/> |Yes  <br/> | [Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443  <br/> |
|Persistent Shared Object Model (PSOM) connections web conferencing  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |*.contoso.com  <br/> |No  <br/> |Yes  <br/> | [Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443  <br/> |
|HTTPS downloads  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |*.contoso.com  <br/> |No  <br/> |Yes  <br/> | [Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443  <br/> |
|Audio  <br/> |Client Computer or Logged on user  <br/> |TCP/UDP 50,000-50019  <br/> |*.contoso.com  <br/> |No  <br/> |Yes  <br/> | [Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443, UDP 3478, TCP/UDP 50,000-59,999  <br/> |
|Video  <br/> |Client Computer or Logged on user  <br/> |TCP/UDP 50,020-50039  <br/> |*.contoso.com  <br/> |No  <br/> |Yes  <br/> | [Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443, UDP 3478, TCP/UDP 50,000-59,999  <br/> |
|Desktop Sharing  <br/> |Client Computer or Logged on user  <br/> |TCP/UDP 50,040-50059  <br/> |*.contoso.com  <br/> |No  <br/> |Yes  <br/> | [Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 443, 50,000-59,999  <br/> |
|Lync Mobile push notifications for Lync Mobile 2010 on iOS devices. You don't need this for Android, Nokia Symbian or Windows Phone mobile devices.  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |*.contoso.com  <br/> |No  <br/> |Yes  <br/> | [Skype for Business IP ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US#BKMK_SfB_IP) <br/> |TCP 5223  <br/> |
|Skype Telemetry  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |skypemaprdsitus.trafficmanager.net  <br/> pipe.skype.com  <br/> |No  <br/> |No  <br/> |N/A  <br/> |TCP 443  <br/> |
|Skype client quicktips  <br/> |Client Computer or Logged on user  <br/> |Ephemeral ports  <br/> |quicktips.skypeforbusiness.com  <br/> |No  <br/> |No  <br/> |N/A  <br/> |TCP 443  <br/> |
   

> [!NOTE]
> The wildcard for contoso.com and broadcast.skype.com represents a long list of nodes that are exclusively used for Office 365. 
  
    
    


### Create provisioning packages

You will use provisioning packages to authenticate to Exchange or Skype for Business.
  
    
    

### Admin group management

After domain joining, you can use Group Policy or the Local Computer Management to set a Security Group as local administrator just like you would for a Windows PC in your domain. Anyone who is a member of that security group can enter their credentials and unlock Settings.
  
    
    

> [!NOTE]
> If your Skype Room Systems v2 device loses trust with the domain (for example, if you remove the Skype Room Systems v2 from the domain after it is domain joined), you won't be able to authenticate into the device and open up Settings. The workaround is to log in with the local Admin account. 
  
    
    


## Local accounts


### Skype Room Systems Local User Account

The Device Account does not typically use a password. It is possible to give it a password, but there are consequences, including a possibility that users might get locked out of the console application when that password expires. Consequently, the administrator should take are to ensure that the password is not allowed to expire.
  
    
    

  
    
    

### "Admin" - Local Administrator Account

Skype Room Systems v2 default password is set to "sfb". The Password can be changed locally by going to Windows Settings > Go to Windows or in the AutoUnattend.xml file (use the Windows System Image manager from ADK to make the change to the xml file).
  
    
    

> [!CAUTION]
> Be sure to change the Skype Room Systems v2 password as soon as possible. 
  
    
    

You can also manage the Local Administrator password by setting up a group policy where domain admins are made local admins.
  
    
    
The Local admin password is not included as a choice during Setup.
  
    
    

### Machine Account

Much like any Windows device, the Machine Name can be renamed by right clicking in Settings > About > Rename PC.
  
    
    
 If you would like to rename the computer after joining it to a domain, use the Rename-Computer PowerShell command followed by the computer's new name.
  
    
    

## See also


#### 


  
    
    
 [Skype Room Systems v2 requirements](skype-room-systems-v2-requirements.md)
  
    
    
 [Deploy Skype Room Systems v2](deploy-skype-room-systems-v2.md)
  
    
    
 [Configure a Skype Room Systems v2 console](configure-a-skype-room-systems-v2-console.md)
  
    
    
 [Manage Skype Room Systems v2](manage-skype-room-systems-v2.md)
