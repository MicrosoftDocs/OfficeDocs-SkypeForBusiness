---
title: 'Lync Server 2013: Planning outbound voice routing'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Planning outbound voice routing
ms:assetid: 37c55fa4-175a-4190-b9e4-c2e5ac7b9261
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425853(v=OCS.15)
ms:contentKeyID: 48183835
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning outbound voice routing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

Outbound call routing applies to calls that are destined for a public switched telephone network (PSTN) gateway, trunk, or private branch exchange (PBX). When a user places a call, the server normalizes the phone number to E.164 format, if necessary, and attempts to match it to a SIP URI. If the server cannot make the match, it applies outbound call routing logic based on the supplied dial string. You define that logic by configuring the server settings that are described in the following table.

### Lync Server Outbound Call Routing Settings

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Object</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dial Plan</p></td>
<td><p>A dial plan is a named set of normalization rules that translates phone numbers for a named location, individual user, or contact object into a single standard (E.164) format for purposes of phone authorization and call routing.</p></td>
</tr>
<tr class="even">
<td><p>Normalization rule</p></td>
<td><p>Normalization rules define how phone numbers expressed in various formats are to be routed for each specified location, user, or contact object. The same dial string may be interpreted and translated differently, depending on the location from which it is dialed and the person or contact object that makes the call. A set of normalization rules associated with a particular location constitutes a dial plan.</p></td>
</tr>
<tr class="odd">
<td><p>Voice policy</p></td>
<td><p>A voice policy associates one or more PSTN usage records with one user or a group of users. A voice policy also provides a list of calling features that you can enable or disable.</p></td>
</tr>
<tr class="even">
<td><p>PSTN usage record</p></td>
<td><p>A PSTN usage record specifies a class of call (such as internal, local, or long distance) that can be made by various users, or groups of users, in an organization.</p></td>
</tr>
<tr class="odd">
<td><p>Call Route</p></td>
<td><p>A call route associates destination phone numbers with particular trunks and PSTN usage records. A PSTN gateway is considered a trunk.</p></td>
</tr>
</tbody>
</table>


<div>

## In This Section

This section provides guidelines for configuring the following outbound call routing server settings:

  - <span></span>  
    [Dial plans and normalization rules in Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md)

  - <span></span>  
    [Voice policies in Lync Server 2013](lync-server-2013-voice-policies.md)

  - <span></span>  
    [PSTN usage records in Lync Server 2013](lync-server-2013-pstn-usage-records.md)

  - <span></span>  
    [Voice routes in Lync Server 2013](lync-server-2013-voice-routes.md)

</div>

<div>

## See Also


[SIP trunking in Lync Server 2013](lync-server-2013-sip-trunking.md)  
[Direct SIP connections in Lync Server 2013](lync-server-2013-direct-sip-connections.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

