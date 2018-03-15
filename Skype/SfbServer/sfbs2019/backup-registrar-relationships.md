---
title: "Backup Registrar relationships in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7e078271-84b9-4666-989c-c4507a0cdf4a
description: "In addition to providing disaster recovery ability, two paired pools serve as the backup Registrars for each other. In Lync Server 2013, backup Registrar relationships between Front End pools are always 1:1 and reciprocal. This means that if P1 is the backup for P2, then P2 must be the backup for P1, and neither can be the backup for any other Front End pool. This is a change from Lync Server 2010, in which Front End pool backup relationships could be many to one."
---

# Backup Registrar relationships in Lync Server 2013
[]
In addition to providing disaster recovery ability, two paired pools serve as the backup Registrars for each other. In Lync Server 2013, backup Registrar relationships between Front End pools are always 1:1 and reciprocal. This means that if P1 is the backup for P2, then P2 must be the backup for P1, and neither can be the backup for any other Front End pool. This is a change from Lync Server 2010, in which Front End pool backup relationships could be many to one.
  
Even though backup relationships between two Front End pools must be 1:1 and symmetrical, each Front End pool can still also be the backup registrar for any number of Survivable Branch Appliances, just as in Lync Server 2010.
  
Note that Lync Server 2013 does not extend disaster recovery support to users homed on a Survivable Branch Appliance. If a Front End pool that serves as the backup for a Survivable Branch Appliance goes down, users signed into the Survivable Branch Appliance fall into resiliency mode even after users homed on the Front End pool are failed over to the backup Front End pool.
  

