---
title: 'Lync Server 2013: Conference Detail Report'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Conference Detail Report
ms:assetid: 1d61cd81-dcfe-40b4-9a41-a73b038bc216
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204728(v=OCS.15)
ms:contentKeyID: 48183565
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Conference Detail Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

The Conference Detail Report provides detailed information about all the users who participated in a conference. For example, you can see such information as the date and time that a user joined the conference, the date and time that the user left the conference, and the user agent of the endpoint that was used to connect that user to the conference. You can also see information the user's role in each conference (for example, Presenter or Attendee). Perhaps most important, you get quickly see which users successfully join and complete the conference, and which users were not able to successfully join and complete the conference.

<div>

## Accessing the Conference Detail Report

The Conference Detail Report can be accessed from the following reports:

  - The [Call Admission Control Report in Lync Server 2013](lync-server-2013-call-admission-control-report.md) (by clicking the Detail metric for a conference)

  - The [Failure List Report in Lync Server 2013](lync-server-2013-failure-list-report.md) (by clicking the Conference metric)

  - The [User Activity Report in Lync Server 2013](lync-server-2013-user-activity-report.md) (by clicking the Conference URI metric)

From the Conference Detail Report you can access the [Diagnostic Report in Lync Server 2013](lync-server-2013-diagnostic-report.md) by clicking the Diagnostic Report (Detail) metric.

</div>

<div>

## Filters

None. You cannot filter on the Conference Detail Report.

</div>

<div>

## Metrics

The following table lists the information provided in the Conference Information section of the Conference Detail Report.

### Conference Information Metrics

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Can you sort on this item?</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Conference URI</strong></p></td>
<td></td>
<td><p>URI assigned to the conference. For example:</p>
<p>sip:kmyer@litwareinc.com;gruu;opaque=app:conf:focus:id:drg2y8v4</p></td>
</tr>
<tr class="even">
<td><p><strong>Pool FQDN</strong></p></td>
<td></td>
<td><p>Fully-qualified domain name of the Registrar pool or Edge Server involved in a session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Start time</strong></p></td>
<td></td>
<td><p>Date and time that the conference started.</p></td>
</tr>
<tr class="even">
<td><p><strong>Organizer</strong></p></td>
<td></td>
<td><p>SIP address of the user who organized the conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>End time</strong></p></td>
<td></td>
<td><p>Date and time that the conference ended.</p></td>
</tr>
</tbody>
</table>


The following table lists the information provided in the Conference Participation Section of the Conference Detail Report.

### Conference Participation Metrics

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Can you sort on this item?</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>User</strong></p></td>
<td></td>
<td><p>SIP address of the user who participated in the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Role</strong></p></td>
<td></td>
<td><p>Role (for example, Presenter) played by the conference participant.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Connectivity</strong></p></td>
<td></td>
<td><p>Network connectivity (typically From Internal or From External) for the participant.</p></td>
</tr>
<tr class="even">
<td><p>Join time</p></td>
<td></td>
<td><p>Date and time that the participant joined the conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Leave time</strong></p></td>
<td></td>
<td><p>Date and time that the participant left the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>User agent</strong></p></td>
<td></td>
<td><p>Identifier for the software used by the participant’s endpoint.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Diagnostic reports</strong></p></td>
<td></td>
<td><p>Provides diagnostic and troubleshooting information. Including SIP response codes, diagnostic headers, conference join times, and diagnostic IDs for failed sessions.</p></td>
</tr>
</tbody>
</table>


The following table lists the information provided in the Conference Modalities section of the Conference Detail Report.

### Conference Modalities Metrics

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Can you sort on this item?</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>User</strong></p></td>
<td></td>
<td><p>SIP address of the user who participated in the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Join time</strong></p></td>
<td></td>
<td><p>Date and time that the participant joined the conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Leave time</strong></p></td>
<td></td>
<td><p>Date and time that a participant left the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Conferencing server URI</strong></p></td>
<td></td>
<td><p>URI for the Conferencing server used in the conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Diagnostic reports</strong></p></td>
<td></td>
<td><p>Provides diagnostic and troubleshooting information. Including SIP response codes, diagnostic headers, conference join times, and diagnostic IDs for failed sessions.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

