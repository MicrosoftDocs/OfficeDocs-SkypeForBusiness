---
title: 'Port summary - Scaled consolidated edge with hardware load balancers'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Port summary - Scaled consolidated edge with hardware load balancers
ms:assetid: 91213b1e-f875-464b-83e8-fe3a351595a4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398739(v=OCS.15)
ms:contentKeyID: 48184841
ms.date: 04/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Port summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-04-27_

The Lync Server 2013, Edge Server functionality described in this scenario architecture is very similar to what was implemented in Lync Server 2010. The most noticeable addition is the port **5269 over TCP** entry for the extensible messaging and presence protocol (XMPP). Lync Server 2013 optionally deploys an XMPP proxy on the Edge Server or Edge pool and the XMPP gateway server on the Front End Server or Front End pool.

In addition to IPv4, the Edge Server now supports IPv6. For clarity, only IPv4 is used in the scenarios.

**Scaled Consolidated Edge using Hardware Load Balancing**

![Edge Server Perimeter Network ports and protocols](images/Gg398739.063f7dd1-16db-4cc7-8708-bca9bc41184d(OCS.15).jpg "Edge Server Perimeter Network ports and protocols")

<div>

## Port and Protocol Details

It is recommended that you open only the ports required to support the functionality for which you are providing external access.

For remote access to work for any edge service, it is mandatory that SIP traffic is allowed to flow bi-directionally as shown in the Inbound/Outbound edge traffic figure. Stated another way, the SIP messaging to and from the Access Edge service is involved in instant messaging (IM), presence, web conferencing, audio/video (A/V) and federation.

### Firewall Summary for Scaled Consolidated Edge, Hardware Load Balanced: External Interface – Node 1 and Node 2 (Example)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Role/Protocol/TCP or UDP/Port</th>
<th>Source IP address</th>
<th>Destination IP address</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Access/HTTP/TCP/80</p></td>
<td><p>Edge Server Access Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>Certificate revocation/CRL check and retrieval</p></td>
</tr>
<tr class="even">
<td><p>Access/DNS/TCP/53</p></td>
<td><p>Edge Server Access Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>DNS query over TCP</p></td>
</tr>
<tr class="odd">
<td><p>Access/DNS/UDP/53</p></td>
<td><p>Edge Server Access Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>DNS query over UDP</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>Edge Server A/V Edge service IP address</p></td>
<td><p>Any</p></td>
<td><p>Required for federating with partners running Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010 and Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/RTP/UDP/50,000-59,999</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>Required only for federation with partners running Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>Any</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>Required only for federation with partners running Office Communications Server 2007</p></td>
</tr>
<tr class="odd">
<td><p>A/V/RTP/UDP/50,000-59,999</p></td>
<td><p>Any</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>Required only for federation with partners running Office Communications Server 2007</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>3478 outbound is used to determine the version of Edge Server that Lync Server is communicating with and also for media traffic from Edge Server-to-Edge Server. Required for federation with Lync Server 2010, Windows Live Messenger, and Office Communications Server 2007 R2, and also if multiple Edge pools are deployed within a company.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Any</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>STUN/TURN negotiation of candidates over UDP/3478</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>Any</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>STUN/TURN negotiation of candidates over TCP/443</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>STUN/TURN negotiation of candidates over TCP/443</p></td>
</tr>
</tbody>
</table>


### Firewall Summary for Scaled Consolidated Edge, Hardware Load Balanced: Internal Interface Node 1 and Node 2

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Role/Protocol/TCP or UDP/Port</th>
<th>Source IP address</th>
<th>Destination IP address</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/MTLS/TCP/23456</p></td>
<td><p>Any (can be defined as Front End Server address, or Front End pool virtual IP address running the XMPP Gateway service)</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Outbound XMPP traffic from XMPP Gateway service running on Front End Server or Front End pool</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/4443</p></td>
<td><p>Any (can be defined as the Front End Server server IP or pool that holds the Central Management store)</p></td>
<td><p>Edge Server Internal interface</p></td>
<td><p>Replication of changes from the Central Management store to the Edge Server</p></td>
</tr>
<tr class="odd">
<td><p>PSOM/MTLS/TCP/8057</p></td>
<td><p>Any (can be defined as Director IP, Front End Server IP or Pool virtual IP)</p></td>
<td><p>Edge Server Internal interface</p></td>
<td><p>Web conferencing traffic from Internal deployment to Internal Edge Server interface</p></td>
</tr>
<tr class="even">
<td><p>STUN/MSTURN/UDP/3478</p></td>
<td><p>Any (can be defined as Director IP, Front End Server IP or Pool virtual IP)</p></td>
<td><p>Edge Server Internal interface</p></td>
<td><p>Preferred path for A/V media transfer between internal and external users, Survivable Branch Appliance or Survivable Branch Server</p></td>
</tr>
<tr class="odd">
<td><p>STUN/MSTURN/TCP/443</p></td>
<td><p>Any (can be defined as Director IP, Front End Server IP or Pool virtual IP)</p></td>
<td><p>Edge Server Internal interface</p></td>
<td><p>Fallback path for A/V media transfer between internal and external users, Survivable Branch Appliance or Survivable Branch Server if UDP communication cannot be established, TCP is used for file transfer and desktop sharing</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50001</p></td>
<td><p>Any</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50002</p></td>
<td><p>Any</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50003</p></td>
<td><p>Any</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection</p></td>
</tr>
</tbody>
</table>


Hardware load balancers have specific requirements when deployed to provide availability and load balancing for Lync Server. The requirements are defined in the following figure and tables. Third party vendors may use different terminology for the requirements defined here. It will be necessary to map the requirements of Lync Server to the features and configuration options provided by your hardware load balancer vendor.

When configuring hardware load balancers, consider the following requirements:

  - Source Network Address Translation (SNAT) can be configured on the hardware load balancer (HLB) for Access Edge service and Web Conferencing Edge service

  - SNAT cannot be configured on the A/V Edge service– the A/V Edge service must respond with the real server address, not the HLB virtual IP (VIP), for simple traversal of UDP over NAT (STUN)/traversal using relay NAT (TURN)/federation TURN (FTURN) to work properly
    
      - If the client sends a request to the HLB, the response must come back from the HLB VIP
    
      - If the client sends a request to the Edge, the response must come back from the Edge IP

  - Public IP addresses are used on each server interface and on the VIPs of the HLB, and your public IP address requirements are N+1, where there is a public IP address for each real server interface and one for each HLB VIP. Where you have 2 Edge servers in the pool, this results in 9 public IP addresses, where 3 are used for the HLB VIPs, and one for each Edge server interface (a total of six for the servers)

  - For the Access Edge service and Web Conferencing Edge service, (and using NAT on the HLB) the client contacts the VIP, the VIP changes the source IP address from the client to its own IP address. The server interface addresses the return address to the VIP, the VIP changes the source address from the server interface IP address and sends the packet to the client

  - For the A/V Edge service, the VIP must NOT change the source IP address, and the real server address is returned to the client directly – you cannot configure NAT on the HLB for AV traffic
    
      - If the client sends a request to the HLB VIP, the response must come back from the HLB VIP
    
      - If the client sends a request to the Edge IP, the response must come back from the Edge IP

  - For AV, the external firewall will retain the real server public IP address for all packets

  - Once established, client to A/V Edge service communication is to the real server, not the HLB

  - Internal edge to internal servers and clients must be routed, and persistent routes are set for all internal networks that host servers or clients

  - The HLB Access Edge service VIP will act as the default gateway for each Edge server interface

<div>


> [!NOTE]
> For further information on NAT planning and functionality, please refer to <A href="lync-server-2013-hardware-load-balancer-requirements.md">Hardware load balancer requirements for Lync Server 2013</A>.



</div>

![Edge Server ports and protocols details](images/Gg398739.1c193b80-98ab-4d59-a854-dbfdb5e209e2(OCS.15).jpg "Edge Server ports and protocols details")

### External Port Settings Required for Scaled Consolidated Edge, Hardware Load Balanced: External Interface Virtual IPs

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Role/Protocol/TCP or UDP/Port</th>
<th>Source IP address</th>
<th>Destination IP address</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Any</p></td>
<td><p>XMPP Proxy service (shares IP address with Access Edge service)</p></td>
<td><p>XMPP Proxy service accepts traffic from XMPP contacts in defined XMPP federations</p></td>
</tr>
<tr class="even">
<td><p>XMPP/TCP/5269</p></td>
<td><p>XMPP Proxy service (shares IP address with Access Edge service)</p></td>
<td><p>Any</p></td>
<td><p>XMPP Proxy service sends traffic to XMPP contacts in defined XMPP federations</p></td>
</tr>
<tr class="odd">
<td><p>Access/SIP(TLS)/TCP/443</p></td>
<td><p>Any</p></td>
<td><p>Access Edge service public VIP address</p></td>
<td><p>Client-to-server SIP traffic for external user access</p></td>
</tr>
<tr class="even">
<td><p>Access/SIP(MTLS)/TCP/5061</p></td>
<td><p>Any</p></td>
<td><p>Access Edge service public VIP address</p></td>
<td><p>SIP signaling, federated and public IM connectivity using SIP</p></td>
</tr>
<tr class="odd">
<td><p>Access/SIP(MTLS)/TCP/5061</p></td>
<td><p>Access Edge service public VIP address</p></td>
<td><p>Federated partner</p></td>
<td><p>SIP signaling, federated and public IM connectivity using SIP</p></td>
</tr>
<tr class="even">
<td><p>Web Conferencing/PSOM(TLS)/TCP/443</p></td>
<td><p>Any</p></td>
<td><p>Edge Server Web Conferencing Edge service public VIP address</p></td>
<td><p>Web Conferencing media</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Any</p></td>
<td><p>Edge Server A/V Edge service public VIP address</p></td>
<td><p>STUN/TURN negotiation of candidates over UDP/3478</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>Any</p></td>
<td><p>Edge Server A/V Edge service public VIP address</p></td>
<td><p>STUN/TURN negotiation of candidates over TCP/443</p></td>
</tr>
</tbody>
</table>


### Firewall Summary for Scaled Consolidated Edge, Hardware Load Balanced: Internal Interface Virtual IPs

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Role/Protocol/TCP or UDP/Port</th>
<th>Source IP address</th>
<th>Destination IP address</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Access/SIP(MTLS)/TCP/5061</p></td>
<td><p>Any (can be defined as Director, Director pool virtual IP address, Front End Server or Front End pool virtual IP address)</p></td>
<td><p>Edge Server Internal VIP interface</p></td>
<td><p>Outbound SIP traffic (from Director, Director pool virtual IP address, Front End Server or Front End pool virtual IP address)to Internal Edge VIP</p></td>
</tr>
<tr class="even">
<td><p>Access/SIP(MTLS)/TCP/5061</p></td>
<td><p>Edge Server Internal VIP interface</p></td>
<td><p>Any (can be defined as Director, Director pool virtual IP address, Front End Server or Front End pool virtual IP address)</p></td>
<td><p>Inbound SIP traffic (to Director, Director pool virtual IP address, Front End Server or Front End pool virtual IP address) from Edge Server internal interface</p></td>
</tr>
<tr class="odd">
<td><p>SIP/MTLS/TCP/5062</p></td>
<td><p>Any (can be defined as Front End Server IP address, or Front End pool IP address or any Survivable Branch Appliance or Survivable Branch Server using this Edge Server)</p></td>
<td><p>Edge Server Internal VIP interface</p></td>
<td><p>Authentication of A/V users (A/V authentication service) from Front End Server or Front End pool IP address or any Survivable Branch Appliance or Survivable Branch Server using this Edge Server</p></td>
</tr>
<tr class="even">
<td><p>STUN/MSTURN/UDP/3478</p></td>
<td><p>Any</p></td>
<td><p>Edge Server Internal VIP interface</p></td>
<td><p>Preferred path for A/V media transfer between internal and external users</p></td>
</tr>
<tr class="odd">
<td><p>STUN/MSTURN/TCP/443</p></td>
<td><p>Any</p></td>
<td><p>Edge Server Internal VIP interface</p></td>
<td><p>Fallback path for A/V media transfer between internal and external users if UDP communication cannot be established, TCP is used for file transfer and desktop sharing</p></td>
</tr>
<tr class="even">
<td><p>STUN/MSTURN/TCP/443</p></td>
<td><p>Edge Server Internal VIP interface</p></td>
<td><p>Any</p></td>
<td><p>Fallback path for A/V media transfer between internal and external users if UDP communication cannot be established, TCP is used for file transfer and desktop sharing</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

