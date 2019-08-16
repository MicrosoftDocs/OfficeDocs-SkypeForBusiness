---
title: Microsoft Teams | Upgrade, Islands Mode, Interop Policy,  Only 
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: dearbeen
description: Details of Skype for Business and Microsoft Teams coexistence options and interoperability between Skype for Business and Teams. 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

![Upgrade journey diagram, emphasizing the Project Definition stage](media/upgrade-banner-project-definition.png "Stages of the upgrade journey, with emphasis on the Project Definition stage")

This article is part of the Project Definition stage of your upgrade journey, an activity you complete after you create a sponsorship coalition and project team and define the scope, goals, and vision for your project. Before proceeding, confirm that you’ve completed the following activities:

- [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
- [Defined your project scope](https://aka.ms/SkypetoTeams-Scope)

# Understand Microsoft Teams and Skype for Business coexistence and interoperability

If your organization uses Skype for Business today and you are starting to use Teams alongside Skype for Business—or you are starting to upgrade to Teams—it’s important to understand how the two applications coexist, when and how they interoperate, and how to manage users’ migration all the way to their eventual upgrade from Skype for Business to Teams.

> [!Tip]
> Watch the following session to learn about [Coexistence and Interoperability](https://aka.ms/teams-upgrade-coexistence-interop).
>
> Additionally, you can join us for live, interactive workshops in which we’ll share guidance, best practices, and resources designed to kick start upgrade planning and implementation.
>
> Join the [Plan your upgrade](https://aka.ms/SkypeToTeamsPlanning) session first to get started.

## Coexistence of Teams and Skype for Business

In addition to collaboration capabilities, Teams delivers chat, calling, and meeting capabilities. Depending on how you choose to deploy Teams, these capabilities may overlap with the capabilities delivered by Skype for Business for a given user. The default mode is to run Teams alongside Skype for Business with the capabilities overlap; however, a user can be assigned one of several coexistence modes (also known as upgrade modes) that were designed to ensure that these capabilities don’t overlap for that user (in which case interoperability between Teams and Skype for Business is available). For example, if you have significant Skype for Business Server on-premises assets with a complex Enterprise Voice deployment but want your users to enjoy modern meetings as quickly as possible, you might want to evaluate Meetings First (as described below) as an alternative path.

We recommend that you review the following coexistence modes to help determine which path is right for your organization.

> [!Important]
> Introducing new technology or making changes to your existing, familiar Skype for Business environment, while delivering great new business benefits, can be disruptive for users. Take time to assess user readiness and implement a communication and training plan before you implement any of the changes outlined in this article. In addition, we strongly encourage you to pilot your plan with a selected group of users before implementing it across your organization.

### Islands mode

By default, users can run Teams alongside Skype for Business as two separate solutions that deliver similar and overlapping capabilities such as presence, chat, calling, and meetings. Teams users also can take advantage of new collaboration capabilities such as teams and channels, access to files in Office 365, and applications.

In this coexistence mode, called **Islands**, each of the client applications operates as a separate island. Skype for Business talks to Skype for Business, and Teams talks to Teams. Users are expected to run both clients at all times and can communicate natively in the client from which the communication was initiated. As such, there’s no need for interoperability in **Islands** mode.

To avoid a confusing or regressed Skype for Business experience, external (federated) communications, PSTN voice services and voice applications, Office integration, HID controls for USB devices, and several other integrations continue to be handled by Skype for Business and are not available in Teams in **Islands** mode. Phone System is not supported in Teams in **Islands** mode; in this mode, the only Enterprise Voice client is Skype for Business.

> [!Important]
> In **Islands** mode, all messages and calls from federated users (people outside your organization) are delivered to Skype for Business. After upgrading to **Teams Only** mode, all messages and calls from outside your organization are delivered to Teams.

> [!Tip]
> Skype for Business Online customers recommended path is to start with the default **Islands** mode, drive Teams adoption saturation in the organization, and then move to **Teams Only** mode rapidly. On premises and hybrid customers, especially complex ones, might benefit from deploying the **Skype for Business with Teams Collaboration** mode as a starting point rather than **Islands** mode, and progress from there to **Skype for Business with Teams Collaboration and Meetings** mode (that is, Meetings First), if appropriate, and to **Teams Only** mode when the organization is ready to adopt Teams.

### Skype for Business only

In this coexistence mode, users remain in Skype for Business—not Teams—for chat, meeting, and calling capabilities, and they don’t use Teams for teams and channels. This mode is available today; however, in the current implementation, teams and channels are not automatically turned off for the user. This can be achieved by using the App Permissions policy to hide teams and channels.

This mode can be used prior to starting a managed deployment of Teams to prevent users from starting to use Teams ahead of having built readiness, or as a way to enable authenticated participation in Teams meetings for Skype for Business users, provided the users are licensed for Teams.

### Teams Only

A **Teams Only** user (also called an *upgraded* user) has access to all the capabilities in Teams. They may retain the Skype for Business client to join meetings on Skype for Business that have been organized by non-upgraded users or external parties. An upgraded user can continue to communicate with other users in the organization who are still using Skype for Business by using the interoperability capabilities between Teams and Skype for Business (provided these Skype for Business users are not in **Islands** mode). However, an upgraded user can't initiate a Skype for Business chat, call, or meeting.

As soon as your organization is ready for some or all users to use Teams as their only communications and collaboration tool, you can upgrade those users to **Teams Only** mode. If you are upgrading from **Islands** mode, we advise that you first saturate Teams adoption throughout your organization before beginning the upgrade process. This avoids broken communication scenarios due to **Islands** mode not providing interoperability.

For additional considerations about moving to **Teams Only** mode, see [Teams Only mode considerations](teams-only-mode-considerations.md).

![Screen shot of Teams confirmation message](media/teams-and-skypeforbusiness-coexistence-and-interop-image1.png "Skype for Business client running in a special mode after the user is upgraded as a Teams-only user")

### Skype for Business with Teams Collaboration

Use this mode to introduce Teams in your environment while you continue to leverage your existing investment in Skype for Business. In this mode, you leave Skype for Business unchanged for chat, calling, and meeting capabilities, and you add Teams collaboration capabilities—teams and channels, access to files in Office 365, and applications. Teams communications capabilities—private chat, calling, and scheduling meetings—are off by default in this mode.

Organizations with a starting point of Skype for Business Server on premises or hybrid should consider this mode as an alternative to **Islands** mode if they want to give their users interoperability and predictability for their communications, as well as having a predictable timeline for their upgrade to Teams (as opposed to relying on adoption saturation in **Islands** mode).

### Skype for Business with Teams Collaboration and Meetings, also known as Meetings First

Use this coexistence mode to accelerate the availability of Teams meeting capabilities in your organization, in addition to its collaboration capabilities, enabling your users to take advantage of the superior Teams meetings experience-great quality, innovative capabilities such as transcription and translation or background blurring, and superior user experience across all platforms, including mobile devices and browsers.

Along with using Teams for teams and channels–based conversations in this mode, users will use Teams to schedule and conduct their meetings. Private chat and calling remain on Skype for Business. Teams and Skype for Business benefit from a range of “better together” capabilities, such as presence reconciliation, automatic hold/unhold, and HID device support across both applications. Note that it is possible to hide teams and channels if desired using the App Permissions policy.

This coexistence mode is especially useful for organiztions with Skype for Business on-premises deployments with Enterprise Voice, who are likely to take some time to upgrade to Teams and want to benefit from the superior Teams meetings as soon as possible.

> [!Note]
> When deployed in any coexistence mode except **Islands**, Teams and Skype for Business can [interoperate](#interoperability-of-teams-and-skype-for-business), enabling users to chat with and call one another, and ensuring that communications remain fluid across your organization during your upgrade journey to Teams. Coexistence modes govern interoperability. The coexistence mode of the receiver determines whether interoperability will be available. For example, if the receiver is in a mode in which chat is only available in one client (say, Teams), chat interoperability will generally be available in case the initiator uses the other client (in this case, Skype for Business) to start the chat. On the other hand, if the receiver is in the mode in which chat is available in both clients (Islands mode), interoperability won’t be available for the chat. The message will be received by the receiver in the same client in which the initiator started the chat. Therefore, proper communication in **Islands** mode requires Teams adoption saturation; that is, all users actively using and monitoring both clients.

> [!TIP]
> To help identify the recommended upgrade mode based on the capabilities you want to enable in Teams while Skype for Business is still in use, leverage the [Skype to Teams Upgrade Wizard](https://aka.ms/SkypeToTeamsWizard).

For more details about coexistence modes, prerequisites, and management, see [Migration and interoperability guidance for organizations using Teams together with Skype for Business](https://aka.ms/SkypeToTeams-Interop) and [Setting your coexistence and upgrade settings](https://aka.ms/SkypeToTeams-SetCoexistence).

| | | |
|---|---|---|
|<img src="media/audio_conferencing_image7.png" alt= "An icon depicting a decision point"/>|Decision point|<ul><li>Which coexistence mode(s) best fit your organization’s and users’ needs?</li></ul>|
|<img src="media/audio_conferencing_image9.png" alt= "An icon depicting the next step"/>|Next step|<ul><li>Choose the best approach for your upgrade journey.</li></ul>|

## Interoperability of Teams and Skype for Business

Interoperability is the ability for Teams and Skype for Business users in the same organization to communicate across Teams and Skype for Business.

Interoperability is governed by the coexistence mode (also known as upgrade mode) of the receiver. There is no interoperability when the receiver is in **Islands** mode.

### Native interop and interop escalation

There are two types of interop experiences: native and interop escalation.

- A _native interop_ experience occurs in the client that the user is currently using. One user will be in the Skype for Business client, the other in Teams. A native interop experience won’t take them to another client to communicate, the users will be able to conduct their conversation in the client they’re currently using. The native interop experiences are one-to-one chat and calling.
- An _interop escalation_ experience means that as part of helping users perform an advanced action (such as sharing their desktop), the client facilitates the creation of a meeting which users can join to continue the experience in that meeting. The meeting is created on the platform of the initiator of the action. The user or users who aren’t on that platform receive a meeting join link. As they click this link, they are joined to the meeting in a compatible client (browser, web app, or full client, depending on configuration). Interop escalation from Skype for Business requires a recent client. Interop escalation from Teams is now available. Both are supported in interoperability experiences in-tenant, and for federated communication cross-tenants.

### Native interop experiences

Depending on the coexistence modes assigned to users (as previously described), the following native interop experiences are available:

Skype for Business users can chat one-on-one with Teams users, and vice versa. An interop chat needs to go through an interop gateway that’s part of Teams cloud services (and therefore only exists online). Interop chats are plain text: rich text and emoticons aren’t supported. Users in Teams and in Skype for Business are notified that the conversation is an interop conversation.

<!--![Screen shot of Interop chat experience from Teams](media/Interop_chat_experience_from_Teams.png "Interop chat experience from Teams")-->

Skype for Business users can make one-on-one voice and video calls to Teams users, and vice versa.

<!--![Screen shot of Interop calling experience from Teams](media/Interop_calling_experience_from_Teams.png "Interop calling experience from Teams")-->

> [!Important]
> Interop experiences with an on-premises deployment of Skype for Business require that the on-premises environment is in hybrid mode with Office 365 Skype for Business. For details, see [Migration and interoperability guidance](https://aka.ms/SkypeToTeams-Interop).

These interop experiences are available to and between users who have one of the following coexistence modes assigned: **Skype for Business with Teams Collaboration**, **Skype for Business with Teams Collaboration and meetings**, **Skype for Business Only**, or **Teams Only**. There is no interoperability to users in **Islands** mode.

### Native interop experience limitations

Because of the difference in protocols and technology, it is not possible to support all capabilities natively. Specifically, the following capabilities are not available:

- Markdown, rich text, and the full emoticon set aren’t supported either from Teams or Skype for Business. Other native features of the compose box in Teams chats aren’t supported.
- Screen sharing (desktop or app sharing) between Teams and Skype for Business isn’t supported natively. However, it is supported through interop escalation.
- Group chats (multiple-party conversations) in Teams can only include participants who are using Teams.
- Multiple-party IM conversations (group chats) in Skype for Business can only include participants who are using Skype for Business. However, interop escalation to multiple-party is available from Skype for Business.
- Escalating an ongoing peer-to-peer voice or video call to a multiple-party call involving both Teams and Skype for Business users isn’t supported.
- File transfer for two-party chats, or file attachment in group chats, from Teams to Skype for Business—and vice versa—aren’t supported.
- There is no interoperability with Skype for Business Persistent Chat.

For all these limitations (except for Persistent Chat), one possible workaround is for one user to start a meeting and invite the other user to join it.

This workaround is the basis for interop escalation. In particular, screen sharing and escalation to multiparty are not achievable natively but they are supported via interop escalation.

### Interop escalation experiences

Interop escalation consists in supplementing the native interop capabilities with managed escalations to meetings. Meetings offer rich experiences available to anyone, regardless of which client they have.

When interop escalation is triggered by the Teams user, a Teams meeting is created. When it is triggered by the Skype for Business user, a Skype for Business meeting is created. In both cases, the meeting created is a **Meet now** meeting, which is not reflected on the user’s calendar.
 
The other party receives the meeting join link through interop chat and joins by clicking that link. If the Skype for Business user has a Teams account and is invited by the Teams user, they will join the meeting authenticated. Otherwise, they will join as an anonymous participant. Conversely, Teams users almost always have a Skype for Business account and a Skype for Business client they can use to join a Skype for Business meeting as an authenticated participant, but they might also join as an anonymous participant, for example using the Skype Meeting App.

Once the parties have joined the meeting, they can conduct any activity supported in meetings, such as desktop or content sharing, file sharing or transfer, adding other participants, and so on.

#### Interop escalation from Skype for Business

Interop and interop escalation from Skype for Business was updated in the July 2019 build of monthly C2R. Previously, Skype for Business did not have advance awareness that the remote party was using Teams. It only surmised that from the signaling received after a session was established.

When the signaling indicated that the response came from (or through) the interop gateway, it would display the yellow business bar (banner) indicating the other party was not using Skype for Business. With the evolution of our service, this resulted in false positives where Skype for Business users would see the business bar when they were connected to the Cloud Voicemail Service or other cloud voice services, rather than to an actual **Teams Only** user.
 
To prevent these false positives, the presence service is now informing the Skype for Business client when the other party is a **Teams Only** actual user. This allows Skype for Business to be aware that it needs to create an interop conversation ahead of it having been created, and the conversation window to be specific to interop.

![Screen shot of Teams message to create interop conversation with a Skype for Business user](media/teams-and-skypeforbusiness-coexistence-and-interop-create-conversation-with-skype-user.png)

If the Skype for Business user wants to share their desktop for example, they are informed that we will start a meeting and guided through the steps.

![Screen shot of Teams message to start meeting with a Teams user](media/teams-and-skypeforbusiness-coexistence-and-interop-start-meeting-with-teams-user.png)

Meanwhile, the Teams user receives an incoming chat message with the link to the meeting and are guided to join.

This escalation to a Skype for Business meeting is available for both in-tenant interop and cross-tenant federated calls and chats. It is on by default and there is no setting the admin has to provision.

#### Interop escalation from Teams

Interop escalation from Teams to a Teams meeting is now available when the Teams user selects the desktop sharing button in an in-tenant interop thread with a Skype for Business user or in a cross-tenant interop federation thread. Interop escalation is supported from a 1:1 chat conversation or from a 1:1 call.

The capability is supported in the Teams desktop client for Windows, in the Teams desktop client for Mac, and in the Teams web client on browsers where content sharing is supported, while in communication with any Skype for Business client version.

In interoperability threads, and in federation interoperability threads, the Teams user now has the controls (button) to start content sharing. When the Teams user selects the button, they are presented with an additional menu that informs them that to share content, they will need to start a Teams meeting.

If the users were in a call, the menu also warns them that their current call between Teams and Skype for Business will be terminated as they are put into a Teams meeting. If they so choose, they can warn the Skype for Business user prior to accepting.

![Screen shot of Teams message to share meeting with a Skype for Business user](media/teams-and-skypeforbusiness-coexistence-and-interop-share-meeting-with-skype-user.png)

Upon acceptance, they are put in the Teams meeting; they must start sharing from the sharing tray in the meeting.
 
Meanwhile, the Skype for Business user receives an incoming chat message with the link to the meeting and are guided to join.

This escalation to a Teams meeting is available for both in-tenant interop and cross-tenant federated calls and chats. It is on by default and there is no setting the admin has to provision. However, it is turned off for the user if the admin sets ``-AllowPrivateMeetNow`` in ``CsTeamsMeetingPolicy`` to ``$false``.

After you review this article, see [Choose your upgrade journey](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md), [Migration and interoperability guidance](https://aka.ms/SkypeToTeams-Interop), [Coexistence with Skype for Business](coexistence-chat-calls-presence.md), and [Setting your coexistence and upgrade settings](https://aka.ms/SkypeToTeams-SetCoexistence) for implementation details.

## Related Links

[Video: Manage Coexistence and Interoperability between SfB and Teams](https://www.youtube.com/watch?v=wEc9u4S3GIA&list=PLaSOUojkSiGnKuE30ckcjnDVkMNqDv0Vl&index=11)
