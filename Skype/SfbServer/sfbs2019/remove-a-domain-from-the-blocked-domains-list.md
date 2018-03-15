---
title: "Remove a domain from the blocked domains list in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: a11ea475-bb8b-44be-a5a5-4abb2fed42b8
description: "Two steps are required to remove a domain from the blocked domains list. First, you must use the New-CsEdgeDomainPattern cmdlet to create a domain object for the domain to be removed:"
---

# Remove a domain from the blocked domains list in Skype for Business Online
[]
Two steps are required to remove a domain from the blocked domains list. First, you must use the [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) cmdlet to create a domain object for the domain to be removed: 
  
```
$x = New-CsEdgeDomainPattern "fabrikam.com"
```

After creating this object, use the following syntax to remove the domain (in this example, the domain stored in the variable $x) from the blocked domains list:
  
```
Set-CsTenantFederationConfiguration -BlockedDomains @{Remove=$x}
```

To remove all the domains from the blocked domains list, set the value of the BlockedDomains property to null ($Null):
  
```
Set-CsTenantFederationConfiguration -BlockedDomains $Null
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

