---
title: "Edge Server system requirements in Skype for Business Server"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Hybrid
ms.custom:
ms.assetid: ed53a566-0504-46f9-81a7-116a637833af
description: "Summary: Learn about the system requirements for Edge Server in Skype for Business Server."
---

# Edge Server system requirements in Skype for Business Server
 
**Summary:** Learn about the system requirements for Edge Server in Skype for Business Server.
  
When it comes to your Skype for Business Server Edge Server deployment, these are the things you'll need to do for the server or servers that are in the environment itself, as well as planning for the environment structure. For more information on topology, DNS, certificates, and other infrastructure concerns, check out the environmental requirements documentation.
  
## Components

When discussing the Edge Server environment, we're referencing components that are, for the most part, deployed in a perimeter network (that's to say it's either in a workgroup or a domain that's outside your Skype for Business Server domain structure).
  
Keeping that in mind, these are the components you're going to need to keep in mind for deploying your Edge successfully:
  
- [Edge Servers](system-requirements.md#EdgeServers)
    
- [Reverse proxies](system-requirements.md#ReverseProxies)
    
- [Firewalls](system-requirements.md#Firewalls)
    
- [Directors](system-requirements.md#Directors) (these are optional, and if they're included, they'll be located on your internal network)
    
- [Load Balancers](system-requirements.md#LoadBalancers) (you can have DNS load balancing or a hardware load balancer (HLB), but for a single Edge Server, this isn't needed)
    
We have more detail on each of these below:
  
### Edge Servers
<a name="EdgeServers"> </a>

These are the Skype for Business servers deployed in your perimeter environment. Their role is to send and receive network traffic to external users for the services offered by your internal Skype for Business Server deployment. To do this successfully, each Edge Server runs:
  
- **Access Edge service**: Provides a single, trusted connection point for both outbound and inbound Session Initiation Protocol (SIP) traffic.
    
- **Web Conferencing Edge service**: Enables external users to join meetings that are hosted on your internal Skype for Business Server environment.
    
- **A/V Edge service**: Makes audio, video, application sharing and file transfer available to external users.
    
- **XMPP Proxy service**: Accepts and sends extensible messaging and presence protocol (XMPP) messages to and from configured XMPP Federated partners.
    
Authorized external users can use your Edge Servers to connect to your internal Skype for Business Server deployment, but otherwise, they provide no other access to your internal network for anyone.
  
> [!NOTE]
> Edge Servers are deployed to provide connections for enabled Skype for Business clients and other Edge Servers (in federation scenarios). You can't connect from other end point client or server types. The XMPP Gateway server can allow connections with configured XMPP partners. But again, those are the only client and federation types that will work. 

> [!NOTE]
> XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migrating XMPP federation](../../../SfBServer2019/migration/migrating-xmpp-federation.md) for more information.
  
### Reverse proxies
<a name="ReverseProxies"> </a>

A reverse proxy (RP) server has no Skype for Business Server role, but is an essential component of an Edge Server deployment. A reverse proxy allows external users to:
  
- connect to meetings or dial-in conferences using simple URLs.
    
- download meeting content.
    
- expand distribution groups.
    
- get user-based certificates for client certificate based authentication
    
- download files from the Address Book Server, or to submit queries to the Address Book Web Query service.
    
- obtain updates to client and device software.
    
And for mobile devices:
  
- it lets them automatically discover Front End Servers offering mobility services.
    
- it enables push notifications from Office 365 to mobile devices.
    
Our current reverse proxy recommendations can be found on the [Telephony Infrastructure for Skype for Business](https://docs.microsoft.com/SkypeForBusiness/certification/infra-gateways) page. So your reverse proxy:
  
- should be able to use transport layer security (TLS) that's introduced to your environment via public certificates to connect to the published external Web services of:
    
  - Director or Director pool
    
  - Front End Server or Front End pool
    
- needs to be able to publish internal Web sites using certificates for encryption, or publish them over an unencrypted means, if needed.
    
- should be able to publish an internally hosted web site externally by using a fully qualified domain name (FQDN).
    
- needs to be able to publish all the contents of your hosted web site. By default, you can use the **/\\*** directive, which is recognized by most web servers to mean "Publish all content on the web server." You can also modify the directive—for example, **/Uwca/\\***, which means "Publish all content under the virtual directory Ucwa."
    
- must require TLS connections with clients that request content from your published website.
    
- has to accept certificates with subject alternative name (SAN) entries.
    
- needs to be able to allow the binding of a certificate to a listener or interface through which the external web services FQDN will resolve. Listener configurations are preferable to interfaces. Many listeners can be configured on a single interface.
    
- must allow for the configuration of host header handling. Often, the original host header sent by the requesting client must be passed transparently, instead of being modified by the reverse proxy.
    
- should allow bridging of TLS traffic from one externally defined port (for example, TCP 443) to another defined port (for example, TCP 4443). Your reverse proxy may decrypt the packet on receipt and then reencrypt the packet on sending.
    
- should allow bridging of unencrypted TCP traffic from one port (for example, TCP 80) to another (for example, TCP 8080).
    
- needs to allow configuration of, or accept, NTLM authentication, no authentication, and pass-through authentication.
    
If your reverse proxy can address all the needs in this list, you should be good to go, but please keep in mind our recommendations at the link provided above.
  
### Firewalls
<a name="Firewalls"> </a>

You need to put your Edge deployment behind an external firewall, but we recommend having two firewalls, one external, and one internal between the Edge environment and your internal environment. All our documentation in our Scenarios will have two firewalls. We recommend two firewalls because it ensures strict routing from one network edge to the other, and doubles the firewall protection for your internal network.
  
### Directors
<a name="Directors"> </a>

This is an optional role. It can be a single server or a pool of servers running the Director role. It's a role found on the internal Skype for Business Server environment.
  
The Director is an internal next hop server which receives inbound SIP traffic from the Edge Servers that's destined for Skype for Business Server internal servers. It preauthenticates inbound requests and redirects them to a user's home pool or server. This preauthentication allows you to drop unidentified user account requests.
  
Why does that matter? An important function for a Director is to protect Standard Edition servers and Front End Servers or Front End pools from malicious traffic, such as denial-of-service (DoS) attacks. If your network is flooded with invalid external traffic, the traffic stops at the Director.
  
### Load Balancers
<a name="LoadBalancers"> </a>

The Skype for Business Server scaled consolidated Edge topology is optimized for DNS load balancing for new deployments, and we recommend this. If you need high availability, we recommend using a hardware load balancer for one specific situation:
  
- Exchange UM for remote users using Exchange UM **prior** to Exchange 2013.
    
> [!IMPORTANT]
> It's vital to note that you can't mix load-balancers. In your Skype for Business Server environment all interfaces must use either DNS or HLB. 
  
> [!NOTE]
> Direct server return (DSR) NAT isn't supported for Skype for Business Server. 
  
#### hardware load balancer requirements for Edge Servers Edge Servers running the A/V Edge service

For any Edge Server running the A/V Edge service, these are the requirements:
  
- Turn off TCP nagling for both internal and external ports 443 (nagling is the process of combining several small packets into a single, larger packet for more efficient transmission).
    
- Turn off TCP nagling for the external port range 50000 - 59999.
    
- Don't use NAT on your internal or external firewalls.
    
- Your Edge internal interface must be on a different network than your Edge Server external interface, and routing between them must be disabled.
    
- The external interface of any Edge Server running the A/V Edge service must use publicly routable IP addresses and no NAT or port translation on any of the Edge external IP addresses.
    
#### HLB requirements

Skype for Business Server doesn't have a lot of cookie-based affinity requirements. So you don't need to use a cookie-based persistence **unless** (and this is Skype for Business Server 2015-specific) you're going to have Lync Server 2010 Front End Servers or Front End pools in your Skype for Business Server environment. They would need cookie-based affinity in the configuration method recommended for Lync Server 2010.
  
> [!NOTE]
> If you decide to turn cookie-based affinity on for your HLB, there won't be a problem doing so, even if your environment doesn't need it. 
  
If your environment **doesn't** need cookie-based affinity:
  
- On the reverse proxy publishing rule for port 443, set **Forward host header** to **True**. This will ensure the original URL is forwarded.
    
For deployments that **do** need cookie-based affinity:
  
- On the reverse proxy publishing rule for port 443, set **Forward host header** to **True**. This will ensure the original URL is forwarded.
    
- The hardware load balancer cookie **must not** be marked httpOnly.
    
- The hardware load balancer cookie **must not** have an expiration time.
    
- The hardware load balancer cookie **must** be named **MS-WSMAN** (this is the value that the Web services expect, and it can't be changed).
    
- The hardware load balancer cookie **must** be set in every HTTP response for which the incoming HTTP request didn't have a cookie, regardless of whether a previous HTTP response on that same TCP connection had gotten a cookie. If your hardware load balancer optimizes cookie insert to only occur once per TCP connection, that optimization **must not** be used.
    
> [!NOTE]
> It's typical for HLB configurations to use source-affinity and 20 minute TCP session lifetime, which is fine for Skype for Business Server and its clients, because session state is maintained through client usage, and/or application interaction. 
  
If you're deploying mobile devices, your HLB must be able to load balance individual requests within a TCP session (in effect, you need to be able to load balance an individual request based on the target IP address).
  
> [!IMPORTANT]
> F5 HLBs have a feature called OneConnect. It ensures that each request within a TCP connection is individually load balanced. If you're deploying mobile devices, ensure your HLB vendor supports the same functionality. The latest iOS mobile apps require TLS version 1.2. If you need to know more, F5 provides specific settings for this. 
  
Here are the HLB requirements for the (optional) Director and (required) Front End pool Web Services:
  
- For your internal Web Services VIPs, set Source_addr persistence (internal port 80, 443) on your HLB. For Skype for Business Server, Source_addr persistence means that multiple connections coming from a single IP address are always sent to one server, to maintain session state.
    
- Use a TCP idle timeout of 1800 seconds.
    
- On the firewall between your reverse proxy and your next hop pool's HLB, create a rule to allow https: traffic on port 4443, from your reverse proxy to your HLB. Your HLB needs to be configured to listen on ports 80, 443, and 4443.
    
#### Summary of HLB affinity requirements

|**Client/user location**|**External web services FQDN affinity requirements**|**Internal web services FQSN affinity requirements**|
|:-----|:-----|:-----|
|Skype for Business Web App (internal and external users)  <br/> Mobile device (internal and external users  <br/> |No affinity  <br/> |Source address affinity  <br/> |
|Skype for Business Web App (external users only)  <br/> Mobile device (internal and external users  <br/> |No affinity  <br/> |Source address affinity  <br/> |
|Skype for Business Web App (internal users only)  <br/> Mobile device (not deployed)  <br/> |No affinity  <br/> |Source address affinity  <br/> |
   
#### Port monitoring for HLBs

You define port monitoring on your hardware load balancers to determine when specific services are no longer available, due to hardware or communications failure. For example, if the Front End Server service (RTCSRV) stops because the Front End Server or Front End pool fails, the HLB monitoring should also stop receiving traffic on the Web Services. You should implement port monitoring on the HLB to monitor the following for your HLB external interface:
  
|**Virtual IP/Port**|**Node Port**|**Node Machine/Monitor**|**Persistence Profile**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|\<pool\>web_mco_443_vs  <br/> 443  <br/> |4443  <br/> |Front End  <br/> 5061  <br/> |None  <br/> |HTTPS  <br/> |
|\<pool\>web_mco_80_vs  <br/> 80  <br/> |8080  <br/> |Front End  <br/> 5061  <br/> |None  <br/> |HTTP  <br/> |
   
## Hardware and software requirements

We've covered Edge Server hardware and software requirements in our overall [Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md) and  [System requirements for Skype for Business Server 2019](../../../SfBServer2019/plan/system-requirements.md) documentation.
  
## Collocation

We've covered Edge Server collocation in our [Topology Basics for Skype for Business Server](../../plan-your-deployment/topology-basics/topology-basics.md) documentation.
  

