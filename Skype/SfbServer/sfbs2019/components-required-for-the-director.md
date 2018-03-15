---
title: "Components required for the Director in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 15c7c8d4-b93f-4386-b2d1-d76dab8f801e
description: "The only component required to create and configure a Director is to deploy the Director server role. You do this by using Topology Builder and define either a single computer pool or a multiple computer pool in the Director pool node. After you have defined the Director or Director pool, run the Lync Server Deployment Wizard on the computer that will be a Director. In the case of a Director pool, you run the Lync Server Deployment Wizard on each server that will be a member of the pool."
---

# Components required for the Director in Lync Server 2013
[]
The only component required to create and configure a Director is to deploy the Director server role. You do this by using Topology Builder and define either a single computer pool or a multiple computer pool in the Director pool node. After you have defined the Director or Director pool, run the Lync Server Deployment Wizard on the computer that will be a Director. In the case of a Director pool, you run the Lync Server Deployment Wizard on each server that will be a member of the pool.
  
## Topologies

You can implement a single Director server or a Director pool. The Director is always a separate server or pool, not collocated with any other server role in Lync Server 2013. 
  
> [!NOTE]
> If you do not deploy Directors, the Front End Server or Front End pool will assume the Director role. 
  
A pool of Directors must be load balanced. You can do one of the following:
  
- Create a topology that uses a hardware load balancer for web services and Domain Name System (DNS) load balancing for the other traffic types.
    
    [Scaled Director pool - DNS load balancing and hardware load balancer in Lync Server 2013](scaled-director-pooldns-load-balancing-and-hardware-load-balancer.md)
    
- Create a topology that uses a hardware load balancer for load balancing needed for the Director pool.
    
    [Scaled Director pool - hardware load balancer in Lync Server 2013](scaled-director-poolhardware-load-balancer.md)
    

