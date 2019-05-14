---
title: 'Lync Server 2013: Call Park experience during pool failure'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Call Park experience during pool failure
ms:assetid: f6303e69-8771-492a-9e8b-c3d7ba231309
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205383(v=OCS.15)
ms:contentKeyID: 48185831
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Call Park experience in Lync Server 2013 during pool failure

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-10_

When a Front End pool becomes unavailable due an unplanned incident, calls that have been parked but not yet retrieved are disconnected. During failover to a backup pool, users are redirected to the backup pool and are in resiliency mode. While in resiliency mode, users cannot park calls, but they can place calls on hold and transfer them. When failover is complete, calls can again be parked and retrieved as usual. During failback, users cannot park calls until they are out of resiliency mode.

During disaster recovery, users who have been redirected to the backup pool as part of the failover process use the Call Park application that is deployed in the backup pool. Therefore, users who are redirected to the backup pool use the call park settings that are configured for the Call Park application in the backup pool.

The following table summarizes the Call Park experience through the phases of disaster recovery.

### User Experience During Disaster Recovery

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Call state</th>
<th>When outage occurs</th>
<th>During failover</th>
<th>During failback</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Call not yet parked</p></td>
<td><p>Call remains connected, but cannot be parked.</p></td>
<td><ul>
<li><p>During failover, call cannot be parked while users are in resiliency mode, but can be put on hold and transferred.</p></li>
<li><p>When failover completes, call can be parked and retrieved.</p></li>
</ul></td>
<td><ul>
<li><p>During failback, call cannot be parked while users are in resiliency mode, but can be put on hold and transferred.</p></li>
<li><p>When failback completes, call can be parked and retrieved.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Call parked, but not yet retrieved</p></td>
<td><p>Call is disconnected.</p></td>
<td><p>No calls in this state.</p></td>
<td><p>Call remains parked.</p></td>
</tr>
<tr class="odd">
<td><p>Parked call already retrieved</p></td>
<td><p>Call remains connected.</p></td>
<td><p>Call remains connected.</p></td>
<td><p>Call remains connected.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

