---
title: 'Lync Server 2013: Call Detail Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Call Detail Report
ms:assetid: 38862e35-3fec-41b9-a035-0b301942d446
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558637(v=OCS.15)
ms:contentKeyID: 48183843
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Call Detail Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-05_

The Call Detail Report provides a detailed look at an individual call; the report includes nearly all the Quality of Experience metrics and statistics collected by Lync Server, divided into report sections such as:

  - Call Information

  - Caller Device and Signal Metrics

  - Callee Device and Signal metrics

  - Caller Client Event

  - Callee Client Event

  - Audio Stream (Caller to Callee)

  - Video Stream (Caller to Callee)

  - Audio Stream (Callee to Caller)

  - Video Stream (Callee to Caller)

Keep in mind that the categories and the metrics you see on a given report depend on two things: the type of session and the type of endpoints used in the session. For example, an audio-only call will not report metrics for video streams; that's because the call didn't have a video stream. Likewise, you might have a report that lists caller statistics but not callee statistics. That's typically because the callee was not using a SIP-compliant device. Endpoints are responsible for reporting statistics at the end of a call; however, a cell phone (which knows nothing about SIP or SIP statistics) is unable to report that kind of information. If you call someone and they answer you on their cell phone, you will not get a report from that cell phone when the call ends.

The Call Detail Report is most useful when you are trying to determine exactly why a given call experienced media quality problems.

<div>

## Accessing the Call Detail Report

The Call Detail Report can be accessed from any of the following reports:

  - The [Location Report in Lync Server 2013](lync-server-2013-location-report.md) (by clicking either the Call volume or the Poor call percentage metric)

  - The [Media Quality Summary Report in Lync Server 2013](lync-server-2013-media-quality-summary-report.md) (by clicking either the Call volume or Poor call percentage metric)

  - The [Media Quality Comparison Report in Lync Server 2013](lync-server-2013-media-quality-comparison-report.md) (by clicking the [Call List Report in Lync Server 2013](lync-server-2013-call-list-report.md) and then clicking the Detail metric).

  - The [Server Performance Report in Lync Server 2013](lync-server-2013-server-performance-report.md) (by clicking either the Call volume or Poor call percentage metric)

  - The [Call List Report in Lync Server 2013](lync-server-2013-call-list-report.md) (by clicking the Detail metric)

From within the Call Detail Report you can access the [Device Report in Lync Server 2013](lync-server-2013-device-report.md) by clicking either of the following metrics:

  - Capture device

  - Render device

You can also access the Server Media Quality Trend Report by clicking the A/V edge server metric.

</div>

<div>

## Making the Best Use of the Call Detail Report

The Call Detail Report typically includes over 250 different metrics, including such items as Microphone timestamp drift, Low SNR time, and Near end to echo time. If you can't remember what all of these metrics actually measure, try holding your mouse over the metric label; often-times, a tooltip will appear describing that metric.

If you have problems locating a metric, type part of the metric label in the search box and then click Find. For example, if you can't find the Low SNR time metric, type SNR in the search box and then click Find.

Note that the report only tracks information about a call. The call itself is not recorded.

</div>

<div>

## Filters

None. You cannot filter the Call Detail Report.

</div>

<div>

## Metrics

The following table lists the information provided in the Call Detail Report for each call.

### Call Detail Report Metrics

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
<td><p><strong>Caller PAI</strong></p></td>
<td><p>No</p></td>
<td><p>P-Asserted-Identity of the user who initiated the call. The P-Asserted-Identity is used to convey the proven identity of a user within a trusted network.</p></td>
</tr>
<tr class="even">
<td><p><strong>Caller URI</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the user who initiated the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Caller endpoint</strong></p></td>
<td><p>No</p></td>
<td><p>Device used to make the call.</p></td>
</tr>
<tr class="even">
<td><p><strong>Caller user agent</strong></p></td>
<td><p>No</p></td>
<td><p>Software used on the device that made the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Call start</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time that the call was initially placed.</p></td>
</tr>
<tr class="even">
<td><p><strong>Mediation Server bypass call</strong></p></td>
<td><p>No</p></td>
<td><p>Indicates whether the call connected to a PSTN voice gateway or qualified IP-PBX without passing through the Mediation Server.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Caller OS</strong></p></td>
<td><p>No</p></td>
<td><p>Operating system of the caller's computer.</p></td>
</tr>
<tr class="even">
<td><p><strong>Caller CPU</strong></p></td>
<td><p>No</p></td>
<td><p>CPU installed in the computer of the user who initiated the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Caller CPU core number</strong></p></td>
<td><p>No</p></td>
<td><p>Processor number in the computer used by the person who initiated the call.</p></td>
</tr>
<tr class="even">
<td><p><strong>Caller CPU speed</strong></p></td>
<td><p>No</p></td>
<td><p>Clock speed of the CPU of the computer used by the person who initiated the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Caller CPU virtualization</strong></p></td>
<td><p>No</p></td>
<td><p>Virtualization (if any) used on the computer used by the person who initiated the call.</p></td>
</tr>
<tr class="even">
<td><p><strong>Callee PAI</strong></p></td>
<td><p>No</p></td>
<td><p>P-Asserted-Identity of the user who was invited to join the call. The P-Asserted-Identity is used to convey the proven identity of a user within a trusted network.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Callee URI</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the user who was called.</p></td>
</tr>
<tr class="even">
<td><p><strong>Callee endpoint</strong></p></td>
<td><p>No</p></td>
<td><p>Device used to receive the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Callee user agent</strong></p></td>
<td><p>No</p></td>
<td><p>Software used on the device that received the call.</p></td>
</tr>
<tr class="even">
<td><p><strong>Duration</strong></p></td>
<td><p>No</p></td>
<td><p>Length of time for the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Media bypass warning flag</strong></p></td>
<td><p>No</p></td>
<td><p>Warning issued when the Mediation Server was bypassed.</p></td>
</tr>
<tr class="even">
<td><p><strong>Callee OS</strong></p></td>
<td><p>No</p></td>
<td><p>Operating system of the computer for the user who was called.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Callee CPU</strong></p></td>
<td><p>No</p></td>
<td><p>CPU installed in the computer of the user who was called.</p></td>
</tr>
<tr class="even">
<td><p><strong>Callee core number</strong></p></td>
<td><p>No</p></td>
<td><p>Processor number in the computer used by the person who was called.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Callee CPU speed</strong></p></td>
<td><p>No</p></td>
<td><p>Clock speed of the CPU of the computer used by the person who was called.</p></td>
</tr>
<tr class="even">
<td><p><strong>Callee CPU virtualization</strong></p></td>
<td><p>No</p></td>
<td><p>Virtualization (if any) used on the computer used by the person who was called.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

