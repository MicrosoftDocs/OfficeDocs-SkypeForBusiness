---
title: "New-CsDeviceUpdateConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2a06450d-291e-40f9-a780-45e2c4b28494
description: "Creates a new instance of device update configuration settings. These settings are used to manage the Device Update Web service, a Skype for Business Server 2015 component that enables administrators to distribute firmware updates to telephones and other devices running Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010."
---

# New-CsDeviceUpdateConfiguration
[]
Creates a new instance of device update configuration settings. These settings are used to manage the Device Update Web service, a Skype for Business Server 2015 component that enables administrators to distribute firmware updates to telephones and other devices running Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsDeviceUpdateConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-LogCleanUpInterval <TimeSpan>] [-LogCleanUpTimeOfDay <DateTime>] [-LogFlushInterval <TimeSpan>] [-MaxLogCacheLimit <UInt32>] [-MaxLogFileSize <UInt32>] [-ValidLogFileExtensions <PSListModifier>] [-ValidLogFileTypes <PSListModifier>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 creates a new set of device update configuration settings with the Identity site:Redmond. Because no other parameters are included in the command, this new collection of configuration settings will use the default values for each property.
  
```
New-CsDeviceUpdateConfiguration -Identity site:Redmond
```

### EXAMPLE 2

Example 2 also creates a new set of device update configuration settings with the Identity site:Redmond. In this case, two additional parameters are used in order to customize the new settings: MaxLogFileSize is used to set the maximum log file size to 2048000 bytes, while LogCleanUpInterval is used to set the log cleanup interval time to 7 days (7 days . 00 hours : 00 minutes : 00 seconds).
  
```
New-CsDeviceUpdateConfiguration -Identity site:Redmond -MaxLogFileSize 204800 -LogCleanUpInterval 7.00:00:00
```

## Detailed Description

The Device Update Web service provides a way for administrators to distribute firmware updates to devices that run Skype for Business Server 2015. Periodically, administrators upload a set of device update rules to Skype for Business Server 2015. After those rules have been tested and approved, they can then be applied to the appropriate devices as those devices connect to the system. Devices check for updates when they are first powered on, then check again when a user logs on. After that, devices check for updates every 24 hours.
  
Device update configuration settings, which are used to manage the Device Update Web service, can be assigned to the global level or to the site scope. To create a new collection of settings for a site, use the **New-CsDeviceUpdateConfiguration** cmdlet. Note that you can only create new settings at the site scope; your command will fail if you try to create a new collection of settings at the global scope. In addition, your command will fail if you try to create a new collection of settings for, say, the Redmond site, and that site already hosts a collection of device update configuration settings. That's because you can only have one collection of device update configuration settings per site.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity of the new device update configuration settings. Because new settings can only be created at the site scope, the Identity will look something like this:  `-Identity "site:Redmond"`.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _LogCleanUpInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the amount of time a device update log file is kept before it is deleted by the system.  <br/> The value must be entered in the format dd.hh:mm:ss where dd is days, hh is hours, mm is minutes, and ss is seconds. To enter only days, you must follow the value with a period (.).  <br/> Minimum Value: 1.00:00:00 (1 Day)  <br/> Maximum Value: 365.00:00:00 (1 Year)  <br/> Default: 10.00:00:00 (10 Days)  <br/> |
| _LogCleanUpTimeOfDay_ <br/> |Optional  <br/> |System.DateTime  <br/> |Indicates the time of day when the system checks to see if there are any expired log files that should be deleted. (Expired log files are any files older than the value specified in by the LogCleanupInterval property.)  <br/> The value passed to the LogCleanupTimeOfDay parameter must be in the 24-hour time format hh:mm, where hh represents the hours and mm represents the minutes. In this format, midnight is represented as 00:00; 8:30 A.M. is represented as 08:30; and 11:52 P.M. is represented as 23:52. The default value is null.  <br/> |
| _LogFlushInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Indicates how often information stored in the log file cache is written to the actual log file. By default, device update information is not immediately written to the log file; instead, that information is cached in memory until: 1) the log flush time interval has expired; or, 2) the cache has reached its maximum size. If this value is set to 10 minutes (00:10:00), then information in the cache will be written to the log file every 10 minutes. After the data has been logged the cache will be cleared.  <br/> The value must be entered in the format hh:mm:ss where hh is hours, mm is minutes, and ss is seconds.  <br/> Minimum Value: 00:01:00 (1 minute)  <br/> Maximum Value: 1:00:00 (1 hour)  <br/> Default: 00:05:00  <br/> |
| _MaxLogCacheLimit_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum amount of information (in bytes) that can be held in the log file cache before that cache must be cleared and the data written to a log file. By default, log files are "flushed" every X number of minutes. (For details, see the description of the parameter LogFlushInterval.) However, if the cache reaches its maximum size, the information in it will automatically be written to a log file (and the cache cleared) even if the log flush interval has not yet expired.  <br/> Default: 512000  <br/> |
| _MaxLogFileSize_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum size, in bytes, for an individual log file. When a file reaches the maximum size, the next batch of data is automatically written to a new log file. The old log file will be retained until the log cleanup interval has expired.  <br/> Default: 1024000  <br/> |
| _ValidLogFileExtensions_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Indicates the valid log file extensions that can be used with the Device Update Web service. This list can be modified; however, there is no reason to modify the list unless you have a device running Skype for Business that creates log files that use a different file extension.  <br/> Default: .dmp, .clg, .clg2, .bak, .kdmp, .dat, .bin, .cat, .xml, .txt, .hex  <br/> |
| _ValidLogFileTypes_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Indicates the log file types retained by the device update system. The default file types include the following:  <br/> Watson. Log files automatically generated by a device if the system stops responding.  <br/> CELog. Logs for phones running Skype for Business that contain the results of functional tests and a record of critical system events.  <br/> Additional file types can be added if you have a device running Skype for Business Phone Edition that creates a different kind of log file. You can also remove files. For example, if you do not want to store CELog files then you can remove the CELog file type.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsDeviceUpdateConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsDeviceUpdateConfiguration** cmdlet creates instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration object.
  
## See also

#### 

[Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)
  
[Remove-CsDeviceUpdateConfiguration](remove-csdeviceupdateconfiguration.md)
  
[Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md)

