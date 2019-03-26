---
title: 'Lync Server 2013: Incoming calls'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Incoming calls
ms:assetid: 65b9c1b4-6af7-4527-8c33-22c4442bd209
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994038(v=OCS.15)
ms:contentKeyID: 51803948
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Incoming calls in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-09_

The routing of incoming calls to users enabled for Location-Based Routing depends on the location of the user’s endpoint. The routing of incoming calls is affected in the following way. If a user has an incoming call to an endpoint located in a Location-Based Routing enabled network site, and the endpoint is located in the same network site as the PSTN gateway, the call will be routed. If a user has an incoming call to an endpoint located in a Location-Based Routing enabled network site, and the endpoint is located in a different network site than the PSTN gateway, the call will not be routed. When a user has no endpoints located in the same network site as the PSTN gateway where the incoming call is originating from, the incoming call will be routed directly to the user’s voicemail and a missed call notification will be sent to the called party.

The call forwarding settings of a user that is enabled for Location-Based Routing will continue to be enforced, however, calls forwarded will be subject to Location-Based Routing restrictions of the user.

The following table illustrates how Location-Based Routing affects the routing of inbound calls depending on the location of the callee’s endpoint. The network site of the PSTN gateway is enabled for Location-Based Routing, and Location-Based Routing only permits routing of PSTN calls to endpoints within the same network site.

### Callee receiving an inbound call from the PSTN

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Callee’s endpoint located in the same network site as PSTN gateway</th>
<th>Callee’s endpoint not located in the same network site as PSTN gateway</th>
<th>Callee’s endpoint located in unknown network site or not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Routing of inbound PSTN call</p></td>
<td><p>Incoming call is routed to callee’s endpoints</p></td>
<td><p>Incoming call is not routed to callee’s endpoints</p></td>
<td><p>Incoming call is not routed to callee’s endpoints</p></td>
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

