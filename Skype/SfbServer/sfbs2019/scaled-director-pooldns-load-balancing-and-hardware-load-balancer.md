---
title: "Scaled Director pool - DNS load balancing and hardware load balancer in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a1f6ffc0-9e6e-4217-a923-025c9679e154
description: "A scaled Director pool, where there are more than one Director deployed to handle additional capacity and to provide high availability, requires load balancing to distribute client and server communication to all members of the pool. A Director hosts web services much like a Front End pool. To provide the load balancing, you can use either hardware load balancing or domain name system (DNS) load balancing and hardware load balancing. Hardware load balancing is required for the web services, and DNS load balancing alone does not provide the capabilities required for the web services."
---

# Scaled Director pool - DNS load balancing and hardware load balancer in Lync Server 2013
[]
A scaled Director pool, where there are more than one Director deployed to handle additional capacity and to provide high availability, requires load balancing to distribute client and server communication to all members of the pool. A Director hosts web services much like a Front End pool. To provide the load balancing, you can use either hardware load balancing or domain name system (DNS) load balancing and hardware load balancing. Hardware load balancing is required for the web services, and DNS load balancing alone does not provide the capabilities required for the web services.
  
The following topics describe the planning considerations for deploying a Director pool using DNS load balancing in conjunction with hardware load balancing. If you intend to use hardware load balancing, but not DNS load balancing for the Director pool, see the topic [Scaled Director pool - hardware load balancer in Lync Server 2013](scaled-director-poolhardware-load-balancer.md) that describes the planning requirements for that topology. 
  
![Scaled Director Pool](media/Plan_LyncServer_Director_NetPerimeter_PooledDirectorDNSandHLB.jpg)
  
## In this section

- [Certificate summary - DNS and HLB load balanced in Lync Server 2013](certificate-summarydns-and-hlb-load-balanced.md)
    
- [Port summary - DNS and HLB load balanced in Lync Server 2013](port-summarydns-and-hlb-load-balanced.md)
    
- [DNS summary - DNS and HLB load balanced in Lync Server 2013](dns-summarydns-and-hlb-load-balanced.md)
    

