---
title: "Create network intersite policies in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: b0714aae-55dc-4587-b718-34a03f596b22
description: "Create network inter-site policies, which are used by Enterprise Voice call admission control in Skype for Business Server."
---

# Create network intersite policies in Skype for Business Server
 
Create network inter-site policies, which are used by Enterprise Voice call admission control in Skype for Business Server. 
  
A network inter-site policy defines bandwidth limitations between sites that have direct WAN links between them.
  
> [!IMPORTANT]
> A network inter-site policy is required  *only*  if there is a direct cross link between two network sites.
  
In the example topology North America region, there is a direct link between the Reno and Albuquerque sites. These two sites require an inter-site policy that applies an appropriate bandwidth policy profile. The following example applies the 20Mb_Link profile.
  
### To create a network inter-site policy

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. Run the New-CsNetworkInterSitePolicy cmdlet to create network inter-site policies and apply an appropriate bandwidth policy profile for two sites that have a direct cross link. For example, run:
    
   ```
   New-CsNetworkInterSitePolicy -InterNetworkSitePolicyID Reno_Albuquerque -NetworkSiteID1 Reno -NetworkSiteID2 Albuquerque -BWPolicyProfileID 20Mb_Link
   ```

3. Repeat step 2 as needed to create network inter-site policies for all network sites pairs that have a direct cross link.
    
## See also

[New-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/new-csnetworkintersitepolicy?view=skype-ps)
  
[Get-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/get-csnetworkintersitepolicy?view=skype-ps)
  
[Set-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/set-csnetworkintersitepolicy?view=skype-ps)
  
[Remove-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/remove-csnetworkintersitepolicy?view=skype-ps)
