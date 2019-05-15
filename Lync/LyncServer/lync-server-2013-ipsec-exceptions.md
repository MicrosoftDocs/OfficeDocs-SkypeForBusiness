---
title: Lync Server 2013 IPsec exceptions
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: IPsec exceptions
ms:assetid: 241f1eca-6f2f-44de-90b1-2cb659cbe27c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425719(v=OCS.15)
ms:contentKeyID: 48183627
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# IPsec exceptions in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-27_

For enterprise networks where Internet Protocol security (IPsec) (see IETF RFC 4301-4309) has been deployed, IPsec must be disabled over the range of ports used for the delivery of audio, video, and panorama video. The recommendation is motivated by the need to avoid any delay in the allocation of media ports due to IPsec negotiation.

The following table explains the recommended IPsec exception settings.

### Recommended IPsec Exceptions

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Rule name</th>
<th>Source IP</th>
<th>Destination IP</th>
<th>Protocol</th>
<th>Source port</th>
<th>Destination port</th>
<th>Authentication Requirement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A/V Edge Server Internal Inbound</p></td>
<td><p>Any</p></td>
<td><p>A/V Edge Server Internal</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="even">
<td><p>A/V Edge Server External Inbound</p></td>
<td><p>Any</p></td>
<td><p>A/V Edge Server External</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="odd">
<td><p>A/V Edge Server Internal Outbound</p></td>
<td><p>A/V Edge Server Internal</p></td>
<td><p>Any</p></td>
<td><p>UDP &amp; TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="even">
<td><p>A/V Edge Server External Outbound</p></td>
<td><p>A/V Edge Server External</p></td>
<td><p>Any</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="odd">
<td><p>Mediation Server Inbound</p></td>
<td><p>Any</p></td>
<td><p>Mediation</p>
<p>Server(s)</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="even">
<td><p>Mediation Server Outbound</p></td>
<td><p>Mediation</p>
<p>Server(s)</p></td>
<td><p>Any</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="odd">
<td><p>Conferencing Attendant Inbound</p></td>
<td><p>Any</p></td>
<td><p>Front End Server running Conferencing Attendant</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="even">
<td><p>Conferencing Attendant Outbound</p></td>
<td><p>Front End Server running Conferencing Attendant</p></td>
<td><p>Any</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="odd">
<td><p>A/V Conferencing Inbound</p></td>
<td><p>Any</p></td>
<td><p>Front End Servers</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="even">
<td><p>A/V Conferencing Outbound</p></td>
<td><p>Front End Servers</p></td>
<td><p>Any</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="odd">
<td><p>Exchange Inbound</p></td>
<td><p>Any</p></td>
<td><p>Exchange Unified Messaging</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="even">
<td><p>Application Sharing Servers Inbound</p></td>
<td><p>Any</p></td>
<td><p>Application Sharing Servers</p></td>
<td><p>TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="odd">
<td><p>Application Sharing Server Outbound</p></td>
<td><p>Application Sharing Servers</p></td>
<td><p>Any</p></td>
<td><p>TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="even">
<td><p>Exchange Outbound</p></td>
<td><p>Exchange Unified Messaging</p></td>
<td><p>Any</p></td>
<td><p>UDP and TCP</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
<tr class="odd">
<td><p>Clients</p></td>
<td><p>Any</p></td>
<td><p>Any</p></td>
<td><p>UDP</p></td>
<td><p>Specified media port range</p></td>
<td><p>Any</p></td>
<td><p>Do not authenticate</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

