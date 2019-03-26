---
title: 'Lync Server 2013: Call Admission Control Report'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Call Admission Control Report
ms:assetid: ea4b0c9f-7f93-4b8a-b901-01e1636c44fb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615043(v=OCS.15)
ms:contentKeyID: 48185933
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Call Admission Control Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-29_

The Call Admission Control Report provides information about peer-to-peer and conferencing sessions that were conducted under restrictions set in place by Call Admission Control. Call Admission Control, introduced in Microsoft Lync Server 2010, provides a way for administrators to allow (or not allow) communication sessions based on bandwidth constraints. For example, administrators can create policies that impose a limit on the amount of bandwidth available for voice and video calls. If that bandwidth limit has been reached, then no new voice or video calls can be placed until one of the current calls has ended and freed up the required network resources.

<div>

## Accessing the Call Admission Control Report

The Call Admission Control Report is accessed from the Monitoring Reports home page. From the Call Admission Control Report you can drill down to either of the following reports:

  - Conference Detail Report – To access this report, click the Details metric from a conference session.

  - Peer-to-Peer Session Detail Report – To access this report, click the Details metric for a peer-to-peer session.

</div>

<div>

## Making the Best Use of the Call Admission Control Report

To get a list of calls that failed because of insufficient bandwidth, select Calls rejected because of call admission control from the Call category dropdown list. Most of the returned calls will likely have a diagnostic ID of 5:

Insufficient bandwidth to establish session. Attempt PSTN re-route.

That indicates that Call Admission Control limitations were preventing the call from being made on the VoIP network.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Call Admission Control Report enables you to filter calls by the user who initiated the call or by the user who was being called. You can also choose how data should be grouped. In this case, calls are grouped by hour, day, week, or month.

The following table lists the filters that you can use with the Call Admission Control Report.

### Call Admission Control Report Filters

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
<td><p><strong>From</strong></p></td>
<td><p>Start date/time for the time range. To view data by hours, enter both the start date and time as follows:</p>
<p>7/17/12012 1:00 PM</p>
<p>If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:</p>
<p>7/17/12012</p>
<p>To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):</p>
<p>7/13/2012</p>
<p>Weeks always run from Sunday through Saturday.</p></td>
</tr>
<tr class="even">
<td><p><strong>To</strong></p></td>
<td><p>End date/time for the time range. To view data by hours, enter both the end date and time as follows:</p>
<p>7/17/12012 1:00 PM</p>
<p>If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:</p>
<p>7/17/12012</p>
<p>To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):</p>
<p>7/13/2012</p>
<p>Weeks always run from Sunday through Saturday.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click <strong>[All]</strong> to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database.</p></td>
</tr>
<tr class="even">
<td><p><strong>Activity type</strong></p></td>
<td><p>Type of activity. Select one of the following activities:</p>
<ul>
<li><p>[All]</p></li>
<li><p>Peer-to-Peer</p></li>
<li><p>Conference</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Call category</strong></p></td>
<td><p>Indicates the reason that CAC was used for the call. Select one of the following:</p>
<ul>
<li><p>[All]</p></li>
<li><p>Call rejected because of call admission control</p></li>
<li><p>Calls rerouted through PSTN because of call admission control</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Peer-to-Peer Sessions

The following table lists the information provided in the Call Admission Control Report for peer-to-peer sessions (that is, sessions involving just two participants).

### Metrics for Peer-to-Peer Sessions

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
<td><p>When you click this item, the report shows you a Peer-to-Peer Session Detail Report for the specified session.</p></td>
</tr>
<tr class="even">
<td><p><strong>From user</strong></p></td>
<td><p>Yes</p></td>
<td><p>SIP address of the user who initiated the session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>To user</strong></p></td>
<td><p>Yes</p></td>
<td><p>SIP address of the user who was invited to join the session.</p></td>
</tr>
<tr class="even">
<td><p><strong>Modalities</strong></p></td>
<td><p>Yes</p></td>
<td><p>Communication modalities (such as audio and video) that were used during the session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Invite time</strong></p></td>
<td><p>Yes</p></td>
<td><p>Date and time the initial session invitation was sent to the From user.</p></td>
</tr>
<tr class="even">
<td><p><strong>Response time</strong></p></td>
<td><p>Yes</p></td>
<td><p>Date and time that the invitation acceptance was received.</p></td>
</tr>
<tr class="odd">
<td><p><strong>End time</strong></p></td>
<td><p>Yes</p></td>
<td><p>Date and time that the session ended.</p></td>
</tr>
<tr class="even">
<td><p><strong>Diagnostic ID</strong></p></td>
<td><p>Yes</p></td>
<td><p>Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors. Diagnostics headers are optional (it is possible to have SIP sessions that do not include these headers), and diagnostic IDs are reported only for sessions that experienced problems of some kind.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Conferencing Sessions

The following table lists the information provided in the Call Admission Control Report for conferencing sessions (that is, sessions involving three or more participants).

### Metrics for Conferencing Sessions

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
<td><p>Yes</p></td>
<td><p>Unique identifier for the conference. When you click this item, the report shows the individual conference participants.</p></td>
</tr>
<tr class="even">
<td><p><strong>Organizer</strong></p></td>
<td><p>Yes</p></td>
<td><p>SIP address of the user who organized the conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>Yes</p></td>
<td><p>Edge Server used in the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Start time</strong></p></td>
<td><p>Yes</p></td>
<td><p>Date and time that the conference started.</p></td>
</tr>
<tr class="odd">
<td><p><strong>End time</strong></p></td>
<td><p>Yes</p></td>
<td><p>Date and time that the conference ended.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Individual Conference Participants

The following table lists the information provided in the Call Admission Control Report for individual conference participants.

### Metrics for Individual Conference Participants

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
<td><p><strong>Role</strong></p></td>
<td><p>No</p></td>
<td><p>Role (for example, Presenter) played by the conference participant.</p></td>
</tr>
<tr class="even">
<td><p><strong>Participant</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the conference participant.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Connectivity</strong></p></td>
<td><p>No</p></td>
<td><p>Network connectivity (typically From Internal or From External) for the participant.</p></td>
</tr>
<tr class="even">
<td><p><strong>Modality</strong></p></td>
<td><p>No</p></td>
<td><p>Conference type (for example, A/V conferencing).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Join time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time that the participant joined the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Leave time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time that the participant left the conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Diagnostic ID</strong></p></td>
<td><p>No</p></td>
<td><p>Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors. Diagnostics headers are optional (it is possible to have SIP sessions that do not include these headers), and diagnostic IDs are reported only for sessions that experienced problems of some kind.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

