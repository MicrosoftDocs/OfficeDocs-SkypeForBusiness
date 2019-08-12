---
title: 'Lync Server 2013: Call Diagnostic Summary Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Call Diagnostic Summary Report
ms:assetid: 9091de56-13e6-440e-9353-f57c10c906fe
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615016(v=OCS.15)
ms:contentKeyID: 48184789
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Call Diagnostic Summary Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-06_

The Call Diagnostic Summary Report provides an overall look at failed peer-to-peer and conferencing sessions. The report shows the overall failure rate for both types of sessions, and further breaks the failure information down by session modality type:

  - Instant messaging

  - Application sharing

  - File transfer

  - Audio

  - Video

<div>

## Accessing the Call Diagnostic Summary Report

The Call Diagnostic Summary Report is accessed from the Monitoring Reports Home page. From the Call Diagnostic Summary Report you can access the [Peer-to-Peer Activity Diagnostic Report in Lync Server 2013](lync-server-2013-peer-to-peer-activity-diagnostic-report.md) by clicking the Failure rate metric under the Peer-to-Peer Session Summary section of the report. You can also access the [Conference Diagnostic Report in Lync Server 2013](lync-server-2013-conference-diagnostic-report.md) by clicking any of the following conference metrics:

  - Overall session failure rate

  - Focus failure rate

  - MCU failure rate

</div>

<div>

## Making the Best Use of the Call Diagnostic Summary Report

The Call Diagnostic Summary Report includes graphs that compare failure rates for the various modalities used in Microsoft Lync Server 2013. The columns in these graphs are actually hotlinks; for example, if you click the Instant messaging column for peer-to-peer sessions, you'll drill down to an instance of the [Peer-to-Peer Activity Diagnostic Report in Lync Server 2013](lync-server-2013-peer-to-peer-activity-diagnostic-report.md), a report that provides additional details about all the instant messaging sessions included in the Call Diagnostic Summary Report.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Call Diagnostic Summary Report enables you to filter on such things as the Registrar pool or Edge Server used in the session. You can also choose how data should be grouped. In this case, calls are grouped by hour, day, week, or month.

The following table lists the filters that you can use with the Call Diagnostic Summary Report.

### Call Diagnostic Summary Report Filters

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
<td><p><strong>Interval</strong></p></td>
<td><p>Time interval. Select one of the following:</p>
<ul>
<li><p>Hourly (a maximum of 25 hours can be displayed)</p></li>
<li><p>Daily (a maximum of 31 days can be displayed)</p></li>
<li><p>Weekly (a maximum of 12 weeks can be displayed)</p></li>
<li><p>Monthly (a maximum of 12 months can be displayed)</p></li>
</ul>
<p>If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2012 and an end date of 2/28/2012, data is displayed for the days 8/7/2012 12:00 AM to 9/7/2012 12:00 AM (that is, a total of 31 days' worth of data).</p></td>
</tr>
<tr class="even">
<td><p><strong>Pool</strong></p></td>
<td><p>Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click <strong>[All]</strong> to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Peer-to-Peer Sessions

The following table lists the information provided in the Call Diagnostic Summary Report for peer-to-peer sessions (that is, sessions involving just two participants).

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
<td><p><strong>Total sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of peer-to-peer sessions conducted.</p></td>
</tr>
<tr class="even">
<td><p><strong>Failure rate</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of peer-to-peer sessions that failed. When you click this item, the report shows the Peer-to-Peer Activity Diagnostic report, which displays more detailed information about the failed peer-to-peer sessions.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Conferencing Sessions

The following table lists the information provided in the Call Diagnostic Report for conferencing sessions (that is, sessions involving three or more participants).

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
<td><p><strong>Total conferences</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of conferences conducted.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total conference sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of conferencing sessions conducted.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Overall session failure rate</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of the total conferencing sessions that failed.</p></td>
</tr>
<tr class="even">
<td><p><strong>Focus sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of Focus-based conferencing sessions that failed.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Focus failure rate</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of the Focus-based conferencing sessions that failed.</p></td>
</tr>
<tr class="even">
<td><p><strong>MCU sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of conferencing server-based (formerly known as Multipoint Control Unit or MCU) conferences that failed.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MCU failure rate</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of the conferencing server-based (formerly known as Multipoint Control Unit or MCU) conferences that failed.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

