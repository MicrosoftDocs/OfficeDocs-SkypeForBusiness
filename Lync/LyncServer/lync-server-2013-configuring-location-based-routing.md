---
title: 'Lync Server 2013: Configuring Location-Based Routing'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring Location-Based Routing
ms:assetid: 63cdc474-e80f-43b1-a237-9d9ed673300a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994036(v=OCS.15)
ms:contentKeyID: 51803946
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Location-Based Routing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-12_

Lync Server 2013 CU1, Location-Based Routing is a feature of Enterprise Voice. Location-Based Routing is a call management feature that controls how calls are routed by Lync Server 2013 CU1. It enforces restrictions on whether calls can be routed to PBX or PSTN destinations based on the Lync caller’s location. Location-Based Routing applies call authorization rules to PSTN calls based on the caller’s network location. The caller’s location is determined based on the network site associated with the network subnet the caller is connected on. Configuring Location-Based Routing requires first deploying Enterprise Voice, then configuring network regions, sites and subnets. This sets up the foundation for enabling Location-Based Routing.

Before deploying Location-Based Routing, you must first deploy Enterprise Voice, and configure network regions, sites, and associate network subnets to your network sites. Once completed, you can configure Location-Based Routing. For steps on how to configure network regions, sites and subnets, see [Deploying advanced Enterprise Voice features in Lync Server 2013](lync-server-2013-deploying-advanced-enterprise-voice-features.md)

This section guides you through the configuration of Location-Based Routing using the following example as illustration.

![Enterprise Voice location-based routing example](images/JJ994036.b6ef5afc-36ac-406f-8ec2-a87532b20612(OCS.15).png "Enterprise Voice location-based routing example")

  
The following table represents the users defined in this example.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Endpoint type</th>
<th>Location</th>
<th>Users</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync</p></td>
<td><p>Delhi corporate office</p></td>
<td><p>DEL-LYNC-1,DEL-LYNC-2,DEL-LYNC-3</p></td>
</tr>
<tr class="even">
<td><p>Lync</p></td>
<td><p>Hyderabad corporate office</p></td>
<td><p>HYD-LYNC-1, HYD-LYNC-2, HYD-LYNC-3</p></td>
</tr>
<tr class="odd">
<td><p>Lync</p></td>
<td><p>Unknown (i.e. hotel)</p></td>
<td><p>UNK-LYNC-1</p></td>
</tr>
<tr class="even">
<td><p>PBX</p></td>
<td><p>Delhi corporate office</p></td>
<td><p>DEL-PBX-1, DEL-PBX-2</p></td>
</tr>
<tr class="odd">
<td><p>PBX</p></td>
<td><p>Hyderabad corporate office</p></td>
<td><p>HYD-PBX-1, HYD-PBX-2</p></td>
</tr>
<tr class="even">
<td><p>PSTN</p></td>
<td><p>Unknown</p></td>
<td><p>PSTN-1, PSTN-2, PSTN-3</p></td>
</tr>
</tbody>
</table>

  

The following table represents the systems illustrated in this example environment.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>System</th>
<th>Location</th>
<th>Name</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 2013 CU1 pool</p></td>
<td><p>any</p></td>
<td><p>LS-PL1</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 CU1, Mediation Server</p></td>
<td><p>any</p></td>
<td><p>MS-PL1</p></td>
</tr>
<tr class="odd">
<td><p>PSTN gateway 1</p></td>
<td><p>Delhi</p></td>
<td><p>DEL-GW</p></td>
</tr>
<tr class="even">
<td><p>PSTN gateway 2</p></td>
<td><p>Hyderabad</p></td>
<td><p>HYD-GW</p></td>
</tr>
<tr class="odd">
<td><p>PBX 1</p></td>
<td><p>Delhi</p></td>
<td><p>DEL-PBX</p></td>
</tr>
<tr class="even">
<td><p>PBX 2</p></td>
<td><p>Hyderabad</p></td>
<td><p>RED-PBX</p></td>
</tr>
</tbody>
</table>


<div>

## In This Section

  - [Configuring Enterprise Voice in Lync Server 2013](lync-server-2013-configuring-enterprise-voice.md)

  - [Deploying network regions, sites, and subnets in Lync Server 2013](lync-server-2013-deploying-network-regions-sites-and-subnets.md)

  - [Enabling Location-Based Routing in Lync Server 2013](lync-server-2013-enabling-location-based-routing.md)

</div>

<div>

## See Also


[Deploying advanced Enterprise Voice features in Lync Server 2013](lync-server-2013-deploying-advanced-enterprise-voice-features.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

