---
title: 'Lync Server 2013: Conference Summary Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Conference Summary Report
ms:assetid: 62f54812-5700-45a3-8526-8f58b0f77fbc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558656(v=OCS.15)
ms:contentKeyID: 48184299
ms.date: 09/03/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Conference Summary Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-09-03_

The Conference Summary Report provides an overall view of your online conferencing sessions. A conference typically involves more than 2 users and requires the use of Microsoft Lync Server 2013 conferencing services. By comparison, a peer-to-peer session typically involves just 2 users and does not require the use of Lync Server's conferencing services. Peer-to-peer activities are reported on the [Peer-to-Peer Activity Summary Report in Lync Server 2013](lync-server-2013-peer-to-peer-activity-summary-report.md).

The Conference Summary Report not only tells you how many conferences were held during a given time period (hourly, daily, weekly, monthly) but also tells you the total number of people who took part in those conferences, and the total number of unique conference organizers.

A "unique” organizer is anyone who schedules at least one conference. For example, if Pilar Ackerman schedules one conference she counts as one unique organizer. If Ken Myer schedules 148 conferences he, too counts as one unique organizer. For example, the table below shows 8 conferences scheduled, but just three unique organizers (Ken Myer, Pilar Ackerman, and David Ahs).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Conference Organizer</th>
<th>Conference Date</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 10:00 AM</p></td>
</tr>
<tr class="even">
<td><p>David Ahs</p></td>
<td><p>7/7/2012 10:00 AM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 11:00 AM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/7/2012 11:00 AM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 1:00 PM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/7/2012 2:00 PM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/2/2012 10:00 AM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/2/2012 10:00 AM</p></td>
</tr>
</tbody>
</table>


The Conference Summary Report also indicates how many conferences included audio and/or video.

<div>

## Accessing the Conference Summary Report

The Conference Summary Report is accessed from the Monitoring Reports home page. You can drill down to the Conference Activity report by clicking either of the following metrics:

  - Total conferences

  - Total participants

</div>

<div>

## Making the Best Use of the Conference Summary Report

Total values for most of the metrics used on the Conference Summary Report can be found at the bottom of the report; scroll down to see values such as the total number of conferences held during the specified time period, and the total number of people who participated in those conferences. One metric that is not totaled at the bottom of the report is Total unique conference organizers. Why not? Here’s one reason. Suppose you are looking at a month's worth of data. On day 1 you had 34 unique conference organizers; on day 2 you had 27 unique conference organizers. Does that mean you had 61 unique conference organizers for those two days? Not necessarily. After all, all 27 people who organized conferences on day 2 might be among the 34 people who organized conferences on day 1. For example, in this simple report, note that Ken Myer and Pilar Ackerman scheduled conferences both on 7/7/2012 and on 7/2/2012:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Conference Organizer</th>
<th>Conference Date</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 10:00 AM</p></td>
</tr>
<tr class="even">
<td><p>David Ahs</p></td>
<td><p>7/7/2012 10:00 AM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 11:00 AM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/7/2012 11:00 AM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 1:00 PM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/7/2012 2:00 PM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/2/2012 10:00 AM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/2/2012 10:00 AM</p></td>
</tr>
</tbody>
</table>


To get a better idea of the total number of unique users who organized conferences, change your time interval; for example, look at the data by month instead of by day.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Conference Summary Report enables you to choose how data should be grouped. In this case, conferences grouped by hour, day, week, or month.

The following table lists the filters that you can use with the Conference Summary Report.

### Conference Summary Report Filters

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
<p>If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) are displayed. For example, if you select the Daily interval with a start date of 7/7/2012 and an end date of 2/28/2012, data is displayed for the days 8/7/2012 12:00 AM to 9/7/2012 12:00 AM (that is, a total of 31 days' worth of data).</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table the information provided by the Conferences Summary Report.

### Conference Summary Report Metrics

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
<td><p>Indicates the time interval that you selected on the filter toolbar. Where applicable, you can click a given time interval to view detailed information for that interval. For example, if you are using the Daily interval and you click 7/7/2012, you see an hourly breakdown of user registration activity for that date.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total conferences</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of conferences (regardless of conference type) that were held. When you click this item, the report shows you the Conference Activity Report for the selected time period.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total participants</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of people who took part in the conferences. When you click this item, the report shows you the Conference Activity Report for the selected time period.</p></td>
</tr>
<tr class="even">
<td><p><strong>Average participants per conference</strong></p></td>
<td><p>No</p></td>
<td><p>Average number of people who took part in a given conference. Determined by dividing the total conferences by the total participants.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total A/V conferences</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of conferences that included audio or video.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total A/V conference minutes</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of minutes devoted to audio/video conferencing.</p>
<p>The Total A/V conference minutes metric summarizes all the audio/visual conference types, including: A/V conferences; IM conferences; app sharing conferences; data conferences; and PSTN conferences.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total A/V conference participant minutes</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of participant minutes devoted to audio/video conferencing. For example, suppose one user spends 5 minutes in an audio/video conference and a second user spends 3 minutes in that same conference. That makes a total of 8 participant minutes: 5 minutes plus 3 minutes.</p></td>
</tr>
<tr class="even">
<td><p><strong>Average A/V conference minutes</strong></p></td>
<td><p>No</p></td>
<td><p>Average number of minutes per audio/video conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total number of unique organizers of conferences</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of users who organized at least one conference. Users who organized more than one conference are counted as one unique organizer, just like users who only organized a single conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total conference messages</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of instant messages sent during the conferences.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

