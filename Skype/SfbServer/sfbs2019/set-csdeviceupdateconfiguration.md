---
title: "Set-CsDeviceUpdateConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4f200a03-984a-4c5b-a9c1-a866ba1851cd
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsDeviceUpdateConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies a collection of Device Update Web service configuration settings. These settings are used to manage the Device Update Web service, a Lync Server component that enables administrators to distribute firmware updates to telephones and other devices running Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsDeviceUpdateConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 shows how the **Set-CsDeviceUpdateConfiguration** cmdlet can be used to modify the global configuration settings. In this case, two property values are modified: the MaxLogFileSize property is set to 2048000 bytes and the MaxLogCacheLimit property is set to 1024000 bytes. 
  
```
Set-CsDeviceUpdateConfiguration -Identity global -MaxLogFileSize 2048000 -MaxLogCacheLimit 1024000
```

### EXAMPLE 2

Example 2 modifies the LogFlushInterval property for the device update configuration settings with the Identity site:Redmond. To do this, the Identity parameter is used to specify the settings at the Redmond site and the LogFlushInterval parameter is used to indicate the property value that be changed. In this case, the LogFlushInterval is set to 2 minutes (00 hours: 02 minutes: 00 seconds). 
  
```
Set-CsDeviceUpdateConfiguration -Identity site:Redmond -LogFlushInterval 00:02:00
```

### EXAMPLE 3

In Example 3, all of the device configuration update settings in the organization are modified in order to set the LogCleanUpInterval to 14 days. To do this, the **Get-CsDeviceUpdateConfiguration** cmdlet is first used to retrieve a collection of all the device update configuration settings currently in use. This collection is then piped to the **Set-CsDeviceUpdateConfiguration** cmdlet, which uses the LogCleanUpInterval parameter to set the log clean up interval time for each item in the collection to 14 days (14 days . 00 hours : 00 minutes : 00 seconds). 
  
```
Get-CsDeviceUpdateConfiguration | Set-CsDeviceUpdateConfiguration -LogCleanUpInterval 14.00:00:00
```

### EXAMPLE 4

Example 4 demonstrates how you can modify a property value for all the device update configuration settings that have been configured at the site scope; in this case, the command sets the LogCleanUpInterval to 20 days (20 days . 00 hours : 00 minutes : 00 seconds). In order to do this, the **Get-CsDeviceUpdateConfiguration** cmdlet is used along with the Filter parameter; the filter value "site:*" limits the returned data to settings that have an Identity that begins with the string value "site:". This filtered collection is then piped to the **Set-CsDeviceUpdateConfiguration** cmdlet, which changes the value of the log cleanup interval for each item in the collection. 
  
```
Get-CsDeviceUpdateConfiguration -Filter "site:*" | Set-CsDeviceUpdateConfiguration -LogCleanUpInterval 20.00:00:00
```

### EXAMPLE 5

Example 5 removes CELog from the list of valid log file types used by the device update configuration settings. In this command, the **Get-CsDeviceUpdateConfiguration** cmdlet is first used to retrieve a collection of all the device update configuration settings currently in use in the organization. That collection is then piped to the **Set-CsDeviceUpdateConfiguration** cmdlet, which uses the ValidLogFileTypes parameter in order to remove CELog from the list of valid log file types. The parameter value passed to ValidLogFileTypes, @{Remove="CELog"}, instructs the **Set-CsDeviceUpdateConfiguration** cmdlet to remove CELog from the set of valid file types. To remove multiple files types in a single command, simply include the additional types as part of a comma-separated list. For example: 
  
@{Remove="CELog","Watson"}
  
```
Get-CsDeviceUpdateConfiguration | Set-CsDeviceUpdateConfiguration -ValidLogFileTypes @{Remove="CELog"}
```

## Detailed Description
<a name="sectionSection1"> </a>

The Device Update Web service provides a way for administrators to distribute firmware updates to devices that run Lync Phone Edition. Periodically, administrators upload a set of device update rules to Lync Server. After those rules have been tested and approved, they can then be applied to the appropriate devices as those devices connect to the system. Devices check for updates when they are first powered on, then check again when a user logs on. After that, devices will check for updates every 24 hours.
  
Device update configuration settings can be applied at either the global or the site scope. The **Set-CsDeviceUpdateConfiguration** cmdlet enables you to make changes to a collection of settings. For example, you can use this cmdlet to change the length of time a log file is kept before it is automatically deleted by the system). 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsDeviceUpdateConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsDeviceUpdateConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the device update configuration settings to be modified. To refer to the global settings, use this syntax: -Identity global. To refer to site settings, use syntax similar to this: -Identity "site:Redmond". Note that you cannot use wildcards when specifying an Identity.  <br/> |
| _Instance_ <br/> |Optional  <br/> |DeviceUpdateSettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _LogCleanUpInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the amount of time a device update log file is kept before it is deleted by the system.  <br/> The value must be entered in the format dd.hh:mm:ss where dd is days, hh is hours, mm is minutes, and ss is seconds. To enter only days, you must follow the value with a period (.).  <br/> Minimum Value: 1.00:00:00 (1 Day)  <br/> Maximum Value: 365.00:00:00 (1 Year)  <br/> Default: 10.00:00:00 (10 Days)  <br/> |
| _LogCleanUpTimeOfDay_ <br/> |Optional  <br/> |System.DateTime  <br/> |Indicates the time of day when the system checks to see if there are any expired log files that should be deleted. (Expired log files are any files older than the value specified in by the LogCleanupInterval property.)  <br/> The value passed to the LogCleanupTimeOfDay parameter should be in the 24-hour time format hh:mm, where hh represents the hours and mm represents the minutes. In this format, midnight is represented as 00:00; 8:30 A.M. is represented as 08:30; and 11:52 P.M. is represented as 23:52.  <br/> |
| _LogFlushInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Indicates how often information stored in the log file cache is written to the actual log file. By default, device update information is not immediately written to the log file; instead, that information is cached in memory until: 1) the log flush time interval has expired; or, 2) the cache has reached its maximum size. If this value is set to 10 minutes (00:10:00), then information in the cache will be written to the log file every 10 minutes. After the data has been logged the cache will be cleared.  <br/> The value must be entered in the format hh:mm:ss where hh is hours, mm is minutes, and ss is seconds.  <br/> Minimum Value: 00:01:00 (1 minute)  <br/> Maximum Value: 1:00:00 (1 hour)  <br/> Default: 00:05:00  <br/> |
| _MaxLogCacheLimit_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum amount of information (in bytes) that can held in the log file cache before that cache must be cleared and the data written to a log file. By default, log files are "flushed" every 5 minutes. (For details, see the description of the parameter LogFlushInterval.) However, if the cache reaches its maximum size the information in it will automatically be written to a log file (and the cache cleared), even if the log flush interval has not yet expired.  <br/> Default: 512000  <br/> |
| _MaxLogFileSize_ <br/> |Optional  <br/> |System.UInt32  <br/> |Indicates the maximum size, in bytes, for an individual log file. When a file reaches the maximum size, the next batch of data is automatically written to a new log file. The old log file will be retained until the log cleanup interval has expired.  <br/> Default: 1024000  <br/> |
| _ValidLogFileExtensions_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Indicates the valid log file extensions that can be used with the Device Update Web service. This list can be modified; however, there is no reason to modify the list unless you have a Lync Phone Edition compatible device that creates log files that use a different file extension.  <br/> Default: .dmp, .clg, .clg2, .bak, .kdmp, .dat, .bin, .cat, .xml, .txt, .hex  <br/> |
| _ValidLogFileTypes_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Indicates the log file types retained by the device update system. The default file types include the following:  <br/> Watson. Log files automatically generated by a device in the event of a system crash.  <br/> CELog. Lync Phone logs that contain the results of functional tests and also a record of critical system events.  <br/> Additional file types can be added if you have a Lync Phone Edition-compatible device that creates a different kind of log file. You can also remove files. For example, if you do not want to store CELog files then you can remove the CELog file type.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration object. The **Set-CsDeviceUpdateConfiguration** cmdlet accepts pipelined instances of the device update configuration object. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsDeviceUpdateConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)
  
[New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md)
  
[Remove-CsDeviceUpdateConfiguration](remove-csdeviceupdateconfiguration.md)

