---
title: 'Lync Server 2013: tblComplianceData'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: tblComplianceData
ms:assetid: 05b28f9b-4aba-4b69-ba8d-2ceeb6cbfaac
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558606(v=OCS.15)
ms:contentKeyID: 48183308
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# tblComplianceData in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-12_

tblComplianceData contains the compliance events that have not been processed by the compliance adapter yet.

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
<td><p>cmplEventID</p></td>
<td><p>bigint, not null</p></td>
<td><p>Event ID.</p></td>
</tr>
<tr class="even">
<td><p>entryDate</p></td>
<td><p>smalldatetime, not null</p></td>
<td><p>Time of insertion (may be far in the future for cmplType=9 because the entry is just a placeholder in that case).</p></td>
</tr>
<tr class="odd">
<td><p>cmplType</p></td>
<td><p>int, not null</p></td>
<td><p>Type of compliance event:</p>
<ul>
<li><p>1: Chat</p></li>
<li><p>2: Backchat</p></li>
<li><p>3: File download</p></li>
<li><p>4: File upload</p></li>
<li><p>9: Provisional file transfer</p></li>
<li><p>10: Chat deletion (with replace)</p></li>
<li><p>11: Chat purging</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>cmplTime</p></td>
<td><p>bigint, not null</p></td>
<td><p>Time stamp for the event.</p></td>
</tr>
<tr class="odd">
<td><p>cmplChannelUri</p></td>
<td><p>nvarchar (255), not null</p></td>
<td><p>Channel Uniform Resource Identifier (URI).</p></td>
</tr>
<tr class="even">
<td><p>cmplChatID</p></td>
<td><p>bigint</p></td>
<td><p>Chat ID (corresponding to tblChat.chatId table).</p></td>
</tr>
<tr class="odd">
<td><p>cmplUserID</p></td>
<td><p>int, not null</p></td>
<td><p>Principal ID of the poster (corresponding to tblPrincipal.prinID table).</p></td>
</tr>
<tr class="even">
<td><p>cmplUserUri</p></td>
<td><p>nvarchar (255), not null</p></td>
<td><p>User URI.</p></td>
</tr>
<tr class="odd">
<td><p>cmplMessage</p></td>
<td><p>nvarchar (max)</p></td>
<td><p>Message (encoding depends on cmplType).</p></td>
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
<td><p>cmplEventID</p></td>
<td><p>Primary key.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

