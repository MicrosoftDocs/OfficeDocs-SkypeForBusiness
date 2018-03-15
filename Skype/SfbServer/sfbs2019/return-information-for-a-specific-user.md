---
title: "Return information for a specific user in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 6c8c2190-8e62-4f92-bbe9-4f692bd7ebf5
description: "There are multiple ways of referencing a specific user account when calling the Get-CsOnlineUser cmdlet. You can use the user's Active Directory Domain Services display name:"
---

# Return information for a specific user in Skype for Business Online
[]
There are multiple ways of referencing a specific user account when calling the [Get-CsOnlineUser](get-csonlineuser.md) cmdlet. You can use the user's Active Directory Domain Services display name: 
  
```
Get-CsOnlineUser -Identity "Ken Myer"
```

You can use the user's SIP address:
  
```
Get-CsOnlineUser -Identity "sip:kenmyer@litwareinc.com"
```

You can use the user's user principal name (UPN):
  
```
Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

