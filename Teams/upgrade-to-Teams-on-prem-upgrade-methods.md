---
title: Upgrade to Teams from a Skype for Business on-premises deployment - Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 10/22/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: bjwhalen
description: Upgrade from Skype for Business to Teams  
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: Teams-upgrade-guidance
ms.collection: 
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Upgrade from Skype for Business to Teams &mdash; for IT administrators

## Upgrade methods

There are two methods for migrating an existing organization with Skype for Business (whether online or on-premises) to Teams: Overlapping capabilities method, and the Select capabilities method.  This article helps you choose the right method for your organization by describing both methods and presenting the pros and cons of each. 

- [Overlapping capabilities method (using Islands mode)](#overlapping-capabilities-method-using-islands-mode)

   Users in an existing Skype for Business organization are introduced to Teams so that they can use both clients during a transitional phase. During this period, most--but not all--functionality of Teams is available to them. The mode for this configuration is referred to as Islands, and this is the default mode for any existing organization with Skype for Business. Once the organization is ready, the administrator moves the users to TeamsOnly mode.

- [Select capabilities method (using one or more of the Skype for Business modes)](#select-capabilities-method-using-skype-for-business-modes)

   The administrator manages the transition (from Skype for Business to Teams) of chat, calling, and meeting scheduling functionality for users in their organization.  Each of these functions is available either in Skype for Business or Teams, but not both. Administrators use TeamsUpgradePolicy to control when to shift this functionality to Teams for their users. Users who are not yet in TeamsOnly mode continue to use Skype for Business for chat and calling, and the two sets of users can communicate via interop functionality. Administrators manage the transition by progressively migrating more users into TeamsOnly mode.  

## Overlapping capabilities method (using Islands mode)

With the overlapping capabilities method, users can use both Teams and Skype for Business clients for chat, VoIP calling, and meetings. This state is referred to as “Islands” mode because the communication traffic for Skype for Business and Teams remains separate (even for the same user) and the two different clients never communicate with each other (for users within the same organization). For example, assume recipient User A is in Islands mode:

- Communication initiated from another user’s Skype for Business client will always land in User A’s Skype for Business client.

- Communication initiated from another user’s Teams client will always land in User A’s Teams client, *if the other user is in the same organization*. 

- Communication initiated from another user’s Teams client will always land in User A’s Skype for Business client, *if the other user is in a federated organization*.

Islands mode is the default mode of TeamsUpgradePolicy for any existing organization that is not yet TeamsOnly. When you assign a Microsoft 365 or Office 365 license, both Teams and Skype for Business Online licenses are assigned by default. (This is true even if the user is homed on-premises in Skype for Business Server. Whether the user is homed on-premises or online, leave the Skype for Business Online license enabled, because it is currently needed for full Teams functionality.) In fact, if you have not taken any steps to change the default configuration, you may already have significant usage of Teams in your organization.  This is one of the benefits of the overlapping capabilities approach. It allows for rapid, end-user driven adoption within an organization.

For this method to work effectively, it requires all users to run both clients simultaneously. Incoming chats and calls from within the organization to a user in Islands mode can land in either the Skype for Business or Teams client--and this is not under the control of the recipient. It depends on what client the sender uses to initiate the communication. If the sender and recipient are in different organizations, incoming calls and chats to a user in Islands mode always land in the Skype for Business client.  

For example, if an Islands mode recipient is running Skype for Business but not Teams, and someone messages them from Teams, the Islands mode recipient will not see the message (but they will eventually get an email saying they missed a message in Teams). Likewise, if a user is running Teams but not Skype for Business, and someone messages that user from Skype for Business, the user will not see that chat.  They will get an email saying there was a missed message. The behavior in each of these cases is similar for calling. If users do not run both clients, it can easily lead to frustration.

When User A is in Islands mode, User A’s presence as seen by other users in Teams and in Skype for Business is independent:

- Other users, when using Teams, will see presence based on User A’s activity in Teams. 
- Other users, when using Skype for Business, will see presence based on User A’s activity in Skype for Business. 

This means other users may see different presence states for User A, depending on which client they use. For more details, see [Presence](upgrade-to-teams-on-prem-coexistence.md#presence).

Once you are ready to upgrade users to TeamsOnly mode, you can upgrade users individually or you can upgrade the entire tenant at once using the tenant-wide policy. Once a user is upgraded to TeamsOnly mode, they receive all incoming chats and calls in Teams. (Note that migration of Skype for Business meetings to Teams meetings is only triggered when applying TeamsUpgradePolicy to individual users, not on a per tenant basis. See [Meeting Migration](upgrade-to-teams-on-prem-tools.md#meeting-migration) for details.)

However, non-upgraded recipients in Islands mode may continue to receive chats and calls from a TeamsOnly user in either their Skype for Business or Teams clients.  This is because the Teams client maintains separate conversation threads for Teams-to-Teams and Teams-to-Skype for Business communication, even for the same user.  (See [Teams Conversations - Interop versus native threads](upgrade-to-teams-on-prem-coexistence.md#teams-conversations---interop-versus-native-threads).)  For example, assume Islands User A uses Teams to message TeamsOnly User B. When User B replies to that chat, the communication will land in User A’s Teams client. Now assume User A uses his Skype for Business client to message TeamsOnly User B. User B will receive the chat in Teams, but this will be a separate conversation in User B's Teams client compared to the other conversation. If User B replies to this conversation with User A, it will land in User A’s Skype for Business client. 

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
| Allows users to learn and get familiar with Teams while still having full access to Skype for Business. | Potential for end user dissatisfaction due to missed messages if the user is not running both clients. Users may complain that they are not receiving messages.|
| Minimal administration effort to get started in Teams. | Can be challenging to “get out of Islands” mode and move to TeamsOnly mode if not everyone in the organization is using Teams, especially if not all users are active in Teams. For example, once a subset of users is upgraded to TeamsOnly mode, those users will only send in Teams. For the rest of the population in Islands mode, those messages will always land in Teams. But if some of that population is not running Teams, they will perceive these messages as missed. |
|  | When using Teams, users who have an on-premises account in Skype for Business Server do not have interop or federation support.  This can potentially create confusion if you have a mix of Islands users--some who are homed in Skype for Business Online and some in Skype for Business on-premises.   |

## Select capabilities method (using Skype for Business modes)

Some organizations may prefer to provide their end users a simpler, more predictable experience as their organization transitions from Skype for Business to Teams. In this model, IT administrators use one of the Skype for Business modes in TeamsUpgradePolicy to explicitly designate which users remain in Skype for Business prior to migrating to TeamsOnly mode. As they are ready to shift selected users to TeamsOnly mode, the administrator updates the mode for those users to TeamsOnly. As the deployment progresses, more and more users are transitioned from Skype for Business to TeamsOnly mode.  During this transition:

- Users still on Skype for Business receive all incoming chats and calls in their Skype for Business client, regardless of whether the communication originated from the other user’s Teams or Skype for Business client. In addition, for these Skype for Business users, calling and chat functionality in the Teams client are disabled to help prevent end user confusion and to ensure proper routing. 

- Users in TeamsOnly mode receive all incoming chats and calls in their Teams client, regardless of where the communication originated from:  Teams, Skype for Business, or any kind of federated user. 

Unlike the Islands method, in the select capabilities method, Skype for Business users and TeamsOnly users can communicate with each other. Communication between a Skype for Business user and Teams user is known as interoperability or “interop”. (See [Interoperability](upgrade-to-teams-on-prem-coexistence.md#interoperability).) Interop communication is possible on a one-to-one basis for chats and calls between a user in Skype for Business and another user in Teams. In addition, invited users can always join either a Skype for Business or Teams meeting, however, they must use a client that corresponds to the type of meeting. For more information, see [Meetings](upgrade-to-teams-on-prem-coexistence.md#meetings).

Because users in a select capabilities transition are typically not in Islands mode, presence for a user is consistent regardless of which client is used by the other user. If the user is in one of the Skype for Business modes, all other users see presence based on that user’s activity in Skype for Business. Similarly, if a user is in TeamsOnly mode, all other users see presence based on that user’s activity in Teams. For details, see [Presence](upgrade-to-teams-on-prem-coexistence.md#presence).

For an organization that has not yet started using Teams, the administrator should change the tenant-wide mode from Islands to SfbWithTeamsCollab. (For organizations that already have some Teams usage, the administrator should “grandfather” users already active in Teams to ensure this change does not apply to them. For details, see [A select capabilities method for an organization that is already using Teams in Islands mode](upgrade-to-teams-on-prem-implement.md#a-select-capabilities-upgrade-for-an-organization-that-is-already-using-teams-in-islands-mode).)

When mode changes from Islands to SfbWithTeamsCollab, a user that has never used Teams will see no difference in how they use Skype for Business. However, should that user start to use Teams, they would only be exposed to functionality such as Teams & Channel and Files. Chat, calling and meeting scheduling would not be available in Teams, since the administrator has (for now) designated Skype for Business as the desired client for those functions.  

Note: When User A changes from Islands to one of the Skype for Business modes, the Teams client of any other user that communicates with User A needs to know that User A’s mode changed so it can route the communication to the appropriate client for User A.  For any users who have already established native Teams-to-Teams chats with User A, it can take up to 36 hours for these other users' Teams clients to be aware of the mode change from Islands to any Skype for Business mode.   In contrast, changes for an existing user to TeamsOnly mode are discovered by other clients within 2 hours.

When administrators are ready, they can shift chat, calling, and meeting scheduling for a given user to Teams all at once by updating the user’s mode to TeamsOnly.  

Alternatively, the administrator can first shift only meeting scheduling to Teams, while leaving chat and calling functions in Skype for Business using the SfBWithTeamsCollabAndMeetings mode. This mode allows organizations to transition to Teams for meetings--if users are not yet ready to move to TeamsOnly mode (typically because more time may be needed to migrate existing PSTN functionality). This transitional scenario is referred to as [Meetings First](meetings-first.md).

The following table summarizes the pros and cons of using Skype for Business modes as a transitional step toward TeamsOnly mode.


| Pros     |       Cons |
| :------------------ | :---------------- |
| Predictable routing for the end user.  All calls and chats either land in Skype for Business or Teams (but not both), based on administrator selection.  | Interop conversations lack support for rich text, file sharing, and screen sharing.  This can be worked around with on-demand meetings but this is not as seamless.  |
| Eliminate end user confusion because a given functionality is only available in one client.  | Users can’t try both clients side by side for the same set of functionality. This may especially be a factor if the users perceive the shift from Skype for Business to Teams as a major paradigm shift. |
| Allows for incremental introduction of Teams.  |  | |
| Administrator is in full control of the transition from Skype for Business to Teams. |  | | 
| Allows an organization to use Teams for meetings, even if it is not yet ready to move entirely to TeamsOnly mode. |  | |
| Presence of a given user as viewed by others is the same, regardless of which client they use.  |  | |

## Summary of upgrade methods

The following table summarizes the upgrade methods:

| Overlapping capabilities (using Islands mode)     |      Select capabilities (using Skype for Business modes) |
| :------------------ | :---------------- |
| Prior to being upgraded to TeamsOnly, users must run both clients simultaneously since incoming chats and calls may land in either client.   | Chats and calls only land in one client, based on the recipient’s mode. Non-upgraded users may run both clients, but there is no functional overlap (calling and chat are not available in Teams).  Administrators can also control whether users schedule meetings in Teams or Skype for Business.   |
| Users can use Skype for Business and Teams side by side for same functionality.   | Allows administrators to introduce net new functionality of Teams to end users (Teams and Channels), without providing same functionality that also exists in Skype for Business.   |
|Interop between Skype for Business and Teams does not exist while both users are in Islands mode. Once some users are upgraded to TeamsOnly, interop conversation may occur between those users and other users still in Islands mode. However, the Islands user could choose to use Teams and avoid the interop conversation. | Interop is required for communication between Skype for Business and Teams users.   |


## Related links

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md) 

[Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](https://docs.microsoft.com/SkypeForBusiness/hybrid/configure-hybrid-connectivity)

[Move users between on-premises and cloud](https://docs.microsoft.com/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud)

[Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md)

[Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps)

[Using the Meeting Migration Service (MMS)](https://docs.microsoft.com/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms)

