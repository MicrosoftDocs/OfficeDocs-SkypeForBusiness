---
title: "Assign an audio conferencing provider to a user in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 60db6896-9c5c-4d64-ab7e-10d91748587c
description: "The Set-CsUserAcp cmdlet provides a way for you to assign an audio conferencing provider to a user:"
---

# Assign an audio conferencing provider to a user in Skype for Business Online
[]
The [Set-CsUserAcp](set-csuseracp.md) cmdlet provides a way for you to assign an audio conferencing provider to a user: 
  
```
Set-CsUserAcp -Identity "Ken Myer" -TollNumber "12065551219" -TollFreeNumbers "18005550712" -ParticipantPasscode "p@ssw0rd" -Domain "sip.contoso.com" -Name "Contoso ACP"
```

This assignment will be meaningless unless you have already contracted with the specified provider.
  
## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

