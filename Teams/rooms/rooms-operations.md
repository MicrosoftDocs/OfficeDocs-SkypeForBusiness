---
title: Microsoft Teams Rooms maintenance and operations
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: kramachandra
ms.date: 09/30/2024
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
description: Learn about managing Microsoft Teams Rooms.
---

# Microsoft Teams Rooms on Windows Maintenance and Operations
 
 
Microsoft Teams Rooms is Microsoft's conferencing solution designed to transform your meeting room into a rich, collaborative experience. Users enjoy its familiar Microsoft Teams interface and IT administrators appreciate an easily deployed and managed Windows app. Microsoft Teams Rooms is designed to use existing equipment for ease of installation to bring Microsoft Teams into your meeting room. This document provides support for managing and operating Teams Rooms on Windows devices.
 
## Collecting logs on Microsoft Teams Rooms
<a name="Logs"> </a>

To collect logs in the Pro Management Portal, go to **Rooms** and select the display name of the device you want logs for. In the actions panel, select "Log Collection" and select "Run". Once you confirm the desired logs, the logs will be ready for download in the Activity tab after a few minutes.

To collect logs in Teams admin center, go to **Teams devices > Teams Rooms on Windows**. Select the display name of the device you want logs for. In the top panel, select "Download device logs." Once you confirm, the logs will be ready for download in the History tab after a few minutes.

You can also use PowerShell to collect logs. You must invoke the log collection script that ships with the Microsoft Teams Rooms app. In [Admin mode](rooms-operations.md), start an elevated command prompt, and issue the following command:
 
```PowerShell
powershell -ExecutionPolicy unrestricted c:\rigel\x64\scripts\provisioning\ScriptLaunch.ps1 CollectSrsV2Logs.ps1
```

The logs are output as a ZIP file in c:\rigel.

## Front of Room Display Configuration
<a name="Display"> </a>

### Display Sleep/Wake Behavior
Teams Rooms on Windows devices are configured out of the box to send no video signal after 10 minutes of inactivity, at which time the Windows PC will stop sending video from its video outputs. You need to configure front of room displays in PC mode if available or set displays to automatically sleep/wake on an inactive/active HDMI video signal, consult your display OEM documentation for guidance. If the display doesn't support any of the mentioned functionalities, you may be able to use a display controller to enable the desired behavior over CEC or RS-232 control:
- [Crestron HD-CTL-101](https://www.crestron.com/Products/Control-Hardware-Software/Hardware/Control-Modules/HD-CTL-101)
- [Liberty DL-UHDILC](https://secure.libertycable.com/product_details.php?pitem=DL-UHDILC)
- [Extron HD CTL 100](https://www.extron.com/article/hdctl100ad)

If the displays aren't visible to the Windows PC when in their sleep state, Teams Rooms may report display disconnected alerts messages in Teams Admin Center and the Pro Management Portal and you may experience instability with your Teams Rooms devices. Windows believes the displays are physically disconnected. Consult your display manufacturer documentation for how to configure your displays in a way that keeps the HDMI sync with the Windows PC. If unsuccessful, powered Extended Display Identification Data (EDID) emulators/minders can be used to mitigate the instability and prevent monitoring alerts, several options are listed:

- [Extron EDID 101H 4K PLUS](https://www.extron.com/product/edid101h4kplus)
- [StarTech EDID Emulator](https://www.startech.com/en-us/audio-video-products/vsedidhd)
- [Crestron HD-CTL-101](https://www.crestron.com/Products/Control-Hardware-Software/Hardware/Control-Modules/HD-CTL-101)

### Display resolution and scaling

Teams Rooms on Windows support many resolutions, you may find you need to specify the resolution and scale settings to meet your desired configuration. Resolution can be set remotely, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md) or manually with these steps:

1. On your Teams Room, switch to [admin mode](#switching-to-admin-mode-and-back-when-the-microsoft-teams-rooms-app-is-running)
2. Select the start icon. Then **Settings > System > Display**
3. Go to **Scale and layout**, then **Change the size of text, apps, and other items**, and set the scaling to 100%
4. Set the display resolution to as desired. If you have dual monitors, set the scale and resolution for both screens
5. Next, select the start icon and enter **Command prompt**. Select **Run as administrator**
6. Run the following command:
 ```powershell
 Powershell -ExecutionPolicy Unrestricted c:\Rigel\x64\scripts\provisioning\scriptlaunch.ps1 ApplyCurrentDisplayScaling.ps1 
 ```
7. Restart the device


## Microsoft Teams Rooms Reset & Factory Restore
<a name="Reset"> </a>

### Simple Reset
If Microsoft Teams Rooms isn't running well, performing a reset might help. Open the Teams Rooms on Windows settings and select **Reset Device** to clear the device credentials and return the Teams Rooms application to default settings.

### Factory Reset
If the basic reset doesn't resolve your issue, you may need to do a full factory reset. We recommend using the recovery media available from your Teams Rooms on Windows OEM, however, you can also use the [Microsoft Teams Rooms recovery tool](recovery-tool.md) and follow the factory restore instructions.


## Software updates
<a name="SWupdate"> </a>

By default, Microsoft Teams Rooms connects to Windows Update to retrieve operating system and USB peripheral device firmware updates, and installs them outside of configured business hours. For the Teams Rooms application, your device connects to the Windows Store to get the latest version of the Microsoft Teams Rooms software. Before contacting Microsoft with support issues, be sure Microsoft Teams Rooms is loaded with the latest version of the app to ensure your device is in a supported state.

If you're trying to update a severely out of date Teams Rooms on Windows device, you can run this tool which that updates both the Windows operating system and Teams Rooms applications to the latest versions automatically: [Microsoft Teams Rooms Provisioning Tool](https://aka.ms/mtrp/mtrpprovisioningtool)

If you want to manage updates manually, you can acquire and run the latest MTR-Update script from [Manually update a Microsoft Teams Rooms device](/microsoftteams/rooms/manual-update).

## Switching to Admin mode
<a name="AdminMode"> </a>

### Switching to Admin mode and back when the Microsoft Teams Rooms app is running

1. Hang up any ongoing calls, and return to the home screen.
2. Select the Gear icon and bring up the menu (options are **Settings**, **Accessibility**, and **Restart Device** ).
3. Select **Settings**.
4. Enter the Administrator password. The Setup screen appears. If the device isn't domain-joined, the local administrative account (username "Admin") is used by default. The default password for this account is 'sfb'. Change this password as soon as possible. If the machine is domain-joined, you can sign in with an appropriately privileged domain account.
5. Select **Windows Settings** in the left column.
6. Log in to the desktop with your administrative credentials. You have the necessary privileges to manage the device.
7. Perform the necessary administrative tasks.
8. Restart the machine when you're finished.
 
The console is now back in its normal operation mode. The following procedure requires you to attach a keyboard to the device if one isn't already attached. 

### Switching to Admin Mode and back when the Microsoft Teams Rooms app is frozen

1. Press the Windows key five times in rapid succession. To access the Windows logon screen. 
2. Log in to the desktop with your administrative credentials.
3. Perform the necessary administrative tasks.
4. Restart the machine when you're finished.

 > [!NOTE]
 > This method doesn't log the Skype user off or gracefully terminate the app, but you'd use it if the app wasn't responding and the other method wasn't available. 

 The console restarts into its normal operation mode, running the Microsoft Teams Rooms app. You can remove the keyboard, if you attached one to complete this procedure.

## Clearing the Teams Rooms on Windows Cache

To clear cache using the Pro Management Portal, go to **Rooms** and select the display name of the device you want to clear the cache on. In the actions panel, select "Restart device-Clear cache", select "Run", check the "Delete Teams cache?" box, and select "Run". Your Teams Room clears its cache and reboot.

You can also perform this task directly on the device with these steps:

1. Switch to Admin mode
2. Open Windows Explorer and follow the instructions for your app version:
3. If running Teams Rooms on Windows 4.19.82.0 or earlier:
4. Navigate to: `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalCache\Roaming\Microsoft\`
5. Delete the **Teams** folder
6. If running Teams Rooms 5.0.0 or newer:
7. Navigate to: `C:\Users\Skype\AppData\Local\Packages\MSTeamsRooms_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams`
8. Delete everything inside the MSTeams folder
9. Restart the Teams Rooms device and allow it to return to the Teams Rooms interface

## Changing the Teams Rooms console language or date & time format

1. Switch to Admin mode
2. Select the **Start** menu
3. Select the gear icon to launch the **Settings** app
4. Select **Time &amp; language** tab
5. Select **Language &amp; region**
6. Under Regional format, select **Recommended**
7. Under Preferred languages, select **Add a language**
8. Select the language you want to add
9. Select **Next**
10. Under Language preferences, check **Set as my Windows display language**
11. Select **Install**
12. Verify that the language you added is at the top of the Preferred languages list and is the Windows display language
13. Optionally, if you want to remove any languages:
 1. Select the three-dot menu next to the language you wish to remove
 1. Select **Remove**
14. Sign out
15. Sign back in to your admin account
16. Start an elevated command prompt
17. Run the following command
```PowerShell
  powershell -executionpolicy unrestricted c:\Rigel\x64\scripts\provisioning\scriptlaunch.ps1 ApplyCurrentRegionAndLanguage.ps1
```
18. Restart the system

Your desired language is now applied to the Microsoft Teams Rooms app.



## Configuring Group Policy for Microsoft Teams Rooms
<a name="GroupPolicy"> </a>

This section covers system settings that Microsoft Teams Rooms depends on to function properly. 

Joining Teams Rooms to an Active Directory domain provides the following benefits:

- Domain-joining Teams Rooms enables you to grant domain users and groups administrative rights. By doing so, you don't need to remember the local machine level administrator account password.

- You can deploy Windows Quality of Service configuration to Teams Rooms.

When you join Teams Rooms to a domain, you must create a separate Organizational Unit (OU), to provide Group Policy Object (GPO) exclusions to where all Teams Rooms objects reside. Disable all GPO inheritance so that unsupported Group Policy settings don't get applied to Teams Rooms. Create machine objects in the OU before joining Teams Rooms to the domain to assure that Group Policies applied to the default computers OU aren't applied.

> [!NOTE]
> Even if you create a separate OU and block inheritance, there are some group policies which could cause issues if they have No Override set. A Group Policy with No Override set beats an OU with Block Policy Inheritance set.

Many organizations have the following GPOs, which affect Teams Rooms functionality. Ensure that you override or block the inheritance of:

- Timeout of logon sessions (auto lockout)
- Power management related policies
- Requiring extra authentication steps
- Denying access to local drives
- Prompting users for slow network connections
- Start a certain program at logon
- Create another domain user account on all domain-joined machines
- Push Windows Update to Teams Rooms

When joining Microsoft Teams Rooms to a domain, ensure that your group policies don't override the settings in the following table.

|Setting|Allows|
|:-----|:-----|
|HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon AutoAdminLogon = (REG_SZ) 1 |Enables Microsoft Teams Rooms to boot up |
|Power Management -\> On AC, turn off screen after 10 minutes <br/> Power Management -\> On AC, never put system to sleep |Enables Microsoft Teams Rooms to turn off attached displays and wake up automatically |
|net accounts /maxpwage:unlimited <br/> Or equivalent means of disabling password expiration on the local account. Failure to do this configuration will cause the Skype account to fail logon complaining about an expired password. This impacts all local accounts on the machine, and thus failure to set this configuration will cause the administrative account on the box to eventually expire as well. |Enables Skype account to always log in |

> [!NOTE]
> When Microsoft Teams Rooms is compatible with the next version of Windows 10 OS, Teams Rooms automatically updates to the next version through Windows Update. Microsoft Teams Rooms shouldn't be upgraded to the next release of Windows manually or via enabling Windows Update for Business (WUFB) group policies “Select the Windows readiness level for the updates you want to receive” and "Select when Preview Builds and Feature Updates are received" through GPO. Teams Rooms with these group policies enabled is known to run into issues with Windows OS updates.

### Managing Disk Space
<a name="Space"> </a>

Downloaded logs on the device can take up disk space. If logs aren't regularly cleaned up, they can interfere with the normal functionality of the room. Teams Rooms deletes downloaded logs after 30 days. IT admins can override the log clean-up using the device registry setting.

|Setting|Allows|
|:-----|:-----|
|HKLM\SOFTWARE\Microsoft\PPI\SkypeSettings\LogCleanupAgeThreshold |Cleans up logs after 30 days. |

## Remote Management using PowerShell
<a name="RemotePS"> </a>

You can perform the following management operations remotely by using PowerShell (see the table for script samples):
 
- Get attached devices
- Get app status
- Get system info
- Reboot system
- Retrieve logs
- Transfer files (requires a domain-joined Microsoft Teams Rooms)

> [!NOTE]
> This functionality is off by default. You need to enable remote PowerShell for your environment on the Microsoft Teams Rooms system to perform the operations listed. Refer to the documentation on **[Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting)** for information about how to enable remote PowerShell.

For example, you can enable Remote PowerShell as follows:
 
1. Sign in as Admin on a Microsoft Teams Rooms device
2. Open an elevated PowerShell command prompt
3. Enter the following command: `Enable-PSRemoting -SkipNetworkProfileCheck -Force`
4. Open the Local Security Policy and add the *Administrators* security group to **Security Settings** > **Local Policies** > **User Rights Assignment** > **Access this computer from the network**

To perform a management operation:
 
1. Sign in to a PC with account credentials that have permission to run PowerShell commands on a Microsoft Teams Rooms device.
2. Open a regular PowerShell command prompt on the PC.
3. Copy the command text from the table and paste it at the prompt.
4. Replace `<Device fqdn>` fields with fully qualified domain name (FQDN) values appropriate to your environment.
5. Replace *\<path\>* with the file name and local path of the master SkypeSettings.xml configuration file (or Theme image).
 
To Get Attached Devices
 
```PowerShell
invoke-command {Write-Host "VIDEO DEVICES:" 
gwmi -Class Win32_PnPEntity | where {$_.PNPClass -eq "Image" -or $_.PNPClass -eq "Camera"} | Format-Table Name,Status,Present; Write-Host "AUDIO DEVICES:" 
gwmi -Class Win32_PnPEntity | where {$_.PNPClass -eq "Media"} | Format-Table Name,Status,Present; Write-Host "DISPLAY DEVICES:" 
gwmi -Class Win32_PnPEntity | where {$_.PNPClass -eq "Monitor"} | Format-Table Name,Status,Present} -ComputerName <Device fqdn>
```

Get App Status
 
```PowerShell
invoke-command { $package = get-appxpackage -User Skype -Name Microsoft.SkypeRoomSystem; if ($package -eq $null) {Write-host "SkypeRoomSystems not installed."} else {write-host "SkypeRoomSystem Version : " $package.Version}; $process = Get-Process -Name "Microsoft.SkypeRoomSystem" -ErrorAction SilentlyContinue; if ($process -eq $null) {write-host "App not running."} else {$process | format-list StartTime,Responding}} -ComputerName <Device fqdn>
```

Get System Info
 
```PowerShell
invoke-command {gwmi -Class Win32_ComputerSystem | Format-List PartOfDomain,Domain,Workgroup,Manufacturer,Model
gwmi -Class Win32_Bios | Format-List SerialNumber,SMBIOSBIOSVersion} -ComputerName <Device fqdn>
```

Reboot System
 
```PowerShell
invoke-command { Shutdown /r /t 0 } -ComputerName <Device fqdn>
```

Retrieve Logs
 
```PowerShell
$targetDevice = "<Device fqdn> "
$logFile = invoke-command {$output = Powershell.exe -ExecutionPolicy Bypass -File C:\Rigel\x64\Scripts\Provisioning\ScriptLaunch.ps1 CollectSrsV2Logs.ps1
Get-ChildItem -Path C:\Rigel\*.zip | Sort-Object -Descending -Property LastWriteTime | Select-Object -First 1} -ComputerName $targetDevice
$session = new-pssession -ComputerName $targetDevice
Copy-Item -Path $logFile.FullName -Destination .\ -FromSession $session; invoke-command {remove-item -force C:\Rigel\*.zip} -ComputerName $targetDevice
```

Push an XML configuration file (or theme graphic).
 
```XML
$movefile = "<path>";
$targetDevice = "\\<Device fqdn> \Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState\SkypeSettings.xml"; 
Copy-Item $movefile $targetDevice 
```
