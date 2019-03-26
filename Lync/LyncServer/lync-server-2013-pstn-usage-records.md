---
title: 'Lync Server 2013: PSTN usage records'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: PSTN usage records
ms:assetid: b5f624aa-abe8-455b-a8e3-c228be230463
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412878(v=OCS.15)
ms:contentKeyID: 48185188
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# PSTN usage records in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-23_

Planning PSTN usage records consists mainly of listing all the call permissions that are currently in force in your organization, from the CEO to temporary workers, consultants, and contingent staff. This process also provides an opportunity to reexamine existing call permissions and revise them. You can create PSTN usage records only for those call permissions that apply to your anticipated Enterprise Voice users, but a better long-range solution might be to create PSTN usage records for all call permissions, regardless of whether some may not currently apply to the group of users to be enabled for Enterprise Voice. If call permissions change or new users with different call permissions are added, you will have already created the required PSTN usage records.

The following table shows a typical PSTN usage table.

### PSTN Usage Records

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Phone attribute</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Local</p></td>
<td><p>Local calls</p></td>
</tr>
<tr class="even">
<td><p>Long-Distance</p></td>
<td><p>Long distance calls</p></td>
</tr>
<tr class="odd">
<td><p>International</p></td>
<td><p>International calls</p></td>
</tr>
<tr class="even">
<td><p>Delhi</p></td>
<td><p>Delhi full-time employees</p></td>
</tr>
<tr class="odd">
<td><p>Redmond</p></td>
<td><p>Redmond full-time employees</p></td>
</tr>
<tr class="even">
<td><p>RedmondTemps</p></td>
<td><p>Redmond temporary employees</p></td>
</tr>
<tr class="odd">
<td><p>Zurich</p></td>
<td><p>Zurich full-time employees</p></td>
</tr>
</tbody>
</table>


By themselves, PSTN usage records do not do anything. For them to work, you must associate them with the following:

  - Voice policies, which are assigned to users.

  - Routes, which are assigned to phone numbers.

For details about voice policies and routes, see [Voice policies in Lync Server 2013](lync-server-2013-voice-policies.md) and [Voice routes in Lync Server 2013](lync-server-2013-voice-routes.md). For details about how to create and configure them, see [Configuring voice routes for outbound calls in Lync Server 2013](lync-server-2013-configuring-voice-routes-for-outbound-calls.md).

</div>

<span> </span>

</div>

</div>

</div>

