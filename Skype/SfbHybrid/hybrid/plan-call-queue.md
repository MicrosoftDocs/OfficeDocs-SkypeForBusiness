---
title: "Plan a Cloud PBX call queue"
ms.author: jambirk
author: jambirk
manager: serdars 
ms.reviewer: wasseemh
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Overview of using a Cloud PBX auto attendant with Skype for Business Server 2019."
---

# Plan Cloud call queues 

The call queue service used with Exchange Unified Messaging (Exchange Server 2013 or Exchange Server 2016) is no longer available in Exchange Server 2019 or Exchange Online. If your implementation of Skype for Business Server 2019 integrates with either of these Exchange versions, you'll need to use the online Cloud Voice features associated with Phone System. See [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md) for information about moving Exchange UM services homed on Exchange server 2013 and 2016 to the cloud.

This inherently means that you will have a hybrid implementation of Skype for Business Server 2019. See [Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md) for details.

A Cloud call queue can include a greeting the caller can't interact with (this can be a different message during office hours and outside office hours) and when reached it can play that message and then place the caller on hold,  while it searches for an available agent to answer. You can associate a call queue's redirection of a call with call agents in mail-enabled distribution lists and security groups. Your organization can have one or many call queues. Call queues are usually used in combination with auto attendants.

In addition, Cloud call queues can provide:

- Music while callers are waiting on hold
- Customized settings for call queue maximum size, timeout, and call handling options

Each call queue is assigned a resource account on your Skype for Business Server 2019 system that is linked directly to a call queue in the Microsoft Teams admin center. See [Create a Cloud call queue](/MicrosoftTeams/create-a-phone-system-call-queue) for more detail on what call queues are and what options and features exist for call queues.

> [!NOTE]
> You are now able to link multiple inbound phone numbers to a single Cloud call queue.

## Requirements

The following requirements assume that you already have Skype for Business Server 2019 deployed in a supported topology.  Your requirements depend on your scenario:

- If you are already using Exchange UM online or on premises and you upgrade to Skype for Business 2019, you will need to capture the structure of your auto attendants and call queues and re-create them in the cloud using Phone System. For more information, see [Manually moving an Exchange UM auto attendant to Cloud auto attendant](configure-cloud-auto-attendant.md#manually-moving-an-exchange-um-auto-attendant-to-cloud-auto-attendant).

- For a new configuration of Cloud call queues, follow the steps outlined in [Configure Cloud call queues](configure-call-queue.md).

In addition to the requirements above, the below requirements must be configured to connect to the Microsoft Cloud call queue service:

- Hybrid connectivity. If you already have Skype for Business Server deployed, and you want to enable Cloud call queues for your on-premises users, you must ensure that you have hybrid connectivity set up between your on-premises and online environments. This is sometimes called a split domain configuration.

   For more information, see [Plan hybrid connectivity between Skype for Business Server and Office 365](plan-hybrid-connectivity.md) and [Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md).

- For phone numbers that you assign to your call queue, you will need an [Office 365 Enterprise E5](/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/office-365-enterprise-e5-with-audio-conferencing) license.

- If you have an on-premises only deployment (that is, only Exchange Server 2019 and Skype for Business Server 2019 on-premises servers) but you want to take advantage of Cloud auto attendant, you need the ON-PREM license.

- Create an on-premises [resource account](/MicrosoftTeams/manage-resource-accounts) for each call queue, including assigning phone numbers and licenses. Note that you now have the ability to assign licenses used by online services like Phone System to on-premise phone numbers.
- Implement a new Cloud call queue service with Skype for Business Online and Phone System. See [Configure Cloud call queues](configure-call-queue.md) for implementation details.

## Migration and interoperability

If you are planning to deploy Skype for Business Server 2019 and/or Exchange Server 2019, you must plan your migration carefully to ensure continued support for call queues. Keep the following in mind:

- Exchange Server 2019 no longer provides Exchange UM functionality
- Skype for Business Server 2019 no longer integrates with Exchange Online UM

Version interoperability and supported topologies for Cloud call queues are listed in the following table. For the preview release, Cloud call queues only work with Skype for Business Server 2019 and Exchange Server 2019 or Exchange Online.


| | Exchange Server 2013 | Exchange Server 2016 | Exchange Server 2019 | Exchange Online |
|:---    |:---|:---|:---|:--- |
| Skype for Business Server 2019 | Exchange Server UM | Exchange Server UM | Cloud call queue | Cloud call queue
Skype for Business Server 2015 | Exchange Server UM | Exchange Server UM |Not supported  | Cloud call queue <br> Exchange Online UM* |
Lync Server 2013  | Exchange Server UM | Exchange Server UM |Not supported | Cloud call queue <br> Exchange Online UM* |

\* Until deprecated.

Microsoft recommends the following migration paths:

- If you are upgrading to Skype for Business Server 2019, you can use Exchange UM in Exchange Server 2013 or 2016, but you must upgrade to Cloud auto attendant if you are using Exchange Server 2019.

- If you are upgrading to Exchange Server 2019, and you are using previous versions of Exchange Server UM for Skype for Business Server voice messaging, Microsoft recommends that you upgrade to Skype for Business Server 2019 before the mailbox upgrade.  Otherwise, voice messaging capabilities will be lost. 

For more information about planning your migration, see [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md).

### Migrating a previously implemented Exchange UM call queue

Currently we don't support automated migration to the Cloud of a UM call queue created in Exchange 2013 or 2016. To manually re-create a call queue, you'll need to:

1. Use Exchange admin powershell commands to review the structure of the old auto attendant system, including any nested auto attendants and call queues.  
2. Create copies of text-to-speech scripts or recorded messages associated with each UM call queue node.
3. Create on premise endpoints for each call queue, including assigning a test phone numbers and licenses to the objects. Note that you now have the ability to assign on-premise phone numbers licenses used by online services like Phone System.
4. Implement a new Cloud call queue service with Skype for Business Online and Phone System. See [Configure cloud auto attendant](configure-cloud-auto-attendant.md) for implementation details. As you do this, upload the text-to-speech scripts or recorded messages associated with each call queue.
5. Test the functionality of the Cloud call queue.
6. Reassign the phone number assigned to the old Exchange UM call queue to the newly created Cloud call queue (it's possible it doesn't have a phone number, as call queues are often used in combination with auto attendants).

See [Manually moving an Exchange UM auto attendant to Cloud auto attendant](configure-cloud-auto-attendant.md#manually-moving-an-exchange-um-auto-attendant-to-cloud-auto-attendant) for details on these steps.

## Additional planning resources

The tutorial titled [Small business example - Set up an auto attendant](/microsoftteams/tutorial-org-aa) goes through the process of gathering information about user needs, planning a structure of auto attendants and users (and possibly call queues), writing the menu prompts, and implementing the plan in the Online Admin center. review the tutorial and use the exercises there t create your plan.

When you have a solid structure that meets your needs and a script that guides customers efficiently, proceed to [Configure Cloud call queues](configure-call-queue.md).

> [!CAUTION]
> As mentioned in [KB4480742](https://support.microsoft.com/en-us/help/4480742/call-failures-and-500-server-internal-error-after-migration-to-2019), moving Exchange UM auto attendants created in Server 2015 to servers running Server 2019 is discouraged. For the time being, you'd have to keep them on a Skype for Business Server 2015 pool running in coexistence mode.

## See Also

[Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md)

[Configure Cloud auto attendant](configure-cloud-auto-attendant.md)

[Configure Cloud call queues](configure-call-queue.md)

[Enable custom prompt recording using the telephone user interface](https://docs.microsoft.com/exchange/voice-mail-unified-messaging/greetings-announcements-menus-and-prompts/enable-custom-prompt-recording)

[What are Cloud auto attendants?](/SkypeForBusiness/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants)

[Set up a Cloud auto attendant](/MicrosoftTeams/create-a-phone-system-auto-attendant)

Exchange UM: [Automatically answer and route incoming calls](https://docs.microsoft.com/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/automatically-answer-and-route-calls)

[Plan hybrid connectivity between Skype for Business Server and Office 365](plan-hybrid-connectivity.md)

[Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md)

[Manage resource accounts in Microsoft Teams](/MicrosoftTeams/manage-resource-accounts)
