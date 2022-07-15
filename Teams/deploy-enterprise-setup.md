---
title: Set up Microsoft Teams in your enterprise
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
description: Set up Teams in your enterprise to enable your users to collaborate using chat and file sharing, set up and attend small and large meetings, and talk via video and voice.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
appliesto: 
  - Microsoft Teams
---

# Set up Microsoft Teams in your enterprise

Use the information in this article to guide you through the deployment of Teams in your organization.

> [!NOTE]
> If you haven't done so already, we strongly suggest that you begin your Teams deployment with a pilot. A pilot will allow you and a few early adopters to get familiar with Teams and its features before your planning and eventual roll out. For more information about how to start your pilot, check out [Get started with Microsoft Teams](get-started-with-teams-quick-start.md).

Before you roll out Teams broadly, make sure your organization is ready by reviewing the items in [Make sure you're ready](get-started-with-teams-quick-start.md#make-sure-youre-ready).

## Plan your deployment

Before you start deploying Teams, make sure you've completed your planning process. Your planning process should include:

- Understanding Teams architecture
- Reviewing and understanding Teams workloads and how they work with Microsoft 365
- Calculated network requirements and ensuring your network and Internet connection have the hardware and capacity required to support critical requirements like real-time communications
- Understanding regulatory and compliance requirements for information stored in Teams and other Microsoft 365 services
- Creating an adoption plan to help users understand the benefits of using Teams

We strongly recommend using the [Teams advisor](https://admin.teams.microsoft.com/teams-deployment) to help you with your deployment. For details about how the Teams advisor works, see [Use Advisor for Teams to help you roll out Microsoft Teams](use-advisor-teams-roll-out.md).

> [!TIP]
> See how you can use Teams advisor to help you plan your Teams deployment by completing the [Roll out using the Teams advisor](/learn/modules/m365-teams-rollout-using-advisor/) module on Microsoft Learn.

For information about planning for Teams, see [Teams enterprise deployment overview](deploy-enterprise-overview.md).

## Workloads

There are lots of ways you can customize Teams. The following sections show you how to set up each Teams workload: **chats, teams and channels**; **meetings and conferencing**; and **Phone System**. The order in which you set up each workload is up to you. While we recommend setting up the chats, teams, and channels workload first, you can start with meetings and conferencing or even Phone System.

#### [Chat, teams, and channels](#tab/ChatTeamsChannels)

Chat, teams, and channels, are the cornerstone of Teams. **Chat** lets one or more users talk to each other, share files, and meet privately. **Teams**, which can be visible to everyone in your organization or only to those in the team, let the right people collaborate whatever the task or occasion, whether it's a long-running project or planning for a birthday party. **Channels** within teams can segment topics, projects, departments, or anything else make sense for your team. For details about chat, teams, and channels, check out [Overview of teams and channels](teams-channels-overview.md).

> [!TIP]
> See how you can manage team roles, access, and messaging policies by completing the [Manage Microsoft Teams](/learn/modules/m365-teams-collab-manage-teams/) module on Microsoft Learn.

### Administration and team ownership

| Decision | Description |
|--|--|
| Who should be Teams administrators? | Admin roles can be used to grant specific permissions to people who you want to administer Teams. Small businesses may not need these extra roles because the same person may be responsible for all aspects of Teams. You can always add or remove administrators later on.<p>[Use Microsoft Teams administrator roles to manage Teams](using-admin-roles.md) |
| Who should be Team owners and members? | Team owners control who can access a team and its channels. They can decide whether a team or channel is public (to the organization) or private and can set up policies like whether a channel should be moderated. Members can access the team and its channels (unless a channel is set to private and they're not a member of that channel) and can be designated as moderators.<p>[Assign team owners and members in Microsoft Teams](assign-roles-permissions.md) |

### Default settings and lifecycle policies

| Decision | Description |
|--|--|
| What messaging policies should be applied? | Messaging policies control which chat and channel messaging features (such as who can use chat, who can edit and delete sent messages, and so on) are available to users in Teams. Teams has a global policy that applies to everyone. All of the features in the global policy are **On** by default.<p>If you want the same policy to apply to everyone, all you need to do is make changes to this global policy (for example, turn off meme support in conversations).<p>If you want different policies for different groups of people (for example, one policy for office workers and another for factory workers), you can create and assign policies. When you assign a policy to a user, the global policy no longer applies to them.<p>[Manage messaging policies in Teams](messaging-policies-in-teams.md) |
| What Team settings should be applied? | Teams settings let you set up your teams for features such as email integration, cloud storage options, organization tab, meeting room device setup, and search scope. When you make changes to these settings, they apply to all the teams in your organization. <p>[Teams settings](enable-features-office-365.md#teams-settings)  |

### External and guest access

| Decision | Description |
|--|--|
| Should external access be enabled? | External access lets anyone in another organization talk to people in your organization. This is useful when you have a close relationship with another organization, such as a supplier, and want to make it easy for people in either organization to chat with each other, hold meetings, and so on. <p>External access is different than guest access. External access gives everyone in an organization access to interact with people in your organization. Guest access invites specific individuals access to interact with people in your organization.<p>External access is turned **On** by default.<p>[Manage external access in Microsoft Teams](manage-external-access.md)  |
| Should guest access be enabled? |Guest access lets people in your organization invite people outside your organization access your teams and channels. Guest access is often used to collaborate with people outside your organization who don't have a formal relationship with yours. For example, you might invite a project planner to work on a project temporarily.<p>Guest access is different than external access. Guest access invites specific individuals access to interact with people in your organization. External access gives everyone in another organization access to interact with people in your organization. <p>Guest access is turned **On** by default. <p>[Collaborate with guests in a team](/microsoft-365/solutions/collaborate-as-team)  |

#### [Meetings and audio conferencing](#tab/MeetingsAudioConferencing)

Meetings and conferencing let people in your organization meet with each other and those outside your organization. Anyone with a Teams or Skype for Business client can join **meetings** to which they've been invited. Using the microphone, camera, and screen of their device lets participants join in the conversation without the need for a phone. Participants can chat, make voice calls, and share video and apps with other participants using a PC or mobile device.

**Audio conferencing** lets participants join to meetings via a regular phone by calling a conference phone number and entering a meeting ID. Audio conferencing is useful when a participant doesn't have a good Internet connection, the meeting is voice-only, or some other circumstance doesn't allow them to join via the Teams client.

> [!TIP]
> Get more familiar with meetings and events by completing the [Manage meetings, conferences, and events with Microsoft Teams](/learn/modules/m365-teams-collab-manage-meetings) module on Microsoft Learn.

### Meetings

| Decision | Description |
|--|--|
| What org-wide meeting settings should be applied| Meeting policies control which meeting features are available to organizers and participants of meetings. You can control whether anonymous participants can join meetings, customize meeting invites, control how real-time media is handled, and more. When you make changes to these settings, they apply to all meetings in your organization. <p>[Manage meeting settings in Microsoft Teams](meeting-settings-in-teams.md)|
| What meeting policies should be applied? | Meeting policies are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization. You can control whether users can schedule private meetings, enable the Meet Now option, allow meetings to be recorded, and so on. Teams has a global policy that applies to everyone.<p> If you want the same policy to apply to everyone, all you need to do is make changes to this global policy (for example, turn off the recording of meetings). <p>If you want different policies for different groups of people (for example, one policy for office workers and another for executives), you can create and assign policies. When you assign a policy to a user, the global policy no longer applies to them.<p> [Manage meeting policies in Teams](meeting-policies-overview.md)|
| Do you want to allow meeting recording and archiving?| Meeting organizers can record and archive meetings in the cloud. You can turn meeting recording and archiving on or off using meeting policies.<p> [Teams cloud meeting recording](cloud-recording.md) |

### Audio conferencing

| Decision | Description |
|--|--|
| Do you want to set up video interoperability with third-party solutions?| Cloud video interoperability lets third-party telepresence and personal video devices to join Teams meetings. If you've already invested in video conferencing and personal video devices, you can use video interoperability to integrate those devices with Teams.<p> [Cloud Video Interop for Microsoft Teams](cloud-video-interop.md)|
| What org-wide audio conferencing settings should be applied?| Audio conferencing settings let you control how meeting participants call into meetings using a phone. You can set length of the PINs required to join meetings, reset conference IDs, enable or disable sending audio conferencing information to participants, and so on. Changes to audio conferencing settings apply to everyone in your organization.<p>[Manage the Audio Conferencing settings for your organization in Microsoft Teams](manage-the-audio-conferencing-settings-for-my-organization-in-teams.md) |
| Do meeting organizers need to dial out to any destination?| Communication Credits are used when calling from an audio conferencing meeting to phone numbers outside your organization. You need to purchase enough Communication Credits to ensure you won't run out during audio conferencing calls.<p>Some audio conferencing subscriptions may include outbound calling. Check your subscription information for details.<p> [Set up Communications Credits for your organization](set-up-communications-credits-for-your-organization.md)|
| What outbound calling restrictions should be applied?| You can use outbound call controls to restrict the type of audio conferencing calls that can be made by users in your organization. For example, you can control whether meetings can call international phone numbers, make any outbound calls at all, call only to specific countries or regions, and so on.<p>[Outbound calling restriction policies for Audio Conferencing and user PSTN calls](outbound-calling-restriction-policies.md) |
| Do you want to change how dialed phone numbers are interpreted by Teams? | You can control how phone numbers are interpreted using dial plans. For example, you can set which number to dial to reach an outside phone line, control how phone extensions are handled, set a prefix so a dialed extension is translated into a full phone number, and so on.<p> [Create and manage dial plans](create-and-manage-dial-plans.md) |
| Do you want to enable live events? | Live events let you broadcast video and meeting content to large audiences. If you enable live events, you can set policies for them to control how they're used. For example, you can configure the URL participants should use for support, configure a third-party video distribution provider if you have one, and so on. Teams has a global policy that applies to everyone.<p>If you want the same policy to apply to everyone, all you need to do is make changes to this global policy. <p>If you want different policies for different groups of people (for example, one policy for office workers and another for executives), you can create and assign policies. When you assign a policy to a user, the global policy no longer applies to them.<p> [Set up for live events in Microsoft Teams](teams-live-events/set-up-for-teams-live-events.md) |

#### [Phone System and PSTN connectivity](#tab/PhoneSystem)

Phone System allows you to replace your existing on-premises phone system with a set of features delivered from Microsoft 365 that is tightly integrated into your cloud experience.

| Decision | Description |
|--|--|
| Do you want to replace your on-premises phone system? | Set up Phone System, configure auto attendants, calling plans, call queues, and so on. <p> [Set up Phone System in your organization](setting-up-your-phone-system.md)|
| Do you want to set Cloud Voicemail policies?| You can control which Cloud Voicemail features are available to your users, and how they work. For example, you can enable or disable voicemail transcription for your whole organization, enable or disable profanity masking for specific users, and so on.<p> [Set up Cloud Voicemail](set-up-phone-system-voicemail.md) |
| Do you want to enable dynamic emergency calling?| Dynamic emergency calling lets you configure a location map based on network settings and other metadata to determine where to send emergency personnel in the event an emergency call is placed by a user. You can configure network settings, assign emergency addresses to locations, and so on.<p>[Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md) |
| Do you want to customize caller ID behavior? | By default, the phone number shown when a Teams user makes a call is the user's phone number. You can change this to be the company's main number, block the phone number, make the number anonymous, or another service number. Teams has a global policy that applies to everyone.<p>If you want the same policy to apply to everyone, all you need to do is make changes to this global policy. <p>If you want different policies for different groups of people (for example, one policy for office workers and another for executives), you can create and assign policies. When you assign a policy to a user, the global policy no longer applies to them.<p> [Manage caller ID policies in Microsoft Teams](caller-id-policies.md) |

---

## Security

Teams is designed and developed in compliance with the [Microsoft Trustworthy Computing Security Development Lifecycle (SDL)](https://www.microsoft.com/sdl/default.aspx). To conform to the SDL, Teams incorporates industry standard security technologies as a fundamental part of its architecture, including:

- Designing threat models that features are then tested against
- Incorporating security-related improvements into the coding process and practices
- Creating build-time tools to detect buffer overruns and other potential security threats before code can be checked into the product

Although Teams follows a "Trustworthy by Design" methodology, it's impossible to design against all unknown security threats. For this reason, it's important to understand how Teams works and interacts with other systems. It's also important to understand how common threats, such as IP address spoofing, denial-of-service attacks, man-in-the-middle attacks, and so on, work so that you can design your network and Teams configuration to reduce the chances of these attacks happening.

To understand how Teams incorporates security fundamentals into its design, and to read more about common threats, see [Security and Microsoft Teams](teams-security-guide.md).

## Compliance

Teams and Microsoft 365 provide many tools that can help you conform to regulatory requirements where your company and users are located. See the following articles for information on how to configure each compliance feature in Teams:

| Feature | Description|
|-|-|
| [Information barriers](information-barriers-in-teams.md)| Prevents individuals or groups from communicating with, or finding in the user picker, each other.|
| [Retention policies](retention-policies.md)| Lets you control how long data in Teams should be kept or whether data must be removed after a certain time.|
| [Communication compliance](communication-compliance.md)| Helps reduce communication risks by identifying, and taking action on, offensive, profane, and harassing language; adult racy, and gory images; and the sharing of sensitive information. |
| [Policy-based recording for calls and meetings](teams-recording-policy.md)| Lets you control when, or whether, calls and meetings should be automatically recorded and stored for later processing, retention, or analysis.|
| [Sensitivity labels](sensitivity-labels.md)| Helps you to protect and regulate access to sensitive information by creating labels that enforce selected privacy options.|
| [Microsoft Purview Data Loss Prevention](/microsoft-365/compliance/dlp-microsoft-teams?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json)| Lets you create rules that determine how certain information, such as social security numbers, credit card numbers, and so on, should be handled. You can prevent the sending of certain information, prevent it from leaving your organization, and so on.|
| [eDiscovery](eDiscovery-investigation.md)| Helps you search for, and retrieve, content in your organization when your organization receives discovery demands in legal proceedings. |
| [Legal hold](legal-hold.md)| Helps you retain information in your organization, even if it's deleted by a user, when required during legal proceedings so that it can be discovered during eDiscovery investigations. |
| [Content search](content-search.md)| Provides a way to query Teams information spanning Exchange, SharePoint Online, and OneDrive for Business.|
| [Auditing](audit-log-events.md)| Lets you see information about a specified action, including who performed the action, when the action was performed, the IP address that was used, and so on. Actions include the creation or deletion of teams, creation of channels, changed settings in Teams, and so on.|
| [Customer key](/microsoft-365/compliance/customer-key-tenant-level?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json)| Lets you create a data encryption policy using encryption keys you provide.|

## Clients

When you're ready for your users to start using Teams, they can install the Teams client on their Windows, Mac, or Linux PC, or on their Android or iOS device. Users can download the Teams client directly from <https://teams.microsoft.com/downloads>.

Make sure everyone who will be using Teams has a Teams license. For more information about assigning a Teams license, see [Manage user access to Teams](user-access.md#using-the-microsoft-365-admin-center).

> [!TIP]
> Get recommendations on how to plan your Teams client deployment by completing the [Deploy Microsoft Teams clients](/learn/modules/m365-teams-collab-deploy-clients/) module on Microsoft Learn.

If your organization uses Microsoft Endpoint Configuration Manager, Group Policy, or a third-party distribution mechanism, to deploy software to your user's computers, see [Install Microsoft Teams using Microsoft Endpoint Configuration Manager](msi-deployment.md).

If you want detailed information about deploying Teams clients, see [Get clients for Microsoft Teams](get-clients.md).

## Training

For information on how to train your users and admins to use Teams, see [Microsoft Teams training](training-microsoft-teams-landing-page.md).
