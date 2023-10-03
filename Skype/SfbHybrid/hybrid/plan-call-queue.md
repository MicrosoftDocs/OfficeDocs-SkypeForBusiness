---
ms.date: 06/22/2018
title: "Plan a Cloud call queue"
ms.author: serdars
author: MicrosoftHeidi
manager: serdars 
ms.reviewer: wasseemh
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.collection: 
description: "Overview of using a Cloud auto attendant with Skype for Business Server 2019."
---

# Plan Cloud call queues

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

Cloud call queue is a service that accepts customer calls, plays a greeting message, and then places these calls in a wait queue while searching a pre-configured list of agents to answer these calls. You can define the set of agents in mail-enabled distribution lists or security groups. Your organization can have one or many call queues. Call queues are often used in combination with auto attendants.

In addition, Cloud call queues can provide:

- Music while callers are waiting on hold
- Customized settings for call queue maximum size, timeout, and call handling options

Each call queue is assigned a **resource account** (see [Configure resource accounts](configure-onprem-ra.md)) on your Skype for Business Server 2019 system that will be linked directly to a call queue in the Microsoft Teams admin center. See [Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue) for more detail on what call queues are and what options and features exist for call queues.

> [!NOTE]
> You can assign multiple phone numbers to a call queue, but they must be Microsoft service numbers, Direct Routing numbers, or hybrid numbers.

## Requirements

The following requirements assume that you already have Skype for Business Server 2019 deployed in a supported topology.  Your requirements depend on your scenario:

- For a new configuration of Cloud call queues, follow the steps outlined in [Configure resource accounts](configure-onprem-ra.md). You'll need to create resource accounts either online or in Skype for Business Server 2019, and you may also need to associate a phone number with the call queue.

In addition to the requirements above, the below requirements must be configured to connect to the Microsoft Cloud call queue service:

- Hybrid connectivity. If you already have Skype for Business Server deployed, and you want to enable Cloud call queues for your on-premises users, you must ensure that you have hybrid connectivity set up between your on-premises and online environments. This is sometimes called a split domain configuration.

   For more information, see [Plan hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](plan-hybrid-connectivity.md) and [Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](configure-hybrid-connectivity.md).

- If you're assigning a phone number to a resource account, you can now use the cost-free **Microsoft Teams Phone Resource Account** license. This provides Phone System capabilities to phone numbers at the organizational level, and allows you to create auto attendant and call queue capabilities.

- Create an on-premises [resource account](configure-onprem-ra.md) for each call queue, and assign a license and phone number if required.  

When you have a solid structure that meets your needs and a script that guides customers efficiently, proceed to  [Configure resource accounts](configure-onprem-ra.md).

## See Also

[Configure resource accounts](configure-onprem-ra.md)

[Enable custom prompt recording using the telephone user interface](/exchange/voice-mail-unified-messaging/greetings-announcements-menus-and-prompts/enable-custom-prompt-recording)

[What are Cloud auto attendants?](/SkypeForBusiness/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants)

[Set up a Cloud auto attendant](/MicrosoftTeams/create-a-phone-system-auto-attendant)

[Plan hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](plan-hybrid-connectivity.md)

[Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](configure-hybrid-connectivity.md)

[Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts)
