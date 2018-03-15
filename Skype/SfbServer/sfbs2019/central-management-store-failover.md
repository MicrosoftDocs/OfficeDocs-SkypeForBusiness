---
title: "Central Management store failover in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f464d715-68a4-462c-9584-00f41ab10db0
description: "The Central Management store contains configuration data about servers and services in your Lync 2013 deployment. It provides a robust, schematized storage of the data needed to define, set up, maintain, administer, describe, and operate a Lync 2013 deployment. It also validates the data to ensure configuration consistency."
---

# Central Management store failover in Lync Server 2013
[]
The Central Management store contains configuration data about servers and services in your Lync 2013 deployment. It provides a robust, schematized storage of the data needed to define, set up, maintain, administer, describe, and operate a Lync 2013 deployment. It also validates the data to ensure configuration consistency.
  
Each Lync deployment includes one Central Management store, which is hosted by the Back End Server of one Front End pool. 
  
When you establish a pool pairing that includes the pool hosting the Central Management store, a backup Central Management store database is set up in the backup pool, and Central Management store services are installed in both pools. At any point in time, one of the two Central Management store databases is the active master, and the other is a standby. The content is replicated by the Backup Service from the active master to the standby.
  
During a pool failover that involves the pools hosting the Central Management store, the administrator must fail over the Central Management store before failing over the Front End pool.
  
After the disaster is repaired, it is not necessary to fail back the Central Management store. After repair, the Central Management store in the original backup pool can remain as the active master. 
  
The engineering targets for Central Management store failover are 5 minutes for recovery time objective (RTO) and 5 minutes for recovery point objective (RPO).
  

