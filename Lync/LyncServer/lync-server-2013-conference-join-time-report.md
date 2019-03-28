---
title: 'Lync Server 2013: Conference Join Time Report'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Conference Join Time Report
ms:assetid: e64dc89a-25e4-4cb8-bcb1-51712e69ba5a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205344(v=OCS.15)
ms:contentKeyID: 48185686
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Conference Join Time Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-04-23_

The Conference Join Time Summary enables you to determine how long it takes your users to join a conference. The report shows the average join time (in milliseconds), and also provides a breakdown that lets you know how many users were able to join a conference in 2 seconds or less, how many users required between 2 and 5 seconds to join the conference, and so on.

<div>

## Accessing the Conference Join Time Report

The Conference Join Time Report is accessed from the Monitoring Reports home page.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Conference Join Time Report.

### Conference Join Time Report Filters

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
<tr class="odd">
<td><p><strong>Conference sessions</strong></p></td>
<td><p>Type of session. Allowed values are:</p>
<ul>
<li><p>[All]</p></li>
<li><p>Focus sessions (the Focus is the central policy and state manager for online meetings and coordinates all aspects of A conference</p></li>
<li><p>Application sharing</p></li>
<li><p>A/V conferencing</p></li>
</ul>
<p>If you select [All], the total conference join time will be displayed at the top of the report. Note that these totals are only for conferences which were scheduled by using Microsoft Exchange or Microsoft Outlook.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the Conference Join Time Report.

### Conference Join Time Report Metrics

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
<td><p><strong>Date</strong></p>
<p>The actual title for this metric will vary depending on the Interval that was selected.</p></td>
<td><p>No</p></td>
<td><p>Date and time that the conference took place.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of sessions, including successful sessions, failed sessions (both expected failures and unexpected failures), and uncategorized sessions.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Average (ms)</strong></p></td>
<td><p>No</p></td>
<td><p>Average amount of time (in milliseconds) that it took participants to join the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessions &lt; 2 seconds, Volume</strong></p></td>
<td><p>No</p></td>
<td><p>Number of participants who were able to join the conference in less than 2 seconds.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions &lt; 2 seconds, Percentage</strong></p></td>
<td><p>No</p></td>
<td></td>
</tr>
<tr class="even">
<td><p><strong>Sessions 2-5 seconds, Volume</strong></p></td>
<td><p>No</p></td>
<td><p>Number of participants who took between 2 seconds and 5 seconds to join the conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions 2-5 seconds, Percentage</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of the total call participants who took between 2 seconds and 5 seconds to join the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessions 5-10 seconds, Volume</strong></p></td>
<td><p>No</p></td>
<td><p>Number of participants who took between 5 seconds and 10 seconds to join the conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions 5-10 seconds, Percentage</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of the total call participants who took between 5 seconds and 10 seconds to join the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessions &gt; 10 seconds, Volume</strong></p></td>
<td><p>No</p></td>
<td><p>Number of participants who required more than 10 seconds to join the conference.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessions &gt; 10 seconds, Percentage</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of the total call participants who required more than 10 seconds to join the conference.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

