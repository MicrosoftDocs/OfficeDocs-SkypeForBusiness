---
title: "Add a domain to the allowed domains list in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 7b7f76c8-3047-40be-a938-8ac2868a6bc8
description: "Adding a first domain to the allowed domains list is a three-step process. First, use the New-CsEdgeDomainPattern cmdlet to create a domain object for the domain to be added:"
---

# Add a domain to the allowed domains list in Skype for Business Online
[]
Adding a first domain to the allowed domains list is a three-step process. First, use the [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) cmdlet to create a domain object for the domain to be added: 
  
```
$x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
```

Next, use the [New-CsEdgeAllowList](new-csedgeallowlist.md) cmdlet to create a new allowed list that includes the domain object: 
  
```
$newAllowList = New-CsEdgeAllowList -AllowedDomain $x
```

Finally, use the [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet to write the new allowed list to Skype for Business Online: 
  
```
Set-CsTenantFederationConfiguration -AllowedDomains $newAllowList
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

