---
title: "DNS requirements for Front End pools in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ba28919c-fbbe-4c54-8bf9-2b0cd3fa39c7

description: "This section describes the Domain Name System (DNS) records that are required for deployment of Front End pools."
---

# DNS requirements for Front End pools in Lync Server 2013
[]
This section describes the Domain Name System (DNS) records that are required for deployment of Front End pools.
  
## DNS Records for Front End Pools

The following table specifies DNS requirements for a Lync Server 2013 Front End pool deployment.
  
**DNS Requirements for a Front End Pool**

|**Deployment scenario**|**DNS requirement**|
|:-----|:-----|
|Front End pool with multiple Front End Servers and a hardware load balancer (whether or not DNS load balancing is also deployed on that pool)  <br/> | When using both DNS load balancing and a hardware load balancer, you need to Host (A) records. Create an internal A record that resolves the fully qualified domain name (FQDN) of the Front End pool for DNS load balancing. Create an internal host (A) record for the internal Web services to the virtual IP (VIP) address of the load balancer. You must use the internal Web services name as defined in Topology Builder.  <br/>  For example, if you use both DNS load balancing and hardware load balancing, you would have an A record for each Front End Server in a pool for DNS load balancing, and an A record for the internal Web services pointing to the virtual IP of the hardware load balancer:  <br/>  DNS load balancing: Pool01.contoso.net IP Address of pool 10.10.10.5  <br/> > [!CAUTION]>  Each Front End Server will also have a distinct A record:            FE01.contoso.net 10.10.10.1  <br/>  FE02.contoso.net 10.10.10.2  <br/>  FE03.contoso.net 10.10.10.3  <br/>  FE04.contoso.net 10.10.10.4  <br/>  Hardware load balancing: WebInternal.contoso.net IP Address of HLB VIP 192.168.10.5  <br/>  All traffic except for HTTP/HTTPS traffic will use the Pool01.contoso.net record. HTTP/HTTPS traffic will use the defined internal Web services address of 192.168.10.5  <br/> |
|Front End pool with DNS load balancing deployed  <br/> |A set of internal A records that resolve the FQDN of the pool to the IP address of each server in the pool. There must one A record for each server in the pool.  <br/> |
|Front End pool with DNS load balancing deployed  <br/> |A set of internal A records that resolve the FQDN of each server in the pool to the IP address of that server. For details, see [DNS load balancing in Lync Server 2013](dns-load-balancing.md) in the Planning documentation.  <br/> |
|Front End pool with a single Front End Server and a dedicated back-end database but no load balancer  <br/> |An internal A record that resolves the FQDN of the Front End pool to the IP address of the single Enterprise Edition Front End Server.  <br/> |
|Automatic client sign-in  <br/> |For each supported SIP domain, an SRV record for _sipinternaltls._tcp.<domain> over port 5061 that maps to the FQDN of the Front End pool that authenticates and redirects client requests for sign-in. For details, see [DNS requirements for automatic client sign-in in Lync Server 2013](dns-requirements-for-automatic-client-sign-in.md).  <br/> |
|Device Update Web service discovery by unified communications (UC) devices  <br/> |An internal A record with the name ucupdates-r2.\<SIP domain\> that resolves to the IP address of the Front End pool that hosts the Device Update Web service. In the situation where a UC device is turned on, but a user has never logged into the device, the A record allows the device to discover the Front End pool hosting Device Update Web service and obtain updates. Otherwise, devices obtain this information though in-band provisioning the first time a user logs in.  <br/> > [!IMPORTANT]> If you have an existing deployment of Device Update Web service in Lync Server 2010, you have already created an internal A record with the name ucupdates. _\<SIP domain\>_. For Microsoft Office Communications Server 2007 R2, you must create an additional DNS A record with the name ucupdates-r2. _\<SIP domain\>_.           |
|A reverse proxy to support HTTP traffic  <br/> |An external A record that resolves the external web farm FQDN to the external IP address of the reverse proxy. Clients and UC devices use this record to connect to the reverse proxy. For details, see [Determine DNS requirements for Lync Server 2013](determine-dns-requirements.md) in the Planning documentation.  <br/> |
   
The following table shows an example of the DNS records required for the internal web farm FQDN.
  
**Example DNS Records for Internal Web Farm FQDN**

|**Internal web farm FQDN**|**Pool FQDN**|**DNS A record(s)**|
|:-----|:-----|:-----|
|webcon.contoso.com  <br/> |ee-pool.contoso.com  <br/> |DNS A record for the ee-pool.contoso.com that resolves to the VIP address of the load balancer used by the Front End Servers.  <br/> DNS A record for webcon.contoso.com that resolves to the VIP address of the load balancer used by the Front End Servers.  <br/> |
|ee-pool.contoso.com  <br/> |ee-pool.contoso.com  <br/> |DNS A record for ee-pool.contoso.com that resolves to the virtual IP (VIP) address of the load balancer used by the Enterprise Edition Front End Servers in the Front End pool.  <br/> Note that if you are using DNS load balancing on this pool, your Front End pool and internal web farm cannot have the same FQDN.  <br/> |
   

