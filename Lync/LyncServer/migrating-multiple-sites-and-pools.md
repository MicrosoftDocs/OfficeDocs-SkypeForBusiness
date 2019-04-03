---
title: Migrating multiple sites and pools
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migrating multiple sites and pools
ms:assetid: a6d726d2-564d-4b39-a97c-5656a673292a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205165(v=OCS.15)
ms:contentKeyID: 48185079
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migrating multiple sites and pools

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-17_

Lync Server 2013 supports multi-site and multi-pool deployments. The process of migrating multiple pools from Lync Server 2010 to Lync Server 2013 requires the following considerations:

1.  After deploying a Lync Server 2013 pilot pool, you need to define a subset of pilot users that will be moved to the Lync Server 2013 pool, and a methodology for validating the functionality of the users. For example, after moving a user to the pilot pool, verify the user’s conference policy has moved to Lync Server 2013.

2.  After deploying an Edge Server in the pilot pool, you need to validate that external users can communicate with the Lync Server 2013 pool.

3.  After transitioning the federated routes from Lync Server 2010 Edge Servers to the pilot Lync Server 2013 Edge Servers, you need to validate that federated users can communicate with the Lync Server 2013 pool.

4.  After moving all the users and non-user contact objects, you need to validate that the Lync Server 2010 pool is empty.

5.  After verifying that the Lync Server 2010 pool is empty, you can then deactivate the pool.
    
    For details about how to deactivate the legacy Lync Server 2010 pool and servers, see [Phase 8: Decommission legacy pools](phase-8-decommission-legacy-pools.md).

</div>

<span> </span>

</div>

</div>

</div>

