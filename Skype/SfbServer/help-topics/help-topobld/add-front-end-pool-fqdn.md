---
title: "Add Front End Pool FQDN"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddFrontEndPoolPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 02ae996c-a1c6-4ff4-b6d6-bdef4ad44d2a
description: "Specify the fully qualified domain name (FQDN) of the Front End pool that you are creating. You cannot change the FQDN of a pool after you publish the topology containing the Front End pool. If you need to rename a pool, you must delete the pool and then add a new pool with the new FQDN."
---

# Add Front End Pool FQDN
 
Specify the fully qualified domain name (FQDN) of the Front End pool that you are creating. You cannot change the FQDN of a pool after you publish the topology containing the Front End pool. If you need to rename a pool, you must delete the pool and then add a new pool with the new FQDN.
  
> [!TIP]
> If you plan to implement a Front End pool in the future, select **Multiple computer pool**. Even though a pool is defined as two or more computers that are load balanced, you can create a single computer pool and create a pool FQDN for the single computer. When you are ready to add more computers to the pool later, you must run Topology Builder again to define the new pool member, publish the new topology, and then set up the new Front End pool member through the Skype for Business Server Deployment Wizard. You must also add the new pool member to the appropriate load balancers for the pool, Domain Name System (DNS) load balancing, or hardware load balancers. In many cases, you would have both load balancing systems in place. Be sure that you are adding the new member server to both. 
  

