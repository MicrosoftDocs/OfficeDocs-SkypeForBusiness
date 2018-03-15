---
title: "Conferencing load distribution in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5901a076-1b6f-4720-8837-95fc7f3c37f3
description: "Unlike some other dedicated conferencing solutions, Lync Server architecture is a shared-hardware model. This means that the same hardware is shared by many software components, each of which supports different real-time communications. Each type of real-time communications places specific loads on the servers. For example, the Front End Server can run the Session Initiation Protocol (SIP) routing components, web applications (such as Address Book search), Web Conferencing service, A/V Conferencing service, Enterprise Voice applications (for example, Conferencing Attendant application and Response Group application), and Mediation Server. A set of databases on the Front End Server also provide storage and processing for user, contact, presence, conferencing, and voice routing data. With this hardware sharing, components, services, and processes compete for CPU and memory resources, so non-conferencing workloads have a direct impact on server scaling."
---

# Conferencing load distribution in Lync Server 2013
[]
Unlike some other dedicated conferencing solutions, Lync Server architecture is a shared-hardware model. This means that the same hardware is shared by many software components, each of which supports different real-time communications. Each type of real-time communications places specific loads on the servers. For example, the Front End Server can run the Session Initiation Protocol (SIP) routing components, web applications (such as Address Book search), Web Conferencing service, A/V Conferencing service, Enterprise Voice applications (for example, Conferencing Attendant application and Response Group application), and Mediation Server. A set of databases on the Front End Server also provide storage and processing for user, contact, presence, conferencing, and voice routing data. With this hardware sharing, components, services, and processes compete for CPU and memory resources, so non-conferencing workloads have a direct impact on server scaling. 
  
Compared to other hardware port-based conferencing solutions, Lync Server conferencing architecture is a no-reservation model. When a user schedules a meeting, Lync Server creates a record in the conferencing database, which stores conferencing data, but does not reserve any hardware resources for the scheduled meeting ahead of time. Instead, Lync Server has built-in load balancing logic to dynamically allocate conferencing resources on Front End Servers in a way that distributes loads equally across all Front End Servers in the pool. This effectively provisions and utilizes hardware resources, but makes it challenging to support very large meetings (especially without appropriate planning). For example, when a Lync Server 2013 pool is running close to its top capacity, each Front End Server might host approximately 125 average-size meetings. Adding another small meeting would not be a problem, but adding a meeting for 1000 users would be a problem because the Front End Servers would probably not be able to support such a large meeting at the same time as the other 125 meetings.
  

