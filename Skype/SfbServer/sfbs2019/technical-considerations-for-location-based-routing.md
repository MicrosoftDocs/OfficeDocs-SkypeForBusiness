---
title: "Technical considerations for Location-Based Routing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2e2a9199-7c6f-48d3-9adb-3873fc4f8c4e
description: "When planning Location-Based Routing, you should consider the impact to the following scenarios."
---

# Technical considerations for Location-Based Routing in Lync Server 2013
[]
When planning Location-Based Routing, you should consider the impact to the following scenarios.
  
## Disaster Recovery

During a failover from the primary pool to a backup pool as well as when restoring normal operations to the primary pool, Location-Based Routing remains enforced at all times during a disaster and recovery procedure.
  
## Survivable Branch Appliance

Configuring Location-Based Routing impacts the planning of where you deploy the gateways associated to your Survivable Branch Appliances. The gateway associated to your SBA must be located in the same network site as your Survivable Branch Appliance; otherwise, users homed on your Survivable Branch Appliance will not be permitted to place outbound calls if Location-Based Routing is configured. When the WAN connection between your Survivable Branch Appliance and the central site is down, Location-Based Routing restrictions remains enforced.
  
## See also

#### 

[Planning for Location-Based Routing in Lync Server 2013](planning-for-location-based-routing.md)

