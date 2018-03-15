---
title: "Create network intersite policies in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b0714aae-55dc-4587-b718-34a03f596b22
description: "A network intersite policy defines bandwidth limitations between sites that have direct WAN links between them."
---

# Create network intersite policies in Lync Server 2013
[]
A network intersite policy defines bandwidth limitations between sites that have direct WAN links between them. 
  
For details, see the Lync Server Management Shell documentation for the following cmdlets:
  
- [New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)
    
- [Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)
    
- [Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)
    
- [Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)
    
> [!IMPORTANT]
> A network intersite policy is required  *only*  if there is a direct cross link between two network sites. 
  
In the example topology North America region, there is a direct link between the Reno and Albuquerque sites. These two sites require an intersite policy that applies an appropriate bandwidth policy profile. The following example applies the 20Mb_Link profile.
  
### To create a network intersite policy

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the New-CsNetworkInterSitePolicy cmdlet to create network intersite policies and apply an appropriate bandwidth policy profile for two sites that have a direct cross link. For example, run:
    
  ```
  New-CsNetworkInterSitePolicy -InterNetworkSitePolicyID Reno_Albuquerque -NetworkSiteID1 Reno -NetworkSiteID2 Albuquerque -BWPolicyProfileID 20Mb_Link
  ```

3. Repeat step 2 as needed to create network intersite policies for all network sites pairs that have a direct cross link.
    

