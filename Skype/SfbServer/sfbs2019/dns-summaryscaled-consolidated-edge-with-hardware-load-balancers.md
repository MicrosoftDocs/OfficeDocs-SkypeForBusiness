---
title: "DNS summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8453297c-da1d-4b9e-a37e-6721458c6feb
description: "DNS record requirements for remote access to Lync Server 2013 are fairly straightforward compared to those for certificates and ports. Also, many records are optional, depending on how you configure clients running Lync 2013 and whether you enable federation."
---

# DNS summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013
[]
DNS record requirements for remote access to Lync Server 2013 are fairly straightforward compared to those for certificates and ports. Also, many records are optional, depending on how you configure clients running Lync 2013 and whether you enable federation.
  
For details about Lync 2013 DNS requirements, see [Determine DNS requirements for Lync Server 2013](determine-dns-requirements.md).
  
For details about configuring automatic configuration of Lync 2013 clients if split-brain DNS is not configured, see the "Automatic Configuration without Split Brain DNS" section in [Determine DNS requirements for Lync Server 2013](determine-dns-requirements.md).
  
The following table contains a summary of the DNS records that are required to support the Scaled Consolidated Edge Topology (Hardware Load Balanced) figure. Note that certain DNS records are required only for automatic configuration for Lync clients. If you plan to use group policy objects (GPOs) to configure Lync clients, the associated records are not necessary.
  
## IMPORTANT: Edge Server Network Adapter Requirements

To avoid routing issues, verify that there are at least two network adapters in your Edge Servers and that the default gateway is set only on the network adapter associated with the external interface. For example, as shown in the Scaled Consolidated Edge Scenario figure in [Scaled consolidated edge with hardware load balancers in Lync Server 2013](scaled-consolidated-edge-with-hardware-load-balancers.md), the default gateway would point to the external firewall.
  
You can configure two network adapters in each of your Edge Servers as follows:
  
- **Network adapter 1 (Internal Interface)**
    
    Internal interface with 172.25.33.10 assigned.
    
    No default gateway.
    
    Ensure there is a route from the network containing the Edge Server internal interface to any networks that contain Lync Server clients or servers running Lync Server (for example, from 172.25.33.0 to 192.168.10.0).
    
- **Network adapter 2 (External Interface)**
    
    Three public IP addresses are assigned to this network adapter, for example 131.107.155.10 for Access Edge service, 131.107.155.20 for Web Conferencing Edge service, 131.107.155.30 for A/V Edge service. 
    
    > [!NOTE]
    > The IP addresses that are assigned to the actual external network interfaces of the Edge Server may depend on which hardware load balancer you choose. Refer to the documentation for your hardware load balancer to understand the actual IP address requirements. > It is possible, though not recommended, to use a single IP address for all three Edge service interfaces. Though this does save IP addresses, it requires different port numbers for each service. The default port number is 443/TCP, which ensures that most remote firewalls will allow the traffic. Changing the port values to (for example) 5061/TCP for the Access Edge service, 444/TCP for the Web Conferencing Edge service and 443/TCP for the A/V Edge service might cause problems for remote users where a firewall that they are behind does not allow the traffic over 5061/TCP and 444/TCP. Additionally, three distinct IP addresses makes troubleshooting easier due to being able to filter on IP address. 
  
    Access Edge service IP address is primary with default gateway set to Internet-facing router (131.107.155.1). 
    
    Web Conferencing Edge service and A/V Edge service IP addresses secondary.
    
> [!TIP]
> Configuring the Edge Server with two network adapters is one of two options. The other option is to use one network adapter for the internal side and three network adapters for the external side of the Edge Server. The main benefit of this option is a distinct network adapter per Edge Server service, and potentially more concise data collection when troubleshooting is necessary 
  
**DNS Records Required for Scaled Consolidated Edge, Hardware Load Balanced (Example)**

|**Location/TYPE/Port**|**FQDN/DNS Record**|**IP Address/FQDN**|**Maps to/Comments**|
|:-----|:-----|:-----|:-----|
|External DNS/A  <br/> |sip.contoso.com  <br/> |131.107.155.10  <br/> |Access Edge service external interface (Contoso). Repeat as necessary for all SIP domains with Lync enabled users  <br/> |
|External DNS/A  <br/> |webcon.contoso.com  <br/> |131.107.155.20  <br/> |Web Conferencing Edge service external interface  <br/> |
|External DNS/A  <br/> |av.contoso.com  <br/> |131.107.155.30  <br/> |A/V Edge service external interface  <br/> |
|External DNS/SRV/443  <br/> |_sip._tls.contoso.com  <br/> |sip.contoso.com  <br/> |Access Edge service external interface. Required for automatic configuration of Lync 2013 and Lync 2010 clients to work externally. Repeat as necessary for all SIP domains with Lync enabled users.  <br/> |
|External DNS/SRV/5061  <br/> |_sipfederationtls._tcp.contoso.com  <br/> |sip.contoso.com  <br/> |SIP Access Edge service external interface Required for automatic DNS discovery of federated partners known as "Allowed SIP Domain" (called enhanced federation in previous releases). Repeat as necessary for all SIP domains with Lync enabled users and Microsoft Lync Mobile clients that use either the Push Notification Service or the Apple Push Notification service  <br/> |
|Internal DNS/A  <br/> |lsedge.contoso.net  <br/> |172.25.33.10  <br/> |Consolidated Edge internal interface  <br/> |
   

