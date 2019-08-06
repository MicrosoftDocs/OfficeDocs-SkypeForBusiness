---
title: "Add a location policy to a network site in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 43bfab8a-3d6b-4ca4-8425-879fd910502e
description: "Assign E9-1-1 location policies to network sites in Skype for Business Server Enterprise Voice."
---

# Add a location policy to a network site in Skype for Business Server
 
Assign E9-1-1 location policies to network sites in Skype for Business Server Enterprise Voice. 
  
The following examples show how to add the **Redmond** location policy defined in [Create location policies in Skype for Business Server](create-location-policies.md) to an existing network site and how to create a new network site that uses the **Redmond** location policy.
  
For details about working with network sites, see the Lync Server Management Shell documentation for the following cmdlets:
  
- **New-CsNetworkSite**
    
- **Get-CsNetworkSite**
    
- **Set-CsNetworkSite**
    
- **Remove-CsNetworkSite**
    
### To assign a location policy to an existing network site

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. Run the following cmdlets to modify an existing network site.
    
    Assign the **Redmond** tagged Location policy to an existing network site named **Redmond**.
    
   ```
   Set-CsNetworkSite -Identity "Redmond" -NetworkRegionID "NorthAmerica" -LocationPolicy "Redmond"
   ```

### To assign a location policy to a new network site

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. Run the following cmdlet to create a new network site.
    
    Create a new network site in the network region and assign the **Redmond** tagged Location policy.
    
   ```
   New-CsNetworkSite -Identity "Redmond" -NetworkRegionID "NorthAmerica" -LocationPolicy "Redmond"
   ```


