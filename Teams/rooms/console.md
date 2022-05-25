---
title: "Build a Microsoft Teams Rooms image"
ms.author: czawideh
author: cazawideh
ms.reviewer: Travis-Snoozy
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.service: msteams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
ms.custom: seo-marvel-apr2020
ms.assetid: dae1bfb6-7262-4030-bf53-dc3b3fe971ea
description: This article describes how to set up and configure the Microsoft Teams Rooms console and its peripherals.
---

# Build a Microsoft Teams Rooms image

This article describes how to build a Microsoft Teams Rooms image for mass deployment of Teams Rooms.

> [!NOTE]
> The following steps should only be used when creating a [WIM-based image](/windows-hardware/manufacture/desktop/capture-and-apply-an-image) for mass deployment. If you are recovering individual devices, contact your Original Equipment Manufacturer (OEM) for support.

You should only perform these steps if the necessary Microsoft Teams or Skype for Business and Exchange accounts have already been created and tested as described in [Deploy Microsoft Teams Rooms](rooms-deploy.md). You will need the hardware and software described in [Microsoft Teams Rooms requirements](requirements.md). This topic contains the following sections:
  
- [Prepare the installation media](console.md#Prep_Media)
- [Install a private CA certificate on the console](console.md#Certs)
- [Install Windows 10 and the Microsoft Teams Rooms console app](console.md#Reimage)
- [Initial set up of the console](console.md#Initial)
- [Microsoft Teams Rooms deployment checklist](console.md#Checklist)

## Prepare the installation media
<a name="Prep_Media"> </a>

Installing the Microsoft Teams Rooms console app requires a USB storage device with at least 32GB of capacity. There should be no other files on the device; any existing files on the USB storage will be lost.
  
> [!NOTE]
> Failure to create your Microsoft Teams Rooms installation media according to these instructions will likely result in unexpected behavior.

> [!NOTE]
> The process below is for creating installation media to image new Microsoft Teams Rooms devices. Existing devices, by default, update automatically from Windows Update and the Windows Store.

> [!IMPORTANT]
> The Windows 10 machine used to create the Microsoft Teams Rooms installation media must be on the same or later version of Windows as the target installation media.
  
1. Download the [CreateSrsMedia.ps1 script](https://go.microsoft.com/fwlink/?linkid=867842).
2. Run the CreateSrsMedia.ps1 script from an elevated prompt on a Windows 10 machine.
3. Follow the script's instructions to create a Microsoft Teams Rooms USB setup disk.


> [!TIP]
> Each time the CreateSrsMedia.ps1 script starts, the screen output will include the name of a log file or transcript for the session. If there are issues with running the script, make sure to have a copy of that transcript available when requesting support. 

The CreateSrsMedia.ps1 script automates the following tasks:

1. Download the latest MSI installer for Microsoft Teams Rooms.
2. Determine the build of Windows that the user must supply. The most recently released versions may or may not be tested and supported for use with Microsoft Teams Rooms devices.
3. Download necessary supporting components.
4. Assemble the needed components on the installation media.

> [!NOTE]
A specific version of Windows 10 is required, and this version is only available to volume licensing customers.  You can get a copy from the [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/).

When finished, remove the USB disk from your computer and proceed to [Install Windows 10 and the Microsoft Teams Rooms console app](console.md#Reimage).

    
## Install Windows 10 and the Microsoft Teams Rooms console app
<a name="Reimage"> </a>

You now need to apply the setup media you've created. The target device will run as an appliance and the default user will be set to only run the Microsoft Teams Rooms app.

1. If the target device will be installed in a dock (e.g., a Surface Pro), disconnect it from the dock.

2. Ensure the target device is not connected to the network.

3. Ensure the target device is connected to AC power.

4. Plug your USB setup disk into the target device.

5. Boot to the USB setup disk. Refer to the manufacturer instructions. If your target device is a Surface Pro, use the following steps to boot to the USB setup disk:

    a. Press and continue to hold the volume down (-) button.

    b. Press and release the power button.

    c. Once Windows setup is booted, release the volume down (-) button.

8. The system will shut down once installation is complete.
    
After the system has shut down, it is safe to remove the USB setup disk. At this point, you can place the target device in its dock (if using a dock-based product), attach the peripherals needed for your meeting room, and connect to the network. Refer to the manufacturer instructions.

> [!NOTE]
> Software updates for Microsoft Teams Rooms are automatically downloaded from the Microsoft Store for Business. See [Prerequisites for Microsoft Store for Business and Education](/microsoft-store/prerequisites-microsoft-store-for-business) to verify that the room console will be able to access the store and self-update.  

### Selecting a language 

In Creator's Update, you will need to use the ApplyCurrentRegionAndLanguage.ps1 script in scenarios where implicit language selection does not provide the user with the actual application language they want (e.g., they want the console app to come up in French, but it's coming up in English).
  
> [!NOTE]
> The following instructions work only for consoles created using Windows Creator's Update (Windows 10 20H1) or later.
  
### To apply your desired language

1. Switch to Admin mode.
    
2. Select the Start menu.
    
3. Select the gear icon to launch the **Settings** app.
    
4. Select **Time &amp; language**.
    
5. Select **language**.
    
6. Select **Add a language**.
    
7. Select the language you wish to add.
    
8. Install language features.
    
9. Do not check Set as my Windows display language.
    
10. Select **Install**.
    
11. Select the language you just added to the "Languages" list.
    
12. Set as default- Move up arrow to set default

13. For any languages you wish to remove:
    
    a. Select the language you wish to remove.
    
    b. Select Remove.

14. Start an elevated command prompt.

15. Run the following command: 
    ```PowerShell
    powershell -executionpolicy unrestricted c:\Rigel\x64\scripts\provisioning\scriptlaunch.ps1 ApplyCurrentRegionAndLanguage.ps1
    ```
    
16. Restart the system.
    
Your desired language is now applied to the Microsoft Teams Rooms console.
## Initial set up of the console
<a name="Initial"> </a>

After Windows is installed, the Microsoft Teams Rooms app will go into its initial Setup process.
  
1. The User Account screen appears. Enter the Microsoft Exchange Resource account sign-in address (in user@domain format) of the room account to be used with the console.
    
2. Enter the password for the room account, and re-enter it to verify.
   
3. Select the supported meeting mode - Microsoft Teams Only, Skype for Business Only, or one of the two mixed-mode options. If necessary, enable Modern Authentication.

4. Select **Next**.
    
5. If using Skype for Business and if the Skype for Business SIP domain is different from the Exchange domain of the user, set the FQDN for the Skype for Business Server in the Advanced section. If you are not using Skype for Business or the SIP domain matches the Exchange domain, leave this section blank.
6. Select **Next**.
    
7. Select **Finish**.
    
The Microsoft Teams Rooms app should signing in to Microsoft Teams or Skype for Business Server with the credentials entered above, and should also begin syncing its calendar with Exchange using those same credentials. For details on using Teams Rooms, refer to the [Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2).
  
> [!IMPORTANT]
> Microsoft Teams Rooms relies on the presence of certified console hardware. Even a correctly created image containing the Microsoft Teams Rooms console app will not boot past the initial setup procedure unless the console hardware is detected. For Surface Pro based solutions, the Surface Pro must be connected to its accompanying dock hardware to pass this check.
  
> [!NOTE]
> Some non-English language users may need a physical keyboard connected to the console during initial setup in the event that symbols are not supported on the touch keyboard.
  
### Install a private CA certificate on the console
<a name="Certs"> </a>
> [!NOTE]
> The following only applies if connecting Teams Rooms to Skype for Business.

Microsoft Teams Rooms needs to trust the certificates used by the servers it connects to. In a case where the Certificate Authority is private, for instance an on-premises deployment with Active Directory and the Windows Certificate Authority, you can add the certificate to Microsoft Teams Rooms in a couple of ways:
  
- You can join the console to Active Directory and that will automatically add the required certificates given the Certificate Authority is published to Active Directory (normal deployment option).
    
- You can install the certificate manually after the imaging process. Before you do this, you must complete [Initial set up of the console](console.md#Initial).
    
### To manually install the certificate

1. Download the CA certificate to your computer and save it to "C:\Skype Room Systems\x64\Scripts\Provisioning\CAcertificate.cer".
    
2. Place the console in admin mode (see [Admin mode and device management](rooms-operations.md#AdminMode)).
    
3. Run the following command:
    
   ```PowerShell
   certutil -addstore -f -enterprise root "C:\Skype Room Systems\x64\Scripts\Provisioning\CAcertificate.cer"
   ```

### Join an Active Directory domain (Optional)
<a name="Certs"> </a>

You can join Microsoft Teams Rooms to your domain. Microsoft Teams Rooms should be placed in a separate OU from your PC workstations because many workstation policies are not compatible with Microsoft Teams Rooms. A common example is a password enforcement policy that will prevent Microsoft Teams Rooms from starting up automatically. For information about the management of GPO settings, refer to [Manage Microsoft Teams Rooms](rooms-operations.md).
  
### To join Microsoft Teams Rooms to a domain

1. Sign into the console from the admin account (see [Admin mode and device management](rooms-operations.md#AdminMode)).
    
2. Launch elevated Powershell command prompt.
    
3. Enter the following command in Powershell:
    
   ```PowerShell
   Add-Computer -DomainName <Fully qualified domain> -OUPath "OU=<Child OU>, ... ,OU=<Top level OU>,DC=<child domain>,...,DC=<top level domain>"
   ```

For example, if your fully qualified domain is redmond.corp.microsoft.com and you want your Microsoft Teams Rooms consoles to be in a "Microsoft Teams Rooms" OU that is a child of a "Resources" OU, the command will be:
  
```PowerShell
Add-Computer -DomainName redmond.corp.microsoft.com -OUPath "OU=Microsoft_Teams_Rooms,OU=Resources,DC=redmond,DC=corp,DC=microsoft,DC=com"
```

 If you would like to rename the computer when joining it to a domain, use the -NewName flag followed by the computer's new name.
  
## Microsoft Teams Rooms deployment checklist
<a name="Checklist"> </a>

Use the following checklist while doing a final verification that the console and all its peripherals are fully configured:
  
**Application settings**

|Completed |Check |
|:-----:|:-----|
|☐   |Room account name and phone # (if PSTN enabled) are correctly displayed   |
|☐   |Windows computer name is set correctly (useful for remote administration)   |
|☐   |Administrator account password set and verified   |
|☐   |All firmware updates have been applied   |
   
**Audio/video peripherals**

|Completed |Check |
|:-----:|:-----|
|☐   |Camera peripheral firmware version is correct (if applicable)   |
|☐   |Camera functional and positioned optimally   |
|☐   |Settings for Playback Default Device and Playback Default Communications Device set to intended audio peripheral   |
|☐   |Settings for Recording Default Communication Device set to the intended audio peripheral   |
|☐   |Audio peripheral firmware version is correct (if applicable)   |
|☐   |Audio input device functional and optimally positioned   |
|☐   |Audio output device functional and optimally positioned   |

**Console**

|Completed |Check |
|:-----:|:-----|
|☐   |Cables are secure and not pinched   |
|☐   |Audio ingest over HDMI is functional   |
|☐   |Video ingest over HDMI is functional   |
|☐   |Console can swivel freely   |



   
## See also
<a name="Checklist"> </a>

[Plan for Microsoft Teams Rooms](rooms-plan.md)
  
[Deploy Microsoft Teams Rooms](rooms-deploy.md)
  
[Configure a Microsoft Teams Rooms console](console.md)
  
[Manage Microsoft Teams Rooms](rooms-manage.md)
