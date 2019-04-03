---
title: 'Connecting Survivable Branch Appliance to Lync Server 2013 Front End pool'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Connecting Survivable Branch Appliance to Lync Server 2013 Front End pool
ms:assetid: 3c7ca33f-5295-4d82-9152-41d8bc6f35cf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688026(v=OCS.15)
ms:contentKeyID: 49733616
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Connecting Survivable Branch Appliance to Lync Server 2013 Front End pool

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-05_

Every Survivable Branch Appliance (SBA) is associated with a Front End pool, which serves as a backup Registrar for the SBA. When the Front End pool is upgraded to Lync Server 2013, the SBA must be disassociated from the Front End pool while the Front End pool is upgraded. After the Front End pool is upgraded, the SBA can be reassociated with the Front End pool. This involves deleting the SBA from the topology in Topology Builder and then adding the SBA, again, to Topology Builder. Users homed on the SBA must be moved to another Front End pool before removing the SBA from the topology. After the SBA is added back to the topology, those users can be moved back to the SBA.

These steps are summarized below:

1.  Move branch users homed on SBA to another Front End pool.

2.  Remove SBA from your topology to disassociate the existing Front End pool as the backup Registrar.

3.  Upgrade Front End pool to Microsoft Lync Server 2013.

4.  Add SBA back into your topology.

5.  Associate the new Front End pool to the SBA as a backup Registrar.

6.  Move branch users back to the SBA.

<div>

## In This Section

  - [Add Lync Server 2013 Survivable Branch Appliance branch site to your topology](lync-server-2013-add-lync-server-2013-survivable-branch-appliance-branch-site-to-your-topology.md)

  - [Add Lync Server 2010 Survivable Branch Appliance branch site to your topology](lync-server-2013-add-lync-server-2010-survivable-branch-appliance-branch-site-to-your-topology.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

