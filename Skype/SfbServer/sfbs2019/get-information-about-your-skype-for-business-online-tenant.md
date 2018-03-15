---
title: "Get information about your Skype for Business Online tenant"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 06467515-9114-45bb-8d09-26a915c3fc4d
description: "To return information about your Skype for Business Online tenant call the Get-CsTenant cmdlet, without any additional parameters:"
---

# Get information about your Skype for Business Online tenant
[]
To return information about your Skype for Business Online tenant call the [Get-CsTenant](get-cstenant.md) cmdlet, without any additional parameters: 
  
```
Get-CsTenant
```

To return just the tenant name and ID (the value of the TenantID parameter is required when running cmdlets such as [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) and [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)), use this command:
  
```
Get-CsTenant | Select-Object Name, TenantID
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

