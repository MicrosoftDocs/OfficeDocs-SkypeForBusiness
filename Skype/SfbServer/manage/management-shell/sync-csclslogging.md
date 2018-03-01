---
title: "Sync-CsClsLogging"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0df996b7-1834-42f1-84e5-346ba74631e7
description: "Flushes the centralized logging service cache. Centralized logging provides a way for administrators to simultaneously enable or disable Skype for Business Server 2015 tracing on multiple computers. This cmdlet was introduced in Lync Server 2013."
---

# Sync-CsClsLogging
 
Flushes the centralized logging service cache. Centralized logging provides a way for administrators to simultaneously enable or disable Skype for Business Server 2015 tracing on multiple computers. This cmdlet was introduced in Lync Server 2013.
  
```
Sync-CsClsLogging [-AsXml <SwitchParameter>] [-Computers <String >] [-Pools <String >]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 flushes the centralized logging caches for all the servers in the topology.
  
```
Sync-CsClsLogging 
```

### Example 2

In Example 2, the centralized logging caches are flushed on all the servers in the pool atl-cs-001.litwareinc.com.
  
```
Sync-CsClsLogging -Pools "atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Skype for Business Server 2015. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.
  
Centralized logging is built around a series of predefined scenarios that offer a more finely-targeted approach to logging than offered in previous versions of Skype for Business Server 2015. These scenarios predetermine the server components and logging for you; as a result, an administrator enabling the RGS scenario can be confident that he or she will only log information relevant to the Response Group service and not to, say, the audio conferencing provider service.
  
It is also possible to define custom scenarios by using the [New-CsClsScenario](new-csclsscenario.md) cmdlet.
  
When a scenario is being logged, the service will maintain data in memory and then periodically write that data to disk. However, at any time administrators can run the **Sync-CsClsLogging** cmdlet to "flush" the data cache. When this is done, all the logging data currently in memory will be written to disk, the data caches will be cleared, and the log files will be available for searching.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AsXml_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, information is returned using XML.  <br/> |
| _Computers_ <br/> |Optional  <br/> |System.String   <br/> |Enables administrators to flush the centralized logging service cache on a specified server or set of servers. To flush a single server cache, specify the fully qualified domain name of that server. For example:  <br/>  `-Computers "atl-server-001.litwareinc.com"` <br/> Multiple servers can be specified by separating the computer FQDNs using commas:  <br/>  `-Computers "atl-server-001.litwareinc.com","red-server-002.litwareinc.com"` <br/> If you do not include the Computers parameter or the Pools parameter, the **Sync-CsClsLogging** cmdlet will apply the command against all pools in the topology. <br/> |
| _Pools_ <br/> |Optional  <br/> |System.String   <br/> |Enables administrators to flush the centralized logging service cache on each server in a pool. To flush the server caches in a pool, specify the fully qualified domain name of that pool. For example:  <br/>  `-Pools "atl-cs-001.litwareinc.com"` <br/> Multiple pools can be specified by separating the pool FQDNs using commas:  <br/>  `-Pools "atl-cs-001.litwareinc.com","red-cs-002.litwareinc.com"` <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Sync-CsClsLogging** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

String value. The **Sync-CsClsLogging** cmdlet does not return objects.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Search-CsClsLogging](search-csclslogging.md)
  
[Show-CsClsLogging](show-csclslogging.md)
  
[Start-CsClsLogging](start-csclslogging.md)
  
[Stop-CsClsLogging](stop-csclslogging.md)
  
[Update-CsClsLogging](update-csclslogging.md)

