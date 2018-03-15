---
title: "Supported pool pairing options and best practices for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 142caf34-0f20-47f3-9d32-ce25ab622fad
description: "There is no restriction on the distance between two data centers that are to include Front End pools paired with each other. We recommend that you use two data centers in the same world region, with high-speed links between them. It is best if the two data centers are separated enough to avoid a single disaster hitting both at the same time."
---

# Supported pool pairing options and best practices for Lync Server 2013
[]
There is no restriction on the distance between two data centers that are to include Front End pools paired with each other. We recommend that you use two data centers in the same world region, with high-speed links between them. It is best if the two data centers are separated enough to avoid a single disaster hitting both at the same time. 
  
Having two data centers across world regions is possible, but could incur higher data loss due to latency in data replication.
  
When you plan which pools to pair, you must keep in mind that only the following pairings are supported:
  
- Enterprise Edition pools can be paired only with other Enterprise Edition pools. Similarly, Standard Edition pools can be paired only with other Standard Edition pools.
    
- Physical pools can be paired only with other physical pools. Similarly, virtual pools can be paired only with other virtual pools.
    
- Pools that are paired together must be running the same operating system.
    
Neither Topology Builder nor topology validation will prohibit pairing two pools in a way that does not follow these recommendations. For example, Topology Builder allows you to pair an Enterprise Edition pool with a Standard Edition pool. However, these types of pairings are not supported.
  
Each pool in a pair should have the capacity to serve all users from both pools in the event of a disaster.
  
If you pair Enterprise Edition pools, you can also implement high availability on the Back End Servers, but for pairs of Standard Edition pools only the disaster recovery measures are available. 
  

