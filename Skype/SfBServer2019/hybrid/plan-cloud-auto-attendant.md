---
title: "Plan a Cloud Auto Attendant"
ms.author: jambirk
author: jambirk
manager: serdars 
ms.date: 7/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Overview of using a Cloud Auto Attendant with Skype for Business Server 2019."
---

# Plan Cloud Auto Attendant

[!INCLUDE [disclaimer](../disclaimer.md)]

Skype for Business Server 2019 hybrid implementations only use Cloud Voicemail and do not integrate with Exchange Online.

Using Skype for Business Server 2019 with [Phone System Auto Attendants](/SkypeForBusiness/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants.md) is not yet available.

If you are a current user of Exchange Server 2013 or Exchange Server 2016, you will be able to continue to use them as you implement Skype for Business Server 2019. Exchange UM, including Auto Attendant functionality, is being retired in Exchange 2019.

Similar functionality exists in Phone System, and Skype for Business Server 2019 interaction with Phone system is rolling out on a feature-by-feature basis. Please plan accordingly.

<hr>

## Feature Overview

The Auto Attendant used with Exchange Unified Messaging (Exchange Server 2013 or Exchange Server 2016) is no longer available in Exchange Server 2019 or Exchange Online. If your implementation of Skype for Business Server 2019 integrates with either of these Exchange versions, you'll need to use the online Cloud Voice features associated with Phone System. This inherently means that you will have a hybrid implementation of Skype for Business Server 2019. See [Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md) for details.

An Auto Attendant can include a greeting the caller can't interact with (this can be a different message during office hours and outside office hours) and menu choices the users can interact with either with a voice response or by pressing a telephone keypad, without the intervention of a receptionist or an operator. The options can connect callers to employees, call queues used by entire departments, and other auto attendants that act as sub-menus to a main Auto Attendant. Each Auto Attendant is a distinct virtual user on your Skype for Business 2019 system. See [What are Phone System auto attendants?](/SkypeForBusiness/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants.md) for more detail on what Auto Attendants are and what options and features exist for Auto Attendants.

To create auto attendants in a hybrid environment, you should already have implemented [Cloud Voicemail](plan-cloud-voicemail.md), and in addition you will need to:

1. Create on premise endpoints for each Auto Attendant, including assigning phone numbers and licenses. Note that you now have the ability to assign licenses used by online services like Phone System to on-premise phone numbers.
2. Implement a new Cloud Auto Attendant service with Skype for Business Online and Phone System. See [Configure cloud auto attendant](configure-cloud-auto-attendant.md) for implementation details.

In many auto attendant systems, a receptionist or operator can be reached by pressing or saying zero. Some auto attendant systems use message-only information menus and voice menus so an organization can provide business hours, directions to the premises, information about job opportunities, and answers to other frequently asked questions. After the message plays, callers are forwarded to the receptionist or operator, or they can return to the main menu.

Although auto attendants can be very useful, if they aren't designed and configured thoughtfully, they can confuse and frustrate callers. For example, especially in large organizations, when auto attendants aren't designed well callers can be led through a lengthy series of questions and menu prompts before they're finally transferred to a person to answer their questions. In the worst cases, they can select option after option only to wind up at a menu they've already heard.

Auto Attendants also have a number of settings (such as business hours or a holiday schedule, choosing the codecs used, inaction timeout, and so on) that are configurable to an organization's needs.

See:

- [What are Phone System auto attendants?](/SkypeForBusiness/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants.md)
- [Set up a Phone System auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md)
- [Automatically answer and route incoming calls](/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/automatically-answer-and-route-calls) 

## Migrating a previously implemented Exchange UM Auto Attendant system

Currently we don't support automated migration of a UM auto attendant system created in Exchange 2013 or 2016. To manually re-create an Auto Attendant system, you'll need to:

1. Use Exchange admin powershell commands to review the structure of the old Auto Attendant system, including any nested Auto Attendants and call queues.  
2. Create copies of text-to-speech scripts or recorded messages associated with each UM Auto Attendant node.
3. Create on premise endpoints for each Auto Attendant node, including assigning phone numbers and licenses to the objects. Note that you now have the ability to assign on-premise phone numbers licenses used by online services like Phone System.
4. Implement a new Cloud Auto Attendant service with Skype for Business Online and Phone System. See [Configure cloud auto attendant](configure-cloud-auto-attendant.md) for implementation details. As you do this, upload the text-to-speech scripts or recorded messages associated with each UM Auto Attendant node.

See [Manually moving an Exchange UM Auto Attendant to Cloud Auto Attendant](configure-cloud-auto-attendant.md#manually-moving-an-exchange-um-auto-attendant-to-cloud-auto-attendant) for details on these steps.

## Planning auto attendants

The tutorial titled [Implementation example - Auto Attendants](/SkypeForBusiness/what-is-phone-system-in-office-365/tutorial-org-aa.yml) goes through the process of gathering information about user needs, planning a structure of Auto Attendants and users (and possibly Call Queues, which are not yet supported for hybrid implementations), writing the menu prompts, an implementing the plan in the Online Admin center. review the tutorial and use the exercises there to create your plan.

When you have a solid structure that meets your needs and a script that guides customers efficiently, proceed to [Configure Cloud Auto Attendant](configure-cloud-auto-attendant.md).

## See Also

[Configure Cloud Auto Attendant](configure-cloud-auto-attendant.md)

[Enable custom prompt recording using the telephone user interface](/exchange/voice-mail-unified-messaging/greetings-announcements-menus-and-prompts/enable-custom-prompt-recording)

[Plan Cloud Voicemail service](plan-cloud-voicemail.md)

[Configure Cloud Voicemail service](configure-cloud-voicemail.md)

[What are Phone System auto attendants?](/SkypeForBusiness/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants.md)

[Set up a Phone System auto attendant](/SkypeForBusiness/what-is-phone-system-in-office-365/set-up-a-phone-system-auto-attendant.md)

Exchange UM: [Automatically answer and route incoming calls](/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/automatically-answer-and-route-calls)