---
title: 'Lync Server 2013: tblAdminLock'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: tblAdminLock
ms:assetid: 785a43c0-6892-474c-821c-fa9cdbeb99d8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558665(v=OCS.15)
ms:contentKeyID: 48184560
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# tblAdminLock in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-25_

tblAdminLock contains the administrator lock that is needed to run some administrator commands.

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
<td><p>lockExpiresTime</p></td>
<td><p>datetime, not null</p></td>
<td><p>Lock expiration date and time. The owner can extend this value periodically.</p></td>
</tr>
<tr class="even">
<td><p>lockServerID</p></td>
<td><p>int, not null</p></td>
<td><p>ID of the server that owns the lock.</p></td>
</tr>
<tr class="odd">
<td><p>lockActorID</p></td>
<td><p>int, not null</p></td>
<td><p>ID of the principal that owns the lock.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

