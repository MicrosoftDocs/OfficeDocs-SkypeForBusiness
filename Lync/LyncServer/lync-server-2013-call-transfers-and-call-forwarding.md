---
title: 'Lync Server 2013: Call transfers and call forwarding'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Call transfers and call forwarding
ms:assetid: 978610ec-63c7-4cf6-ad7a-9ef91559bf12
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994051(v=OCS.15)
ms:contentKeyID: 51803962
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Call transfers and call forwarding in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-09_

When a PSTN endpoint is involved, Location-Based Routing analyzes the location of the calle’s endpoint and the endpoint where the call will be transferred or forwarded to (i.e. transfer/forward target). Location-Based Routing determines whether the call should be transferred or forwarded depending on the location of both endpoints.

The following table illustrates the scenario of a Lync user in a call with a PSTN endpoint, and the Lync user transfers the call to another Lync user. Depending on the network site location of the transferee’s endpoint, Location-Based Routing affects the routing of the call transfer or forward.

### Initiating call transfer or forward

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>User initiating the call transfer/forward</th>
<th>Target endpoint is in same network site as user initiating call transfer or forward</th>
<th>Target endpoint is in different network site as user initiating call transfer or forward</th>
<th>Target endpoint is in unknown network site or network site not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync user</p></td>
<td><p>Call forward or transfer is allowed</p></td>
<td><p>Call forward or transfer is not allowed</p></td>
<td><p>Call forward or transfer is not allowed</p></td>
</tr>
</tbody>
</table>

  

For example: a Lync user in a call with a PSTN endpoint transfers the call to another Lync user that is in the same network site. In this case, the call transfer is allowed.

The following table illustrates the scenario of a Lync user in a call with another Lync user, and one of the users transfers the call to a PSTN endpoint. Depending on the location of the user the call is being transferred to, the table details how Location-Based Routing affects the call.

### Call transfer or forward to PSTN endpoint

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Call transfer/forward endpoint target</th>
<th>Lync users in same network site</th>
<th>Lync users in different network sites</th>
<th>One or both Lync users in unknown network site or network site not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PSTN endpoint</p></td>
<td><p>Call forward or transfer allowed by the transferred user’s site voice routing policy</p></td>
<td><p>Call forward or transfer allowed by the transferred user’s site voice routing policy</p></td>
<td><p>Call forward or transfer allowed by the transferred user’s voice policy only through trunks not enabled for Location-Based Routing</p></td>
</tr>
</tbody>
</table>

  
For example: a Lync user in a call with another Lync user that is in the same network site transfers the call to a PSTN endpoint and the call transfer is allowed.

<div>

## See Also


[Scenarios for Location-Based Routing in Lync Server 2013](lync-server-2013-scenarios-for-location-based-routing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

