---
title: 'Lync Server 2013: Peer-to-Peer Session Detail Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Peer-to-Peer Session Detail Report
ms:assetid: 6be1d676-68f7-4a53-a72a-de73296c5571
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558659(v=OCS.15)
ms:contentKeyID: 48184416
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Peer-to-Peer Session Detail Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-06_

The Peer-to-Peer Session Detail Report returns detailed information about a peer-to-peer session. For example, if you select an instant messaging session, the report will tell you the number of messages sent by each of the two users in the session.

<div>

## Accessing the Peer-to-Peer Session Detail Report

The Peer-to-Peer Session Detail Report can be accessed from any of the following reports (all of which can be accessed from the Monitoring Reports home page):

  - IP Phone Inventory Report

  - User Activity Report

  - Call Admission Control Report

  - Failure List Report

From within the Peer-to-Peer Session Detail Report you can access the [Diagnostic Report in Lync Server 2013](lync-server-2013-diagnostic-report.md) by clicking the Diagnostic Report (Details) metric. You can also access the Top Failures Report by clicking either of these two metrics:

  - Response

  - Diagnostic ID

</div>

<div>

## Making the Best Use of the Peer-to-Peer session Detail Report

The Peer-to-Peer Session Detail Report includes a large number of metrics, many of which might not be familiar to system administrators. Often-times, however, you can view a tooltip that offers a brief description of that metric simply by holding your mouse over the metric label.

Note that the actual metrics shown on a given report will depend on the type of peer-to-peer session you selected. An audio/video session will report a different set of metrics than an instant messaging session.

You can also hold your mouse over the Response code and Diagnostic ID metrics in order to obtain a description of those values:

</div>

<div>

## Filters

None. You cannot filter the Peer-to-Peer Session Detail Report.

</div>

<div>

## Session Information Metrics

The following table lists the information provided in the Peer-to-Peer Session Detail Report for each session.

### Session Information Metrics

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Pool FQDN</strong></p></td>
<td><p>Fully qualified domain name (FQDN) of the Registrar pool or Edge Server involved in the session.</p></td>
</tr>
<tr class="even">
<td><p><strong>Invite time</strong></p></td>
<td><p>Date and time the session invitation was originally sent.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Response time</strong></p></td>
<td><p>Date and time that the invitation acceptance was received.</p></td>
</tr>
<tr class="even">
<td><p><strong>From user</strong></p></td>
<td><p>SIP address of the user who initiated the session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>From user agent</strong></p></td>
<td><p>Software used by the endpoint of the user who initiated the session.</p></td>
</tr>
<tr class="even">
<td><p><strong>Is From user internal</strong></p></td>
<td><p>Indicates whether the user who initiated the session was logged on to the internal network.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Is From user integrated with desk phone</strong></p></td>
<td><p>Indicates whether the endpoint used by the user who initiated the session is integrated with his or her desktop phone.</p></td>
</tr>
<tr class="even">
<td><p><strong>Session Priority</strong></p></td>
<td><p>Priority assigned to the session. Valid priorities are: Unknown; Non-Urgent; Normal; Urgent; and Emergency.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Response code</strong></p></td>
<td><p>SIP response code sent when the session failed.</p></td>
</tr>
<tr class="even">
<td><p><strong>Front end</strong></p></td>
<td><p>Name of the Front End Server used in the conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Capture time</strong></p></td>
<td><p>Date and time that the session information was recorded.</p></td>
</tr>
<tr class="even">
<td><p><strong>End time</strong></p></td>
<td><p>Date and time the session ended.</p></td>
</tr>
<tr class="odd">
<td><p><strong>To user</strong></p></td>
<td><p>SIP address of the user who was invited to the session.</p></td>
</tr>
<tr class="even">
<td><p><strong>To user agent</strong></p></td>
<td><p>Software used by the endpoint of the user who was invited to the session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Is To user internal</strong></p></td>
<td><p>Indicates whether the user who was invited to the session was logged on to the internal network.</p></td>
</tr>
<tr class="even">
<td><p><strong>Is To user integrated with desk phone</strong></p></td>
<td><p>Indicates whether the endpoint used by the user who was invited to the session is integrated with his or her desktop phone.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Is retried session</strong></p></td>
<td><p>Indicates whether the session is an attempt to retry a session that previously failed.</p></td>
</tr>
<tr class="even">
<td><p><strong>Diagnostic ID</strong></p></td>
<td><p>Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors. Hold the mouse over the ID number to view additional information about that ID.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Modalities

The following table lists the information provided in the Peer-to-Peer Session Detail Report for each session modality.

### Metrics for Modalities

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
<td><p><strong>Modalities</strong></p></td>
<td><p>No</p></td>
<td><p>Modalities used in the session. For example, instant messaging (IM) or file transfer.</p></td>
</tr>
<tr class="even">
<td><p><strong>From user messages</strong></p></td>
<td><p>No</p></td>
<td><p>Number of messages sent by the user who initiated the session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>To user messages</strong></p></td>
<td><p>No</p></td>
<td><p>Number of messages sent by the user who was invited to join the session.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Diagnostic Reports

The following table lists the information provided in the Peer-to-Peer Session Detail Report for each diagnostic report.

### Metrics for Diagnostic Reports

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
<td><p><strong>Detail</strong></p></td>
<td><p>No</p></td>
<td><p>When you click this item, the report shows the Diagnostic Report for the session.</p></td>
</tr>
<tr class="even">
<td><p><strong>Report time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time the report was recorded.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Request</strong></p></td>
<td><p>No</p></td>
<td><p>SIP request type. For example, INVITE or BYE.</p></td>
</tr>
<tr class="even">
<td><p><strong>Diagnostic ID</strong></p></td>
<td><p>No</p></td>
<td><p>Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Content type</strong></p></td>
<td><p>No</p></td>
<td><p>Type of media content used in the conference. For example, a common content type is Application/sdp. Session Description Protocol (SDP) is a standard Internet protocol used for session announcements, session invitations, and other forms of multimedia session initiation.</p></td>
</tr>
<tr class="even">
<td><p><strong>Reported by</strong></p></td>
<td><p>No</p></td>
<td><p>Computer (that is, client or server) that reported the problem.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

