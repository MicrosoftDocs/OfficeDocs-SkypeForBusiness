---
title: "Enable/disable federation with public IM providers in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 8609682c-97d3-48e6-a243-d84c1f9c8419
description: "To enable your users to communicate with users who have accounts on a public instant messaging (IM) provider, use the Set-CsTenantFederationConfiguration cmdlet and set the AllowPublicUsers property to True ($True):"
---

# Enable/disable federation with public IM providers in Skype for Business Online
[]
To enable your users to communicate with users who have accounts on a public instant messaging (IM) provider, use the [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet and set the AllowPublicUsers property to True ($True): 
  
```
Set-CsTenantFederationConfiguration -AllowPublicUsers $True
```

Note that you must then use the [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) cmdlet to specify the public IM providers that your users will be allowed to communicate with. 
  
To disable federation with public providers, set the AllowPublicUsers property back to false ($False):
  
```
Set-CsTenantFederationConfiguration -AllowPublicUsers $False
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

