---
title: "Manage Exchange Unified Messaging and hosted voicemail"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: 707198df-df85-4833-9c15-aa29b71f085c
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1keywords: None
ms.custom:
- PowerShell
description: "Use PowerShell to manage Exchange Unified Messaging capabilities such as Auto Attendant and Subscriber Access and hosted voicemail in Skype for Business Online."
---

# Manage Exchange Unified Messaging and hosted voicemail

You can manage Exchange Unified Messaging and hosted voicemail in Skype for Business Online by using a set of cmdlets.
  
## Manage Exchange unified messaging and hosted voice mail

The following cmdlets can be used to manage Exchange Unified Messaging (UM) and hosted voicemail policies:
  

| **Cmdlet**                                                                                                                                                                                                                                                                                                                        | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Get-CsExUmContact](https://go.microsoft.com/fwlink/p/?linkid=849628) <br/><br/> [New-CsExUmContact](https://go.microsoft.com/fwlink/p/?linkid=849629) <br/> <br/>[Remove-CsExUmContact](https://go.microsoft.com/fwlink/p/?linkid=849630) <br/> <br/>[Set-CsExUmContact](https://go.microsoft.com/fwlink/p/?linkid=849631) <br/> | Creates and manages contact objects used for Auto Attendant and Subscriber Access services, when Exchange UM is a hosted service.  <br/><br/> Skype for Business Online works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. Auto Attendant provides a way for calls to automatically be answered and routed to the correct person. Subscriber Access enables users to connect to Exchange UM and retrieve email, voice messages, contacts, and calendar information.  <br/><br/> When Exchange UM is provided as a hosted service, contact objects used for the Auto Attendant and Subscriber Access services must be created by using Microsoft PowerShell. These objects are created and managed by using the **CsExUmContact** cmdlets. <br/> |
| [Get-CSHostedVoicemailPolicy](https://go.microsoft.com/fwlink/p/?linkid=849633) <br/> <br/>[Grant-CSHostedVoicemailPolicy](https://go.microsoft.com/fwlink/p/?linkid=849602) <br/>                                                                                                                                                | Manages hosted voicemail policies used in the organization. Hosted voicemail policies specify how unanswered calls are routed to the Exchange UM service. These policies affect only users who have been enabled for Exchange UM hosted voicemail.  <br/><br/> To verify whether a user is enabled for hosted voicemail, run a command similar to the following from the PowerShell prompt.  <br/> \`Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"                                                                                                                                                                                                                                                                                                                                                           |

## Related topics
[Set up your computer for skype for business online management using Windows PowerShell](set-up-your-computer-for-windows-powershell.md)

  
 
