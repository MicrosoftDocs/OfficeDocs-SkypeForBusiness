---
title: "Plan a Cloud auto attendant"
ms.author: crowe
author: CarolynRowe
manager: serdars 
ms.reviewer: wasseemh
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.collection: 
description: "Overview of using a Cloud auto attendant with Skype for Business Server 2019"
---

# Plan Cloud auto attendants

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

The auto attendant used with Exchange Unified Messaging (Exchange Server 2013 or Exchange Server 2016) is no longer available in Exchange Server 2019 or Exchange Online. If your implementation of Skype for Business Server 2019 integrates with either of these Exchange versions, you'll need to use the online Cloud Voice features associated with Phone System. See [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md) for information about moving Exchange UM services homed on Exchange server 2013 and 2016 to the cloud.

This inherently means that you will have a hybrid implementation of Skype for Business Server 2019 if you wish to use Unified Messaging features like auto attendants. See [Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](configure-hybrid-connectivity.md) for details.

An auto attendant is a cloud service that accepts customer calls and plays greetings, provides them with menu options, and interacts with callers using speech or the dial pad to route their calls to the right destination. Each auto attendant is assigned a *resource account* (see [Configure resource accounts](configure-onprem-ra.md)) on your Skype for Business Server 2019 system that will be linked directly to an auto attendant in the Microsoft Teams admin center. See [Set up an auto attendant](/microsoftteams/create-a-phone-system-auto-attendant) for more detail on what auto attendants are and what options and features exist for auto attendants.

> [!NOTE]
> You can assign multiple Microsoft service numbers, Direct Routing numbers, or hybrid numbers to an auto attendant.

An incoming call to a Cloud auto attendant can take one of several paths, as shown here:

![Diagram for auto attendants.](../../SfBServer2019/media/AA-plan-concept.png)

1. Via Skype for Business Server 2019
2. Via a [Session Border Controller](/microsoftteams/direct-routing-border-controllers) and [Direct Routing](/microsoftteams/direct-routing-plan-media-bypass).
3. Via a number homed online in Microsoft 365 or Office 365.

Also see:

- [Set up a Cloud auto attendant](/microsoftteams/create-a-phone-system-auto-attendant)
- [Automatically answer and route incoming calls](/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/automatically-answer-and-route-calls)

## Requirements

The following requirements assume that you already have Skype for Business Server 2019 deployed in a supported topology.  Your requirements depend on your scenario:

- If you are already using Exchange UM online or on-premises and you upgrade to Skype for Business 2019, you will need to capture the structure of your Auto attendants and re-create them in the cloud using Cloud auto attendants. For more information, see [Moving an Exchange UM auto attendant or call queue to Phone System](configure-onprem-ra.md#moving-an-exchange-um-auto-attendant-or-call-queue-to-phone-system).

- For a new configuration of Cloud auto attendants, follow the steps outlined in  [Configure resource accounts](configure-onprem-ra.md).

In addition to the requirements above, the below requirements must be configured to connect to the Microsoft Cloud auto attendant service:

- Hybrid connectivity. If you already have Skype for Business Server deployed, and you want to enable Cloud auto attendant for your on-premises users, you must ensure that you have hybrid connectivity set up between your on-premises and online environments. This is sometimes called a split domain configuration.

   For more information, see [Plan hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](plan-hybrid-connectivity.md) and [Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](configure-hybrid-connectivity.md).

- If you're assigning a phone number to to your auto attendant, you will need an [Office 365 Enterprise E5](../../SfbOnline/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/office-365-enterprise-e5-with-audio-conferencing.md) license.
- Create an online [resource account](/MicrosoftTeams/manage-resource-accounts) or on-premises [resource account](configure-onprem-ra.md) for each auto attendant, and assign phone numbers and licenses. 

## Migration and interoperability

If you are planning to deploy Skype for Business Server 2019 and/or Exchange Server 2019, you must plan your migration carefully to ensure continued support for auto attendants. Keep the following in mind:

- Exchange Server 2019 no longer provides Exchange UM functionality
- Exchange Unified Messaging is in retirement mode
- Skype for Business Server 2019 no longer integrates with Exchange Online UM

Cloud auto attendants can be configured with Skype for Business Server 2019, 2015, and 2013.

Microsoft recommends the following migration paths:

- If you are upgrading to Skype for Business Server 2019, you can use Exchange UM in Exchange Server 2013 or 2016, but you must upgrade to Cloud auto attendant if you are using Exchange Server 2019.

- If you are upgrading to Exchange Server 2019, and you are using previous versions of Exchange Server UM for Skype for Business Server voice messaging, Microsoft recommends that you upgrade to Skype for Business Server 2019 before the mailbox upgrade.  Otherwise, voice messaging capabilities will be lost.

For more information about planning your migration, see [Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md).

### Migrating a previously implemented Exchange UM auto attendant system

Currently we don't support automated migration to the Cloud of a UM auto attendant system created in Exchange 2013 or 2016. To manually re-create an auto attendant system, you'll need to:

1. Use Exchange admin PowerShell commands to review the structure of the old auto attendant system, including any nested auto attendants and call queues.  
2. Create copies of text-to-speech scripts or recorded messages associated with each UM auto attendant node.
3. Create on premise endpoints for each auto attendant node, including assigning a test phone numbers and licenses to the objects. Note that you now have the ability to assign on-premise phone numbers licenses used by online services like Phone System.
4. Implement a new Cloud auto attendant service with Microsoft Teams and Phone System. See [Configure resource accounts](configure-onprem-ra.md) for implementation details. As you do this, upload the text-to-speech scripts or recorded messages associated with each UM auto attendant node.
5. Test the functionality of the Cloud auto attendant.
6. Reassign the phone number assigned to the old Exchange UM auto attendant to the newly created main Cloud auto attendant.

See [Moving an Exchange UM auto attendant or call queue to Phone System](configure-onprem-ra.md#moving-an-exchange-um-auto-attendant-or-call-queue-to-phone-system) for details on these steps.

When you have a solid structure that meets your needs and a script that guides customers efficiently, proceed to [Configure resource accounts](configure-onprem-ra.md).

> [!CAUTION]
> As mentioned in [KB4480742](https://support.microsoft.com/help/4480742/call-failures-and-500-server-internal-error-after-migration-to-2019), moving Exchange UM auto attendants created in Server 2015 to servers running Server 2019 is discouraged. For the time being, you'd have to keep them on a Skype for Business Server 2015 pool running in coexistance mode.

## See Also

[Plan for Skype for Business Server and Exchange Server migration](plan-um-migration.md)

[Configure resource accounts](configure-onprem-ra.md)

[Enable custom prompt recording using the telephone user interface](/exchange/voice-mail-unified-messaging/greetings-announcements-menus-and-prompts/enable-custom-prompt-recording)

[What are Cloud auto attendants?](/SkypeForBusiness/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants)

[Set up a Cloud auto attendant](/microsoftteams/create-a-phone-system-auto-attendant)

Exchange UM: [Automatically answer and route incoming calls](/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/automatically-answer-and-route-calls)

[Plan hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](plan-hybrid-connectivity.md)

[Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](configure-hybrid-connectivity.md)

[KB4480742: Calls to Subscriber Access or auto attendant fail with fast busy and “500 Server Internal" error after moving contact objects to Skype for Business Server 2019](https://support.microsoft.com/help/4480742/call-failures-and-500-server-internal-error-after-migration-to-2019)
