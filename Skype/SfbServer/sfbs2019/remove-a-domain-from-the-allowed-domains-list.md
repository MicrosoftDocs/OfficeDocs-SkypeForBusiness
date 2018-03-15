---
title: "Remove a domain from the allowed domains list in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 04948582-363b-49bd-8305-166c4c1d0dd9
description: "Removing a domain from the allowed domains list involves a series of steps. First, you must use a command similar to the following, in order to retrieve a collection of all the domains currently on the list:"
---

# Remove a domain from the allowed domains list in Skype for Business Online
[]
Removing a domain from the allowed domains list involves a series of steps. First, you must use a command similar to the following, in order to retrieve a collection of all the domains currently on the list:
  
```
$x = (Get-CsTenantFederationConfiguration).AllowedDomains
```

Next, run this command to review those domains:
  
```
$x
```

Take note of the numeric position of the domain to be removed. If the domain is the first domain in the list, then it has an index value of 0. If the domain is the second domain in the list, it has an index value of 1, and so on.
  
After you know the index number, use a command like the following to remove the specified domain, making sure to use the correct index number. This command removes the first domain in the list (index number 0):
  
```
$x.AllowedDomain.RemoveAt(0)
```

Finally, call the [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet to write your changes to Skype for Business Online: 
  
```
Set-CsTenantFederationConfiguration -AllowedDomains $x
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

