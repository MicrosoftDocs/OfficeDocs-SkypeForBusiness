---
title: 'Lync Server 2013: AppSharingMetricsThreshold table'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: AppSharingMetricsThreshold table
ms:assetid: 782cfab9-01a6-4843-aea1-28f47b0b51f7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205018(v=OCS.15)
ms:contentKeyID: 48184556
ms.date: 12/09/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# AppSharingMetricsThreshold table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-12-08_

The AppSharingMetricsThreshold table contains optimal and acceptable values for the Quality of Experience metrics used with application sharing. These thresholds are used to determine if the application sharing experience should be classified as poor.

This table was introduced in Microsoft Lync Server 2013.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Column</strong></th>
<th><strong>Data Type</strong></th>
<th><strong>Key/Index</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>CallType</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>Type of call that was placed.</p></td>
</tr>
<tr class="even">
<td><p><strong>AppliedBandwidthLimitOptimal</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>Optimal bandwidth limitation for application sharing. The default value is 1000000.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AppliedBandwidthLimitAcceptable</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>Acceptable bandwidth limitation for application sharing. The default value is 500000.</p></td>
</tr>
<tr class="even">
<td><p><strong>SpoiledTilePercentTotalOptimal</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td></td>
<td><p>Optimal percentage rate for “spoiled” tiles for classifying an Application Sharing quality. This value is the percentage of the content from the sharer that did not reach the viewer. Content may be discarded (or spoiled) when the sharer discards tiles from the graphics source or the ASMCU tiles discards tiles from Sharer respectively. The default value is 11 percent.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SpoiledTilePercentTotalAcceptable</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td></td>
<td><p>cceptable percentage rate for “spoiled” tiles for classifying an Application Sharing quality. This value is the percentage of the content from the sharer that did not reach the viewer. Content may be discarded (or spoiled) when the sharer discards tiles from the graphics source or the ASMCU tiles discards tiles from Sharer respectively. The default value is 36 percent.</p></td>
</tr>
<tr class="even">
<td><p><strong>JitterInterArrivalOptimal</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>This column is not used in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>JitterInterArrivalAcceptable</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>This column is not used in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayBurstDensityOptimal</strong></p></td>
<td><p>float</p></td>
<td></td>
<td><p>This column is not used in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayBurstDensityAcceptable</strong></p></td>
<td><p>float</p></td>
<td></td>
<td><p>This column is not used in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyBurstDensityOptimal</strong></p></td>
<td><p>float</p></td>
<td></td>
<td><p>This column is not used in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RDPTileProcessingLatencyBurstDensityAcceptable</strong></p></td>
<td><p>float</p></td>
<td></td>
<td><p>This column is not used in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RelativeOneWayAverageOptimal</strong></p></td>
<td><p>float</p></td>
<td></td>
<td><p>Optimal value for the relative one-way delay between the two media endpoints involved in the application sharing. This is a single-hop latency measure. The default value is 1.0 seconds.</p>
<p>The column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RelativeOneWayAverageAcceptable</strong></p></td>
<td><p>float</p></td>
<td></td>
<td><p>Optimal value for the relative one-way delay between the two media endpoints involved in the application sharing. This is a single-hop latency measure. The default value is 1.75 seconds.</p>
<p>The column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>RDPTileProcessingLatencyAverageOptimal</strong></p></td>
<td><p>float</p></td>
<td></td>
<td><p>Optimal value of the average RDP tile processing latency in the AS Conferencing Server over the duration of the viewing session. Latency is the time difference between when the Start Frame is encoded on the server (sharer or MCU depending on the scenario) and the same Start Frame is decoded on the viewer.</p>
<p>A high average reflects a longer delay in the viewing experience. An overloaded conferencing server may experience higher average delays. The default value is 200ms.</p>
<p>The column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RDPTileProcessingLatencyAverageAcceptable</strong></p></td>
<td><p>float</p></td>
<td></td>
<td><p>Acceptable value of the average RDP tile processing latency in the AS Conferencing Server over the duration of the viewing session. Latency is the time difference between when the Start Frame is encoded on the server (sharer or MCU depending on the scenario) and the same Start Frame is decoded on the viewer.</p>
<p>A high average reflects a longer delay in the viewing experience. An overloaded conferencing server may experience higher average delays. The default value is 200ms.</p>
<p>The column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

