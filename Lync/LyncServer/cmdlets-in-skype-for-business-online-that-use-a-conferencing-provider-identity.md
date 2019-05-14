---
title: Cmdlets in Skype for Business Online that use a conferencing provider identity
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Cmdlets that use a conferencing provider identity
ms:assetid: be5621b6-ec11-4b12-83ec-075af269ca6a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362841(v=OCS.15)
ms:contentKeyID: 56558858
ms.date: 05/04/2015
manager: serdars
mtps_version: v=OCS.15
---

# Cmdlets in Skype for Business Online that use a conferencing provider identity

 


To return information about all of the audio conferencing providers that your organization has contracted with, you can simply call the [Get-CsAudioConferencingProvider](https://technet.microsoft.com/en-us/library/jj994030\(v=ocs.15\)) cmdlet without any parameters:

    Get-CsAudioConferencingProvider

If you want to limit the returned data to a single provider (in this example, the provider Contoso Audio Services), then use the Identity parameter:

    Get-CsAudioConferencingProvider -Identity "Contoso Audio Services"

There is only one Skype for Business Online cmdlet that accepts an audio conferencing provider ID:

  - [Get-CsAudioConferencingProvider](https://technet.microsoft.com/en-us/library/jj994030\(v=ocs.15\))

## See Also


[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[The Skype for Business Online cmdlets](https://technet.microsoft.com/en-us/library/dn362817\(v=ocs.15\))

