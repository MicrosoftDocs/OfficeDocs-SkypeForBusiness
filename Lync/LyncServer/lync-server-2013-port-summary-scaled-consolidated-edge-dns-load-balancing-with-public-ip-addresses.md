---
title: 'Lync Server 2013: Port summary - Scaled consolidated edge, DNS load balancing with public IP addresses'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Port summary - Scaled consolidated edge, DNS load balancing with public IP addresses
ms:assetid: f7cbd0f1-841d-4116-8d17-e9d991daa4a8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205394(v=OCS.15)
ms:contentKeyID: 48185865
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Port summary - Scaled consolidated edge, DNS load balancing with public IP addresses in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-04-03_

The Lync Server 2013, Edge Server functionality described in this scenario architecture is very similar to what was implemented in Lync Server 2010. The most noticeable addition is the port **5269 over TCP** entry for the extensible messaging and presence protocol (XMPP). Lync Server 2013 optionally deploys an XMPP proxy on the Edge Server or Edge pool and the XMPP gateway server on the Front End Server or Front End pool.

In addition to IPv4, the Edge Server now supports IPv6. For clarity, only IPv4 is used in the scenarios.

**Enterprise perimeter network for Scaled Consolidated Edge, DNS Load Balancing with Public IP Addresses**

![96f5a8f5-16d2-464d-b86e-7c7ecfc89ead](images/JJ205394.96f5a8f5-16d2-464d-b86e-7c7ecfc89ead(OCS.15).jpg "96f5a8f5-16d2-464d-b86e-7c7ecfc89ead")

<div>

## Port and Protocol Details

It is recommended that you open only the ports required to support the functionality for which you are providing external access.

For remote access to work for any edge service, it is mandatory that SIP traffic is allowed to flow bi-directionally as shown in the Inbound/Outbound edge traffic figure. Stated another way, the SIP messaging to and from the Access Edge service is involved in instant messaging (IM), presence, web conferencing, audio/video (A/V) and federation.

### Firewall Summary for Scaled Consolidated Edge, DNS Load Balancing with Public IP Addresses: External Interface – Node 1 and Node 2 (Example)

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
<td><p>Access/HTTP/TCP/80</p></td>
<td><p>Edge Server Access Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>Certificate revocation/CRL check and retrieval</p></td>
</tr>
<tr class="odd">
<td><p>Access/DNS/TCP/53</p></td>
<td><p>Edge Server Access Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>DNS query over TCP</p></td>
</tr>
<tr class="even">
<td><p>Access/DNS/UDP/53</p></td>
<td><p>Edge Server Access Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>DNS query over UDP</p></td>
</tr>
<tr class="odd">
<td><p>Access/SIP(TLS)/TCP/443</p></td>
<td><p>Any</p></td>
<td><p>Edge Server Access Edge service public IP address</p></td>
<td><p>Client-to-server SIP traffic for external user access</p></td>
</tr>
<tr class="even">
<td><p>Access/SIP(MTLS)/TCP/5061</p></td>
<td><p>Any</p></td>
<td><p>Edge Server Access Edge service public IP address</p></td>
<td><p>For federated and public IM connectivity using SIP</p></td>
</tr>
<tr class="odd">
<td><p>Access/SIP(MTLS)/TCP/5061</p></td>
<td><p>Edge Server Access Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>For federated and public IM connectivity using SIP</p></td>
</tr>
<tr class="even">
<td><p>Web Conferencing/PSOM(TLS)TCP/443</p></td>
<td><p>Any</p></td>
<td><p>Edge Server Web Conferencing Edge service public IP address</p></td>
<td><p>Web Conferencing media</p></td>
</tr>
<tr class="odd">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>Required for federating with partners running Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010 and Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/UDP/50,000-59,999</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>Required only for federation with partners running Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>Any</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>Required only for federation with partners running Office Communications Server 2007</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/UDP/50,000-59,999</p></td>
<td><p>Any</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>Required only for federation with partners running Office Communications Server 2007</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>3478 outbound is used to determine the version of Edge Server that Lync Server is communicating with and also for media traffic from Edge Server-to-Edge Server. Required for federation with Lync Server 2010, Windows Live Messenger, and Office Communications Server 2007 R2, and also if multiple Edge pools are deployed within a company.</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Any</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>STUN/TURN negotiation of candidates over UDP/3478</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>Any</p></td>
<td><p>Edge Server A/V Edge service public IP address</p></td>
<td><p>STUN/TURN negotiation of candidates over TCP/443</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>Edge Server A/V Edge service</p></td>
<td><p>Any</p></td>
<td><p>STUN/TURN negotiation of candidates over TCP/443</p></td>
</tr>
</tbody>
</table>


### Firewall Summary for Scaled Consolidated Edge, DNS Load Balancing with Public IP Addresses: Internal Interface – Node 1 and Node 2 (Example)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocol/TCP or UDP/Port</th>
<th>Source IP address</th>
<th>Destination IP address</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/MTLS/TCP/23456</p></td>
<td><p>Any (can be defined as Front End Server address, or Front End pool IP address running the XMPP Gateway service)</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Outbound XMPP traffic from XMPP Gateway service running on Front End Server or Front End pool</p></td>
</tr>
<tr class="even">
<td><p>SIP/MTLS/TCP/5061</p></td>
<td><p>Any (can be defined as Director, Director pool IP address, Front End Server or Front End pool IP address)</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Outbound SIP traffic (from Director, Director pool IP address, Front End Server or Front End pool IP address) to Edge Server internal interface</p></td>
</tr>
<tr class="odd">
<td><p>SIP/MTLS/TCP/5061</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Any (can be defined as Director, Director pool IP address, Front End Server or Front End pool IP address)</p></td>
<td><p>Inbound SIP traffic (to Director, Director pool IP address, Front End Server or Front End pool IP address) from Edge Server internal interface</p></td>
</tr>
<tr class="even">
<td><p>PSOM/MTLS/TCP/8057</p></td>
<td><p>Any (can be defined as Front End Server IP address, or each Front End Server IP address in a Front End pool)</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Web conferencing traffic from Front End Server or each Front End Server if in a pool, to Edge Server internal interface</p></td>
</tr>
<tr class="odd">
<td><p>SIP/MTLS/TCP/5062</p></td>
<td><p>Any (can be defined as Front End Server IP address, or Front End pool IP address or any Survivable Branch Appliance or Survivable Branch Server using this Edge Server)</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Authentication of A/V users (A/V authentication service) from Front End Server or Front End pool IP address or any Survivable Branch Appliance or Survivable Branch Server using this Edge Server</p></td>
</tr>
<tr class="even">
<td><p>STUN/MSTURN/UDP/3478</p></td>
<td><p>Any</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Preferred path for A/V media transfer between internal and external users, Survivable Branch Appliance or Survivable Branch Server</p></td>
</tr>
<tr class="odd">
<td><p>STUN/MSTURN/TCP/443</p></td>
<td><p>Any</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Fallback path for A/V media transfer between internal and external users, Survivable Branch Appliance or Survivable Branch Server if UDP communication cannot be established, TCP is used for file transfer and desktop sharing</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/4443</p></td>
<td><p>Any (can be defined as the Front End Server IP address, or pool that holds the Central Management store)</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Replication of changes from the Central Management store to the Edge Server</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50001</p></td>
<td><p>Any</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50002</p></td>
<td><p>Any</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50003</p></td>
<td><p>Any</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Centralized Logging Service controller using Lync Server Management Shell and Centralized Logging Service cmdlets, ClsController command line (ClsController.exe) or agent (ClsAgent.exe) commands and log collection</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Firewall Summary for Federation


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
<td><p>Access Edge service public IP address</p></td>
<td><p>Any</p></td>
<td><p>For federated and public IM connectivity using SIP</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Firewall Summary – Public Instant Messaging Connectivity


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
<td><p>Public IM connectivity partners</p></td>
<td><p>Edge Server Access Edge service</p></td>
<td><p>For federated and public IM connectivity using SIP</p></td>
</tr>
<tr class="even">
<td><p>Access/SIP(MTLS)/TCP/5061</p></td>
<td><p>Edge Server Access Edge service</p></td>
<td><p>Public IM connectivity partners</p></td>
<td><p>For federated and public IM connectivity using SIP</p></td>
</tr>
<tr class="odd">
<td><p>Access/SIP(TLS)/TCP/443</p></td>
<td><p>Clients</p></td>
<td><p>Edge Server Access Edge service</p></td>
<td><p>Client-to-server SIP traffic for external user access</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>Edge Server A/V Edge service</p></td>
<td><p>Live Messenger clients</p></td>
<td><p>Used for A/V sessions with Windows Live Messenger if public IM connectivity is configured.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Edge Server A/V Edge service</p></td>
<td><p>Live Messenger clients</p></td>
<td><p>Required for public IM connectivity with Windows Live Messenger</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Live Messenger clients</p></td>
<td><p>Edge Server A/V Edge service</p></td>
<td><p>Required for public IM connectivity with Windows Live Messenger</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Firewall Summary for Extensible Messaging and Presence Protocol


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocol/TCP or UDP/Port</th>
<th>Source (IP address)</th>
<th>Destination (IP address)</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Any</p></td>
<td><p>Edge Server Access Edge service interface IP address</p></td>
<td><p>Standard server-to-server communication port for XMPP. Allows communication to the Edge Server XMPP proxy from federated XMPP partners</p></td>
</tr>
<tr class="even">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Edge Server Access Edge service interface IP address</p></td>
<td><p>Any</p></td>
<td><p>Standard server-to-server communication port for XMPP. Allows communication from the Edge Server XMPP proxy to federated XMPP partners</p></td>
</tr>
<tr class="odd">
<td><p>XMPP/MTLS/TCP/23456</p></td>
<td><p>Any</p></td>
<td><p>Each internal Edge Server Interface IP</p></td>
<td><p>Internal XMPP traffic from the XMPP Gateway on the Front End Server or Front End pool to the Edge Server internal IP address or each Edge pool member’s internal IP address</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

