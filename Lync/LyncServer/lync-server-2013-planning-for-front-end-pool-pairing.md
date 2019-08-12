---
title: 'Lync Server 2013: Planning for Front End pool pairing'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Planning for Front End pool pairing
ms:assetid: cca5773d-57ff-45ce-a7b4-f82ae697c477
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205293(v=OCS.15)
ms:contentKeyID: 48185508
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for Front End pool pairing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

For the best disaster recovery abilities in Lync Server 2013, deploy pairs of Front End pools across two geographically dispersed sites. Each site contains a Front End pool which is paired with a corresponding Front End pool in the other site. Both sites are active, and the Lync Server Backup Service provides real-time data replication to keep the pools synchronized. The Backup Service is a new feature in Lync Server 2013, designed to support the disaster recovery solution. It is installed on a Front End pool when you pair the pool with another Front End pool.

If the pool in one site fails, you can fail over the users from that pool to the pool in the other site, which then provides services to all the users in both pools. For capacity planning purposes, each pool should be designed to handle the workloads of all users in both pools in the event of a disaster.

<div>

## In This Section

  - [Supported pool pairing options and best practices for Lync Server 2013](lync-server-2013-supported-pool-pairing-options-and-best-practices.md)

  - [Backup Registrar relationships in Lync Server 2013](lync-server-2013-backup-registrar-relationships.md)

  - [Recovery time for pool failover and pool failback in Lync Server 2013](lync-server-2013-recovery-time-for-pool-failover-and-pool-failback.md)

  - [Central Management store failover in Lync Server 2013](lync-server-2013-central-management-store-failover.md)

  - [Front End pool pairing data security in Lync Server 2013](lync-server-2013-front-end-pool-pairing-data-security.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

