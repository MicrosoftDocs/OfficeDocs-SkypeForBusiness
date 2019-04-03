---
title: Cmdlets in Skype for Business Online that do not use a scope or an identity
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Cmdlets that do not use a scope or an identity
ms:assetid: 9c50c732-3c64-4b6a-96fd-8f528eb739ce
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362824(v=OCS.15)
ms:contentKeyID: 56558839
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

# Cmdlets in Skype for Business Online that do not use a scope or an identity

 


The cmdlets used when modifying the allowed lists and blocked lists (lists that determine which outside organizations your users are allowed to communicate with) do not use either a scope or an Identity. In fact, the **New-CsEdgeAllowAllKnownDomains** cmdlet does not have any parameters whatsoever. The cmdlets that do not use either a scope or an Identity are:

  - [New-CsEdgeAllowAllKnownDomains](https://technet.microsoft.com/en-us/library/jj994088\(v=ocs.15\))

  - [New-CsEdgeAllowList](https://technet.microsoft.com/en-us/library/jj994023\(v=ocs.15\))

  - [New-CsEdgeDomainPattern](https://technet.microsoft.com/en-us/library/jj994040\(v=ocs.15\))

Note that, with both the **New-CsEdgeAllowList** cmdlet and the **New-CsEdgeDomainPattern** cmdlet, you must include the Domain parameter. For example:

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"

## See Also


[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[The Skype for Business Online cmdlets](https://technet.microsoft.com/en-us/library/dn362817\(v=ocs.15\))

