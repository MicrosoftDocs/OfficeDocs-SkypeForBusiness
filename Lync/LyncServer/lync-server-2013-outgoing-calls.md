---
title: 'Lync Server 2013: Outgoing calls'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Outgoing calls
ms:assetid: 885ffe6f-cd51-4f21-8d4f-a1ff8d818858
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994049(v=OCS.15)
ms:contentKeyID: 51803960
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Outgoing calls in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-09_

The routing of outbound calls of users enabled for Location-Based Routing is affected by the network location of the user’s endpoint. The following table illustrates how Location-Based Routing affects the routing of outbound calls depending on the location of the caller’s endpoint.

### Caller placing an outbound call to the PSTN

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>User endpoint located in a network site enabled for Location-Based Routing</th>
<th>User endpoint located in unknown network site or not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authorization of outbound calls</p></td>
<td><p>Call is authorized based on user’s voice policy</p></td>
<td><p>Call is authorized based on user’s voice policy</p></td>
</tr>
<tr class="even">
<td><p>Routing of outbound call</p></td>
<td><p>Call is routed according to the network site’s voice routing policy</p></td>
<td><p>Call is routed according to user’s voice policy and only through trunks not enabled for Location-Based Routing (if available)</p></td>
</tr>
</tbody>
</table>


<div>

## See Also


[Scenarios for Location-Based Routing in Lync Server 2013](lync-server-2013-scenarios-for-location-based-routing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

