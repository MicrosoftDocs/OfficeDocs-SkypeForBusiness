---
title: "Show-CsClsLogging"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 19b2de51-5c14-4a8b-97e5-573c3285b174
description: "Shows the current status of the centralized logging service. (That is, shows which centralized logging scenarios are currently active.) Centralized logging provides a way for administrators to simultaneously enable or disable Skype for Business Server 2015 tracing on multiple computers. This cmdlet was introduced in Lync Server 2013."
---

# Show-CsClsLogging
 
Shows the current status of the centralized logging service. (That is, shows which centralized logging scenarios are currently active.) Centralized logging provides a way for administrators to simultaneously enable or disable Skype for Business Server 2015 tracing on multiple computers. This cmdlet was introduced in Lync Server 2013.
  
```
Show-CsClsLogging [-AsXml <SwitchParameter>] [-Computers <String >] [-Pools <String >]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns information about the scenarios currently being logged on all the Computers in the topology.
  
```
Show-CsClsLogging
```

### Example 2

In Example 2, logging information is returned for all the servers in the pool atl-cs-001…litwareinc.com…
  
```
Show-CsClsLogging -Pools "atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Skype for Business Server 2015. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.
  
It is also possible to define custom scenarios by using the [New-CsClsScenario](new-csclsscenario.md) cmdlet.
  
The **Show-CsClsLogging** cmdlet returns information about all the scenarios currently being logged on a computer or set of computers; this information includes the name and duration of each active scenario, as well as the date and time that logging began.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AsXml_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, information is returned using XML.  <br/> |
| _Computers_ <br/> |Optional  <br/> |System.String   <br/> |Enables administrators to return logging information from a specified server or set of servers. To return information from a single server, specify the fully qualified domain name of that server. For example:  <br/>  `-Computers "atl-server-001.litwareinc.com"` <br/> Multiple servers can be specified by separating the computer FQDNs using commas:  <br/>  `-Computers "atl-server-001.litwareinc.com","red-server-002.litwareinc.com"` <br/> If you do not include the Computers parameter or the Pools parameter, the **Show-CsClsLogging** cmdlet will show the status of all Computers in the topology. <br/> |
| _Pools_ <br/> |Optional  <br/> |System.String   <br/> |Enables administrators to return logging information for each server in a pool. To return information for a pool, specify the fully qualified domain name of that pool. For example:  <br/>  `-Pools "atl-cs-001.litwareinc.com"` <br/> Multiple pools can be specified by separating the pool FQDNs using commas:  <br/>  `-Pools "atl-cs-001.litwareinc.com","red-cs-002.litwareinc.com"` <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Show-CsClsLogging** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

String value or XML output. The **Show-CsClsLogging** cmdlet does not return objects.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Search-CsClsLogging](search-csclslogging.md)
  
[Start-CsClsLogging](start-csclslogging.md)
  
[Stop-CsClsLogging](stop-csclslogging.md)
  
[Sync-CsClsLogging](sync-csclslogging.md)
  
[Update-CsClsLogging](update-csclslogging.md)

