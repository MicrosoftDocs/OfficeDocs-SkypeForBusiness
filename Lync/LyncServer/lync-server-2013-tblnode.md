---
title: 'Lync Server 2013: tblNode'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: tblNode
ms:assetid: a31d2961-aa83-4286-a12e-15d279c95f19
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615024(v=OCS.15)
ms:contentKeyID: 48184960
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# tblNode in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-12_

tblNode contains the object tree (with category or chat room nodes) as managed in the Lync Server 2013 Control Panel and administrative cmdlets.

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
<td><p>nodeID</p></td>
<td><p>int, not null</p></td>
<td><p>Node ID (unique number).</p></td>
</tr>
<tr class="even">
<td><p>nodeGuid</p></td>
<td><p>GUID, not null</p></td>
<td><p>Node GUID.</p></td>
</tr>
<tr class="odd">
<td><p>parentID</p></td>
<td><p>int</p></td>
<td><p>Node ID of parent. The root node (with ID 1) includes itself as parent as well.</p></td>
</tr>
<tr class="even">
<td><p>nodeType</p></td>
<td><p>bit, not null</p></td>
<td><p>True if the node is a category.</p>
<p>False if the node is a chat room.</p></td>
</tr>
<tr class="odd">
<td><p>nodeName</p></td>
<td><p>nvarchar (256), not null</p></td>
<td><p>Node name.</p></td>
</tr>
<tr class="even">
<td><p>nodeDesc</p></td>
<td><p>nvarchar (256), not null</p></td>
<td><p>Node description.</p></td>
</tr>
<tr class="odd">
<td><p>invite</p></td>
<td><p>bit</p></td>
<td><p>For categories:</p>
<ul>
<li><p>True if invites are on.</p></li>
<li><p>False if invites are off.</p></li>
</ul>
<p>For rooms:</p>
<ul>
<li><p>False if invites are off (overrides the parent category).</p></li>
<li><p>Null if the invites setting is inherited from the parent category.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>logged</p></td>
<td><p>bit</p></td>
<td><p>For categories:</p>
<ul>
<li><p>True if chat history is on.</p></li>
<li><p>False if chat history is off.</p></li>
</ul>
<p>For rooms:</p>
<ul>
<li><p>Null.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>filePost</p></td>
<td><p>bit</p></td>
<td><p>For categories:</p>
<ul>
<li><p>True if file uploads are allowed.</p></li>
<li><p>False if file uploads are disallowed.</p></li>
</ul>
<p>For rooms:</p>
<ul>
<li><p>Null.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>disabled</p></td>
<td><p>bit, not null</p></td>
<td><p>True if the chat room is disabled. Applies only to chat rooms. (False for categories.)</p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>behavior</p></td>
<td><p>smallint, not null</p></td>
<td><p>Behavior (looked up in EnumValue table):</p>
<ul>
<li><p>4: Normal (normal chat rooms).</p></li>
<li><p>5: Auditorium (auditorium chat rooms, only presenters can contribute).</p></li>
</ul>
<p>Applies only to chat rooms.</p></td>
</tr>
<tr class="odd">
<td><p>visibility</p></td>
<td><p>smallint, not null</p></td>
<td><p>Visibility (looked up on EnumValue table):</p>
<ul>
<li><p>2: Private</p></li>
<li><p>3: Scoped</p></li>
<li><p>6: Open</p></li>
</ul>
<p>Applies only to chat rooms.</p></td>
</tr>
<tr class="even">
<td><p>siopID</p></td>
<td><p>GUID</p></td>
<td><p>Add-In GUID if an add-in is associated with this chat room. (Categories do not have add-ins.)</p>
<p>The add-in information is looked up in SiopWhiteList table.</p></td>
</tr>
<tr class="odd">
<td><p>nodeAddedBy</p></td>
<td><p>int, not null</p></td>
<td><p>ID of the principal that created this node.</p></td>
</tr>
<tr class="even">
<td><p>nodeAddedOn</p></td>
<td><p>bigint, not null</p></td>
<td><p>Time stamp of the node creation.</p></td>
</tr>
<tr class="odd">
<td><p>nodeUpdatedBy</p></td>
<td><p>int, not null</p></td>
<td><p>ID of the principal that did the latest update of this node.</p></td>
</tr>
<tr class="even">
<td><p>nodeUpdatedOn</p></td>
<td><p>bigint, not null</p></td>
<td><p>Time stamp of the latest update of this node.</p></td>
</tr>
<tr class="odd">
<td><p>purgedOn</p></td>
<td><p>datetime</p></td>
<td><p>Time of the latest purge operation (removal of scopes from tblScopedPrincipal table and roles from tblPrincipalRole table) that affected this node. This is used by the Chat service’s internal cache update mechanism.</p></td>
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
<td><p>nodeID</p></td>
<td><p>Primary key.</p></td>
</tr>
<tr class="even">
<td><p>behavior</p></td>
<td><p>Foreign key with lookup in tblEnumValue.valueID table.</p></td>
</tr>
<tr class="odd">
<td><p>visibility</p></td>
<td><p>Foreign key with lookup in tblEnumValue.valueID table.</p></td>
</tr>
<tr class="even">
<td><p>parentID</p></td>
<td><p>Foreign key with lookup in tblNode.nodeID table.</p></td>
</tr>
<tr class="odd">
<td><p>siopID</p></td>
<td><p>Foreign key with lookup in tblSiopWhiteList.siopId table.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

