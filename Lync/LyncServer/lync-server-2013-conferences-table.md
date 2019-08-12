---
title: 'Lync Server 2013: Conferences table'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Conferences table
ms:assetid: c3da6271-b3c6-4898-894f-10456ec794d0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412964(v=OCS.15)
ms:contentKeyID: 48185340
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Conferences table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

Each record in this table contains call details about one conference.


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
<td><p>Primary</p></td>
<td><p>Time that the conference request was captured by the CDR agent. Used only as a primary key to uniquely identify a conference instance.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>ID number to identify the session. Used in conjunction with <strong>SessionIdTime</strong> to uniquely identify a conference instance. *</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceUriId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Conference URI. See the <a href="lync-server-2013-conferenceuris-table.md">ConferenceUris table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConfInstance</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p> </p></td>
<td><p>Useful for recurring conferences; each instance of a recurring conference has the same <strong>ConferenceUri</strong>, but will have a different <strong>ConfInstance</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceStartTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>Conference start time.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConferenceEndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>Conference start time.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PoolId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>ID number to identify the pool in which the conference was captured. See the <a href="lync-server-2013-pools-table.md">Pools table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>OrganizerId</strong></p></td>
<td><p>Int</p></td>
<td><p>Foreign</p></td>
<td><p>ID number to identify the organizer URI of this conference. See the <a href="lync-server-2013-users-table.md">Users table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Flag</strong></p></td>
<td><p>smallint</p></td>
<td></td>
<td><p>A bit mask that contains Conference Attributes. Possible values are:</p>
<ul>
<li><p>0X01</p></li>
<li><p>Synthetic</p></li>
<li><p>Transaction</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Processed</strong></p></td>
<td><p>bit</p></td>
<td></td>
<td><p>Internal field used by the Monitoring service.</p>
<p>This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


\* For most sessions, SessionIdSeq will have the value of 1. If two sessions start at exactly the same time, the SessionIdSeq for one will be 1, and for the other will be 2, and so on.

</div>

<span> </span>

</div>

</div>

</div>

