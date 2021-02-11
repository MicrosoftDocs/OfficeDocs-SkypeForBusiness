---
title: Choose a path to your organization-wide rollout
author: dstrome
ms.author: dstrome
manager: serdars
ms.date: 11/06/2018
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: dstrome
description: Once you've set up your first teams, learn where to go to find in-depth deployment and adoptions resources for Microsoft Teams.
ms.custom: 
- seo-marvel-apr2020
- seo-marvel-mar2020
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
appliesto: 
  - Microsoft Teams
---

# Choose a path to your organization-wide rollout of Microsoft Teams

Now that you've successfully set up your first teams and onboarded a few early adopters, it's time to begin your rollout of Teams to the rest of your organization.

> [!TIP]
> Before you begin your Teams rollout, we strongly recommend that you complete the [Prepare for a Teams deployment with Microsoft 365](/learn/modules/m365-teams-collab-prepare-deployment/) Microsoft Learn module. This 30 minute module will jump-start your understanding of Teams and talk through key decisions you need to make as you roll out Teams.
>
> If you want to check out more learning paths and modules available for Teams, see [Microsoft Learn for Teams](/learn/teams/).

Select **Small business** if you only have a few employees or don't have multiple locations or a complex network.

Select **Medium/large business** if you want to create a formal adoption process for key stakeholders; have multiple locations or a large network with proxy servers or multiple firewalls; have complex compliance requirements; or have other non-standard requirements that require extra planning.

#### [Small business](#tab/SmallBusiness)

There are lots of ways you can customize Teams. The following sections show you how to set up each Teams workload: **chats, teams and channels**; **meetings and conferencing**; and **cloud voice**. The order in which you set up each workload is up to you. While we recommend setting up the chats, teams, and channels workload first, you can start with meetings and conferencing or even cloud voice. The choice is yours.

Before you roll out Teams broadly, make sure your organization is ready by reviewing the items in [Make sure you're ready](get-started-with-teams-quick-start.md#make-sure-youre-ready).

Jump to the section you're interested in:

- [Workloads](#workloads)
  - [Chat, teams, and channels](#chat-teams-and-channels)
  - [Meetings and conferencing](#meetings-and-conferencing)
  - [Business Voice](#business-voice)
- [Deploy clients](#deploy-clients)
- [Training](#training)

### Workloads
#### Chat, teams, and channels

Chat, teams, and channels, are the cornerstone of Teams. **Chat** lets one or more users talk to each other, share files, and meet privately. **Teams**, which can be visible to everyone in your organization or only to those in the team, let the right people collaborate whatever the task or occasion, whether it's a long-running project or planning for a birthday party. **Channels** within teams can segment topics, projects, departments, or anything else make sense for your team. For details about chat, teams, and channels, check out [Overview of teams and channels](teams-channels-overview.md).

> [!TIP]
> See how you can manage team roles, access, and messaging policies by completing the [Manage Microsoft Teams](https://docs.microsoft.com/learn/modules/m365-teams-collab-manage-teams/) module on Microsoft Learn.

As you think about rolling out teams and channels, you need to decide who should be able to create them, what policies should be applied to them, whether guests from outside your organization can access them, and so on. The article [Chat, teams, channels, & apps in Microsoft Teams](deploy-chat-teams-channels-microsoft-teams-landing-page.md) has lots of information about planning for chat, teams, and channels, however, here are some key things from that article you should think about. Click on a decision if you want more information about it.

| Decision | Description |
|--|--|
| [Who should be Teams administrators?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#teams-administrators) | Admin roles can be used to grant specific permissions to people who you want to administer Teams. Small businesses may not need these extra roles because the same person may be responsible for all aspects of Teams. You can always add or remove administrators later on.<br><br>[Use Microsoft Teams administrator roles to manage Teams](using-admin-roles.md) |
| [Who should be Team owners and members?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#teams-owners-and-members) | Team owners control who can access a team and its channels. They can decide whether a team or channel is public (to the organization) or private and can set up policies like whether a channel should be moderated. Members can access the team and its channels (unless a channel is set to private and they're not a member of that channel) and can be designated as moderators.<br><br>[Assign team owners and members in Microsoft Teams](assign-roles-permissions.md) |
| [What messaging policies should be applied?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#messaging-policies)  | Messaging policies control which chat and channel messaging features (such as who can use chat, who can edit and delete sent messages, and so on) are available to users in Teams. Teams has a global policy that applies to everyone. All of the features in the global policy are **On** by default.<br>If you want the same policy to apply to everyone, all you need to do is make changes to this global policy (for example, turn off meme support in conversations).<br>If you want different policies for different groups of people (for example, one policy for office workers and another for factory workers), you can create and assign policies. When you assign a policy to a user, the global policy no longer applies to them.<br><br>[Manage messaging policies in Teams](messaging-policies-in-teams.md) |
| [What Team settings should be applied?](enable-features-office-365#teams-settings) | Teams settings let you set up your teams for features such as email integration, cloud storage options, organization tab, meeting room device setup, and search scope. When you make changes to these settings, they apply to all the teams in your organization. <br><br>[Teams settings](enable-features-office-365#teams-settings)  |
| [Should external access be enabled?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#external-access) | External access lets anyone in another organization talk to people in your organization. This is useful when you have a close relationship with another organization, such as a supplier, and want to make it easy for people in either organization to chat with each other, hold meetings, and so on. <br>External access is different than guest access. External access gives everyone in an another organization access to interact with people in your organization. Guest access invites specific individuals access to interact with people in your organization.<br>External access is turned **Off** by default.<br><br>[Manage external access in Microsoft Teams](manage-external-access.md)  |
| [Should guest access be enabled?](deploy-chat-teams-channels-microsoft-teams-landing-page.md#guest-access) |Guest access lets people in your organization invite people outside your organization access your teams and channels. Guest access is often used to collaborate with people outside your organization who don't have a formal relationship with yours. For example, you might invite a project planner to work on a project temporarily.<br>Guest access is different than external access. Guest access invites specific individuals access to interact with people in your organization. External access gives everyone in an another organization access to interact with people in your organization. <br>Guest access is turned **Off** by default. <br><br>[Turn on or turn off guest access to Microsoft Teams](set-up-guests.md)  |

#### Meetings and conferencing

Meetings and conferencing lets people in your organization meet with each other and those outside your organization. Anyone with a Teams or Skype for Business client can join **meetings** (meetings up 300 attendees, and live events up to 10,000 attendees) to which they've been invited. Using the microphone, camera, and screen of their device lets participants join in the conversation without the need for a phone. Participants can chat, talk to each other via voice, and share video and apps with other participants using a PC or mobile device.

**Audio conferencing** lets participants join to meetings via a regular phone by calling a conference phone number and entering a meeting ID. Audio conferencing is useful when a participant doesn't have a good Internet connection, the meeting is voice-only, or some other circumstance doesn't allow them to join via the Teams client.

> [!TIP]
> Get more familiar with meetings and events by completing the [Manage meetings, conferences, and events with Microsoft Teams](https://docs.microsoft.com/learn/modules/m365-teams-collab-manage-meetings) module on Microsoft Learn.

Meetings are enabled by default in Teams, however, you can control the meeting experience for organizers and participants. You can also set policies for what people are, and aren't, allowed to do before and during meetings. For example, you can:

- Allow or prevent anonymous users from joining meetings organized by people in your organization.
- Allow or prevent the use of PowerPoint sharing, whiteboards, shared notes, and chat.
- Customize meeting invitations with your company logo, support website, and more.
- Allow or prevent the use of cameras during meetings.
- Enable or disable the recording of meetings.
- Enable or disable screen sharing.

The [Admin quick start - Meetings and live events in Microsoft Teams](quick-start-meetings-live-events.md) article guides you to the right information to customize Teams meetings for your organization.

The [Set up Audio Conferencing for small and medium businesses](audio-conferencing-smb.md) article shows you how to set up audio conferencing for your meetings.

#### Business Voice

[Microsoft 365 Business Voice](business-voice/whats-business-voice.md) is a great solution for businesses with fewer than 300 users that gives you all the features of an office phone system. Business Voice includes voicemail, caller ID, phone system menus, toll-free numbers, and more, without the need to manage a complex and costly on-premises phone system.

Based on Microsoft 365 Phone System, Business Voice simplifies adding voice to your organization by bundling Phone System features and add-ons, and providing an easy-to-follow wizard to help you set up your phone system. If your organization is located in a [country or region that supports Business Voice](business-voice/country-region-availability.md), you can transfer your phone numbers to Microsoft 365 and let us manage your phone system for you.

With Microsoft 365 as your phone system, you can turn any device into a phone by installing the Teams client on it. Or, if you'd rather have a traditional desk phone or conference phone, there are many Teams-certified devices to choose from. Either way, calls are always routed to where you are, and calls you make always have your office phone number.

If you're interested in trying out Business Voice, check out [What do I need to buy to use Microsoft 365 Business Voice?](business-voice/what-to-buy.md).

### Deploy clients

When you're ready for your users to start using Teams, they can install the Teams client on their Windows, Mac, or Linux PC, or on their Android or iOS device. Users can download the Teams client directly from <https://teams.microsoft.com/downloads>.

Make sure everyone who will be using Teams has a Teams license. For more information about assigning a Teams license, see [Manage user access to Teams](user-access.md#using-the-microsoft-365-admin-center).

> [!TIP]
> Get recommendations on how to plan your Teams client deployment by completing the [Deploy Microsoft Teams clients](https://docs.microsoft.com/learn/modules/m365-teams-collab-deploy-clients/) module on Microsoft Learn.

If your organization uses Microsoft Endpoint Configuration Manager, Group Policy, or a third-party distribution mechanism, to deploy software to your user's computers, see [Install Microsoft Teams using Microsoft Endpoint Configuration Manager](msi-deployment.md).

If you want detailed information about deploying Teams clients, see [Get clients for Microsoft Teams](get-clients.md).

### Training

For information on how to train your users to use Teams, see [Microsoft Teams training](training-microsoft-teams-landing-page.md).

#### [Medium/large business](#tab/LargeBusiness)

Many businesses can deploy Teams just using the [quick start guide](get-started-with-teams-quick-start.md), which shows you how to set up a Teams pilot and enable the most common features. However, some organizations have complex requirements, such as the ones below, that need additional planning:

- Multiple office locations
- Compliance and privacy requirements
- Thousands of users distributed across multiple locations
- Numerous device and rooms types
- Non-standard telephony implementations

If this sounds like your organization, you need to complete Teams advanced setup. Advanced setup helps you plan your deployment and provides recommendations for how to establish an adoption program to maximize the use of Teams.

> [!div class="nextstepaction"]
> [Go to advanced setup](deploy-advanced.md)

---
