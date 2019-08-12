---
title: 'Lync Server 2013: Location-Based Routing and consultative call transfers'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Location-Based Routing and consultative call transfers
ms:assetid: b12460c2-36c8-481f-b867-fe10dc1c0bdf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362836(v=OCS.15)
ms:contentKeyID: 56335089
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Location-Based Routing and consultative call transfers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-31_

In addition to enforcing Location-Based Routing to Lync meetings, the Location-Based Routing Conferencing application enforces Location-Based Routing restrictions on consultative call transfers that egress to PSTN endpoints. A consultative call transfer is a call established between two parties where one of the parties transfers the call to a new user. For example, a PSTN endpoint calls user A (Lync callee). User A determines the PSTN user should be forwarded to user B (Lync user). User A places the call with the PSTN user on hold, and calls user B. User B agrees to talk to the PSTN user. User A transfers the call on-hold to user B.

**Consultative call transfer call flow**

![Location-based routing for conferencing diagram](images/Dn362836.e4d43d6f-23d2-49c9-b12b-15248a743f92(OCS.15).jpg "Location-based routing for conferencing diagram")

When a user enabled for Location-Based Routing initiates a consultative call transfer of a PSTN endpoint (as shown in the preceding figure), this creates two active calls, one call between the PSTN user and Lync user A, and the other between Lync user A and Lync user B. the following behavior is enforced by the Location-Based Routing Conferencing application:

  - If the SIP trunk routing the PSTN call is authorized to re-route the PSTN call to the network site where Lync user B (i.e. transfer target) is located,, then the call transfer will be allowed; otherwise, the consultative call transfer will be blocked. This authorization is performed based on the transferred party’s location being in the same network site as the SIP trunk that is routing the active call to the PSTN endpoint.

  - If the SIP trunk routing the inbound PSTN call is not authorized to route calls to the network site where the transferred party (Lync user B) is located or the transferred party is located in an unknown network site, then the consultative call transfer to the PSTN endpoint (i.e. call transfer target) will be blocked.

The following table describes how Location-Based Routing restrictions are applied by the Location-Based Routing Conferencing application for consultative call transfers. Although PBX endpoints are not directly associated with a network site, the SIP trunk the PBX is connected to can be assigned a network site. Therefore, the PBX endpoint can be indirectly associated with a network site.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Network site of call transferred party</p></td>
<td><p>Network site of call transfer target</p></td>
<td><p>Behavior</p></td>
</tr>
<tr class="even">
<td><p>PSTN endpoint</p></td>
<td><p>Lync user in the same network site (i.e. site 1)</p></td>
<td><p>Consultative transfer will be allowed</p></td>
</tr>
<tr class="odd">
<td><p>PSTN endpoint</p></td>
<td><p>Lync user in different network sites (i.e. site 2)</p></td>
<td><p>Consultative transfer will be disallowed</p></td>
</tr>
<tr class="even">
<td><p>PSTN endpoint</p></td>
<td><p>Lync user in an unknown network site</p></td>
<td><p>Consultative transfer will be disallowed</p></td>
</tr>
<tr class="odd">
<td><p>PSTN endpoint</p></td>
<td><p>Federated Lync user</p></td>
<td><p>Consultative transfer will be disallowed</p></td>
</tr>
<tr class="even">
<td><p>PSTN endpoint</p></td>
<td><p>PBX endpoint in the same site (i.e. site 1)</p></td>
<td><p>Consultative transfer will be allowed</p></td>
</tr>
<tr class="odd">
<td><p>PSTN endpoint</p></td>
<td><p>PBX endpoint in a different sites (i.e. site 2)</p></td>
<td><p>Consultative transfer will be disallowed</p></td>
</tr>
<tr class="even">
<td><p>PBX endpoint in the same site (i.e. site 1)</p></td>
<td><p>PSTN endpoint</p></td>
<td><p>Consultative transfer will be allowed</p></td>
</tr>
<tr class="odd">
<td><p>PBX endpoint in a different site (i.e. site 2)</p></td>
<td><p>PSTN endpoint</p></td>
<td><p>Consultative transfer will be disallowed</p></td>
</tr>
<tr class="even">
<td><p>PBX endpoint in any site</p></td>
<td><p>Lync user in the same network site (i.e. site 1)</p></td>
<td><p>Consultative transfer will be allowed</p></td>
</tr>
<tr class="odd">
<td><p>PBX endpoint in any site</p></td>
<td><p>Lync user in different network sites (i.e. site 2)</p></td>
<td><p>Consultative transfer will be allowed</p></td>
</tr>
<tr class="even">
<td><p>PBX endpoint in any site</p></td>
<td><p>Lync user in an unknown network site</p></td>
<td><p>Consultative transfer will be allowed</p></td>
</tr>
<tr class="odd">
<td><p>PBX endpoint in any site</p></td>
<td><p>Federated Lync user</p></td>
<td><p>Consultative transfer will be allowed</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

