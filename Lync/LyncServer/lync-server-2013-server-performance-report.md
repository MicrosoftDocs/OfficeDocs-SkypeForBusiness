---
title: 'Lync Server 2013: Server Performance Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Server Performance Report
ms:assetid: 942bb39a-1790-498e-9d99-8f6ce2d155c3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615018(v=OCS.15)
ms:contentKeyID: 48184879
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Server Performance Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

The Server Performance Report provides a list of Microsoft Lync Server 2013 servers that have experienced the highest-percentage of poor calls. The report breaks down servers by server type, reporting separate statistics for the following types:

  - Mediation Server

  - A/V Conferencing Server

  - A/V Edge Server

  - Gateway (Mediation Server)

  - Gateway (Mediation Server bypass)

  - Video (including video metrics for A/V Conferencing servers and A/V Edge servers)

  - Application Sharing (including application sharing metrics for A/V Conferencing servers and A/V Edge servers)

It’s important to note that the ranking shown in this report as relative rankings. For example, suppose your worst-performing server had one poor call among its 1,000 placed calls. That's a more-than-acceptable percentage of .1%. However, if that's the worst-performing server you have (that is, if all your other servers have a poor call percentage even lower than .1%), then that server will still appear on the Server Performance Report.

<div>

## Accessing the Server Performance Report

The Server Performance Report is accessed from the Monitoring Reports home page. You can drill down to the [Call List Report in Lync Server 2013](lync-server-2013-call-list-report.md) by clicking either of the following metrics:

  - Call volume

  - Poor call percentage

In addition, you can drill down to the Server Media Quality Trend Report by clicking the following metric:

  - Trend

</div>

<div>

## Making the Best Use of the Server Performance Report

The Server Performance Report provides a number of ways to filter data; for example, you can filter on network type (calls made from a wired connection vs. calls made from a wireless connection) and access type (calls made from inside the firewall vs. calls made from outside the firewall). It's a good idea when viewing the server performance report to make use of these filters. For example, suppose you have a Mediation Server that has a poor call percentage of 3.24%. If you look solely at wireless calls, that same server might have a poor call percentage approaching 20%. That means that the server was having difficulty with wireless calls, a problem that is partially obscured because the server was not having problems with wired calls.

</div>

<div>

## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Server Performance Report enables you to do such things as filter the returned data by server type or by network type (that is, wired or wireless). You can also choose how data should be grouped. In this case, data is grouped by hour, day, week, or month.

The following table lists the filters that you can use with the Server Performance Report.

### Server Performance Report Filters

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
<td><p><strong>Server type</strong></p></td>
<td><p>Indicates the type of server whose performance should be reported. Select one of the following:</p>
<ol>
<li><p>[All]</p></li>
<li><p>Mediation Server</p></li>
<li><p>A/V Conferencing Server</p></li>
<li><p>A/V Edge Server</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p><strong>Top N</strong></p></td>
<td><p>Indicates the number of servers (based on their poor call percentage) to be displayed in each category. For example, if you select <strong>5</strong> then the five poorest-performing servers are displayed. Select one of the following:</p>
<ol>
<li><p>[All]</p></li>
<li><p>5</p></li>
<li><p>10</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><strong>Access type</strong></p></td>
<td><p>Indicates whether the client was logged on to the internal network or the external network when the call was placed. Select one of the following:</p>
<ol>
<li><p>[All]</p></li>
<li><p>Internal</p></li>
<li><p>External</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p><strong>Network type</strong></p></td>
<td><p>Indicates the type of network the client was connected to when the call was placed. Select one of the following:</p>
<ol>
<li><p>[All]</p></li>
<li><p>Wired</p></li>
<li><p>Wireless</p></li>
</ol></td>
</tr>
<tr class="odd">
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

The following table lists the information provided in the Server Performance Report.

### Server Performance Report Metrics: Audio Call Summary

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Can Sort On</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Server</strong></p></td>
<td><p>No</p></td>
<td><p>Name/IP address of the server.</p></td>
</tr>
<tr class="even">
<td><p><strong>Call volume</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls made.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Poor call percentage</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls classified as poor. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).</p></td>
</tr>
<tr class="even">
<td><p><strong>Round trip (ms)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average amount of (in milliseconds) required for a real-time transport protocol (RTP) packet to travel to another endpoint and then back. Round-trip times of 100 milliseconds or less are considered of acceptable quality.</p>
<p>High round-trip values can be caused by international call routing; a routing misconfiguration; or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Degradation (MOS)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average amount of mean opinion score (MOS) degradation experienced during a call. Degradation values can range from a low of 0.0 to a high of 5.0. A value of 0.5 or less represents acceptable degradation. Historically, mean options scores were calculated by having users rate the quality of a call on a scale of 1-to-5. In Lync Server, the Monitoring Server uses a set of algorithms to predict how users would have rated a call.</p>
<p>High degradation values can be caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server or endpoint. High degradation results in distorted or lost audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Packet loss</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average rate of real-time transport protocol (RTP) packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server. Packet loss typically results in distorted or lost audio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Jitter (ms)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average jitter detected between RTP packet arrivals. (Jitter is a measure of the &quot;shakiness&quot; of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Healer concealed ratio</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average ratio of concealed audio samples to the total to the total number of samples. (A concealed audio sample is a technique used to smooth out the abrupt transition that would usually be caused by dropped network packets.) High values indicate significant levels of loss concealment applied caused by packet loss or jitter, and results in distorted or lost audio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Healer stretched ratio</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average ratio of stretched audio samples to the total to the total number of samples. (Stretched audio is audio that has been expanded to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample stretching caused by jitter, and result in audio sounding robotic or distorted.</p></td>
</tr>
<tr class="even">
<td><p><strong>Healer compressed ratio</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average ratio of compressed audio samples to the total number of samples. (Compressed audio is audio that has been compressed to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample compression caused by jitter, and result in audio sounding accelerated or distorted.</p></td>
</tr>
</tbody>
</table>


### Server Performance Report Metrics: Video Call Summary

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
<td><p><strong>Call type/Endpoint type</strong></p></td>
<td><p>No</p></td>
<td><p>When you click this item, the report shows detailed information about calls based on that type. Call types include:</p>
<ul>
<li><p>UC Peer-to-Peer Calls</p></li>
<li><p>UC Conference Sessions</p></li>
<li><p>PSTN Conference Sessions</p></li>
<li><p>PSTN Calls: Media Bypass</p></li>
<li><p>PSTN Calls (Non-Bypass): UC Leg</p></li>
<li><p>PSTN Calls (Non-Bypass): Gateway Leg</p></li>
<li><p>Other Call Types</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Call volume</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls per call type.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Poor call percentage</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls classified as poor. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).</p></td>
</tr>
<tr class="even">
<td><p><strong>Call volume (wireless call)</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls that used a wireless connection.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Call volume (VPN call)</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls that used a VPN connection.</p></td>
</tr>
<tr class="even">
<td><p><strong>Call volume (external call)</strong></p></td>
<td><p>No</p></td>
<td><p>Number of calls that used an external connection (that is, a connection outside the internal network).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Avg bit-rate (Kbits/s)</strong></p></td>
<td><p>No</p></td>
<td><p>Average video bit rate (in kilobits per second).</p></td>
</tr>
<tr class="even">
<td><p><strong>Low bit-rate %</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of the call where the bit rate was low.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Outbound packet loss</strong></p></td>
<td><p>No</p></td>
<td><p>Real-Time Transport Protocol (RTP) packet loss for outbound packets. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion; lack of bandwidth; wireless congestion or interference; or an overloaded media server. Packet loss typically results in distorted or lost audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Frozen frame %</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of “frozen” frames. In a frozen frame, the video stops advancing while the audio portion of the call continues.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Outbound avg frame rate</strong></p></td>
<td><p>No</p></td>
<td><p>Average frame rate for outbound transmissions during the call.</p></td>
</tr>
<tr class="even">
<td><p><strong>Inbound avg frame rate</strong></p></td>
<td><p>No</p></td>
<td><p>Average frame rate for incoming transmissions during the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Inbound low frame rate %</strong></p></td>
<td><p>No</p></td>
<td><p>Percentage of the call where the bit rate for incoming video was low.</p></td>
</tr>
<tr class="even">
<td><p><strong>Client health %</strong></p></td>
<td></td>
<td><p>Indicates the relative health of the client device during the call.</p></td>
</tr>
</tbody>
</table>


### Server Performance Report Metrics: Application Sharing Call Summary

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
<td><p><strong>Call type/Endpoint type</strong></p></td>
<td><p>No</p></td>
<td><p>When you click this item, the report shows detailed information about calls based on that type. Call types include:</p>
<ul>
<li><p>UC Peer-to-Peer Calls</p></li>
<li><p>UC Conference Sessions</p></li>
<li><p>PSTN Conference Sessions</p></li>
<li><p>PSTN Calls: Media Bypass</p></li>
<li><p>PSTN Calls (Non-Bypass): UC Leg</p></li>
<li><p>PSTN Calls (Non-Bypass): Gateway Leg</p></li>
<li><p>Other Call Types</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Call volume</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls per call type.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Poor call percentage</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls classified as poor. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).</p></td>
</tr>
<tr class="even">
<td><p><strong>Call volume (wireless call)</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls that used a wireless connection.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Call volume (VPN call)</strong></p></td>
<td><p>No</p></td>
<td><p>Total number of calls that used a VPN connection.</p></td>
</tr>
<tr class="even">
<td><p><strong>Call volume (external call)</strong></p></td>
<td><p>No</p></td>
<td><p>Number of calls that used an external connection (that is, a connection outside the internal network).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Jitter (ms)</strong></p></td>
<td><p>No</p></td>
<td><p>Average jitter detected between RTP packet arrivals. (Jitter is a measure of the &quot;shakiness&quot; of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Avg. relative one way</strong></p></td>
<td><p>No</p></td>
<td><p>Average relative one-way delay between two media endpoints. This is a single-hop latency measure.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Avg. RDP tile processing latency</strong></p></td>
<td><p>No</p></td>
<td><p>The average RDP tile processing latency in the AS Conferencing Server over the duration of the viewing session. This metric does not cover network latency. A high average reflects a longer delay in the viewing experience. An overloaded conferencing server may experience higher average delays.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total spoiled tile %</strong></p></td>
<td><p>No</p></td>
<td><p>Total percentage of spoiled RDP tiles.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

