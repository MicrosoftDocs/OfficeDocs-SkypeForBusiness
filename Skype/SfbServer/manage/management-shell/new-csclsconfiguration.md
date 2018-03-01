---
title: "New-CsClsConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 44cf1720-feae-47a5-b56a-5891a095b243
description: "Creates a new collection of centralized logging configuration settings. Centralized logging provides a way for administrators to simultaneously enable or disable Skype for Business Server 2015 tracing on multiple computers. This cmdlet was introduced in Lync Server 2013."
---

# New-CsClsConfiguration
 
Creates a new collection of centralized logging configuration settings. Centralized logging provides a way for administrators to simultaneously enable or disable Skype for Business Server 2015 tracing on multiple computers. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsClsConfiguration -Identity <XdsIdentity> [-CacheFileLocalFolders <String>] [-CacheFileLocalMaxDiskUsage <UInt32>] [-CacheFileLocalRetentionPeriod <UInt32>] [-CacheFileNetworkFolder <String>] [-ComponentThrottleLimit <UInt32>] [-ComponentThrottleSample <UInt32>] [-Confirm [<SwitchParameter>]] [-EtlFileFolder <String>] [-EtlFileRolloverMinutes <UInt32>] [-EtlFileRolloverSizeMB <UInt32>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MinimumClsAgentServiceVersion <UInt32>] [-NetworkUsagePacketSize <UInt32>] [-NetworkUsageThreshold <UInt32>] [-Regions <PSListModifier>] [-Scenarios <PSListModifier>] [-SearchTerms <PSListModifier>] [-SecurityGroups <PSListModifier>] [-TmfFileSearchPath <String>] [-Version <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new collection of centralized logging configuration settings for the Redmond site. In this new collection, the ETL file rollover size is set to 40 megabytes, and the ETL file rollover time is set to 2 hours (120 minutes).
  
```
New-CsClsConfiguration -Identity "site:Redmond" -EtlFileRolloverSizeMB 40 -EtlFileRolloverMinutes 120
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Skype for Business Server 2015. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.
  
It is also possible to define custom scenarios by using the [New-CsClsScenario](new-csclsscenario.md) cmdlet.
  
Centralized logging is managed by using collections of centralized logging service configuration settings. When you install Skype for Business Server 2015, you install a global set of these configuration settings; in addition, administrators can add custom settings collections at the site scope. This is done by using the **New-CsClsConfiguration** cmdlet.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **New-CsCClsConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the centralized logging configuration settings to be created. Because these settings can only be created at the site scope, use syntax similar to this, with the prefix "site:" followed by the name of the site:  <br/>  `-Identity "site:Redmond"` <br/> |
| _CacheFileLocalFolders_ <br/> |Optional  <br/> |System.String  <br/> |One or more full paths to the local folders where the cache files will be stored. The default value is %TEMP%\Tracing. If more than one path is specified, then separate them with semi-colons.  <br/> |
| _CacheFileLocalMaxDiskUsage_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum amount of disk space (percentage) that can be used for the cache files. The default value is 80.  <br/> |
| _CacheFileLocalRetentionPeriod_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum number of days that cache files are retained locally. The default value is 14.  <br/> |
| _CacheFileNetworkFolder_ <br/> |Optional  <br/> |System.String  <br/> |Full UNC path to the network cache folder. There is no default value.  <br/> |
| _ComponentThrottleLimit_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum rate at which a component is allowed to generate trace records before its tracing is throttled. The default value is 5000 trace calls per second.  <br/> |
| _ComponentThrottleSample_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum number of times the ComponentThrottleLimit can be exceeded within a one minute interval. The default value is 3.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EtlFileFolder_ <br/> |Optional  <br/> |System.String  <br/> |Full path to the folder where the event log trace files will be stored. The default value is %TEMP%\Tracing. Note that %TEMP% is evaluated in the contents of the CLS Service so it actual expands to %WINDIR%\ServiceProfiles\NetworkService\AppData\Local  <br/> |
| _EtlFileRolloverMinutes_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum amount of time (in minutes) that can elapse before a new event log trace file is created. (This new file will be created even if the existing trace file has not reached the specified rollover size.) The default value is 60.  <br/> |
| _EtlFileRolloverSizeMB_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum size (in megabytes) that at event trace log file can reach before a new file is created. The default value is 20.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _MinimumClsAgentServiceVersion_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the minimum version of the centralized logging service agent to be used when logging data; any computers with an agent version lower than the minimum value will be excluded from the logging operations. The default value is 6, representing Skype for Business Server 2015. This parameter is intended for use with Skype for Business Online.  <br/> |
| _NetworkUsagePacketSize_ <br/> |Optional  <br/> |System.UInt32  <br/> |Packet size (in kilobytes) for transmitting agent search results and copying cache files over the network. The default value is 64 KB.  <br/> |
| _NetworkUsageThreshold_ <br/> |Optional  <br/> |System.UInt32  <br/> |Bandwidth usage threshold (in MB per second) for transmitting agent search results and copying cache files over the network. The default value is 10.  <br/> |
| _Regions_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of regions defined for the centralized logging configuration settings. Regions are defined using the New-CsClsRegion cmdlet.  <br/> This parameter is intended for use with Skype for Business Online.  <br/> |
| _Scenarios_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of components/situations that can be traced using centralized logging. Scenarios are managed using the **CsClsScenario** cmdlets. <br/> |
| _SearchTerms_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of terms that help determine the personally identifiable information available to technical support personnel who search the centralized logging files. Search terms are managed using the **CsClsSearchTerm** cmdlets. <br/> |
| _SecurityGroups_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Security groups who are allowed to access the log files.  <br/> This parameter is intended for use with Skype for Business Online.  <br/> |
| _TmfFileSearchPath_ <br/> |Optional  <br/> |System.String  <br/> |Search path for TMF (trace message format) files. TMF files convert binary trace messages to a human-readable format.  <br/> |
| _Version_ <br/> |Optional  <br/> |System.String  <br/> |This parameter is reserved for internal Microsoft use.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _ETLEnoughFreeSpaceInDiskInBytes_ <br/> |Optional  <br/> |System.Int64  <br/> |PARAMVALUE: Int64  <br/> |
| _ETLEnoughQuotaInBytes_ <br/> |Optional  <br/> |System.Int64  <br/> |PARAMVALUE: Int64  <br/> |
| _ETLMaxQuotaInBytes_ <br/> |Optional  <br/> |System.Int64  <br/> |PARAMVALUE: Int64  <br/> |
| _EtlMaxRetentionInDays_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _ETLMinFreeSpaceInDiskInBytes_ <br/> |Optional  <br/> |System.Int64  <br/> |PARAMVALUE: Int64  <br/> |
| _ETLMinQuotaInBytes_ <br/> |Optional  <br/> |System.Int64  <br/> |PARAMVALUE: Int64  <br/> |
| _EtlModeEnabled_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _EtlModeRevision_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _EtlNtfsCompressionEnabled_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _InsertTypesForSubstringMatch_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _LocalSearchMode_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _LocalSearchModeRevision_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _ZipEtlEnabled_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _EtlMdsUploadEnabled_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _MdsProviders_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |PARAMVALUE: PSListModifier  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsClsConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsClsConfiguration** cmdlet creates new instances of the icrosoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.CentralizedLoggingConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsClsConfiguration](get-csclsconfiguration.md)
  
[Remove-CsClsConfiguration](remove-csclsconfiguration.md)
  
[Set-CsClsConfiguration](set-csclsconfiguration.md)

