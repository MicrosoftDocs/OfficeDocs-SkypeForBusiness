---
title: "Enable/disable conference recording in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.assetid: f6c5afab-081c-495c-97f7-135dcc2f6085
description: "If you do not want users to have the ability to record online conferences, use the Set-CsMeetingConfiguration cmdlet and set the value of the AllowConferenceRecording parameter to False ($False):"
---

# Enable/disable conference recording in Skype for Business Online
[]
If you do not want users to have the ability to record online conferences, use the [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) cmdlet and set the value of the AllowConferenceRecording parameter to False ($False): 
  
```
Set-CsMeetingConfiguration -AllowConferenceRecording $False

```

To restore the ability to record online conferences, set the value of the AllowConferenceRecording parameter to True ($True):
  
```
Set-CsMeetingConfiguration -AllowConferenceRecording $True
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

