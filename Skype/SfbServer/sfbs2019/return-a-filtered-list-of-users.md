---
title: "Return a filtered list of users in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: f2c4d13b-8601-4192-8b94-e9a57969da11
description: "By using the Get-CsOnlineUser cmdlet and the LdapFilter or Filter parameters, you can easily return information about a targeted set of users. For example, this command returns all the users who work in the Finance department:"
---

# Return a filtered list of users in Skype for Business Online
[]
By using the [Get-CsOnlineUser](get-csonlineuser.md) cmdlet and the LdapFilter or Filter parameters, you can easily return information about a targeted set of users. For example, this command returns all the users who work in the Finance department: 
  
```
Get-CsOnlineUser -LdapFilter "department=Finance"
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

