---
title: "Migrating multiple sites and pools"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Skype for Business Server 2019 supports multi-site and multi-pool deployments. The process of migrating multiple pools to Skype for Business Server 2019 requires the following considerations:"
---

# Migrating multiple sites and pools

Skype for Business Server 2019 supports multi-site and multi-pool deployments. The process of migrating multiple pools to Skype for Business Server 2019 requires the following considerations: 
  
1. After deploying a Skype for Business Server 2019 pilot pool, you need to define a subset of pilot users that will be moved to the Skype for Business Server 2019 pool, and a methodology for validating the functionality of the users. For example, after moving a user to the pilot pool, verify that the user's conference policy has moved to Skype for Business Server 2019. 
    
2. After deploying an Edge Server in the pilot pool, you need to validate that external users can communicate with the Skype for Business Server 2019 pool.

3. Persistent Chat, SQL Mirroring, and XMPP functionality are deprecated in Skype for Business Server 2019 and no longer available as Skype for Business Server 2019 features, but they can be continued in a coexistence environment if they were previously deployed in a legacy environment. If you want to continue using these features, you should plan to continue with a coexistence environment where certain users will remain in legacy pools.
    
4. After transitioning the federated routes' Edge Servers to the pilot Skype for Business Server 2019 Edge Servers, you need to validate that federated users can communicate with the Skype for Business Server 2019 pool.
    
5. After moving all users and non-user contact objects, you need to validate that the legacy pool is empty.
    
6. After verifying that the legacy pool is empty, you can then deactivate the pool. 
    
    For details about how to deactivate the legacy pool and servers, see [Phase 8: Decommission legacy pools](phase-8-decommission-legacy-pools.md).
    

