---
title: "Choosing a topology in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 23f2aeb6-fed9-4349-8fba-dcbf18ee4b04
description: "When you choose a topology, you can use one the following supported topology options:"
---

# Choosing a topology in Lync Server 2013
[]
 When you choose a topology, you can use one the following supported topology options: 
  
> [!NOTE]
> Unless otherwise noted, if you have experience with Microsoft Lync Server 2010, you will find the guidance here is largely unchanged. 
  
- [Single consolidated edge with private IP addresses and NAT in Lync Server 2013](single-consolidated-edge-with-private-ip-addresses-and-nat.md)
    
- [Single consolidated edge with public IP addresses in Lync Server 2013](single-consolidated-edge-with-public-ip-addresses.md)
    
- [Scaled consolidated edge, DNS load balancing with private IP addresses using NAT in Lync Server 2013](scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)
    
- [Scaled consolidated edge, DNS load balancing with public IP addresses in Lync Server 2013](scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)
    
- [Scaled consolidated edge with hardware load balancers in Lync Server 2013](scaled-consolidated-edge-with-hardware-load-balancers.md)
    
> [!IMPORTANT]
> The internal Edge interface and external Edge interface must use the same type of load balancing. You cannot use DNS load balancing on one Edge interface and hardware load balancing on the other Edge interface. 
  
The following table summarizes the functionality available with the supported Microsoft Lync Server 2013 topologies. The column headings indicate the functionality available for a given Edge configuration option. Using the Scaled Edge (DNS load balanced) option as an example, you can see that it supports high availability, can use non-routable private IP addresses (with NAT) or routable public IP addresses assigned to the Edge external interfaces, and reduces cost because a hardware load balancer is not required.
  
Edge failover scenarios supported with DNS Load Balancing are Lync-to-Lync point-to-point sessions, Lync conferencing sessions, Lync-to-PSTN sessions and Office 365. Edge failover scenarios that do not benefit from DNS Load Balancing are failover for remote user Exchange Unified Messaging (UM) (prior to Exchange 2010 SP1), public instant messaging (IM) connectivity, and federation with servers running Office Communications Server.
  
**Summary of Edge Server Topology Options**

|**Topology**|**High availability**|**Additional DNS A records required for external Edge Server in the Edge pool**|**Edge Failover for Lync-to-Lync sessions**|**Edge Failover for Lync-to-Lync EUM/PIC/OCS Federation sessions**|
|:-----|:-----|:-----|:-----|:-----|
|Single Edge using NAT  <br/> |No  <br/> |No  <br/> |No  <br/> |No  <br/> |
|Single Edge using Public IP  <br/> |No  <br/> |No  <br/> |No  <br/> |No  <br/> |
|Scaled Edge (DNS Load Balanced) using NAT  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |\*  <br/> |
|Scaled Edge (DNS Load Balanced) using Public IP  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |\*  <br/> |
|Scaled Edge Hardware load balanced)  <br/> |Yes  <br/> |No (one DNS A record per VIP)  <br/> |Yes  <br/> |Yes  <br/> |
   
 **\*** Failover for public instant messaging (IM) connectivity, and federation with servers running Office Communications Server is not available with DNS load balancing. Exchange UM (remote user) failover using DNS load balancing requires Exchange Server 2010 SP1 or newer. 
  
> [!NOTE]
> >  Single Edge and Scaled Edge (DNS load balanced) topologies can use: >  Routable public IP addresses >  Non-routable private IP address if symmetric network address translation (NAT) is used >  If you decide to use non-routable private IP addresses with NAT: >  You must use routable private IP addresses on all three external interfaces >  You must configure symmetric NAT for incoming and outgoing traffic >  Scaled Edge (hardware load balanced) topology must use public IP addresses. 
  
Lync Server 2013 supports placing Access, Web Conferencing, and A/V Edge external interfaces behind a router or firewall that performs network address translation (NAT) for both single and scaled consolidated Edge Server topologies.
  
Using NAT for all Edge external interfaces requires the use of DNS load balancing. When compared to using hardware load balancers, using DNS load balancing without NAT allows you to reduce the number of public IP address per Edge Server in an Edge pool as described in the following list:
  
- Lync Server 2013 Scaled Consolidated Edge (DNS load balanced) Requires three public IP addresses for each Edge Server in an Edge pool.
    
- Lync Server 2013 Scaled Consolidated Edge (hardware load balanced) Requires three public IP address for load balancer virtual IP addresses (one time requirement that does not increment as more Edge Servers are added to the pool) plus three public IP addresses per Edge Server in a pool.
    
**IP Address Requirements for Scaled Consolidated Edge (IP Address per role)**

|**Number of Edge Servers per pool**|**Number of required IP addresses Lync Server 2013 (DNS load balanced)**|**Number of required IP addresses Lync Server 2013 (hardware load balanced)**|
|:-----|:-----|:-----|
|2  <br/> |6  <br/> |3 (1 per VIP) + 6  <br/> |
|3  <br/> |9  <br/> |3 (1 per VIP) + 9  <br/> |
|4  <br/> |12  <br/> |3 (1 per VIP) + 12  <br/> |
|5  <br/> |15  <br/> |3 (1 per VIP) + 15  <br/> |
   
**IP Address Requirements for Scaled Consolidated Edge (Single IP address for all roles)**

|**Number of Edge Servers per pool**|**Number of required IP addresses Lync Server 2013 (DNS load balanced)**|**Number of required IP addresses Lync Server 2013 (hardware load balanced)**|
|:-----|:-----|:-----|
|2  <br/> |2  <br/> |1 (1 per VIP) + 2  <br/> |
|3  <br/> |3  <br/> |1 (1 per VIP) + 3  <br/> |
|4  <br/> |4  <br/> |1 (1 per VIP) + 4  <br/> |
|5  <br/> |5  <br/> |1 (1 per VIP) + 5  <br/> |
   
The primary decision points for topology selection are high availability and load balancing. The requirement for high availability can influence the load balancing decision.
  
- **High availability** If you need high availability, deploy at least two Edge Servers in a pool. A single Edge pool will support up to twelve Edge Servers. If more capacity is required, you can deploy multiple Edge pools. As a general rule, 10% of a given user base will need external access. 
    
    > [!IMPORTANT]
    > Topology Builder will allow you to configure up to twenty Edge Servers in a single Edge pool. The tested and supported maximum number of Edge Servers in a pool is twelve and Topology Builder allowing for a number larger than twelve should not be construed as implied support for more than twelve Edge Servers in a single Edge pool. 
  
- **Hardware load balancing** Hardware load balancing is supported for load balancing Lync Server 2013 Edge Servers when using publicly routable IP addresses for the Edge external interfaces. For example, you would use this approach in situations where failover is required for any of the following applications: 
    
  - Public IM connectivity
    
  - Federation with companies running Microsoft Office Communications Server 2007 or Microsoft Office Communications Server 2007 R2
    
  - External access to Exchange 2007 Unified Messaging (UM) or Exchange 2010 UM
    
    > [!IMPORTANT]
    > DNS load balancing for Exchange 2010 SP1 and newer is supported for Exchange UM. 
  
    These three applications will continue to operate, but they are not DNS load balancing aware and will only connect to the first Edge Server in the pool. If that server is unavailable, the connection will fail. For example, if multiple Edge Servers are deployed in a pool to handle the federated traffic load, only one access proxy actually receives traffic while the others are idle.
    
> [!IMPORTANT]
> Using DNS load balancing is recommended if you are federating with companies using Lync Server 2010 and Microsoft Office 365. Be aware that there are significant performance impacts if most of your federated partners are using Office Communications Server 2007 or Office Communications Server 2007 R2. 
  

