---
title: "Configure a Skype Room Systems v2 console"
ms.author: jambirk
author: jambirk
ms.reviewer: Travis-Snoozy
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: Strat_SB_Admin
ms.custom: 
ms.assetid: dae1bfb6-7262-4030-bf53-dc3b3fe971ea
description: "This article describes how to set up the Skype Room Systems v2 console and its peripherals."
---

# Configure a Skype Room Systems v2 console
 
This article describes how to set up the Skype Room Systems v2 console and its peripherals.
  
You should only perform these steps if the necessary Skype for Business and Exchange accounts have already been created and tested as described in [Deploy Skype Room Systems v2](room-systems-v2.md). You will need the hardware and software described in [Skype Room Systems v2 requirements](../../plan-your-deployment/clients-and-devices/requirements.md). This topic contains the following sections:
  
- [Prepare the installation media](console.md#Prep_Media)
    
- [Install a private CA certificate on the console](console.md#Certs)
    
- [Install Windows 10 and the Skype Room Systems v2 console app](console.md#Reimage)
   
- [Initial set up of the console](console.md#Initial)
    
- [Skype Room Systems v2 deployment checklist](console.md#Checklist)
    
> [!NOTE]
> Skype Room Systems v2 will only work in a properly configured Skype for Business environment where the device accounts are set up correctly as described in [Deploy Skype Room Systems v2](room-systems-v2.md).
  
## Prepare the installation media
<a name="Prep_Media"> </a>

Installing the Skype Room Systems v2 console app requires a USB storage device with at least 32GB of memory formatted as a FAT32 disk. There should be no other files on the device, any existing files on the USB storage will be lost.
  
> [!NOTE]
> Failure to create your Skype Room Systems v2 installation media according to these instructions will likely result in unexpected behavior. Windows 10 Enterprise Anniversary Update (Version 1607) is no longer supported for Skype Room Systems v2 installation media creation.

> [!NOTE]
> An existing Skype Room Systems v2 with Windows 10 Enterprise moving to Skype Room Systems v2 update 3 by way of the Windows Store will work, but a new installation should be done as described below.
  
1. Download the [CreateSrsMedia.ps1 script](https://go.microsoft.com/fwlink/?linkid=867842).
2. (Optional) Download and place any desired language pack CAB files in the same directory as the script. The script will indicate where you can download language pack files appropriate for the type of media you are creating, if you're unsure where to acquire the language packs from.
3. Run the CreateSrsMedia.ps1 script from an elevated prompt on a Windows 10 machine.

Follow the script's instructions to create a Skype Room Systems v2 USB setup disk. When finished, remove the USB disk from your computer and proceed to [Install Windows 10 and the Skype Room Systems v2 console app](console.md#Reimage).

> [!TIP]
> You might have noticed that we no longer call out specific versions of the drivers, Skype Room Systems v2 client, or Windows 10 Enterprise. This is deliberate, we want the script to match and verify compatibility for all installers. The script will automatically find and get what it needs for a supported configuration.  
    
## Install Windows 10 and the Skype Room Systems v2 console app
<a name="Reimage"> </a>

You now need to apply the setup media you've created. The target device will run as an appliance and the default user will be set to only run the Skype Room Systems v2 console app.

1. If the target device will be installed in a dock (e.g., a Surface Pro), disconnect it from the dock.

2. Ensure the target device is not connected to the network.

3. Ensure the target device is connected to AC power.

4. Plug your USB setup disk into the target device.

5. Boot to the USB setup disk. Refer to the manufacturer instructions. If your target device is a Surface Pro, use the following steps to boot to the USB setup disk:

    1. Press and continue to hold the volume down (-) button.

    2. Press and release the power button.

    3. Once Windows setup is booted, release the volume down (-) button.

8. The system will shut down once installation is complete.
    
After the system has shut down, it is safe to remove the USB setup disk. At this point, you can place the target device in its dock (if using a dock-based product), attach the peripherals needed for your meeting room, and connect to the network. Refer to the manufacturer instructions.
  
### Selecting a language 

In Creator's Update, you will need to use the ApplyCurrentRegionAndLanguage.ps1 script in scenarios where implicit language selection does not provide the user with the actual application language they want (e.g., they want the console app to come up in French, but it's coming up in English).
  
> [!NOTE]
> The following instructions work only for consoles created using Windows Creator's Update. Legacy/in-market systems that have not been set up using media with the new provisioning system will not be able to use these instructions, but should also not suffer from the initial issue that requires this manual intervention (Anniversary Edition let you pick your app language explicitly as part of setup).
  
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
    ```
    powershell -executionpolicy unrestricted c:\Rigel\x64\scripts\provisioning\scriptlaunch.ps1 ApplyCurrentRegionAndLanguage.ps1
    ```
    
13. Restart the system.
    
Your desired language is now applied to the Skype Room Systems v2 console.
## Initial set up of the console
<a name="Initial"> </a>

After Windows is installed, the Skype Room Systems v2 console app will go into its initial Setup process when it is started next or if the /reboot option was chosen.
  
1. The User Account screen appears. Enter the Skype sign-in address (in user@domain format) of the room account to be used with the console.
    
2. Enter the password for the room account, and re-enter it to verify.
    
3. Under "Configure Domain," set the FQDN for the Skype for Business Server. If the Skype for Business SIP domain is different from the Exchange domain of the user, enter the Exchange domain in this field.
    
4. Click **Next**.
    
5. Select the indicated devices on the Features screen and click **Next**. The default is to have Auto Screen sharing set to On and Hide meeting names set to Off. The devices to select are:
    
   - Microphone for Conferencing: the default microphone for this conference room.
    
   - Speaker for Conferencing: the default speaker for conferencing. 
    
   - Default Speaker: the speaker used for audio from the HDMI ingest.
    
     Each item has a drop-down menu of options to select from. You must make a selection for each device.
    
6. Click **Finish**.
    
The Skype Room Systems v2 console app should immediately start signing in to Skype for Business Server with the credentials entered above, and should also begin syncing its calendar with Exchange using those same credentials. For details on using the console app, refer to the [Skype Room Systems version 2 help](https://support.office.com/en-US/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2).
  
> [!IMPORTANT]
> Skype Room Systems v2 relies on the presence of certified console hardware. Even a correctly created image containing the Skype Room Systems v2 console app will not boot past the initial setup procedure unless the console hardware is detected. For Surface Pro based solutions, the Surface Pro must be connected to its accompanying dock hardware to pass this check.
  
> [!NOTE]
> Some non-English language users may need a physical keyboard connected to the console during initial setup in the event that symbols are not supported on the touch keyboard.
  
### Install a private CA certificate on the console
<a name="Certs"> </a>

The Skype Room Systems v2 console needs to trust the certificates used by the Skype for Business and Exchange servers it connects to. For O365 this is done automatically, since these servers are using public Certificate Authorities and these are automatically trusted by Windows 10. In a case where the Certificate Authority is private, for instance an on-premises deployment with Active Directory and the Windows Certificate Authority, you can add the certificate to the Skype Room Systems v2 console in a couple of ways:
  
- You can join the console to Active Directory and that will automatically add the required certificates given the Certificate Authority is published to Active Directory (normal deployment option).
    
- You can install the certificate manually after the imaging process. Before you do this, you must complete [Initial set up of the console](console.md#Initial).
    
### To manually install the certificate

1. Download the CA certificate to your computer and save it to "C:\Skype Room Systems\x64\Scripts\Provisioning\CAcertificate.cer".
    
2. Place the console in admin mode (see [Admin mode and device management](../../manage/skype-room-systems-v2/room-systems-v2-operations.md#AdminMode)).
    
3. Run the following command:
    
   ```
   certutil -addstore -f -enterprise root "C:\Skype Room Systems\x64\Scripts\Provisioning\CAcertificate.cer"
   ```

### Join an Active Directory domain (Optional)
<a name="Certs"> </a>

You can join Skype Room Systems v2 consoles to your domain. Skype Room Systems v2 consoles should be placed in a separate OU from your PC workstations because many workstation policies are not compatible with Skype Room Systems v2. A common example are password enforcement policies that will prevent Skype Room Systems v2 from starting up automatically. For information about the management of GPO settings, please refer to [Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/room-systems-v2-operations.md).
  
### To join Skype Room System v2 to a domain

1. Sign into the console from the admin account (see [Admin mode and device management](../../manage/skype-room-systems-v2/room-systems-v2-operations.md#AdminMode)).
    
2. Launch elevated Powershell command prompt.
    
3. Enter the following command in Powershell:
    
   ```
   Add-Computer -DomainName <Fully qualified domain> -OUPath "OU=<Child OU>, … ,OU=<Top level OU>,DC=<child domain>,…,DC=<top level domain>"
   ```

For example, if your fully qualified domain is redmond.corp.microsoft.com and you want your Skype Room Systems v2 consoles to be in a "Skype Room Systems v2" OU that is a child of a "Resources" OU, the command will be:
  
```
Add-Computer -DomainName redmond.corp.microsoft.com -OUPath "OU=Skype_Room_System,OU=Resources,DC=redmond,DC=corp,DC=microsoft,DC=com"
```

 If you would like to rename the computer when joining it to a domain, use the -NewName flag followed by the computer's new name.
  
## Skype Room Systems v2 deployment checklist
<a name="Checklist"> </a>

Use the following checklist while doing a final verification that the console and all its peripherals are fully configured:
  
**Application settings**

|||
|:-----|:-----|
|☐  <br/> |Room account name and phone # (if PSTN enabled) are correctly displayed in top right of console screen  <br/> |
|☐  <br/> |Windows computer name is set correctly (useful for remote administration)  <br/> |
|☐  <br/> |Administrator account password set and verified  <br/> |
|☐  <br/> |All firmware updates have been applied  <br/> |
   
**Audio/video peripherals**

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

[Plan for Skype Room Systems v2](../../plan-your-deployment/clients-and-devices/skype-room-systems-v2-0.md)
  
[Deploy Skype Room Systems v2](room-systems-v2.md)
  
[Configure a Skype Room Systems v2 console](console.md)
  
[Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/skype-room-systems-v2.md)