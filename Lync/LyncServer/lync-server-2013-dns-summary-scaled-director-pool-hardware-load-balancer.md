---
title: 'Lync Server 2013: DNS summary - Scaled Director pool, hardware load balancer'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: DNS summary - Scaled Director pool, hardware load balancer
ms:assetid: 08ba48e6-bfa1-4ab0-bc89-d58ddb9c20af
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204655(v=OCS.15)
ms:contentKeyID: 48183340
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS summary - Scaled Director pool, hardware load balancer in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-20_

The following table contains a summary of the DNS records that are required to support the hardware load balanced Director. The role of the Director requires similar DNS records as the Front End Server. The number of records needed is reflected in the subject alternative names required on the Director certificate. Different from the Front End Server, the Director pool does not host user accounts or host the Mobility Services.

### DNS Records Required for the Director pool using a Hardware Load Balancer and DNS Load Balancing

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Location/TYPE/Port</th>
<th>FQDN/DNS Record</th>
<th>IP Address/FQDN</th>
<th>Maps to/Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Internal DNS/A</p></td>
<td><p>dir01.contoso.net</p></td>
<td><p>Director</p></td>
<td><p>Director host record used for replication and server to server communication</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS/A</p></td>
<td><p>dirpool01.contoso.net</p></td>
<td><p>Director pool HLB VIP</p></td>
<td><p>Host record for the DNS load balanced Director pool</p></td>
</tr>
<tr class="odd">
<td><p>Internal DNS/A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Director pool HLB VIP</p></td>
<td><p>Inbound session initiation protocol (SIP) from the internal interface of the Edge Server</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS/A</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>Director pool HLB VIP</p></td>
<td><p>Hardware load balanced published dialin web services from reverse proxy</p></td>
</tr>
<tr class="odd">
<td><p>Internal DNS/A</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>Director pool HLB VIP</p></td>
<td><p>Hardware load balanced published meet web services from reverse proxy</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS/A</p></td>
<td><p>webdirexternal.contoso.com</p></td>
<td><p>Director pool HLB VIP</p></td>
<td><p>Hardware load balanced published and defined by the reverse proxy Web Ticket external web services for the Director pool</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

