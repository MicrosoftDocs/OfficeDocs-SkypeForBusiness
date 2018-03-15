---
title: "Assign a per-user policy to a user in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 37e07da7-6391-4d6d-a428-c70272897039
description: "To assign a per-user policy to a user, you must first select the appropriate Grant-Cs cmdlet. (For example, the Grant-CsVoicePolicy, if you want to assign a per-user voice policy.) Run the cmdlet, making sure to specify both the Identity of the user to be assigned the policy and the name of the policy being assigned:"
---

# Assign a per-user policy to a user in Skype for Business Online
[]
To assign a per-user policy to a user, you must first select the appropriate **Grant-Cs** cmdlet. (For example, the [Grant-CsVoicePolicy](grant-csvoicepolicy.md), if you want to assign a per-user voice policy.) Run the cmdlet, making sure to specify both the Identity of the user to be assigned the policy and the name of the policy being assigned:
  
```
Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"
```

If you want to assign the same policy to all your users, use this syntax:
  
```
Get-CsOnlineUser | Grant-CsVoicePolicy -PolicyName "RedmondVoicePolicy"
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

