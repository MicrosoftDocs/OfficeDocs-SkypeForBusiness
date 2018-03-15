---
title: "DNS requirements for Skype for Business Server 2015"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/15/2018
ms.audience: ITPro
ms.topic: concetpual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.custom: Strat_SB_Admin
ms.assetid: c50e38d2-b1e4-4ebd-8dc3-85d4ae7a76ee
description: "Summary: Review the DNS considerations in this topic before implementing Skype for Business Server 2015."
---

# DNS requirements for Skype for Business Server 2015
 
**Summary:** Review the DNS considerations in this topic before implementing Skype for Business Server 2015.
  
This article only addresses DNS planning for Skype for Business Server 2015 deployments on an organization's on-premise network. For Skype for Business Online refer to "Office 365 URLs and IP address ranges" at [http://aka.ms/o365ips](http://aka.ms/o365ips). 
  
A Domain name service (DNS) server maps hostnames (like www.contoso.com, presumably a web server) to IP addresses (such as 10.10.10.10). It helps clients and interdependent servers communicate with each other on the network. When you set up an implementation of Skype for Business Server 2015 you'll need to make sure the mapping of new server names (usually reflecting the role they'll be taking on) matches the IP addresses they are assigned to.
  
While this may seem a bit daunting at first, the heavy lifting for planning this can be done using the [Skype for Business Server 2015 Planning Tool](https://www.microsoft.com/en-us/download/details.aspx?id=50357). Once you've gone through the wizard's questions about what features you plan to use, for each site you define you can view the DNS Report within the Edge Admin Report, and use the information listed there to create your DNS records. You can also make adjustments to many of the names and IP addresses used, for details see [Review the DNS Report](../../management-tools/planning-tool/review-the-administrator-reports.md#DNS_Report). Keep in mind you can export the Edge Admin Report to an Excel spreadsheet, and the DNS Report will be one of the worksheets in the file. 
  
When you are installing a new implementation as described in [Create DNS records for Skype for Business Server 2015](../../deploy-1/install-0/create-dns-records.md) and building your topology for Skype for Business Server 2015, we recognize that you can choose to use the DNS capabilities built in to Windows Server 2016 or a third-party DNS package, so we'll keep the discussions in this article general rather than specific. We're detailing what's needed, and how you meet that need is your decision to make.
  
Experienced Skype for Business, Lync, and Office Communications Suite administrators will probably find the following tables useful. If the table is confusing to you, the later sections or articles will shed some light on the following concepts: 
  
- [Summary tables](dns.md#BK_Summary)
    
- [DNS basics](basics.md)
    
- [Hybrid considerations](dns.md#BK_Hybrid)
    
- [Split brain DNS](dns.md#BK_split)
    
- [Simple URLs ](dns.md#BK_Simple)
    
- [DNS by server role](dns.md#BK_Servers)
    
## Summary tables
<a name="BK_Summary"> </a>

The following tables show DNS records Skype for Business Server 2015 uses to provide services to users. Some are optional in that they are only needed to support certain features, and they can be skipped if those features are not desired. The DNS records needed for internal access only are in the first table, and a deployment allowing internal and external access will need records from both tables.
  
**Internal DNS mappings**

|**Record Type**|**Value**|**Resolves to**|**Purpose**|**Required**|
|:-----|:-----|:-----|:-----|:-----|
|A/AAAA  <br/> |Front End pool FQDN  <br/>  *FE-pool.contoso.com*  <br/> |Front End pool server IP addresses  <br/>  DNS LB to *192.168.21.122 192.168.21.123 192.168.21.124*  <br/> |DNS Load Balancing of Front End Pools. Maps the Front End pool name to a set of IP addresses.  <br/> See [Deploying DNS Load Balancing on Front End Pools and Director Pools](load-balancing.md#BK_FE_Dir) <br/> |Y  <br/> |
|A/AAAA  <br/> | FQDN of each Front End Server or Standard Edition server in a pool, or a standalone server <br/>  * FE01.contoso.com, FE02.contoso.com, FE03.contoso.com*  <br/> |Corresponding IP of each server  <br/>  *192.168.21.122 192.168.21.123 192.168.21.124*  <br/> |Maps the server name to its IP address.  <br/> |Y  <br/> |
|A/AAAA  <br/> |Enterprise Pool Internal Web Services Override FQDN  <br/>  *Web-int.contoso.com*  <br/> |HLB VIP for Front End Server Internal Web Services  <br/>  *192.168.21.120 *  <br/> |Required to enable client to server web traffic, such as downloading the Skype for Business Web App. Also required for Mobile clients.  <br/> |Y  <br/> |
|A/AAAA  <br/> |Enterprise Pool External Web Services Override FQDN  <br/>  *Web-ext.contoso.com*  <br/> |HLB VIP for Front End Server External Web Services  <br/>  *68.123.56.90*  <br/> |Required to enable client to server web traffic, such as downloading the Skype for Business Web App. Required if mobile clients will resolve DNS internally. Can resolve to DMZ Reverse Proxy IP or Internet IP.  <br/> ||
|A/AAAA  <br/> | Back End Server SQL server FQDN <br/>  *SQL1.contoso.com*  <br/> |server IP address  <br/>  *192.168.11.90*  <br/> |Maps the server name for a back-end SQL server working with the Front End pool to its IP address  <br/> ||
|A/AAAA  <br/> |Back End Server Mirror SQL server FQDN  <br/>  *SQL2.contoso.com*  <br/> |server IP address  <br/>  *192.168.11.91*  <br/> |Maps the server name for a back-end SQL mirror server working with the Front End pool to its IP address  <br/> ||
|A/AAAA  <br/> |Director pool FQDN  <br/> **Note:** Not applicable when using a standalone Director server <br/>  *DirPool.contoso.com*  <br/> |Director pool IP addresses  <br/> DNS LB to  *192.168.21.132, 192.168.21.133, 192.168.21.134*  <br/> |DNS load balancing of Director Pool servers. Maps the pool name for the Director pool to an IP address, see [Deploying DNS Load Balancing on Front End Pools and Director Pools](load-balancing.md#BK_FE_Dir) <br/> A Director can authenticate a user and is optional.  <br/> ||
|A/AAAA  <br/> |Director FQDN  <br/> |Server IP address of each Director server  <br/> |Maps the pool name for the Director to an IP address, see [Deploying DNS Load Balancing on Front End Pools and Director Pools](load-balancing.md#BK_FE_Dir) <br/> ||
|A/AAAA  <br/> |Mediation Server pool FQDN  <br/> |Pool IP addresses  <br/> |The Mediation Server role is optional. You can co-locate the services provided by a mediation server to the Front End server or pool. See [Using DNS Load Balancing on Mediation Server Pools](load-balancing.md#BK_Mediation) <br/> ||
|A/AAAA  <br/> |Mediation Server FQDN  <br/> |Server IP address  <br/> |You can co-locate the services provided by a mediation server to the Front End server or pool. See [Using DNS Load Balancing on Mediation Server Pools](load-balancing.md#BK_Mediation) <br/> ||
|A/AAAA  <br/> |Persistent Chat Server FQDN  <br/> |Persistent Chat Server IP address  <br/> |A Persistent Chat server is required for the Persistent Chat feature and is otherwise optional.  <br/> ||
|A/AAAA  <br/> |lyncdiscoverinternal. _\<sipdomain\>_ <br/> lyncdiscoverinternal.*contoso.com*  <br/> |HLB Front End pool VIP or Director IP  <br/>  192.168.21.121 <br/> |Internal AutoDiscover Service1, required for Mobility support. If internal DNS is used to resolve for mobile devices, it should point to the external IP, or DMZ VIP.  <br/> For Web services we require HLB on the Front End pool as HTTPS can't leverage DNS. For Front End pool or Director pool this should resolves to an HLB VIP, or a regular IP for a Standard edition server or a Standalone Director server.  <br/> |Y  <br/> |
|CNAME  <br/> |lyncdiscoverinternal. _\<sipdomain\>_ <br/> lyncdiscoverinternal. *contoso.com*  <br/> |HLB FE Pool FQDN or Director FQDN  <br/> Web-int.contoso.com  <br/> |Internal AutoDiscover Service1 <br/> You can implement this as a CNAME instead of an A record if desired.  <br/> ||
|A/AAAA  <br/> |sip. _\<sipdomain\>_ <br/> sip. _contoso.com_ <br/> |Front End pool server IP addresses (or to a each Director IP address)  <br/>  DNS LB to *192.168.21.122 192.168.21.123 192.168.21.124*  <br/> |Required for automatic configuration, see [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#WalkthroughOfSkype) <br/> A record or records pointing to the Front End pool servers or Director servers on the internal network, or the Access Edge service when the client is external  <br/> |2 <br/> |
|A/AAAA  <br/> |ucupdates-r2. _\<sipdomain\>_ <br/> ucupdates-r2. _contoso.com_ <br/> |HLB FE Pool VIP Or Director Pool HLB VIP , or SE/Director Server IP  <br/>  192.168.21.121 <br/> |Deploying this record is optional 3 <br/> ||
|SRV  <br/> |_sipinternaltls._tcp. _\<sipdomain\>_ Port 5061 <br/> _sipinternaltls._tcp. _contoso.com_ Port 5061 <br/> |Front End pool FQDN  <br/>  _FE-Pool.contoso.com_ <br/> |Enables Internal user automatic sign-in 1 to the Front End server/pool or SE server/pool that authenticates and redirects client requests for sign-in. <br/> |2 <br/> |
|SRV  <br/> |_sipinternal. _\<sipdomain\>_ <br/> _sipinternal. _contoso.com_ <br/> |Front End pool FQDN  <br/>  _FE-Pool.contoso.com_ <br/> |Internal user access 1 <br/> |2 <br/> |
|SRV  <br/> |_ntp._udp. _\<sipdomain\>_ <br/> _ntp._udp. _contoso.com_ <br/> |TimeServer FQDN  <br/> north-america.pool.ntp.org  <br/> |NTP source required for Lync Phone Edition devices  <br/> |This is required to support desktop handsets.  <br/> |
|SRV  <br/> |_sipfederationtls._tcp.  _\<sipdomain\>_ <br/> _sipfederationtls._tcp.  _contoso.com_ <br/> | Access Edge service FQDN <br/> EdgePool-int. _contoso.com_ <br/> |Create one SRV record for each SIP domain that has IOS or Windows phone Mobile clients.  <br/> |For Mobile client support  <br/> |
|A/AAAA  <br/> |admin URL  <br/>  _Web-int.contoso.com_ <br/> |HLB FE Pool VIP  <br/> 192.168.21.121  <br/> |Skype for Business Server Control Panel, see [Simple URLs ](dns.md#BK_Simple) <br/> ||
|A/AAAA  <br/> |meet URL  <br/>  _Web-int.contoso.com_ <br/> |HLB FE Pool VIP  <br/> 192.168.21.121  <br/> |Online meetings, see [Simple URLs ](dns.md#BK_Simple) <br/> ||
|A/AAAA  <br/> |dial-in URL  <br/>  _Web-int.contoso.com_ <br/> |HLB FE Pool VIP  <br/> 192.168.21.121  <br/> |Dial-in conferencing, see [Simple URLs ](dns.md#BK_Simple) <br/> ||
|A/AAAA  <br/> |internal Web Services FQDN  <br/>  _Web-int.contoso.com_ <br/> |HLB FE Pool VIP  <br/> 192.168.21.121  <br/> |Skype for Business Web Service used by Skype for Business Web App  <br/> ||
|A/AAAA  <br/> |Office Web Apps Server pool FQDN  <br/> OWA.contoso.com  <br/> | Office Web Apps Server pool VIP address <br/> 192.168.1.5  <br/> |Defines the Office Web Apps Server pool FQDN  <br/> ||
|A/AAAA  <br/> | Internal Web FQDN <br/> Web-int.contoso.com  <br/> | Front End pool VIP address <br/> 192.168.21.121  <br/> |Defines the Internal Web FQDN used by Skype for Business Web App  <br/> If you are using DNS load balancing on this pool, your Front End pool and internal web farm cannot have the same FQDN.  <br/> ||
   
 **1** Used by a client to discover the Front End Server or Front End pool, and be authenticated and signed in as a user. More detail on this is in [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#WalkthroughOfSkype).
  
 **2** This is only required to support legacy clients prior to Lync 2013, and desktop handsets.
  
 **3** In the situation where a Unified Communications device is turned on, but a user has never logged into the device, the A record allows the device to discover the server hosting Device Update Web service and obtain updates. Otherwise, devices obtain the server information though in-band provisioning the first time a user logs in.
  
The following diagram shows an example that includes both internal and external DNS records, and many of the records shown in the surrounding tables: 
  
**Edge network diagram using Public IPv4 addresses**

![example of DNS network diagram](../../media/2cc9546e-5560-4d95-8fe4-65a792a0e9c3.png)
  
**Perimeter network DNS mappings (both internal and external interfaces)**

|**Record Type**|**Value**|**Resolves to**|**Purpose**|**Required**|
|:-----|:-----|:-----|:-----|:-----|
|A/AAAA  <br/> |Internal Edge pool FQDN  <br/>  _EdgePool-int.contoso.com_ <br/> |Internal-facing Edge pool IP addresses  <br/> 172.25.33.10, 172.25.33.11  <br/> |Consolidated Edge Pool internal interface IP Addresses  <br/> |Y  <br/> |
|A/AAAA  <br/> |Edge Server FQDN  <br/>  _Cons-1.contoso.com_ <br/> |Internal-facing server IP for a server in the Edge pool  <br/> 172.25.33.10  <br/> |Create a record for each server in the pool with the server FQDN pointing to its internal server node IP in the pool, see [DNS Load Balancing on Edge Server Pools](load-balancing.md#BK_Edge).  <br/> |Y  <br/> |
|A/AAAA  <br/> |Access Edge service Pool FQDN  <br/>  _Access1.contoso.com_ <br/> |Access Edge service Pool external IP addresses  <br/> 131.107.16.10, 131.107.16.11  <br/> |The Access Edge service provides a single, trusted connection point for both outbound and inbound Session Initiation Protocol (SIP) traffic.  <br/> |Y  <br/> |
|A/AAAA  <br/> |Web Conferencing Edge service Pool FQDN  <br/>  _Webcon1.contoso.com_ <br/> |Web Conferencing Edge service external IP addresses  <br/> 131.107.16.90, 131.107.16.91  <br/> |The Web Conferencing Edge service enables external users to join meetings that are hosted on your internal Skype for Business Server environment.  <br/> |Y  <br/> |
|A/AAAA  <br/> | _av.\<sip-domain\>_ Pool FQDN <br/>  _AV1.contoso.com_ <br/> |A/V Edge external IP addresses  <br/> 131.107.16.170, 131.107.16.171  <br/> |The A/V Edge service makes audio, video, application sharing and file transfer available to external users.  <br/> |Y  <br/> |
|CNAME  <br/> |sip. _\<sipdomain\>_ <br/> sip. _contoso.com_ <br/> |External Access Edge Pool FQDN  <br/>  _Access1.contoso.com_ <br/> |Locates the Edge Server pool . See [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#WalkthroughOfSkype) <br/> |Y  <br/> |
|SRV  <br/> |_sip._tls. _\<sipdomain\>_ <br/> _sip._tls. _contoso.com_ <br/> |External Access Edge FQDN  <br/>  _Access1.contoso.com_ <br/> |Used for external user access. See [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#WalkthroughOfSkype) <br/> |Y  <br/> |
|SRV  <br/> |_sipfederationtls._tcp. _\<sipdomain\>_ <br/> _sipfederationtls._tcp. _contoso.com_ <br/> |External Access Edge FQDN  <br/>  _Access1.contoso.com_ <br/> |Used for Federation and public IM connectivity  <br/> |1 <br/> |
|SRV  <br/> |_xmpp-server._tcp. _\<sipdomain\>_ <br/> _xmpp-server._tcp. _contoso.com_ <br/> |External Access Edge FQDN  <br/>  _Access1.contoso.com_ <br/> |The XMPP Proxy service accepts and sends extensible messaging and presence protocol (XMPP) messages to and from configured XMPP Federated partners.  <br/> |Y, to deploy Federation, otherwise optional  <br/> |
|SRV  <br/> |_sipfederationtls._tcp.  _\<sipdomain\>_ <br/> _sipfederationtls._tcp.  _contoso.com_ <br/> |External Access Edge FQDN  <br/>  _Access1.contoso.com_ <br/> |To support Push Notification Service and Apple Push Notification service, you create one SRV record for each SIP domain. 3 <br/> ||
|A/AAAA  <br/> |External Front End pool web services FQDN  <br/>  _Web-ext.contoso.com_ <br/> |Reverse proxy public IP address, proxies to the External Web Services VIP for your Front End pool 1 <br/> 131.107.155.1 proxy to 192.168.21.120  <br/> |Front End pool external interface used by Skype for Business Web App  <br/> |Y  <br/> |
|A/AAAA/CNAME  <br/> |lyncdiscover. _\<sipdomain\>_ <br/> lyncdiscover. _contoso.com_ <br/> |Reverse proxy public IP address, resolves to the External Web Services VIP for your Director pool, if you have one, or for your Front End pool if you do not have a Director 2 <br/> 131.107.155.1 proxy to 192.168.21.120  <br/> | External record for client AutoDiscover, also used by Mobility, Skype for Business Web App, and scheduler Web app, resolved by the reverse proxy server <br/> To support Push Notification Service and Apple Push Notification service, you create one SRV record for each SIP domain that has Microsoft Lync Mobile clients. 3 <br/> |Y  <br/> |
|A/AAAA  <br/> |meet. _\<sipdomain\>_ <br/> meet. _contoso.com_ <br/> |Reverse proxy public IP address, resolves to the external Web interface for the Front End pool  <br/> 131.107.155.1 proxy to 192.168.21.120  <br/> |Proxy to Skype for Business Web Service  <br/> See [Simple URLs ](dns.md#BK_Simple) <br/> |Y  <br/> |
|A/AAAA  <br/> |dial-in _\<sipdomain\>_ <br/> dial-in _contoso.com_ <br/> |Reverse proxy public IP address, proxies to the external Web interface for the Front End pool  <br/> 131.107.155.1 proxy to 192.168.21.120  <br/> |Proxy to Skype for Business Web Service  <br/> See [Simple URLs ](dns.md#BK_Simple) <br/> |Y  <br/> |
|A/AAAA  <br/> |Office Web Apps Server pool FQDN  <br/> OWA.contoso.com  <br/> | Reverse proxy public IP address, proxies to the external Web interface for the Office Web Apps Server <br/> 131.107.155.1 proxy to 192.168.1.5  <br/> | Office Web Apps Server pool VIP address <br/> 192.168.1.5  <br/> |Defines the Office Web Apps Server pool FQDN  <br/> |
   
 **1** Required to deploy Federation, otherwise optional.
  
 **2** Used by a client to discover the front end server or Front End pool, and be authenticated and signed in as a user.
  
 **3** This requirement applies only to clients on Apple or Microsoft based mobile devices. Android and Nokia Symbian devices do not use push notification.
  
 For more detail on Edge Servers and perimeter networks, see the Edge server [DNS planning](../../plan-your-deployment/edge-server-deployments/edge-environmental-requirements.md#DNSPlan) content.
  
> [!IMPORTANT]
> Skype for Business Server supports the use of IPv6 addressing. See [Plan for IPv6 in Skype for Business](ipv6.md) for more details.
  
> [!IMPORTANT]
> For more detail on FQDNs, see [DNS basics](basics.md). 
  
 **Split brain DNS** is a DNS configuration where you have two DNS zones with the same namespace. The first DNS zone handles internal requests, while the second DNS zone handles external requests, as mentioned in these tables. For more about this see [Split-brain DNS](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#SplitBrainDNS). 
  
## Hybrid considerations
<a name="BK_Hybrid"> </a>

If you plan to have some users homed online and some homed on premises, refer to the hybrid [DNS settings](../../skype-for-business-hybrid-solutions/plan-hybrid-connectivity.md#BKMK_DNS). You will need to configure DNS as normal for Skype for Business Server 2015 and also add additional DNS records. 
  
You should also refer to "Office 365 URLs and IP address ranges" at [http://aka.ms/o365ips](http://aka.ms/o365ips) to confirm that your users will have access to the online resources they will need.
  
## Simple URLs
<a name="BK_Simple"> </a>

A Uniform Resource Locator (URL) is a reference to a web resource that specifies its location on a computer network and a protocol used to retrieve it. 
  
Skype for Business Server supports using three "simple" URLs to access services:
  
- **Meet** is used as the base URL for all conferences in the site. An example of a Meet simple URL is https://meet.contoso.com. A URL for a particular meeting might be https://meet.contoso.com/ _username_/7322994. 
    
    With the Meet simple URL, links to join meetings are easy to comprehend and easy to communicate.
    
- **Dial-in** enables access to the Dial-in Conferencing Settings web page. This page displays conference dial-in numbers with their available languages, assigned conference information (that is, for meetings that do not need to be scheduled), and in-conference DTMF controls, and supports management of personal identification number (PIN) and assigned conferencing information. The Dial-in simple URL is included in all meeting invitations so that users who want to dial in to the meeting can access the necessary phone number and PIN information. An example of the Dial-in simple URL is https://dialin.contoso.com.
    
- **Admin** enables quick access to the Skype for Business Server Control Panel. From any computer within your organization's firewalls, an admin can open the Skype for Business Server Control Panel by typing the Admin simple URL into a browser. The Admin simple URL is internal to your organization. An example of the Admin simple URL is https://admin.contoso.com.
    
Simple URLs are discussed in more detail at [DNS requirements for simple URLs in Skype for Business Server 2015](simple-urls.md).
  
## DNS by server role
<a name="BK_Servers"> </a>

You can set the names of these pools and servers as you wish, but make them memorable and reflect their function in the system.
  
### DNS records for individual servers or pools

These generic record requirements apply to any server role used by Skype for Business. A pool is a set of servers running the same services that work together to handle client requests directed to them through a load balancer. See [Load balancing requirements for Skype for Business](load-balancing.md) for details
  
**DNS record Requirements for Server/pool roles (presumes DNS load balancing)**

|**Deployment scenario**|**DNS requirement**|
|:-----|:-----|
|One Server:  <br/> Persistent Chat, Director, Mediation Server, Front end server  <br/> |An internal A record that resolves the fully qualified domain name (FQDN) of the server to its IP address.  <br/> ServerRole.contoso.com 10.10.10.0  <br/> |
|Pool:  <br/> Persistent Chat, Director, Edge Server, Mediation Server, Front end  <br/> |An internal A record that resolves the fully qualified domain name (FQDN) of each server node in the pool to its IP address.  <br/> **Example** <br/> ServerRole01.contoso.com 10.10.10.1  <br/> ServerRole02.contoso.com 10.10.10.2  <br/> Multiple internal A records that resolve the fully qualified domain name (FQDN) of the pool to the IP addresses of the server nodes in the pool.  <br/> **Example** <br/> ServerPool.contoso.com 10.10.10.1  <br/> ServerPool.contoso.com 10.10.10.2  <br/> |
   
### Edge Server specific DNS topics

 To plan edge server deployment, review [Plan for Edge Server deployments in Skype for Business Server 2015](../../plan-your-deployment/edge-server-deployments/edge-server-deployments.md), and [Advanced Edge Server DNS planning for Skype for Business Server 2015](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md) which has the following sections
  
- [DNS disaster recovery](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#DNSDR)
    
- [DNS load balancing](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#DNSLB)
    
- [Automatic configuration without split-brain DNS](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#NoSplitBrainDNS)
    
- [Split-brain DNS](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#SplitBrainDNS)
    
- [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#WalkthroughOfSkype)
    

