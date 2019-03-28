---
title: 'Lync Server 2013: Conference Summary Subreport'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Conference Summary Subreport
ms:assetid: 2fc1d2bf-34f5-4093-a6e2-250ec1f1b004
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204779(v=OCS.15)
ms:contentKeyID: 48183742
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Conference Summary Subreport in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-06_

The Conference Summary Subreport provides an overall view of failed conference sessions. These failed sessions are further broken down by session type: Focus sessions and MCU sessions.

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Conference Summary Subreport.

### Conference Summary Subreport Filters

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
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the Conference Summary Subreport.

### Conference Summary Subreport Metrics

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
<td><p>Total number of conferences held.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total conference sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of conference sessions. A single conference can have multiple sessions; for example, a conference might include both a Focus session and an MCU session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Overall session failure rate</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of all conferences that failed.</p></td>
</tr>
<tr class="even">
<td><p><strong>Focus sessions</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of Focus sessions.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Focus failure rate</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of Focus sessions that failed.</p></td>
</tr>
<tr class="even">
<td><p>MCU sessions</p></td>
<td><p>No</p></td>
<td><p>Total number of MCU sessions.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MCU failure rate</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of MCU sessions that failed.</p></td>
</tr>
<tr class="even">
<td><p><strong>MCU sessions by modality</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of MCU sessions, grouped by modality (for example, IM conferencing).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Failure rate by modality</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of MCU sessions that failed, grouped by modality (for example, IM conferencing).</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

