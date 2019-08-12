---
title: 'Lync Server 2013: Media Quality Comparison Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Media Quality Comparison Report
ms:assetid: c1d0b5a8-98ff-455a-b78b-a05a21cf066d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205236(v=OCS.15)
ms:contentKeyID: 48185317
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Media Quality Comparison Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-04-22_

The Media Quality Comparison Report enables you to compare call quality values for different types of audio calls (for example, calls made over a wireless network vs. calls made across a wired connection).

<div>

## Accessing the Media Quality Comparison Report

The Media Quality Comparison Report is accessed from the Monitoring Reports home page.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Media Quality Comparison Report.

### Media Quality Comparison Report Filters

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
<td><p><strong>Calls</strong></p></td>
<td><p>Type of call to be used as the main comparison item. Allowed values are:</p>
<ul>
<li><p>[All]</p></li>
<li><p>External</p></li>
<li><p>Internal</p></li>
<li><p>VPN</p></li>
<li><p>Non-VPN</p></li>
<li><p>Wired</p></li>
<li><p>Wireless</p></li>
<li><p>External and wired</p></li>
<li><p>External and wireless</p></li>
<li><p>External and VPN</p></li>
<li><p>External and non-VPN</p></li>
<li><p>Internal and wired</p></li>
<li><p>Internal and wireless</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Compare with calls</strong></p></td>
<td><p>Type of call to be used as the secondary comparison item. Allowed values are:</p>
<ul>
<li><p>[All]</p></li>
<li><p>External</p></li>
<li><p>Internal</p></li>
<li><p>VPN</p></li>
<li><p>Non-VPN</p></li>
<li><p>Wired</p></li>
<li><p>Wireless</p></li>
<li><p>External and wired</p></li>
<li><p>External and wireless</p></li>
<li><p>External and VPN</p></li>
<li><p>External and non-VPN</p></li>
<li><p>Internal and wired</p></li>
<li><p>Internal and wireless</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Interval</strong></p></td>
<td><p>Time interval. Select one of the following:</p>
<ul>
<li><p>Hourly (a maximum of 25 hours can be displayed)</p></li>
<li><p>Daily (a maximum of 31 days can be displayed)</p></li>
<li><p>Weekly (a maximum of 12 weeks can be displayed)</p></li>
</ul>
<p>If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2012 and an end date of 2/28/2012, data is displayed for the days 8/7/2012 12:00 AM to 9/7/2012 12:00 AM (that is, a total of 31 days' worth of data).</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the Media Quality Comparison Report.

### Media Quality Comparison Report Metrics

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
<td><p><strong>Call volume</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls.</p></td>
</tr>
<tr class="even">
<td><p><strong>Degradation (MOS)</strong></p></td>
<td><p>No</p></td>
<td><p>Average amount of MOS (mean opinion score) degradation experienced during a call. Degradation values can range from a low of 0.0 to a high of 5.0; a value of 0.5 or less represents acceptable degradation. Historically, mean opinion scores were calculated by having users rate the quality of a call on a scale of 1-to-5. Lync Server uses a set of algorithms to predict how users would have rated a call.</p>
<p>High degradation values can be caused by congestion; lack of bandwidth; wireless congestion or interference, or an overloaded media server or endpoint. High degradation results in distorted or lost audio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Poor call percentage</strong></p></td>
<td><p>No</p></td>
<td><p>The total number of calls classified as poor. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).</p></td>
</tr>
<tr class="even">
<td><p><strong>Round trip (ms)</strong></p></td>
<td><p>No</p></td>
<td><p>Average amount of (in milliseconds) required for a Real-Time Transport Protocol packet to travel to another endpoint and then back. Round-trip times of 200 milliseconds or less are considered of acceptable quality.</p>
<p>High round-trip values can be caused by international call routing; a routing misconfiguration; or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Packet loss</strong></p></td>
<td><p>No</p></td>
<td><p>Average rate of Real-Time Transport Protocol (RTP) packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion; lack of bandwidth; wireless congestion or interference; or an overloaded media server. Packet loss typically results in distorted or lost audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Jitter (ms)</strong></p></td>
<td><p>No</p></td>
<td><p>Average jitter detected between RTP packet arrivals. (Jitter is a measure of the &quot;shakiness&quot; of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Healer concealed ratio</strong></p></td>
<td><p>No</p></td>
<td><p>Average ratio of concealed audio samples to the total to the total number of samples. (A concealed audio sample is a technique used to smooth out the abrupt transition that would usually be caused by dropped network packets.) High values indicate significant levels of loss concealment applied caused by packet loss or jitter, and results in distorted or lost audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Healer stretched ratio</strong></p></td>
<td><p>No</p></td>
<td><p>Average ratio of stretched audio samples to the total to the total number of samples. (Stretched audio is audio that has been expanded to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample stretching caused by jitter, and result in audio sounding robotic or distorted.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Healer compressed ratio</strong></p></td>
<td><p>No</p></td>
<td><p>Average ratio of compressed audio samples to the total number of samples. (Compressed audio is audio that has been compressed to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample compression caused by jitter, and result in audio sounding accelerated or distorted.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

