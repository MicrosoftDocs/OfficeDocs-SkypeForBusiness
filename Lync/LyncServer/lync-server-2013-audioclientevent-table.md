---
title: 'Lync Server 2013: AudioClientEvent table'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: AudioClientEvent table
ms:assetid: fef73d8f-7261-4e5b-9769-82435b007979
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413086(v=OCS.15)
ms:contentKeyID: 48185967
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# AudioClientEvent table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-17_

Each record contains a client event for one endpoint in an audio call. Usually, one call has two records, one for caller and one for callee.


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
<td><p><strong>ConferenceDateTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primary</p></td>
<td><p>Referenced from the <a href="lync-server-2013-medialine-table.md">MediaLine table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>Referenced from the <a href="lync-server-2013-medialine-table.md">MediaLine table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaLineLabel</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primary</p></td>
<td><p>Referenced from the <a href="lync-server-2013-medialine-table.md">MediaLine table in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromCaller</strong></p></td>
<td><p>bit</p></td>
<td><p>Primary</p></td>
<td><p>0: Callee’s data</p>
<p>1: Caller’s data</p></td>
</tr>
<tr class="odd">
<td><p><strong>NetworkSendQualityEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the NetworkSendQuality event was fired for ‘Bad’ state.</p>
<p>Network quality in terms of jitter or packet loss is severe and impacting the quality of audio being sent.</p></td>
</tr>
<tr class="even">
<td><p><strong>NetworkReceiveQualityEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the ReceiveSendQuality event was fired for ‘Bad’ state.</p>
<p>Network quality in terms of jitter or packet loss is severe and impacting the quality of audio being received.</p></td>
</tr>
<tr class="odd">
<td><p><strong>NetworkDelayEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the Delay event was fired for ‘Bad’ state. Network latency is severe and impacting the experience by preventing interactive communication</p></td>
</tr>
<tr class="even">
<td><p><strong>NetworkBandwidthLowEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the LowBandwidth event was fired for ‘Bad’ state. The available bandwidth is insufficient for an acceptable voice experience.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CPUInsufficientEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the insufficient CPU event was fired for ‘Bad’ state. There are insufficient CPU cycles for processing with the current modalities and applications in use. This causes distortions with the audio channel.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceHalfDuplexAECEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the DeviceHalfDuplexAEC event was fired for ‘Bad’ state. In order to prevent echo, the system has enter half duplex.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceRenderNotFunctioningEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the DeviceRenderNotFunctioning event was fired for ‘Bad’ state. The render device currently being used for the session is not functioning correctly. This can cause one-way audio issues.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceCaptureNotFunctioningEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the DeviceCaptureNotFunctioning event was fired for ‘Bad’ state. The capture device currently being used for the session is not functioning correctly. This can cause one-way audio issues.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceGlitchesEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the DeviceGlitches event was fired for ‘Bad’ state. There are severe glitches in the rendering of audio which is causing distortions. These glitches can be caused by driver issues, deferred procedure calls (DPC) storm (drivers), and high CPU usage.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceLowSNREventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the DeviceLowSNR event was fired for ‘Bad’ state. The capture quality is very poor, either very noisy or user is talking too far away from the microphone. This will cause distortions.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceLowSpeechLevelEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the DeviceLowSpeechLevel event was fired for ‘Bad’ state. User‘s speech level is too low and the system cannot increase it any further. This can either cause distortions or perceived as one-way audio.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceClippingEventRatio</strong></p></td>
<td><p>Decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the DeviceClipping event was fired for ‘Bad’ state.</p>
<p>When near-end speech clips the microphone, far-end hears distortion due to clipping. It is important to avoid near-end microphone clipping.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceEchoEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the DeviceEchoEvent event was fired for ‘Bad’ state. Device or setup is causing echo beyond the ability of the system to compensate.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceNearEndToEchoRatioEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td><p> </p></td>
<td><p>Percentage of session the DeviceNearEndToEchoRatio event was fired for ‘Bad’ state. The user’s speech is too low compared to the echo being captured which impacts the users experience because it limits how easy it is to interrupt a user. Reduce speaker volume, move the microphone closer to the talker.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceMultipleEndpointsEventCount</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>Number of times during session the DeviceMultipleEndpoints event was fired for ‘Bad’ state. Multiple audio endpoints in the same session detected and the system has compensated by reducing render volume.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceHowlingEventCount</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Number of times during session the DeviceHowlingEvent event was fired for ‘Bad’ state. Audio feedback loop detected (caused by multiple endpoints sharing audio path).</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceRenderZeroVolumeEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td></td>
<td><p>Percentage of session the DeviceRenderZeroVolume event was fired for being in the “Bad’ state. The render device was set to zero volume.</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceRenderMuteEventRatio</strong></p></td>
<td><p>decimal(5,2)</p></td>
<td></td>
<td><p>Percentage of session the DeviceRenderMute event was fired for being in the “Bad’ state. The render device was muted.</p>
<p>This column was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

