---
title: "Cmdlets in Skype for Business Online that use a conferencing provider identity"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: be5621b6-ec11-4b12-83ec-075af269ca6a
description: "To return information about all of the audio conferencing providers that your organization has contracted with, you can simply call the Get-CsAudioConferencingProvider cmdlet without any parameters:"
---

# Cmdlets in Skype for Business Online that use a conferencing provider identity
[]
To return information about all of the audio conferencing providers that your organization has contracted with, you can simply call the [Get-CsAudioConferencingProvider](get-csaudioconferencingprovider.md) cmdlet without any parameters: 
  
```
Get-CsAudioConferencingProvider
```

If you want to limit the returned data to a single provider (in this example, the provider Contoso Audio Services), then use the Identity parameter:
  
```
Get-CsAudioConferencingProvider -Identity "Contoso Audio Services"
```

There is only one Skype for Business Online cmdlet that accepts an audio conferencing provider ID:
  
- [Get-CsAudioConferencingProvider](get-csaudioconferencingprovider.md)
    
## See also

#### 

[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants.md)
  
[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)

