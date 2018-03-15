---
title: "View the domains on your allowed domains list in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 13bceaba-5c4f-431f-864f-9e374cafa986
description: "To view all of the domains on your allowed domain list, use the Get-CsTenantFederationConfiguration and the following syntax:"
---

# View the domains on your allowed domains list in Skype for Business Online
[]
To view all of the domains on your allowed domain list, use the [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md) and the following syntax: 
  
```
Get-CsTenantFederationConfiguration | Select-Object -ExpandProperty AllowedDomains | Select-Object AllowedDomain
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

