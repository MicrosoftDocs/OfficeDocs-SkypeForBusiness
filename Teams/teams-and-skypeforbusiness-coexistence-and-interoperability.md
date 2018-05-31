---
title: Microsoft Teams and Skype for Business coexistence and interoperability
author: arachmanGitHub
ms.author: MyAdvisor
manager: serdars
ms.date: 05/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: lehewe
description: Details of coexistence modes to choose from as you upgrade from Skype for Business to Microsoft Teams, and how they interact with interoperability.
localization_priority: Priority
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

![Stages of the upgrade journey, with emphasis on Technical Readiness](media/upgrade-banner-tech-readiness.png "Stages of the upgrade journey, with emphasis on Technical Readiness")

This article is part of the Technical Readiness stage of your upgrade journey, an activity you complete in parallel with the User Readiness stage. 

# Microsoft Teams and Skype for Business coexistence and interoperability

If your organization uses Skype for Business today and you intend to start using Teams alongside Skype for Business—or you intend to start upgrading to Teams—it's important to understand how the two applications coexist, when and how they interoperate, and how to manage users’ migration all the way to their eventual upgrade from Skype for Business to Teams.

> [!Note]
> Before taking a deeper look into the coexistence and interoperability of Teams and Skype for Business, you should become familiar with the concepts of coexistence and upgrade journeys, in addition to the coexistence modes described in this article, to help you choose the best upgrade journey for your organization. For more information, see [Understand coexistence and upgrade journeys for Skype for Business and Microsoft Teams](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md). 
 
## Coexistence of Teams and Skype for Business

In addition to collaboration capabilities, Teams delivers chat, calling, and meeting capabilities. Depending on how you choose to deploy Teams alongside Skype for Business, these capabilities might overlap with the capabilities delivered by Skype for Business for a given user. In addition to the default mode of running Teams alongside Skype for Business, a user can be assigned one of several coexistence modes that were designed to ensure that these capabilities don’t overlap for that user.

By default, users can run Teams alongside Skype for Business as two separate solutions that deliver similar and overlapping capabilities such as chat, calling, and meetings in addition to Teams-specific collaboration capabilities such as teams and channels, access to files in Office 365, and applications.

This coexistence mode is called Islands, to express the notion that each of the client applications operates as a separate island. Skype for Business talks to Skype for Business, and Teams talks to Teams. There’s no need for interoperability in Islands mode, because users run both clients and can communicate natively in the client from which the communication was initiated.
The vast majority of organizations—in particular, virtually all Skype for Business Online customers—are likely to deploy Islands mode. If you plan to move to Teams fairly rapidly and you don’t expect to support coexistence for long, you should consider Islands.

If the default Islands coexistence mode doesn’t meet the needs of your organization, you can assign another coexistence mode to a given user. This situation should only apply to a small subset of customers who anticipate having an extended period of coexistence because they have a very complex deployment or requirements, such as on-premises—and in particular, enterprise voice—deployments. These other coexistence modes are all designed to ensure that there will be no overlapping capability between Teams and Skype for Business for a given user. These modes can be assigned to any or all users, and multiple modes can coexist in one organization. A user who has been assigned one of these other coexistence modes needs interoperability to receive communications sent to them from a different client, because they only have one client capable of receiving that communication. The additional coexistence modes are:

-   **Skype for Business with Teams collaboration**: Use this mode to enable very rapid deployment of Teams collaboration with minimal user disruption. A simple initial step you can take is to leave Skype for Business unchanged with chat, calling, and scheduling meetings, and add Teams collaboration capabilities—teams and channels, access to files in Office 365, and applications.
-   **Skype for Business with Teams collaboration and meetings**: Use this coexistence mode to accelerate the delivery of Teams meetings capabilities in your organization, so you can take advantage of the great quality and new capabilities such as transcription and translation, and support for meetings in browsers.<br>Using Teams for collaboration and meetings while retaining Skype for Business for chat and calling is especially useful for users in Skype for Business on-premises deployments that have enterprise voice, who are likely to take some time to be upgraded to Teams or might even stay in an on-premises deployment for the foreseeable future. Users who aren’t in enterprise voice deployments will probably not need this step and can be upgraded directly to Teams, as explained below.
-   **Teams only**: In this coexistence mode, users use Teams for all its capabilities.<br>As soon as your organization is ready for some or all users to use Teams as their only communications and collaboration tool, you can upgrade those users to this mode. If the Skype for Business client remains present and running, it runs in a special mode that only lets it join Skype for Business meetings but doesn’t offer the ability to initiate chat, calling, or meetings.
-   **Skype for Business only**: In this coexistence mode, users continue to use chat and calling capabilities in Skype for Business rather than Teams, and they don’t use Teams for teams and channels.<br>If some users need to keep using Skype for Business and can’t use teams and channels for the foreseeable future due to specific business needs—such as compliance requirements that can’t be met by Teams now, or readiness initiatives that aren’t yet complete—you can assign this coexistence mode to those users. Users can be licensed for Teams or not, and Teams can be present to enable the users to join meetings created in Teams by other users; you can also decide to let the users run Teams-based applications. Skype for Business only coexistence mode might also be useful as an initial starting point if you prefer not to deploy Islands mode until you’ve given users appropriate training and information; at that point, you might assign them (for example) Skype for Business with Teams collaboration coexistence mode.<br>This mode is expected to be used only in rare cases or for very short periods of time.

Each of these coexistence modes can be assigned to any user or any group of users (also called a _cohort_). A given user might be assigned a succession of different modes, for example from Islands to Teams only, or from Skype for Business with Teams collaboration to Skype for Business with Teams collaboration and meetings to Teams only. Planning for assigning coexistence modes should be part of your organization’s upgrade journey. As you decide which type of upgrade journey you’ll choose, be sure to include the following discussion points during the planning session for your organization:

-   Length of time that Skype for Business and Teams will have to coexist
-   Considerations for a large organization with a complex on-premises enterprise voice deployment
-   Requirement for interoperability at all times
-   Compliance requirements
-   Don’t want overlapping unified communications workloads
-   Third-party integration points

> [!Note]
> When deployed in specific coexistence modes, Teams and Skype for Business can interoperate, enabling users to chat with and call one another, and ensuring that communications remain fluid across your organization during your upgrade journey to Teams.
> Coexistence modes govern interoperability. The coexistence mode of the receiver is what is assessed to determine whether interoperability will be available.
> For example, if the receiver is in a mode in which chat is only available in one client (say, Teams), chat interoperability will generally be available in case the initiator uses the other client (in this case, Skype for Business) to start the chat. On the other hand, if the receiver is in a mode in which chat is available in both clients, interoperability won’t be available for the chat—and the message will be received by the receiver in the same client in which the initiator started the chat.

For more details about coexistence modes, prerequisites, and management, see [Migration and interoperability guidance for organizations using Teams together with Skype for Business](https://docs.microsoft.com/MicrosoftTeams/migration-interop-guidance-for-teams-with-skype).

> [!Important]
> Introducing new technology—or making changes to your existing, familiar Skype for Business environment—can be disruptive for users. Take time to assess user readiness, and implement a communication and training plan before you implement any of the changes outlined in this article. In addition, we strongly encourage you to pilot your plan with a selected group of users before implementing it across your organization.

## Interoperability of Teams and Skype for Business

Interoperability is the ability for Teams and Skype for Business users in the same organization to communicate across Teams and Skype for Business.

### Native interop and interop escalation experience - MAYBE NOT NECESSARY HEADING?

There are two types of interop experiences: native and interop escalation.

-   A _native interop_ experience occurs in the client that the user is currently using. One user will be in the Skype for Business client, the other in Teams. A native interop experience won’t take them to another client to communicate, the users will be able to conduct their conversation in the client they’re currently using. The native interop experiences are one-to-one chat and calling.
-   An _interop escalation_ experience means that as part of helping users perform an advanced action (such as sharing their desktop), the service can facilitate the creation of a meeting and continue the experience in that meeting. The meeting is created on the platform of the initiator of the action. The user or users who aren’t on that platform receive meeting join coordinates and join the meeting (switching client).

### Native interop experiences

Depending on the coexistence modes assigned to users (as described above), the following native interop experiences are possible:

-   Skype for Business users can chat one-on-one with Teams users, and vice versa. An interop chat needs to go through an interop gateway that’s part of Teams cloud services (and therefore only exists online). Interop chats are plain text: rich text and emoticons aren’t supported. Users in Teams are notified that the conversation is an interop conversation; a similar notification for Skype for Business users will be provided soon.<br>GRAPHIC GOES HERE
-   Skype for Business users can make one-on-one voice and video calls to Teams users, and vice versa.<br>GRAPHIC GOES HERE

### Native interop experience limitations

Some features aren’t available for the interop chat and interop calling experience between Teams and Skype for Business:

-   Markdown, rich text, and the full emoticon set aren’t supported either from Teams or Skype for Business. Other native features of the compose box in Teams chats aren’t supported.
-   Screen sharing (desktop or app sharing) between Teams and Skype for Business isn’t supported natively.
-   Group chats (multiple-party conversations) in Teams can only include participants who are using Teams.
-   Multiple-party IM conversations (group chats) in Skype for Business can only include participants who are using Skype for Business.
-   Escalating an ongoing peer-to-peer voice or video call to a multiple-party call involving both Teams and Skype for Business users isn’t supported natively.
-   File transfer for two-party chats, or file attachment in group chats, from Teams to Skype for Business—and vice versa—aren’t supported.
-   There is no interoperability with Skype for Business persistent chat.

For all these limitations (except for persistent chat), one possible workaround is for one user to start a meeting and invite the other user to join it. This workaround is the basis for interop escalation.

### Interop escalation experiences

For the workaround described above, we intend to provide interop escalation scenarios where meeting creation will be facilitated. The facilitation will remove as many manual steps from the process as possible; however, the target user will have to manually join the meeting (typically by clicking a link).

For example, a user who is currently in a native interop conversation takes an action that isn’t natively supported (in this case, sharing their desktop). The intent of the interop escalation scenario is to provide the following: prepare a meeting silently on the platform of the initiator, and then send the other participant a link and instructions on how to join the meeting. After the users have joined the meeting, the existing call is terminated and the initiator is joined to the meeting. Desktop sharing then starts automatically.

The scenarios currently considered for interop escalation are:

-   Desktop sharing in a native interop conversation.
-   Escalation of a native interop conversation into a multiple-party conversation.
-   Escalation of a non-interop conversation (Teams-to-Teams or Skype for Business–to–Skype for Business) into a multiple-party conversation in which at least one participant isn’t on the same client.
-   Ad-hoc invitation to a meeting in which at least one participant is on a different platform from the originator. 

> [!Important]
> These interop escalation scenarios represent our current thinking and are subject to change.

