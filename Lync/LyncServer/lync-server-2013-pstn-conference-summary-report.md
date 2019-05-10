---
title: 'Lync Server 2013: PSTN Conference Summary Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: PSTN Conference Summary Report
ms:assetid: 8e2f0862-4dfa-4c2b-bf8d-ad71419f15d2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615014(v=OCS.15)
ms:contentKeyID: 48184764
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# PSTN Conference Summary Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

In Microsoft Lync Server 2013, a PSTN conference is any conference in which at least one participant dials in to the audio portion by a using a PSTN (public switched telephone network) phone. (A PSTN phone is a "landline," a cell phone, or any other phone which does not make use of Voice over IP.) Although referred to as PSTN conferences in the Monitoring Reports, these conferences are perhaps more-commonly known as dial-in conferences.

The PSTN Conference Summary Report provides information about all the PSTN conferences held in your organization (that is, all the conferences that had at least one dial-in user). The report includes information about the total number of PSTN conferences, the total number of people who participated in those conferences, and, perhaps, most important, the total number of dial-in users (the Total PSTN participants metric).

<div>

## Accessing the PSTN Conference Summary Report

The PSTN Conference Summary Report can only be accessed from the Monitoring Reports home page. This report is not linked to any other reports. Note that you cannot retrieve detailed call information for a PSTN conference, in part because individual endpoints are responsible for submitting this information. PSTN phones are not capable of tracking or submitting call detail information.

</div>

<div>

## Making the Best Use of the PSTN Conference Summary Report

To determine the percentage of all your conferences that include dial-in users, compare the value of the Total PSTN conferences metric with the Total conferences metric found on the [Conference Summary Report in Lync Server 2013](lync-server-2013-conference-summary-report.md).

If you don't see as many PSTN conferences as you might have expected to see, keep in mind that the ability to organize a conference that allows dial-in users depends on the conferencing policy that has been assigned to a user: if very few of your users are allowed to hold PSTN conferences you would obviously see very few PSTN conferences. You can quickly verify which of your conferencing policies (if any) allow users to schedule PSTN conferences by running the following command from within the Lync Server Management Shell:

    Get-CsConferencingPolicy | Select-Object Identity, EnableDialInConferencing

That will return data similar to this:

    Identity                                EnableDialInConferencing
    --------                                ------------------------
    Global                                                      True
    site:Redmond                                               False
    site:Dublin                                                False
    Tag:RedmondDialInUsers                                      True
    Tag:DublinDialInUsers                                       True

That will return data similar to this:

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the PSTN Conference Summary Report enables you to choose how data should be grouped. In this case, conferences are grouped by hour, day, week, or month.

The following table lists the filters that you can use with the PSTN Conference Summary Report.

### PSTN Conference Summary Report Filters

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
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information in the PSTN Conference Summary Report.

### PSTN Conference Summary Report Metrics

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
<td><p>Indicates the selected time interval. Where applicable, you can click a given time interval to view detailed information for that interval. For example, if you are using the Daily interval and you click 7/7/2012, you see an hourly breakdown of user registration activity for that date.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total PSTN conferences</strong></p></td>
<td><p>No</p></td>
<td><p>Total number conferences that allowed dial-in access.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total participants</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of people who participated in conferences that allowed dial-in access.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total A/V conference minutes</strong></p></td>
<td><p>No</p></td>
<td><p>Total amount of audio/visual conference time.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total A/V conference participant minutes</strong></p></td>
<td><p>No</p></td>
<td><p>Total amount of audio/visual participant time. For example, if one participant spent five minutes in an A/V conference and another participant spent three minutes in the same conference, the total A/V conference participant time would be eight minutes.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total PSTN participants</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of users who dialed in to conferences that allowed dial-in access.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total PSTN participant minutes</strong></p></td>
<td><p>No</p></td>
<td><p>Total amount of conference time spent by dial-in users. For example, if one dial-in participant spent five minutes in a conference and another participant spent three minutes in the same conference, the total PSTN participant time would be eight minutes.</p></td>
</tr>
<tr class="even">
<td><p><strong>Unique conference organizers</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of users who organized at least one conference that allowed dial-in access. Users who organized more than one conference are counted as one unique organizer, just like users who only organized a single conference.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

