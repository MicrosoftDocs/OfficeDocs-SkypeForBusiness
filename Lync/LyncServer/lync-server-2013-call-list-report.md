---
title: 'Lync Server 2013: Call List Report'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Call List Report
ms:assetid: 9739f9f0-7a37-4844-91d5-f089d2011013
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615020(v=OCS.15)
ms:contentKeyID: 48184921
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Call List Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

The Call List Report provides Quality of Experience (QoE) metrics for individual calls made and received in your organization. Note that the actual metrics reported will depend on how you access the Call List report. For example, if you open the report from the [Device Report in Lync Server 2013](lync-server-2013-device-report.md), you'll see metrics such as the following, metrics that are also reported on the Device Report:

  - Caller's microphone

  - Caller's speaker

  - Callee's microphone

  - Callee's speaker

  - Ratio of voice switch time

However, if you open the Call List Report from the [Location Report in Lync Server 2013](lync-server-2013-location-report.md), you won't see any of those metrics; instead, you'll see metrics like these:

  - Round trip (ms)

  - Degradation (MOS)

  - Packet loss

  - Jitter (ms)

Those are the metrics reported on the Location Report. However, from the Call List Report you can always click the Detail metric to provide complete QoE information for any call.

<div>

## Accessing the Call List Report

The Call List Report can be accessed from any of the following reports:

  - The [Location Report in Lync Server 2013](lync-server-2013-location-report.md) (by clicking the Call volume or Poor call percentage metric)

  - The [Device Report in Lync Server 2013](lync-server-2013-device-report.md) (by clicking the Call volume or Poor call percentage metric)

  - The [Media Quality Summary Report in Lync Server 2013](lync-server-2013-media-quality-summary-report.md) (by clicking the Call volume or Poor call percentage metric)

  - The [Server Performance Report in Lync Server 2013](lync-server-2013-server-performance-report.md) (by clicking the Call volume or Poor call percentage metric)

From within the Call List Report you can access the [Call Detail Report in Lync Server 2013](lync-server-2013-call-detail-report.md) by clicking the Detail metric.

</div>

<div>

## Making the Best Use of the Call List Report

If you can't remember what some of the Call List Report metrics (such as Ratio voice switch time) actually measure, hold your mouse over the metric label; a tool tip will then appear giving you a brief description of the metric.

</div>

<div>

## Filters

None. You cannot filter the Call List Report.

</div>

<div>

## Metrics

The following table lists the information provided in the Call List Report for each call.

### Call List Report Metrics

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
<td><p><strong>Details</strong></p></td>
<td><p>No</p></td>
<td><p>When you click this item, the report shows additional information on the call.</p></td>
</tr>
<tr class="even">
<td><p><strong>Caller</strong></p></td>
<td><p>Yes</p></td>
<td><p>SIP address of the person who initiated the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Callee</strong></p></td>
<td><p>Yes</p></td>
<td><p>SIP address of the person who was called.</p></td>
</tr>
<tr class="even">
<td><p><strong>Start time</strong></p></td>
<td><p>Yes</p></td>
<td><p>Date and time that the call started.</p></td>
</tr>
<tr class="odd">
<td><p><strong>End time</strong></p></td>
<td><p>Yes</p></td>
<td><p>Date and time that the call ended.</p></td>
</tr>
<tr class="even">
<td><p><strong>Caller user agent</strong></p></td>
<td><p>Yes</p></td>
<td><p>Software used by the endpoint of the person who initiated the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Callee user agent</strong></p></td>
<td><p>Yes</p></td>
<td><p>Software used by the endpoint of the person who was called.</p></td>
</tr>
<tr class="even">
<td><p><strong>Round trip (ms)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average amount of (in milliseconds) required for a real-time transport protocol (RTP) packet to travel to another endpoint and then back. Round-trip times of 100 milliseconds or less are considered of acceptable quality.</p>
<p>High round-trip values can be caused by international call routing, a routing misconfiguration, or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Degradation (MOS)</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average amount of mean opinion score (MOS) degradation experienced during a call. Degradation values can range from a low of 0.0 to a high of 5.0. A value of 0.5 or less represents acceptable degradation. Historically, mean options scores were calculated by having users rate the quality of a call on a scale of 1-to-5. In Lync Server, Lync Server uses a set of algorithms to predict how users would have rated a call.</p>
<p>High degradation values can be caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server or endpoint. High degradation results in distorted or lost audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Packet loss</strong></p></td>
<td><p>Yes</p></td>
<td><p>Average rate of RTP packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server. Packet loss typically results in distorted or lost audio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Jitter</strong></p></td>
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
<tr class="odd">
<td><p><strong>Connectivity</strong></p></td>
<td><p>Yes</p></td>
<td><p>Type of wireless communication link. Typically, this is one of the following:</p>
<ul>
<li><p>Relay</p></li>
<li><p>Direct</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

