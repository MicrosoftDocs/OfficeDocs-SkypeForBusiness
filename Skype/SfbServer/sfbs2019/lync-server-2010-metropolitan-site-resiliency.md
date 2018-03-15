---
title: "Lync Server 2010 metropolitan site resiliency"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 18673ff6-b664-4a57-a89b-cbda8b129e6a
description: "The metropolitan site resiliency solution supported for Lync Server 2010 is not supported for Lync Server 2013. This solution involved spanning a single Front End pool across two data centers in the same metropolitan area."
---

# Lync Server 2010 metropolitan site resiliency
[]
The metropolitan site resiliency solution supported for Lync Server 2010 is not supported for Lync Server 2013. This solution involved spanning a single Front End pool across two data centers in the same metropolitan area.
  
The metropolitan site resiliency solution was designed to recover from the loss of a full datacenter. When you span your pool across two datacenters, you typically put half of your front ends in one datacenter and the other half in the second datacenter. If you lose an entire datacenter, you have lost half of your Front End Servers. This can cause issues with the new distributed system model for Front End Pools in Lync Server 2013. For more information, see [Topologies and components for Front End Servers, instant messaging, and presence in Lync Server 2013](topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md).
  

