---
title: "Add a domain to the blocked domains list in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: ea6ebeea-3031-4c42-9a2c-88eaab790636
description: "To add a domain to the blocked domains list, use syntax similar to this:"
---

# Add a domain to the blocked domains list in Skype for Business Online
[]
To add a domain to the blocked domains list, use syntax similar to this:
  
```
$x = New-CsEdgeDomainPattern "fabrikam.com"
Set-CsTenantFederationConfiguration -BlockedDomains @{Add=$x}

```

As you can see, this command requires two steps. First, you use the [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) to create a domain object representing the domain to be added to the blocked list. After that, you use the [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet and the Add method to add that domain (in this example, the domain stored in the variable $x) to the list. 
  
## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

