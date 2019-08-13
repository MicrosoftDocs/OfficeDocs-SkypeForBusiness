---
title: "Connect a Survivable Branch Appliance"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Every Survivable Branch Appliance (SBA) is associated with a Front End pool which serves as a backup registrar for the SBA. When the Front End pool is migrated to Skype for Business Server 2019, the SBA must be disassociated from the Front End pool while the pool is upgraded, Once the pool has been migrated to Skype for Business Server 2019, the SBA can be re-associated with the upgraded Front End pool. This involves deleting the SBA from the legacy topology in Topology Builder and then adding the SBA to the Skype for Business Server 2019 topology. Users homed on the legacy SBA must first be moved to another Front End pool before removing the SBA from the topology. Once the SBA is added to the Skype for Business Server 2019 topology, those users can then be moved back to the SBA. These steps are summarized below:"
---

# Connect a Survivable Branch Appliance

Every Survivable Branch Appliance (SBA) is associated with a Front End pool that serves as a backup registrar for the SBA. When the Front End pool is migrated to Skype for Business Server 2019, the SBA must be disassociated from the Front End pool while the pool is upgraded. After the pool has been migrated to Skype for Business Server 2019, the SBA can be re-associated with the upgraded Front End pool. This involves deleting the SBA from the legacy topology in Topology Builder and then adding the SBA to the Skype for Business Server 2019 topology. Users homed on the legacy SBA must first be moved to another Front End pool before removing the SBA from the topology. After the SBA is added to the Skype for Business Server 2019 topology, those users can be moved back to the SBA. These steps are summarized below:
  
1. Move branch users homed on the legacy SBA to another Front End pool.
    
2. Remove SBA from the legacy topology to disconnect the existing Front End pool as a backup registrar.
    
3. Add SBA to the Skype for Business Server 2019 topology and configure this new Front End pool as the backup registrar. 
    
4. Move the branch users to the new Skype for Business Server 2019 SBA.
    
### Add legacy SBA branch site to your topology

1. Open **Topology Builder**.
    
2. In the left pane, right-click **Branch sites**, and then click **New Branch Site**.
    
3. In the **Define New Branch Site** dialog box, click **Name**, and then type the name of the branch site.
    
4. (Optional) Click **Description**, and then type a meaningful description for the branch site.
    
5. Click **Next**.
    
6. (Optional) In the next **Define New Branch Site** dialog box, do any of the following: 
    
    1. Click **City**, and then type the name of the city in which the branch site is located.
    
    2. Click **State/Region**, and then type the name of the state or region in which the branch site is located.
    
    3. Click **Country Code**, and then type the two-digit calling code for the country/region in which the branch site is located.
    
7. Click **Next**, and then, if you are using a Survivable Branch Appliance or Server at this site, be sure to clear the **Open the New Survivable Wizard when this wizard closes** check box. Click **Finish**.
    
8. To associate the legacy SBA to the Skype for Business Server 2019 Front End pool:
    
    1. Expand the branch site that has been created. 
    
    2. Right-click on legacy version, and then click **New**.
    
    3. Click **Survivable Branch Appliance**.
    
9. Follow the directions in the wizard that opens. For information about wizard items, see    
   <!-- [Define a Survivable Branch Appliance or Server in Lync 2013](https://technet.microsoft.com/en-us/library/gg398280(v=ocs.15).aspx). -->
   <!-- The above link points to un-rebranded 2013 content we will need to discuss rebrand or bring forward -->
    
    > [!NOTE]
    > A Survivable Branch Appliance can only be associated with a Monitoring Store. 
  
10. If you are not using a Survivable Branch Appliance or Server at this site, clear the **Open the New Survivable Wizard when this wizard closes** check box, and then click **Finish**.
    
11. Repeat the previous steps for each branch site you want to add to the topology.
    

