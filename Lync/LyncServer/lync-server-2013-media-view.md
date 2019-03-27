---
title: 'Lync Server 2013: Media view'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Media view
ms:assetid: 1a7b2e59-082e-4188-98ae-48ae9bd3494a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ687981(v=OCS.15)
ms:contentKeyID: 49733570
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Media view in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

The Media view stores information about one media type used in a peer-to-peer session. One session would be represented by multiple records in the table, if more than one media type is used. This view was introduced in Microsoft Lync Server 2013.

<div>


> [!NOTE]  
> The Media view should not be used to calculate the media duration for a session. This view contains the signaling details of media exchange in a session. Media exchange is done by the INVITE request, and StartTime indicates the time that the INVITE was sent out. The invite time does not necessarily mean the media start time, because media starts only after the session is accepted.



</div>

The Media view contains all of the columns in the [SessionDetails view in Lync Server 2013](lync-server-2013-sessiondetails-view.md) in addition the ones listed below.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Column</th>
<th>Data Type</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Media</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Media type. See the <a href="lync-server-2013-medialist-table.md">MediaList table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>MediaStartTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Time that a media request was sent out.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaEndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>End time of the session.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

