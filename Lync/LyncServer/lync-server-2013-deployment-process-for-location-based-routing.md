---
title: 'Lync Server 2013: Deployment process for Location-Based Routing'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deployment process for Location-Based Routing
ms:assetid: 9e923e72-83fc-4a4f-8937-28a55739ed3e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994055(v=OCS.15)
ms:contentKeyID: 51803966
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment process for Location-Based Routing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-09_

This topic provides an overview of the process involved in configuring Location-Based Routing. You must deploy Lync Server Enterprise Edition or Standard Edition with Enterprise Voice before you configure Location-Based Routing. The components required by Location-Based Routing are already installed and enabled when you deploy Enterprise Voice.

### Location-Based Routing Deployment Process

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Phase</th>
<th>Steps</th>
<th>Required groups and roles</th>
<th>Deployment documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Deploy Enterprise Voice</p></td>
<td><ul>
<li><p>Configure Trunks</p></li>
<li><p>Create Voice Policies</p></li>
<li><p>Define Voice Routes</p></li>
</ul></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td><p>Deploying Enterprise Voice</p></td>
</tr>
<tr class="even">
<td><p>Verify your Enterprise Voice deployment</p></td>
<td></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Configure network regions, sites, and subnets</p></td>
<td><ul>
<li><p>Create network regions</p></li>
<li><p>Create network sites</p></li>
<li><p>Associates subnets with network sites</p></li>
</ul></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td><p>About Network Regions, Sites, and Subnets<br />
Create or Modify a Network Region<br />
Create or Modify a Network Site<br />
Associate a Subnet with a Network Site</p></td>
</tr>
<tr class="even">
<td><p>Configure Location-Based Routing</p></td>
<td><ul>
<li><p>Create voice routing policies</p></li>
<li><p>Define separate trunk configuration per trunk</p></li>
<li><p>Modify voice policies</p></li>
<li><p>Enable Location-Based Routing configuration</p></li>
</ul></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td></td>
</tr>
</tbody>
</table>


<div>

## Sample Deployment

The following deployment is used to illustrate further the mechanisms enabled by Location-Based Routing.

![e1bd2230-44da-4784-b359-24572b6ce02d](images/JJ994055.e1bd2230-44da-4784-b359-24572b6ce02d(OCS.15).png "e1bd2230-44da-4784-b359-24572b6ce02d")

<div>

## Incoming PSTN calls

An administrator can enable the trunk defined to route calls to “Site 1 Gateway” for Location-Based Routing and associate the “Site 1 Gateway” to site 1. Once enabled, calls that are routed through “Site 1 Gateway“ will only be routed to users that are located in site 1. All calls routed through the “Site 1 Gateway” trunk destined to users in a different site, such as site 2 will be blocked to prevent PSTN toll bypass.

All incoming PSTN calls through “Site 1 Gateway” will only be allowed to route to endpoints located in site 1. For example, when “Lync user 1” travels to site 2, all incoming PSTN calls through “Site 1 Gateway” will not be routed to “Lync user 1” endpoints located in site 2. The same routing rule applies if “Lync user 1” travels to an unknown network site where the user’s location can’t be determined.

The following table outlines the user experience of “Lync user 1” in this context.


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
<th>Lync user 1 endpoints located in network site 1</th>
<th>Lync user 1 endpoints located in network site 2</th>
<th>Lync user 1 endpoints located in unknown network site</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Inbound PSTN calls to Lync user 1</p></td>
<td><p>Calls are routed to endpoints in this location</p></td>
<td><p>Calls are not routed to endpoints in this location</p></td>
<td><p>Calls are not routed to endpoints in this location</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Outgoing PSTN calls

Voice routes are referenced in both Voice Policies assigned directly to users, and Voice Routing Policies assigned to network sites. Both policies contain references to routes, which can be used to route a call differently. For example, an administrator can define a Voice Routing Policy for all users located in network site 1 to route all outbound calls through the “Site 1 Gateway” while the Voice Policy of some users define a route for all outbound calls through the “Site 2 Gateway”. While these users are located in network site 1, their outbound calls will be routed through the “Site 1 Gateway”.

When a user is located in a network site configured for Location-Based Routing, the network site’s Voice Routing Policy route overrides the user’s Voice Policy route. This rule is particularly useful for users that temporarily move to a different site. In this particular case a user will always use a gateway that is local to his location; if “Lync user 3” is located at “Site 2”, all his outbound calls will be routed via “Site 2 Gateway”, but if he travels to site 1, all his outbound calls placed while he’s at site 1 will be routed through “Site 1 Gateway”.

The following table illustrates the user experience of Lync user 1 placing an outbound call from the following network sites.


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
<th>Network site 1</th>
<th>Network site 2</th>
<th>Unknown network site or not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authorization of outbound calls</p></td>
<td><p>Lync user 1 voice policy</p></td>
<td><p>Lync user 1 voice policy</p></td>
<td><p>Lync user 1 voice policy</p></td>
</tr>
<tr class="even">
<td><p>Routing of outbound calls</p></td>
<td><p>Site 1 voice routing policy</p></td>
<td><p>Site 2 voice routing policy</p></td>
<td><p>User’s voice policy and only to systems not enabled for Location-Based Routing</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Call transfers and forwards

When calls are transferred or forwarded, the routing of calls is affected by Location-Based Routing.

The following table depicts Lync user 1 transferring or forwarding a PSTN call to another Lync user.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>User initiating call transfer or forward</th>
<th>Lync user 2</th>
<th>Lync user 4</th>
<th>Lync user in network site not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync user 1</p></td>
<td><p>Call forward or transfer is allowed</p></td>
<td><p>Call forward or transfer is not allowed</p></td>
<td><p>Call forward or transfer is not allowed</p></td>
</tr>
</tbody>
</table>

  
The following table illustrates how Location-Based Routing affects how the call is routed based on the location of the Lync user being transferred (Lync user 2, Lync user 4, etc) to a PSTN endpoint


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Endpoint where call is transferred or forwarded to</th>
<th>Lync user 2</th>
<th>Lync user 4</th>
<th>Lync user in network site not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PSTN endpoint</p></td>
<td><p>Call forward or transfer is routed through site 1 voice routing policy and egress via Site 1 Gateway</p></td>
<td><p>Call forward or transfer is routed through site 2 voice routing policy and egress via Site 2 Gateway</p></td>
<td><p>Call forward or transfer is routed through the Lync user voice policy and egress via a gateway not enabled for location-based routing (if available)</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Simultaneous ringing

Once location-based routing is configured in the sample topology, the following interactions are enforced.

The following table illustrates whether Location-Based Routing allows simultaneous ringing for different Lync users (i.e. Lync user 2, Lync user 4, etc).


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Incoming PSTN call target</th>
<th>Lync user 2</th>
<th>Lync user 4</th>
<th>Lync user in network site not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync user 1</p></td>
<td><p>Simultaneous ring is allowed</p></td>
<td><p>Simultaneous ring is not allowed</p></td>
<td><p>Simultaneous ring is not allowed</p></td>
</tr>
</tbody>
</table>

  
The following table illustrates whether Location-Based Routing allows simultaneous ringing to a PSTN endpoint from different Lync users (i.e. Lync user 2, Lync user 4, etc).


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
<th>Lync user 2</th>
<th>Lync user 4</th>
<th>Lync user in network site not enabled for Location-Based Routing</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync user 1 mobile phone (PSTN endpoint)</p></td>
<td><p>Call routed through network site 1’s voice routing policy and egress via site 1 gateway</p></td>
<td><p>Call routed through network site 2’s voice routing policy and egress via site 2 gateway</p></td>
<td><p>Call routed through the caller voice policy and will egress via a PSTN gateway not enabled for Location-Based Routing</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<div>

## See Also


[Planning for Location-Based Routing in Lync Server 2013](lync-server-2013-planning-for-location-based-routing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

