---
title: Lync Server 2013 Central Management store failover
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Central Management store failover
ms:assetid: f464d715-68a4-462c-9584-00f41ab10db0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205376(v=OCS.15)
ms:contentKeyID: 48185809
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Central Management store failover in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-18_

The Central Management store contains configuration data about servers and services in your Lync 2013 deployment. It provides a robust, schematized storage of the data needed to define, set up, maintain, administer, describe, and operate a Lync 2013 deployment. It also validates the data to ensure configuration consistency.

Each Lync deployment includes one Central Management store, which is hosted by the Back End Server of one Front End pool.

When you establish a pool pairing that includes the pool hosting the Central Management store, a backup Central Management store database is set up in the backup pool, and Central Management store services are installed in both pools. At any point in time, one of the two Central Management store databases is the active master, and the other is a standby. The content is replicated by the Backup Service from the active master to the standby.

During a pool failover that involves the pools hosting the Central Management store, the administrator must fail over the Central Management store before failing over the Front End pool.

After the disaster is repaired, it is not necessary to fail back the Central Management store. After repair, the Central Management store in the original backup pool can remain as the active master.

The engineering targets for Central Management store failover are 5 minutes for recovery time objective (RTO) and 5 minutes for recovery point objective (RPO).

</div>

<span> </span>

</div>

</div>

</div>

