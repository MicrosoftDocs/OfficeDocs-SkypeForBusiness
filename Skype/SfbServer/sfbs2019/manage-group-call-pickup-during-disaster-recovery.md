---
title: "Manage Group Call Pickup during disaster recovery in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2d32f19f-c649-4a72-a4fb-edd338e3a7cc
description: "When a Front End pool becomes unavailable due an unplanned incident, service is failed over to the backup pool. During failover to the backup pool, users are redirected to the backup pool and are in resiliency mode. While in resiliency mode, users cannot pick up other users' calls or have their calls picked up by other users. When failover is complete, users can again use Group Call Pickup as usual."
---

# Manage Group Call Pickup during disaster recovery in Lync Server 2013
[]
When a Front End pool becomes unavailable due an unplanned incident, service is failed over to the backup pool. During failover to the backup pool, users are redirected to the backup pool and are in resiliency mode. While in resiliency mode, users cannot pick up other users' calls or have their calls picked up by other users. When failover is complete, users can again use Group Call Pickup as usual. 
  
During failback to the primary pool, users are redirected to the primary pool and are again in resiliency mode. Group Call Pickup functionality is not available until the users are out of resiliency mode. 
  
This section discusses some considerations for Group Call Pickup during disaster recovery and also describes the user experience.
  
## Considerations for Group Call Pickup During Disaster Recovery

During disaster recovery, users who have been redirected to the backup pool as part of the failover process use the Call Park application running in the backup pool for the call pickup group numbers. Therefore, support for Group Call Pickup during disaster recovery requires the Call Park application to be deployed and enabled in both the primary pool and the backup pool.
  
The Group Call Pickup number ranges in the call park orbit table must be redirected to the backup pool after the failover process to the backup pool is complete. The number ranges must be redirected back to the primary pool after the failback process to the primary pool is complete. To redirect the Group Call Pickup ranges, use the **Set-CsCallParkOrbit** cmdlet. 
  
If you deploy a new pool with a different fully qualified domain name (FQDN) to replace the primary pool, you need to reassign all the Group Call Pickup number ranges that were associated with the primary pool to the FQDN of the new pool. To reassign number ranges to the new pool, you can use the **Set-CsCallParkOrbit** cmdlet. For details about the **Set-CsCallParkOrbit** cmdlet, see [Set-CsCallParkOrbit](set-cscallparkorbit.md).
  
## Group Call Pickup Experience During Pool Failure

The following table summarizes the Group Call Pickup experience through the phases of disaster recovery.
  
**User Experience During Disaster Recovery**

|**Call state**|**Failover to backup pool**|**Failback to primary pool**|
|:-----|:-----|:-----|
|New calls  <br/> |**During failover process:** <br/>  Group Call Pickup not available for users in resiliency mode  <br/> **After failover is complete:** <br/>  Group Call Pickup available when users out of resiliency and Group Call Pickup number ranges are redirected to backup pool  <br/> |**During failback process:** <br/>  Group Call Pickup not available for users in resiliency mode  <br/> **After failback is complete:** <br/>  Group Call Pickup available when users out of resiliency and Group Call Pickup number ranges are redirected back to primary pool  <br/> |
|Calls in Group Call Pickup queue  <br/> |**During failover process:** <br/>  Calls in queue cannot be answered through Group Call Pickup.  <br/> **After failover is complete:** <br/>  No calls in this state  <br/> |**During failback process:** <br/>  Calls in queue cannot be answered through Group Call Pickup.  <br/> **After failback is complete:** <br/>  Calls in queue cannot be answered through Group Call Pickup.  <br/> |
|Established call  <br/> |**During failover process:** <br/>  Calls stay connected  <br/> **After failover is complete:** <br/>  Calls stay connected  <br/> |**During failback process:** <br/>  Calls stay connected  <br/> **After failback is complete:** <br/>  Calls stay connected  <br/> |
   

