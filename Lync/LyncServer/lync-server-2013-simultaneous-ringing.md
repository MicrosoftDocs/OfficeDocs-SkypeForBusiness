---
title: 'Lync Server 2013: Simultaneous ringing'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Simultaneous ringing
ms:assetid: df02f919-4d50-4832-9300-6c51f8b4fc56
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994079(v=OCS.15)
ms:contentKeyID: 51803990
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Simultaneous ringing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-09_

When the called party has simultaneous ringing enabled, Location-Based Routing analyzes the location of the calling party and the endpoints of the called parties to determine whether the call should be routed.

The following table illustrates a user configured with simultaneous ringing, and the simultaneous ringing target is a user in the same network site, in a different network site, or in an unknown network site.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Incoming PSTN call for</th>
<th>Located in the same network site as callee</th>
<th>Located in different network site than callee</th>
<th>Located in unknown network site or not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync user</p></td>
<td><p>Simultaneous ring allowed</p></td>
<td><p>Simultaneous ring not allowed</p></td>
<td><p>Simultaneous ring not allowed</p></td>
</tr>
</tbody>
</table>

  
The following table illustrates a call from a Lync user (i.e. Lync caller) in the same network site, in a different network site, or from an unknown network site. The callee has a PSTN endpoint (i.e. cellphone) configured as a simultaneous ring target. In this scenario, Location-Based Routing will determine whether the call should be routed to the simultaneous ring target (i.e. cellphone) of the callee or not.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Simultaneous ring target</th>
<th>Located in the same network site as callee</th>
<th>Located in different network site than callee</th>
<th>Located in unknown network site or not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PSTN endpoint</p></td>
<td><p>Simultaneous ring allowed through the caller’s site voice routing policy</p></td>
<td><p>Simultaneous ring allowed through the caller’s site voice routing policy</p></td>
<td><p>Simultaneous ring allowed through the caller’s voice policy to trunks not enabled for Location-Based Routing</p></td>
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

