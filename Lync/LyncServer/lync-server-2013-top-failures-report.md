---
title: 'Lync Server 2013: Top Failures Report'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Top Failures Report
ms:assetid: 438942e2-580a-4b67-9d42-f116111fb26a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558640(v=OCS.15)
ms:contentKeyID: 48184021
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Top Failures Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

The Top Failures Report provides a look at the most-commonly reported failures and their trends over time. Failures are based on a combination of the following two metrics:

  - **Diagnostic ID**. Unique identifier (in the form of an ms-diagnostics header) that is attached to a SIP message. Diagnostic IDs provide information useful in troubleshooting call-related problems.

  - **Response code**. Response codes are used in SIP communication sessions to respond to SIP requests. For example, suppose Ken sends the INVITE request to Pilar Ackerman (that is, suppose Ken Myer calls Pilar Ackerman). If Pilar answers, her phone will send the response code 200 (OK), letting Ken's phone know that Pilar has answered. The Top Failures Report only includes response codes that were sent in response to a call failure; Lync Server does not keep track of all the response codes issued during the course of a call.

Information is reported not only for the total number of sessions where a failure occurred but also for the total number of users who were impacted by the failure.

<div>

## Accessing the Top Failures Report

The Top Failures Report is accessed from the Monitoring Reports home page. Clicking the Reported sessions metric will take you to the [Failure Distribution Report in Lync Server 2013](lync-server-2013-failure-distribution-report.md).

</div>

<div>

## Making the Best Use of the Top Failures Report

The Top Failures Report is unusual in one regard: it allows you to filter on as many as 5 diagnostic IDs at once. (Typically you can only filter on one item – such as one user SIP address – at a time.) To filter on multiple diagnostic IDs, simply enter each ID in the Diagnostic IDs box, separating the IDs by using commas. (If you want to, you can leave a blank space after each comma.) For example:

1011, 2412, 1033, 52116, 1008

Do that, and only failed calls that reported at least one of those five diagnostic IDs will be displayed.

If you hold your mouse over a Response code you'll see a tooltip that tells you what the Response code in question means. For example, if you hold the mouse over the Response code 486 you'll see this message:

Busy Here.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Top Failures Report enables you to filter the returned data based on such things as the activity type (peer-to-peer session or conferencing session) or by the SIP response code that accompanied the failed session. You can also choose how data should be grouped. In this case, usages are grouped by hour, day, week, or month.

The following table lists the filters that you can use with the Top Failures Report.

### Top Failures Report Filters

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
<td><p><strong>Activity type</strong></p></td>
<td><p>Type of activity. Select one of the following:</p>
<ul>
<li><p>[All]</p></li>
<li><p>Peer-to-peer</p></li>
<li><p>Conference</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Modality</strong></p></td>
<td><p>At this time the only option available is <strong>[All]</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click <strong>[All]</strong> to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database.</p></td>
</tr>
<tr class="even">
<td><p><strong>Category</strong></p></td>
<td><p>Type of failure experienced. Select one of the following:</p>
<ul>
<li><p>Both expected and unexpected failure</p></li>
<li><p>Unexpected failure</p></li>
</ul>
<p>An &quot;expected failure&quot; is a failure that is expected to happen. For example, if a user has set his or her status to Do Not Disturb you would expect any call to that user to fail. An &quot;unexpected failure&quot; is a failure that occurs in what would appear to be an otherwise healthy system. For example, a call should not be terminated if the caller is placed on hold. If that occurs, that would be flagged as an unexpected failure.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Response code</strong></p></td>
<td><p>SIP response code sent when the conference failed. Enter the entire response code For example:</p>
<p>400</p></td>
</tr>
<tr class="even">
<td><p><strong>Diagnostic ID</strong></p></td>
<td><p>Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors. Diagnostics headers are optional (it is possible to have SIP sessions that do not include these headers), and diagnostic IDs are reported only for sessions that experienced problems of some kind.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the Top Failures Report.

### Top Failures Report Metrics

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
<td><p>Yes</p></td>
<td><p>Relative rank based on the number of reported sessions.</p></td>
</tr>
<tr class="even">
<td><p><strong>Reported sessions</strong></p></td>
<td><p>Yes</p></td>
<td><p>Total number of failed sessions based on diagnostic ID and SIP response code.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Users impacted</strong></p></td>
<td><p>Yes</p></td>
<td><p>Total number of users affected by the failed session.</p></td>
</tr>
<tr class="even">
<td><p><strong>Failure information</strong></p></td>
<td><p>No</p></td>
<td><p>Detailed information about the failure, including diagnostic ID, SIP response code, and description of why the session failed.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Trend in the past</strong></p></td>
<td><p>No</p></td>
<td><p>Graphs failed sessions over time.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

