---
title: "Migrating multiple sites and pools"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a6d726d2-564d-4b39-a97c-5656a673292a
description: "Lync Server 2013 supports multi-site and multi-pool deployments. The process of migrating multiple pools from Lync Server 2010 to Lync Server 2013 requires the following considerations:"
---

# Migrating multiple sites and pools
[]
Lync Server 2013 supports multi-site and multi-pool deployments. The process of migrating multiple pools from Lync Server 2010 to Lync Server 2013 requires the following considerations: 
  
1. After deploying a Lync Server 2013 pilot pool, you need to define a subset of pilot users that will be moved to the Lync Server 2013 pool, and a methodology for validating the functionality of the users. For example, after moving a user to the pilot pool, verify the user's conference policy has moved to Lync Server 2013. 
    
2. After deploying an Edge Server in the pilot pool, you need to validate that external users can communicate with the Lync Server 2013 pool.
    
3. After transitioning the federated routes from Lync Server 2010 Edge Servers to the pilot Lync Server 2013 Edge Servers, you need to validate that federated users can communicate with the Lync Server 2013 pool.
    
4. After moving all the users and non-user contact objects, you need to validate that the Lync Server 2010 pool is empty.
    
5. After verifying that the Lync Server 2010 pool is empty, you can then deactivate the pool. 
    
    For details about how to deactivate the legacy Lync Server 2010 pool and servers, see [Phase 8: Decommission legacy pools](phase-8-decommission-legacy-pools.md).
    

