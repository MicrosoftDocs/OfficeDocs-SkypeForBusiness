---
title: Lync Server 2013 recovery time for pool failover and pool failback
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Recovery time for pool failover and pool failback
ms:assetid: 902c658f-8442-4d0d-b3ad-bf795ecd550d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205079(v=OCS.15)
ms:contentKeyID: 48184786
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Recovery time for pool failover and pool failback in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-10_

For pool failover and pool failback, the engineering target for recovery time objective (RTO) is 30 minutes. This is the time required for the failover to happen, after administrators have determined there was a disaster and initiated the failover procedures. It does not include the time for administrators to assess the situation and make a decision, nor does it include the time for users to sign in again after failover is complete.

For pool failover and pool failback, the engineering target for recovery point objective (RPO) is 30 minutes. This represents the time measure of data that could be lost due to the disaster, due to replication latency of the Backup Service. For example, if a pool goes down at 10:00 A.M., and the RPO is 30 minutes, data written to the pool between 9:30 A.M. and 10:00 A.M.might not have replicated to the backup pool, and would be lost.

All RTO and RPO numbers in this document assume that the two data centers are located within the same world region with high-speed, low-latency transport between the two sites. These numbers are measured for a pool with 40,000 concurrently active users and 200,000 users enabled for Lync with respect to a pre-defined user model where there is no backlog in data replication. They are subject to change based on performance testing and validation.

</div>

<span> </span>

</div>

</div>

</div>

