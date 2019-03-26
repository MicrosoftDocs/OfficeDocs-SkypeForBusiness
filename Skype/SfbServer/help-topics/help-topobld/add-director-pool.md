---
title: "Add Director Pool"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddDirectorPoolPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 751ead48-b97f-4c6f-ba6b-14d446473658
description: "To Define the Director pool FQDN, select either a Multiple computer pool that will consist of two or more Directors in a load-balanced pool, or a Single computer pool. You must also type the fully qualified domain name (FQDN) that will be used to connect to the Director pool or the single Director's FQDN. For a pool of Director computers, this would be the Domain Name System (DNS) entry for the virtual IP of a hardware load balancer or the shared DNS entry for DNS load balancing."
---

# Add Director Pool
 
To **Define the Director pool FQDN**, select either a **Multiple computer pool** that will consist of two or more Directors in a load-balanced pool, or a **Single computer pool**. You must also type the fully qualified domain name (FQDN) that will be used to connect to the Director pool or the single Director's FQDN. For a pool of Director computers, this would be the Domain Name System (DNS) entry for the virtual IP of a hardware load balancer or the shared DNS entry for DNS load balancing.
  
> [!TIP]
> If you plan to implement a Director pool in the future, select **Multiple computer pool**. Even though a pool is defined as two or more computers that are load-balanced, you can create a single computer pool and create a pool FQDN for the single computer. When you are ready to add more computers to the pool later, you must run Topology Builder again to define the new pool member, publish the new topology, and then setup the new Director pool member through the Skype for Business Server Deployment Wizard. You must also add the new pool member to the appropriate load balancers for the pool, for Domain Name System (DNS) load-balancing, or for hardware load balancers. In many cases, you will have both load balancing systems in place. Be sure that you are adding the new member server to both. 
  

