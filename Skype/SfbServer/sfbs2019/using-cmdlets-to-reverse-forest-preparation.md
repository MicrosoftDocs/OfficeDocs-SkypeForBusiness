---
title: "Using cmdlets to reverse forest preparation for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f48c7eb3-ccb0-48e6-ac79-ab7c7062b9d3
description: "Use the Disable-CsAdForest cmdlet to reverse the forest preparation step."
---

# Using cmdlets to reverse forest preparation for Lync Server 2013
[]
Use the **Disable-CsAdForest** cmdlet to reverse the forest preparation step. 
  
> [!CAUTION]
> If you run the **Disable-CsAdForest** cmdlet in an environment where you also have a previous version of Lync Server deployed, the global settings for the previous version will also be deleted. 
  
### To use cmdlets to reverse forest preparation

1. Log on to a computer that is joined to a domain as a member of the Domain Admins group in the forest root domain.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Run:
    
  ```
  Disable-CsAdForest [-Force] [-GroupDomain <FQDN of the domain in which universal groups were created>]
  ```

    For example:
    
  ```
  Disable-CsAdForest -Force -GroupDomain contoso.net
  ```

    The Force parameter specifies whether to force running the task. If this parameter is not present, the command will not run if even one domain in the forest is still prepared for Lync Server 2013. If the Force parameter is specified, the action will continue regardless of the state of other domains in the forest.
    
    If you do not specify the GroupDomain parameter, the default value is the local domain.
    
## See also

#### 

[Running forest preparation for Lync Server 2013](running-forest-preparation.md)
#### 

[Preparing the forest for Lync Server 2013](preparing-the-forest.md)

