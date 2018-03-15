---
title: "Scaled consolidated edge with hardware load balancers in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6783e225-9677-415a-8731-0bf2e2c4cf8b
description: "In the Edge pool topology, two or more Edge Servers are deployed as a load-balanced pool in the perimeter network of the data center. Hardware load balancing is used for traffic to both the external and internal Edge Server interfaces."
---

# Scaled consolidated edge with hardware load balancers in Lync Server 2013
[]
In the Edge pool topology, two or more Edge Servers are deployed as a load-balanced pool in the perimeter network of the data center. Hardware load balancing is used for traffic to both the external and internal Edge Server interfaces. 
  
If your organization requires support for more than 15,000 Access Edge service client connections, 1,000 active Web Conferencing Edge service client connections, or 500 concurrent A/V Edge service sessions, and high availability of the Edge Server is important, this topology offers the advantages of scalability and failover support. 
  
The figure does not show Directors, an optional server role deployed in the internal network between the Edge Servers and your Front End pools or server. . For details about the topology for Directors, see [Components required for the Director in Lync Server 2013](components-required-for-the-director.md). 
  
> [!NOTE]
> The figure shown is for orientation and example IP addressing, but does not intend to represent actual communication flows with the correct incoming and outgoing traffic. The figure represents a high level view of possible traffic. Details for traffic flow as they pertain to incoming (to listening ports) and outgoing (to destination servers or clients) is represented in the Port Summary diagram in each scenario. For example, TCP 443 is actually inbound (to the Edge Server or reverse proxy) only, and is only a two-way flow from a protocol (TCP) perspective. Additionally, the figure shows the nature of traffic as it changes when NAT (network address translation) occurs (destination address is changed on inbound, source address is changed on outbound). Example external and internal firewall, and server interfaces are shown for reference purposes only. Finally, example default gateway and route relationships are shown, where applicable. Note also that the diagram uses the .com DNS zone to represent the external DNS zone for both reverse proxy and Edge Servers, and the .net DNS zone refers to the internal DNS zone. 
  
New to Microsoft Lync Server 2013 is support for IPv6 addressing. Much like IPv4 addressing, IPv6 addresses must be assigned in such a way that the addresses are part of your assigned IPv6 address space. The addresses in this topic are for example only. You must acquire IPv6 addresses that will function in your deployment, provide the correct scope and will interoperate with internal and external addressing. Windows Server provides a feature that is important to transitional IPv6 operation and IPv4 to IPv6 communication called the dual stack. The dual stack is a separate and distinct network stack for IPv4 and for IPv6. The dual stack is what allows you to assign addressing for IPv4 and IPv6 concurrently, and allows the server to communicate with other hosts and clients based on what their requirements are.
  
Typical address types that you will use for IPv6 addressing will be the IPv6 global addresses (similar to public IPv4 addresses), IPv6 unique local addresses (similar to the private IPv4 address ranges) and IPv6 link-local addresses (similar to automatic private IP addresses in Windows Server for IPv4) 
  
Network address translation technologies (NAT) for IPv6 exist that will allow for NAT IPv6 to IPv4 (commonly referred to as NAT64) and for NAT IPv6 to IPv6 (commonly referred to as NAT66). The existence of NAT technologies means that the five scenarios presented for Lync Server Edge Servers are still valid. 
  
> [!CAUTION]
> IPv6 is a complex topic and requires careful planning with your networking team and your Internet provider to ensure that the addresses you assign at the Windows server level and at the Lync Server 2013 level will work as expected. See the links at the end of this topic for additional resources on IPv6 addressing and planning. 
  
 **Hardware Load Balancer Configuration**
  
For details, see the "Hardware Load Balancer Requirements for A/V Edge" section in [Components required for external user access in Lync Server 2013](components-required-for-external-user-access.md).
  
**Scaled consolidated edge topology (hardware load balanced)**

![Scaled Consolidated Edge Topology](media/Plan_LyncServer_Edge_Scenario_ScaledConsolidatedEdgeHLB.jpg)
  
> [!IMPORTANT]
> If you are using Call Admission Control (CAC), you still must assign IPv4 addresses to the Edge Server internal interface. CAC uses IPv4 addresses and must have them available to operate. 
  
## In this section

- [Certificate summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013](certificate-summaryscaled-consolidated-edge-with-hardware-load-balancers.md)
    
- [Port summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013](port-summaryscaled-consolidated-edge-with-hardware-load-balancers.md)
    
- [DNS summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013](dns-summaryscaled-consolidated-edge-with-hardware-load-balancers.md)
    
## See also

#### 

[IP Version 6 Addressing Architecture](https://tools.ietf.org/html/rfc4291)
  
[IPv6 Global Unicast Address Format](https://tools.ietf.org/html/rfc3587)
  
[Unique Local IPv6 Unicast Addresses](https://tools.ietf.org/html/rfc4193)

