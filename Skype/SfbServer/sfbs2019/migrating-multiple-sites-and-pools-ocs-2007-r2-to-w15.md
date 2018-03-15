---
title: "Migrating multiple sites and pools [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3bf677d4-a5af-4f73-8fad-1abf5b668cc1
description: "Lync Server 2013 supports multi-site and multi-pool deployments. The process of migrating multiple pools from Office Communications Server 2007 R2 to Lync Server 2013 requires the following considerations:"
---

# Migrating multiple sites and pools [OCS 2007 R2 to W15]
[]
Lync Server 2013 supports multi-site and multi-pool deployments. The process of migrating multiple pools from Office Communications Server 2007 R2 to Lync Server 2013 requires the following considerations: 
  
1. After deploying a Lync Server 2013 pilot pool, you need to define a subset of pilot users that will be moved to the Lync Server 2013 pool, and a methodology for validating the functionality of the users.
    
2. After deploying an Edge Server in the pilot pool, you need to validate that external users can communicate with the Lync Server 2013 pool.
    
3. After transitioning the federated routes from Office Communications Server 2007 R2 Edge Servers to the pilot Lync Server 2013 Edge Servers, you need to validate that federated users can communicate with the Lync Server 2013 pool.
    
4. After moving all the users and non-user contact objects, you need to validate that the Office Communications Server 2007 R2 pool is empty.
    
5. After verifying that the Office Communications Server 2007 R2 pool is empty, you can then deactivate the pool. 
    
    For details about how to deactivate the legacy Office Communications Server 2007 R2 pool and servers, see [Phase 10: Decommission legacy site [OCS 2007 R2 to W15]](phase-10-decommission-legacy-site-ocs-2007-r2-to-w15.md).
    

