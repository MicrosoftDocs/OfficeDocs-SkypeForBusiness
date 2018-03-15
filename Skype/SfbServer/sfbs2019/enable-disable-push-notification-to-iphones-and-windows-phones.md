---
title: "Enable/disable push notification to iPhones and Windows Phones in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 64482dcb-6354-4fb5-a2e4-1564b3d0e047
description: "To disable push notifications from being sent to either iPhones or Windows Phones, use the Set-CsPushNotificationConfiguration cmdlet and set the values of the EnableApplePushNotificationService and the EnableMicrosoftPushNotificationService properties to False ($False):"
---

# Enable/disable push notification to iPhones and Windows Phones in Skype for Business Online
[]
To disable push notifications from being sent to either iPhones or Windows Phones, use the [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md) cmdlet and set the values of the EnableApplePushNotificationService and the EnableMicrosoftPushNotificationService properties to False ($False): 
  
```
Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False -EnableMicrosoftPushNotificationService $False
```

Note that iPhones and Windows phones can be set independently. For example, this command disables push notifications on iPhones, but enables those notifications on Windows Phones:
  
```
Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False -EnableMicrosoftPushNotificationService $True
```

## See also

#### 

[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

