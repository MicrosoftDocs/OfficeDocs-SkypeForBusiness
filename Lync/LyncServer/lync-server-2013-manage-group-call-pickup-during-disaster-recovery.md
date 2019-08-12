---
title: 'Lync Server 2013: Manage Group Call Pickup during disaster recovery'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Manage Group Call Pickup during disaster recovery
ms:assetid: 2d32f19f-c649-4a72-a4fb-edd338e3a7cc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945618(v=OCS.15)
ms:contentKeyID: 51541455
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Manage Group Call Pickup during disaster recovery in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-30_

When a Front End pool becomes unavailable due an unplanned incident, service is failed over to the backup pool. During failover to the backup pool, users are redirected to the backup pool and are in resiliency mode. While in resiliency mode, users cannot pick up other users' calls or have their calls picked up by other users. When failover is complete, users can again use Group Call Pickup as usual.

During failback to the primary pool, users are redirected to the primary pool and are again in resiliency mode. Group Call Pickup functionality is not available until the users are out of resiliency mode.

This section discusses some considerations for Group Call Pickup during disaster recovery and also describes the user experience.

<div>

## Considerations for Group Call Pickup During Disaster Recovery

During disaster recovery, users who have been redirected to the backup pool as part of the failover process use the Call Park application running in the backup pool for the call pickup group numbers. Therefore, support for Group Call Pickup during disaster recovery requires the Call Park application to be deployed and enabled in both the primary pool and the backup pool.

The Group Call Pickup number ranges in the call park orbit table must be redirected to the backup pool after the failover process to the backup pool is complete. The number ranges must be redirected back to the primary pool after the failback process to the primary pool is complete. To redirect the Group Call Pickup ranges, use the **Set-CsCallParkOrbit** cmdlet.

If you deploy a new pool with a different fully qualified domain name (FQDN) to replace the primary pool, you need to reassign all the Group Call Pickup number ranges that were associated with the primary pool to the FQDN of the new pool. To reassign number ranges to the new pool, you can use the **Set-CsCallParkOrbit** cmdlet. For details about the **Set-CsCallParkOrbit** cmdlet, see [Set-CsCallParkOrbit](https://docs.microsoft.com/powershell/module/skype/Set-CsCallParkOrbit).

</div>

<div>

## Group Call Pickup Experience During Pool Failure

The following table summarizes the Group Call Pickup experience through the phases of disaster recovery.

### User Experience During Disaster Recovery

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Call state</th>
<th>Failover to backup pool</th>
<th>Failback to primary pool</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>New calls</p></td>
<td><p><strong>During failover process:</strong></p>
<ul>
<li><p>Group Call Pickup not available for users in resiliency mode</p></li>
</ul>
<p><strong>After failover is complete:</strong></p>
<ul>
<li><p>Group Call Pickup available when users out of resiliency and Group Call Pickup number ranges are redirected to backup pool</p></li>
</ul></td>
<td><p><strong>During failback process:</strong></p>
<ul>
<li><p>Group Call Pickup not available for users in resiliency mode</p></li>
</ul>
<p><strong>After failback is complete:</strong></p>
<ul>
<li><p>Group Call Pickup available when users out of resiliency and Group Call Pickup number ranges are redirected back to primary pool</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Calls in Group Call Pickup queue</p></td>
<td><p><strong>During failover process:</strong></p>
<ul>
<li><p>Calls in queue cannot be answered through Group Call Pickup.</p></li>
</ul>
<p><strong>After failover is complete:</strong></p>
<ul>
<li><p>No calls in this state</p></li>
</ul></td>
<td><p><strong>During failback process:</strong></p>
<ul>
<li><p>Calls in queue cannot be answered through Group Call Pickup.</p></li>
</ul>
<p><strong>After failback is complete:</strong></p>
<ul>
<li><p>Calls in queue cannot be answered through Group Call Pickup.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Established call</p></td>
<td><p><strong>During failover process:</strong></p>
<ul>
<li><p>Calls stay connected</p></li>
</ul>
<p><strong>After failover is complete:</strong></p>
<ul>
<li><p>Calls stay connected</p></li>
</ul></td>
<td><p><strong>During failback process:</strong></p>
<ul>
<li><p>Calls stay connected</p></li>
</ul>
<p><strong>After failback is complete:</strong></p>
<ul>
<li><p>Calls stay connected</p></li>
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

