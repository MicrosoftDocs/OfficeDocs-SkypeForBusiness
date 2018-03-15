---
title: "Configure network regions for CAC in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ea3ff988-dd5a-4bc4-bec5-39a0fb09793a
description: "Network regions are the network hubs or backbones that are used in configuring CAC, E9-1-1, and media bypass. Use the following procedure to create network regions that align to network regions in the example network topology for CAC. To view the example network topology, see Example: Gathering your requirements for call admission control in Lync Server 2013 in the Planning documentation."
---

# Configure network regions for CAC in Lync Server 2013
[]
> [!IMPORTANT]
> If you have already created network regions for E9-1-1 or media bypass, you can modify the existing network regions by adding settings specific to call admission control (CAC) by using the **Set-CsNetworkRegion** cmdlet. For an example of how to modify a network region, see [Create or modify a network region in Lync Server 2013](create-or-modify-a-network-region.md). 
  
Network regions are the network hubs or backbones that are used in configuring CAC, E9-1-1, and media bypass. Use the following procedure to create network regions that align to network regions in the example network topology for CAC. To view the example network topology, see [Example: Gathering your requirements for call admission control in Lync Server 2013](example-gathering-your-organization-s-requirements-for-call-admission-control.md) in the Planning documentation. 
  
The example network topology for CAC has three regions: North America, EMEA, and APAC. Each region has a specified central site. For the North America region, the designated central site is named CHICAGO. The following procedure shows an example of how you can use the **New-CsNetworkRegion** cmdlet to create the North America region. 
  
> [!NOTE]
> In the following procedure, Lync Server Management Shell is used to create a network region. For details about using Lync Server Control Panel to create a network region, see [Create or modify a network region in Lync Server 2013](create-or-modify-a-network-region.md). 
  
### To create a network region for call admission control

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. For each region that you need to create, run the **New-CsNetworkRegion** cmdlet. For example, to create the North America region, run: 
    
  ```
  New-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "All North America Locations"
  ```

3. Repeat step 2 to create the network regions, EMEA and APAC.
    

