---
title: "Return information about your audio conferencing providers in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: df9c8fc0-8bb6-4416-a5cc-aa9b1601a688
description: "To return information about the audio conferencing providers that have been assigned to a user, use the Get-CsUserAcp cmdlet and the following syntax:"
---

# Return information about your audio conferencing providers in Skype for Business Online
[]
To return information about the audio conferencing providers that have been assigned to a user, use the [Get-CsUserAcp](get-csuseracp.md) cmdlet and the following syntax: 
  
```
Get-CsUserAcp -Identity "Ken Myer" | Select-Object -ExpandProperty AcpInfo
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

