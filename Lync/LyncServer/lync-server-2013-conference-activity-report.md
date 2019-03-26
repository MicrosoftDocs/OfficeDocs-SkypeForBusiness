---
title: 'Lync Server 2013: Conference Activity Report'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Conference Activity Report
ms:assetid: 22ddb509-af16-4fc8-9b98-6f58caa6f37e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558627(v=OCS.15)
ms:contentKeyID: 48183618
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Conference Activity Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

The Conference Activity Report makes it easy for you to answer questions like these: how many conferences are being held each day, and when are those conferences being held? Information like this is useful not only in its own right, but also as a troubleshooting tool. For example, suppose users are complaining that the network seems particularly slow in the middle of the day. A quick glance at the Conference Activity reports might suggest one possible reason: far more conferences are being scheduled between the hours of 10:00 AM and 2:00 PM then at any other time.

If the slow network is causing problems, you can encourage users to reschedule some of their conferences during the less-heavily trafficked times of the day.

<div>

## Accessing the Conference Activity Report

The Conference Activity Report is accessed from the [Conference Summary Report in Lync Server 2013](lync-server-2013-conference-summary-report.md) by clicking either one of the following metrics:

  - Total conferences

  - Total participants

</div>

<div>

## Making the Best Use of the Conference Activity Report

By default the Conference Activity Report shows you the total number of conferences for the specified time period (for example, the total number of conferences per day, or the total number of conferences per hour of the day). However, you can also choose to display the total number of participants for that time period or the total number of participant minutes. To do that, click the Show/Hide Parameters button to display the filtering options, and then select one of the following from the Report by dropdown list:

  - Participant count

  - Participant minutes

  - Conference count

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Conference Activity Report.

### Conference Activity Report Filters

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
<td><p>Time interval. Select any of the following:</p>
<ul>
<li><p>Hourly (a maximum of 25 hours can be displayed)</p></li>
<li><p>Daily (a maximum of 31 days can be displayed)</p></li>
<li><p>Weekly (a maximum of 12 weeks can be displayed)</p></li>
<li><p>Monthly (a maximum of 12 months can be displayed)</p></li>
</ul>
<p>If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2012 and an end date of 2/28/2012, data is displayed for the days 8/7/2012 12:00 AM to 9/7/2012 12:00 AM (that is, a total of 31 days' worth of data).</p></td>
</tr>
<tr class="even">
<td><p><strong>Report by</strong></p></td>
<td><p>Indicates the values to be used in the report. You can select one of the following:</p>
<ul>
<li><p>Participant Count</p></li>
<li><p>Participant Minutes</p></li>
<li><p>Conference Count</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Conferences by Pool

The following table lists the information in the Conference Activity Report for each pool.

### Metrics for Conferences by Pool

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
<td><p><strong>Pool</strong></p></td>
<td><p>No</p></td>
<td><p>Name of the Registrar pool or Edge Server used in the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Date/Time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time when the conference was held.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>No</p></td>
<td><p>Total participant count, total participant minutes, or total conference count.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for Conferences by Server Type

The following table lists the information in the Conference Activity Report for each type of server.

### Metrics for Conferences by Server Type

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
<td><p><strong>Conferencing server type</strong></p></td>
<td><p>No</p></td>
<td><p>Type of server used in the conference, typically one of the following:</p>
<ul>
<li><p>Web Conferencing Server</p></li>
<li><p>IM Conferencing Server</p></li>
<li><p>Telephony Conferencing Server</p></li>
<li><p>AV Conferencing Server</p></li>
<li><p>Application Sharing</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Date/Time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time when the conference was held.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>No</p></td>
<td><p>Total participant count, total participant minutes, or total conference count.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

