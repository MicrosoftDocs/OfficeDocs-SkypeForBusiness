---
title: "Return specific information for specific users in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: bbee85bd-d8a7-4b28-90d7-45c43eee48f6
description: "By default, the Get-CsOnlineUser cmdlet returns a huge amount of information for each Skype for Business Online user account. If you are interested in only a subset of that information, pipe the returned data to the Select-Object cmdlet. For example, this command returns all the data for the user Ken Myer, then uses the Select-Object cmdlet to limit the information displayed onscreen to Ken's Active Directory Domain Services display name and dial plan:"
---

# Return specific information for specific users in Skype for Business Online
[]
By default, the [Get-CsOnlineUser](get-csonlineuser.md) cmdlet returns a huge amount of information for each Skype for Business Online user account. If you are interested in only a subset of that information, pipe the returned data to the **Select-Object** cmdlet. For example, this command returns all the data for the user Ken Myer, then uses the **Select-Object** cmdlet to limit the information displayed onscreen to Ken's Active Directory Domain Services display name and dial plan: 
  
```
Get-CsOnlineUser -Identity "Ken Myer" | Select-Object DisplayName, DialPlan
```

The following command returns the display name and dial plan for all your users.
  
```
Get-CsOnlineUser | Select-Object DisplayName, DialPlan
```

To find the properties of a Skype for Business Online user account, use this command:
  
```
Get-CsOnlineUser | Get-Member
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

