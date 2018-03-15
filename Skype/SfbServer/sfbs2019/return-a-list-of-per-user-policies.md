---
title: "Return a list of per-user policies in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: e95a2755-3501-40cc-a704-5ecd01839d76
description: "To return a list of available per-user policies, first select the appropriate Get-Cs cmdlet (for example, the Get-CsVoicePolicy cmdlet, if you want to return per-user voice policies). Then use the following syntax to return the Identity for each per-user policy:"
---

# Return a list of per-user policies in Skype for Business Online
[]
To return a list of available per-user policies, first select the appropriate **Get-Cs** cmdlet (for example, the [Get-CsVoicePolicy](get-csvoicepolicy.md) cmdlet, if you want to return per-user voice policies). Then use the following syntax to return the Identity for each per-user policy: 
  
```
Get-CsVoicePolicy -Filter "tag:*" | Select-Object Identity
```

Note that, because of different licensing agreements and different country/region restrictions, it's possible that certain conferencing policies, external access policies, or mobility policies cannot be assigned to a particular user. To verify the per-user policies that can actually be assigned to a given user (for example, kenmyer@litwareinc.com) use one of the following commands (and the ApplicableTo parameter), as appropriate:
  
```
Get-CsConferencingPolicy -ApplicableTo "kenmyer@litwareinc.com"
Get-CsExternalAccessPolicy -ApplicableTo "kenmyer@litwareinc.com"
Get-CsMobilityPolicy -ApplicableTo "kenmyer@litwareinc.com"
```

The preceding syntax returns only those per-user policies that can actually be assigned to Ken Myer.
  
## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

