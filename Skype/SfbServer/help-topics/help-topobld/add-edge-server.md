---
title: "Add Edge Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/25/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddEdgeServerPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9bd9c2b2-8329-4b31-a937-e462f5cc7293
description: "To incorporate an Edge Server or an Edge Server pool into your topology design, you need to specify the fully qualified domain name (FQDN) of the server on which you want to deploy Edge Server or Edge Server pool. Prior to publishing a topology that includes the Edge Server or Edge Server pool and installing Skype for Business Server, you should have completed all prerequisites for deploying external user access. For details about these prerequisites, see Preparing for Installation of Servers in the Perimeter Network in the Deployment documentation."
---

# Add Edge Server

To incorporate an Edge Server or an Edge Server pool into your topology design, you need to specify the fully qualified domain name (FQDN) of the server on which you want to deploy Edge Server or Edge Server pool. Prior to publishing a topology that includes the Edge Server or Edge Server pool and installing Skype for Business Server, you should have completed all prerequisites for deploying external user access. For details about these prerequisites, see [Preparing for Installation of Servers in the Perimeter Network](https://technet.microsoft.com/library/5e6c457a-f964-4ef7-a709-97abda9c673a.aspx) in the Deployment documentation.

> [!IMPORTANT]
> The name you specify must be identical to the computer name configured on the server. By default, the computer name of a computer that is not joined to a domain is a short name, not an FQDN. Topology Builder uses FQDNs, not short names. You must configure a Domain Name System (DNS) suffix on the name of the computer to be deployed as an Edge Server or Edge Server pool that is not joined to a domain.

> [!TIP]
> If you plan to implement an Edge Server pool in the future, select **Multiple computer pool**. Even though a pool is defined as two or more computers that are load balanced, you can create a single computer pool and create a pool FQDN for the single computer. When you are ready to add more computers to the pool later, you must Topology Builder again to define the new pool member, publish the new topology, and then set up the new Edge Server pool member through the Skype for Business Server Deployment Wizard. You must also add the new pool member to the appropriate load balancers for the pool, DNS load balancing or hardware load balancers. The internal Edge interface and external Edge interface must use the same type of load balancing. You cannot use DNS load balancing on one Edge interface and hardware load balancing on the other Edge interface. Be sure that you are adding the new member server to the appropriate load balancer.

You can add support for external user access when you deploy your initial topology, or after you deploy your initial topology. For details about adding Edge Servers or Edge Server pool to an existing topology, see [Define Your Edge Topology](https://technet.microsoft.com/library/787b23f1-8fa0-4c37-abf2-c516c5dd66f0.aspx) in the Edge Server Deployment documentation.


