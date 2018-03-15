---
title: "Managing Lync Server 2013 disaster recovery, high availability, and Backup Service"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f4cd36fb-ffd6-48fa-b761-e11b3bcff91a
description: "This section contains procedures for disaster recovery operations, as well as for maintaining the Backup Service which synchronizes the data in paired Front End pools."
---

# Managing Lync Server 2013 disaster recovery, high availability, and Backup Service
[]
This section contains procedures for disaster recovery operations, as well as for maintaining the Backup Service which synchronizes the data in paired Front End pools.
  
Disaster recovery procedures, both failover and failback, are manual. If there is a disaster, the administrator must manually invoke the failover procedures. The same applies to failback after the pool is repaired.
  
The disaster recovery procedures in the rest of this section assume the following:
  
- You have a deployment with paired Front End pools, located in different sites, as described in [Planning for high availability and disaster recovery in Lync Server 2013](planning-for-high-availability-and-disaster-recovery.md). The Backup Service has been running on these paired pools to keep them synchronized.
    
- If the Central Management store is hosted on either pool, it is installed and running on both of the paired pools, with one of those pools hosting the active master and the other pool hosting the standby.
    
> [!IMPORTANT]
>  In the following procedures, the PoolFQDN parameter refers to the FQDN of the pool that is affected by disaster, not the pool that affected users are being redirected from. For the same set of affected users, it refers to the same pool in both failover and failback cmdlets (that is, the pool that first homed the users before the failover). >  For example, assume a case in which all users homed on a pool P1 were failed over to the backup pool, P2. If the administrator wants to move all the users currently serviced by P2 to be serviced by P1, the administrator must perform the following steps: >  Fail back all the users originally homed on P1 from P2 to P1 using the failback cmdlet. In this case, the PoolFQDN is P1's FQDN. >  Fail over all the users originally homed on P2 to P1 using the failover cmdlet. In this case, the PoolFQDN is P2's FQDN. >  If the administrator later wants to fail back those P2 users back to P2, the PoolFQDN is P2's FQDN. >  Note that step 1 above must be performed before step 2 to preserve pool integrity. If you try step 2 before step 1, the step 2 cmdlet will fail. 
  
## In this section

- [Configuring and monitoring the Backup Service in Lync Server 2013](configuring-and-monitoring-the-backup-service.md)
    
- [Failing over a pool in Lync Server 2013](failing-over-a-pool.md)
    
- [Failing back a pool in Lync Server 2013](failing-back-a-pool.md)
    
- [Failing over a mirrored database in Lync Server 2013](failing-over-a-mirrored-database.md)
    
- [Failing over the Edge pool used for Lync Server federation in Lync Server 2013](failing-over-the-edge-pool-used-for-lync-server-federation.md)
    
- [Failing over the Edge pool used for XMPP federation in Lync Server 2013](failing-over-the-edge-pool-used-for-xmpp-federation.md)
    
- [Failing back the Edge pool used for Lync Server federation or XMPP federation in Lync Server 2013](failing-back-the-edge-pool-used-for-lync-server-federation-or-xmpp-federation.md)
    
- [Changing the Edge pool associated with a Front End pool in Lync Server 2013](changing-the-edge-pool-associated-with-a-front-end-pool.md)
    
- [Restoring conference contents using the Backup Service in Lync Server 2013](restoring-conference-contents-using-the-backup-service.md)
    
## See also

#### 

[Planning for high availability and disaster recovery in Lync Server 2013](planning-for-high-availability-and-disaster-recovery.md)

