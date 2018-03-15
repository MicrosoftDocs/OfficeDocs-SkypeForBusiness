---
title: "Prevent anonymous users from automatically being admitted to a meeting in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 23f120d2-4c39-4509-aa1f-4d186a525075
description: "To prevent anonymous users from automatically being admitted to an online meeting, use the Set-CsMeetingConfiguration cmdlet and set the AdmitAnonymousUsersByDefault property to False ($False):"
---

# Prevent anonymous users from automatically being admitted to a meeting in Skype for Business Online
[]
To prevent anonymous users from automatically being admitted to an online meeting, use the [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) cmdlet and set the AdmitAnonymousUsersByDefault property to False ($False): 
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False

```

To enable automatic admittance, set the AdmitAnonymousUsersByDefault property back to True ($True):
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

