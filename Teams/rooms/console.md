---
title: Build a Microsoft Teams Rooms image
ms.author: tonysmit
author: mstonysmith
ms.reviewer: Travis-Snoozy
manager: pamgreen
ms.date: 08/22/2024
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
ms.custom: seo-marvel-apr2020
ms.assetid: dae1bfb6-7262-4030-bf53-dc3b3fe971ea
description: This article describes how to create and apply Microsoft Teams Rooms installation media.
---

# Build a Microsoft Teams Rooms image

This article describes how to build a Microsoft Teams Rooms image for mass deployment of Teams Rooms.

> [!IMPORTANT]
> The information in this article is intended for test environments or for organizations that have very specific and uncommon deployment blockers that prevent the usage of [certified Teams Rooms systems](certified-hardware.md). Before following the information in this article, we strongly recommend that you discuss your specific Teams Rooms deployment with your Microsoft representative.
> [!NOTE]
> The following steps should only be used when creating a [WIM-based image](/windows-hardware/manufacture/desktop/capture-and-apply-an-image) for mass deployment. If you are recovering individual devices, contact your Original Equipment Manufacturer (OEM) for support.

You should only perform these steps if the necessary Microsoft Teams and Exchange accounts have already been created and tested as described in [Deploy Microsoft Teams Rooms](rooms-deploy.md). This topic contains the following sections:

- [Supported hardware](console.md#supported-hardware)
- [Prepare the installation media](console.md#Prep_Media)
- [Install a private CA certificate on the console](console.md#Certs)
- [Install Windows and the Microsoft Teams Rooms console app](console.md#Reimage)
- [Initial set up of the console](console.md#Initial)
- [Microsoft Teams Rooms deployment checklist](console.md#Checklist)

## Supported hardware

|Tablet|Processor|RAM|Disk|
|:-----|:-----|:-----|:-----|
|Surface Pro 6| Core i5 |16 GB or 8 GB |128 GB or more |
|Surface Pro </br>(fifth Gen) |Core i5 |8 GB or 4 GB |128 GB or more |
|Surface Pro 4 |Core i5 |8 GB or 4 GB |128 GB or more |

> [!NOTE]
> - Core M3 processors aren't supported.
> - You need a 32 GB or larger USB drive configured as bootable Windows installation media for Windows Enterprise.

Surface Pro devices require one of the following docking station options:

- [Logitech SmartDock](https://www.logitech.com/assets/64799/smartdockdatasheetweb.pdf)
- [Polycom MSR Series](https://www.polycom.com/hd-video-conferencing/microsoft-video/msr-series.html)

## Prepare the installation media
<a name="Prep_Media"> </a>

Installing the Microsoft Teams Rooms console app requires a USB storage device with at least 32GB of capacity. There should be no other files on the device; any existing files on the USB storage will be lost. The script will require that a specific Windows ISO be supplied in order to generate the installation media. That ISO is available only through [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/).
  
> [!NOTE]
> Failure to create your Microsoft Teams Rooms installation media according to these instructions will likely result in unexpected behavior.
> [!NOTE]
> The process below is for creating installation media to image new Microsoft Teams Rooms devices. Existing devices, by default, update automatically from Windows Update and the Windows Store.

1. Download the [CreateSrsMedia.ps1 script](https://go.microsoft.com/fwlink/?linkid=867842).
2. Run the CreateSrsMedia.ps1 script from an elevated prompt on a Windows machine.
3. Follow the script's instructions to create a Microsoft Teams Rooms USB setup disk.

> [!TIP]
> Each time the CreateSrsMedia.ps1 script starts, the screen output will include the name of a log file or transcript for the session. If there are issues with running the script, make sure to have a copy of that transcript available when requesting support.

When finished, safely eject and remove the USB disk from your computer and proceed to [Install Windows and the Microsoft Teams Rooms console app](console.md#Reimage).

## Install Windows and the Microsoft Teams Rooms console app
<a name="Reimage"> </a>

You now need to apply the setup media you've created. The target device will run as an appliance and the default user will be set to only run the Microsoft Teams Rooms app.

> [!IMPORTANT]
> Installation is supported only on [certified Microsoft Teams Rooms on Windows hardware](certified-hardware.md?tabs=Windows). Microsoft will not provide any support for non-certified hardware, even if installation succeeds.

1. If the target device will be installed in a dock (e.g., a Surface Pro), disconnect it from the dock.

2. Ensure the target device is not connected to the network.

3. Ensure the target device is connected to AC power.

4. Plug your USB setup disk into the target device.

5. Boot to the USB setup disk. Refer to the manufacturer instructions. If your target device is a Surface Pro, use the following steps to boot to the USB setup disk:

    a. Press and continue to hold the volume down (-) button.

    b. Press and release the power button.

    c. Once Windows setup is booted, release the volume down (-) button.

6. The system will shut down once installation is complete.

After the system has shut down, it is safe to remove the USB setup disk. At this point, you can place the target device in its dock (if using a dock-based product), attach the peripherals needed for your meeting room, and connect to the network. Refer to the manufacturer instructions.

> [!NOTE]
> Software updates for Microsoft Teams Rooms are automatically downloaded from the Microsoft Store for Business. See [Prerequisites for Microsoft Store for Business and Education](/microsoft-store/prerequisites-microsoft-store-for-business) to verify that the room console will be able to access the store and self-update.  

### Selecting a language

In Creator's Update, you'll need to use the ApplyCurrentRegionAndLanguage.ps1 script in scenarios where implicit language selection does not provide the user with the actual application language they want (e.g., they want the console app to come up in French, but it's coming up in English).

> [!NOTE]
> The following instructions work only for consoles created using Windows Creator's Update (Windows 10 20H1) or later.

### To apply your desired language

1. Switch to Admin mode.

2. Select the **Start** menu.

3. Select the gear icon to launch the **Settings** app.

4. Select the **Time &amp; language** tab.

5. Select **Language &amp; region**.

6. Under Regional format, select **Recommended**.

7. Under Preferred languages, select **Add a language**.

8. Select the language you want to add.

9. Select **Next**.

10. Under Language preferences, check **Set as my Windows display language**.

11. Select **Install**.

12. Verify that the language you added is at the top of the Preferred languages list and has become the Windows display language.

13. Optionally, if you want to remove any languages:

    a. Select the three-dot menu next to the language you wish to remove.

    b. Select **Remove**.

14. Sign out.

15. Sign back in to your admin account.

16. Start an elevated command prompt.

17. Run the following command:
    ```PowerShell
    powershell -executionpolicy unrestricted c:\Rigel\x64\scripts\provisioning\scriptlaunch.ps1 ApplyCurrentRegionAndLanguage.ps1
    ```

18. Restart the system.

Your desired language is now applied to the Microsoft Teams Rooms app.

> [!NOTE]
> Optionally, if you want to set a different language on your Windows admin settings from the language you applied to the Microsoft Teams Rooms app, repeat steps 1 to 15 only.

## Initial set up of the console
<a name="Initial"> </a>

After Windows is installed, the Microsoft Teams Rooms app will go into its initial Setup process.
  
1. The End user license screen appears. Select **Accept** to continue 
1. The User Account screen appears. Enter the Microsoft Teams/ Microsoft Exchange Resource account sign-in address (in user@domain format) of the room account to be used with the console.
1. Enter the password for the room account, and re-enter it to verify.
1. Select **Next**.
1. Select **Finish**.

The Microsoft Teams Rooms app should signing in to Microsoft Teams with the credentials entered above, and should also begin syncing its calendar with Exchange using those same credentials. For details on using Teams Rooms, refer to the [Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2).

> [!IMPORTANT]
> Microsoft Teams Rooms relies on the presence of certified console hardware. Even a correctly created image containing the Microsoft Teams Rooms console app will not boot past the initial setup procedure unless the console hardware is detected. For Surface Pro based solutions, the Surface Pro must be connected to its accompanying dock hardware to pass this check. For more information about supported hardware, see [Supported hardware](console.md#supported-hardware).

> [!NOTE]
> Some non-English language users may need a physical keyboard connected to the console during initial setup in the event that symbols are not supported on the touch keyboard.

### Install a private CA certificate on the console
<a name="Certs"> </a>
> [!NOTE]
> The following only applies if connecting Teams Rooms to on-premise Exchange server.
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

After the system has shut down, it is safe to remove the USB setup disk. A drive image can now be captured from this device, for use in bulk deployment of identical hardware if necessary.


## See also
<a name="SeeAlso"> </a>

[Plan for Microsoft Teams Rooms](rooms-plan.md)
  
[Deploy Microsoft Teams Rooms](rooms-deploy.md)
  
[Configure a Microsoft Teams Rooms console](console.md)
  
[Manage Microsoft Teams Rooms](rooms-manage.md)

