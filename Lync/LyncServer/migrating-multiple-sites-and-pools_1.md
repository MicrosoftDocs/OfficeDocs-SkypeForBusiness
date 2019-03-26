---
title: Migrating multiple sites and pools
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migrating multiple sites and pools
ms:assetid: 3bf677d4-a5af-4f73-8fad-1abf5b668cc1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688025(v=OCS.15)
ms:contentKeyID: 49733615
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

_**Topic Last Modified:** 2012-08-26_

Lync Server 2013 supports multi-site and multi-pool deployments. The process of migrating multiple pools from Office Communications Server 2007 R2 to Lync Server 2013 requires the following considerations:

1.  After deploying a Lync Server 2013 pilot pool, you need to define a subset of pilot users that will be moved to the Lync Server 2013 pool, and a methodology for validating the functionality of the users.

2.  After deploying an Edge Server in the pilot pool, you need to validate that external users can communicate with the Lync Server 2013 pool.

3.  After transitioning the federated routes from Office Communications Server 2007 R2 Edge Servers to the pilot Lync Server 2013 Edge Servers, you need to validate that federated users can communicate with the Lync Server 2013 pool.

4.  After moving all the users and non-user contact objects, you need to validate that the Office Communications Server 2007 R2 pool is empty.

5.  After verifying that the Office Communications Server 2007 R2 pool is empty, you can then deactivate the pool.
    
    For details about how to deactivate the legacy Office Communications Server 2007 R2 pool and servers, see [Phase 10: Decommission legacy site](phase-10-decommission-legacy-site.md).

</div>

<span> </span>

</div>

</div>

</div>

