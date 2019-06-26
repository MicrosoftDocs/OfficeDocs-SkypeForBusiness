---
title: "DNS requirements for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: c50e38d2-b1e4-4ebd-8dc3-85d4ae7a76ee
description: "Summary: Review the DNS considerations in this topic before implementing Skype for Business Server."
---

# DNS requirements for Skype for Business Server

**Summary:** Review the DNS considerations in this topic before implementing Skype for Business Server.

This article only addresses DNS planning for Skype for Business Server deployments on an organization's on-premise network. For Skype for Business Online refer to "Office 365 URLs and IP address ranges" at [https://aka.ms/o365ips](https://aka.ms/o365ips).

A Domain name service (DNS) server maps hostnames (like www.<span></span>contoso<span></span>.com, presumably a web server) to IP addresses (such as 10.10.10.10). It helps clients and interdependent servers communicate with each other on the network. When you set up an implementation of Skype for Business Server 2015 you'll need to make sure the mapping of new server names (usually reflecting the role they'll be taking on) matches the IP addresses they are assigned to.

While this may seem a bit daunting at first, the heavy lifting for planning this can be done using the [Skype for Business Server 2015 Planning Tool](https://www.microsoft.com/en-us/download/details.aspx?id=50357). Once you've gone through the wizard's questions about what features you plan to use, for each site you define you can view the DNS Report within the Edge Admin Report, and use the information listed there to create your DNS records. You can also make adjustments to many of the names and IP addresses used, for details see [Review the DNS Report](../../management-tools/planning-tool/review-the-administrator-reports.md#DNS_Report). Keep in mind you can export the Edge Admin Report to an Excel spreadsheet, and the DNS Report will be one of the worksheets in the file. While this tool includes features [deprecated from Skype for Business Server 2019](../../../SfBServer2019/deprecated.md), it can still be used to create an initial plan if those features are not selected

When you are installing a new implementation as described in [Create DNS records for Skype for Business Server](../../deploy/install/create-dns-records.md) and building your topology for Skype for Business Server, we recognize that you can choose to use the DNS capabilities built in to Windows Server 2016 or a third-party DNS package, so we'll keep the discussions in this article general rather than specific. We're detailing what's needed, and how you meet that need is your decision to make.

Experienced Skype for Business, Lync, and Office Communications Suite administrators will probably find the following tables useful. If the table is confusing to you, the later sections or articles will shed some light on the following concepts:

## Summary tables
<a name="BK_Summary"> </a>

The following tables show DNS records Skype for Business Server uses to provide services to users. Some are optional in that they are only needed to support certain features, and they can be skipped if those features are not desired. The DNS records needed for internal access only are in the first table, and a deployment allowing internal and external access will need records from both tables.

**Internal DNS mappings**

|Record Type|Value|Resolves to|Purpose|Required|
|:-----|:-----|:-----|:-----|:-----|
|A/AAAA   |Front End pool FQDN  <br/> *FE-pool.<span></span>contoso<span></span>.com*   |Front End pool server IP addresses  <br/>  DNS LB to *192.168.21.122 192.168.21.123 192.168.21.124*   |DNS Load Balancing of Front End Pools. Maps the Front End pool name to a set of IP addresses.  <br/> See [Deploying DNS Load Balancing on Front End Pools and Director Pools](load-balancing.md#BK_FE_Dir)  |Y   |
|A/AAAA   | FQDN of each Front End Server or Standard Edition server in a pool, or a standalone server <br/>  *FE01.<span></span>contoso.<span></span>com FE02.<span></span>contoso<span></span>.com FE03.<span></span>contoso<span></span>.com*   |Corresponding IP of each server  <br/> *192.168.21.122 192.168.21.123 192.168.21.124*   |Maps the server name to its IP address.   |Y   |
|A/AAAA   |Enterprise Pool Internal Web Services Override FQDN  <br/> *Web-int.<span></span>contoso<span></span>.com*   |HLB VIP for Front End Server Internal Web Services  <br/> *192.168.21.120*   |Required to enable client to server web traffic, such as downloading the Skype for Business Web App. Also required for Mobile clients.   |Y   |
|A/AAAA   |Enterprise Pool External Web Services Override FQDN  <br/> *Web-ext.<span></span>contoso<span></span>.com*   |HLB VIP for Front End Server External Web Services  <br/>*68.123.56.90*   |Required to enable client to server web traffic, such as downloading the Skype for Business Web App. Required if mobile clients will resolve DNS internally. Can resolve to DMZ Reverse Proxy IP or Internet IP.   ||
|A/AAAA   | Back End Server SQL server FQDN <br/> *SQL1.<span></span>contoso<span></span>.com*   |server IP address  <br/> *192.168.11.90*   |Maps the server name for a back-end SQL server working with the Front End pool to its IP address   ||
|A/AAAA   |Back End Server Mirror SQL server FQDN  <br/> *SQL2.<span></span>contoso<span></span>.com*   |server IP address  <br/> *192.168.11.91*   |Maps the server name for a back-end SQL mirror server working with the Front End pool to its IP address   ||
|A/AAAA   |Director pool FQDN  <br/>**Note:** Not applicable when using a standalone Director server <br/> *DirPool.<span></span>contoso<span></span>.com*   |Director pool IP addresses  <br/> DNS LB to *192.168.21.132, 192.168.21.133, 192.168.21.134*   |DNS load balancing of Director Pool servers. Maps the pool name for the Director pool to an IP address, see [Deploying DNS Load Balancing on Front End Pools and Director Pools](load-balancing.md#BK_FE_Dir) <br/> A Director can authenticate a user and is optional.   ||
|A/AAAA   |Director FQDN   |Server IP address of each Director server   |Maps the pool name for the Director to an IP address, see [Deploying DNS Load Balancing on Front End Pools and Director Pools](load-balancing.md#BK_FE_Dir)  ||
|A/AAAA   |Mediation Server pool FQDN   |Pool IP addresses   |The Mediation Server role is optional. You can co-locate the services provided by a mediation server to the Front End server or pool. See [Using DNS Load Balancing on Mediation Server Pools](load-balancing.md#BK_Mediation)  ||
|A/AAAA   |Mediation Server FQDN   |Server IP address   |You can co-locate the services provided by a mediation server to the Front End server or pool. See [Using DNS Load Balancing on Mediation Server Pools](load-balancing.md#BK_Mediation)  ||
|A/AAAA   |Persistent Chat Server FQDN   |Persistent Chat Server IP address   |A Persistent Chat server is required for the Persistent Chat feature and is otherwise optional.   ||
|A/AAAA   |lyncdiscoverinternal.*\<sipdomain\>* <br/> lyncdiscoverinternal.*<span></span>contoso<span></span>.com*   |HLB Front End pool VIP or Director IP  <br/>  192.168.21.121  |Internal AutoDiscover Service1, required for Mobility support. If internal DNS is used to resolve for mobile devices, it should point to the external IP, or DMZ VIP.  <br/> For Web services we require HLB on the Front End pool as HTTPS can't leverage DNS. For Front End pool or Director pool this should resolves to an HLB VIP, or a regular IP for a Standard edition server or a Standalone Director server.   |Y   |
|CNAME   |lyncdiscoverinternal.*\<sipdomain\>* <br/> lyncdiscoverinternal. *<span></span>contoso<span></span>.com*   |HLB FE Pool FQDN or Director FQDN  <br/> Web-int.<span></span>contoso<span></span>.com   |Internal AutoDiscover Service1 <br/> You can implement this as a CNAME instead of an A record if desired.   ||
|A/AAAA   |sip.*\<sipdomain\>* <br/> sip.*<span></span>contoso<span></span>.com*  |Front End pool server IP addresses (or to a each Director IP address)  <br/>  DNS LB to *192.168.21.122 192.168.21.123 192.168.21.124*   |Required for automatic configuration, see [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#WalkthroughOfSkype) <br/> A record or records pointing to the Front End pool servers or Director servers on the internal network, or the Access Edge service when the client is external   |&#x2777;  |
|A/AAAA   |ucupdates-r2.*\<sipdomain\>* <br/> ucupdates-r2.*<span></span>contoso<span></span>.com*  |HLB FE Pool VIP Or Director Pool HLB VIP , or SE/Director Server IP  <br/>  192.168.21.121  |Deploying this record is optional &#x2778;  ||
|SRV   |\_sipinternaltls.\_tcp.*\<sipdomain\>* <br/>Port 5061 <br/>\_sipinternaltls.\_tcp.*<span></span>contoso<span></span>.com* <br/>Port 5061  |Front End pool FQDN  <br/>*FE-Pool.<span></span>contoso<span></span>.com*  |Enables Internal user automatic sign-in 1 to the Front End server/pool or SE server/pool that authenticates and redirects client requests for sign-in.  |&#x2777; |
|A/AAAA |sipinternal.*\<sipdomain\>* <br/>sipinternal.<span></span>*contoso<span></span>.com*  |Front End pool FQDN  <br/>_FE-Pool.<span></span>contoso<span></span>.com_  |Internal user access &#x2776;  |&#x2777;  |
|SRV   | \_ntp.\_udp.*\<sipdomain\>* <br/> \_ntp.\_udp.<span></span>*contoso<span></span>.com*  |TimeServer FQDN  <br/> north-america.pool.ntp.org   |NTP source required for Lync Phone Edition devices   |This is required to support desktop handsets.   |
|SRV   |\_sipfederationtls.\_tcp.*\<sipdomain\>* <br/>\_sipfederationtls.\_tcp.<span></span>*contoso<span></span>.com*  | Access Edge service FQDN <br/> EdgePool-int.<span></span>*contoso<span></span>.com*  |Create one SRV record for each SIP domain that has IOS or Windows phone Mobile clients.   |For Mobile client support   |
|A/AAAA   |admin URL  <br/>*Web-int.<span></span>contoso<span></span>.com*  |HLB FE Pool VIP  <br/> 192.168.21.121   |Skype for Business Server Control Panel, see [Simple URLs](dns.md#BK_Simple)  ||
|A/AAAA   |meet URL  <br/>*Web-int.<span></span>contoso<span></span>.com*  |HLB FE Pool VIP  <br/> 192.168.21.121   |Online meetings, see [Simple URLs](dns.md#BK_Simple)  ||
|A/AAAA   |dial-in URL  <br/>*Web-int.<span></span>contoso<span></span>.com*  |HLB FE Pool VIP  <br/> 192.168.21.121   |Dial-in conferencing, see [Simple URLs](dns.md#BK_Simple)  ||
|A/AAAA   |internal Web Services FQDN  <br/>*Web-int.<span></span>contoso<span></span>.com*  |HLB FE Pool VIP  <br/> 192.168.21.121   |Skype for Business Web Service used by Skype for Business Web App   ||
|A/AAAA   |Office Web Apps Server pool FQDN  <br/> OWA.<span></span>contoso<span></span>.com   | Office Web Apps Server pool VIP address <br/> 192.168.1.5   |Defines the Office Web Apps Server pool FQDN   ||
|A/AAAA   | Internal Web FQDN <br/> Web-int.<span></span>contoso<span></span>.com   | Front End pool VIP address <br/> 192.168.21.121   |Defines the Internal Web FQDN used by Skype for Business Web App  <br/> If you are using DNS load balancing on this pool, your Front End pool and internal web farm cannot have the same FQDN.   ||

&#x2776; Used by a client to discover the Front End Server or Front End pool, and be authenticated and signed in as a user. More detail on this is in [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#WalkthroughOfSkype).

&#x2777; This is only required to support legacy clients prior to Lync 2013, and desktop handsets.

&#x2778; In the situation where a Unified Communications device is turned on, but a user has never logged into the device, the A record allows the device to discover the server hosting Device Update Web service and obtain updates. Otherwise, devices obtain the server information though in-band provisioning the first time a user logs in.

The following diagram shows an example that includes both internal and external DNS records, and many of the records shown in the surrounding tables:

**Edge network diagram using Public IPv4 addresses**

![example of DNS network diagram](../../media/2cc9546e-5560-4d95-8fe4-65a792a0e9c3.png)

**Perimeter network DNS mappings (both internal and external interfaces)**

|Record Type|Value|Resolves to|Purpose|Required|
|:--- |:--- |:--- |:--- |:--- |
|A/AAAA   |Internal Edge pool FQDN  <br/>*EdgePool-int.<span></span>contoso<span></span>.com*  |Internal-facing Edge pool IP addresses  <br/> 172.25.33.10, 172.25.33.11   |Consolidated Edge Pool internal interface IP Addresses   |Y   |
|A/AAAA   |Edge Server FQDN  <br/>*Cons-1.<span></span>contoso<span></span>.com*  |Internal-facing server IP for a server in the Edge pool  <br/> 172.25.33.10   |Create a record for each server in the pool with the server FQDN pointing to its internal server node IP in the pool, see [DNS Load Balancing on Edge Server Pools](load-balancing.md#BK_Edge).   |Y   |
|A/AAAA   |Access Edge service Pool FQDN  <br/>*Access1.<span></span>contoso<span></span>.com*  |Access Edge service Pool external IP addresses  <br/> 131.107.16.10, 131.107.16.11   |The Access Edge service provides a single, trusted connection point for both outbound and inbound Session Initiation Protocol (SIP) traffic.   |Y   |
|A/AAAA   |Web Conferencing Edge service Pool FQDN  <br/>*Webcon1.<span></span>contoso<span></span>.com*  |Web Conferencing Edge service external IP addresses  <br/> 131.107.16.90, 131.107.16.91   |The Web Conferencing Edge service enables external users to join meetings that are hosted on your internal Skype for Business Server environment.   |Y   |
|A/AAAA   |*av.\<sip-domain\>* Pool FQDN <br/>*AV1.<span></span>contoso<span></span>.com*  |A/V Edge external IP addresses  <br/> 131.107.16.170, 131.107.16.171   |The A/V Edge service makes audio, video, application sharing and file transfer available to external users.   |Y   |
|CNAME   |sip.*\<sipdomain\>* <br/> sip.*<span></span>contoso<span></span>.com*  |External Access Edge Pool FQDN  <br/>*Access1.<span></span>contoso<span></span>.com*  |Locates the Edge Server pool . See [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#WalkthroughOfSkype)  |Y   |
|SRV   |\_sip.\_tls.*\<sipdomain\>* <br/>\_sip.\_tls.<span></span>*contoso<span></span>.com*  |External Access Edge FQDN  <br/>_Access1.<span></span>contoso<span></span>.com_  |Used for external user access. See [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#WalkthroughOfSkype)  |Y   |
|SRV   |\_sipfederationtls.\_tcp.*\<sipdomain\>* <br/>\_sipfederationtls.\_tcp.<span></span>*contoso<span></span>.com*  |External Access Edge FQDN  <br/>*Access1.<span></span>contoso<span></span>.com*  |Used for Federation and public IM connectivity   |&#x2776;  |
|SRV   |\_xmpp-server.\_tcp.*<sipdomain\>* <br/>\_xmpp-server.\_tcp.*<span></span>contoso<span></span>.com*  |External Access Edge FQDN  <br/>*Access1.<span></span>contoso<span></span>.com*  |The XMPP Proxy service accepts and sends extensible messaging and presence protocol (XMPP) messages to and from configured XMPP Federated partners.   |Y, to deploy Federation, otherwise optional  <br/> Not available in Skype for Business Server 2019.|
|SRV   |\_sipfederationtls.\_tcp.*\<sipdomain\>* <br/>\_sipfederationtls.\_tcp.*<span></span>contoso<span></span>.com*  |External Access Edge FQDN  <br/>*Access1.<span></span>contoso<span></span>.com*  |To support Push Notification Service and Apple Push Notification service, you create one SRV record for each SIP domain. &#x2778;  ||
|A/AAAA   |External Front End pool web services FQDN  <br/>*Web-ext.<span></span>contoso<span></span>.com*  |Reverse proxy public IP address, proxies to the External Web Services VIP for your Front End pool &#x2776; <br/> 131.107.155.1 proxy to 192.168.21.120   |Front End pool external interface used by Skype for Business Web App   |Y   |
|A/AAAA/CNAME   |lyncdiscover.*\<sipdomain\>* <br/> lyncdiscover.*<span></span>contoso<span></span>.com*  |Reverse proxy public IP address, resolves to the External Web Services VIP for your Director pool, if you have one, or for your Front End pool if you do not have a Director &#x2777; <br/> 131.107.155.1 proxy to 192.168.21.120   | External record for client AutoDiscover, also used by Mobility, Skype for Business Web App, and scheduler Web app, resolved by the reverse proxy server <br/> To support Push Notification Service and Apple Push Notification service, you create one SRV record for each SIP domain that has Microsoft Lync Mobile clients. 3  |Y   |
|A/AAAA   |meet.*\<sipdomain\>* <br/> meet.*<span></span>contoso<span></span>.com*  |Reverse proxy public IP address, resolves to the external Web interface for the Front End pool  <br/> 131.107.155.1 proxy to 192.168.21.120   |Proxy to Skype for Business Web Service  <br/> See [Simple URLs](dns.md#BK_Simple)  |Y   |
|A/AAAA   |dial-in.*\<sipdomain\>* <br/> dial-in.*<span></span>contoso<span></span>.com*  |Reverse proxy public IP address, proxies to the external Web interface for the Front End pool  <br/> 131.107.155.1 proxy to 192.168.21.120   |Proxy to Skype for Business Web Service  <br/> See [Simple URLs](dns.md#BK_Simple)  |Y   |
|A/AAAA   |Office Web Apps Server pool FQDN  <br/> OWA.<span></span>contoso<span></span>.com   | Reverse proxy public IP address, proxies to the external Web interface for the Office Web Apps Server <br/> 131.107.155.1 proxy to 192.168.1.5   | Office Web Apps Server pool VIP address <br/> 192.168.1.5   |Defines the Office Web Apps Server pool FQDN   |

&#x2776; Required to deploy Federation, otherwise optional.

&#x2777; Used by a client to discover the front end server or Front End pool, and be authenticated and signed in as a user.

&#x2778; This requirement applies only to clients on Apple or Microsoft based mobile devices. Android and Nokia Symbian devices do not use push notification.

 For more detail on Edge Servers and perimeter networks, see the Edge server [DNS planning](../../plan-your-deployment/edge-server-deployments/edge-environmental-requirements.md#DNSPlan) content.

> [!IMPORTANT]
> Skype for Business Server supports the use of IPv6 addressing. See [Plan for IPv6 in Skype for Business](ipv6.md) for more details.

> [!IMPORTANT]
> For more detail on FQDNs, see [DNS basics](basics.md).

**Split brain DNS**
<a name="BK_split"> </a>

Split brain DNS is a DNS configuration where you have two DNS zones with the same namespace. The first DNS zone handles internal requests, while the second DNS zone handles external requests, as mentioned in these tables. For more about this see [Split-brain DNS](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#SplitBrainDNS).

## Hybrid considerations
<a name="BK_Hybrid"> </a>

If you plan to have some users homed online and some homed on premises, refer to the Hybrid connectivity planning article [Skype for Business server 2019](../../../SfbHybrid/hybrid/plan-hybrid-connectivity.md?toc=/SkypeForBusiness/sfbhybridtoc/toc.json). You will need to configure DNS as normal for Skype for Business Server 2015 and also add additional DNS records.

You should also refer to "Office 365 URLs and IP address ranges" at [https://aka.ms/o365ips](https://aka.ms/o365ips) to confirm that your users will have access to the online resources they will need.

## Simple URLs
<a name="BK_Simple"> </a>

A Uniform Resource Locator (URL) is a reference to a web resource that specifies its location on a computer network and a protocol used to retrieve it.

Skype for Business Server supports using three "simple" URLs to access services:

- **Meet** is used as the base URL for all conferences in the site. An example of a Meet simple URL is https:<span></span>//<span></span>meet.<span></span>contoso<span></span>.com. A URL for a particular meeting might be https:<span></span>//<span></span>meet.<span></span>contoso<span></span>.com/_username_/7322994.

    With the Meet simple URL, links to join meetings are easy to comprehend and easy to communicate.

- **Dial-in** enables access to the Dial-in Conferencing Settings web page. This page displays conference dial-in numbers with their available languages, assigned conference information (that is, for meetings that do not need to be scheduled), and in-conference DTMF controls, and supports management of personal identification number (PIN) and assigned conferencing information. The Dial-in simple URL is included in all meeting invitations so that users who want to dial in to the meeting can access the necessary phone number and PIN information. An example of the Dial-in simple URL is https://<span></span>dialin.<span></span>contoso<span></span>.com.

- **Admin** enables quick access to the Skype for Business Server Control Panel. From any computer within your organization's firewalls, an admin can open the Skype for Business Server Control Panel by typing the Admin simple URL into a browser. The Admin simple URL is internal to your organization. An example of the Admin simple URL is https://<span></span>admin.<span></span>contoso<span></span>.com.

Simple URLs are discussed in more detail at [DNS requirements for simple URLs in Skype for Business Server](simple-urls.md).

## DNS by server role
<a name="BK_Servers"> </a>

You can set the names of these pools and servers as you wish, but make them memorable and reflect their function in the system.

### DNS records for individual servers or pools

These generic record requirements apply to any server role used by Skype for Business. A pool is a set of servers running the same services that work together to handle client requests directed to them through a load balancer. See [Load balancing requirements for Skype for Business](load-balancing.md) for details

**DNS record Requirements for Server/pool roles (presumes DNS load balancing)**

|Deployment scenario|DNS requirement|
|:-----|:-----|
|One Server:  <br/> Persistent Chat, Director, Mediation Server, Front end server   |An internal A record that resolves the fully qualified domain name (FQDN) of the server to its IP address.  <br/> ServerRole.<span></span>contoso<span></span>.com 10.10.10.0   |
|Pool:  <br/> Persistent Chat, Director, Edge Server, Mediation Server, Front end   |An internal A record that resolves the fully qualified domain name (FQDN) of each server node in the pool to its IP address.  <br/>**Example** <br/> ServerRole01.<span></span>contoso<span></span>.com 10.10.10.1  <br/> ServerRole02.<span></span>contoso<span></span>.com 10.10.10.2  <br/> Multiple internal A records that resolve the fully qualified domain name (FQDN) of the pool to the IP addresses of the server nodes in the pool.  <br/>**Example** <br/> ServerPool.<span></span>contoso<span></span>.com 10.10.10.1  <br/> ServerPool.<span></span>contoso<span></span>.com 10.10.10.2   |

### Edge Server specific DNS topics

 To plan edge server deployment, review [Plan for Edge Server deployments in Skype for Business Server 2015](../../plan-your-deployment/edge-server-deployments/edge-server-deployments.md), and [Advanced Edge Server DNS planning for Skype for Business Server 2015](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md) which has the following sections

- [DNS disaster recovery](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#DNSDR)

- [DNS load balancing](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#DNSLB)

- [Automatic configuration without split-brain DNS](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#NoSplitBrainDNS)

- [Split-brain DNS](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#SplitBrainDNS)

- [Walkthrough of Skype for Business clients locating services](../../plan-your-deployment/edge-server-deployments/advanced-edge-server-dns.md#WalkthroughOfSkype)


