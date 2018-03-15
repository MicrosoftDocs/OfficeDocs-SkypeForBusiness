---
title: "Load balancing requirements for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 84489328-64a4-486c-9384-a3e5c8ed9c8b
description: "If you have Front End pools, Director pools, or Edge Server pools, you need to deploy load balancing for these pools. Load balancing distributes the traffic among the servers in a pool."
---

# Load balancing requirements for Lync Server 2013
[]
If you have Front End pools, Director pools, or Edge Server pools, you need to deploy load balancing for these pools. Load balancing distributes the traffic among the servers in a pool.
  
Lync Server 2013 supports two types of load balancing solutions for client-to-server traffic: Domain Name System (DNS) load balancing and hardware load balancing. DNS load balancing offers several advantages including simpler administration, more efficient troubleshooting, and the ability to isolate much of your Lync Server traffic from any potential hardware load balancer problems.
  
Decide which load balancing solution is appropriate for each pool in your deployment, keeping in mind the following restrictions: 
  
- The internal Edge interface and external Edge interface must use the same type of load balancing. You cannot use DNS load balancing on one interface and hardware load balancing on the other.
    
- Some types of traffic require a hardware load balancer. For example, HTTP traffic requires a hardware load balancer instead of DNS load balancing. DNS load balancing does not work with client-to-server web traffic.
    
For more details about choosing a hardware load balancer solution, see [Hardware load balancer requirements for Lync Server 2013](hardware-load-balancer-requirements.md).
  
If you choose to use DNS load balancing for a pool but still need to implement hardware load balancers for traffic such as HTTP traffic, the administration of the hardware load balancers is greatly simplified. For example, configuring the hardware load balancer will be simpler as it will only manage the HTTP and HTTPS traffic, while all other protocols will be managed by DNS load balancing. For details, see [DNS load balancing in Lync Server 2013](dns-load-balancing.md). 
  
For server-to-server traffic, Lync Server 2013 uses topology-aware load balancing. Servers read the published topology in the Central Management store to obtain the FQDNs of servers in the topology, and automatically distribute the traffic among the servers. Administrators do not need to set up or manage this type of load balancing. 
  
If you use DNS load balancing and you need to block traffic to a specific computer, it is not sufficient to just remove the IP address entries from the Pool FQDN. You must remove the DNS entry for the computer as well. 
  

