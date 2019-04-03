---
title: Lync Server 2013 topology changes
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Topology changes
ms:assetid: 9e40ef93-9ab0-498c-9bbf-f94584353e53
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688153(v=OCS.15)
ms:contentKeyID: 49733756
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Topology changes in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-02_

Topology requirements and considerations for Lync Server 2013 are different from those for earlier releases, as described in this section.

<div>

## New Front End Pools Architecture

In Lync Server 2013, the architecture of Enterprise Edition Front End pools has changed to a distributed systems architecture.

With this new architecture, the Back End database is no longer the real-time data store in a pool. Information about a particular user is kept on three Front End Servers in the pool. For each user, one Front End Server acts as the master for that user’s information, and two other Front End Servers serve as replicas. If a Front End Server goes down, another Front End Server which served as a replica is automatically promoted to master.

This happens behind the scenes, and administrators do not need to know which Front End Servers are the masters for which users. This distribution of data storage improves performance and scalability within the pool, and eliminates the single point of failure of a single Back End Server.

The Back End Server serves as backup storage for user and conference data, and is also the primary storage for other databases such as the Response Group database.

These improvements also mean there are changes in how you plan and maintain your pools. We recommend that all your Enterprise Edition Front End pools include at least three Front End Servers, to provide the full number of replicas that the Front End pool architecture is designed for. Additionally, you must follow certain procedures when adding servers to a Front End pool, removing servers from it, or upgrading servers. For more information, see [Topologies and components for Front End Servers, instant messaging, and presence in Lync Server 2013](lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md).

<div>

## Server Role Topology Changes

Some server roles that previously ran on separate servers are now consolidated into the Front End Server role, enabling you to save on hardware costs

  - In Lync Server 2013, A/V Conferencing Server is always collocated with Front End Server.

  - The front ends for both Monitoring and Archiving are now always collocated with Front End Server. Monitoring and Archiving each still require a separate Back-End Database, which can be collocated on the same server as the Front End Pool’s back-end database, or can be hosted on separate Back-End Servers.

  - Persistent Chat Server is now a server role. In Microsoft Lync Server 2010, Group Chat Server was a third-party trusted application for Microsoft Lync Server 2010. In Lync Server 2013, Persistent Chat Server functionality is implemented using three new server roles:
    
      - **PersistentChatService:** Main Persistent Chat Server services implemented as a front end role
    
      - **PersistentChatStore:** Back End Server role
    
      - **PersistentChatComplianceStore:** Back End Server role for Persistent Chat Compliance

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

