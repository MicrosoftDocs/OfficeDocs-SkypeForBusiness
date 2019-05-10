---
title: 'Lync Server 2013: Configuring Enterprise Voice'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring Enterprise Voice
ms:assetid: 7df179fa-d3a2-4b23-a433-b750aedf980b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994041(v=OCS.15)
ms:contentKeyID: 51803952
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Enterprise Voice in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-12_

To deploy Enterprise Voice, you’ll need to configure the following:

  - Create a Trunk

  - Define a Voice Policy

  - Define a Voice Route

  - Enable Users for Enterprise Voice

<div>

## Create a Trunk

You must define trunks in your Enterprise Voice deployment. For Location-Based Routing, you must create a trunk configuration per trunk. Use the Lync Server Topology Builder to define your trunks, and use the Lync Server Windows PowerShell command, New-CsTrunkConfiguration, or the Lync Server Control Panel to define the corresponding trunk configurations. More information on how to enable Location-Based Routing on trunk configurations can be found in the section, Enable Location-Based Routing to Trunks, in the topic, [Enabling Location-Based Routing in Lync Server 2013](lync-server-2013-enabling-location-based-routing.md). For this example, the following table illustrates the trunks used in this scenario.

For more information, see [Define additional trunks in Topology Builder in Lync Server 2013](lync-server-2013-define-additional-trunks-in-topology-builder.md).


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Trunk name</th>
<th>System type</th>
<th>Name</th>
<th>Location</th>
<th>Mediation Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Trunk 1 DEL-GW</p></td>
<td><p>PSTN gateway</p></td>
<td><p>DEL-GW</p></td>
<td><p>Delhi</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="even">
<td><p>Trunk 2 HYD-GW</p></td>
<td><p>PSTN gateway</p></td>
<td><p>HYD-GW</p></td>
<td><p>Hyderabad</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="odd">
<td><p>Trunk 3 DEL-PBX</p></td>
<td><p>PBX</p></td>
<td><p>DEL-PBX</p></td>
<td><p>Delhi</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="even">
<td><p>Trunk 4 HYD-PBX</p></td>
<td><p>PBX</p></td>
<td><p>HYD-PBX</p></td>
<td><p>Hyderabad</p></td>
<td><p>MS1</p></td>
</tr>
</tbody>
</table>


<div>


</div>

</div>

<div>

## Defines Voice Policies

You must define voice policies for your Enterprise Voice deployment. Define a Voice Policy to enforce Location-Based Routing restrictions to a subset of users if only a subset of them is required to use Location-Based Routing. For this example, the following table illustrates the voice policies used in this scenario. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.

For more information, see [Configuring voice policies and PSTN usage records to authorize calling features and privileges in Lync Server 2013](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Voice policy 1</th>
<th>Voice policy 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Voice policy ID</p></td>
<td><p>Delhi voice policy</p></td>
<td><p>Hyderabad voice policy</p></td>
</tr>
<tr class="even">
<td><p>PSTN usages</p></td>
<td><p>Delhi usage, PBX Del usage, PBX Hyd usage</p></td>
<td><p>Hyderabad usage, PBX Hyd usage, PBX Del usage</p></td>
</tr>
<tr class="odd">
<td><p>PreventPSTNTollBypass</p></td>
<td><p>False</p></td>
<td><p>False</p></td>
</tr>
</tbody>
</table>


<div>


</div>

</div>

<div>

## Define Voice Routes

You must define voice routes for your Enterprise Voice deployment. For this example, the following table illustrates the voice routes used in this scenario. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.

For more information, see [Configuring voice routes for outbound calls in Lync Server 2013](lync-server-2013-configuring-voice-routes-for-outbound-calls.md).


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Voice route 1</th>
<th>Voice route 2</th>
<th>Voice route 3</th>
<th>Voice route 4</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>Delhi route</p></td>
<td><p>Hyderabad route</p></td>
<td><p>PBX Del route</p></td>
<td><p>PBX Hyd route</p></td>
</tr>
<tr class="even">
<td><p>PSTN usages</p></td>
<td><p>Delhi usage</p></td>
<td><p>Hyderabad usage</p></td>
<td><p>PBX Del usage</p></td>
<td><p>PBX Hyd usage</p></td>
</tr>
<tr class="odd">
<td><p>Trunk</p></td>
<td><p>Trunk 1 DEL-GW</p></td>
<td><p>Trunk 2 HYD-GW</p></td>
<td><p>Trunk 3 DEL-PBX</p></td>
<td><p>Trunk 4 HYD-PBX</p></td>
</tr>
</tbody>
</table>


<div>


</div>

</div>

<div>

## Enable Users for Enterprise Voice

Enable users for Enterprise Voice and assign them a voice policy you’ve previously defined. For this example, the following table illustrates the assignment used in this scenario. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.

For more information, see [Enable users for Enterprise Voice in Lync Server 2013](lync-server-2013-enable-users-for-enterprise-voice.md).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Users located in Delhi</th>
<th>Users located in Hyderabad</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Associated voice policy</p></td>
<td><p>Delhi voice policy</p></td>
<td><p>Hyderabad voice policy</p></td>
</tr>
<tr class="even">
<td><p>Sample users</p></td>
<td><p>DEL-LYNC-1,DEL-LYNC-2,DEL-LYNC-3</p></td>
<td><p>HYD-LYNC-1, HYD-LYNC-2, HYD-LYNC-3</p></td>
</tr>
</tbody>
</table>


<div>


</div>

</div>

<div>

## See Also


[Configuring Location-Based Routing in Lync Server 2013](lync-server-2013-configuring-location-based-routing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

