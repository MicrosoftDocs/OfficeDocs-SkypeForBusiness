---
title: "Port summary - Single consolidated edge with private IP addresses using NAT in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3c1a389f-5f42-4719-a05b-e0b84aa3eb9e
description: "In this articlePort and Protocol DetailsFirewall Summary for FederationFirewall Summary - Public Instant Messaging ConnectivityFirewall Summary for Extensible Messaging and Presence Protocol"
---

# Port summary - Single consolidated edge with private IP addresses using NAT in Lync Server 2013
[]
 **In this article**
  
[Port and Protocol Details](#sectionSection0)
  
[Firewall Summary for Federation](#sectionSection1)
  
[Firewall Summary - Public Instant Messaging Connectivity](#sectionSection2)
  
[Firewall Summary for Extensible Messaging and Presence Protocol](#sectionSection3)
  
The Lync Server 2013, Edge Server functionality described in this scenario architecture is very similar to what was implemented in Lync Server 2010. The most noticeable addition is the port **5269 over TCP** entry for the extensible messaging and presence protocol (XMPP). Lync Server 2013 optionally deploys an XMPP proxy on the Edge Server or Edge pool and the XMPP gateway server on the Front End Server or Front End pool. 
  
In addition to IPv4, the Edge Server now supports IPv6. For clarity, only IPv4 is used in the scenarios.
  
**Network Perimeter for a Single Consolidated Edge Server with Private IP Addressing Using NAT**

![Single Consolidated Edge Server](media/Plan_LyncServer_Edge_NetPerimeter_SingleConsolidatedEdge.jpg)
  
## Port and Protocol Details
<a name="sectionSection0"> </a>

We recommend that you open only the ports required to support the functionality for which you are providing external access. 
  
For remote access to work for any edge service, it is mandatory that SIP traffic is allowed to flow bi-directionally as shown in the Inbound/Outbound edge traffic figure. Stated another way, the SIP messaging to and from the Access Edge service is involved in instant messaging (IM), presence, web conferencing, audio/video (A/V), and federation.
  
**Firewall Summary for Single Consolidated Edge with Private IP Addresses using NAT: External Interface**

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|XMPP/TCP/5269  <br/> |Any  <br/> |XMPP Proxy service (shares IP address with Access Edge service)  <br/> |XMPP Proxy service accepts traffic from XMPP contacts in defined XMPP federations  <br/> |
|Access/HTTP/TCP/80  <br/> |Edge Server Access Edge service  <br/> |Any  <br/> |Certificate revocation/CRL check and retrieval  <br/> |
|Access/DNS/TCP/53  <br/> |Edge Server Access Edge service  <br/> |Any  <br/> |DNS query over TCP  <br/> |
|Access/DNS/UDP/53  <br/> |Edge Server Access Edge service  <br/> |Any  <br/> |DNS query over UDP  <br/> |
|Access/SIP(TLS)/TCP/443  <br/> |Any  <br/> |Edge Server Access Edge service  <br/> |Client-to-server SIP traffic for external user access  <br/> |
|Access/SIP(MTLS)/TCP/5061  <br/> |Any  <br/> |Edge Server Access Edge service  <br/> |For federated and public IM connectivity using SIP  <br/> |
|Access/SIP(MTLS)/TCP/5061  <br/> |Edge Server Access Edge service  <br/> |Any  <br/> |For federated and public IM connectivity using SIP  <br/> |
|Web Conferencing/PSOM(TLS)/TCP/443  <br/> |Any  <br/> |Edge Server Web Conferencing Edge service  <br/> |Web Conferencing media  <br/> |
|A/V/RTP/TCP/50,000-59,999  <br/> |Edge Server A/V Edge service  <br/> |Any  <br/> |Required for federating with partners running Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010 and Lync Server 2013.  <br/> |
|A/V/RTP/UDP/50,000-59,999  <br/> |Edge Server A/V Edge service  <br/> |Any  <br/> |Required only for federation with partners running Office Communications Server 2007.  <br/> |
|A/V/RTP/TCP/50,000-59,999  <br/> |Any  <br/> |Edge Server A/V Edge service  <br/> |Required only for federation with partners running Office Communications Server 2007  <br/> |
|A/V/RTP/UDP/50,000-59,999  <br/> |Any  <br/> |Edge Server A/V Edge service  <br/> |Required only for federation with partners running Office Communications Server 2007  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Edge Server A/V Edge service  <br/> |Any  <br/> |3478 outbound is used to determine the version of Edge Server that Lync Server is communicating with and also for media traffic from Edge Server-to-Edge Server. Required for federation with Lync Server 2010, Windows Live Messenger, and Office Communications Server 2007 R2, and also if multiple Edge pools are deployed within a company.  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Any  <br/> |Edge Server A/V Edge service  <br/> |STUN/TURN negotiation of candidates over UDP/3478  <br/> |
|A/V/STUN,MSTURN/TCP/443  <br/> |Any  <br/> |Edge Server A/V Edge service  <br/> |STUN/TURN negotiation of candidates over TCP/443  <br/> |
|A/V/STUN,MSTURN/TCP/443  <br/> |Edge Server A/V Edge service  <br/> |Any  <br/> |STUN/TURN negotiation of candidates over TCP/443  <br/> |
   
**Firewall Summary for Single Consolidated Edge with Private IP Addresses Using NAT: Internal Interface**

|**Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Comments**|
|:-----|:-----|:-----|:-----|
|XMPP/MTLS/TCP/23456  <br/> |Any (can be defined as Standard Edition server IP, Standard Edition server IP address, or pool IP address running the XMPP Gateway service)  <br/> |Edge Server internal interface  <br/> |Outbound XMPP traffic from XMPP Gateway service running on Front End Server or Front End pool  <br/> |
|SIP/MTLS/TCP/5061  <br/> |Any (can be defined as Director, Director pool IP address, Front End Server or Front End pool IP address)  <br/> |Edge Server internal interface  <br/> |Outbound SIP traffic (from Director, Director pool IP address, Front End Server or Front End pool IP address) to Edge Server internal interface  <br/> |
|SIP/MTLS/TCP/5061  <br/> |Edge Server internal interface  <br/> |Any (can be defined as Director, Director pool IP address, Front End Server or Front End pool IP address)  <br/> |Inbound SIP traffic (to Director, Director pool IP address, Front End Server or Front End pool IP address) from Edge Server internal interface  <br/> |
|PSOM/MTLS/TCP/8057  <br/> |Any (can be defined as Front End Server IP address, or each Front End Server IP address in a Front End pool)  <br/> |Edge Server internal interface  <br/> |Web conferencing traffic from Front End Server or each Front End Server if in a pool, to Edge Server internal interface  <br/> |
|SIP/MTLS/TCP/5062  <br/> |Any (can be defined as Front End Server IP address, or Front End pool IP address or any Survivable Branch Appliance or Survivable Branch Server using this Edge Server)  <br/> |Edge Server internal interface  <br/> |Authentication of A/V users (A/V authentication service) from Front End Server or Front End pool IP address or any Survivable Branch Appliance or Survivable Branch Server using this Edge Server  <br/> |
|STUN/MSTURN/UDP/3478  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Preferred path for A/V media transfer between internal and external users, Survivable Branch Appliance or Survivable Branch Server  <br/> |
|STUN/MSTURN/TCP/443  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Fallback path for A/V media transfer between internal and external users, Survivable Branch Appliance or Survivable Branch Server if UDP communication cannot be established, TCP is used for file transfer and desktop sharing  <br/> |
|HTTPS/TCP/4443  <br/> |Any (can be defined as the Front End Server IP address, or pool that holds the Central Management store)  <br/> |Edge Server internal interface  <br/> |Replication of changes from the Central Management store to the Edge Server  <br/> |
|MTLS/TCP/50001  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection  <br/> |
|MTLS/TCP/50002  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection  <br/> |
|MTLS/TCP/50003  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection  <br/> |
   
## Firewall Summary for Federation
<a name="sectionSection1"> </a>

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|Access/SIP(MTLS)/TCP/5061  <br/> |Access Edge service public IP address  <br/> |Any  <br/> |For federated and public IM connectivity using SIP  <br/> |
   
## Firewall Summary - Public Instant Messaging Connectivity
<a name="sectionSection2"> </a>

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|Access/SIP(MTLS)/TCP/5061  <br/> |Public IM connectivity partners  <br/> |Edge Server Access Edge service  <br/> |For federated and public IM connectivity using SIP  <br/> |
|Access/SIP(MTLS)/TCP/5061  <br/> |Edge Server Access Edge service  <br/> |Public IM connectivity partners  <br/> |For federated and public IM connectivity using SIP  <br/> |
|Access/SIP(TLS)/TCP/443  <br/> |Clients  <br/> |Edge Server Access Edge service  <br/> |Client-to-server SIP traffic for external user access  <br/> |
|A/V/RTP/TCP/50,000-59,999  <br/> |Edge Server A/V Edge service  <br/> |Live Messenger clients  <br/> |Used for A/V sessions with Windows Live Messenger if public IM connectivity is configured.  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Edge Server A/V Edge service  <br/> |Live Messenger clients  <br/> |Required for public IM connectivity with Windows Live Messenger  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Live Messenger clients  <br/> |Edge Server A/V Edge service  <br/> |Required for public IM connectivity with Windows Live Messenger  <br/> |
   
## Firewall Summary for Extensible Messaging and Presence Protocol
<a name="sectionSection3"> </a>

|**Protocol/TCP or UDP/Port**|**Source (IP address)**|**Destination (IP address)**|**Comments**|
|:-----|:-----|:-----|:-----|
|XMPP/TCP/5269  <br/> | Any  <br/> |Edge Server Access Edge service interface IP address  <br/> |Standard server-to-server communication port for XMPP. Allows communication to the Edge Server XMPP proxy from federated XMPP partners  <br/> |
|XMPP/TCP/5269  <br/> |Edge Server Access Edge service interface IP address  <br/> |Any  <br/> |Standard server-to-server communication port for XMPP. Allows communication from the Edge Server XMPP proxy to federated XMPP partners  <br/> |
|XMPP/MTLS/TCP/23456  <br/> |Any  <br/> |Each internal Edge Server Interface IP  <br/> |Internal XMPP traffic from the XMPP Gateway on the Front End Server or Front End pool to the Edge Server internal IP address or each Edge pool member's internal IP address  <br/> |
   

