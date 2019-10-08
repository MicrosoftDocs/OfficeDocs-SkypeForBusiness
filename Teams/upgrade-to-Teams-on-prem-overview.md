---
title: Upgrade to Teams from a Skype for Business on-premises deployment - Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 01/09/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: bjwhalen
description: Upgrade from Skype for Business to Teams  
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Upgrade from Skype for Business on-premises to Teams

## Overview

When upgrading from Skype for Business to Teams, some organizations require a progressive rollout that is planned and managed by their IT departments.  This article is primarily targeted to IT administrators in large,on-premises organizations, but it might also apply to some Skype for Business Online organizations.  

To implement your upgrade strategy, you specify the appropriate upgrade mode for your users in the TeamsUpgradePolicy. For a succesful Teams migration, the ultimate goal is to move all users to TeamsOnly mode. 
 
In TeamsOnly mode, all incoming chats and calls land in the Teams client, regardless of what client the sender is using.  A TeamsOnly user initiates all chats and calls from the Teams client, and all new meetings are scheduled in Teams.  A TeamsOnly user can, however, still use the Skype for Business client if necessary to join Skype for Business meetings. 

There are two methods for migrating an existing organization with Skype for Business to Teams:

- **A side-by-side method**, using Islands mode, in which users in the organization continue to use both Skype for Business and Teams until the migration is complete and all users are in TeamsOnly mode.  With this approach, users have access to most, but not all, Teams functionality until the migration is complete.

- **A phased method**, using one of the Skype for Business modes, in which users continue to use Skype for Business for core functionality, such as chat and calling, while using Teams for other functionality, such as Meetings. With this approach, you will progressively move more and more users to TeamsOnly mode until the migration is complete.  Users in the Skype for Business modes can continue to communicate with one another via client interoperability, but a given set of functionality, such as chat and calling, is available to them only in one client.

This article helps you choose the right method for your organization by describing the pros and cons of both methods.


## Side-by-side method (with two clients)

With the side-by-side method, users can use both Teams and Skype for Business for chat, VOIP calling, and meetings. This state is referred to as “Islands” mode, because the users in Skype for Business and those in Teams are like islands: The communication paths remain separate (at least for users within the same organization). For example, assume recipient user, A, is in Islands mode: 

- Communication initiated from another user’s Skype for Business client will always land in A’s Skype for Business client. 
- Communication initiated from another user’s Teams client will always land in A’s Teams client, if the other user is in the same organization. 
- Communication initiated from another user’s Teams client will always land in A’s Skype for Business client, if the other user is in a federated organization. 

Islands mode is the default mode in TeamsUpgradePolicy for any existing organization that is not yet TeamsOnly. When you assign an Office 365 license, both Teams and Skype for Business Online licenses are assigned by default.  In fact, if you have not taken any steps to change the default configuration, you may already have significant usage of Teams in your organization.  

The side-by-side approach allows for rapid adoption within an organization. 
 
> [!NOTE]
> For this model to work effectively, all users must run both clients simultaneously. Incoming chats and calls can land in either the Skype for Business or Teams client--depending on which client the sender used to initiate the communication.  The recipient cannot control which client receives the communication.

Therefore, for this method to succeed, you must run both clients.  For example, if an Islands mode recipient is only running Skype for Business, and someone messages them from Teams, the recipient will not see the message, but they will get an email saying they missed a message in Teams. Likewise, if a user is running Teams but not Skype for Business, and someone messages that user from Skype for Business, the user will not see that chat.  Instead, they will get an email saying there was a missed message. The behavior in each of these cases is similar for calling. 

When a user is in Islands mode, the presence for that user published to other users corresponds to the Island-mode user’s activity in their respective clients. For example, if a user is active in Teams but has not signed in to Skype for Business, other users would see this user as active from their Teams client, but from their Skype for Business client they would see the user as offline. This is by design, since the user is not available in a client that is not running. 

Once you are ready to upgrade users to TeamsOnly mode, you can upgrade users individually or you can upgrade the entire tenant at once using the tenant-wide policy. Once a user is upgraded to TeamsOnly, they receive all incoming chats and calls in Teams. However, non-upgraded recipients in Islands mode may receive chats and calls in either Skype for Business or Teams, depending on how in the Teams client the TeamsOnly user. 

Note that using Teams in Islands mode is not the same as being in TeamsOnly mode: 

- TeamsOnly: all incoming chats and calls, regardless of where from (another Teams user, another Skype for Business user, federated user), always land in Teams. 
- Full PSTN functionality is available only in TeamsOnly mode.  
- Presence.  Other users will see different presence for a user, depending on what client they are using, and depending on the watched user’s activity in each client. In contrast, in TeamsOnly, users in any client will see the user’s presence based on their activity in Teams. 

| Pros     |       Cons |
| :------------------ | :---------------- |
| Allows for rapid adoption within an organization.| Potential for end user confusion of using both clients. Some users confused about having two apps that do the same thing and having different ways of doing the same thing. Also, they have no control of which client the incoming chats/calls land in. |
| Allows users to learn and get familiar with Teams while still having full access to Skype for Business. | Potential for end user dis-satisfaction due to missed messages, if user is not running both clients. Users may complain that they are not receiving messages. |
| Minimal administration effort to get started in Teams. | Challenging to get out of “islands” mode to TeamsOnly if not everyone in the org is using Teams, especially if not all users are active in Teams. For example once a subset of users is upgraded to TeamsOnly, those users will only ever send in Teams. Which means for the rest of the population in Islands mode, those messages will always land in Teams. But if some of that population is not running Teams because they will perceive this as missed messages. |
|  | When using Teams, users who have Skype for Business homed on-premises do not have interopability or federation support.  This can potentially create confusion if you have a mix of Islands users some of which are homed in Skype for Business Online and others are in Skype for Business on-premises.  |


## Phased method (with client interoperability)

You might prefer to provide your users with a simpler, more predictable experience as your organization transitions from Skype for Business to Teams. In this model, you use the TeamsUpgradePolicy to explicitly designate which users remain in Skype for Business prior to migrating to TeamsOnly. As the deployment progresses, you transition more and more users from Skype for Business to TeamsOnly.  During this transition: 

- For users still on Skype for Business, all incoming chats and calls are routed to the user’s Skype for Business client, regardless of whether the communication originated from the other user’s Teams or Sfb client. In addition, for these Skype for Business users, calling and chat functionality in the Teams client are disabled to help prevent end user confusion and to ensure proper routing.  

-  For users in TeamsOnly mode, all incoming chats and calls are always routed to that user’s Teams client, regardless of where the communication originated from, be it Teams, Skype for Business or any kind of federated user.

Unlike the side-by-side Islands method, in this method Skype for Business and TeamsOnly users can communicate with each other. Communication between a Skype for Business user and a Teams user is known as interoperability. Interop communication is possible on a one-to-one basis for chats and calls between a user in Skype for Business and another user in Teams. In addition, eligible users can always join either an Skype for Business or Teams meetings, however, they must use a client that corresponds to the type of meeting. 

### Meetings

Regardless of whether a user is a Teams only user or a Skype for Business user, the user can always join any type of meeting they are invited to, whether Skype for Business or Teams.  Users must join the meeting with a corresponding client that matches the meeting type: 

- If the meeting is a Teams meeting, all participants (whether they are Teams only, Islands, or Skype for Business users) use Teams client to join the meeting. 

- If the meeting is a Skype for Business meeting, all participants (whether they are Teams only, Islands, or Skype for Business users) use Skype for Business client to join the meeting. 

When *organizing* meetings, a TeamsOnly user will always schedule the meeting in Teams.  Depending on the admin configuration, Skype for Business users schedule meetings either in Skype for Business or in Teams. This is based on the coexistence mode of the user, as defined in TeamsUpgradePolicy.  If a user is in either SfbWithTeamsCollab or SfbOnly mode, meeting scheduling in Teams is explicitly disabled since the intent is for all meetings organized by that user to be scheduled in Skype for Business. Conversely, for a user in SfBWithTeamsCollabAndMeetings mode, the intent is for that user to schedule all meetings in Teams, so meeting scheduling is disabled in Skype for Business and explicitly enabled in Teams. 

### Interoperability

Interopability refers to a chat or call between a Skype for Business user and a Teams user. Within this  communication, there are some limitations to be aware of: 

- No group chats or calls are possible. Communication is between two users: one in Skype for Business and one in Teams. 
- Chat is plain text only; there is no support for rich text. 
- File sharing and screen sharing are not possible. 

Although group chat, file and screen sharing are not possible directly in the interop chat, users can easily accomplish these tasks by creating an on-demand meeting, from within the interop chat.  

- If the Teams user does this, an on-demand Teams meeting is created and an invite to that meeting is received in the Skype for Business user’s client. Upon clicking the link, the Skype for Business user will open Teams and join the meeting. 

- If the Skype for Business user does this, an on-demand Skype for Business meeting is created and an invite to that meeting is received in the Teams user’s client. Upon clicking the link, the Teams user will open Skype for Business and join the meeting. If the Teams users has the Skype for Business client installed, it will be opened. Otherwise, the user will be prompted to use the web version. 

### Pros and cons   (needs another title)

| Pros     |       Cons |
| :------------------ | :---------------- |
| Predictable routing for the end user. All calls and chats either land in SFB or Teams, based on admin selection.  | Interop conversations have lower fidelity than Skype for Business to Skype for Business or Teams to Teams.  This can be worked around with on-demand meetings but this is not as seamless.  |
| Eliminate end user confusion because a given functionality is only available in one client.  | Users can’t try out both apps side-by-side, for the same set of functionality.  |
| Allows for incremental introduction of Teams  |  | |
| Admin is in full control of the transition from Skype for Business to Teams.  |

## Summary of migration methods

| Side-by-side (Islands mode)     |      Phased (Skype for Business modes) |
| :------------------ | :---------------- |
| Prior to being upgraded to TeamsOnly, users must run both clients simultaneously since incoming chats and calls may land in either client.   | Chats and calls only land in one client, based on the recipient’s mode. Non-upgraded users may run both clients, both there is no functional overlap; (calling and chat are not available in Teams).  Admin can also control whether users schedule meetings in Teams or Skype for Business.   |
| Users can use SfB and Teams side by side for same functionality.   | Allows admin to introduce net new functionality of Teams to end users (Teams and Channels), without providing same functionality that also exists in Skype for Business.   |
|Interop between Skype for Business and Teams does not exist. |Interop between Skype for Business and Teams exists, but with lower fidelity than a native chat.   |

## Manage the user experience

To manage the upgrade method and the user experience, you use the TeamsUpgradePolicy to specify a user’s coexistence mode. Coexistence mode is a single setting that ensures that routing, presence, and client experience are all aligned. It governs which client a user uses for calling and chat, as well as which client a user uses for scheduling new meetings.  There are five basic modes* which are described below: 

| Mode    |      Calls and chats |    Meeting scheduling   |   Teams Channels available   |   Comments    |
| :------------------ | :---------------- | :---------------- | :---------------- | :---------------- |
| TeamsOnly  | Teams |  Teams  | Yes   |  The final state of being upgraded, as well as the default state for new orgs. | 
 | Islands | Either | Either | Yes | Allows a single user to evaluate both clients side by side.  Chats and calls can land in either client; Users must continue to run both clients.  Default state for existing orgs. |
| SfbWithTeamsCollab | Skype for Business | Skype for Business | Yes | Calls & chats always routed to only one client throughout the migration. Users schedule meetings in Skype for Business. |
| SfBWithTeamsCollabAndMeetings | Skype for Business | Teams |Yes | Calls and chats always routed to only one client throughout the migration. Users schedule meetings in Teams. |
| SfBOnly* | Skype for Business | Skype for Business | No* | Same as SfbWithTeamsCollab. Eventually, Teams & Channels will not available in this mode.  |

**INSERT TABLE HERE**

 
*Effectively there are only four modes because SfBOnly and SfbWithTeamsCollab currently behave identically. In the future, mode may also govern whether Teams and Channels are available in the Teams client.  Teams & Channels are always available in all modes, however in the future, it is expected that Teams & Channels will not be available in the SfBOnly mode. Until that time. SfbOnly and SfbWithTeamsCollab behave identically.

 
Like any other policy in Teams, TeamsUpgradePolicy can be assigned directly to a user, and it can also be set as the tenant-wide default. Any assignment to a user takes precedence over the tenant default setting.  Note that users who are homed in Skype for Business on-premises cannot be assigned TeamsOnly mode. Those users must be moved online (either to Skype for Business Online or direct to Teams) using the Skype for Business on-prem Move-CsUser tool. 

As previously noted, existing Skype for Business organizations are by default in Islands mode, which allows for the side-by-side migration experience.   

Organizations can optionally use any of the Skype for Business coexistence modes (SfBOnly, SfBWithTeamsCollab, SfBWithTeamsCollabAndMeetings) to ensure predictable communication between users who are in TeamsOnly mode and users who aren't yet. Whether an organization choose to use any of these modes or stay in Islands mode, TeamsOnly mode is the final destination for all users in the organization. 

For more information, see Migration and interoperability guidance for organizations using Teams together with Skype for Business and Setting your coexistence and upgrade settings. 

## Considerations for on-premises organizations

If you have an existing Skype for Business Server deployment, consider the following:

- Setting up Skype for Business hybrid connectivity is a pre-requisite to migrate to TeamsOnly. While it is possible to use Teams in islands mode without hybrid, the transition to TeamsOnly cannot be made until the user is moved from Skype for Business on-premises to Skype for Business Online (using Move-CsUser). 
- In particular, you must ensure your users are properly sync’d into Azure AD with the correct Skype for Business attributes. If users are not sync’d properly to Azure AD, the management tools in Teams will not be able to manage these users. 
- When on-premises, Teams users cannot interoperate with Skype for Business users, nor can they federate with external users. This functionality is only available once the users are moved to the cloud (either as Skype for Business Online users in Islands mode, or as TeamsOnly users). 
- When a user is moved from on-premises to the cloud, meetings organized by that user are migrated to either Skype for Business Online or Teams. 

## Peforming a side-by-side migration

You should consider this option if:

- You are able to do a fast migration for your overall organization.  Because there is potential risk of confusion with running both clients, it’s best if you minimize the amount of time users have access to both clients.

-  Users already have Skype for Business Online.  This is the out-of-box model and doesn't require any configuration.  

It can be challenging to move users from Islands mode to TeamsOnly mode.  Because upgraded 
users only communicate via Teams, any other user in the org communicating with that user must be using Teams.  If you have pockets of users that have not started using Teams, they will be exposed to missing messages. Furthermore, they won’t ever see the TeamsOnly users online in Skype for Business. Some orgs choose to do a tenant-wide upgrade using the Tenant global policy to avoid this, however that requires waiting till all users are ready to be upgraded. 

## Performing a phased migration

Performing a phased migration differs depending on whether users have already started using Teams in Islands mode or not.

### For users who haven't started using Teams

The first step is to set the default tenant-wide policy for TeamsUpgradePolicy to one of the Skype for Business modes; for example, SfbWithTeamsCollab.  If users have not yet started using Teams, they won’t notice any difference in behavior. However, setting this policy at the tenant level makes it possible to start upgrading users to TeamsOnly, and ensuring that the upgrade users can still communicate with non-upgrade users.  Once you have identified your pilot users you can upgrade them to TeamsOnly.  If they are on-prem, use move-csUser. If they are online, simply assign them TeamsOnly mode using TeamsUpgradePolicy.  By default, any Skype for meetings scheduled by these users will be migrated to Teams. 

1. Set tenant-wide default to mode = SfbWithTeamsCollab as follows:

```
Grant-CsTeamsUpgradePolicy -PolicyName SfbWithTeamsCollab -Global
```

2. Upgrade a user to TeamsOnly as follows:

   - If already online:

   ```
   Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Identity $username 
   ```

   - If on-premises:

   ```
   Move-CsUser -identity $user -Target sipfed.online.lync.com -MoveToTeams -credential $cred 
   ```

Notes
 
- Instead of setting the tenant-wide policy to SfbWithTeamsCollab, you could set it to SfbWithTeamsCollabAndMeetings. This cause all users to start scheduling meetings in Teams. 
- Move-CsUser is a cmdlet in the on-prem tools. The MoveToTeams switch requires CU8 for Skype for Business Server 2015 or later. If you are using a prior version, you can first move the user to Skype for Business Online, and then grant TeamsOnly mode to that user. 
- By default, Skype for Business meetings are migrated to Teams when upgrading to TeamsOnly.  


INSERT TABLE OR GRAPHIC


### For users that are already using Teams in Islands mode

If some users in your organization are already actively using Teams in Islands mode, you likely do not want to remove any functionality from existing users. Therefore, the previous approach would not be suitable for these users.  The solution here is to “grandfather” these existing active Teams users into Islands mode, before setting the tenant-wide policy to SfbWithTeamsCollab.  Once you’ve done that, you can proceed with deployment as above, however, you’ll have 2 source populations of users who are moving to TeamsOnly:  the users who were active in Teams will be in Islands mode, and the remaining users will be in SfBWIthTeamsCOllab.  You can progressively shift these users over to TeamsOnly mode.

1. Find users who are active in Teams as follows:

   1. From the Office 365 Admin Portal, in the left-hand navigation, go to Reports, and then Usage. 
   2. Click Export and find the users who are active in Teams.

2. For each active Teams user found in step 1, assign them Islands mode. This won’t change their experience, but it allows you to do the next step after this, and ensure you don’t change their experience.  

   ```
   $users=get-content “C:\MyPath\users.txt” 
    foreach ($user in $users){ 
    Grant-CsTeamsUpgradePolicy -identity $user -PolicyName Islands} 
   ```

3. Set the tenant wide policy to SfbWithTeamsCollab:

   ```
   Grant-CsTeamsUpgradePolicy -Global -PolicyName SfbWithTeamsCollab 
   ```

4. Upgrade selected users to TeamsOnly mode. You can choose either users in Islands mode or SfbWIthTeamsCollab, although you might want to start with the users in Islands mode to eliminate this scenario:

   ```
   Grant-CsTeamsUpgradePolicy -identity $user -PolicyName UpgradeToTeams 
   ```

INSERT TABLE OR GRAPHIC HERE
   

## Considerations for PSTN Calling

If PSTN Calling functionality is involved, there are three possible scenarios when moving users to TeamsOnly mode: 

- A user in Skype for Business Online, with an Microsoft Calling Plan. Upon upgrade, this user will continue to have an Microsoft Calling plan. 
- A user in Skype for Business Online, with voice functionality via Skype for Business on-premises or Cloud Connector Edition. Upon upgrade, this user will have PSTN functionality obtained via Direct Routing. 
- A user in Skype for Business on-premises who will be moving to online. Upon upgrade, this user will no longer be homed in Skype for Business on-premises, and will have PSTN functionality obtained via Direct Routing. 

This article provides a high-level overview.  For more information, see   INSERT LINK HERE.

### From Skype for Business Online with Microsoft Calling Plans 

This is the simplest upgrade scenario involving voice. If users already have a Microsoft Calling Plan with a phone number, the only required change is to assign the user TeamsOnly mode in TeamsUpgradePolicy.  Prior to assigning TeamsOnly mode, incoming PSTN calls land in the user’s Skype for Business client. After the upgrade, incoming PSTN calls land in the user’s Teams client.  Note that outbound calls are possible even before the user is upgraded to TeamsOnly mode. 

### From Skype for Business Online with on-premises voice

In this scenario, the user is already in Skype for Business Online, but their PSTN connectivity comes via on-premises, either using a deployment of Skype for Business Server in hybrid mode, or a deployment of Cloud Connector Edition. Migrating these users to TeamsOnly with PSTN functionality means enabling them for Direct Routing, in which PSTN trunks connect directly to the Teams PSTN Edge in the cloud, via your on-premises Session Border Controller (SBC). 

The basic steps are listed below.  Steps 1-4 are listed in the suggested sequence, but they can be done in any order. The key is that all of these should be completed before Step 5. 

1. If you will be setting the tenant-wide policy to one of the Skype for Business modes, be sure to grandfather any existing Islands users by explicitly assigning them Islands mode, as previously described. 

2. Pair your on-premises SBC with the Teams PSTN Edge. See details here. 

3. If desired, configure various Teams policies for these users (e.g. TeamsMessagingPolicy, TeamsMeetingPolicy, etc). This can be done at any time, but if you want to ensure that users have the correct configuration when they are upgraded, it’s best to do this before the user is upgraded to TeamsOnly mode. 

4. Prepare select users for voice migration as follows: 

   - If necessary, assign the Teams license.  Assuming the user is already functional with Skype for Business Online with on-premises voice, the user already has Skype for Business Plan 2 as well as Microsoft Phone System. Leave both those plans enabled, including the Skype for Business Online Plan 2 license.  
   - Create an OnlineVoiceRoutingPolicy if you haven’t done so already. 
   - Assign desired OnlineVoiceRoutingPolicy.

5. Upgrade the user: These steps should be coordinated. 

   - In Office 365, upgrade the user to TeamsOnly mode (Grant-CsTeamsUpgradePolicy).
   - On the SBC, configure voice routing to enable incoming calls by sending calls to Direct Routing instead of to the on-premises Mediation Server.


### From Skype for Business Server on-premises, with Enterprise Voice

In this scenario, the user is still homed in Skype for Business on-premises, and their PSTN connectivity also comes via on-premises. Migrating these users to TeamsOnly mode with PSTN functionality means enabling them for Direct Routing and then moving the user to the cloud. 
 
The basic steps are listed below.  Steps 1-6 are listed in the suggested sequence, but they can be done in any order. The key is that all of these should be completed before Step 7. 

1. If you will be setting the tenant-wide policy to one of the Skype for Business modes, be sure to grandfather any existing Islands users by explicitly assigning them Islands mode, as previously described. 
2. If not already done, configure the organization for Skype for Business hybrid connectivity. 
3. Pair your on-premises SBC with the Teams PSTN Edge. See details here. 
4. If desired, configure various Teams policies for these users (e.g. TeamsMessagingPolicy, TeamsMeetingPolicy, etc). This can be done at any time, but if you want to ensure that users have the correct configuration when they are upgraded, it’s best to do this before the user is upgraded to Teams Only. 
5. Create the OnlineVoiceRouting Policy and re-create in online the voice routes from on-premises voice policy. 
6. Assign the Office 365 licenses if necessary.  The user should have both Teams and Skype for Business Online Plan 2, as well as Phone System. If the Skype for Business Online Plan 2 is disabled, re-enable it.  
7. Upgrade the user: These steps should be coordinated. 
   - Using the on-premises Skype for Business tools, run Move-CsUser with -MoveToTeams switch. 
   - On the SBC, configure voice routing to enable incoming calls by sending calls to Direct Routing instead of to the on-premises Mediation Server. 
   - In Office 365: Assign the relevant OnlineVoiceRoutingPolicy to enable outgoing calls. (MUST THIS BE DONE AFTER USER IS MOVED ONLINE? MUST ADMIN WAIT 4 HOURS?)