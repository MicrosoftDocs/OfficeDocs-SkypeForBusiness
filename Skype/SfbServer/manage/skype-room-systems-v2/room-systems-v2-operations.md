---
title: "Skype Room Systems v2 maintenance and operations"
ms.author: jambirk
author: jambirk
ms.reviewer: davgroom
manager: serdars
ms.date: 5/10/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Read this topic to learn about management of Skype Room Systems v2, the next generation of Skype Room Systems."
---

# Skype Room Systems v2 maintenance and operations 
 
Read this topic to learn about management of Skype Room Systems v2, the next generation of Skype Room Systems.
  
Skype Room Systems v2 is Microsoft's latest conferencing solution designed to transform your meeting room into a rich, collaborative Skype for Business experience. Users will enjoy its familiar Skype for Business interface and IT administrators will appreciate an easily deployed and managed Windows 10 Skype Meeting app. Skype Room Systems v2 is designed to leverage existing equipment like LCD panels for ease of installation to bring Skype for Business into your meeting room.
  
With additional configuration, remote management is possible using Microsoft Operations Management Suite (OMS) as described in [Plan Skype Room Systems v2 management with OMS](../../plan-your-deployment/clients-and-devices/oms-management.md), [Deploy Skype Room Systems v2 management with OMS](../../deploy/deploy-clients/with-oms.md), and [Manage Skype Room Systems v2 devices with OMS](oms.md). You may also [Manage a Skype Room Systems v2 console settings remotely with an XML configuration file](xml-config-file.md), which includes applying a Custom display theme. 
  
## Collecting logs on Skype Room Systems v2
<a name="Logs"> </a>

To collect logs, you must invoke the log collection script that ships with the Skype Room Systems v2 app. In Admin mode, start an elevated command prompt, and issue the following command:
  
```
powershell -ExecutionPolicy unrestricted c:\rigel\x64\scripts\provisioning\ScriptLaunch.ps1 CollectSrsV2Logs.ps1
```

The logs will be output as a ZIP file in c:\rigel.
  
## Front of Room Display Settings
<a name="Display"> </a>

Configure the Front of Room display to Extended mode. Doing so will ensure that the console UI is not duplicated on that display when you cycle power on the display.
  
> [!NOTE]
> A consumer TV used as a front of room display needs to support/enable the Consumer Electronics Control (CEC) feature of HDMI so that it can switch automatically to an active video source from standby mode. This feature is not supported on all TVs. 
  
## Skype Room Systems v2 Reset (Factory Restore)
<a name="Reset"> </a>

If Skype Room Systems v2 isn't running well, performing a factory reset might help. This can be done in the Settings app on the **Recovery** tab. Beneath **Reset this PC**, select **Get started**, and then **Remove everything**. Follow the remaining prompts to reset the device.
  
> [!NOTE]
> There is a known issue where the Skype Room Systems v2 can become unusable if the **Keep my files - Removes Apps and settings, but keeps your personal files** option is selected during the Windows Reset process. Do _not_ use this option.
  
## Supported Remote Options
<a name="RemoteOptions"> </a>

The following table summarizes the possible remote operations and the methods you can use to accomplish them.
  

|**Workgroup**|**Not domain joined**|**Domain joined**|
|:-----|:-----|:-----|
|Restart  <br/> |Remote desktop  <br/> Remote Powershell  <br/> |Remote desktop (requires further configuration)  <br/> Remote Powershell (requires further configuration)  <br/> SCCM  <br/> |
|Update OS  <br/> |Windows Update  <br/> |Windows Update  <br/> WSUS  <br/> |
|App update  <br/> |Windows Store  <br/> |Windows Store  <br/> SCCM  <br/> |
|Skype Account Config  <br/> |Not currently supported  <br/> |Not currently supported  <br/> |
|Access logs  <br/> |Not currently supported  <br/> |Not currently supported  <br/> |
   
## Configuring Group Policy for Skype Room Systems v2
<a name="GroupPolicy"> </a>

This section covers system settings that Skype Room Systems v2 depends on to function properly. When joining Skype Room Systems v2 to a domain, ensure that your group policy doesn't override the settings in the following table.
  

|**Setting**|**Allows**|
|:-----|:-----|
|HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon AdminAutoLogon = (REG_SZ) 1  <br/> |Enables Skype Room Systems v2 to boot up  <br/> |
|Power Management -\> On AC, turn screen off after 10 minutes  <br/> Power Management -\> On AC, never put system to sleep  <br/> |Enables Skype Room Systems v2 to turn off attached displays and wake up automatically  <br/> |
|net accounts /maxpwage:unlimited  <br/> Or equivalent means of disabling password expiration on the local account. Failure to do this will eventually cause the Skype account to fail logon complaining about an expired password. Note that this impacts all local accounts on the machine, and thus failure to set this will also cause the administrative account on the box to eventually expire as well.  <br/> |Enables Skype account to always log in  <br/> |
   
Transferring files using Group Policies is discussed in [Configure a File Item](https://technet.microsoft.com/library/cc772536%28v=ws.11%29.aspx).
  
## Remote Management using PowerShell
<a name="RemotePS"> </a>

You can perform the following management operations remotely by using PowerShell (see the table below for script samples):
  
- Get attached devices
    
- Get app status
    
- Get system info
    
- Reboot system
    
- Retrieve logs
    
- Transfer files (requires a domain-joined Skype Room Systems v2)
    
> [!NOTE]
> This functionality is off by default. You need to enable remote PowerShell for your environment on the Skype Room Systems v2 system to perform the operations below. Refer to the documentation on **[Enable-PSRemoting](https://technet.microsoft.com/library/hh849694.aspx)** for information about how to enable remote PowerShell.
  
For example, you can enable Remote PowerShell as follows:
  
1. Sign in as Admin on a Skype Room Systems v2 device.
    
2. Open an elevated PowerShell command prompt.
    
3. Enter the following command: Enable-PSRemoting -force
    
To perform a management operation:
  
1. Sign in to a PC with account credentials that have permission to run PowerShell commands on a Skype Room Systems v2 device.
    
2. Open a regular PowerShell command prompt on the PC.
    
3. Copy the command text from the table below and paste it at the prompt.
    
4. Replace  `<Device fqdn>` fields with FQDN values appropriate to your environment.
    
5. Replace  *\<path\>*  with the file name and local path of the master SkypeSettings.xml configuration file (or Theme image).
    
To Get Attached Devices
  
```
invoke-command {Write-Host "VIDEO DEVICES:" 
gwmi -Class Win32_PnPEntity | where {$_.PNPClass -eq "Image"} | Format-Table Name,Status,Present; Write-Host "AUDIO DEVICES:" 
gwmi -Class Win32_PnPEntity | where {$_.PNPClass -eq "Media"} | Format-Table Name,Status,Present; Write-Host "DISPLAY DEVICES:" 
gwmi -Class Win32_PnPEntity | where {$_.PNPClass -eq "Monitor"} | Format-Table Name,Status,Present} -ComputerName <Device fqdn>
```

Get App Status
  
```
invoke-command { $package = get-appxpackage -User Skype -Name Microsoft.SkypeRoomSystem; if ($package -eq $null) {Write-host "SkypeRoomSystems not installed."} else {write-host "SkypeRoomSystem Version : " $package.Version}; $process = Get-Process -Name "Microsoft.SkypeRoomSystem" -ErrorAction SilentlyContinue; if ($process -eq $null) {write-host "App not running."} else {$process | format-list StartTime,Responding}}  -ComputerName <Device fqdn>
```

Get System Info
  
```
invoke-command {gwmi -Class Win32_ComputerSystem | Format-List PartOfDomain,Domain,Workgroup,Manufacturer,Model
gwmi -Class Win32_Bios | Format-List SerialNumber,SMBIOSBIOSVersion} -ComputerName <Device fqdn>
```

Reboot System
  
```
invoke-command { Shutdown /r /t 0 } -ComputerName <Device fqdn>
```

Retrieve Logs
  
```
$targetDevice = "<Device fqdn> "
$logFile = invoke-command {$output = Powershell.exe -ExecutionPolicy Bypass -File C:\Rigel\x64\Scripts\Provisioning\ScriptLaunch.ps1 CollectSrsV2Logs.ps1
Get-ChildItem -Path C:\Rigel\*.zip | Sort-Object -Descending -Property LastWriteTime | Select-Object -First 1} -ComputerName $targetDevice
$session = new-pssession -ComputerName $targetDevice
Copy-Item -Path $logFile.FullName -Destination .\ -FromSession $session; invoke-command {remove-item -force C:\Rigel\*.zip} -ComputerName $targetDevice
```

Push an XML configuration file (or theme graphic)
  
```
$movefile = "<path>";
$targetDevice = "\\<Device fqdn> \Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState\SkypeSettings.xml"; 
Copy-Item $movefile $targetDevice 
```

## Software updates
<a name="SWupdate"> </a>

By default, Skype Room Systems v2 attempts to connect to the Windows Store to get the latest version of Skype Room Systems v2 software, so the device will require regular internet access. Before contacting Microsoft with support issues, be sure the Skype Room Systems v2 device is loaded with the latest version of the app.
  
By default, Skype Room Systems v2 connects to Windows Update to retrieve operating system and USB peripheral device firmware updates, and installs them outside of configured business hours. You can configure business hours by signing into the administrator account and running the Settings app.
  
If you want to manage updates manually, and are unable to follow the normal procedure for [Microsoft Store for Business](https://businessstore.microsoft.com/store) to [Distribute offline apps](https://docs.microsoft.com/microsoft-store/distribute-offline-apps), you can acquire the appropriate APPX file and dependencies from the [deployment kit](https://go.microsoft.com/fwlink/?linkid=851168) (from the instructions to [Configure a Skype Room Systems v2 console](../../deploy/deploy-clients/console.md)) that can be used with SCCM. The deployment kit release lags behind the store release, so it might not always match the latest available build.
  
### To update using Powershell

1. Extract the package from the installation [MSI](https://go.microsoft.com/fwlink/?linkid=851168) to a share the device can access.
    
2. Run the following script targeting the Skype Room Systems v2 devices, changing \<share\> to the device share as appropriate:
    
```
Add-AppxPackage -Update -ForceApplicationShutdown -Path '\\<share>\$oem$\$1\Rigel\x64\Ship\AppPackages\*\*.appx' -DependencyPath (Get-ChildItem '\\<share>\$oem$\$1\Rigel\x64\Ship\AppPackages\*\Dependencies\x64\*.appx' | Foreach-Object {$_.FullName})
```

## Admin mode and device management
<a name="AdminMode"> </a>

Some management functions, like manually installing a private CA certificate, require placing the Surface Pro device in Admin mode. 
  
### Switching to Admin Mode and back when the Skype Room Systems v2 app is running

1. Hang up any ongoing calls, and return to the home screen.
    
2. Select the Gear icon and bring up the menu (options are **Settings**, **Accessibility**, and **Restart Device** ).
    
3. Select **Settings**.
    
4. Enter the Administrator Password. The Setup screen will appear.
    
    > [!NOTE]
    > If the device isn't domain-joined, the local administrative account (username "Admin") will be used by default. The default password for this account is 'sfb' but it is recommended that your organization change this for security reasons as soon as possible. If the machine is domain-joined, you can sign in with an appropriately privileged domain account. 
  
5. Select **Windows Settings** in the left column.
    
6. Choose **Go to Admin Sign-in**.
    
7. Enter the Administrator Password. This will gracefully log off the app and take you to the Windows login screen. 
    
8. Log in to the desktop with your administrative credentials. You'll have the necessary privileges to manage the device.
    
9. Perform the necessary administrative tasks.
    
10. Sign out from the Admin account.
    
11. Return to Skype Room Systems v2 by selecting the user account icon on the far left side of the screen and then selecting **Skype**.
    
    If the **Skype** user is not listed, you might have to select **other user** and enter **.\skype** as the user name, and sign in.
    
The console is now back in its normal operation mode.The following procedure requires you to attach a keyboard to the device if one is not already attached. 
  
### Switching to Admin Mode and back when the Skype Room Systems v2 app crashes

1. Press the Windows key five times in rapid succession. This will bring you to the Windows logon screen. 
    
2. Log in to the desktop with your administrative credentials.
    
    > [!NOTE]
    > This method doesn't log the Skype user off or gracefully terminate the app, but you'd use it if the app wasn't responding and the other method wasn't available. 
  
3. Perform the necessary administrative tasks.
    
4. Restart the machine when you're finished.
    
   The console restarts into its normal operation mode, running the Skype Room Systems v2 app. You can remove the keyboard, if it was attached to allow you to perform this procedure.
   ## Troubleshooting tips
   <a name="TS"> </a>

- Meeting invitations might not appear when sent across domain boundaries (for example, between two companies). In such cases, IT admins should decide whether to allow external users to schedule a meeting.
    
- Skype Room Systems v2 doesn't support Exchange AutoDiscover redirects via Exchange 2010.
    
- In general, it's a good practice for IT admins to disable any audio endpoints they don't intend to use.
    
- In the event that a mirror image is displayed in room preview, the IT admin can correct by cycling camera power or flipping the image orientation using the camera remote control.
    
- Loss of console touchscreen access has been known to occur. In such cases, the issue is sometimes resolved by restarting the Skype Room Systems v2 system.
    
- Loss of local audio when connecting a PC to console via wired ingest has been known to occur. In such cases, restarting the PC can resolve the local audio playback issue.
    
