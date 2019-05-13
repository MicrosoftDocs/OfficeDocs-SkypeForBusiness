---
title: Migration phases
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migration phases
ms:assetid: cb7747ba-b872-42ca-ab41-76e3c4e77d06
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205336(v=OCS.15)
ms:contentKeyID: 48185642
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migration phases

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-17_

In Lync Server 2013, you define sites on your network that contain Lync Server 2013 components. A site is a set of computers that are well-connected by a high-speed, low-latency network, such as a single local area network (LAN) or two networks connected by a high-speed fiber optic network.

A *Front End pool* is a set of Front End Servers that are configured identically and work together to provide services for a common group of users. A pool provides scalability and failover capability to your users. Each server in a pool must run an identical server role or roles. A Standard Edition server, designed for small organizations, also defines a pool and runs on a single server. This enables you to have Lync Server 2013 functionality for a lesser cost, but does not provide a true high-availability solution.

The following phases describe the process of a pool migration from Lync Server 2010 to Lync Server 2013. For multiple sites containing multiple pools, each individual pool should follow this phased approach.

1.  [Phase 1: Plan your migration from Lync Server 2010](phase-1-plan-your-migration-from-lync-server-2010.md)

2.  [Phase 2: Prepare for migration](phase-2-prepare-for-migration.md)

3.  [Phase 3: Deploy Lync Server 2013 pilot pool](phase-3-deploy-lync-server-2013-pilot-pool.md)

4.  [Phase 4: Move test users to the pilot pool](phase-4-move-test-users-to-the-pilot-pool.md)

5.  [Phase 5: Add Lync Server 2013 Edge Server to pilot pool](phase-5-add-lync-server-2013-edge-server-to-pilot-pool.md)

6.  [Phase 6: Move from pilot deployment into production](phase-6-move-from-pilot-deployment-into-production.md)

7.  [Phase 7: Complete post-migration tasks](phase-7-complete-post-migration-tasks.md)

8.  [Phase 8: Decommission legacy pools](phase-8-decommission-legacy-pools.md)

</div>

<span> </span>

</div>

</div>

</div>

