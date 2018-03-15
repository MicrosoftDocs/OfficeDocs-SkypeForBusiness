---
title: "Start-CsClsLogging"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cac15f5a-5a0c-4b3c-9bef-bb4fd44005b2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Start-CsClsLogging
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Starts the specified scenario centralized logging service scenario. Centralized logging provides a way for administrators to simultaneously enable or disable Lync Server 2013 tracing on multiple computers. This cmdlet was introduced in Lync Server 2013.
  
```
Start-CsClsLogging -Scenario <String> [-AsXml <SwitchParameter>] [-Computers <String[]>] [-Duration <String>] [-Pools <String[]>]
```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 starts logging the AlwaysOn scenario on all the computers in the current topology.
  
```
Start-CsClsLogging -Scenario "AlwaysOn"
```

### Example 2

The command shown in Example 2 starts CPS logging on all the computers in the pool atl-cs-001.litwareinc.com with duration of 12 hours.
  
```
Start-CsClsLogging -Scenario "cps" -Pools "atl-cs-001.litwareinc.com" -Duration 12:0
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Lync Server 2013. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet. 
  
Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Lync Server. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.
  
It is also possible to define custom scenarios by using the [New-CsClsScenario](new-csclsscenario.md) cmdlet. 
  
The **Start-CsClsLogging** cmdlet provides a way for administrators to begin logging a specified scenario on a computer or set of computers. By default, that logging operation will continue to run until the Duration time limit has expired. However, administrators can manually stop a logging operation at any time by using the [Stop-CsClsLogging](stop-csclslogging.md) cmdlet. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Scenario_ <br/> |Required  <br/> |System.String  <br/> |Name of the centralized logging scenario to be started. Available scenarios (and their names) names can be returned by using this command:  <br/> Get-CsClsScenario | Select-Object Name  <br/> Note that you can only specify one scenario per call to the **Start-CsClsLogging** cmdlet. . Also only one scenario other than the "AlwaysOn" scenario can be started on a computer at any one time.  <br/> |
| _AsXml_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, information is returned using XML.  <br/> |
| _Computers_ <br/> |Optional  <br/> |System.String[]  <br/> |Enables administrators to start logging on a specified server or set of servers. To start logging on a single server, specify the fully qualified domain name of that server. For example:  <br/> -Computers "atl-server-001.litwareinc.com"  <br/> Multiple servers can be specified by separating the computer FQDNs using commas:  <br/> -Computers "atl-server-001.litwareinc.com","red-server-002.litwareinc.com"  <br/> If you do not include the Computers parameter or the Pools parameter, the **Start-CsClsLogging** cmdlet will automatically run against all the computers in the topology.  <br/> |
| _Duration_ <br/> |Optional  <br/> |System.String  <br/> |Amount of time that the logging operation should run. For example, this syntax causes the logging operation to run for 2 hours (0 days.02 hours:00 minutes) and then stop:  <br/> -Duration 0.02:00  <br/> This following syntax would specify a duration of 3 hours and 15 minutes:  <br/> -Duration 0.03:15  <br/> The following syntax would specify a duration of 6 days, 5 hours and 12 minutes:  <br/> -Duration 6.05:12  <br/> The default value is 4 hours (04:00).  <br/> |
| _Pools_ <br/> |Optional  <br/> |System.String[]  <br/> |Enables administrators to start logging a scenario on each server in a pool. To start logging in a pool, specify the fully qualified domain name of that pool. For example:  <br/> -Pools "atl-cs-001.litwareinc.com"  <br/> Multiple pools can be specified by separating the pool FQDNs using commas:  <br/> -Pools "atl-cs-001.litwareinc.com","red-cs-002.litwareinc.com"  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Start-CsClsLogging** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

String value or XML output. The **Start-CsClsLogging** cmdlet does not return objects. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Search-CsClsLogging](search-csclslogging.md)
  
[Show-CsClsLogging](show-csclslogging.md)
  
[Stop-CsClsLogging](stop-csclslogging.md)
  
[Sync-CsClsLogging](sync-csclslogging.md)
  
[Update-CsClsLogging](update-csclslogging.md)

