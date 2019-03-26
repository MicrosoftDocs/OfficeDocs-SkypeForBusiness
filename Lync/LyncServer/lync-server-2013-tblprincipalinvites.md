---
title: 'Lync Server 2013: tblPrincipalInvites'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: tblPrincipalInvites
ms:assetid: 548ec156-4d1a-469d-a804-62cff226e5c2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558650(v=OCS.15)
ms:contentKeyID: 48184141
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# tblPrincipalInvites in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-25_

tblPrincipalInvites contains invitations for all provisioned users for all nodes with auto-invite on.

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
<td><p>prinID</p></td>
<td><p>int, not null</p></td>
<td><p>Principal ID.</p></td>
</tr>
<tr class="even">
<td><p>invID</p></td>
<td><p>int, not null</p></td>
<td><p>Unique sequential number (per principal ID) generated from tblLastInviteId table.</p></td>
</tr>
<tr class="odd">
<td><p>nodeID</p></td>
<td><p>int, not null</p></td>
<td><p>Node ID (chat room only).</p></td>
</tr>
<tr class="even">
<td><p>createdOn</p></td>
<td><p>datetime, not null</p></td>
<td><p>Time of creation.</p></td>
</tr>
</tbody>
</table>


### Keys

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
<td><p>&lt;prinID, nodeID&gt;</p></td>
<td><p>Primary key.</p></td>
</tr>
<tr class="even">
<td><p>prinID</p></td>
<td><p>Foreign key with lookup in tblPrincipal.prinID table.</p></td>
</tr>
<tr class="odd">
<td><p>nodeID</p></td>
<td><p>Foreign key with lookup in tblNode.nodeID table.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

