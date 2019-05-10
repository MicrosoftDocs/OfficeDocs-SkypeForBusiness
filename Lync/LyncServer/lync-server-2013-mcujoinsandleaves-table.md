---
title: 'Lync Server 2013: McuJoinsAndLeaves table'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: McuJoinsAndLeaves table
ms:assetid: 4e073366-0b5d-45b4-a3f6-d63dd5fd9f25
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398316(v=OCS.15)
ms:contentKeyID: 48184115
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# McuJoinsAndLeaves table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

Each record in this table contains call details about one combination of a user join or leave and conferencing server. For example, if a user joins a conference that includes web conferencing and audio/video elements, one record would be created for that user’s web conferencing join, and another record would be created for the user’s audio/video conferencing join.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Column</th>
<th>Data Type</th>
<th>Key/Index</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primary, Foreign</p></td>
<td><p>Time of conference instance. Used in conjunction with <strong>SessionIdSeq</strong> to uniquely identify a conference instance. See the <a href="lync-server-2013-conferences-table.md">Conferences table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primary, Foreign</p></td>
<td><p>ID number to identify the conference instance. Used in conjunction with <strong>SessionIdTime</strong> to uniquely identify a conference instance. See the <a href="lync-server-2013-conferences-table.md">Conferences table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserId</strong></p></td>
<td><p>int</p></td>
<td><p>Primary, Foreign</p></td>
<td><p>Unique number identifying this user. See the <a href="lync-server-2013-users-table.md">Users table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>McuUserInstance</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>If a user is logged on at multiple computers or devices at once, McuUserInstance uniquely identifies the user/device combination.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsFromPstn</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>Whether the user is joining from a PSTN or not.</p></td>
</tr>
<tr class="even">
<td><p><strong>McuId</strong></p></td>
<td><p>int</p></td>
<td><p>Primary, Foreign</p></td>
<td><p>Unique number identifying this conferencing server. See the <a href="lync-server-2013-mcus-table.md">Mcus table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogSessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Foreign</p></td>
<td><p>Time of session request. Used in conjunction with <strong>SessionIdSeq</strong> to uniquely identify a session. See the <a href="lync-server-2013-dialogs-table.md">Dialogs table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogSessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>ID number to identify the session. Used in conjunction with <strong>SessionIdTime</strong> to uniquely identify a session. See the <a href="lync-server-2013-dialogs-table.md">Dialogs table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserJoinTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>The time this user joins this conferencing server.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserLeaveTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>The time this user leaves this conferencing server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientVerId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Identifier that specifies the version number of the client software use in the conference. See the <a href="lync-server-2013-clientversions-table.md">ClientVersions table in Lync Server 2013</a> for more information.</p>
<p>This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

