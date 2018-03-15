---
title: "Parameters vs. properties in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 65348f95-f4d4-40cd-8869-f9d72643792d
description: "When reviewing the help topics for the Skype for Business Online cmdlets, you'll sometimes see the terms parameter and property used interchangeably. Don't be confused by this terminology: although the two are technically different, in Skype for Business Online, the terms essentially refer to the same thing."
---

# Parameters vs. properties in Skype for Business Online
[]
When reviewing the help topics for the Skype for Business Online cmdlets, you'll sometimes see the terms parameter and property used interchangeably. Don't be confused by this terminology: although the two are technically different, in Skype for Business Online, the terms essentially refer to the same thing. 
  
Technically speaking, parameters are used when you run a cmdlet. For example, in the following Windows PowerShell command, EnableMicrosoftPushNotificationService and EnableApplePushNotificationService are parameters of the [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md) cmdlet: 
  
```
Set-CsPushNotificationConfiguration -EnableMicrosoftPushNotificationService -EnableApplePushNotificationService $True
```

A property is an attribute of a Skype for Business Online object (for example, a collection of push notification configuration settings). Let's say that you run this command:
  
```
Set-CsPushNotificationConfiguration
```

When you do this, you'll get back a collection of properties and their associated values, which will include the following items:
  
```
EnableMicrosoftPushNotificationService : True
EnableApplePushNotificationService     : True
```

As you can see, properties and parameters share the same name: you use the EnableMicrosoftPushNotificationService parameter to configure the value of the EnableMicrosoftPushNotificationService property.
  
## See also

#### 

[An introduction to Windows PowerShell and Skype for Business Online](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

