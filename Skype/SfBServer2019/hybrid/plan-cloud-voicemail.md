---
title: "Plan Cloud Voicemail Service"
ms.author: <ms alias>
author: <github alias>
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "<topic description>"
---
<!-- PM Francois Doremieux  -->
# Plan Cloud Voicemail Service

[!INCLUDE [disclaimer](../disclaimer.md)]

## Feature Overview 

This feature allows Skype for Business Server to use the same Cloud Voicemail Service (located in Azure) as Skype for Business Online users, as described in [Check Skype for Business voicemail and options] (https://support.office.com/en-us/article/Check-Skype-for-Business-voicemail-and-options-2deea7f8-831f-4e85-a0d4-b34da55945a8?ui=en-US&rs=en-US&ad=US). Unanswered calls will be sent by the Server to the Service (i.e. from on-prem to online). The Service will process the voicemail, including transcription. The Service will then deposit the voicemail in the Exchange mailbox of the users, regardless of whether they are homed on-prem or online (as is done for Cloud PBX users). Users will have access to their voicemail both from the Skype for Business client and from their Exchange mailbox (as is currently the case). On-prem users will be able to use the web based portal to manage the same user facing parameters available for online users. An admin will have controls over the same range of controls available for online users. See [Set up Phone System voicemail](https://support.office.com/en-us/article/Set-up-Phone-System-voicemail-Admin-help-9c590873-b014-4df3-9e27-1bb97322a79d?ui=en-US&rs=en-US&ad=US) for example. 





