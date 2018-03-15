---
title: "Connecting Survivable Branch Appliance to Lync Server 2013 Front End pool"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3c7ca33f-5295-4d82-9152-41d8bc6f35cf
description: "Every Survivable Branch Appliance (SBA) is associated with a Front End pool, which serves as a backup Registrar for the SBA. When the Front End pool is upgraded to Lync Server 2013, the SBA must be disassociated from the Front End pool while the Front End pool is upgraded. After the Front End pool is upgraded, the SBA can be reassociated with the Front End pool. This involves deleting the SBA from the topology in Topology Builder and then adding the SBA, again, to Topology Builder. Users homed on the SBA must be moved to another Front End pool before removing the SBA from the topology. After the SBA is added back to the topology, those users can be moved back to the SBA."
---

# Connecting Survivable Branch Appliance to Lync Server 2013 Front End pool
[]
Every Survivable Branch Appliance (SBA) is associated with a Front End pool, which serves as a backup Registrar for the SBA. When the Front End pool is upgraded to Lync Server 2013, the SBA must be disassociated from the Front End pool while the Front End pool is upgraded. After the Front End pool is upgraded, the SBA can be reassociated with the Front End pool. This involves deleting the SBA from the topology in Topology Builder and then adding the SBA, again, to Topology Builder. Users homed on the SBA must be moved to another Front End pool before removing the SBA from the topology. After the SBA is added back to the topology, those users can be moved back to the SBA.
  
These steps are summarized below:
  
1. Move branch users homed on SBA to another Front End pool.
    
2. Remove SBA from your topology to disassociate the existing Front End pool as the backup Registrar.
    
3. Upgrade Front End pool to Microsoft Lync Server 2013.
    
4. Add SBA back into your topology.
    
5. Associate the new Front End pool to the SBA as a backup Registrar.
    
6. Move branch users back to the SBA.
    
## In this section

- [Add Lync Server 2013 Survivable Branch Appliance branch site to your topology](add-lync-server-2013-survivable-branch-appliance-branch-site-to-your-topology.md)
    
- [Add Lync Server 2010 Survivable Branch Appliance branch site to your topology](add-lync-server-2010-survivable-branch-appliance-branch-site-to-your-topology.md)
    

