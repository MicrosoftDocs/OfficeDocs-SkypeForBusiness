---
title: 'Lync Server 2013: Port summary - Scaled Director pool, hardware load balancer'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Port summary - Scaled Director pool, hardware load balancer
ms:assetid: 6ae2f4ac-5b64-4e45-8253-133308f5812d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204983(v=OCS.15)
ms:contentKeyID: 48184434
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Port summary - Scaled Director pool, hardware load balancer in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-21_

Firewall port requirements for a Director pool consist of the ports that are used to establish communication with the Director from the internal interface of the Edge Server or internal-facing interface of the reverse proxy. Microsoft Lync Server 2013 by default expects ports HTTP/TCP 8080 and HTTPS/TCP 4443 to be open from the reverse proxy to the Director, as well as the Front End pool and Front End Server. Additionally, there must be session initiation protocol (SIP) communication from the Edge Server internal interface to the Director and to the Front End pool and Front End Server. The SIP protocol uses SIP/MTLS/TCP 5061 from the Edge Server to the Front End pool and Front End Server. A rule that allows SIP/MTLS/TCP 5061 communication from the Director, Front End pool and Front End Server to the Edge Server internal interface must be created as well.

### Director Ports and Protocols for Firewall Definitions

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
<td><p>HTTP/TCP 8080</p></td>
<td><p>Reverse proxy internal interface</p></td>
<td><p>Director Hardware Load Balancer VIP</p></td>
<td><p>Initially received by the external side of the reverse proxy, the communication is sent on to the Director HLB VIP and Front End Servers web services</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP 4443</p></td>
<td><p>Reverse proxy internal interface</p></td>
<td><p>Director Hardware Load Balancer VIP</p></td>
<td><p>Initially received by the external side of the reverse proxy, the communication is sent on to the Director HLB VIP and Front End Servers web services</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP 444</p></td>
<td><p>Director</p></td>
<td><p>Front End Server or Front End pool</p></td>
<td><p>Inter-server communication between the Director HLB VIP and the Front End Servers</p></td>
</tr>
<tr class="even">
<td><p>HTTP/TCP 80</p></td>
<td><p>Internal Clients</p></td>
<td><p>Director Hardware Load Balancer VIP</p></td>
<td><p>The Director provides web services to internal as well as external clients.</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP 443</p></td>
<td><p>Internal Clients</p></td>
<td><p>Director Hardware Load Balancer VIP</p></td>
<td><p>The Director provides web services to internal as well as external clients.</p></td>
</tr>
<tr class="even">
<td><p>SIP/MTLS/TCP 5061</p></td>
<td><p>Edge Server internal interface</p></td>
<td><p>Director Hardware Load Balancer VIP</p></td>
<td><p>SIP communication from the Edge Server to the Director, and Front End Servers.</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50001</p></td>
<td><p>Any</p></td>
<td><p>Director</p></td>
<td><p>Centralized Logging Service controller (ClsController.exe) or agent (ClsAgent.exe)commands and log collection</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50002</p></td>
<td><p>Any</p></td>
<td><p>Director</p></td>
<td><p>Centralized Logging Service controller (ClsController.exe) or agent (ClsAgent.exe)commands and log collection</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50003</p></td>
<td><p>Any</p></td>
<td><p>Director</p></td>
<td><p>Centralized Logging Service controller (ClsController.exe) or agent (ClsAgent.exe)commands and log collection</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

