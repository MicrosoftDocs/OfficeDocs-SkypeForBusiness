---
title: "Configure a Skype Room Systems v2 console"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/14/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Priority
ms.collection: Strat_SB_Admin
ms.custom: 
ms.assetid: dae1bfb6-7262-4030-bf53-dc3b3fe971ea
description: "This article describes how to set up the Skype Room Systems v2 console device and its peripherals."
---

# Configure a Skype Room Systems v2 console
 
This article describes how to set up the Skype Room Systems v2 console device and its peripherals.
  
You should only perform these steps if the necessary Skype for Business and Exchange accounts have already been created and tested as described in [Deploy Skype Room Systems v2](room-systems-v2.md). You will need the hardware and software described in [Skype Room Systems v2 requirements](../../plan-your-deployment/clients-and-devices/requirements.md). This topic contains the following sections:
  
- [Prepare the installation image](console.md#Prep_Image)
    
- [Install a private CA certificate on the tablet device](console.md#Certs)
    
- [Install Windows 10 and the Skype Room Systems v2 console app ](console.md#Reimage)
   
- [Initial set up of the Console ](console.md#Initial)
    
- [Skype Room Systems v2 Deployment Checklist](console.md#Checklist)
    
> [!NOTE]
> Skype Room Systems v2 will only work in a properly configured Skype for Business environment where the device accounts are set up correctly as described in [Deploy Skype Room Systems v2](room-systems-v2.md). 
  
## Prepare the installation image
<a name="Prep_Image"> </a>

Installing the Skype Room Systems v2 app on a Surface Pro 4 or Surface Pro requires a USB storage device with at least 32GB of memory formatted as a FAT32 disk. There should be no other files on the device, any existing files on the USB storage will be lost. 
  
> [!NOTE]
> Failure to create your console image according to these instructions will likely result in unexpected behavior. Windows 10 Enterprise Anniversary Update (Version 1607) is no longer supported for Skype Room Systems v2 image creation. 
  
> [!NOTE]
> An existing Skype Room Systems v2 with Windows 10 Enterprise Anniversary Update moving to Skype Room Systems v2 update 3 by way of the Windows Store will work, but a new installation should be done as described below. 
  
1. Download the [MSU for KB4056892](http://download.windowsupdate.com/c/msdownload/update/software/secu/2018/01/windows10.0-kb4056892-x64_a41a378cf9ae609152b505c40e691ca1228e28ea.msu).
2. Download the [CreateSrsMedia.ps1 script](room-systems-v2-scripts.md#createsrsmediaps1).
3. Place the MSU for KB4056892 in the same directory as the CreateSrsMedia.ps1 script.
4. Run the CreateSrsMedia.ps1 script from an elevated prompt on a Windows 10 machine.


Follow the script's instructions to create a Skype Room Systems v2 USB setup disk. When finished, remove the USB disk from your computer and proceed to [Install Windows 10 and the Skype Room Systems v2 console app ](console.md#Reimage).
    
## Install Windows 10 and the Skype Room Systems v2 console app
<a name="Reimage"> </a>

You now need to apply the image you've created. The tablet will run as an appliance and the default user will be set to only run the Skype Room Systems v2 app. 
  
1. The tablet should be connected to a power source. Start from a completely powered-off state. If necessary, press and keep pressing the Power button until the tablet switches off.
    
2. Plug your USB Setup disk into the tablet.
    
3. Press and continue to hold the volume down (-) button on the tablet. 
    
4. Press and release the power button on the tablet.
    
5. Once Windows setup is booted, release the volume down (-) button.
    
6. The system will shut down once installation is complete.
    
After the system has shut down, it is safe to remove the USB Setup Disk. At this point, you can place the tablet in the dock and attach the peripherals needed for your meeting room. Refer to the manufacturer instructions.
  
 
### Selecting a language in Creator's Update

In Creator's Update, you will need to use the ApplyCurrentRegionAndLanguage.ps1 script in scenarios where implicit language selection does not provide the user with the actual application language they want (e.g., they want the app to come up in French, but it's coming up in English).
  
> [!NOTE]
> The following instructions work only for devices created using Windows Creator's Update. Legacy/in-market systems that have not been re-imaged properly to the new provisioning system will not be able to use these instructions, but should also not suffer from the initial issue that requires this manual intervention (Anniversary Edition let you pick your app language explicitly as part of setup). 
  
### To apply your desired language

1. Switch to Admin mode.
    
2. Select the Start menu.
    
3. Select the gear icon to launch the **Settings** app.
    
4. Select **Time &amp; language**.
    
5. Select **Region &amp; language**.
    
6. Select **Add a language**.
    
7. Select the language you wish to add.
    
8. Select the language you just added to the "Languages" list.
    
9. Select **Set as default**.
    
10. For any languages you wish to remove:
    
    a. Select the language you wish to remove.
    
    b. Select **Remove**.
    
11. Start an elevated command prompt.
    
12. Run the following command: 
    
    powershell -executionpolicy unrestricted c:\Rigel\x64\scripts\provisioning\scriptlaunch.ps1 ApplyCurrentRegionAndLanguage.ps1
    
13. Restart the system.
    
Your desired language is now applied to the Skype Room Systems v2 device.
## Initial set up of the Console
<a name="Initial"> </a>

After Windows is installed, the Skype Room Systems v2 app will go into its initial Setup process when it is started next or if the /reboot option was chosen.
  
1. The User Account screen appears. Enter the Skype sign-in address (in user@domain format) of the room account to be used with the device.
    
2. Enter the password for the room account, and re-enter it to verify.
    
3. Under "Configure Domain," set the FQDN for the Skype for Business Server. If the Skype for Business SIP domain is different from the Exchange domain of the user, enter the Exchange domain in this field.
    
4. Click **Next**.
    
5. Select the indicated devices on the Features screen and click **Next**. The default is to have Auto Screen sharing set to On and Hide meeting names set to Off. The devices to select are:
    
   - Microphone for Conferencing: the default microphone for this conference room.
    
   - Speaker for Conferencing: the default speaker for conferencing. 
    
   - Default Speaker: the speaker used for audio from the HDMI ingest.
    
    Each item has a drop-down menu of options to select from. You must make a selection for each device.
    
6. Click **Finish**.
    
The app should immediately start signing in to Skype for Business Server 2015 with the credentials entered above, and should also begin syncing its calendar with Exchange using those same credentials. For details on using the app, refer to the [Skype Room Systems version 2 help](https://support.office.com/en-US/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2).
  
> [!IMPORTANT]
> Skype Room Systems v2 relies on the presence of certified console hardware (the Logitech SmartDock). Even a correctly created image containing the Skype Room Systems v2 app loaded on a Surface Pro 4 or Surface Pro will not boot past the initial setup procedure unless the console hardware is detected. 
  
> [!NOTE]
> Some non-English language users may need a physical keyboard connected to the Console during initial setup in the event that symbols are not supported on the touch keyboard. 
  
### Install a private CA certificate on the tablet device
<a name="Certs"> </a>

The Skype Room Systems v2 device needs to trust the certificates used by the Skype for Business and Exchange servers it connects to. For O365 this is done automatically, since these servers are using public Certificate Authorities and these are automatically trusted by Windows 10. In a case where the Certificate Authority is private, for instance an on-premises deployment with Active Directory and the Windows Certificate Authority, you can add the certificate to the Skype Room Systems v2 device in a couple of ways:
  
- You can join the device to Active Directory and that will automatically add the required certificates given the Certificate Authority is published to Active Directory (normal deployment option).
    
- You can install the certificate manually after the imaging process. Before you do this, you must complete [Initial set up of the Console ](console.md#Initial). 
    
### To manually install the certificate

1. Download the CA certificate to your computer and save it to "C:\Skype Room Systems\x64\Scripts\Provisioning\CAcertificate.cer".
    
2. Place the Surface 4 in admin mode (see [Admin mode and device management](../../manage/skype-room-systems-v2/skype-room-systems-v2.md#AdminMode)).
    
3. Run the following command:
    
  ```
  certutil -addstore -f -enterprise root "C:\Skype Room Systems\x64\Scripts\Provisioning\CAcertificate.cer"
  ```

### Join an Active Directory Domain (Optional)
<a name="Certs"> </a>

You can join Skype Room Systems v2 devices to your domain. Skype Room Systems v2 devices should be placed in a separate OU from your PC workstations because many workstation policies are not compatible with Skype Room Systems v2. A common example are password enforcement policies that will prevent Skype Room Systems v2 from starting up automatically. For information about the management of GPO settings, please refer to [Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/skype-room-systems-v2.md). 
  
### To join Skype Room System v2 to a domain

1. Sign into the console from the admin account (see [Admin mode and device management](../../manage/skype-room-systems-v2/skype-room-systems-v2.md#AdminMode)).
    
2. Launch elevated Powershell command prompt.
    
3. Enter the following command in Powershell:
    
  ```
  Add-Computer -DomainName <Fully qualified domain> -OUPath "OU=<Child OU>, … ,OU=<Top level OU>,DC=<child domain>,…,DC=<top level domain>"
  ```

For example, if your fully qualified domain is redmond.corp.microsoft.com and you want your Skype Room Systems v2 devices to be in a "Skype Room Systems v2" OU that is a child of a "Resources" OU, the command will be:
  
```
Add-Computer -DomainName redmond.corp.microsoft.com -OUPath "OU=Skype_Room_System,OU=Resources,DC=redmond,DC=corp,DC=microsoft,DC=com"
```

 If you would like to rename the computer when joining it to a domain, use the -NewName flag followed by the computer's new name.
  
## Skype Room Systems v2 Deployment Checklist
<a name="Checklist"> </a>

Use the following checklist while doing a final verification that the console device and all its peripherals are fully configured:
  
**Application Settings**

|||
|:-----|:-----|
|☐  <br/> |Room account name and phone # (if PSTN enabled) are correctly displayed in top right of console screen  <br/> |
|☐  <br/> |Windows computer name is set correctly (useful for remote administration)  <br/> |
|☐  <br/> |Administrator account password set and verified  <br/> |
|☐  <br/> |All Surface Pro 4 or Surface Pro System Updates have been applied  <br/> |
   
**Audio/Video Peripherals**

|||
|:-----|:-----|
|☐  <br/> |Camera peripheral firmware version is correct (if applicable)  <br/> |
|☐  <br/> |Camera functional and positioned optimally  <br/> |
|☐  <br/> |Settings for Playback Default Device and Playback Default Communications Device set to intended audio peripheral  <br/> |
|☐  <br/> |Settings for Recording Default Communication Device set to the intended audio peripheral  <br/> |
|☐  <br/> |Audio peripheral firmware version is correct (if applicable)  <br/> |
|☐  <br/> |Audio input device functional and optimally positioned  <br/> |
|☐  <br/> |Audio output device functional and optimally positioned  <br/> |
   
**Dock**

|||
|:-----|:-----|
|☐  <br/> |Cables are secure and not pinched  <br/> |
|☐  <br/> |Audio ingest over HDMI is functional  <br/> |
|☐  <br/> |Video ingest over HDMI is functional  <br/> |
|☐  <br/> |Dock can swivel freely  <br/> |
|☐  <br/> |Display brightness is acceptable for environment  <br/> |
   
## See also
<a name="Checklist"> </a>

#### 

[Plan for Skype Room Systems v2](../../plan-your-deployment/clients-and-devices/skype-room-systems-v2-0.md)
  
[Deploy Skype Room Systems v2](room-systems-v2.md)
  
[Configure a Skype Room Systems v2 console](console.md)
  
[Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/skype-room-systems-v2.md)

