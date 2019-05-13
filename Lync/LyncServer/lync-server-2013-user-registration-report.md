---
title: 'Lync Server 2013: User Registration Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: User Registration Report
ms:assetid: 151d5cc9-cc1b-4cfa-be9c-55ebe321f7a4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558614(v=OCS.15)
ms:contentKeyID: 48183486
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# User Registration Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-21_

The User Registration Report provides an overview of user logon activity, most notably information about the number of users who logged on to Microsoft Lync Server 2013 during a specified time period (hourly, daily, weekly, monthly). Keep in mind that the report only tells you how many people logged on. It does not tell you *which* people logged on. Monitoring Reports do not provide information about which specific users are using Lync Server 2013 (and which ones are not). However, you can get a rough estimate of user information by using the User Activity Report.

When providing information about user logons, the User Registration Report draws two important distinctions. First, it breaks logons down into two primary categories: internal logons and external logons. Internal logons represent users who logged on from inside your organization's firewall (that is, while connected to the corporate network). External logons represent users who logged on from outside the firewall through an Edge Server (for example, a user who logged on from an Internet café counts as an external logon). If you need to know how many of your users are logging on from outside the firewall, the User Registration Report can provide you with this information.

In addition, the User Registration Report notes how many *active* users were present during a given time period. An active user is a user who took part in an instant messaging (IM) session, participated in a Lync Meeting, made or received a phone call, or otherwise used Lync Server during that period of time. This is different from a user who logged on, but never actually used the system.

<div>

## Accessing the User Registration Report

You access the User Registration Report only from the Monitoring Reports home page. The User Registration Report does not link to any other reports.

</div>

<div>

## Making the Best Use of the User Registration Report

After you've deployed Lync Server one commonly-asked question is this: How do I know if my users are actually using this new technology? Although it has a few limitations in this regard, the User Registration Report can help you answer this question. To determine whether or not users are using Lync Server, you need to do two things. First, get the value of the Unique logon users metric from the User Registration Report. This value tells you how many distinct individuals logged on to Lync Server.

By comparison, the Total logons metric shows how many total times anyone logged on to Lync Server. For example, suppose Ken Myer logged on to Lync Server five different times in a single day. In that case, Ken Myer would count as five separate logon sessions for the Total logons metric, but just one logon user for the Unique logon users metric. Likewise, it's not uncommon for a user to log on from multiple devices or multiple locations. For example, a user can log on using her desktop computer, her laptop computer, and she can have an IP phone that automatically logs on to Lync Server. In this example, there is one unique user with three logons.

To further explain the difference between total logons and unique logons, consider the logons for a given time period in the following table.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>User</th>
<th>Logon time</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 8:45 AM</p></td>
</tr>
<tr class="even">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 8:46 AM</p></td>
</tr>
<tr class="odd">
<td><p>Pilar Ackerman</p></td>
<td><p>7/7/2012 9:17 AM</p></td>
</tr>
<tr class="even">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 9:22 AM</p></td>
</tr>
<tr class="odd">
<td><p>Pilar Ackerman</p></td>
<td><p>7/7/2012 9:31 AM</p></td>
</tr>
</tbody>
</table>


Notice that there is a total of five logons; however, there are only two unique logon users: Ken Myer (who logged on three times) and Pilar Ackerman (who logged on twice). That's the difference between logons and unique logon users.

In addition to knowing the number of unique logons, you need to know the total number of users who have been enabled for Lync Server. That value can be retrieved by opening the Lync Server 2013 Management Shell and running the following Windows PowerShell command:

    (Get-CsUser).Count

If the preceding command returns a value of 1,236 and Unique logon users metric returns an average value of 667, that suggests that a little over half of your users enable for Lync are actually logging on to the system each day (that is, 667 divided by 1,236, which is approximately 54%).

<div>


> [!WARNING]  
> Keep in mind that the logon metrics record users who actually logged on during the specified time period. They don't keep track of users who were already logged on to the system. For example, if your Unique logon users metric shows 667 logons and you have 1,236 users, that suggests that about half your users are logging on to the system. However, suppose 300 users were already logged on to the system at the time you began checking the logon data. That would mean that you actually had nearly 1,000 users logged on to Lync Server, which would mean that closer to 80% of your users were logged on.



</div>

You should also compare the Unique logon users value with the value of the Unique active users metric. The Unique active users metric tells you how many unique users actually used Lync Server: they made a phone call, they joined a Lync Meeting, or they participated in an IM session. This is useful information, because Microsoft Lync 2013 can be configured to automatically start each time a user starts Windows. Because of that, you might have a large number of users who automatically log on to Lync when they log on to Windows each day, but then never actually use Lync Server during that time period.

The Unique active users metric also provides more meaningful data in an organization where users typically do not log off Windows at the end of the day. Instead, they simply lock their computers and leave Windows and Lync running. In a situation like that, you might end up with very few logons per day because your users logged on several days ago and never logged off. However, Unique active users tells you whether users are actively using Lync or another Lync Server client.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely targeted set of data or to view the returned data in different ways. For example, the User Registration Report enables you to view data for all your Registrar pool and Edge Servers or to view data for an individual pool. You can also choose how data should be grouped. In this case, registrations grouped by hour, day, week, or month.

The following table lists the filters that you can use with the User Registration Report.

### User Registration Report Filters

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
<td><p>End date and time for the time range. To view data by hours, enter both the end date and time as follows:</p>
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
<tr class="even">
<td><p><strong>Pool</strong></p></td>
<td><p>Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or choose <strong>[All]</strong> to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the User Registration Report.

### User Registration Report Metrics

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
<td><p><strong>Total logons</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of successful logon sessions.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Internal logons</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of logons within the internal network.</p></td>
</tr>
<tr class="even">
<td><p><strong>External logons</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of logons from outside the internal network, using the Edge Server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Unique logon users</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of users who had at least one logon session. A user who had multiple logon sessions counts as one user, the same as a person who had just a single logon session.</p></td>
</tr>
<tr class="even">
<td><p><strong>Unique active users</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of users who were involved in a peer-to-peer or conferencing session. A user who had multiple sessions counts as one user, the same as a person who had just a single session.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

