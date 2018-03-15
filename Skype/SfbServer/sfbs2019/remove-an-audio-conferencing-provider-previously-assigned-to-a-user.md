---
title: "Remove an audio conferencing provider previously assigned to a user in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 85d59e6c-d646-4908-9767-adb48763f6de
description: "To remove all the audio conferencing providers assigned to a user, run the Remove-CsUserAcp cmdlet without any parameters (other than the Identity parameter, which indicates the user in question):"
---

# Remove an audio conferencing provider previously assigned to a user in Skype for Business Online
[]
To remove all the audio conferencing providers assigned to a user, run the [Remove-CsUserAcp](remove-csuseracp.md) cmdlet without any parameters (other than the Identity parameter, which indicates the user in question): 
  
```
Remove-CsUserAcp -Identity "Ken Myer"
```

If a user has been assigned multiple audio conferencing providers, you can remove a single provider by including the Name parameter, followed by the name of the provider to be removed:
  
```
Remove-CsUserAcp -Identity "Ken Myer" -Name "Contoso ACP"
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

