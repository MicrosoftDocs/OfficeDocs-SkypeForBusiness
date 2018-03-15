---
title: "Backing up and restoring Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 07dc1f5e-af66-4e18-bf39-881dceff8bc3
description: "In this section, you'll find the best practices for backing up your Lync Server 2013 data, and for restoring it if you have a failure. These best practices apply to the following situations:"
---

# Backing up and restoring Lync Server 2013
[]
In this section, you'll find the best practices for backing up your Lync Server 2013 data, and for restoring it if you have a failure. These best practices apply to the following situations:
  
- An entire Lync Server pool of any type (Front End Server, Edge Server, Mediation Server, Persistent Chat Server, or Director), or an individual server in one of these pools.
    
- The Central Management Server
    
- A Standard Edition server
    
- An Enterprise Edition Back End Server
    
- A File Store
    
- An Archiving database, Monitoring database, or Persistent Chat database
    
This section does not include information about restoring an entire site or for developing a standby site. For details about developing a disaster recovery solution with paired Front End pools, see [Planning for high availability and disaster recovery in Lync Server 2013](planning-for-high-availability-and-disaster-recovery.md). This is the recommended method for planning for disaster recovery.
  
If you have deployed paired Front End pools, if one of these pools fails and becomes unrecoverable, you can restore this pool with a new fully qualified domain name (FQDN) from its paired pool. For details on the steps to perform this recovery, see [Failing over a pool in Lync Server 2013](failing-over-a-pool.md). Additionally, if you later want to recreate a failed and unrecoverable pool that was part of a Front End pair, you can use the steps in [Performing an ABC Front End pool failover in Lync Server 2013](performing-an-abc-front-end-pool-failover.md).
  
The methodology described in this document involves special considerations during the planning phase. For details, see [Establishing a backup and restoration plan for Lync Server 2013](establishing-a-backup-and-restoration-plan.md).
  
## In this section

- [Preparing for Lync Server 2013 backup and restoration](preparing-for-lync-server-backup-and-restoration.md)
    
- [Backing up data and settings in Lync Server 2013](backing-up-data-and-settings.md)
    
- [Restoring data and settings in Lync Server 2013](restoring-data-and-settings.md)
    
- [Backup and restoration worksheets for Lync Server 2013](backup-and-restoration-worksheets.md)
    

