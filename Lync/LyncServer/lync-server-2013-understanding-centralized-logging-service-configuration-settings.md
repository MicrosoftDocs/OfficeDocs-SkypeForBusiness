---
title: 'Understanding Centralized Logging Service configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Understanding Centralized Logging Service configuration settings
ms:assetid: 3c34e600-0b91-43dc-b4cc-90b6a70ee12e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688029(v=OCS.15)
ms:contentKeyID: 49733619
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Understanding Centralized Logging Service configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

The Centralized Logging Service is configured to define what the logging service is intended to collect, how it collects, where it will collect from, and what the log settings are. You define these settings globally (that is, for the entire deployment) or for a site (that is, a named site in your deployment). Any logging that you define will use the settings that are appropriate for the identity that you use for commands to start, stop, flush, and search logs.

<div>

## To display the current Centralized Logging Service configuration

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Type the following at a command-line prompt:
    
        Get-CsClsConfiguration
    
    <div>
    

    > [!TIP]
    > You can narrow or expand the scope of the configuration settings that are returned by defining <CODE>-Identity</CODE> and a scope, such as "Site:Redmond" to return only the CsClsConfiguration for the site Redmond. If you want details about a given portion of the configuration, you can pipe the output into another Windows PowerShell cmdlet. For example, to get details about the scenarios defined in the configuration for site "Redmond", type: <CODE>Get-CsClsConfiguration -Identity "site:Redmond" | Select-Object -ExpandPropery Scenarios</CODE>

    
    </div>
    
    ![Sample output from Get-CsClsConfiguration.](images/JJ688029.23f98ddc-fc48-499a-b6c5-752611f2a0b0(OCS.15).jpg "Sample output from Get-CsClsConfiguration.")
    
    The result from the cmdlet displays the current configuration of the Centralized Logging Service.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Configuration Setting</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>Identity</strong></p></td>
    <td><p>Identifies the scope and name for this configuration. There is only one Global configuration, and one configuration per site.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Scenarios</strong></p></td>
    <td><p>Listing of all scenarios that are defined for this configuration.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>SearchTerms</strong></p></td>
    <td><p>Defined search terms for the configuration. Office 365, not on-premises deployments.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>SecurityGroups</strong></p></td>
    <td><p>Defined security groups that control who (that is, members of the security groups) can see computers based on the site they are located in. Site, in this context, is the site as defined in Topology Builder.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Regions</strong></p></td>
    <td><p>Defined regions are used to collect SecurityGroups into a region, for example EMEA.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>EtlFileFolder</strong></p></td>
    <td><p>Defined path to the location where log files are written on computers. CLSAgent writes the log files and runs under the context of the Network Service. In this case, %TEMP% expands to %WINDIR%\ServiceProfiles\NetworkService\AppData\Local</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>EtlFileRolloverSizeMB</strong></p></td>
    <td><p>The parameter indicates the maximum size of the log file before a new event trace log (.etl) file is created. A new log file is created when the defined size is reached even if the maximum time set in EtlFileRolloverMinutes has not yet been reached.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>EtlFileRolloverMinutes</strong></p></td>
    <td><p>Defined maximum amount of time, in minutes, that a log can elapse before a new .etl file is created. A new log file is created when the timer expires even if the maximum size set in EtlFileRolloverSizeMB has not yet been reached.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>TmfFileSearchPath</strong></p></td>
    <td><p>Location to search for the trace message format files. The trace message format files are used to convert the binary files into a human readable format.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>CacheFileLocalFolders</strong></p></td>
    <td><p>Defined path to the location where cache files are written on computers. CLSAgent writes the cache files and runs under the context of the Network Service. In this case, %TEMP% expands to %WINDIR%\ServiceProfiles\NetworkService\AppData\Local. By default, cache files and log files are written to the same directory.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>CacheFileNetworkFolder</strong></p></td>
    <td><p>You can define a universal naming convention (UNC) path to receive the cache files during logging operations.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>CacheFileLocalRetentionPeriod</strong></p></td>
    <td><p>Defined as the maximum time, in days, that cache files are retained.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>CacheFileMaxDiskUsage</strong></p></td>
    <td><p>Defined as the percentage of disk space that can be used by the cache files.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>ComponentThrottleLimit</strong></p></td>
    <td><p>Defined as the maximum number of traces per second that a component can produce before the automatic throttle limiter is triggered.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>ComponentThrottleSample</strong></p></td>
    <td><p>Number of times in 60 seconds that the ComponentThrottleLimit can be exceeded.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>MinimumClsAgentServiceVersion</strong></p></td>
    <td><p>The minimum version of the CLSAgent allowed to run. This element is intended for Office 365.</p></td>
    </tr>
    </tbody>
    </table>


</div>

<div>

## See Also


[Overview of the Centralized Logging Service in Lync Server 2013](lync-server-2013-overview-of-the-centralized-logging-service.md)  


[Set-CsClsConfiguration](https://technet.microsoft.com/en-us/library/JJ619182(v=OCS.15))  
[Remove-CsClsConfiguration](https://technet.microsoft.com/en-us/library/JJ619191(v=OCS.15))  
[New-CsClsConfiguration](https://technet.microsoft.com/en-us/library/JJ619177(v=OCS.15))  
[Get-CsClsConfiguration](https://technet.microsoft.com/en-us/library/JJ619179(v=OCS.15))  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

