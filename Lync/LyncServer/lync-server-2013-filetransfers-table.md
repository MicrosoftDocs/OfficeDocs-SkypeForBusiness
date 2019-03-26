---
title: 'Lync Server 2013: FileTransfers table'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: FileTransfers table
ms:assetid: 5368e67c-d8a9-43a1-9472-a839950dedb3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398353(v=OCS.15)
ms:contentKeyID: 48184118
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# FileTransfers table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

Each record represents one file transfer session.


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
<td><p>Time of session request. Used in conjunction with <strong>SessionIdSeq</strong> to uniquely identify a session. See the <a href="lync-server-2013-dialogs-table.md">Dialogs table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primary, Foreign</p></td>
<td><p>ID number to identify the session. Used in conjunction with <strong>SessionIdTime</strong> to uniquely identify a session. See the <a href="lync-server-2013-dialogs-table.md">Dialogs table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>File Name</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td></td>
<td><p>Name of the file.</p></td>
</tr>
<tr class="even">
<td><p><strong>FileIdentity</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td></td>
<td><p>Unique identifier to distinguish between file transfers involving the same file name.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Cookie</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p>Primary</p></td>
<td><p>Used to identify every follow-up message as being associated with this one.</p></td>
</tr>
<tr class="even">
<td><p><strong>Accept</strong></p></td>
<td><p>bit</p></td>
<td></td>
<td><p>Can be TRUE or NULL. If TRUE, then Reject and Cancel will be NULL.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Reject</strong></p></td>
<td><p>bit</p></td>
<td></td>
<td><p>Can be TRUE or NULL. If TRUE, then Accept and Cancel will be NULL.</p></td>
</tr>
<tr class="even">
<td><p><strong>Cancel</strong></p></td>
<td><p>bit</p></td>
<td></td>
<td><p>Can be TRUE or NULL. If TRUE, then Accept and Reject will be NULL.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

