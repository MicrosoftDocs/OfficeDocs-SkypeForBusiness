---
title: Microsoft Teams Rooms maintenance and operations
ms.author: tonysmit
author: tonysmit
ms.reviewer: rachelan
ms.date: 10/04/2023
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.subservice: itpro-rooms
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: Learn about managing Microsoft Teams Rooms.
---

# Microsoft Teams Rooms maintenance and operations
 
 
Microsoft Teams Rooms is Microsoft's conferencing solution designed to transform your meeting room into a rich, collaborative experience. Users will enjoy its familiar Microsoft Teams interface and IT administrators will appreciate an easily deployed and managed Windows app. Microsoft Teams Rooms is designed to leverage existing equipment for ease of installation to bring Microsoft Teams into your meeting room. The below information provides support for managing and operating Teams Rooms on Windows devices.
    
## Collecting logs on Microsoft Teams Rooms
<a name="Logs"> </a>

To collect logs in Teams admin center, go to **Teams devices > Teams Rooms on Windows**. Select the display name of the device you want logs for. In the top panel, select "Download device logs." Once you confirm, the logs will be ready for download in the History tab after a few minutes.

You can also use PowerShell to collect logs. You must invoke the log collection script that ships with the Microsoft Teams Rooms app. In [Admin mode](rooms-operations.md), start an elevated command prompt, and issue the following command:
  
```PowerShell
powershell -ExecutionPolicy unrestricted c:\rigel\x64\scripts\provisioning\ScriptLaunch.ps1 CollectSrsV2Logs.ps1
```

The logs will be output as a ZIP file in c:\rigel.

### Managing Disk Space
<a name="Space"> </a>

Downloaded logs on the device can take up disk space. If logs are not regularly cleaned up, they can interfere with the normal functionality of the room. Teams Rooms deletes downloaded logs after 30 days. IT admins can override the log clean-up using the device registry setting.

|Setting|Allows|
|:-----|:-----|
|HKLM\SOFTWARE\Microsoft\PPI\SkypeSettings\LogCleanupAgeThreshold   |Cleans up logs after 30 days.   |

## Front of Room display settings
<a name="Display"> </a>

Configure the settings of your Front of Room display(s) to support Consumer Electronics Control(CEC) or enable PC Mode.
  
If you desire a front of room display to automatically switch to Teams Rooms when it wakes from standby mode, certain conditions must be met. This feature is optional but supported by Microsoft Teams Rooms software, provided underlying hardware supports the feature. A consumer TV used as a front of room display needs to support the Consumer Electronics Control (CEC) feature of HDMI.  Depending on the dock or console selected (which might not support CEC, refer to manufacturer support documentation), a controller such as an [HD-RX-4K-201-C-E](https://www.crestron.com/Products/Video/HDMI-Solutions/HDMI-Extenders/HD-RX-4K-210-C-E) from Crestron, the [DL-UHDILC](https://secure.libertycable.com/product_details.php?pitem=DL-UHDILC) from Liberty, or [Extron HD CTL 100](https://www.extron.com/article/hdctl100ad) from Extron may be needed to enable the desired behavior.

### Scale and resolution

To get Teams Rooms designed experience, your Front of Room displays need to meet resolution and scale requirements.

To set the scale and resolution of your Front of Rooms displays remotely, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md).

To set the scale and resolution manually in the Teams Rooms admin settings:

1. On your Teams Room, switch to [admin mode](#switching-to-admin-mode-and-back-when-the-microsoft-teams-rooms-app-is-running).

2. Select the start icon. Then **Settings > System > Display**.

3. Go to **Scale and layout**, then **Change the size of text, apps, and other items**, and set the scaling to 100%.

4. Set the display resolution to 1080p. If you have dual monitors, set the scale and resolution for both screens.

5. Next, select the start icon and enter **Command prompt**. Select **Run as administrator**.

6. Run the following command:

   ```powershell
   Powershell -ExecutionPolicy Unrestricted c:\Rigel\x64\scripts\provisioning\scriptlaunch.ps1 ApplyCurrentDisplayScaling.ps1 
   ```

7. Restart the device.
  
## Microsoft Teams Rooms Reset (Factory Restore)
<a name="Reset"> </a>

If Microsoft Teams Rooms isn't running well, performing a factory reset might help. To do this, use the [Microsoft Teams Rooms recovery tool](recovery-tool.md) and follow the factory restore instructions.

> [!NOTE]
> There is a known issue where the Microsoft Teams Rooms can become unusable if the **Keep my files - Removes Apps and settings, but keeps your personal files** option is selected during the Windows Reset process. Do *not* use this option.

## Supported Remote Options
<a name="RemoteOptions"> </a>

The following table summarizes the possible remote operations and the methods you can use to accomplish them.
  


|Workgroup|Not domain joined|Domain joined|
|:-----|:-----|:-----|
|Restart   |Teams admin center  <br/> Remote desktop  <br/> Remote PowerShell   | <br/>Remote desktop (requires further configuration)  <br/> Remote PowerShell (requires further configuration)  <br/> Configuration Manager   |
|Update OS   |Windows Update   |Windows Update  <br/> WSUS   |
|App update   |Windows Store   |Windows Store  <br/> Configuration Manager   |
|Account Config   |Teams admin center   |Teams admin center   |
|Access logs   |Teams admin center  <br/> PowerShell   |Teams admin center <br/> PowerShell  |

## Configuring Group Policy for Microsoft Teams Rooms
<a name="GroupPolicy"> </a>

This section covers system settings that Microsoft Teams Rooms depends on to function properly. 

Joining Teams Rooms to an Active Directory domain provides the following benefits:

- Domain-joining Teams Rooms enables you to grant domain users and groups administrative rights. By doing so, you will not have to remember the local machine level administrator account password.

- You can deploy Windows Quality of Service configuration to Teams Rooms.

When you join Teams Rooms to a domain, it is required that you create a separate Organizational Unit (OU), so that you can provide Group Policy Object (GPO) exclusions to the OU where all Teams Rooms objects reside. Disable all GPO inheritance so that unsupported Group Policy settings do not get applied to Teams Rooms. Create machine objects in the OU before joining Teams Rooms to the domain to assure that Group Policies applied to the default computers OU are not applied.

> [!NOTE]
> Even if you create a separate OU and block inheritance, there are some group policies which could cause issues if they have No Override set. A Group Policy with No Override set beats an OU with Block Policy Inheritance set.

Many organizations have the following GPOs, which affect Teams Rooms functionality. Ensure that you override or block the inheritance of these:

- Timeout of logon sessions (auto lockout)
- Power management related policies
- Requiring additional authentication steps
- Denying access to local drives
- Prompting users for slow network connections
- Start a certain program at logon
- Create another domain user account on all domain-joined machines
- Push Windows Update to Teams Rooms

When joining Microsoft Teams Rooms to a domain, ensure that your group policies don't override the settings in the following table.

|Setting|Allows|
|:-----|:-----|
|HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon AutoAdminLogon = (REG_SZ) 1   |Enables Microsoft Teams Rooms to boot up   |
|Power Management -\> On AC, turn screen off after 10 minutes  <br/> Power Management -\> On AC, never put system to sleep   |Enables Microsoft Teams Rooms to turn off attached displays and wake up automatically   |
|net accounts /maxpwage:unlimited  <br/> Or equivalent means of disabling password expiration on the local account. Failure to do this will eventually cause the Skype account to fail logon complaining about an expired password. Note that this impacts all local accounts on the machine, and thus failure to set this will also cause the administrative account on the box to eventually expire as well.   |Enables Skype account to always log in   |

> [!NOTE]
> When Microsoft Teams Rooms is compatible with the next version of Windows 10 OS, Teams Rooms automatically updates to the next version through Windows Update. Microsoft Teams Rooms should not be upgraded to the next release of Windows 10 manually or via enabling Windows Update for Business (WUFB) group policies “Select the Windows readiness level for the updates you want to receive” and "Select when Preview Builds and Feature Updates are received" through GPO. Teams Rooms with these group policies enabled is known to run into issues with Windows 10 OS updates.

## Remote Management using PowerShell
<a name="RemotePS"> </a>

You can perform the following management operations remotely by using PowerShell (see the table below for script samples):
  
- Get attached devices
- Get app status
- Get system info
- Reboot system
- Retrieve logs
- Transfer files (requires a domain-joined Microsoft Teams Rooms)

> [!NOTE]
> This functionality is off by default. You need to enable remote PowerShell for your environment on the Microsoft Teams Rooms system to perform the operations below. Refer to the documentation on **[Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting)** for information about how to enable remote PowerShell.

For example, you can enable Remote PowerShell as follows:
  
1. Sign in as Admin on a Microsoft Teams Rooms device.
2. Open an elevated PowerShell command prompt.
3. Enter the following command: `Enable-PSRemoting -SkipNetworkProfileCheck -Force`
4. Open the Local Security Policy and add the *Administrators* security group to **Security Settings** > **Local Policies** > **User Rights Assignment** > **Access this computer from the network**.

To perform a management operation:
  
1. Sign in to a PC with account credentials that have permission to run PowerShell commands on a Microsoft Teams Rooms device.
2. Open a regular PowerShell command prompt on the PC.
3. Copy the command text from the table below and paste it at the prompt.
4. Replace  `<Device fqdn>` fields with FQDN values appropriate to your environment.
5. Replace  *\<path\>*  with the file name and local path of the master SkypeSettings.xml configuration file (or Theme image).
    
To Get Attached Devices
  
```PowerShell
invoke-command {Write-Host "VIDEO DEVICES:" 
gwmi -Class Win32_PnPEntity | where {$_.PNPClass -eq "Image" -or $_.PNPClass -eq "Camera"} | Format-Table Name,Status,Present; Write-Host "AUDIO DEVICES:" 
gwmi -Class Win32_PnPEntity | where {$_.PNPClass -eq "Media"} | Format-Table Name,Status,Present; Write-Host "DISPLAY DEVICES:" 
gwmi -Class Win32_PnPEntity | where {$_.PNPClass -eq "Monitor"} | Format-Table Name,Status,Present} -ComputerName <Device fqdn>
```

Get App Status
  
```PowerShell
invoke-command { $package = get-appxpackage -User Skype -Name Microsoft.SkypeRoomSystem; if ($package -eq $null) {Write-host "SkypeRoomSystems not installed."} else {write-host "SkypeRoomSystem Version : " $package.Version}; $process = Get-Process -Name "Microsoft.SkypeRoomSystem" -ErrorAction SilentlyContinue; if ($process -eq $null) {write-host "App not running."} else {$process | format-list StartTime,Responding}}  -ComputerName <Device fqdn>
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

Push an XML configuration file (or theme graphic)
  
```XML
$movefile = "<path>";
$targetDevice = "\\<Device fqdn> \Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState\SkypeSettings.xml"; 
Copy-Item $movefile $targetDevice 
```

## Software updates
<a name="SWupdate"> </a>

By default, Microsoft Teams Rooms connects to Windows Update to retrieve operating system and USB peripheral device firmware updates, and installs them outside of configured business hours. You can configure business hours by signing into the administrator account and running the **Settings** app.
  
If you want to manage updates manually, and are unable to follow the normal procedure for [Microsoft Store for Business](https://businessstore.microsoft.com/store) to [Distribute offline apps](/microsoft-store/distribute-offline-apps), you can acquire and run the latest MTR-Update script from [Manually update a Microsoft Teams Rooms device](/microsoftteams/rooms/manual-update).

By default, Microsoft Teams Rooms attempts to connect to the Windows Store to get the latest version of Microsoft Teams Rooms software. Therefore, Teams Rooms requires regular internet access. Before contacting Microsoft with support issues, be sure Microsoft Teams Rooms is loaded with the latest version of the app.



## Admin mode and device management
<a name="AdminMode"> </a>

Some management functions, like manually installing a private CA certificate, require placing Teams Rooms in Admin mode. 
  
### Switching to Admin mode and back when the Microsoft Teams Rooms app is running

1. Hang up any ongoing calls, and return to the home screen.
2. Select the Gear icon and bring up the menu (options are **Settings**, **Accessibility**, and **Restart Device** ).
3. Select **Settings**.
4. Enter the Administrator password. The Setup screen will appear.  If the device isn't domain-joined, the local administrative account (username "Admin") will be used by default. The default password for this account is 'sfb'. Change this password as soon as possible. If the machine is domain-joined, you can sign in with an appropriately privileged domain account.
5. Select **Windows Settings** in the left column.
6. Log in to the desktop with your administrative credentials. You'll have the necessary privileges to manage the device.
7. Perform the necessary administrative tasks.
8. Restart the machine when you're finished.
    
The console is now back in its normal operation mode. The following procedure requires you to attach a keyboard to the device if one is not already attached. 

### Clearing the Teams Rooms on Windows Client Cache

1. Plug in a physical keyboard to the Teams Rooms device.
2. Press the **Windows** key five times in rapid succession. This will bring you to the Windows logon screen.
3. Log in to the desktop with your administrative credentials.
4. Sign the **Skype** user out of the account.
   1. Open **Task Manager**.
   1. Select the **Users** tab.
   1. Right click the **Skype** user.
   1. Select **Sign Off**.
5. Navigate to `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalCache\Roaming\Microsoft\`
6. Delete the **Teams** folder.
7. Restart the Teams Rooms device.
8. Sign in and restart again, once the Teams Room's interface has appeared.

### Changing the Teams Room console language or date & time format

1. Switch to Admin mode.
2. Select the Start menu.
3. Select the gear icon to launch the **Settings** app.
4. Select **Time &amp; language**.
5. Select **Language &amp; region**.    
6. Select **Add a language**.    
7. Select the language you wish to add.    
8. Install language features.
9. Do not check **Set as my Windows display language**      
10. Select **Install**.    
11. Select the language you just added to the "Languages" list.    
12. Set as default- Move up arrow to set default
13. For any languages you wish to remove:
    1. Select the language you wish to remove.
    1. Select Remove.
14. If you wish to change the date & time format, modify the location selection tied to **Regional format** until Windows displays as desired
14. Start an elevated command prompt.
15. Run the following command: 

    ```PowerShell
    powershell -executionpolicy unrestricted c:\Rigel\x64\scripts\provisioning\scriptlaunch.ps1 ApplyCurrentRegionAndLanguage.ps1
    ```

1. Restart the system.
    
Your desired language is now applied to the Microsoft Teams Rooms console.
 
### Switching to Admin Mode and back when the Microsoft Teams Rooms app crashes

1. Press the Windows key five times in rapid succession. This will bring you to the Windows logon screen. 
2. Log in to the desktop with your administrative credentials.
3. Perform the necessary administrative tasks.
4. Restart the machine when you're finished.

    > [!NOTE]
    > This method doesn't log the Skype user off or gracefully terminate the app, but you'd use it if the app wasn't responding and the other method wasn't available. 

   The console restarts into its normal operation mode, running the Microsoft Teams Rooms app. You can remove the keyboard, if you attached one to complete this procedure.

## Troubleshooting tips
<a name="TS"> </a>

- Meeting invitations might not appear when sent across domain boundaries (for example, between two companies). In such cases, IT admins should decide whether to allow external users to schedule a meeting. See the article for the Exchange PowerShell cmdlet [Set-CalendarProcessing](/powershell/module/exchange/set-calendarprocessing), specifically the 'ProcessExternalMeetingMessages' parameter.
- Microsoft Teams Rooms doesn't support Exchange AutoDiscover redirects via Exchange 2010.
- In general, it's a good practice for IT admins to disable any audio endpoints they don't intend to use.
- In the event that a mirror image is displayed in room preview, the IT admin can correct by cycling camera power or flipping the image orientation using the camera settings.
- Loss of console touchscreen access has been known to occur. In such cases, the issue is sometimes resolved by restarting Teams Rooms.
- Loss of local audio when connecting a PC to console via wired ingest has been known to occur. In such cases, restarting the PC can resolve the local audio playback issue.


