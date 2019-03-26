---
title: 'Lync Server 2013: tblRoleType'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: tblRoleType
ms:assetid: 1eac3a54-656a-40ac-b771-edfc64d6e34b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558623(v=OCS.15)
ms:contentKeyID: 48183577
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# tblRoleType in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-25_

tblRoleType is a static lookup table with role types and their associated permission sets.

### Columns

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Column</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>rtypeID</p></td>
<td><p>int, not null</p></td>
<td><p>Role type ID.</p></td>
</tr>
<tr class="even">
<td><p>rtypeDesc</p></td>
<td><p>nvarchar (256), not null</p></td>
<td><p>Role type description. There are four available roles:</p>
<ul>
<li><p>Member: Chat room member</p></li>
<li><p>Manager: Chat room manager</p></li>
<li><p>Voiced: Presenter for an auditorium chat room</p></li>
<li><p>Creator: Can create chat rooms</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>rtypeAllowedPermSet</p></td>
<td><p>bigint, not null</p></td>
<td><p>Permission set for the role. The used bits are:</p>
<ul>
<li><p>2: True if the role can manage nodes.</p></li>
<li><p>4: True if the role can create children nodes.</p></li>
<li><p>7: True if the role can join a chat room (or children chat rooms of a category).</p></li>
<li><p>8: True if the role can chat in a chat room (or in children chat rooms of a category).</p></li>
<li><p>10: True if the role can read chat history even when not joined to a chat room.</p></li>
<li><p>11: True if the role can see the chat room. (This is further refined by factors such as scope and visibility.)</p></li>
<li><p>12: True if the role can chat in an auditorium chat room.</p></li>
<li><p>13: True if the role can bypass visibility rules when viewing nodes.</p></li>
</ul></td>
</tr>
</tbody>
</table>


### Key

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Column</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>rtypeID</p></td>
<td><p>Primary key.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

