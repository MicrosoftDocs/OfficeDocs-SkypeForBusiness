---
title: "Plan a Cloud auto attendant"
ms.author: jambirk
author: jambirk
manager: serdars 
ms.reviewer: wasseemh
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Overview of using a Cloud auto attendant with Skype for Business Server 2019"
---

# Plan Cloud auto attendants

The auto attendant used with Exchange Unified Messaging (Exchange Server 2013 or Exchange Server 2016) is no longer available in Exchange Server 2019 or Exchange Online. If your implementation of Skype for Business Server 2019 integrates with either of these Exchange versions, you'll need to use the online Cloud Voice features associated with Phone System. See [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md) for information about moving Exchange UM services homed on Exchange server 2013 and 2016 to the cloud.

This inherently means that you will have a hybrid implementation of Skype for Business Server 2019 if you wish to use Unified Messaging features like auto attendants. See [Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md) for details.

An auto attendant can include a greeting the caller can't interact with (this can be a different message during office hours and outside office hours) and menu choices the users can interact with either with a voice response or by pressing a telephone keypad. The options can connect callers to employees, an Operator, call queues used by entire departments, and other auto attendants that act as sub-menus to a main auto attendant. Each auto attendant is assigned a **resource account** (see[Configure resource accounts](configure-onprem-ra.md)) on your Skype for Business Server 2019 system that will be linked directly to an auto attendant in the Microsoft Teams admin center. See [What are Cloud auto attendants?](/SkypeForBusiness/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants.md) for more detail on what auto attendants are and what options and features exist for auto attendants.

> [!NOTE]
> You are now able to link multiple inbound phone numbers to a single Cloud auto attendant.

An incoming call to a Cloud auto attendant can take one of several paths, as shown here:

![Diagram for auto attendants](../../SfBServer2019/media/AA-plan-concept.png)

1. Via Skype for Business Server 2019
2. Via a [Session Border Controller](/MicrosoftTeams/direct-routing-border-controllers.md) and [Direct Routing](/MicrosoftTeams/direct-routing-plan.md)
3. Via a number homed online in Office 365.

Your implementation might involve one or two of these paths, but it's unlikely your implementation will need all three.

Also see:

- [Set up a Cloud auto attendant](/microsoftteams/create-a-phone-system-auto-attendant)
- [Automatically answer and route incoming calls](https://docs.microsoft.com/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/automatically-answer-and-route-calls)

## Requirements

The following requirements assume that you already have Skype for Business Server 2019 deployed in a supported topology.  Your requirements depend on your scenario:

- If you are already using Exchange UM online or on premises and you upgrade to Skype for Business 2019, you will need to capture the structure of your Auto attendants and re-create them in the cloud using Cloud auto attendants. For more information, see [Manually moving an Exchange UM auto attendant or call queue to Phone System](configure-onprem-ra.md#manually-moving-an-exchange-um-auto-attendant-or-call-queue-to-phone-system).

- For a new configuration of Cloud auto attendants, follow the steps outlined in  [Configure resource accounts](configure-onprem-ra.md).

In addition to the requirements above, the below requirements must be configured to connect to the Microsoft Cloud auto attendant service:

- Hybrid connectivity. If you already have Skype for Business Server deployed, and you want to enable Cloud auto attendant for your on-premises users, you must ensure that you have hybrid connectivity set up between your on-premises and online environments. This is sometimes called a split domain configuration.

   For more information, see [Plan hybrid connectivity between Skype for Business Server and Office 365](plan-hybrid-connectivity.md) and [Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md).

- For phone numbers that you assign to your auto attendant, you will need an [Office 365 Enterprise E5](/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/office-365-enterprise-e5-with-audio-conferencing) license.
- If you have an on-premises only deployment (that is, only Exchange Server 2019 and Skype for Business Server 2019 on-premises servers) but you want to take advantage of Cloud auto attendant, you need the appropriate license.
- Create an on-premises [resource account](/MicrosoftTeams/manage-resource-accounts.md) for each auto attendant, including assigning phone numbers and licenses. Note that you now have the ability to assign licenses used by online services like Phone System to on-premise phone numbers.
- Implement a new Cloud auto attendant service with Skype for Business Online and Phone System. See [Configure resource accounts](configure-onprem-ra.md) for implementation details.

## Migration and interoperability

If you are planning to deploy Skype for Business Server 2019 and/or Exchange Server 2019, you must plan your migration carefully to ensure continued support for auto attendants. Keep the following in mind:

- Exchange Server 2019 no longer provides Exchange UM functionality
- Skype for Business Server 2019 no longer integrates with Exchange Online UM

Version interoperability and supported topologies for Cloud auto attendants are listed in the following table. For the preview release, Cloud auto attendants only work with Skype for Business Server 2019 and Exchange Server 2019 or Exchange Online.

| | Exchange Server 2013 | Exchange Server 2016 | Exchange Server 2019 | Exchange Online |
|:---    |:---|:---|:---|:--- |
| Skype for Business Server 2019 | Exchange Server UM | Exchange Server UM | Cloud auto attendant | Cloud auto attendant
Skype for Business Server 2015 | Exchange Server UM | Exchange Server UM |Not supported  | Cloud auto attendant <br> Exchange Online UM* |
Lync Server 2013  | Exchange Server UM | Exchange Server UM |Not supported | Cloud auto attendant <br> Exchange Online UM* |

\* Until deprecated.

Microsoft recommends the following migration paths:

- If you are upgrading to Skype for Business Server 2019, you can use Exchange UM in Exchange Server 2013 or 2016, but you must upgrade to Cloud auto attendant if you are using Exchange Server 2019.

- If you are upgrading to Exchange Server 2019, and you are using previous versions of Exchange Server UM for Skype for Business Server voice messaging, Microsoft recommends that you upgrade to Skype for Business Server 2019 before the mailbox upgrade.  Otherwise, voice messaging capabilities will be lost.

For more information about planning your migration, see [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md).

### Migrating a previously implemented Exchange UM auto attendant system

Currently we don't support automated migration to the Cloud of a UM auto attendant system created in Exchange 2013 or 2016. To manually re-create an auto attendant system, you'll need to:

1. Use Exchange admin powershell commands to review the structure of the old auto attendant system, including any nested auto attendants and call queues.  
2. Create copies of text-to-speech scripts or recorded messages associated with each UM auto attendant node.
3. Create on premise endpoints for each auto attendant node, including assigning a test phone numbers and licenses to the objects. Note that you now have the ability to assign on-premise phone numbers licenses used by online services like Phone System.
4. Implement a new Cloud auto attendant service with Skype for Business Online and Phone System. See [Configure resource accounts](configure-onprem-ra.md) for implementation details. As you do this, upload the text-to-speech scripts or recorded messages associated with each UM auto attendant node.
5. Test the functionality of the Cloud auto attendant.
6. Reassign the phone number assigned to the old Exchange UM auto attendant to the newly created main Cloud auto attendant.

See [Manually moving an Exchange UM auto attendant or call queue to Phone System](configure-onprem-ra.md#manually-moving-an-exchange-um-auto-attendant-or-call-queue-to-phone-system) for details on these steps.

## Additional planning resources

The tutorial titled [Small business example - Set up an auto attendant](/microsoftteams/tutorial-org-aa) goes through the process of gathering information about user needs, planning a structure of auto attendants and users (and possibly call queues), writing the menu prompts, and implementing the plan in the Online Admin center. review the tutorial and use the exercises there to create your plan.

When you have a solid structure that meets your needs and a script that guides customers efficiently, proceed to [Configure resource accounts](configure-onprem-ra.md).

> [!CAUTION]
> As mentioned in [KB4480742](https://support.microsoft.com/en-us/help/4480742/call-failures-and-500-server-internal-error-after-migration-to-2019), moving Exchange UM auto attendants created in Server 2015 to servers running Server 2019 is discouraged. For the time being, you'd have to keep them on a Skype for Business Server 2015 pool running in coexistance mode.

## See Also

[Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md)

[Configure resource accounts](configure-onprem-ra.md)

[Enable custom prompt recording using the telephone user interface](https://docs.microsoft.com/exchange/voice-mail-unified-messaging/greetings-announcements-menus-and-prompts/enable-custom-prompt-recording)

[What are Cloud auto attendants?](/SkypeForBusiness/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants)

[Set up a Cloud auto attendant](/microsoftteams/create-a-phone-system-auto-attendant)

Exchange UM: [Automatically answer and route incoming calls](https://docs.microsoft.com/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/automatically-answer-and-route-calls)

[Plan hybrid connectivity between Skype for Business Server and Office 365](plan-hybrid-connectivity.md)

[Configure hybrid connectivity between Skype for Business Server and Office 365](configure-hybrid-connectivity.md)

[KB4480742: Calls to Subscriber Access or auto attendant fail with fast busy and “500 Server Internal" error after moving contact objects to Skype for Business Server 2019](https://support.microsoft.com/help/4480742/call-failures-and-500-server-internal-error-after-migration-to-2019)
