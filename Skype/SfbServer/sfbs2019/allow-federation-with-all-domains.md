---
title: "Allow federation in Skype for Business Online with all domains"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: d26f1057-a76c-447a-9efe-72efdce4c15e
description: "If you want your users to be allowed to communicate with users from any domain, you must do two things. First, use the New-CsEdgeAllowAllKnownDomains cmdlet to create an instance of the AllowAllKnownDomains object:"
---

# Allow federation in Skype for Business Online with all domains
[]
If you want your users to be allowed to communicate with users from any domain, you must do two things. First, use the [New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md) cmdlet to create an instance of the AllowAllKnownDomains object: 
  
```
$x = New-CsEdgeAllowAllKnownDomains
```

After that, call the [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet, and set the value of the AllowedDomains property to the variable (in this example, $x) that contains the AllowAllKnownDomains object: 
  
```
Set-CsTenantFederationConfiguration -AllowedDomains $x
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

