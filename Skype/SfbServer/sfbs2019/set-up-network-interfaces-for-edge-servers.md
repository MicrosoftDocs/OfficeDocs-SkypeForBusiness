---
title: "Set up network interfaces for Edge Servers in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b0aecdf6-4ae2-46f6-b9b6-948bfc3df11e
description: "Each Edge Server is a multihomed computer with external and internal facing interfaces. The adapter Domain Name System (DNS) settings depend on whether there are DNS servers in the perimeter network. If DNS servers exist in the perimeter, they must have a zone containing one or more DNS A records for the next hop server or pool (that is, either a Director or a designated Front End pool), and for external queries they refer name lookups to other public DNS servers. If no DNS servers exist in the perimeter, the Edge Server(s) use external DNS servers to resolve Internet name lookups, and each Edge Server uses a HOST to resolve the next hop server names to IP addresses."
---

# Set up network interfaces for Edge Servers in Lync Server 2013
[]
Each Edge Server is a multihomed computer with external and internal facing interfaces. The adapter Domain Name System (DNS) settings depend on whether there are DNS servers in the perimeter network. If DNS servers exist in the perimeter, they must have a zone containing one or more DNS A records for the next hop server or pool (that is, either a Director or a designated Front End pool), and for external queries they refer name lookups to other public DNS servers. If no DNS servers exist in the perimeter, the Edge Server(s) use external DNS servers to resolve Internet name lookups, and each Edge Server uses a HOST to resolve the next hop server names to IP addresses.
  
> [!SECURITY NOTE]
> For security reasons, we recommend that you do not have your Edge Servers access a DNS server located in the internal network. 
  
### To configure interfaces with DNS servers in the perimeter network

1. Install two network adapters for each Edge Server, one for the internal-facing interface and one for the external-facing interface. 
    
    > [!IMPORTANT]
    > The internal and external subnets must not be routable to each other. 
  
2. On the external interface, configure three static IP addresses on the external perimeter network (also known as DMZ, demilitarized zone, and screened subnet) subnet, and point the default gateway to the internal interface of the external firewall. Configure adapter DNS settings to point to a pair of perimeter DNS servers.
    
    > [!NOTE]
    > It is possible to use as few as one IP address for this interface, but to do this you need to change the port assignments to non-standard values. You determine this when you create the topology in Topology Builder. 
  
3. On the internal interface, configure one static IP address on the internal perimeter network subnet and do not set a default gateway. Configure adapter DNS settings to point to at least one DNS server, preferably a pair of perimeter DNS servers.
    
4. Create persistent static routes on the internal interface to all internal networks where clients, Lync Server 2013, and Exchange Unified Messaging (UM) servers reside.
    
### To configure interfaces without DNS servers in the perimeter network

1. Install two network adapters for each Edge Server, one for the internal-facing interface and one for the external-facing interface. 
    
    > [!IMPORTANT]
    > The internal and external subnets must not be routable to each other. 
  
2. On the external interface, configure three static IP addresses on the external perimeter network subnet. You also configure the default gateway on the external interface. For example, define the Internet-facing router or the external firewall as the default gateway. Configure DNS settings to point to a DNS server, preferably to a pair of external DNS servers.
    
    > [!NOTE]
    > It is possible, but not recommended, to use as few as one IP address for the external interface. To allow this to work, you need to change the port assignments to non-standard values, and away from the default port 443 that is typically "firewall friendly" for client communication. You determine the IP address setting and the port settings when you create the topology in Topology Builder. 
  
3. On the internal interface, configure one static IP address on the internal perimeter network subnet and do not set a default gateway. Leave adapter DNS settings empty.
    
4. Create persistent static routes on the internal interface to all internal networks where Lync clients or servers running Lync Server 2013 reside.
    
5. Edit the HOST file on each Edge Server to contain a record for the next hop server or virtual IP (VIP) (the record will be the Director, Standard Edition server, or a Front End pool that was configured as the Edge Server next hop address in Topology Builder). If you are using DNS load balancing, include a line for each member of the next hop pool.
    

