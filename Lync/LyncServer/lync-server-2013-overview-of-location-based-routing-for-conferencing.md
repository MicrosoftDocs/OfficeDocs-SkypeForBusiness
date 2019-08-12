---
title: 'Lync Server 2013: Overview of Location-Based Routing for conferencing'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Overview of Location-Based Routing for conferencing
ms:assetid: 8b86740e-db95-4304-bb83-64d0cbb91d47
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362815(v=OCS.15)
ms:contentKeyID: 56335084
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Overview of Location-Based Routing for conferencing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-19_

The Location-Based Routing Conferencing application provides to Lync Conferences a mechanism for the prevention of PSTN toll bypass. The application monitors active conferences and enforces Location-Based Routing restrictions based on the location of the Lync users participating.

The Location-Based Routing Conferencing application determines whether Location-Based Routing is to be enforced on a Lync meeting if the following criteria are met:

  - The meeting organizer is enabled for Location-Based Routing. Location-Based Routing restrictions will be applied only to conferences that are organized by users who are enabled for Location-Based Routing.

  - At least one meeting participant is a PSTN endpoint. Location-Based Routing restrictions are applicable only for conferences that include PSTN endpoints.

  - The network site where the PSTN gateway used to bridge the conference to the PSTN is located as well as the network sites where the organizers and participants are connecting from.

The Location-Based Routing Conferencing application prevents the participation of Lync users and PSTN endpoints from different network sites to the same conference. If the organizer of a meeting is enabled for Location-Based Routing, the Conferencing application enforces the following restrictions:

  - The endpoints that can join a Lync meeting depend on the endpoints that already joined the conference, and this restriction adjusts as joined endpoints leave and new endpoints join the conference. If organizers and participants are joining a Lync meeting from the same network site, then a PSTN endpoint, another participant from the same network site, another participant from a different network site or a participant from an unknown network site are allowed to join.

  - If organizers and participants are joining the meeting from different or unknown network sites, a PSTN endpoint is not allowed to join the meeting if the PSTN call ingresses from a SIP trunk enabled for Location-Based Routing.

  - If organizers and participants are all joining the meeting from the same network site and there are participants joining the same meeting from the PSTN, a Lync endpoint from a different network site is not allowed to join the meeting.

These conferencing Location-Based Routing restrictions are summarized in the following table.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>User(s) in a conference at any given point</p></td>
<td><p>User(s) allowed to join the conference</p></td>
<td><p>User(s) not allowed to join the conference</p></td>
</tr>
<tr class="even">
<td><p>Lync VoIP client user(s) from a single network site</p></td>
<td><p>Lync VoIP client user from the same network site</p>
<p>Lync VoIP client user from a different network site</p>
<p>Lync VoIP client user from an unknown network site</p>
<p>Federated Lync VoIP client user</p>
<p>User joining from a PSTN endpoint</p></td>
<td><p>None</p></td>
</tr>
<tr class="odd">
<td><p>Lync VoIP client user(s) from an unknown network site</p></td>
<td><p>Lync VoIP client user from any site</p>
<p>Lync VoIP client user from an unknown site</p>
<p>Federated Lync VoIP client user</p></td>
<td><p>User joining via a PSTN endpoint</p></td>
</tr>
<tr class="even">
<td><p>Lync VoIP client users from different network sites</p></td>
<td><p>Lync VoIP client user from any network site</p>
<p>Lync VoIP client user from an unknown network site</p>
<p>Federated Lync VoIP client user</p></td>
<td><p>User joining via a PSTN endpoint</p></td>
</tr>
<tr class="odd">
<td><p>Lync VoIP client user(s) from a single network site and users joining from a PSTN endpoint</p></td>
<td><p>Lync VoIP client user from the same network site</p></td>
<td><p>Lync VoIP client user from a different network site</p>
<p>Lync VoIP client user from an unknown network site</p>
<p>Federated Lync VoIP client user</p></td>
</tr>
</tbody>
</table>


The following are additional characteristics of the Location-Based Routing Conferencing application:

  - When a user is not allowed to join a conference given Location-Based Routing restrictions, the users call to the conference will be rejected and his Lync Client will report that the call was not completed or has ended.

  - A PSTN endpoint joining a conference with Location-Based Routing enforcements will not be restricted to join the conference regardless of its state if the endpoint joins via a trunk that is not enabled for Location-Based Routing.

  - A PBX system connected to a Mediations Server over a SIP trunk that does not egress calls to the PSTN will have the same enforcements as Lync users located in the same network site where the SIP trunk is defined. For example, a PSTN endpoint will be able to join a conference with a PBX user and a Lync user if they are located in the same network site; otherwise, the PSTN endpoint will not be allowed to join the conference if the PBX user is in a different network site than the Lync user.

</div>

<span> </span>

</div>

</div>

</div>

