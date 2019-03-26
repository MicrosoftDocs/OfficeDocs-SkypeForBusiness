---
title: "Advanced Edge Server DNS planning for Skype for Business Server"
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
ms.assetid: f3a5895f-f64f-44eb-9a5e-8d606ac1fc38
description: "Summary: Review scenarios for Skype for Business Server deployment options. Whether you want a single server or prefer a server pool with DNS or HLB, this topic should help."
---

# Advanced Edge Server DNS planning for Skype for Business Server
 
**Summary:** Review scenarios for Skype for Business Server deployment options. Whether you want a single server or prefer a server pool with DNS or HLB, this topic should help.
  
When it comes to Domain Name System (DNS) planning for Skype for Business Server, there are a lot of factors that may play into your decision. If your organization's domain structure's already in place, this may be a matter of reviewing how you're going to proceed. We'll begin with the topics found below:
  
- [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/network-requirements/advanced-edge-server-dns.md#WalkthroughOfSkype)
    
- [Split-brain DNS](../../plan-your-deployment/network-requirements/advanced-edge-server-dns.md#SplitBrainDNS)
    
- [Automatic configuration without split-brain DNS](../../plan-your-deployment/network-requirements/advanced-edge-server-dns.md#NoSplitBrainDNS)
    
- [DNS disaster recovery](../../plan-your-deployment/network-requirements/advanced-edge-server-dns.md#DNSDR)
    
- [DNS load balancing](../../plan-your-deployment/network-requirements/advanced-edge-server-dns.md#DNSLB)
    
## Walkthrough of Skype for Business clients locating services
<a name="WalkthroughOfSkype"> </a>

Skype for Business clients are similar to previous versions of Lync clients in how they find and access services in Skype for Business Server. This section details the server location process.
  
1. lyncdiscoverinternal.\<domain\>
    
     *This is an A host record for the Autodiscover service on the internal web services.* 
    
2. lyncdiscover.\<domain\>
    
     *This is an A host record for the Autodiscover service on the external web services.* 
    
3. _sipinternaltls._tcp.\<domain\>
    
     *This is a SRV record for internal TLS connections.* 
    
4. _sip._tls.\<domain\>
    
     *This is a SRV record for external TLS connections.* 
    
5. sipinternal.\<domain\>
    
     *This is an A host record for the Front End pool or Director, resolvable only on the internal network.* 
    
6. sip.\<domain\>
    
     *This is an A host record for the Front End pool or Director, resolvable only on the internal network.* 
    
7. sipexternal.\<domain\>
    
     *This is an A host record for the Access Edge service, when the client is external.* 
    
The Autodiscover service is always favored as that's the preferred method for service location, and the others are fallback methods.
  
> [!NOTE]
> When you're creating SRV records, it's important to remember that they need to point to a DNS A (and AAAA if you're using IPv6 addressing) in the same domain in which the DNS SRV record's being created. For example, if they SRV record's in contoso.com, the A (and AAAA) record it points to can't be in fabrikam.com. 
  
If you're inclined to do it, you can set your mobile device up for manual discovery of services. If that's what you're looking to do, each user needs to configure their mobile device settings with the full internal and external Autodiscover service URIs, including the protocol and path, as follows:
  
- For external access: https://\<ExtPoolFQDN\>/Autodiscover/autodiscoverservice.svc/Root
    
- For internal access: https://\<IntPoolFQDN\>/AutoDiscover/AutoDiscover.svc/Root
    
We do recommend you use automatic discovery as opposed to manual discovery. But if you're doing some troubleshooting or testing, manual settings can be very helpful.
  
## Split-brain DNS
<a name="SplitBrainDNS"> </a>

This is a DNS configuration where you have two DNS zones with the same namespace. The first DNS zone handles internal requests, while the second DNS zone handles external requests.
  
Why would a company do this? They may have a requirement to use the same namespace internally and externally, but of course this will lead to many DNS SRV and A records being unique to one zone or another, and where there is duplication, the IP addresses associated with these records would be unique.
  
This presents some challenges. The most important is that split-brain DNS is **not supported** for Mobility. This is because of the LyncDiscover and LyncDiscoverInternal DNS records (LyncDiscover has to be defined on you external DNS server, while LyncDiscoverInternal has to be defined on your internal DNS server).
  
We'll list the DNS records for the internal and external zones here, but you can find detailed examples on the Edge Server environmental requirements section.
  
### Internal DNS

- Contains a DNS zone called (for example) contoso.com, for which it's authoritative.
    
- This internal contoso.com contains:
    
  - DNS A and AAAA (if you're using IPv6 addressing) records for your Front End pool, Director pool or Director pool name, and all internal servers running Skype for Business Server in your organization's network.
    
  - DNS A and AAAA (if you're using IPv6 addressing) records for your Edge internal interface for each Skype for Business Server Edge Server in your perimeter network.
    
  - DNS A and AAAA (if you're using IPv6 addressing) records for the internal interface of each reverse proxy server in your perimeter network (which is **optional** for management of a reverse proxy).
    
  - DNS A and AAAA (if you're using IPv6 addressing) and SRV records for internal Skype for Business Server client autoconfiguration (which is **optional** ).
    
  - DNS A and AAAA (if you're using IPv6 addressing) or CNAME records for automatic discovery of Skype for Business Server Web Services (which is **optional** ).
    
- All your Skype for Business Server internal Edge interfaces in your perimeter network use this internal DNS zone for resolving queries to contoso.com.
    
- All servers running Skype for Business Server, and clients running Skype for Business Server in the corporate network, point to internal DNS servers for resolving queries to contoso.com, or they use the Host file on each Edge Server and list A and AAAA (if you're using IPv6 addressing) records for the next hop server (specifically for the Director or Director pool VIP, Front End pool VIP, or Standard Edition server).
    
### External DNS

- Contains a DNS zone called (for example) contoso.com, for which it's authoritative.
    
- This external contoso.com contains:
    
  - DNS A and AAAA (if you're using IPv6 addressing), or CNAME records, for automatic discovery of Skype for Business Server web services. This is for use with mobility.
    
  - DNS A and AAAA (if you're using IPv6 addressing) and SRV records for the Edge external interface of each Skype for Business Server Edge Server or hardware load balanced (HLB) VIP in the perimeter network.
    
  - DNS A and AAAA (if you're using IPv6 addressing) and SRV records for the external interface of the Reverse proxy server or (VIP for a pool of Reverse proxy servers), in the perimeter network.
    
  - DNS A and AAAA (if you're using IPv6 addressing) and SRV records for Skype for Business Server client autoconfiguration ( **optional** ).
    
## Automatic configuration without split-brain DNS
<a name="NoSplitBrainDNS"> </a>

If you don't use split-brain DNS, internal automatic configuration of clients running Skype for Business won't work unless you're using one of the workarounds we have here. Why not? Because Skype for Business Server requires the user's SIP URI to match the domain of the Front End pool designated for automatic configuration. This hasn't changed from earlier versions of Lync Server.
  
So, if you have two SIP domains in use, you'd need these DNS SRV records:
  
- _sipinternaltls._tcp.contoso.com. 86400 IN SRV 0 0 5061 pool01.contoso.com
    
     *If a user signs in as bob@contoso.com, this record would work for automatic configuration, as the user's SIP domain matches the domain of the Front End pool (contoso.com).* 
    
- _sipinternaltls._tcp.fabrikam.com. 86400 IN SRV 0 0 5061 pool01.fabrikam.com
    
     *If a user signs in as alice@fabrikam.com, this record would work for automatic configuration of the second domain, again because the SIP domain matches the Front End pool for that domain.* 
    
To take the example further, this would not work:
  
- _sipinternaltls._tcp.litwareinc.com. 86400 IN SRV 0 0 5061 pool01.fabrikam.com
    
     *A user signing in as tim@litwareinc.com won't work for automatic configuration, because his SIP domain (litwareinc.com) doesn't match the domain in the pool (fabrikam.com).* 
    
So now that we know all that, if you need automatic requirement for your Skype for Business clients without split-brain DNS, you have these options:
  
- **Group Policy Objects**
    
    You can use Group Policy Objects (GPOs) to populate the correct server values.
    
    > [!NOTE]
    > This option doesn't enable automatic configuration, but it does automate manual configuration. If this approach is used, the SRV records associated with automatic configuration aren't required. 
  
- **Matching internal zone**
    
    You'll need to create a zone in your internal DNS that matches your external DNS zone (for example, contoso.com), and then create DNS A (and AAAA if you're using IPv6 addressing) records that correspond to the Skype for Business Server pool used for automatic configuration.
    
    For example, if you have a user homed on pool01.contoso.net, but signs into Skype for Business as bob@contoso.com, create an internal DNS zone called contoso.com, and inside it you need to create a DNS A (and AAAA if IPv6 addressing's being used) record for pool01.contoso.com.
    
- **Pin-point internal zone**
    
    If creating an entire zone in your internal DNS isn't an option for you, you can create pin-point (dedicated) zones that correspond to the SRV records required for automatic configuration, and populate those zones using dnscmd.exe. Dnscmd.exe is required because the DNS user interface won't support the creation of pin-point zones.
    
    For example, if your SIP domain is contoso.com, and you have a Front End pool called pool01 that contains two Front End Servers, you'll need the following pin-point zones and A records in your internal DNS:
    
  ```
  dnscmd . /zoneadd _sipinternaltls._tcp.contoso.com. /dsprimary
  dnscmd . /recordadd _sipinternaltls._tcp.contoso.com. @ SRV 0 0 5061 pool01.contoso.com.
  dnscmd . /zoneadd pool01.contoso.com. /dsprimary
  dnscmd . /recordadd pool01.contoso.com. @ A 192.168.10.90
  dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
  dnscmd . /recordadd pool01.contoso.com. @ A 192.168.10.91 
  dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
  ```

    You may have a second SIP domain in your environment. In that case, you'll need the following pin-point zones and A records in your internal DNS:
    
  ```
  dnscmd . /zoneadd _sipinternaltls._tcp.fabrikam.com. /dsprimary
  dnscmd . /recordadd _sipinternaltls._tcp.fabrikam.com. @ SRV 0 0 5061 pool01.fabrikam.com.
  dnscmd . /zoneadd pool01.fabrikam.com. /dsprimary
  dnscmd . /recordadd pool01.fabrikam.com. @ A 192.168.10.90
  dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
  dnscmd . /recordadd pool01.fabrikam.com. @ A 192.168.10.91
  dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
  ```

> [!NOTE]
> You'll see the Front End pool FQDN appears twice, but with two different IP addresses. That's because DNS load balancing is used. If HLB is used, there'd only be a single Front End pool entry. 
  
> [!NOTE]
> Also, the Front End pool FQDN values change between the contoso.com and fabrikam.com examples, but the IP addresses remain the same. That's because users who're signing in from either SIP domain will be using the same Front End pool for automatic configuration. 
  
## DNS disaster recovery
<a name="DNSDR"> </a>

To configure DNS to redirect Skype for Business Server web traffic to your disaster recover (DR) and failover sites, you need to use a DNS provider that supports GeoDNS. You can set up your DNS records to support disaster recover, so that features that use web services continue even if one entire Front End pool goes down. This DR feature supports the Autodiscover, Meet and Dial-in simple URLs.
  
You define and configure additional DNS host A (AAAA if using IPv6) records for internal and external resolution of web services at your GeoDNS provider. The following details assume paired pools, geographically dispersed, and that the GeoDNS supported by your provider **either** has round-robin DNS **or** is configured to use Pool1 as primary and fails over to Pool2 in the event of any communications loss or power failure.
  
All the DNS records in this table are examples.
  
|**GeoDNS record**|**Pool records**|**CNAME records**|**DNS settings (select one option)**|
|:-----|:-----|:-----|:-----|
|Meet-int.geolb.contoso.com  <br/> |Pool1InternalWebFQDN.contoso.com  <br/> Pool2InternalWebFQDN.contoso.com  <br/> |Meet.contoso.com to Meet-int.geolb.contoso.com  <br/>   <br/> |Round Robin between pools  <br/> **OR** <br/> Use primary, connect to secondary if there's a failure  <br/> |
|Meet-ext.geolb.contoso.com  <br/> |Pool1ExternalWebFQDN.contoso.com  <br/> Pool2ExternalWebFQDN.contoso.com  <br/> |Meet.contoso.com to Meet-ext.geolb.contoso.com  <br/>   <br/> |Round Robin between pools  <br/> **OR** <br/> Use primary, connect to secondary if there's a failure  <br/> |
|Dialin-int.geolb.contoso.com  <br/> |Pool1InternalWebFQDN.contoso.com  <br/> Pool2InternalWebFQDN.contoso.com  <br/> |Meet.contoso.com to Meet-int.geolb.contoso.com   <br/>  <br/> |Round Robin between pools  <br/> **OR** <br/> Use primary, connect to secondary if there's a failure  <br/> |
|Dialin-ext.geolb.contoso.com  <br/> |Pool1ExternalWebFQDN.contoso.com  <br/> Pool2ExternalWebFQDN.contoso.com  <br/> |Meet.contoso.com to Meet-ext.geolb.contoso.com  <br/>  <br/> |Round Robin between pools  <br/> **OR** <br/> Use primary, connect to secondary if there's a failure  <br/> |
|Lyncdiscoverint-int.geolb.contoso.com  <br/> |Pool1InternalWebFQDN.contoso.com  <br/> Pool2InternalWebFQDN.contoso.com  <br/> |Meet.contoso.com to Meet-int.geolb.contoso.com   <br/>   <br/> |Round Robin between pools  <br/> **OR** <br/> Use primary, connect to secondary if there's a failure  <br/> |
|Lyncdiscover-ext.geolb.contoso.com  <br/> |Pool1ExternalWebFQDN.contoso.com  <br/> Pool2ExternalWebFQDN.contoso.com  <br/> |Meet.contoso.com to Meet-ext.geolb.contoso.com  <br/>  <br/> |Round Robin between pools  <br/> **OR** <br/> Use primary, connect to secondary if there's a failure  <br/> |
|Scheduler-int.geolb.contoso.com  <br/> |Pool1InternalWebFQDN.contoso.com  <br/> Pool2InternalWebFQDN.contoso.com  <br/> |Meet.contoso.com to Meet-int.geolb.contoso.com   <br/>  <br/> |Round Robin between pools  <br/> **OR** <br/> Use primary, connect to secondary if there's a failure  <br/> |
|Scheduler-ext.geolb.contoso.com  <br/> |Pool1ExternalWebFQDN.contoso.com  <br/> Pool2ExternalWebFQDN.contoso.com  <br/> |Meet.contoso.com to Meet-ext.geolb.contoso.com   <br/>  <br/> |Round Robin between pools  <br/> **OR** <br/> Use primary, connect to secondary if there's a failure  <br/> |
   
## DNS load balancing
<a name="DNSLB"> </a>

DNS load balancing is usually implemented at the application level. The application (for example, a client running Skype for Business), tries to connect to a server in a pool by connecting to one of the IP addresses returned from the DNS A and AAAA (if IPv6 addressing is used) record query for the pool FQDN.
  
For example, if there are three Front End Servers in a pool named pool01.contoso.com, the following would happen:
  
- Clients running Skype for Business query DNS for pool01.contoso.com. The query returns three IP addresses and caches them as follows (in some order):
    
   |||
   |:-----|:-----|
   |pool01.contoso.com  <br/> |192.168.10.90  <br/> |
   |pool01.contoso.com  <br/> |192.168.10.91  <br/> |
   |pool01.contoso.com  <br/> |192.168.10.92  <br/> |
   
- The client tries to establish a TCP connection to one of the IP addresses. If that fails, it'll try the next IP address it's cached from that list.
    
- If the TCP connection succeeds, the client negotiates TLS to connect to the primary registrar on pool01.contoso.com.
    
- If the client tries all cached entries without a successful connection, the user receives a notification that no servers running Skype for Business Server are available at the moment.
    
> [!NOTE]
> DNS-based load balancing is different from DNS round robin (DNS RR), which typically refers to load balancing by relying on DNS to give a different order of IP addresses for the servers in your pool. Typically, DNS RR enables load distribution, but it won't allow you to enable failover. For example, if the connection to the one IP address returned by your DNS A (or AAAA in an IPv6 scenario) query fails, that connection will fail. That makes DNS RR less reliable than DNS-based load balancing. You can still use DNS RR in conjunction with DNS-based load balancing if you need to do that. 
  
You use DNS load balancing to:
  
- Load balance server-to-server SIP to the Edge Servers.
    
- Load balance Unified Communication Application Services (UCAS) applications, such as Conferencing Auto Attendant, Response Group, and Call Park.
    
- Prevent new connections to UCAS applications (also known as draining).
    
- Load balance all client-to-server traffic between clients and Edge Servers.
    
You can't use DNS load balancing for:
  
- Client-to-server web traffic to your Front End Servers or a Director.
    
To go a little more in-depth on how a DNS SRV record's selected when mutiple DNS records are returned by a query, the Access Edge service always picks the record with the lowest numeric priority and, if a tie-breaker is needed, the highest numeric weight. This is consistent with [Internet Engineering Task Force documentation](https://www.ietf.org/rfc/rfc2782.txt).
  
So, for example, if your first DNS SRV record has a weight of 20 and a priority of 40, and your second DNS SRV record has a weight of 10 and a priority of 50, the first record's going to be chosen because it has the lower priority of 40. Priority always goes first, and that's the host that a client will target first. What if there are two targets with the same priority? 
  
In that case, weight comes into consideration. Larger weights should be given a high probability, in this circumstance, of being selected. DNS administrators should use weight 0 when there isn't any server selection to do. In the presence of records containing weights greater than 0, records with weight 0 have a very small chance of bring selected.
  
So, then, what happens if multiple DNS SRV records with equal priority and weight as returned? In this situation the Access Edge service will choose the SRV record that it got from the DNS server first.
  

