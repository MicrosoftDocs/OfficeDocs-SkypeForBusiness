---
title: "Cmdlets in Skype for Business Online that do not use a scope or an identity"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 9c50c732-3c64-4b6a-96fd-8f528eb739ce
description: "The cmdlets used when modifying the allowed lists and blocked lists (lists that determine which outside organizations your users are allowed to communicate with) do not use either a scope or an Identity. In fact, the New-CsEdgeAllowAllKnownDomains cmdlet does not have any parameters whatsoever. The cmdlets that do not use either a scope or an Identity are:"
---

# Cmdlets in Skype for Business Online that do not use a scope or an identity
[]
The cmdlets used when modifying the allowed lists and blocked lists (lists that determine which outside organizations your users are allowed to communicate with) do not use either a scope or an Identity. In fact, the **New-CsEdgeAllowAllKnownDomains** cmdlet does not have any parameters whatsoever. The cmdlets that do not use either a scope or an Identity are: 
  
- [New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md)
    
- [New-CsEdgeAllowList](new-csedgeallowlist.md)
    
- [New-CsEdgeDomainPattern](new-csedgedomainpattern.md)
    
Note that, with both the **New-CsEdgeAllowList** cmdlet and the **New-CsEdgeDomainPattern** cmdlet, you must include the Domain parameter. For example: 
  
```
$x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
```

## See also

#### 

[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants.md)
  
[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)

