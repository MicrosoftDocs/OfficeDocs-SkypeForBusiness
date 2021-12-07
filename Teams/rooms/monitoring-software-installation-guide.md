---
title: Microsoft Teams Rooms Software Installation 
author: donnah007 
ms.author: v-donnahill
manager: serdars
ms.reviewer:  
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Onboarding Teams Rooms devices to managed services
f1keywords: 
---



# Monitoring device software installation  
Deployment requires onboarding Microsoft Teams Rooms devices to the Microsoft Teams Rooms managed services. The monitoring service agent is for use with certified Microsoft Teams Room (MTR) systems and peripherals. 


## Performing operations as the Admin user of the MTR device 
Some configuration/installation procedures require you to log in to the device as Administrator. 

To log in to the device as Administrator (local administrator): 

1. Ensure you hang up any ongoing calls and return to the home screen. 
1. In the Microsoft Teams Room user interface, select  **More** <insert icon here> then select **Settings** <insert icon here> where you'll be prompted for the local Administrator password on the device (the default password is ***sfb***). 
 

1. Select **Settings**, then select  **Windows Settings**  to access Windows as local administrator.  


1. From the list of users displayed in the Windows login screen, select  **Administrator** (or the respective local administrator of your device). 


> [!NOTE]
 > If the computer is *domain joined*, choose **Other User**, then use **.\admin**, or the user name of the local administrator configured in the device as the user name.  


To return to the Microsoft Teams Room app after performing the necessary administrative tasks: 

1. From the Windows ***Start menu***, sign out from the Admin account. 
1. Return to Microsoft Teams Room by selecting the user account icon on the far left side of the screen and then selecting **Skype**. 

 > [!NOTE]
 > If the Skype user is not listed, select Other User and enter ***.\skype*** as the user name, and sign in. 
## Prerequisites 
Follow these procedures to set up your hardware before attempting the enrollment process:

### Adding proxy settings (optional) 
1. Log in as administrator by following [Performing operations as the Admin user of the MTR device](#performing-operations-as-the admin-user-of-the-mtr-device). 
1. In the Windows ***Search*** field (bottom-left section of the screen), enter **cmd** (either long press the screen or right select, and choose ***Run as administrator***).  
1. Run the following command (double quotes at end of command are important:
   
  - If using single ***proxy server***:  bitsadmin /Util /SetIEProxy LOCALSYSTEM MANUAL\_PROXY <proxyserver>:<port> "" 

    *Example:* bitsadmin /Util /SetIEProxy LOCALSYSTEM MANUAL\_PROXY contosoproxy.corp.net:8080 ""* 

 - If using a ***pac*** file:  bitsadmin /Util /SetIEProxy LOCALSYSTEM AUTOSCRIPT <pac file url> "" 

    *Example:* bitsadmin /Util /SetIEProxy LOCALSYSTEM AUTOSCRIPT http://contosoproxy.corp.net/proxy.pac "" 


### Enabling TPM settings  
If TPM on an Intel NUC device is disabled, enable TPM on these devices as follows:  

1. Plug in the keyboard to a NUC device.  
1. Restart device.  
1. To display the BIOS screen, rapidly press **F2**.  
1. Select **Advanced**.  
1. Select **Security**.  
1. On the right-hand side beneath Security Features, enable **Intel Platform Trust Technology**.  
1. To save your settings, press **F10**.  
1. In the confirmation box, select **Yes**.  


## URLs Required for Communication  
> [!NOTE]
> All network traffic between the MTR devices agent and the Microsoft Teams Rooms – Managed Services service portal is SSL over port 443*.*  See [Office 365 URLs and IP address ranges - Microsoft 365 Enterprise | Microsoft Docs](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide).



The following hosts must be allowed if you have **traffic allowlist** enabled within your enterprise environment: 

agent.rooms.microsoft.com<br>
global.azure-devices-provisioning.net<br> 
gj3ftstorage.blob.core.windows.net<br> 
iothubsgagwt5wgvwg6.azure-devices.net<br>
blobssgagwt5wgvwg6.blob.core.windows.net<br>
mmrstgnoamiot.azure-devices.net<br> 
mmrstgnoamstor.blob.core.windows.net<br> 
mmrprodapaciot.azure-devices.net<br>
mmrprodapacstor.blob.core.windows.net<br> 
mmrprodemeaiot.azure-devices.net<br> 
mmrprodemeastor.blob.core.windows.net<br> 
mmrprodnoamiot.azure-devices.net<br> 
mmrprodnoamstor.blob.core.windows.net<br> 


## Process  
The Enrollment process involves a few steps:  

1. On the left navigation bar of the Microsoft Teams Rooms – Managed Services portal [http://portal.rooms.microsoft.com](https://portal.rooms.microsoft.com/), expand **Settings** and select **General**.  
1. Under *Self-Enrollment keys*, select **Download installer** hyperlink https://aka.ms/serviceportalagentmsi to download the monitoring agent software. 
1. Also under *Self-Enrollment keys* section, select **Download Key**. Place the key file under the **C:\Rigel** folder on each device you are enrolling.  
1. ***Optional*:** Set up proxy settings for the agent *– see* *previous section Adding Proxy Settings (optional)* 
1. Install the agent installer (downloaded in step 2) on MTR units, either by running the MSI locally on an MTR device or via your normal means of publishing MSI applications en masse to devices within your environment (Group-Policy etc.)  
1. The room appears in the portal within 5-10 minutes. If it does not, contact managedroomsupport@microsoft.com.  

![alt text](media/software-installation.005.jpg) 


## Installation  
After downloading the installer from Microsoft (either from the portal or by using the AKA.ms URL provided above), unzip its contents to access the file **ManagedRoomsInstaller.msi**. 

There are two modes of installation—individual local machine install and mass deploy mode (usually via group policy of similar method). We recommend individual install for non-domain joined machines or for machines that you have no way of running MSI installers remotely.  

Due to the many varied ways in which customers can run MSI applications in mass deployment mode this document will only walk through installation in individual mode.  

 > [!NOTE]
 > The installer program flow is the same, no matter what mode is being run. The only slight difference is that the install does not request a user to press the next and close buttons in mass deploy mode.  


## Individual Device&mdash;Domain-joined walkthrough  
1. Log in the device as administrator – ensure the *Performing operations as the Admin user of the device* steps are followed. 

1. Copy the following files to the MTR device: 

- Place the ‘Self-Enrollment key’ (previously downloaded from the portal) on the **C:\Rigel** directory of the device. 
- Copy the **ManagedRoomsInstaller.msi** (previously downloaded from the portal or from the AKA.MS) to the device. 



3. On running the ***ManagedRoomsInstaller.msi***, you will see a License Agreement screen. After reading the agreement, check ***I accept the terms in the License Agreement*** and press the **Install** button.  

    This begins the Microsoft Teams Rooms – Managed Services monitoring software install. A prompt for elevation (run as administrator) is displayed.
    
 1. Select ***Yes***. 
 
    The installation will continue. During the installation procedure, a console window opens and begins the final stage of the Microsoft Teams Rooms – Managed Services monitoring software installation.  
    
    > [!NOTE]
    > Do not close the window. Once the installation is complete, the wizard displays a “Finish” button.   

1. Press **Finish**.  


## Completing enrollment  
After the install is complete, wait 5-10 minutes and refresh the portal and the device will be listed, reported as *Onboarding* state. 

In *Onboarding* state, the status of the room is displayed and updated but it won't raise any alerts or create investigation tickets. 

Choose the room and select **Enroll**  to start getting incident alerts, investigation tickets, or to report an incident. 

For any questions or issues, please open a customer reported incident in the portal or contact managedroomsupport@microsoft.com. 


# Unenrolling and uninstalling the monitoring software  
To unenroll the device, remove the monitoring agent from the MTR device as follows: 

1. On the device being monitored, log in the device as administrator. Ensure the *Performing operations as the Admin user of the device* steps are followed. 
1. Download reset script from [aka.ms/MTRPDeviceOffBoarding](https://aka.ms/MTRPDeviceOffBoarding).
1. Extract the script somewhere on the device and copy path 
1. Open PowerShell as administrator: In the Windows ***Search*** field (bottom-left section of the screen), enter ‘Powershell’ and right-click ***Windows PowerShell*** 
1. Select *“Run as Administrator”* and accept UAC prompt. 
1. Enter *Set-ExecutionPolicy –ExecutionPolicy RemoteSigned* , then press **Y** on next prompt.  
1. Paste or type the full path to the unzipped offboarding script into the PowerShell window and press Enter. For example: 

   *C:\Users\admin\Downloads\MTRP\_Device\_Offboarding\MTRP\_Device\_Offboarding.ps1*  

   This resets the device to user standard MTR updates and removes the MTRP monitoring agent and files. 

7. From the left-hand menu in the Microsoft Teams Rooms – Managed Services portal, select **Rooms**.  
8. In the list of rooms provided, choose the room you want to unenroll and select **Unenroll** to stop getting incident alerts or investigation tickets, or to report an incident for the room. 


## Troubleshooting table  
> [!NOTE]
> All Microsoft Teams Rooms – Managed Services monitoring errors are logged on a specific Event Log file named **Microsoft Managed Rooms**.  
### ***Application runtime log file location*** =  
C:\Windows\ServiceProfiles\LocalService\AppData\Local\ServicePortalAgent\ app-x.x.x\ServicePortalAgent\ServicePortal\_Verbose\_LogFile.log, where **x.x.x** is the app version number. 

|**Symptom**  |**Recommended Procedure**  |
| :- | :- |
|<p>You receive an error message stating   </p><p>***ERROR: Please run this application with*** </p><p>***elevated privileges***  </p>|Run the application with escalated privileges and try again  |
|  |  |
|<p>You receive an error message stating   </p><p>***TPM data cannot be found***  </p>|Ensure that your device has TPM (Trusted Platform Module) turned on in its BIOS. This is usually found in the security settings of the device BIOS  |
|  |  |
|<p>You receive an error message  </p><p>` `***ERROR: Local user account named 'Admin' or ‘Skype’ not found***  </p>|Ensure that the user accounts exist on the certified Microsoft Teams Room systems device.  |
|  |  |
|You receive any error state messages that are not covered above  |Please provide a copy of your installation log to your Microsoft Teams System support agent.  |

