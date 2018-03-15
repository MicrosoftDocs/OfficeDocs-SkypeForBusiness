---
title: "Port summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 4/27/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 91213b1e-f875-464b-83e8-fe3a351595a4
description: "The Lync Server 2013, Edge Server functionality described in this scenario architecture is very similar to what was implemented in Lync Server 2010. The most noticeable addition is the port 5269 over TCP entry for the extensible messaging and presence protocol (XMPP). Lync Server 2013 optionally deploys an XMPP proxy on the Edge Server or Edge pool and the XMPP gateway server on the Front End Server or Front End pool."
---

# Port summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013
[]
The Lync Server 2013, Edge Server functionality described in this scenario architecture is very similar to what was implemented in Lync Server 2010. The most noticeable addition is the port **5269 over TCP** entry for the extensible messaging and presence protocol (XMPP). Lync Server 2013 optionally deploys an XMPP proxy on the Edge Server or Edge pool and the XMPP gateway server on the Front End Server or Front End pool. 
  
In addition to IPv4, the Edge Server now supports IPv6. For clarity, only IPv4 is used in the scenarios.
  
**Scaled Consolidated Edge using Hardware Load Balancing**

![Edge Server Perimeter Network ports and protocols](media/Plan_LyncServer_Edge_NetPerimeter_ScaledConsolidatedEdgeHLB.jpg)
  
## Port and Protocol Details

It is recommended that you open only the ports required to support the functionality for which you are providing external access.
  
For remote access to work for any edge service, it is mandatory that SIP traffic is allowed to flow bi-directionally as shown in the Inbound/Outbound edge traffic figure. Stated another way, the SIP messaging to and from the Access Edge service is involved in instant messaging (IM), presence, web conferencing, audio/video (A/V) and federation.
  
**Firewall Summary for Scaled Consolidated Edge, Hardware Load Balanced: External Interface - Node 1 and Node 2 (Example)**

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|Access/HTTP/TCP/80  <br/> |Edge Server Access Edge service public IP address  <br/> |Any  <br/> |Certificate revocation/CRL check and retrieval  <br/> |
|Access/DNS/TCP/53  <br/> |Edge Server Access Edge service public IP address  <br/> |Any  <br/> |DNS query over TCP  <br/> |
|Access/DNS/UDP/53  <br/> |Edge Server Access Edge service public IP address  <br/> |Any  <br/> |DNS query over UDP  <br/> |
|A/V/RTP/TCP/50,000-59,999  <br/> |Edge Server A/V Edge service IP address  <br/> |Any  <br/> |Required for federating with partners running Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010 and Lync Server 2013.  <br/> |
|A/V/RTP/UDP/50,000-59,999  <br/> |Edge Server A/V Edge service public IP address  <br/> |Any  <br/> |Required only for federation with partners running Office Communications Server 2007.  <br/> |
|A/V/RTP/TCP/50,000-59,999  <br/> |Any  <br/> |Edge Server A/V Edge service public IP address  <br/> |Required only for federation with partners running Office Communications Server 2007  <br/> |
|A/V/RTP/UDP/50,000-59,999  <br/> |Any  <br/> |Edge Server A/V Edge service public IP address  <br/> |Required only for federation with partners running Office Communications Server 2007  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Edge Server A/V Edge service public IP address  <br/> |Any  <br/> |3478 outbound is used to determine the version of Edge Server that Lync Server is communicating with and also for media traffic from Edge Server-to-Edge Server. Required for federation with Lync Server 2010, Windows Live Messenger, and Office Communications Server 2007 R2, and also if multiple Edge pools are deployed within a company.  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Any  <br/> |Edge Server A/V Edge service public IP address  <br/> |STUN/TURN negotiation of candidates over UDP/3478  <br/> |
|A/V/STUN,MSTURN/TCP/443  <br/> |Any  <br/> |Edge Server A/V Edge service public IP address  <br/> |STUN/TURN negotiation of candidates over TCP/443  <br/> |
|A/V/STUN,MSTURN/TCP/443  <br/> |Edge Server A/V Edge service public IP address  <br/> |Any  <br/> |STUN/TURN negotiation of candidates over TCP/443  <br/> |
   
**Firewall Summary for Scaled Consolidated Edge, Hardware Load Balanced: Internal Interface Node 1 and Node 2**

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|XMPP/MTLS/TCP/23456  <br/> |Any (can be defined as Front End Server address, or Front End pool virtual IP address running the XMPP Gateway service)  <br/> |Edge Server internal interface  <br/> |Outbound XMPP traffic from XMPP Gateway service running on Front End Server or Front End pool  <br/> |
|HTTPS/TCP/4443  <br/> |Any (can be defined as the Front End Server server IP or pool that holds the Central Management store)  <br/> |Edge Server Internal interface  <br/> |Replication of changes from the Central Management store to the Edge Server  <br/> |
|PSOM/MTLS/TCP/8057  <br/> |Any (can be defined as Director IP, Front End Server IP or Pool virtual IP)  <br/> |Edge Server Internal interface  <br/> |Web conferencing traffic from Internal deployment to Internal Edge Server interface  <br/> |
|STUN/MSTURN/UDP/3478  <br/> |Any (can be defined as Director IP, Front End Server IP or Pool virtual IP)  <br/> |Edge Server Internal interface  <br/> |Preferred path for A/V media transfer between internal and external users, Survivable Branch Appliance or Survivable Branch Server  <br/> |
|STUN/MSTURN/TCP/443  <br/> |Any (can be defined as Director IP, Front End Server IP or Pool virtual IP)  <br/> |Edge Server Internal interface  <br/> |Fallback path for A/V media transfer between internal and external users, Survivable Branch Appliance or Survivable Branch Server if UDP communication cannot be established, TCP is used for file transfer and desktop sharing  <br/> |
|MTLS/TCP/50001  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection  <br/> |
|MTLS/TCP/50002  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection  <br/> |
|MTLS/TCP/50003  <br/> |Any  <br/> |Edge Server internal interface  <br/> |Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection  <br/> |
   
Hardware load balancers have specific requirements when deployed to provide availability and load balancing for Lync Server. The requirements are defined in the following figure and tables. Third party vendors may use different terminology for the requirements defined here. It will be necessary to map the requirements of Lync Server to the features and configuration options provided by your hardware load balancer vendor.
  
When configuring hardware load balancers, consider the following requirements:
  
- Source Network Address Translation (SNAT) can be configured on the hardware load balancer (HLB) for Access Edge service and Web Conferencing Edge service
    
- SNAT cannot be configured on the A/V Edge service- the A/V Edge service must respond with the real server address, not the HLB virtual IP (VIP), for simple traversal of UDP over NAT (STUN)/traversal using relay NAT (TURN)/federation TURN (FTURN) to work properly
    
  - If the client sends a request to the HLB, the response must come back from the HLB VIP
    
  - If the client sends a request to the Edge, the response must come back from the Edge IP
    
- Public IP addresses are used on each server interface and on the VIPs of the HLB, and your public IP address requirements are N+1, where there is a public IP address for each real server interface and one for each HLB VIP. Where you have 2 Edge servers in the pool, this results in 9 public IP addresses, where 3 are used for the HLB VIPs, and one for each Edge server interface (a total of six for the servers)
    
- For the Access Edge service and Web Conferencing Edge service, (and using NAT on the HLB) the client contacts the VIP, the VIP changes the source IP address from the client to its own IP address. The server interface addresses the return address to the VIP, the VIP changes the source address from the server interface IP address and sends the packet to the client
    
- For the A/V Edge service, the VIP must NOT change the source IP address, and the real server address is returned to the client directly - you cannot configure NAT on the HLB for AV traffic
    
  - If the client sends a request to the HLB VIP, the response must come back from the HLB VIP
    
  - If the client sends a request to the Edge IP, the response must come back from the Edge IP
    
- For AV, the external firewall will retain the real server public IP address for all packets
    
- Once established, client to A/V Edge service communication is to the real server, not the HLB
    
- Internal edge to internal servers and clients must be routed, and persistent routes are set for all internal networks that host servers or clients
    
- The HLB Access Edge service VIP will act as the default gateway for each Edge server interface
    
> [!NOTE]
> For further information on NAT planning and functionality, please refer to [Hardware load balancer requirements for Lync Server 2013](hardware-load-balancer-requirements.md). 
  
![Edge Server ports and protocols details](media/Plan_LyncServer_Edge_NetPerimeter_EdgeHLBDetail.jpg)
  
**External Port Settings Required for Scaled Consolidated Edge, Hardware Load Balanced: External Interface Virtual IPs**

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|XMPP/TCP/5269  <br/> |Any  <br/> |XMPP Proxy service (shares IP address with Access Edge service)  <br/> |XMPP Proxy service accepts traffic from XMPP contacts in defined XMPP federations  <br/> |
|XMPP/TCP/5269  <br/> |XMPP Proxy service (shares IP address with Access Edge service)  <br/> |Any  <br/> |XMPP Proxy service sends traffic to XMPP contacts in defined XMPP federations  <br/> |
|Access/SIP(TLS)/TCP/443  <br/> |Any  <br/> |Access Edge service public VIP address  <br/> |Client-to-server SIP traffic for external user access  <br/> |
|Access/SIP(MTLS)/TCP/5061  <br/> |Any  <br/> |Access Edge service public VIP address  <br/> |SIP signaling, federated and public IM connectivity using SIP  <br/> |
|Access/SIP(MTLS)/TCP/5061  <br/> |Access Edge service public VIP address  <br/> |Federated partner  <br/> |SIP signaling, federated and public IM connectivity using SIP  <br/> |
|Web Conferencing/PSOM(TLS)/TCP/443  <br/> |Any  <br/> |Edge Server Web Conferencing Edge service public VIP address  <br/> |Web Conferencing media  <br/> |
|A/V/STUN,MSTURN/UDP/3478  <br/> |Any  <br/> |Edge Server A/V Edge service public VIP address  <br/> |STUN/TURN negotiation of candidates over UDP/3478  <br/> |
|A/V/STUN,MSTURN/TCP/443  <br/> |Any  <br/> |Edge Server A/V Edge service public VIP address  <br/> |STUN/TURN negotiation of candidates over TCP/443  <br/> |
   
**Firewall Summary for Scaled Consolidated Edge, Hardware Load Balanced: Internal Interface Virtual IPs**

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|Access/SIP(MTLS)/TCP/5061  <br/> |Any (can be defined as Director, Director pool virtual IP address, Front End Server or Front End pool virtual IP address)  <br/> |Edge Server Internal VIP interface  <br/> |Outbound SIP traffic (from Director, Director pool virtual IP address, Front End Server or Front End pool virtual IP address)to Internal Edge VIP  <br/> |
|Access/SIP(MTLS)/TCP/5061  <br/> |Edge Server Internal VIP interface  <br/> |Any (can be defined as Director, Director pool virtual IP address, Front End Server or Front End pool virtual IP address)  <br/> |Inbound SIP traffic (to Director, Director pool virtual IP address, Front End Server or Front End pool virtual IP address) from Edge Server internal interface  <br/> |
|SIP/MTLS/TCP/5062  <br/> |Any (can be defined as Front End Server IP address, or Front End pool IP address or any Survivable Branch Appliance or Survivable Branch Server using this Edge Server)  <br/> |Edge Server Internal VIP interface  <br/> |Authentication of A/V users (A/V authentication service) from Front End Server or Front End pool IP address or any Survivable Branch Appliance or Survivable Branch Server using this Edge Server  <br/> |
|STUN/MSTURN/UDP/3478  <br/> |Any  <br/> |Edge Server Internal VIP interface  <br/> |Preferred path for A/V media transfer between internal and external users  <br/> |
|STUN/MSTURN/TCP/443  <br/> |Any  <br/> |Edge Server Internal VIP interface  <br/> |Fallback path for A/V media transfer between internal and external users if UDP communication cannot be established, TCP is used for file transfer and desktop sharing  <br/> |
|STUN/MSTURN/TCP/443  <br/> |Edge Server Internal VIP interface  <br/> |Any  <br/> |Fallback path for A/V media transfer between internal and external users if UDP communication cannot be established, TCP is used for file transfer and desktop sharing  <br/> |
   

