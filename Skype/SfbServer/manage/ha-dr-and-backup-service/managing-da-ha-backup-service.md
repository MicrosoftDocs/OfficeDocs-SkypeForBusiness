---
title: 'Managing disaster recovery, high availability, and Backup Service'
ms.reviewer: 
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Learn about procedures for disaster recovery operations, as well as for maintaining the Backup Service, which synchronizes the data in paired Front End pools."
---


# Managing Skype for Business Server disaster recovery, high availability, and Backup Service

This section contains procedures for disaster recovery operations, as well as for maintaining the Backup Service, which synchronizes the data in paired Front End pools.

Disaster recovery procedures, both failover and failback, are manual. If there is a disaster, the administrator must manually invoke the failover procedures. The same applies to failback after the pool is repaired.

The disaster recovery procedures in this section assume the following:

  - You have a deployment with paired Front End pools, located in different sites, as described in [Plan for high availability and disaster recovery](../../plan-your-deployment/high-availability-and-disaster-recovery/high-availability-and-disaster-recovery.md). The Backup Service has been running on these paired pools to keep them synchronized.

  - If the Central Management store is hosted on either pool, it is installed and running on both of the paired pools, with one of those pools hosting the active master and the other pool hosting the standby.

> [!IMPORTANT]
> In the following procedures, the *PoolFQDN* parameter refers to the FQDN of the pool that is affected by disaster, not the pool that affected users are being redirected from. For the same set of affected users, it refers to the same pool in both failover and failback cmdlets (that is, the pool that first homed the users before the failover).<BR><br>For example, assume a case in which all users homed on a pool P1 were failed over to the backup pool, P2. If the administrator wants to move all the users currently serviced by P2 to be serviced by P1, the administrator must perform the following steps: 
> <OL>
> <LI>
> <P>Fail back all the users originally homed on P1 from P2 to P1 using the failback cmdlet. In this case, the *PoolFQDN* is P1’s FQDN.</P>
> <LI>
> <P>Fail over all the users originally homed on P2 to P1 using the failover cmdlet. In this case, the PoolFQDN is P2’s FQDN.</P>
> <LI>
> <P>If the administrator later wants to fail back those P2 users back to P2, the PoolFQDN is P2’s FQDN.</P></LI></OL><br>Note that step 1 above must be performed before step 2 to preserve pool integrity. If you try step 2 before step 1, the step 2 cmdlet will fail.


## See Also

[Plan for high availability and disaster recovery](../../plan-your-deployment/high-availability-and-disaster-recovery/high-availability-and-disaster-recovery.md) 
  
