---
title: "Return information about all your Skype for Business Online users"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 0b59fadf-67e6-48ea-86f1-2efef500ebdf
description: "To return information about all your users who have been enabled for Skype for Business Online, call the Get-CsOnlineUser cmdlet without any additional parameters:"
---

# Return information about all your Skype for Business Online users
[]
To return information about all your users who have been enabled for Skype for Business Online, call the [Get-CsOnlineUser](get-csonlineuser.md) cmdlet without any additional parameters: 
  
```
Get-CsOnlineUser
```

To return information for a single, randomly-selected user (for example, to use this account for test purposes), call the **Get-CsOnlineUser** cmdlet and set the ResultSize parameter to 1: 
  
```
Get-CsOnlineUser -ResultSize 1
```

That causes the **Get-CsOnlineUser** cmdlet to return information for just one user, regardless of how many users you have in your organization. To return information for five users, set the value of the ResultSize parameter to 5: 
  
```
Get-CsOnlineUser -ResultSize 5
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

