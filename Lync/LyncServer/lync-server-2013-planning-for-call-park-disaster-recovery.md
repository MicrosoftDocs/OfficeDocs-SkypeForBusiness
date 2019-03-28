---
title: 'Lync Server 2013: Planning for Call Park disaster recovery'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Planning for Call Park disaster recovery
ms:assetid: f7cf3958-177b-4340-a864-35a6f44d6d88
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205395(v=OCS.15)
ms:contentKeyID: 48185867
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for Call Park disaster recovery in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-30_

This section describes some ways to prepare the Call Park application for disaster recovery and some considerations for the disaster recovery process.

<div>

## Preparing for Call Park Disaster Recovery

Keep the following in mind when preparing for and carrying out disaster recovery procedures.

  - Plan for disaster recovery when you do your capacity planning. For disaster recovery capacity, each pool in a paired pool should be able to handle the workloads of the Call Park services in both pools. For details about Call Park capacity planning, see [Capacity planning for Call Park in Lync Server 2013](lync-server-2013-capacity-planning-for-call-park.md).

  - During disaster recovery, users who have been redirected to the backup pool as part of the failover process use the Call Park service running in the backup pool. Therefore, support for Call Park during disaster recovery requires the Call Park application to be deployed and enabled in both the primary pool and the backup pool.

  - Each pool must have a valid range of orbit numbers for users who are homed in that pool to use for parking calls.

  - Always keep a separate backup copy of any customized music on hold that has been uploaded for Call Park. These files are not backed up as part of the Lync Server 2013 disaster recovery process and will be lost if the files uploaded to the pool are damaged, corrupted, or erased.

</div>

<div>

## Call Park Disaster Recovery Considerations

You can define only one set of Call Park application configuration settings and one customized music-on-hold audio file per pool. These settings include the timeout threshold, music on hold, maximum call pickup attempts, and timeout URI. To view these configuration settings, run the **Get-CsCpsConfiguration** cmdlet. For details about the **Get-CsCpsConfiguration** cmdlet, see [Get-CsCpsConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsCpsConfiguration).

During disaster recovery, Call Park uses the Call Park application in the backup pool, so settings in the primary pool are not backed up. If the primary pool can't be recovered and you deploy a new pool to replace the primary pool, the settings from the primary pool are lost, and you need to reconfigure the Call Park settings and any customized music-on-hold audio files in the new pool.

If you deploy a new pool with a different fully qualified domain name (FQDN) to replace the primary pool, you need to reassign all the Call Park orbit ranges that were associated with the primary pool to the FQDN of the new pool. To reassign orbit ranges to the new pool, you can use either Lync Server Control Panel or the **Set-CsCallParkOrbit** cmdlet. For details about the **Set-CsCallParkOrbit** cmdlet, see [Set-CsCallParkOrbit](https://docs.microsoft.com/powershell/module/skype/Set-CsCallParkOrbit).

</div>

</div>

<span> </span>

</div>

</div>

</div>

