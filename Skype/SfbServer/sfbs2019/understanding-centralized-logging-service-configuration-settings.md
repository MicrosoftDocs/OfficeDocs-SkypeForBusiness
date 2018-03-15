---
title: "Understanding Centralized Logging Service configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3c34e600-0b91-43dc-b4cc-90b6a70ee12e
description: "The Centralized Logging Service is configured to define what the logging service is intended to collect, how it collects, where it will collect from, and what the log settings are. You define these settings globally (that is, for the entire deployment) or for a site (that is, a named site in your deployment). Any logging that you define will use the settings that are appropriate for the identity that you use for commands to start, stop, flush, and search logs."
---

# Understanding Centralized Logging Service configuration settings in Lync Server 2013
[]
The Centralized Logging Service is configured to define what the logging service is intended to collect, how it collects, where it will collect from, and what the log settings are. You define these settings globally (that is, for the entire deployment) or for a site (that is, a named site in your deployment). Any logging that you define will use the settings that are appropriate for the identity that you use for commands to start, stop, flush, and search logs.
  
### To display the current Centralized Logging Service configuration

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Type the following at a command-line prompt:
    
  ```
  Get-CsClsConfiguration
  ```

    > [!TIP]
    > You can narrow or expand the scope of the configuration settings that are returned by defining  `-Identity` and a scope, such as "Site:Redmond" to return only the CsClsConfiguration for the site Redmond. If you want details about a given portion of the configuration, you can pipe the output into another Windows PowerShell cmdlet. For example, to get details about the scenarios defined in the configuration for site "Redmond", type:  `Get-CsClsConfiguration -Identity "site:Redmond" | Select-Object -ExpandPropery Scenarios`
  
     ![Sample output from Get-CsClsConfiguration.](media/Ops_Get-CsClsConfiguration_Basic.jpg)
  
    The result from the cmdlet displays the current configuration of the Centralized Logging Service.
    
|**Configuration Setting**|**Description**|
|:-----|:-----|
|**Identity** <br/> |Identifies the scope and name for this configuration. There is only one Global configuration, and one configuration per site.  <br/> |
|**Scenarios** <br/> |Listing of all scenarios that are defined for this configuration.  <br/> |
|**SearchTerms** <br/> |Defined search terms for the configuration. Office 365, not on-premises deployments.  <br/> |
|**SecurityGroups** <br/> |Defined security groups that control who (that is, members of the security groups) can see computers based on the site they are located in. Site, in this context, is the site as defined in Topology Builder.  <br/> |
|**Regions** <br/> |Defined regions are used to collect SecurityGroups into a region, for example EMEA.  <br/> |
|**EtlFileFolder** <br/> |Defined path to the location where log files are written on computers. CLSAgent writes the log files and runs under the context of the Network Service. In this case, %TEMP% expands to %WINDIR%\ServiceProfiles\NetworkService\AppData\Local  <br/> |
|**EtlFileRolloverSizeMB** <br/> |The parameter indicates the maximum size of the log file before a new event trace log (.etl) file is created. A new log file is created when the defined size is reached even if the maximum time set in EtlFileRolloverMinutes has not yet been reached.  <br/> |
|**EtlFileRolloverMinutes** <br/> |Defined maximum amount of time, in minutes, that a log can elapse before a new .etl file is created. A new log file is created when the timer expires even if the maximum size set in EtlFileRolloverSizeMB has not yet been reached.  <br/> |
|**TmfFileSearchPath** <br/> |Location to search for the trace message format files. The trace message format files are used to convert the binary files into a human readable format.  <br/> |
|**CacheFileLocalFolders** <br/> |Defined path to the location where cache files are written on computers. CLSAgent writes the cache files and runs under the context of the Network Service. In this case, %TEMP% expands to %WINDIR%\ServiceProfiles\NetworkService\AppData\Local. By default, cache files and log files are written to the same directory.  <br/> |
|**CacheFileNetworkFolder** <br/> |You can define a universal naming convention (UNC) path to receive the cache files during logging operations.  <br/> |
|**CacheFileLocalRetentionPeriod** <br/> |Defined as the maximum time, in days, that cache files are retained.  <br/> |
|**CacheFileMaxDiskUsage** <br/> |Defined as the percentage of disk space that can be used by the cache files.  <br/> |
|**ComponentThrottleLimit** <br/> |Defined as the maximum number of traces per second that a component can produce before the automatic throttle limiter is triggered.  <br/> |
|**ComponentThrottleSample** <br/> |Number of times in 60 seconds that the ComponentThrottleLimit can be exceeded.  <br/> |
|**MinimumClsAgentServiceVersion** <br/> |The minimum version of the CLSAgent allowed to run. This element is intended for Office 365.  <br/> |
   
## See also

#### 

[Overview of the Centralized Logging Service in Lync Server 2013](overview-of-the-centralized-logging-service.md)
#### 

[Set-CsClsConfiguration](set-csclsconfiguration.md)
  
[Remove-CsClsConfiguration](remove-csclsconfiguration.md)
  
[New-CsClsConfiguration](new-csclsconfiguration.md)
  
[Get-CsClsConfiguration](get-csclsconfiguration.md)

