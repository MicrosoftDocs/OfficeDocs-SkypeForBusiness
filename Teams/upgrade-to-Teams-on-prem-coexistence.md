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

# Coexistence with Teams and Skype for Business

This article summarizes behavior that may be experienced when running both Teams and Skype for Business clients in the same organization, regardless of what mode and what upgrade method is used:

- [Meetings](#meetings)
- [Interoperability](#interoperability)
- [Teams conversations-Interop versus native threads](#teams-conversations---interop-versus-native-threads)
- [Presence](#presence)
- [Federation](#federation)
- [Contacts](#contacts)



## Meetings

Regardless of their mode, users can always join any type of meeting they are invited to, whether it is Skype for Business or Teams.  However, users must join the meeting with a corresponding client that matches the meeting type:

- If the meeting is a Teams meeting, all participants (whether they are TeamsOnly, Islands, or Skype for Business users) use the Teams client to join the meeting. If Teams is not installed, the user will be directed to the web, upon attempting to join a meeting.

- If the meeting is a Skype for Business meeting, all participants (whether they are TeamsOnly, Islands, or Skype for Business users) use the Skype for Business client to join the meeting. If the Skype for Business client is not installed, the user will be directed to the web to join via the Skype Meeting App.

When organizing meetings, the meeting type that gets scheduled is based on the mode of the organizer, as shown in the following table:

| Mode of organizer    |      Behavior |
| :------------------ | :---------------- |
| TeamsOnly, SfbWithTeamsCollabAndMeetings | 	All meetings scheduled in Teams. Skype for Business add-in is not available in Outlook. | 
| SfbWithTeamsCollab, SfbOnly	| All meetings scheduled in Skype for Business. Teams add-in is not available in Outlook. | 
| Islands | 	Meetings can be scheduled in either Skype for Business or Teams. Both add-ins are available in Outlook. | 


## Interoperability

Teams supports interoperability (“interop”) with Skype for Business in certain scenarios. Interop communication refers to a chat or call between a Skype for Business user and a Teams user.  Interop communication is only possible between two users; multi-party chat/calling or adding additional users is not supported.

An interop chat or call between two users is created when each of the following are true:

- One user is using Teams and the other is using Skype for Business.

- The mode of the recipient of the initial communication is NOT Islands (otherwise the communication would land in the same client) if both users are in the same organization. In federated scenarios, the sending user is using Teams, and the recipient is not in TeamsOnly mode. 

- The Teams user does NOT also have a Skype for Business account homed on-premises. 

Within the interop communication, chat is plain-text only. In addition, file sharing and screen sharing are not possible *in the interop chat itself*. However, users in an interop conversation can easily achieve file and/or screen sharing by creating an on-demand meeting, from within the interop chat, as described below:

- If the Teams user attempts to share their screen, an on-demand Teams meeting is automatically created and an invite link to that meeting is sent to the Skype for Business user’s client. Upon clicking the link, the Skype for Business user will open Teams and join the meeting. Both users are now in a Teams meeting and can share as needed.

- If the Skype for Business user is using a client from 2018 or later and attempts to share any content, an on-demand Skype for Business meeting is automatically created and an invite link to that meeting is sent to the Teams user’s client. Upon clicking the link, the Teams user will attempt to join the Skype for Business meeting. If the Teams user has the Skype for Business client installed, it will open and the user is prompted to sign in (if not already signed in).  If the Teams user does not have the Skype for Business client installed, the user will be prompted to use the web version. Once both users are signed in, they are in a Skype for Business meeting and can share as needed.

## Teams conversations - Interop versus native threads

Because interop communications do not support all the features of native Teams conversation, the Teams client maintains separate conversation threads for Teams-to-Teams and Teams-to-Skype for Business communication. These conversations are rendered differently in the user interface: Interop threads can be differentiated from a regular native Teams thread by:

- Lack of controls for rich text, file/screen sharing, inability to add users.
- A modification to the target user’s icon, showing an “S” for Skype for Business.

These differences are shown in the following screenshots:

A native Teams-to-Teams conversation with User G3 Test

![Diagram showing a native Teams-to-Teams conversation](media/teams-upgrade-native-thread.png)

An interop conversation with the same User G3 Test

![Diagram showing an interop Teams-to-Teams conversation](media/teams-upgrade-interop-thread.png)

Once a conversation thread is created, its type never changes. Once created, an interop thread in Teams will always route to the target user’s Skype for Business client. A native thread will always route to the target user’s Teams client.  If a recipient user’s mode changes, existing Teams threads to that user will no longer function and a note will be displayed on that chat with a link to start a new native conversation as shown in the following screenshot. For more details, see [Chats and calls from pre-existing threads](coexistence-chat-calls-presence.md#chats-and-calls-from-pre-existing-threads).


![Diagram showing a chat with upgraded Skype for Business user](media/teams-upgrade-chat-with-upgraded-sfb-user.png)

## Presence

Presence for a given user is based on the user’s activity in the service via the client. The presence is then published for other users to see.  Skype for Business and Teams are separate services with separate clients, so each service has its own presence state for a user.   There is also synchronization between the presence services in Teams and in Skype for Business Online.  This allows one service to potentially publish the presence of the user from the other service if needed. 

Presence publishing behavior is based on the user’s mode. There are three basic cases:

- If a user is in TeamsOnly mode, all other users see Teams presence for that user, regardless of which client they use.

- If a user is in any of the Skype for Business modes, all other users see Skype for Business presence for that user, regardless of which client they use.

- If a user is in Islands mode, presence published in Skype for Business and Teams are independent, so the presence shown to users within the same organization will depend on the client of the other user. Users in federated organizations will see presence of that user based on their Skype for Business activity, since federated traffic to an Islands mode user lands in Skype for Business.

For example, Assume User A is in Islands mode. If User A is active in Teams but is not signed in to Skype for Business, other users would see User A as active from their Teams client, but in their Skype for Business client they would see User A as offline. This is by design, since User A cannot be reached if they are not running the client. 

For additional information, see [Presence](coexistence-chat-calls-presence.md#presence).

## Federation

Federation from Teams to another user using Skype for Business requires the Teams user to be homed online in Skype for Business. TeamsUpgradePolicy governs routing for incoming federated chats and calls. Federated routing behavior is the same as for same-tenant scenarios, except in Islands mode. When recipients are in Islands mode:

- Chats and calls initiated from Teams land in Skype for Business if the recipient is in a federated tenant.
- Chats and calls initiated from Teams land in Teams if the recipient is in the same tenant.
- Chats and calls initiated from Skype for Business always land in Skype for Business.

A federated chat between a Teams user and a Skype for Business is an interop thread, so rich text and sharing are not possible. The user interface exposes federated chats in a similar manner to same-tenant interop threads, except there is a note indicating the user is external.

When Teams first introduced federation, a federated chat between two Teams users was also an interop thread, but in the future, native Teams federation will be introduced which provides full functionality for conversations between users who are in TeamsOnly mode. . 

For more details, see [Federated routing for new chats or calls](coexistence-chat-calls-presence.md#federated-routing-for-new-chats-or-calls).

## Contacts

Teams and Skype for Business have separate lists of contacts. This means that contact additions, removal, and modifications made in one system are not synchronized to the other system. However, contacts from Skype for Business are automatically copied over to Teams when either of two specific events occur: 

- For any Skype for Business Online user, the first time they log onto Teams, contacts from Skype for Business will be copied over to Teams.  This behavior is not available for users with an on-premises account in Skype for Business Server.  

- After a user is upgraded to TeamsOnly (either via assigning TeamsUpgradePolicy or via Move-CsUser -MoveToTeams), the next time a user logs into Teams, existing contacts in Skype for Business will be merged with existing contacts already in Teams. This behavior happens whether the user’s Skype for Business Account is homed on-premises or online. 

In both cases, the transfer of contacts from Skype for Business to Teams is asynchronous so it may be a few minutes before contacts appear in Teams. The two events above are what trigger the copy.  

## Related links

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md) 

[Configure hybrid connectivity between Skype for Business Server and Microsoft 365 or Office 365](https://docs.microsoft.com/SkypeForBusiness/hybrid/configure-hybrid-connectivity)

[Move users between on-premises and cloud](https://docs.microsoft.com/SkypeForBusiness/hybrid/move-users-between-on-premises-and-cloud)

[Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md)

[Grant-CsTeamsUpgradePolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsupgradepolicy?view=skype-ps)

[Using the Meeting Migration Service (MMS)](https://docs.microsoft.com/skypeforbusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms)

