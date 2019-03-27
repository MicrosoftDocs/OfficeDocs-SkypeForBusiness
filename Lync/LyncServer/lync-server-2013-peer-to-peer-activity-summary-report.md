---
title: 'Lync Server 2013: Peer-to-Peer Activity Summary Report'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Peer-to-Peer Activity Summary Report
ms:assetid: e829a21e-9dfa-46ba-9b5b-077c175d6586
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615041(v=OCS.15)
ms:contentKeyID: 48185884
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Peer-to-Peer Activity Summary Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-21_

The Peer-to-Peer Activity Summary Report provides an overall view of your peer-to-peer communication sessions. A peer-to-peer session typically involves just two users, and does not require the use of the Lync Server conferencing services. By comparison, a conference typically involves more than two users and requires the use of Microsoft Lync Server 2013 conferencing services. Conference activity is reported on the Conference Summary Report.

The Peer-to-Peer Activity Summary Report helps you answer questions like the following:

  - How many peer-to-peer instant messages do my users send on a typical day?

  - Are any of my users actually taking advantage of the Lync Server application sharing and file transfer capabilities?

  - Users have been complaining that the network seems slow at certain times of the day. How many minutes are devoted to peer-to-peer audio and video sessions during those time periods?

<div>

## Accessing the Peer-to-Peer Activity Summary Report

You access the Peer-to-Peer Activity Summary Report from the Monitoring Reports home page. You open the [Peer-to-Peer IM Report in Lync Server 2013](lync-server-2013-peer-to-peer-im-report.md) by clicking either of the following metrics:

  - Total peer-to-peer IM sessions

  - Total peer-to-peer IM messages

Likewise, you can open the Peer-to-Peer Voice and Video Report by clicking any of these metrics:

  - Total peer-to-peer audio sessions

  - Total peer-to-peer audio session minutes

  - Total peer-to-peer audio sessions

  - Total peer-to-peer audio session minutes

</div>

<div>

## Making the Best Use of the Peer-to-Peer Activity Summary Report

At the bottom of the Peer-to-Peer Activity Summary Report you'll find totals for metrics such as Total peer-to-peer IM sessions and Total peer-to-peer IM messages. This provides a quick summary of the detailed information found in the body of the report.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely targeted set of data or to view the returned data in different ways. For example, the Peer-to-Peer Activity Summary Report enables you to choose how data should be grouped. In this case, activity grouped by hour, day, week, or month.

The following table lists the filters that you can use with the Peer-to-Peer Activity Summary Report.

### Peer-to-Peer Activity Summary Report Filters

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
<p>7/17/12012 1:00 PM</p>
<p>If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:</p>
<p>7/17/12012</p>
<p>To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):</p>
<p>7/13/2012</p>
<p>Weeks always run from Sunday through Saturday.</p></td>
</tr>
<tr class="even">
<td><p><strong>To</strong></p></td>
<td><p>End date and time for the time range. To view data by hours, enter both the end date and time as follows:</p>
<p>7/17/12012 1:00 PM</p>
<p>If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:</p>
<p>7/17/12012</p>
<p>To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):</p>
<p>7/13/2012</p>
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
<p>If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/17/12012 and an end date of 2/28/2012, data is displayed for the days 8/7/12012 12:00 AM to 9/7/12012 12:00 AM (that is, a total of 31 days' worth of data).</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the Peer-to-Peer Activity Summary Report.

### Peer-to-Peer Activity Summary Report Metrics

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
<td><p><strong>Hourly</strong></p>
<p><strong>Daily</strong></p>
<p><strong>Weekly</strong></p>
<p><strong>Monthly</strong></p></td>
<td><p>No</p></td>
<td><p>Indicates the time interval that you selected on the filter toolbar. Where applicable, you can click a given time interval to view detailed information for that interval. For example, if you are using the Daily interval and you click 7/17/12012, you see an hourly breakdown of user registration activity for that date.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total peer-to-peer sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of peer-to-peer sessions conducted, regardless of session type.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total peer-to-peer IM sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of peer-to-peer instant messaging (IM) sessions. When you click this item, the report shows you the Peer-to-Peer IM Report for the selected time period.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total peer-to-peer IM messages</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of instant messages sent in peer-to-peer sessions. When you click this item, the report shows you the Peer-to-Peer IM Report for the selected time period.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total peer-to-peer audio sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of peer-to-peer audio calls. When you click this field, the report shows you the Peer-to-Peer Voice and Video Report for the selected time period.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total peer-to-peer audio session minutes</strong></p></td>
<td><p>No</p></td>
<td><p>Total amount of time spent in peer-to-peer audio sessions. When you click this item, the report shows you the Peer-to-Peer Voice and Video Report for the selected time period.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Average peer-to-peer audio session minutes</strong></p></td>
<td><p>No</p></td>
<td><p>Average amount of time spent in peer-to-peer audio sessions. Calculated by dividing the total audio session time by the total number of audio sessions.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total peer-to-peer video sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of peer-to-peer video calls. Note that video sessions are also counted as audio sessions: each video session is counted as one video session and one audio session. When you click this item, the report shows you the Peer-to-Peer Voice and Video Report for the selected time period.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total peer-to-peer video session minutes</strong></p></td>
<td><p>No</p></td>
<td><p>Total amount of time spent in peer-to-peer video sessions. When you click this item, the report shows you the Peer-to-Peer Voice and Video Report for the selected time period.</p></td>
</tr>
<tr class="even">
<td><p><strong>Average peer-to-peer video session minutes</strong></p></td>
<td><p>No</p></td>
<td><p>Average amount of time spent in peer-to-peer video sessions. Calculated by dividing the total video session time by the total number of video sessions.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total peer-to-peer file transfer sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of peer-to-peer sessions that included file transfers.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total peer-to-peer application sharing sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of peer-to-peer sessions that included application sharing.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

