---
title: 'Lync Server 2013: Configuring video example scenarios'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring video example scenarios
ms:assetid: da0d61a2-7ac4-4562-bf6a-18473a29acb2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205297(v=OCS.15)
ms:contentKeyID: 48185536
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring video example scenarios for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-02_

Lync 2013 adds new video features to support 1920 x 1080 full high definition (HD) video and Gallery View video. Measurements based on customer data show that the typical video bandwidth increased only slightly compared to Lync 2010, but the maximum video stream bandwidth has increased due to full HD support (for details, see the "Media Traffic Network Usage" section in [Network bandwidth requirements for media traffic in Lync Server 2013](lync-server-2013-network-bandwidth-requirements-for-media-traffic.md)). Therefore, administrators may want to restrict video bandwidth for certain users (such as users in a branch office that has less network capacity) and help to ensure the best possible video quality for other users (such as executives).

The following table provides a list of recommended settings for configuring video for different network capacities. These settings will restrict some user scenarios from sending and receiving higher resolution videos (see rightmost column). The minimum setting will result in Gallery Video being unavailable, due to the low maximum receive network bandwidth.

### Recommended Video Settings

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>-</th>
<th>AllowMultiView</th>
<th>EnableMultiViewJoin</th>
<th>VideoBitRateKB</th>
<th>TotalReceiveVideoBitRateKB</th>
<th>Expected video resolution for good quality video</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Best</p></td>
<td><p>True</p></td>
<td><p>True</p></td>
<td><p>8000</p></td>
<td><p>8000</p></td>
<td><p>Peer-to-peer: Up to 1920 x 1080 video resolution</p>
<p>Gallery View: Up to two 1920 x 1080 videos or multiple smaller resolution videos</p></td>
</tr>
<tr class="even">
<td><p>Good</p></td>
<td><p>True</p></td>
<td><p>True</p></td>
<td><p>2500</p></td>
<td><p>2500</p></td>
<td><p>Peer-to-peer: Up to 1280 x 720 video resolution</p>
<p>Gallery View: Up to five 640 x 360 resolution videos</p></td>
</tr>
<tr class="odd">
<td><p>Medium</p></td>
<td><p>True</p></td>
<td><p>True</p></td>
<td><p>1000</p></td>
<td><p>1000</p></td>
<td><p>Peer-to-peer: Up to 960 x 540 video resolution</p>
<p>Gallery View: Up to five 424 x 240 resolution videos</p></td>
</tr>
<tr class="even">
<td><p>Minimum</p></td>
<td><p>True</p></td>
<td><p>False</p></td>
<td><p>350</p></td>
<td><p>350</p></td>
<td><p>Peer-to-peer: Up to 424 x 240 video resolution</p>
<p>Gallery View: Unavailable</p></td>
</tr>
</tbody>
</table>


You can use the information in the preceding table to deploy the new HD video and Gallery View video conferencing features for some users in your organization, while allowing different video resolutions for others.

In the following example, the administrator rolls out the new video features with the highest video quality available only to executives. For employees in a remote branch office that has low network capacity, only the minimum setting from the preceding table is deployed. For all other employees, the "Good" setting from the preceding table is deployed.

To roll out the new features to the executives, the administrator creates a conferencing policy named ExecutiveVideo. This conferencing policy has the following settings:

  - VideoBitRateKB is set to 8000 Kbps

  - TotalReceiveVideoBitRateKB is set to 8000 Kbps

  - AllowMultiview is set to True

  - EnableMultiviewJoin is set to True

For employees in the branch office, the administrator creates a conferencing policy named BranchOfficeVideo. This conferencing policy has the following settings:

  - VideoBitRateKB is set to 350 Kbps

  - TotalReceiveVideoBitRateKB is set to 350 Kbps

  - AllowMultiview is set to True

  - EnableMultiviewJoin is set to False

For all other employees, the administrator creates a conferencing policy named StandardVideo. This conferencing policy has the following settings:

  - VideoBitRateKB is set to 2500 Kbps

  - TotalReceiveVideoBitRateKB is set to 2500 Kbps

  - AllowMultiview is set to True

  - EnableMultiviewJoin is set to True

The administrator assigns conferencing policy to users as follows:

  - The ExecutiveVideo conferencing policy is assigned to the executives.

  - The BranchOfficeVideo conferencing policy is assigned to all employees in the branch office.

  - The StandardVideo conferencing policy is assigned to all other employees.

These conferencing policy assignments result in the following user experience:

  - All conferences organized by any user support Gallery View, but employees in the branch office cannot experience Gallery View.

  - For any two-party or multiparty conferences, executives can send 1920 x 1080 full HD video, if their hardware and network link supports it, and can receive 1920 x 1080 full HD video where the other participant clients support it.

  - Employees who are not executives experience lower resolutions than the executives in their two-party or multiparty conferences, but still get good resolution.

  - Employees who are in the branch office will get good video quality in two-party calls when Lync displays the default video window size; however, if the Lync window is maximized to full screen, the video resolution will not increase. For multiparty conferences, the employees in the branch office will see only one active video.

</div>

<span> </span>

</div>

</div>

</div>

