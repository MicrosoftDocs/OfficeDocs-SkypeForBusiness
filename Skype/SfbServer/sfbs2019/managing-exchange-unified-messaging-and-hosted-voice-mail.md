---
title: "Managing Exchange Unified Messaging and hosted voice mail in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 844bf8d5-e093-4dcd-abcf-48dc70e8c73c

description: "The following cmdlets can be used to manage Exchange Unified Messaging (UM) and hosted voice mail policies:"
---

# Managing Exchange Unified Messaging and hosted voice mail in Skype for Business Online
[]
The following cmdlets can be used to manage Exchange Unified Messaging (UM) and hosted voice mail policies:
  
|**Cmdlet**|**Description**|
|:-----|:-----|
|[Get-CsExUmContact](get-csexumcontact.md) <br/> [New-CsExUmContact](new-csexumcontact.md) <br/> [Remove-CsExUmContact](remove-csexumcontact.md) <br/> [Set-CsExUmContact](set-csexumcontact.md) <br/> |Creates and manages contact objects used for Auto Attendant and Subscriber Access services, when Exchange UM is a hosted service.  <br/> Skype for Business Online works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. Auto Attendant provides a way for calls to automatically be answered and routed to the correct person. Subscriber Access enables users to connect to Exchange UM and retrieve email, voice messages, contacts, and calendar information.  <br/> When Exchange UM is provided as a hosted service, contact objects used for the Auto Attendant and Subscriber Access services must be created by using Windows PowerShell. These objects are created and managed by using the CsExUmContact cmdlets.  <br/> |
|[Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md) <br/> [Grant-CsHostedVoicemailPolicy](grant-cshostedvoicemailpolicy.md) <br/> |Manages hosted voicemail policies used in the organization. Hosted voicemail policies specify how unanswered calls are routed to the Exchange UM service. These policies affect only users who have been enabled for Exchange UM hosted voicemail. To verify whether a user is enabled for hosted voicemail, run a command similar to this from the Windows PowerShell prompt:  <br/> ```Get-CsOnlineUser -Identity "kenmyer@litwareinc.com" | Select-Object HostedVoiceMail```|
   
You cannot manage Exchange UM settings and hosted voicemail policies by using the Skype for Business Online admin center.
  
## See also

#### 

[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)
  
[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online.md)

