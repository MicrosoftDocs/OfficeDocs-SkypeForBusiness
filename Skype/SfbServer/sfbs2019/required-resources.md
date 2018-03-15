---
title: "Required resources for Persistent Chat Server in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 2/5/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bce50b95-f3c8-407e-963a-d8896ee77fbc
description: "High availability and disaster recovery for Persistent Chat Server requires additional resources beyond what is typically needed for full operation. Before configuring Persistent Chat Server for high availability and disaster recovery, ensure that you have the following resources in addition to what is required for standard Persistent Chat Server operation. For additional configuration information, see Configuring Persistent Chat Server in Lync Server 2013."
---

# Required resources for Persistent Chat Server in Lync Server 2013
[]
High availability and disaster recovery for Persistent Chat Server requires additional resources beyond what is typically needed for full operation. Before configuring Persistent Chat Server for high availability and disaster recovery, ensure that you have the following resources in addition to what is required for standard Persistent Chat Server operation. For additional configuration information, see [Configuring Persistent Chat Server in Lync Server 2013](configuring-persistent-chat-server.md).
  
- One dedicated database instance located in the same physical data center in which the home front end of the Persistent Chat Server service is located. This database will serve as the SQL Server mirror for the primary Persistent Chat database. Optionally, designate an additional SQL Server to serve as the mirroring witness if you want an automated failover to the mirror database.
    
- One dedicated database instance located in the other physical data center. This database will serve as the SQL Server Log Shipping secondary database for the database in the primary data center.
    
- One dedicated database instance to serve as the SQL Server mirror for the secondary database. Optionally, designate an additional SQL Server to server as the mirroring witness. Both of these must be located in the same physical data center as the secondary database.
    
- If Persistent Chat Server compliance is enabled, an additional three dedicated database instances are required. Their distribution is the same as those previously outlined for the Persistent Chat database. While it is possible for the compliance database to share the same SQL Server instance as the Persistent Chat database, we recommend standalone instances for high availability and disaster recovery.
    
- A file share must be created and designated for the SQL Server Log Shipping transaction logs. All SQL Servers in both data centers that run Persistent Chat databases must have read/write access to this file share. This share is not defined as part of a FileStore role.
    
- A file share on the secondary database server to serve as the destination folder for the SQL Server transaction logs that are copied from the primary server file share.
    
> [!NOTE]
> Active Persistent Chat servers in a Persistent Chat Server pool MUST reside in the same time zone as the next hop Lync Pool defined in the topology. 
  
The following figures provide examples about how the entire Persistent Chat Server pool can be configured in the two different stretched pool topologies:
  
- Stretched Persistent Chat Server pool when data centers are geo-located with high bandwidth/low latency.
    
- Stretched Persistent Chat Server pool when data centers are geo-located with low bandwidth/high latency.
    
The following figure shows a stretched Persistent Chat Server pool topology where data centers are geo-located with high bandwidth/low latency.
  
**Stretched Persistent Chat Server pool when data centers are geo-located with high bandwidth/low latency.**

![Persistent Chat Server pool HBW configuration exam](media/Deploy_PCS_Topo_StretchPool_HighBW_LowLat.jpg)
  
The following figure shows a stretched Persistent Chat Server pool topology where data centers are geo-located with low bandwidth/high latency.
  
**Stretched Persistent Chat Server pool when data centers are geo-located with low bandwidth/high latency.**

![Persistent Chat Server pool LBW configuration exam](media/Deploy_PCS_Topo_StretchPool_LowBW_HighLat.jpg)
  

