---
title: 'Lync Server 2013: Changes made by domain preparation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Changes made by domain preparation
ms:assetid: 9191221e-6166-4c2b-837e-fa73d90fdf80
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398742(v=OCS.15)
ms:contentKeyID: 48184845
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Changes made by domain preparation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2010-10-18_

The following table lists the access control entries (ACEs) that domain preparation creates on the domain root. All ACEs are inherited unless otherwise noted.

<div id="sectionSection0" class="section">

### ACEs Added to Domain Root

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>ACE</th>
<th>RTCUniversal-UserReadOnly-Group</th>
<th>RTCUniversal-ServerReadOnly-Group</th>
<th>RTCUniversal-UserAdmins</th>
<th>RTCHSUniversal-Services</th>
<th>Authenticated-Users</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Read Container (not inherited)</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Read User PropertySet User-Account-Restrictions</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Read User PropertySet Personal-Information</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Read User PropertySet General-Information</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Read User PropertySet Public-Information</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Read User PropertySet RTCUserSearchProperty-Set</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
</tr>
<tr class="odd">
<td><p>Read User PropertySet RTCPropertySet</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Write User Property Proxy-Addresses</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Write User PropertySet RTCUserSearchProperty-Set</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Write User PropertySet RTCPropertySet</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Read PropertySet DS-Replication-Get-Changes of all Active Directory objects</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
</tr>
</tbody>
</table>


The following table lists the ACEs that domain preparation creates in the three built-in containers: Users, Computers, and Domain Controllers. All ACEs are inherited unless otherwise noted.

### ACEs Added to Built-in Containers

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>ACE</th>
<th>RTCUniversal-UserReadOnly-Group</th>
<th>RTCUniversal-ServerReadOnly-Group</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Read Container (not inherited)</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p><strong>Yes</strong></p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

