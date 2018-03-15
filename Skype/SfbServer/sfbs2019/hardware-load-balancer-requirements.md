---
title: "Hardware load balancer requirements for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 32891268-2059-43d0-adf4-af4ff1e9ce66
description: "In this articleHardware Load Balancer Requirements for Edge Servers Running the A/V Edge ServiceHardware Load Balancer RequirementsSummary of Hardware Load Balancer Affinity RequirementsPort Monitoring for Hardware Load Balancers"
---

# Hardware load balancer requirements for Lync Server 2013
[]
 **In this article**
  
[Hardware Load Balancer Requirements for Edge Servers Running the A/V Edge Service](#sectionSection0)
  
[Hardware Load Balancer Requirements](#sectionSection1)
  
[Summary of Hardware Load Balancer Affinity Requirements](#sectionSection2)
  
[Port Monitoring for Hardware Load Balancers](#sectionSection3)
  
The Lync Server 2013 scaled consolidated Edge topology is optimized for DNS load balancing for new deployments federating primarily with other organizations using Lync Server. If high availability is required for any of the following scenarios, a hardware load balancer must be used on Edge Server pools for the following: 
  
- Federation with organizations using Office Communications Server 2007 R2 or Office Communications Server 2007
    
- Exchange UM for remote users using Exchange UM prior to Exchange 2010 with SP1
    
- Connectivity to public IM users
    
> [!IMPORTANT]
> Using DNS load balancing on one interface and hardware load balancing on the other is not supported. You must use hardware load balancing for both interfaces or DNS load balancing for both. 
  
> [!NOTE]
> If you are using a hardware load balancer, the load balancer deployed for connections with the internal network must be configured to load balance only the traffic to servers running the Access Edge service and the A/V Edge service. It cannot load balance the traffic to the internal Web Conferencing Edge service or the internal XMPP Proxy service. 
  
> [!NOTE]
> The direct server return (DSR) NAT is not supported with Lync Server 2013. 
  
To determine whether your hardware load balancer supports the necessary features required by Lync Server 2013, see "Lync Server 2010 Load Balancer Partners" at [https://go.microsoft.com/fwlink/p/?linkId=202452](https://go.microsoft.com/fwlink/p/?linkId=202452).
  
## Hardware Load Balancer Requirements for Edge Servers Running the A/V Edge Service
<a name="sectionSection0"> </a>

Following are the hardware load balancer requirements for Edge Servers running the A/V Edge service:
  
- Turn off TCP nagling for both internal and external ports 443. Nagling is the process of combining several small packets into a single, larger packet for more efficient transmission.
    
- Turn off TCP nagling for external port range 50,000 - 59,999. 
    
- Do not use NAT on the internal or external firewall. 
    
- The edge internal interface must be on a different network than the Edge Server external interface and routing between them must be disabled. 
    
- The external interface of the Edge Server running the A/V Edge Service must use publically routable IP addresses and no NAT or port translation on any of the edge external IP addresses. 
    
## Hardware Load Balancer Requirements
<a name="sectionSection1"> </a>

Cookie-based affinity requirements are greatly reduced in Lync Server 2013 for Web services. If you are deploying Lync Server 2013 and will not retain any Lync Server 2010 Front End Servers or Front End pools, you do not need cookie-based persistence. However, if you will temporarily or permanently retain any Lync Server 2010 Front End Servers or Front End pools, you still use cookie-based persistence as it is deployed and configured for Lync Server 2010. 
  
> [!NOTE]
> **If you decide to use cookie-based affinity even though your deployment does not require it**, there is no negative impact to doing so. 
  
For deployments that **will not use** cookie-based affinity: 
  
- On the reverse proxy publishing rule for port 4443, set **Forward host header** to True. This will ensure that the original URL is forwarded. 
    
For deployments that **will use** cookie-based affinity: 
  
- On the reverse proxy publishing rule for port 4443, set **Forward host header** to True. This will ensure that the original URL is forwarded. 
    
- Hardware load balancer cookie MUST NOT be marked httpOnly
    
- Hardware load balancer cookie MUST NOT have an expiration time
    
- Hardware load balancer cookie MUST be named **MS-WSMAN** (This is the value that the Web services expect, and cannot be changed) 
    
- Hardware load balancer cookie MUST be set in every HTTP response for which the incoming HTTP request did not have a cookie, regardless of whether a previous HTTP response on that same TCP connection had already obtained a cookie. If the load balancer optimizes cookie insert to only occur once per TCP connection, that optimization MUST NOT be used
    
> [!NOTE]
> Typical hardware load balancer configurations use source-address affinity and a 20 min. TCP session lifetime, which is fine for Lync Server and Lync 2013 clients because session state is maintained through client usage and/or and application interaction. 
  
If you are deploying mobile devices, your hardware load balancer must be able to load balance individual request within a TCP session (in effect, you must be able to load balance an individual request based on the target IP address).
  
> [!CAUTION]
> F5 hardware load balancers have a feature called OneConnect that ensures each request within a TCP connection is individually load balanced. If you are deploying mobile devices, ensure your hardware load balancer vendor supports the same functionality. The latest Apple iOS mobile apps require Transport Layer Security (TLS) version 1.2. F5 provides specific settings for this. > For details on third party hardware load balancers, see [https://go.microsoft.com/fwlink/p/?linkId=230700](https://go.microsoft.com/fwlink/p/?linkId=230700)
  
Following are the hardware load balancer requirements for Director and Front End pool Web Services:
  
- For internal Web Services VIPs, set Source_addr persistence (internal port 80, 443) on the hardware load balancer. For Lync Server 2013, Source_addr persistence means that multiple connections coming from a single IP address are always sent to one server to maintain session state.
    
- Use TCP idle timeout of 1800 seconds.
    
- On the firewall between the reverse proxy and the next hop pool's hardware load balancer, create a rule to allow https: traffic on port 4443, from the reverse proxy to the hardware load balancer. The hardware load balancer must be configured to listen on ports 80, 443, and 4443.
    
> [!IMPORTANT]
> For further reading on configuration of the hardware load balancer, please review [Port summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013](port-summaryscaled-consolidated-edge-with-hardware-load-balancers.md). 
  
## Summary of Hardware Load Balancer Affinity Requirements
<a name="sectionSection2"> </a>

|**Client/user location**|**External web services FQDN affinity requirements**|**Internal web services FQDN affinity requirements**|
|:-----|:-----|:-----|
|Lync Web App (internal and external users)  <br/> Mobile device (internal and external users)  <br/> |No affinity  <br/> |Source address affinity  <br/> |
|Lync Web App (external users only)  <br/> Mobile device (internal and external users)  <br/> |No affinity  <br/> |Source address affinity  <br/> |
|Lync Web App (internal users only)  <br/> Mobile device (not deployed)  <br/> |No affinity  <br/> |Source address affinity  <br/> |
   
## Port Monitoring for Hardware Load Balancers
<a name="sectionSection3"> </a>

You define port monitoring on the hardware load balancers to determine when specific services are no longer available due to hardware or communications failure. For example, if the Front End Server service (RTCSRV) stops because the Front End Server or Front End pool fails, the HLB monitoring should also stop receiving traffic on the Web Services. You implement port monitoring on the HLB to monitor the following:
  
**Front End Server User Pool - HLB Internal Interface**

|**Virtual IP/Port**|**Node Port**|**Node Machine/Monitor**|**Persistence Profile**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|\<pool\>web-int_mco_443_vs  <br/> 443  <br/> |443  <br/> |Front End  <br/> 5061  <br/> |Source  <br/> |HTTPS  <br/> |
|\<pool\>web-int_mco_80_vs  <br/> 80  <br/> |80  <br/> |Front End  <br/> 5061  <br/> |Source  <br/> |HTTP  <br/> |
   
**Front End Server User Pool - HLB External Interface**

|**Virtual IP/Port**|**Node Port**|**Node Machine/Monitor**|**Persistence Profile**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|\<pool\>web_mco_443_vs  <br/> 443  <br/> |4443  <br/> |Front End  <br/> 5061  <br/> |None  <br/> |HTTPS  <br/> |
|\<pool\>web_mco_80_vs  <br/> 80  <br/> |8080  <br/> |Front End  <br/> 5061  <br/> |None  <br/> |HTTP  <br/> |
   

