---
title: Microsoft Teams upgrade from Skype for Business | Modes, Coexistence 
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: dearbeen, bjwhalen
description: Details of Skype for Business and Microsoft Teams coexistence options and modes, and upgrade journeys to Teams from Skype for Business with example scenarios. 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
f1keywords:
- ms.teamsadmincenter.orgwidesettings.teamsfeatures.upgradetoteamsarticle
- ms.teamsadmincenter.upgradeoverride.learnmore
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

![Upgrade journey diagram, emphasizing the Project Definition stage](media/upgrade-banner-project-definition.png "Stages of the upgrade journey, with emphasis on the Project Definition stage")

This article is part of the Project Definition stage of your upgrade journey. Before proceeding, confirm that you’ve completed the following activities:

- [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
- [Defined your project scope](https://aka.ms/SkypetoTeams-Scope)
- [Understood coexistence and interoperability of Skype for Business and Teams](https://aka.ms/SkypeToTeams-Coexist)

# Choose your upgrade journey from Skype for Business to Teams

As an existing Skype for Business customer, your complete transition to Teams might take some time. However, you can begin realizing the value of Teams today, by enabling your users to use Teams alongside Skype for Business. Given that there’s some overlapping functionality between the two apps, we recommend that you review the available coexistence and upgrade modes to help determine which path is right for your organization. For example, you might opt to enable all workloads on both solutions without interoperability. Or, you might decide to manage the user experience, either by gradually introducing Teams capabilities or by targeting groups of users for select capabilities, until your organization is ready to upgrade everyone to Teams. Use the outcome of your pilot to help assess the right upgrade journey for your organization.

> [!IMPORTANT]
> Skype for Business Online will be retired on July 31, 2021, after which it will no longer be accessible or supported. To maximize benefit realization and ensure your organization has proper time to implement your upgrade, we encourage you to begin your journey to Microsoft Teams today.

This article outlines the various modes that enable you to manage which modalities in Skype for Business and Teams are available to your users. As with any deployment, we strongly encourage you to [pilot your intended plan](pilot-essentials.md) with a selected group of users before upgrading your organization to Teams. Remember, introducing new technology can be disruptive for users. Take time to assess user readiness and implement a communication and training plan prior to implementing any of the modes outlined herein.

> [!TIP]
> Join us for live, interactive workshops in which we’ll share guidance, best practices, and resources designed to kick start upgrade planning and implementation.
>
>Join the [Plan your upgrade](https://aka.ms/SkypeToTeamsPlanning) session first to get started.


## Upgrade journey building blocks

To formally prepare your organization for its journey to Teams, you need to start planning for the upgrade scenarios that will eventually let your organization fully embrace Teams as your sole communications and collaboration solution.

To help guide your decision-making process, familiarize yourself with the various modes, concepts, and terminology relevant to upgrading from Skype for Business to Teams. For more information, see [Microsoft Teams and Skype for Business coexistence and interoperability](https://aka.ms/SkypeToTeams-Coexist)

A user that has been migrated to Teams no longer uses a Skype for Business client except to join a meeting hosted in Skype for Business. All incoming chats and calls land in the user’s Teams client, regardless of whether the sender uses Teams or Skype for Business. Any new meetings organized by the upgraded user will be scheduled as Teams meetings. If the user attempts to use the Skype for Business client, initiation of chats and calls is blocked<sup>1</sup>. However, the user can (and must) still use the Skype for Business client to join meetings they are invited to.

Administrators manage their transition to Teams using the concept of [mode](migration-interop-guidance-for-teams-with-skype.md#coexistence-modes), which is a property of [TeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps). A user that has been migrated to Teams as described above is in “TeamsOnly” mode. For an organization that is migrating to Teams, the ultimate goal is to move all users to TeamsOnly mode.

There are two methods for migrating an existing organization with Skype for Business (whether online or on-premises) to Teams:

- **Overlapping capabilities method** (using Islands mode): Users in an existing Skype for Business organization are introduced to Teams so that they can use both clients side by side during a transitional phase. During this period, most--but not all--functionality of Teams is available to them. The mode for this configuration is referred to as Islands, and this is the default mode for any existing organization with Skype for Business. Once the organization is ready, the administrator moves the users to TeamsOnly mode.
- **Select capabilities method** (using one or more of the Skype for Business modes): The administrator manages the transition (from Skype for Business to Teams) of chat, calling, and meeting scheduling functionality for users in their organization. Each of these functions is available either in Skype for Business or Teams, but not both. Administrators use TeamsUpgradePolicy to control when to shift this functionality to Teams for their users. Users who are not yet in TeamsOnly mode continue to use Skype for Business for chat and calling, and the two sets of users can communicate via interop functionality. Administrators manage the transition by progressively migrating more users into TeamsOnly mode.

<sup>1</sup>Older Skype for Business clients that shipped before 2017 do not honor TeamsUpgradePolicy. Make sure you are using the latest Skype for Business client available in your Office channel.

Below are the key factors to help decide the appropriate path for your organization. 

## Overlapping capabilities method (using Islands mode)

With the overlapping capabilities method, users can use both Teams and Skype for Business clients for chat, VoIP calling, and meetings. In this method, chat and VOIP calling in Teams is intra-organization focused, while Skype for Business enables chat and VOIP/PSTN calling with external organizations (if configured). Meetings can be scheduled and attended in both products.

When using the overlapping capabilities method, the communication traffic for Skype for Business and Teams remains separate (even for the same user) and the two different clients never communicate with each other (for users within the same organization). User experiences are based on the recipient’s configuration. For example, assume recipient User A is using this upgrade method:

- Communication initiated from another user’s Skype for Business client will always land in User A’s Skype for Business client.
- Communication initiated from the Teams client from a *user in the same organization* will always land in User A’s Teams client.
- Communication initiated from Teams client from a *user in an external organization* will always land in User A’s Skype for Business client.

If you have assigned an Office 365 license to your users, this will be the default upgrade experience for your organization. When you assign an Office 365 license, both Teams and Skype for Business Online licenses are assigned by default.<sup>2</sup>

For this method to work effectively, all users must run both clients simultaneously. Incoming chats and calls from within the organization to a user in Islands mode can land in either the Skype for Business or Teams client--and this is not under the control of the recipient. It depends on what client the sender uses to initiate the communication. If the sender and recipient are in different organizations, incoming calls and chats to a user in Islands mode always land in the Skype for Business client.

For example, if an Islands mode recipient is signed in to Skype for Business but not Teams, and someone messages them from Teams, the Islands mode recipient will not see the message (but they will eventually get an email saying they missed a message in Teams). Likewise, if a user is running Teams but not Skype for Business, and someone messages that user from Skype for Business, the user will not see that chat. The behavior in each of these cases is similar for calling. If users do not run both clients, it can easily lead to frustration.

Presence also functions independently between Teams and Skype for Business using this upgrade method. This means other users may see different presence states for User A, depending on which client they use. For more details, see [Presence](upgrade-to-Teams-on-prem-overview.md#presence).

- Other users, when using Teams, will see presence based on User A’s activity in Teams.
- Other users, when using Skype for Business, will see presence based on User A’s activity in Skype for Business.

Once you are ready to upgrade users to TeamsOnly mode, you can upgrade users individually or you can upgrade the entire tenant at once using the tenant-wide policy<sup>3</sup>. Once a user is upgraded to TeamsOnly mode, they receive all incoming chats and calls in Teams.

However, non-upgraded recipients in Islands mode may continue to receive chats and calls from a TeamsOnly user in either their Skype for Business or Teams clients. For existing conversations the TeamsOnly user will reply to the client the sender initiated the chat or call from. 

For new conversations from the TeamsOnly user’s point of view, the chat or call will always go to the Islands mode users Teams client. This is because the Teams client maintains separate conversation threads for Teams-to-Teams and Teams-to-Skype for Business communication, even for the same user. To learn more, see [Teams Conversations - Interop versus native threads](upgrade-to-Teams-on-prem-overview.md#teams-conversations---interop-versus-native-threads).

The following table summarizes the Teams experience for both Islands mode and TeamsOnly mode:

| Teams experience | In Islands mode | In TeamsOnly mode |
|:------------------ | :------------------- | :------------------ |
| Incoming chats and calls received in:|  Teams or Skype for Business | Teams |
| PSTN calls received in: | Skype for Business <br>(Using PSTN functionality in Teams is not supported in Islands mode.) 	| Teams |   
 |Presence	| Presence in Skype for Business and Teams is independent. Users may see different states for the same Islands user, depending on which client they use. | Presence is based solely on the user’s activity in Teams. All other users, regardless of which client they use, see that presence. | 
 | Meeting Scheduling	| Users can schedule meetings in either Teams or Skype for Business. They will see both add-ins in Outlook.	| 	Users only schedule meetings in Teams. Only the Teams add-in is available in Outlook. | 

The following table summarizes the pros and cons of using the overlapping capabilities method to migrate your organization to Teams.

| Pros     |       Cons |
| :------------------ | :---------------- |
| Allows for rapid adoption within an organization.| Potential for end user confusion because there are two clients with similar functionality, but different user interfaces. Also, they have no control over which client the incoming chats/calls land in. |
| Allows users to learn and get familiar with Teams while still having full access to Skype for Business. | Potential for end user dissatisfaction due to missed messages if the user is not running both clients.|
| Minimal administration effort to get started in Teams. | Can be challenging to “get out of Islands” mode and move to TeamsOnly mode if users and those they regularly communicate with are not actively using Teams.|
|Enables users to leverage capabilities to enhance teamwork that are not available in Skype for Business.| A user who is using Skype for Business on premises and Teams will not be able to communicate from Teams with another user who is using Skype for Business on premises but does not have Teams.  |

<sup>2</sup>This is true even if the user is homed on-premises in Skype for Business Server. Whether the user is homed on-premises or online, leave the Skype for Business Online license enabled, because it is currently needed for full Teams functionality.

<sup>3</sup>Note that migration of Skype for Business meetings to Teams meetings is only triggered when applying TeamsUpgradePolicy to individual users, not on a per tenant basis. See [Meeting migration](upgrade-to-Teams-on-prem-overview.md#meeting-migration) for details.

## Select capabilities method (using Skype for Business modes)

Some organizations may prefer to provide their end users a more predictable experience as their organization transitions from Skype for Business to Teams. In this model, IT administrators use one of the Skype for Business modes in TeamsUpgradePolicy to explicitly designate which capabilities remain in Skype for Business prior to migrating to TeamsOnly mode. As they are ready to shift selected capabilities to TeamsOnly mode, the administrator updates the mode for those users to TeamsOnly. During this transition:

- Administrators have options to enable certain Teams capabilities for users while keeping chat and calling capabilities in Skype for Business before users move to TeamsOnly experience. Administration can enable Teams collaboration capabilities or Teams meetings + collaboration capabilities.
- Users still on Skype for Business receive all incoming chats and calls in their Skype for Business client, regardless of whether the communication originated from the other user’s Teams or Skype for Business client. In addition, for these Skype for Business users, calling and chat functionality in the Teams client are disabled to help prevent end user confusion and to ensure proper routing and presence.
- Users in TeamsOnly mode receive all incoming chats and calls in their Teams client and presence is provided by Teams, regardless of where the communication originated from: Teams, Skype for Business, or any kind of federated user.

Unlike the overlapping capabilities method, in the select capabilities method, users using Skype for Business can communicate with users who are in TeamsOnly. Communication between a Skype for Business user and Teams user is known as [interoperability](upgrade-to-Teams-on-prem-overview.md#interoperability) or “interop”. Interop communication is possible on a one-to-one basis for chats and calls between a user in Skype for Business and another user in Teams. In addition, invited users can always join either a Skype for Business or Teams meeting, however, they must use a client that corresponds to the type of meeting. For more information, see [Meetings](upgrade-to-Teams-on-prem-overview.md#meetings).

For users in a select capabilities method, presence for a user is consistent regardless of which client is used by the other user. If the user is in one of the Skype for Business modes, all other users see presence based on that user’s activity in Skype for Business. Similarly, if a user is in TeamsOnly mode, all other users see presence based on that user’s activity in Teams. For details, see [Presence](upgrade-to-Teams-on-prem-overview.md#presence).

For an organization that has chosen to follow the select capabilities method, the administrator should change the tenant-wide mode from Islands to the appropriate Skype for Business coexistence mode (SfbWithTeamsCollab or SfBWithTeamsCollabAndMeetings).  

Guests user experiences will adhere to the coexistence mode assigned to the tenant. If you set a Skype for Business  mode at the tenant level, guests can't chat, call, or show their presence. To learn more, read [Guest access in Teams](guest-access.md).

When the mode changes from Islands to SfbWithTeamsCollab, a user that has never used Teams will see no difference in how they use Skype for Business. However, should that user start to use Teams, they would only be exposed to functionality such as Teams & Channel and Files. Chat, calling and meeting scheduling would not be available in Teams, since the administrator has (for now) designated Skype for Business as the desired client for those functions.

> [!NOTE]
> When User A changes from Islands to one of the Skype for Business modes, the Teams client of any other user that communicates with User A needs to know that User A’s mode changed so it can route the communication to the appropriate client for User A. For any users who have already established native Teams-to-Teams chats with User A, it can take time for these other users' Teams clients to be aware of the mode change from Islands to any Skype for Business mode. 
> When administrators are ready, they can shift chat, calling, and meeting scheduling for a given user to Teams all at once by updating the user’s mode to TeamsOnly.

Alternatively, the administrator can first shift only meeting scheduling to Teams, while leaving chat and calling functions in Skype for Business using the SfBWithTeamsCollabAndMeetings mode. This mode allows organizations to transition to Teams for meetings--if users are not yet ready to move to TeamsOnly mode (for example, you are not yet ready to migrate existing PSTN functionality). This transitional scenario is referred to as [Meetings First](meetings-first.md).


|Teams experience  |In SfBWithTeamsCollab mode |In SfBWithTeamsCollabAndMeetings mode |In TeamsOnly mode  |
|---------|---------|---------|---------|
|Incoming chats and VOIP calls from users in your organization received in:     | Skype for Business        | Skype for Business       | Teams        |
|PSTN calls received in:     | Skype for Business        |Skype for Business         | Teams        |
|Presence     | Skype for Business        |Skype for Business         | Teams        |
|Meeting Scheduling     | Skype for Business         | Teams        | Teams        |


The following table summarizes the pros and cons of using Skype for Business modes as a transitional step toward TeamsOnly mode.

| Pros     |       Cons |
| :------------------ | :---------------- |
| Predictable routing for the end user. All calls and chats either land in Skype for Business or Teams (but not both), based on administrator selection.|Interop conversations lack support for rich text, file sharing, and screen sharing. This can be worked around leveraging Meet Now functionality to initiate a meeting. |
|May reduce end user confusion because a given functionality is only available in one client. | Users are do not have access to Teams for common activities performed in Skype for Business such as chat and calling ahead of upgrading to TeamsOnly.|
|Administrator has increased control over the set of capabilities available to users while transitioning from Skype for Business to Teams. | |
| Allows an organization to use Teams for meetings, even if it is not yet ready to move entirely to TeamsOnly mode.||
|Presence of a given user as viewed by others is the same, regardless of which client they use.||

## Summary of upgrade methods
The following table summarizes the upgrade methods:


|Overlapping capabilities (using Islands mode)  |Selected capabilities (using Skype for Business modes)  |
|---------|---------|
|Prior to being upgraded to TeamsOnly, users must run both clients simultaneously since incoming chats and calls may land in either client.     | Chats and calls only land in one client, based on the recipient’s mode. Non-upgraded users may run both clients, but there is no functional overlap (calling and chat are not available in Teams).         |
|Allows administrators to introduce overlapping functionality (chat, meetings, VOIP calling) in both Skype for Business and Teams to end users as well as new capabilities (Teams and Channels) in Teams.     | Allows administrators to introduce select functionality of Teams to end users (Teams and Channels), without providing same functionality that also exists in Skype for Business.        |
|Interop between Skype for Business and Teams does not exist while both users are in Islands mode.      |Interop is required for communication between Skype for Business and Teams users.         |

> [!NOTE]
> If you are unable to follow supported methods for migrating your Skype for Business Server users to Teams, it would be possible to transition your users to Teams by removing Skype for Business Server and all related user attributes in Active Directory. Once the users Azure Active Directory attributes have been cleared of the Skype for Business Server attributes and DNS records have been re-pointed to Office 365, it would then be possible to license the users in Office 365 and upgrade them to Teams. 

> [!IMPORTANT]
> With the cutover migration, contact data and meetings data will not be migrated from on premises environment to Microsoft Teams.

<table>
<tr><td><img src="media/audio_conferencing_image7.png" alt="An icon depicting a decision point"/> <br/>Decision point</td><td><ul> Which upgrade journey is suitable to your organization's business requirements?<br><br></ul></td></tr>
<tr><td><img src="media/audio_conferencing_image9.png" alt="An icon depicting the next step"/><br/>Next step</td><td><ul> Identifying your current deployment model, use case scenarios, and key considerations for your organization will inform the journey to Teams that’s best suited to your organization.<br><br></ul></td></tr>
</table>

<table>
<tr><td><img src="media/audio_conferencing_image7.png" alt="An icon depicting a decision point"/> <br/>Decision point</td><td><ul> Which upgrade scenario is applicable to your organization?<br><br></ul></td></tr>
<tr><td><img src="media/audio_conferencing_image9.png" alt="An icon depicting the next steps"/><br/>Next steps</td><td><ul> Decide the timeline of your organization's upgrade journey based on messaging, meetings, and calling business requirements.<br><br> Decide the required additional work to complete your upgrade journey.<br><br></ul></td></tr>
</table>

After you’ve chosen the best upgrade journey for your organization, [perform your upgrade to Teams](https://aka.ms/SkypeToTeams-Upgrade).
