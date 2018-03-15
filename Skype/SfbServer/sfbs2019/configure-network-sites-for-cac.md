---
title: "Configure network sites for CAC in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: afcea38f-5789-45ec-97af-c6e38364950c
description: "Network sites are the offices or locations within each network region of call admission control (CAC), E9-1-1, and media bypass deployments. Use the following procedures to create network sites that align to network sites in the example network topology for CAC. These procedures show how to create and configure network sites that are constrained by WAN bandwidth and therefore require bandwidth policies that limit real-time audio or video traffic flow."
---

# Configure network sites for CAC in Lync Server 2013
[]
> [!IMPORTANT]
> If you have already created network sites for E9-1-1 or media bypass, you can modify the existing network sites to apply a bandwidth policy profile by using the **Set-CsNetworkSite** cmdlet. For an example of how to modify a network site, see [Create or modify a network site in Lync Server 2013](create-or-modify-a-network-site.md). 
  
Network sites are the offices or locations within each network region of call admission control (CAC), E9-1-1, and media bypass deployments. Use the following procedures to create network sites that align to network sites in the example network topology for CAC. These procedures show how to create and configure network sites that are constrained by WAN bandwidth and therefore require bandwidth policies that limit real-time audio or video traffic flow. 
  
In the example CAC deployment, the North America region has six sites. Three of these sites are constrained by WAN bandwidth: Reno, Portland, and Albuquerque. The other three sites, which are  *not*  constrained by WAN bandwidth: New York, Chicago, and Detroit. For an example of how to create or modify those other network sites, see [Create or modify a network site in Lync Server 2013](create-or-modify-a-network-site.md).
  
To view the example network topology, see [Example: Gathering your requirements for call admission control in Lync Server 2013](example-gathering-your-organization-s-requirements-for-call-admission-control.md) in the Planning documentation. 
  
> [!NOTE]
> In the following procedure, Lync Server Management Shell is used to create a network site. For details about using Lync Server Control Panel to create a network site, see [Create or modify a network site in Lync Server 2013](create-or-modify-a-network-site.md). 
  
### To create network sites for call admission control

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the **New-CsNetworkSite** cmdlet to create network sites and apply an appropriate bandwidth policy profile to each site. For example, run: 
    
  ```
  New-CsNetworkSite -NetworkSiteID Reno -Description "NA:Branch office for sales force" -NetworkRegionID NorthAmerica -BWPolicyProfileID 10MB_Link
  ```

  ```
  New-CsNetworkSite -NetworkSiteID Portland -Description "NA:Branch office for marketing force" -NetworkRegionID NorthAmerica -BWPolicyProfileID 5MB_Link
  ```

  ```
  New-CsNetworkSite -NetworkSiteID Albuquerque -Description "NA:Branch office for SouthWest sales" -NetworkRegionID EMEA -BWPolicyProfileID 10MB_Link
  ```

3. To finish creating network sites for the entire example topology, repeat step 2 for the bandwidth-constrained network sites in the EMEA and APAC regions.
    

