---
title: 'Lync Server 2013: Location Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Location Report
ms:assetid: cb2f1551-1e21-4f13-a39d-91f5f9010ccf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615035(v=OCS.15)
ms:contentKeyID: 48185641
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Location Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

The Location Report provides information about call quality metrics grouped by network location (that is, by network subnet). If your users are experiencing problems with their calls, this report can help you determine if those problems are widespread or if they are largely confined to a given network segment.

<div>

## Accessing the Location Report

The Location Report is accessed from the Monitoring Reports home page. You can drill down to the Call List Report by clicking either of the following metrics:

  - Call volume

  - Poor call percentage

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Location Report enables you to filter on such things as the location where a call was originated or whether the call took place on a wireless or a wired connection. You can also choose how data should be grouped. In this case, calls are grouped by hour, day, week, or month.

The following table lists the filters that you can use with the Location Report.

### Location Report Filters

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
<td><p><strong>Caller location</strong></p></td>
<td><p>IP subnet of the user who placed the call. You can only select <strong>[All]</strong> to indicate all subnets.</p></td>
</tr>
<tr class="even">
<td><p><strong>Callee location</strong></p></td>
<td><p>IP subnet of the user who received the call. You can only select <strong>[All]</strong> to indicate all subnets.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Network type</strong></p></td>
<td><p>Indicates the type of network the client was connected to when the call was placed. Select one of the following:</p>
<ol>
<li><p>[All]</p></li>
<li><p>Wired</p></li>
<li><p>Wireless</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p><strong>VPN</strong></p></td>
<td><p>Indicates whether an external client was using a virtual private network (VPN) connection when the call was placed. Select one of the following:</p>
<ol>
<li><p>[All]</p></li>
<li><p>VPN</p></li>
<li><p>Non-VPN</p></li>
</ol></td>
</tr>
</tbody>
</table>


</div>

<div>

## Metrics

The following table lists the information provided in the Location Report.

### Location Report Metrics

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
<td><p><strong>Caller subnet</strong></p></td>
<td><p>No</p></td>
<td><p>IP subnet of the user who placed the call.</p></td>
</tr>
<tr class="even">
<td><p><strong>Callee subnet</strong></p></td>
<td><p>No</p></td>
<td><p>IP subnet of the user who received the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Call volume</strong></p></td>
<td><p>Yes</p></td>
<td><p>Total number of calls placed.</p></td>
</tr>
<tr class="even">
<td><p><strong>Poor call percentage</strong></p></td>
<td><p>Yes</p></td>
<td><p>Percentage of calls classified as poor calls. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Round trip (ms)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average amount of (in milliseconds) required for a real-time transport protocol (RTP) packet to travel to another endpoint and then back. Round-trip times of 100 milliseconds or less are considered of acceptable quality.</p>
<p>High round-trip values can be caused by international call routing, a routing misconfiguration, or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.</p></td>
</tr>
<tr class="even">
<td><p><strong>Degradation (MOS)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average amount of mean opinion score (MOS) degradation experienced during a call. Degradation values can range from a low of 0.0 to a high of 5.0. A value of 0.5 or less represents acceptable degradation. Historically, mean options scores were calculated by having users rate the quality of a call on a scale of 1-to-5. In Lync Server, Lync Server uses a set of algorithms to predict how users would have rated a call.</p>
<p>High degradation values can be caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server or endpoint. High degradation results in distorted or lost audio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Packet loss</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average rate of RTP packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server. Packet loss typically results in distorted or lost audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Jitter</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average jitter detected between RTP packet arrivals. (Jitter is a measure of the &quot;shakiness&quot; of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Healer concealed ratio</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average ratio of concealed audio samples to the total to the total number of samples. (A concealed audio sample is a technique used to smooth out the abrupt transition that would usually be caused by dropped network packets.) High values indicate significant levels of loss concealment applied caused by packet loss or jitter, and results in distorted or lost audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Healer stretched ratio</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average ratio of stretched audio samples to the total to the total number of samples. (Stretched audio is audio that has been expanded to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample stretching caused by jitter, and result in audio sounding robotic or distorted.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Healer compressed ratio</strong></p></td>
<td><p>Yes</p></td>
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

