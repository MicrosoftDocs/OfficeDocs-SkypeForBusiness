---
title: "Add a location policy to a network site in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 43bfab8a-3d6b-4ca4-8425-879fd910502e
description: "The following examples show how to add the Redmond location policy defined in Create location policies in Lync Server 2013 to an existing network site and how to create a new network site that uses the Redmond location policy."
---

# Add a location policy to a network site in Lync Server 2013
[]
The following examples show how to add the **Redmond** location policy defined in [Create location policies in Lync Server 2013](create-location-policies.md) to an existing network site and how to create a new network site that uses the **Redmond** location policy. 
  
For details about working with network sites, see the Lync Server Management Shell documentation for the following cmdlets:
  
- **New-CsNetworkSite**
    
- **Get-CsNetworkSite**
    
- **Set-CsNetworkSite**
    
- **Remove-CsNetworkSite**
    
### To assign a location policy to an existing network site

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the following cmdlets to modify an existing network site.
    
    Assign the **Redmond** tagged Location policy to an existing network site named **Redmond**.
    
  ```
  Set-CsNetworkSite -Identity "Redmond" -NetworkRegionID "NorthAmerica" -LocationPolicy "Redmond"
  
  ```

### To assign a location policy to a new network site

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the following cmdlet to create a new network site.
    
    Create a new network site in the network region and assign the **Redmond** tagged Location policy. 
    
  ```
  New-CsNetworkSite -Identity "Redmond" -NetworkRegionID "NorthAmerica" -LocationPolicy "Redmond"
  ```


