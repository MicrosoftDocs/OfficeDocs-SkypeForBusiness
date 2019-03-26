---
title: 'Lync Server 2013: tblFileToken'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: tblFileToken
ms:assetid: 49e7dd79-1607-443c-818a-88c160e4ed06
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558646(v=OCS.15)
ms:contentKeyID: 48184073
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# tblFileToken in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-12_

tblFileToken contains temporary tokens for file transfer purposes.

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
<td><p>fileToken</p></td>
<td><p>nvarchar (50), not null</p></td>
<td><p>Unique token (a GUID).</p></td>
</tr>
<tr class="even">
<td><p>fileTokenUserID</p></td>
<td><p>int, not null</p></td>
<td><p>ID of the principal that is transferring the file.</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenChannelID</p></td>
<td><p>GUID, not null</p></td>
<td><p>GUID of the chat room node.</p></td>
</tr>
<tr class="even">
<td><p>fileTokenExpireDate</p></td>
<td><p>datetime, not null</p></td>
<td><p>Expiration time. (Tokens expire after 30 minutes, unless pinned (see the following descriptions in this column).</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenComplianceFileUrl</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>URL of the transferred file (for Compliance service use).</p></td>
</tr>
<tr class="even">
<td><p>fileTokenComplianceThumbnailUrl</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>URL of the thumbnail for the transferred file (for Compliance service use).</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenComplianceTime</p></td>
<td><p>datetime2</p></td>
<td><p>Timestamp for the actual file transfer operation (for Compliance service use).</p></td>
</tr>
<tr class="even">
<td><p>fileTokenComplianceIsUpload</p></td>
<td><p>bit</p></td>
<td><p>True if upload; False if download (for Compliance service use).</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenCompliancePinned</p></td>
<td><p>bit, not null</p></td>
<td><p>True if token is pinned. It’s used to keep the token in the table until Compliance service has a chance to retrieve the relevant fields from it.</p></td>
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
<td><p>fileToken</p></td>
<td><p>Primary key.</p></td>
</tr>
<tr class="even">
<td><p>fileTokenChannelID</p></td>
<td><p>Foreign key with lookup in tblNode.nodeGuid table.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

