---
title: Lync Server 2013 backup Registrar relationships
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Backup Registrar relationships
ms:assetid: 7e078271-84b9-4666-989c-c4507a0cdf4a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205033(v=OCS.15)
ms:contentKeyID: 48184631
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Backup Registrar relationships in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-28_

In addition to providing disaster recovery ability, two paired pools serve as the backup Registrars for each other. In Lync Server 2013, backup Registrar relationships between Front End pools are always 1:1 and reciprocal. This means that if P1 is the backup for P2, then P2 must be the backup for P1, and neither can be the backup for any other Front End pool. This is a change from Lync Server 2010, in which Front End pool backup relationships could be many to one.

Even though backup relationships between two Front End pools must be 1:1 and symmetrical, each Front End pool can still also be the backup registrar for any number of Survivable Branch Appliances, just as in Lync Server 2010.

Note that Lync Server 2013 does not extend disaster recovery support to users homed on a Survivable Branch Appliance. If a Front End pool that serves as the backup for a Survivable Branch Appliance goes down, users signed into the Survivable Branch Appliance fall into resiliency mode even after users homed on the Front End pool are failed over to the backup Front End pool.

</div>

<span> </span>

</div>

</div>

</div>

