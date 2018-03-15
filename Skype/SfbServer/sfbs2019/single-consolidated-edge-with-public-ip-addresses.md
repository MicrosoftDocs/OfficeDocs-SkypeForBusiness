---
title: "Single consolidated edge with public IP addresses in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a92d1179-6a1f-4efe-908a-f8dfc5024f30
description: "If your organization needs support for fewer than 15,000 Access Edge service client connections, 1,000 active Lync Server Web Conferencing service client connections, and 500 concurrent A/V Edge sessions, and high availability of the Edge Server is not important, this topology offers the advantages of lower hardware cost and simpler deployment. If you need greater capacity or you require high availability, you should deploy a scaled consolidated Edge Server topology."
---

# Single consolidated edge with public IP addresses in Lync Server 2013
[]
If your organization needs support for fewer than 15,000 Access Edge service client connections, 1,000 active Lync Server Web Conferencing service client connections, and 500 concurrent A/V Edge sessions, and high availability of the Edge Server is not important, this topology offers the advantages of lower hardware cost and simpler deployment. If you need greater capacity or you require high availability, you should deploy a scaled consolidated Edge Server topology. 
  
> [Scaled consolidated edge, DNS load balancing with private IP addresses using NAT in Lync Server 2013](scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)
    
> [Scaled consolidated edge, DNS load balancing with public IP addresses in Lync Server 2013](scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)
    
> [Scaled consolidated edge with hardware load balancers in Lync Server 2013](scaled-consolidated-edge-with-hardware-load-balancers.md)
    
> [!IMPORTANT]
> When using public IP address on the Edge Server, the default gateway on the Edge Server is no longer your firewall or router, but the router or firewall at your public perimeter edge - which will be a public address. The reverse proxy continues to use the router or firewall associated with the outermost perimeter network. The difference between the reverse proxy and the Edge Server with public IP addresses is that the reverse proxy is still using NAT and the Edge Server is using a route relationship. 
  
The figure does not show Directors, an optional server role deployed in the internal network between the Edge Servers and your Front End pools or server. For details about the topology for Directors, see [Components required for the Director in Lync Server 2013](components-required-for-the-director.md). The figure represents a single reverse proxy.
  
> [!NOTE]
> The figure shown is for orientation and example IP addressing, but does not intend to represent actual communication flows with the correct incoming and outgoing traffic. The figure represents a high level view of possible traffic. Details for traffic flow as they pertain to incoming (to listening ports) and outgoing (to destination servers or clients) is represented in the Port Summary diagram in each scenario. For example, TCP 443 is actually inbound (to the Edge or reverse proxy) only, and is only a two-way flow from a protocol (TCP) perspective. Additionally, the figure shows the nature of traffic as it changes when NAT (network address translation) occurs (destination address is changed on inbound, source address is changed on outbound). Example external and internal firewall, and server interfaces are shown for reference purposes only. Finally, example default gateway and route relationships are shown, where applicable. Note also that the diagram uses the .com DNS zone to represent the external DNS zone for both reverse proxy and Edge Servers, and the .net DNS zone refers to the internal DNS zone. 
  
New to Microsoft Lync Server 2013 is support for IPv6 addressing. Much like IPv4 addressing, IPv6 addresses must be assigned in such a way that the addresses are part of your assigned IPv6 address space. The addresses in this topic are for example only. You must acquire IPv6 addresses that will function in your deployment, provide the correct scope and will interoperate with internal and external addressing. Windows Server provides a feature that is important to transitional IPv6 operation and IPv4 to IPv6 communication called the dual stack. The dual stack is a separate and distinct network stack for IPv4 and for IPv6. The dual stack is what allows you to assign addressing for IPv4 and IPv6 concurrently, and allows the server to communicate with other hosts and clients based on what their requirements are.
  
Typical address types that you will use for IPv6 addressing will be the IPv6 global addresses (similar to public IPv4 addresses), IPv6 unique local addresses (similar to the private IPv4 address ranges) and IPv6 link-local addresses (similar to automatic private IP addresses in Windows Server for IPv4) 
  
Network address translation technologies (NAT) for IPv6 exist that will allow for NAT IPv6 to IPv4 (commonly referred to as NAT64) and for NAT IPv6 to IPv6 (commonly referred to as NAT66). The existence of NAT technologies means that the five scenarios presented for Lync Server Edge Servers are still valid. 
  
> [!CAUTION]
> IPv6 is a complex topic and requires careful planning with your networking team and your Internet provider to ensure that the addresses you assign at the Windows server level and at the Lync Server 2013 level will work as expected. See the links at the end of this topic for additional resources on IPv6 addressing and planning. 
  
**Single Consolidated Edge with Public IP Addresses topology**

![Edge Scenario for Single Consolidated Edge](media/Plan_LyncServer_Edge_Scenario_SingleConsolidatedEdgePublicIP.jpg)
  
> [!IMPORTANT]
> If you are using Call Admission Control (CAC), you still must assign IPv4 addresses to the Edge Server internal interface. CAC uses IPv4 addresses and must have them available to operate. 
  
## In this section

- [Certificate summary - Single consolidated edge with public IP addresses in Lync Server 2013](certificate-summarysingle-consolidated-edge-with-public-ip-addresses.md)
    
- [Port summary - Single consolidated edge with public IP addresses in Lync Server 2013](port-summarysingle-consolidated-edge-with-public-ip-addresses.md)
    
- [DNS summary - Single consolidated edge with public IP addresses in Lync Server 2013](dns-summarysingle-consolidated-edge-with-public-ip-addresses.md)
    
## See also

#### 

[IP Version 6 Addressing Architecture](https://tools.ietf.org/html/rfc4291)
  
[IPv6 Global Unicast Address Format](https://tools.ietf.org/html/rfc3587)
  
[Unique Local IPv6 Unicast Addresses](https://tools.ietf.org/html/rfc4193)

