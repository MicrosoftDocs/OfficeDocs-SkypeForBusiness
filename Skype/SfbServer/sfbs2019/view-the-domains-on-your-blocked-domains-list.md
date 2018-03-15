---
title: "View the domains on your blocked domains list in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 67c65dbf-1a68-4c77-aabd-bed5001b4267
description: "To view all of the domains on your blocked domains list, call the Get-CsTenantFederationConfiguration cmdlet, and then pipe the returned data to the Select-Object cmdlet:"
---

# View the domains on your blocked domains list in Skype for Business Online
[]
To view all of the domains on your blocked domains list, call the [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md) cmdlet, and then pipe the returned data to the **Select-Object** cmdlet: 
  
```
Get-CsTenantFederationConfiguration | Select-Object -ExpandProperty BlockedDomains
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

