---
title: "Using Topology Builder to configure high availability and disaster recovery in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: abc1a25d-1f5e-46ef-91d2-0144fc847206
description: "Perform the following steps within Topology Builder to configure high availability and disaster recovery for Persistent Chat Server."
---

# Using Topology Builder to configure high availability and disaster recovery in Lync Server 2013
[]
Perform the following steps within Topology Builder to configure high availability and disaster recovery for Persistent Chat Server.
  
1. Add the mirror databases and the log shipping secondary database SQL Server stores.
    
2. Edit the Persistent Chat Server service properties to:
    
1. Enable mirroring for the primary database.
    
2. Add the primary mirror SQL Server store.
    
3. Enable the SQL Server Log Shipping database.
    
4. Add the SQL Server Log Shipping secondary SQL Server store.
    
5. Add the SQL Server store mirror for the secondary database.
    
6. Publish the topology.
    

