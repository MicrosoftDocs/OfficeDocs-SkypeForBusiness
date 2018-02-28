---
title: "Invoke-CsStorageServiceFlush"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3f88a70d-79b0-4614-8604-660bac35a86f
description: "Flushes the Skype for Business Server 2015 Storage Service database on each Front End server in a pool. Flushing a database involves writing all the queued data to disk, and then clearing the database queue. This cmdlet was introduced in Lync Server 2013."
---

# Invoke-CsStorageServiceFlush
[]
Flushes the Skype for Business Server 2015 Storage Service database on each Front End server in a pool. Flushing a database involves writing all the queued data to disk, and then clearing the database queue. This cmdlet was introduced in Lync Server 2013.
  
```
Invoke-CsStorageServiceFlush -FlushType <FullFlush | SteadyStateFlush> -PoolFqdn <Fqdn> [-Binding <String>] [-Force <SwitchParameter>] [-HostNameStorageService <String>] [-WaitTime <TimeSpan>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 performs a "steady state" flush of the Storage Service databases found on the pool atl-cs-011.litwareinc.com. In a steady state flush, the only data removed from the queue (and written to disk) is data that can be removed without affecting the database operation.
  
```
Invoke-CsStorageServiceFlush -PoolFqdn "atl-cs-001.litwareinc.com" -FlushType "SteadyState"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Skype for Business Server 2015 Storage Service provides a common interface and infrastructure for managing Skype for Business Server 2015 data, including session data for monitoring, archiving, and conversation history, as well as for integrating with the Exchange storage system. Like other databases, the Storage Service caches data in memory and then, as system resources permit, periodically writes that data to disk. 
  
As a general rule, administrators do not have to interact with this queued data. However, there could be times when the queue becomes too large or because the Registrar pool associated with the database is being failed over. In cases like that, the **Invoke-CsStorageServiceFlush** cmdlet can be called in order to write all the queued data to disk and then clear the database cache.
  
The **Invoke-CsStorageServiceFlush** cmdlet is also useful when multiple Front End servers must be shut down at the same time (for example, in order to do a software upgrade). As a general rule, Front End servers in a pool should be shut down, and restarted, one-by-one; that helps prevent data loss that could occur due to routing group rebalancing. However, there might be occasions when you need to shutdown multiple servers at the same time. To help guard against potential loss, you can run the **Invoke-CsStorageServiceFlush** cmdlet before doing the computer shutdowns. This will flush the queue for the pool and write all that data to disk before any of the servers are actually shut down.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Invoke-CsStorageServiceFlush** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _FlushType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Hadr.FlushType  <br/> |Specifies the type of storage flush to be performed. Allowed values are:  <br/> SteadyState - The only data that will be flushed is data that can be removed from the queue without affecting normal operations of the storage service. This is typically done to remove older data from the queue.  <br/> FullFlush - Flushes all the data from the queue. This is typically used when a pool is being failed over, and when there is no expectation that the queue will be receiving any new data.  <br/> |
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool containing the storage service to be flushed.  <br/> |
| _Binding_ <br/> |Optional  <br/> |System.String  <br/> |Windows Communication Foundation (WCF) binding. A WCF binding determines the transport, encoding, and protocol details required for clients and services to communicate with each other. valid values are:  <br/> NetNamedPipe  <br/> NetTCP  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _HostNameStorageService_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name of the server where the Skype for Business Server 2015 Storage Service is running. This parameter is required if the Binding is set to NetTCP.  <br/> |
| _WaitTime_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Specifies the maximum amount of time the cmdlet will wait before assuming that flushing has begun and moving on to the next step in the flushing process.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Invoke-CsStorageServiceFlush** cmdlet does not accept pipelined data.
  
## Return Types
<a name="ReturnTypes"> </a>

String value.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Invoke-CsPoolFailOver](invoke-cspoolfailover.md)

