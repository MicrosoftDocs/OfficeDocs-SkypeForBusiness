---
title: 'Lync Server 2013: Failure Distribution Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Failure Distribution Report
ms:assetid: 365c7beb-24d4-40f5-92e7-4978b9688916
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558635(v=OCS.15)
ms:contentKeyID: 48183849
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Failure Distribution Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-21_

The Failure Distribution Report ranks failed sessions in the following categories:

  - Top diagnostic reasons

  - Top modalities

  - Top pools

  - Top sources

  - Top components

  - Top from users

  - Top to users

  - Top from user agents

You can use these categories to determine exactly where a problem is occurring and, in some cases, why the problem is occurring. For example, suppose you recorded 242 failed audio/video sessions during a given day. If you look at the Failure Distribution Report, it might show that 237 of those failed sessions took place in your Dublin pool. That gives you a good place to start when it comes to tracking down and diagnosing the causes behind those failures. If you click on the Dublin pool under the **Top pools** category, you will see a Failure Distribution Report just for that pool. You can then begin analyzing why the Dublin pool was experiencing so many difficulties.

<div>

## Viewing the Failure Distribution Report

You can access the Failure Distribution Report from any of the following reports by clicking either the **Expected failure volume** or the **Unexpected failure volume** metric:

  - [Top Failures Report in Lync Server 2013](lync-server-2013-top-failures-report.md)

  - [Conference Diagnostic Report in Lync Server 2013](lync-server-2013-conference-diagnostic-report.md)

  - [Peer-to-Peer Activity Diagnostic Report in Lync Server 2013](lync-server-2013-peer-to-peer-activity-diagnostic-report.md)

From the Failure Distribution Report, you can click any of the following metrics to view the [Failure List Report in Lync Server 2013](lync-server-2013-failure-list-report.md):

  - Top diagnostic reasons (sessions)

  - Top modalities (sessions)

  - Top pools (sessions)

  - Top sources (sessions)

  - Top components (sessions)

  - Top from users (sessions)

  - Top to users (sessions)

  - Top from user agents (sessions)

</div>

<div>

## Using the Failure Distribution Report

Depending on your monitor size and screen resolution, it's possible that some of the data shown in the Failure Distribution Report might be truncated when you view it onscreen. This is especially true for metrics such as user agents, which can have very long labels. For example, a user agent with a name like "UCCAPI/4.0.7400.0 OC/4.0.7400.0 (Microsoft Lync 2013)" might only partially appear onscreen:

UCCAPI/4.0.7400.0 OC/4.0.7400.0 (Microsoft Ly...

Fortunately, you can see the entire label simply by holding your mouse over the truncated value.

One interesting metric that you can filter on by using the Failure Distribution Report is Diagnostic ID. If you see the same Diagnostic ID cropping up in other reports you can filter on that ID in the Failure Distribution Report and get a very detailed look at exactly where, and how often, that ID has been reported during a failed session.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Failed Distribution Report enables you to filter on such things as the activity type (peer-to-peer session or conferencing session) or by the diagnostic ID that accompanied each failed session.

The following table lists the filters that you can use with the Failure Distribution Report.

### Failure Distribution Report Filters

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
<p>7/7/2012 1:00 PM</p>
<p>If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:</p>
<p>7/7/2012</p>
<p>To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):</p>
<p>7/3/2012</p>
<p>Weeks always run from Sunday through Saturday.</p></td>
</tr>
<tr class="even">
<td><p><strong>To</strong></p></td>
<td><p>End date/time for the time range. To view data by hours, enter both the end date and time as follows:</p>
<p>7/7/2012 1:00 PM</p>
<p>If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:</p>
<p>7/7/2012</p>
<p>To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):</p>
<p>7/3/2012</p>
<p>Weeks always run from Sunday through Saturday.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click <strong>[All]</strong> to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database.</p></td>
</tr>
<tr class="even">
<td><p><strong>Activity type</strong></p></td>
<td><p>Type of activity to filter on. Select one of the following:</p>
<ul>
<li><p>[All]</p></li>
<li><p>Peer-to-peer</p></li>
<li><p>Conference</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Session category</strong></p></td>
<td><p>Indicates whether the activity in question succeeded or failed. Select one of the following:</p>
<ul>
<li><p>[All]</p></li>
<li><p>Success</p></li>
<li><p>Expected failure</p></li>
<li><p>Unexpected failure</p></li>
</ul>
<p>An &quot;expected failure&quot; is a failure that is expected to happen. For example, if a user has set his or her status to Do Not Disturb you would expect any call to that user to fail. An &quot;unexpected failure&quot; is a failure that occurs in what would appear to be an otherwise healthy system. For example, a call should not be terminated if the caller is placed on hold. If that occurs, that would be flagged as an unexpected failure.</p></td>
</tr>
<tr class="even">
<td><p><strong>Diagnostic ID</strong></p></td>
<td><p>Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors. Diagnostics headers are optional (it is possible to have SIP sessions that do not include these headers), and diagnostic IDs are reported only for sessions that experienced problems of some kind.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Top Diagnostic Reasons

The following table lists the information provided in the Failure Distribution Report based on the most frequently reported diagnostic ID.

### Metrics for Top Diagnostic Reasons

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
<td><p><strong>Rank</strong></p></td>
<td><p>No</p></td>
<td><p>Relative ranking of failed sessions based on diagnostic IDs. The diagnostic ID is a unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors.</p></td>
</tr>
<tr class="even">
<td><p><strong>Top diagnostic reasons</strong></p></td>
<td><p>No</p></td>
<td><p>Diagnostic ID generated in a session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of failed sessions where the specified diagnostic ID was generated.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Top Modalities

The following table lists the information provided in the Failure Distribution Report based on the session modalities that experienced the most failures.

### Metrics for Top Modalities

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
<td><p><strong>Rank</strong></p></td>
<td><p>No</p></td>
<td><p>Relative ranking based of failed session based on session type (for example, an audio/video conference or a peer-to-peer file transfer session).</p></td>
</tr>
<tr class="even">
<td><p><strong>Top modalities</strong></p></td>
<td><p>No</p></td>
<td><p>Session type.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of failed sessions involving the specified modality.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Top Pools

The following table lists the information provided in the Failure Distribution Report based on the pools that experienced the most failures.

### Metrics for Top Pools

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
<td><p><strong>Rank</strong></p></td>
<td><p>No</p></td>
<td><p>Relative ranking of failed sessions based on the Registrar pool or Edge Server where the session was conducted.</p></td>
</tr>
<tr class="even">
<td><p><strong>Top pools</strong></p></td>
<td><p>No</p></td>
<td><p>Name of the Registrar pool or Edge Server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of failed sessions per Registrar pool or Edge Server.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Top Sources

The following table lists the information provided in the Failure Distribution Report based on the computers that experienced the most failures.

### Metrics for Top Sources

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
<td><p><strong>Rank</strong></p></td>
<td><p>No</p></td>
<td><p>Relative ranking failed sessions per computer.</p></td>
</tr>
<tr class="even">
<td><p><strong>Top sources</strong></p></td>
<td><p>No</p></td>
<td><p>Name of the computer involved in the failed session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of failed sessions per computer.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Top Components

The following table lists the information provided in the Failure Distribution Report based on the Microsoft Lync Server 2010 components that experienced the most failures.

### Metrics for Top Components

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
<td><p><strong>Rank</strong></p></td>
<td><p>No</p></td>
<td><p>Relative ranking of failed sessions based on Lync Server 2010 component (for example, ExumRouting, GroupChat, or MediationServer).</p></td>
</tr>
<tr class="even">
<td><p><strong>Top components</strong></p></td>
<td><p>No</p></td>
<td><p>Name of the component involved in the failed session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of failed sessions per component.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Top From Users

The following table lists the information provided in the Failure Distribution Report based on users who experienced the most failures when they tried to call someone else (known as "From" users).

### Metrics for Top From Users

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
<td><p><strong>Rank</strong></p></td>
<td><p>No</p></td>
<td><p>Relative ranking of failed sessions based on the user who was invited to join the session.</p></td>
</tr>
<tr class="even">
<td><p><strong>Top from users</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the user invited to join the session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of failed sessions per user.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Top To Users

The following table lists the information provided in the Failure Distribution Report based on the users who experienced the most failures when another user tried to call them (known as "To" users).


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
<td><p><strong>Rank</strong></p></td>
<td><p>No</p></td>
<td><p>Relative ranking of failed sessions based on the user who initiated the session.</p></td>
</tr>
<tr class="even">
<td><p><strong>Top to users</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the user who initiated the session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of failed sessions per user.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Top User Agents

The following table lists the information provided in the Failure Distribution Report based on the endpoint software that experienced the most failures.

### Metrics for Top User Agents

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
<td><p><strong>Rank</strong></p></td>
<td><p>No</p></td>
<td><p>Relative ranking of failed sessions based on the user agent (software) involved in the session. For example: RTCC/4.0.0.0 Inbound Routing/4.0.0.0.</p></td>
</tr>
<tr class="even">
<td><p><strong>Top user agents</strong></p></td>
<td><p>No</p></td>
<td><p>Name of the user agent involved in the failed session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of failed sessions per user agent.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

