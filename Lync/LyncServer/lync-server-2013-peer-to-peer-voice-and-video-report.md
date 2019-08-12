---
title: 'Lync Server 2013: Peer-to-Peer Voice and Video Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Peer-to-Peer Voice and Video Report
ms:assetid: e17c36b5-5a2f-4673-9696-3b2d31c2bb2f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615040(v=OCS.15)
ms:contentKeyID: 48185535
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Peer-to-Peer Voice and Video Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-21_

The Peer-to-Peer Voice and Video Report provides a detailed look at the distribution of voice and video calls over a specified period of time (for example, calls per hour or calls per day). The report also gives you the option of viewing all the voice and video calls that were made, or of viewing only the successful or failed calls. The reports shows call information broken down into the following groupings:

  - Calls per pool

  - Calls per call type (for example, a Lync to Lync call vs. a Lync call to a person on the PSTN network)

  - Calls per access type (users logged on to the internal network vs. users logged on to the external network)

  - Calls per Mediation Server

<div>

## To access the peer-to-peer voice and video report

You can access the Peer-to-Peer Voice and Video Report only by opening the Peer-to-Peer Activity Summary Report and then clicking any of the following metrics:

  - Total peer-to-peer audio sessions

  - Total peer-to-peer audio minutes

  - Total peer-to-peer video sessions

  - Total peer-to-peer video minutes

</div>

<div>

## To make the best use of the peer-to-peer voice and video report

There are a number of ways you can filter the Peer-to-Peer Voice and Video Report. However, those filtering options are hidden from view by default. To view the filtering options available to you, click **Show/Hide Parameters** button in the upper-right corner of the Report window.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely targeted set of data or to view the data in different ways. The following table lists the filters that you can use with the Peer-to-Peer Voice and Video Report.

### Peer-to-peer voice and video report filters

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
<td><p>Start date and time for the time range. To view data by hours, enter both the start date and time as follows:</p>
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
<td><p><strong>Media type</strong></p></td>
<td><p>Indicates the type of media used in the session. Select one of the following:</p>
<ul>
<li><p>Both</p></li>
<li><p>Audio</p></li>
<li><p>Video</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Call disposition</strong></p></td>
<td><p>Indicates the success or failure of the session. Select one of the following:</p>
<ul>
<li><p>[All]</p></li>
<li><p>Success Calls</p></li>
<li><p>Failed Calls</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Report by</strong></p></td>
<td><p>Indicates the values to be used in the report. Select one of the following:</p>
<ul>
<li><p>Session count</p></li>
<li><p>Call minutes</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for peer-to-peer voice and video activity by Pool

The following table lists the information provided in the Peer-to-Peer Voice and Video Report for each pool.

### Metrics for peer-to-peer voice and video activity by pool

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
<td><p>Name of the Registrar pool or Edge Server used for the call.</p></td>
</tr>
<tr class="even">
<td><p><strong>Date/Time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time period in which the call took place.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of sessions or total message count.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for peer-to-peer voice and video activity by call type

The following table lists the information provided in the Peer-to-Peer Voice and Video Report for each type of call that was made.

### Metrics for peer-to-peer voice and video activity by call type

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
<td><p><strong>Call type</strong></p></td>
<td><p>No</p></td>
<td><p>Indicates the type of call that was made. Values are one of the following:</p>
<ul>
<li><p>UC-to-UC</p></li>
<li><p>UC-to-PSTN</p></li>
<li><p>PSTN-to-UC</p></li>
<li><p>PSTN-to-PSTN</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Date/Time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time period in which the call took place.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of sessions or total message count.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for peer-to-peer voice and video activity by access type

The following table lists the information provided in the Peer-to-Peer Voice and Video Report for each network access type.

### Metrics for peer-to-peer voice and video activity by access type

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
<td><p><strong>Activity type</strong></p></td>
<td><p>No</p></td>
<td><p>Indicates whether the clients were logged on to the internal network or the external network when the call was placed. Values are typically one of the following:</p>
<ul>
<li><p>Internal</p></li>
<li><p>External</p></li>
<li><p>Mixed</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Date/Time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time period in which the call took place.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of sessions or total message count.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics for peer-to-peer voice and video activity by mediation server

The following table lists the information provided in the Peer-to-Peer Voice and Video Report for each Mediation Server.

### Metrics for peer-to-peer voice and video activity by mediation server

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
<td><p><strong>Mediation Server</strong></p></td>
<td><p>No</p></td>
<td><p>Name of the Mediation Server.</p></td>
</tr>
<tr class="even">
<td><p><strong>Date/Time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time period in which the call took place.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of sessions or total message count.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

