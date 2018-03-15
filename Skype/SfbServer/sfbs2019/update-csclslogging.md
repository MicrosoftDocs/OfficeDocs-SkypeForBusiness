---
title: "Update-CsClsLogging"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 104ecc02-789d-4538-8203-0451448d4301
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Update-CsClsLogging
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Updates the duration time for all active centralized logging scenarios. Centralized logging provides a way for administrators to simultaneously enable or disable Lync Server 2013 tracing on multiple computers. This cmdlet was introduced in Lync Server 2013.
  
```
Update-CsClsLogging -Duration <String> [-AsXml <SwitchParameter>] [-Computers <String[]>] [-Pools <String[]>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 modifies the logging duration time for servers in the topology. In this example, the duration time is set to 1 hour (60 minutes).
  
```
Update-CsClsLogging -Duration 60
```

### Example 2

In Example 2, the duration time is modified for all the servers in the pool atl-cs-001.litwareinc.com.
  
```
Update-CsClsLogging -Duration 60 -Pools "atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Lync Server 2013. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet. 
  
Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Lync Server. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.
  
It is also possible to define custom scenarios by using the [New-CsClsScenario](new-csclsscenario.md) cmdlet. 
  
By default, logging operations run for 4 hours (240 minutes) before automatically stopping; however, administrators have the option of specifying a different duration time when they begin logging. In addition, administrators can also use the **Update-CsClsLogging** cmdlet to change the duration time for all the scenarios currently being logged. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Duration_ <br/> |Required  <br/> |System.String  <br/> |Amount of time that the logging operation should run. For example, this syntax causes the logging operation to run for 2 hours (120 minutes) and then stop:  <br/> -Duration 120  <br/> This following syntax would specify a duration of 3 hours and 14 minutes:  <br/> -Duration 3:15  <br/> The following syntax would specify a duration of 6 days, 5 hours and 12 minutes:  <br/> -Duration 6.5:12  <br/> The default value is 30 minites.  <br/> |
| _AsXml_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, information is returned using XML.  <br/> |
| _Computers_ <br/> |Optional  <br/> |System.String[]  <br/> |Enables administrators to updates the centralized logging service on a specified server or set of servers. To update a single server, specify the fully qualified domain name of that server. For example:  <br/> -Computers "atl-server-001.litwareinc.com"  <br/> Multiple servers can be specified by separating the computer FQDNs using commas:  <br/> -Computers "atl-server-001.litwareinc.com","red-server-002.litwareinc.com"  <br/> If you do not the Computers parameter or the Pools parameter, Update-CsClsLogging will automatically run against all the computers in the topology.  <br/> |
| _Pools_ <br/> |Optional  <br/> |System.String[]  <br/> |Enables administrators to update the centralized logging service on each server in a pool. To update the servers in a pool, specify the fully qualified domain name of that pool. For example:  <br/> -Pools "atl-cs-001.litwareinc.com"  <br/> Multiple pools can be specified by separating the pool FQDNs using commas:  <br/> -Pools "atl-cs-001.litwareinc.com","red-cs-002.litwareinc.com"  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Update-CsClsLogging** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

String value. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Search-CsClsLogging](search-csclslogging.md)
  
[Show-CsClsLogging](show-csclslogging.md)
  
[Start-CsClsLogging](start-csclslogging.md)
  
[Stop-CsClsLogging](stop-csclslogging.md)
  
[Sync-CsClsLogging](sync-csclslogging.md)

