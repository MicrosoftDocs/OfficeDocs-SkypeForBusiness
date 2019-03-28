---
title: 'Lync Server 2013: Client and server support for Location-Based Routing'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Client and server support for Location-Based Routing
ms:assetid: 26c2ca3d-026d-4dd7-94fa-15ebb4406953
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994024(v=OCS.15)
ms:contentKeyID: 51803933
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Client and server support for Location-Based Routing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-06-18_

Location-Based Routing is enforced by Lync Server. Lync Server can identify the network sites where users are connecting from within the corporate network. Since remote users are outside the corporate network, their location is considered to be unknown.

<div>

## Lync Server Support

Location-Based Routing requires that Lync Server 2013 CU1 is deployed on all Front End pools and Standard Edition servers in a given topology. If Lync Server 2013 CU1 is not installed on certain Lync components in the topology, Location-Based Routing restrictions cannot be fully enforced.

The following table identifies the combination of server roles and versions that is supported for Location-Based Routing.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Pool version</th>
<th>Mediation Server version</th>
<th>Supported</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 2013 February 2013 Cumulative Update</p></td>
<td><p>Lync Server 2013 February 2013 Cumulative Update</p></td>
<td><p>yes</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 February 2013 Cumulative Update</p></td>
<td><p>Lync Server 2013</p></td>
<td><p>no</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013 February 2013 Cumulative Update</p></td>
<td><p>Lync Server 2010</p></td>
<td><p>no</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 February 2013 Cumulative Update</p></td>
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>no</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013</p></td>
<td><p>any</p></td>
<td><p>no</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2010</p></td>
<td><p>any</p></td>
<td><p>no</p></td>
</tr>
<tr class="odd">
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>any</p></td>
<td><p>no</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Lync Client Support

The following table identifies the clients that Location-Based Routing supports.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Client type</th>
<th>Supported</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>yes</p></td>
<td><p>Including Lync 2013 February 2013 Cumulative Update</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010</p></td>
<td><p>yes</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>no</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>Lync Phone Edition</p></td>
<td><p>yes</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Lync Attendant</p></td>
<td><p>yes</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>Lync for Windows 8</p></td>
<td><p>no</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Lync Mobile 2013</p></td>
<td><p>no</p></td>
<td><p>VoIP must be disabled for Lync Mobile 2013 clients if used by users with Location-Based Routing enabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync Mobile 2010</p></td>
<td><p>yes</p></td>
<td> </td>
</tr>
</tbody>
</table>

  

<div>


> [!NOTE]  
> To disable VoIP for Lync Mobile 2013 clients, assign a mobility policy with the setting, IP Audio/Video, disabled for all users enabled for Location Based Routing. For more details about mobility policy, see <A href="https://docs.microsoft.com/powershell/module/skype/New-CsMobilityPolicy">New-CsMobilityPolicy</A>.



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

