---
title: "Call Park experience in Lync Server 2013 during pool failure"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f6303e69-8771-492a-9e8b-c3d7ba231309
description: "When a Front End pool becomes unavailable due an unplanned incident, calls that have been parked but not yet retrieved are disconnected. During failover to a backup pool, users are redirected to the backup pool and are in resiliency mode. While in resiliency mode, users cannot park calls, but they can place calls on hold and transfer them. When failover is complete, calls can again be parked and retrieved as usual. During failback, users cannot park calls until they are out of resiliency mode."
---

# Call Park experience in Lync Server 2013 during pool failure
[]
When a Front End pool becomes unavailable due an unplanned incident, calls that have been parked but not yet retrieved are disconnected. During failover to a backup pool, users are redirected to the backup pool and are in resiliency mode. While in resiliency mode, users cannot park calls, but they can place calls on hold and transfer them. When failover is complete, calls can again be parked and retrieved as usual. During failback, users cannot park calls until they are out of resiliency mode.
  
During disaster recovery, users who have been redirected to the backup pool as part of the failover process use the Call Park application that is deployed in the backup pool. Therefore, users who are redirected to the backup pool use the call park settings that are configured for the Call Park application in the backup pool.
  
The following table summarizes the Call Park experience through the phases of disaster recovery.
  
**User Experience During Disaster Recovery**

|**Call state**|**When outage occurs**|**During failover**|**During failback**|
|:-----|:-----|:-----|:-----|
|Call not yet parked  <br/> |Call remains connected, but cannot be parked.  <br/> | During failover, call cannot be parked while users are in resiliency mode, but can be put on hold and transferred.  <br/>  When failover completes, call can be parked and retrieved.  <br/> | During failback, call cannot be parked while users are in resiliency mode, but can be put on hold and transferred.  <br/>  When failback completes, call can be parked and retrieved.  <br/> |
|Call parked, but not yet retrieved  <br/> |Call is disconnected.  <br/> |No calls in this state.  <br/> |Call remains parked.  <br/> |
|Parked call already retrieved  <br/> |Call remains connected.  <br/> |Call remains connected.  <br/> |Call remains connected.  <br/> |
   

