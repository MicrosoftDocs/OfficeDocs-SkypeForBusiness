---
title: Set up Microsoft Teams in your small business
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
ms.reviewer: dstrome
description: Set up Teams in your small business to enable your users to collaborate using chat and file sharing, set up and attend small and large meetings, and talk via video and voice.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Set up Microsoft Teams in your small business

There are lots of ways you can customize Teams. The following sections show you how to set up each Teams workload: **chats, teams and channels**; **meetings and conferencing**; and **voice solutions**. The order in which you set up each workload is up to you. While we recommend setting up the chats, teams, and channels workload first, you can start with meetings and conferencing or even cloud voice. The choice is yours.

> [!NOTE]
> If you haven't done so already, we strongly suggest that you begin your Teams deployment with a pilot. A pilot will allow you and a few early adopters to get familiar with Teams and its features before your planning and eventual roll out. For more information about how to start your pilot, check out [Get started with Microsoft Teams](get-started-with-teams-quick-start.md).

Before you roll out Teams broadly, make sure your organization is ready by reviewing the items in [Make sure you're ready](get-started-with-teams-quick-start.md#make-sure-youre-ready).

Jump to the section you're interested in:

- [Workloads](#workloads)
  - [Chat, teams, and channels](#chat-teams-and-channels)
  - [Meetings and conferencing](#meetings-and-conferencing)
  - [Teams Phone with Calling Plan](#teams-phone-with-calling-plan)
- [Deploy clients](#deploy-clients)
- [Training](#training)

## Workloads
### Chat, teams, and channels

Chat, teams, and channels, are the cornerstone of Teams. **Chat** lets one or more users talk to each other, share files, and meet privately. **Teams**, which can be visible to everyone in your organization or only to those in the team, let the right people collaborate whatever the task or occasion, whether it's a long-running project or planning for a birthday party. **Channels** within teams can segment topics, projects, departments, or anything else make sense for your team. For details about chat, teams, and channels, check out [Overview of teams and channels](teams-channels-overview.md).

> [!TIP]
> See how you can manage team roles, access, and messaging policies by completing the [Manage Microsoft Teams](/learn/modules/m365-teams-collab-manage-teams/) module on Microsoft Learn.

As you think about rolling out teams and channels, you need to decide who should be able to create them, whether guests from outside your organization can access them, and so on. The article [Chat, teams, channels, & apps in Microsoft Teams](deploy-chat-teams-channels-microsoft-teams-landing-page.md) has lots of information about planning for chat, teams, and channels, however, here are some key things from that article you should think about. Select on a decision if you want more information about it.

| Decision | Description |
|--|--|
| [Who should be Teams administrators?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#teams-administrators) | Admin roles can be used to grant specific permissions to people who you want to administer Teams. Small businesses may not need these extra roles because the same person may be responsible for all aspects of Teams. You can always add or remove administrators later on.<br><br>[Use Microsoft Teams administrator roles to manage Teams](using-admin-roles.md) |
| [Who should be Team owners and members?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#teams-owners-and-members) | Team owners control who can access a team and its channels. They can decide whether a team or channel is public (to the organization) or private and can set up policies like whether a channel should be moderated. Members can access the team and its channels (unless a channel is set to private and they're not a member of that channel) and can be designated as moderators.<br><br>[Assign team owners and members in Microsoft Teams](assign-roles-permissions.md) |
| [Should guest access be enabled?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#guest-access) |Guest access lets people in your organization invite people outside your organization access your teams and channels. Guest access is often used to collaborate with people outside your organization who don't have a formal relationship with yours. For example, you might invite a project planner to work on a project temporarily.<br>Guest access is different than external access. Guest access invites specific individuals access to interact with people in your organization.  <br>Guest access is turned **Off** by default. <br><br>[Turn on or turn off guest access to Microsoft Teams](set-up-guests.md)  |

You don't need to do anything else for your users to start using chat, teams, and channels. However, there are lots of options for controlling how Teams is used. You can changes now, or wait until you can see how people are using Teams. For more information, check out the following articles:

- [Manage messaging policies in Teams](messaging-policies-in-teams.md)
- [Teams settings](enable-features-office-365.md#teams-settings)

### Meetings and conferencing

Meetings and conferencing lets people in your organization meet with each other and those outside your organization. Anyone with a Teams or Skype for Business client can join **meetings** to which they've been invited. Using the microphone, camera, and screen of their device lets participants join in the conversation without the need for a phone. Participants can chat, make voice calls, and share video and apps with other participants using a PC or mobile device.

**Audio conferencing** lets participants join to meetings via a regular phone by calling a conference phone number and entering a meeting ID. Audio conferencing is useful when a participant doesn't have a good Internet connection, the meeting is voice-only, or some other circumstance doesn't allow them to join via the Teams client.

> [!TIP]
> Get more familiar with meetings and events by completing the [Manage meetings, conferences, and events with Microsoft Teams](/learn/modules/m365-teams-collab-manage-meetings) module on Microsoft Learn.

Meetings are enabled by default in Teams, however, you can control the meeting experience for organizers and participants. You can also set policies for what people are, and aren't, allowed to do before and during meetings. For more information, check out the following articles:

- [Admin quick start - Meetings and live events in Microsoft Teams](quick-start-meetings-live-events.md)
- [Set up Audio Conferencing for small and medium businesses](audio-conferencing-smb.md)

### Teams Phone with Calling Plan

Microsoft 365 Teams Phone with Calling Plan is a great solution for businesses with fewer than 300 users that gives you all the features of an office phone system. Teams Phone includes voicemail, caller ID, phone system menus, toll-free numbers, and more, without the need to manage a complex and costly on-premises phone system.

For more information on Teams Phone with Calling Plan for small and medium businesses, see [Teams Phone guidance for small and medium businesses](/microsoftteams/business-voice/whats-business-voice).

## Deploy clients

When you're ready for your users to start using Teams, they can install the Teams client on their Windows, Mac, or Linux PC, or on their Android or iOS device. Users can download the Teams client directly from <https://teams.microsoft.com/downloads>.

Make sure everyone who'll be using Teams has a Teams license. For more information about assigning a Teams license, see [Manage user access to Teams](user-access.md#using-the-microsoft-365-admin-center).

> [!TIP]
> Get recommendations on how to plan your Teams client deployment by completing the [Deploy Microsoft Teams clients](/learn/modules/m365-teams-collab-deploy-clients/) module on Microsoft Learn.

If your organization uses Microsoft Endpoint Configuration Manager, Group Policy, or a third-party distribution mechanism, to deploy software to your user's computers, see [Install Microsoft Teams using Microsoft Endpoint Configuration Manager](msi-deployment.md).

If you want detailed information about deploying Teams clients, see [Get clients for Microsoft Teams](get-clients.md).

## Training

For information on how to train your users to use Teams, see [Microsoft Teams training](training-microsoft-teams-landing-page.md).