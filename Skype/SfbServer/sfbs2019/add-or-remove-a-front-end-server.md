---
title: "Add or remove a Front End Server in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 1/21/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ab748733-6bad-4c93-8dda-db8d5271653d
description: "When you add a Front End Server to a pool, or remove a Front End Server from a pool, you then need to restart the pool. To prevent any interruption of service to users, use the following procedure when adding or removing a Front End Server."
---

# Add or remove a Front End Server in Lync Server 2013
[]
When you add a Front End Server to a pool, or remove a Front End Server from a pool, you then need to restart the pool. To prevent any interruption of service to users, use the following procedure when adding or removing a Front End Server.
  
> [!NOTE]
> If you're adding new servers to the pool, update your new pool servers to be at the same Cumulative Update level as the existing servers in the Pool. 
  
### To add or remove Front End servers

1. If you are removing any Front End Servers, first stop new connections to those servers. To do so, you can use the following cmdlet:
    
  ```
  Stop -CsWindowsServices -Graceful
  ```

2. When the servers being removed have no current sessions, stop Lync Server services on them.
    
3. Open Topology Builder, and add or remove the necessary servers. 
    
4. Publish the topology.
    
5. If the pool has gone from having two Front End Servers to more than two, or gone from more than two servers to exactly two, you need to type the following cmdlet:
    
  ```
  Reset-CsPoolRegistrarState-ResetType FullReset -PoolFqdn <PoolFqdn>
  
  ```

    If the pool has three or more servers, then at least three of those servers must be running when you type this cmdlet.
    
6. Restart all Front End Servers in the pool, one at a time.
    

