---
title: "Unassign a per-user policy previously assigned to a user in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: bdba1d22-28e4-4203-a109-a3fb408783d3
description: "If you want to unassign a per-user policy that was previously assigned to a user, rerun the appropriate Grant-Cs cmdlet (for example, the Grant-CsVoicePolicy cmdlet to unassign a voice policy), and set the PolicyName parameter to a null value ($Null):"
---

# Unassign a per-user policy previously assigned to a user in Skype for Business Online
[]
If you want to unassign a per-user policy that was previously assigned to a user, rerun the appropriate **Grant-Cs** cmdlet (for example, the [Grant-CsVoicePolicy](grant-csvoicepolicy.md) cmdlet to unassign a voice policy), and set the PolicyName parameter to a null value ($Null): 
  
```
Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName $Null
```

To unassign voice policies from all your users, use this command:
  
```
Get-CsOnlineUser | Grant-CsVoicePolicy -PolicyName $Null
```

When a policy is unassigned from a user, that user will then be managed by the global policy.
  
## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

