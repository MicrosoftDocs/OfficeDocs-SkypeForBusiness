---
title: Load balancing requirements for Skype for Business
ms.prod: SKYPEFORBUSINESS
ms.assetid: 84489328-64a4-486c-9384-a3e5c8ed9c8b
---


# Load balancing requirements for Skype for Business
[] **Summary:** Review the load balancing considerations before implementing Skype for Business Server 2015.
If you have Front End pools, Mediation Server pools, or Edge Server pools, you need to deploy load balancing for these pools. Load balancing distributes the traffic among the servers in a pool.
  
    
    

Skype for Business Server supports two types of load balancing solutions for client-to-server traffic: Domain Name System (DNS) load balancing and hardware load balancing. DNS load balancing offers several advantages including simpler administration, more efficient troubleshooting, and the ability to isolate much of your Skype for Business Server traffic from any potential hardware load balancer problems.
Decide which load balancing solution is appropriate for each pool in your deployment, keeping in mind the following restrictions: 
  
    
    


- The internal Edge interface and external Edge interface must use the same type of load balancing. You cannot use DNS load balancing on one interface and hardware load balancing on the other.
    
  
- Some types of traffic require a hardware load balancer. For example, HTTP traffic requires a hardware load balancer instead of DNS load balancing. DNS load balancing does not work with client-to-server web traffic.
    
  
If you choose to use DNS load balancing for a pool but still need to implement hardware load balancers for traffic such as HTTP traffic, the administration of the hardware load balancers is greatly simplified. For example, configuring the hardware load balancer will be simpler as it will only manage the HTTP and HTTPS traffic, while all other protocols will be managed by DNS load balancing. For details, see  [DNS Load Balancing](http://technet.microsoft.com/library/7ed0ed20-33ad-4253-926d-21d392590ae7.aspx). For server-to-server traffic, Skype for Business Server uses topology-aware load balancing. Servers read the published topology in the Central Management store to obtain the FQDNs of servers in the topology, and automatically distribute the traffic among the servers. Administrators do not need to set up or manage this type of load balancing. If you use DNS load balancing and you need to block traffic to a specific computer, it is not sufficient to just remove the IP address entries from the Pool FQDN. You must remove the DNS entry for the computer as well. 
## Hardware load balancer requirements

The Skype for Business Server scaled consolidated Edge topology is optimized for DNS load balancing for new deployments federating primarily with other organizations using Skype for Business Server or Lync Server. If high availability is required for any of the following scenarios, a hardware load balancer must be used on Edge Server pools for the following: 
  
    
    

- Federation with organizations using Office Communications Server 2007 R2 or Office Communications Server 2007
    
  
- Exchange UM for remote users using Exchange UM prior to Exchange 2010 with SP1
    
  
- Connectivity to public IM users
    
  

> [!IMPORTANT]
> Using DNS load balancing on one interface and hardware load balancing on the other is not supported. You must use hardware load balancing for both interfaces or DNS load balancing for both. 
  
    
    


> [!NOTE]
> If you are using a hardware load balancer, the load balancer deployed for connections with the internal network must be configured to load balance only the traffic to servers running the Access Edge service and the A/V Edge service. It cannot load balance the traffic to the internal Web Conferencing Edge service or the internal XMPP Proxy service. 
  
    
    


> [!NOTE]
> The direct server return (DSR) NAT is not supported with Skype for Business Server. 
  
    
    

To determine whether your hardware load balancer supports the necessary features required by Skype for Business Server, see  [Infrastructure for Skype for Business](https://technet.microsoft.com/en-us/office/dn947483).
  
    
    

### Hardware Load Balancer Requirements for Edge Servers Running the A/V Edge Service

Following are the hardware load balancer requirements for Edge Servers running the A/V Edge service:
  
    
    

- Turn off TCP nagling for both internal and external ports 443. Nagling is the process of combining several small packets into a single, larger packet for more efficient transmission.
    
  
- Turn off TCP nagling for external port range 50,000 - 59,999. 
    
  
- Do not use NAT on the internal or external firewall. 
    
  
- The edge internal interface must be on a different network than the Edge Server external interface and routing between them must be disabled. 
    
  
- The external interface of the Edge Server running the A/V Edge Service must use publically routable IP addresses and no NAT or port translation on any of the edge external IP addresses. 
    
  
- The load balancer must not change the source address of the client.
    
  

### Hardware Load Balancer Requirements

Cookie-based affinity requirements are greatly reduced in Skype for Business Server for Web services. If you are deploying Skype for Business Server and will not retain any Lync Server 2010 Front End Servers or Front End pools, you do not need cookie-based persistence. However, if you will temporarily or permanently retain any Lync Server 2010 Front End Servers or Front End pools, you still use cookie-based persistence as it is deployed and configured for Lync Server 2010. 
  
    
    

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
> F5 hardware load balancers have a feature called OneConnect that ensures each request within a TCP connection is individually load balanced. If you are deploying mobile devices, ensure your hardware load balancer vendor supports the same functionality. The latest Apple iOS mobile apps require Transport Layer Security (TLS) version 1.2. F5 provides specific settings for this. > For details on third party hardware load balancers, see  [Infrastructure for Skype for Business](https://technet.microsoft.com/en-us/office/dn947483). 
  
    
    

Following are the hardware load balancer requirements for Director and Front End pool Web Services:
  
    
    

- For internal Web Services VIPs, set Source_addr persistence (internal port 80, 443) on the hardware load balancer. For Skype for Business Server, Source_addr persistence means that multiple connections coming from a single IP address are always sent to one server to maintain session state.
    
  
- Use TCP idle timeout of 1800 seconds.
    
  
- On the firewall between the reverse proxy and the next hop pool's hardware load balancer, create a rule to allow https: traffic on port 4443, from the reverse proxy to the hardware load balancer. The hardware load balancer must be configured to listen on ports 80, 443, and 4443.
    
  

### Summary of Hardware Load Balancer Affinity Requirements



|**Client/user location**|**External web services FQDN affinity requirements**|**Internal web services FQDN affinity requirements**|
|:-----|:-----|:-----|
|Lync Web App (internal and external users)  <br/> Mobile device (internal and external users)  <br/> |No affinity  <br/> |Source address affinity  <br/> |
|Lync Web App (external users only)  <br/> Mobile device (internal and external users)  <br/> |No affinity  <br/> |Source address affinity  <br/> |
|Lync Web App (internal users only)  <br/> Mobile device (not deployed)  <br/> |No affinity  <br/> |Source address affinity  <br/> |
   

### Port Monitoring for Hardware Load Balancers

You define port monitoring on the hardware load balancers to determine when specific services are no longer available due to hardware or communications failure. For example, if the Front End Server service (RTCSRV) stops because the Front End Server or Front End pool fails, the HLB monitoring should also stop receiving traffic on the Web Services. You implement port monitoring on the HLB to monitor the following:
  
    
    

**Front End Server User Pool - HLB Internal Interface**


|**Virtual IP/Port**|**Node Port**|**Node Machine/Monitor**|**Persistence Profile**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|<pool>web-int_mco_443_vs  <br/> 443  <br/> |443  <br/> |Front End  <br/> 5061  <br/> |Source  <br/> |HTTPS  <br/> |
|<pool>web-int_mco_80_vs  <br/> 80  <br/> |80  <br/> |Front End  <br/> 5061  <br/> |Source  <br/> |HTTP  <br/> |
   

**Front End Server User Pool - HLB External Interface**


|**Virtual IP/Port**|**Node Port**|**Node Machine/Monitor**|**Persistence Profile**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|<pool>web_mco_443_vs  <br/> 443  <br/> |4443  <br/> |Front End  <br/> 5061  <br/> |None  <br/> |HTTPS  <br/> |
|<pool>web_mco_80_vs  <br/> 80  <br/> |8080  <br/> |Front End  <br/> 5061  <br/> |None  <br/> |HTTP  <br/> |
   

