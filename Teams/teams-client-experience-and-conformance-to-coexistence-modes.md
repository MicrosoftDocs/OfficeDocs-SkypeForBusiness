---
title: Teams client experience and conformance to coexistence modes
author: dearbeen
ms.author: bjwhalen
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: bjwhalen
description: Teams client experience and comformance to coexistence modes
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
MS.collection: Teams_ITAdmin_JourneyFromSfB
appliesto:
- Microsoft Teams
---

<a name="about-upgrade-basic"></a>

# Teams client experience and conformance to coexistence modes

> [!NOTE]
> This page describes important upcoming changes in the behavior of Teams client, when users are in any of the Skype for Business modes (SfBOnly, SfBWithTeamsCollab, SfBWithTeamsCollabAndMeetings).


The purpose of co-existence modes is to provide a simple, predictable experience for end users as organizations transition from Skype for Business to Teams.  For an organization moving to Teams, the TeamsOnly mode is the final destination for each user, though not all users need to be assigned TeamsOnly (or any mode) at the same time.  Prior to users reaching TeamsOnly mode, organizations can use any of the Skype for Business modes (SfBOnly, SfBWithTeamsCollab, SfBWithTeamsCollabAndMeetings) to ensure predictable communication between users who are TeamsOnly and those who aren’t yet. 

When a user is in any of the Skype for Business modes, all incoming chats and calls are routed to the user’s Skype for Business client. To avoid end user confusion and ensure proper routing, the calling and chat functionality in the Teams client is intended to be disabled when a user is in any of the Skype for Business modes. Similarly, meeting scheduling in Teams is intended to be explicitly disabled when users are in the SfBOnly or SfBWithTeamsCollab modes, and explicitly enabled when a user is in the SfBWithTeamsCollabAndMeetings mode.  The functionality to automatically disable chat and calling functionality, as well as enable/disable meeting scheduling based on mode is now starting to rollout to TAP customers.  

Prior to this functionality, Microsoft’s guidance was to ensure the proper user experience by setting the corresponding settings in Messaging, Calling and Meeting policies. However, there was no formal enforcement of this, and since users by default had full access to all functionality in the Teams client,  some users may have retained access to some or all of these  experiences in the Teams client, regardless of their mode.  As a result, as this functionality rolls out, some users may see a change in their experience in the Teams client as the user experience begins to conform to their mode.  The table below shows the new behavior:


|User's effective mode|Experience in Teams client|
|---|---|
|Any Skype for Business mode|Calling and Chat<sup>1</sup> are disabled.|
|SfBWithTeamsCollabAndMeetings|Meeting scheduling is available|
|SfBWithTeamsCollab or SfBOnly<sup>2</sup>|Meeting scheduling is not available|
|||

**Notes:**
<sup>1</sup> Meeting chat is still available.
<sup>2</sup> For now, SfBwithTeamsCollab and SfBOnly behave the same, but these will eventually be differentiated.


**How organizations can prepare for automatic UX conformance to modes**
Prior to this change rolling out, organizations can achieve the desired experience in the Teams client using additional policies as described in this section. This ensures the rollout is seamless for end users. Note that once the change rolls out, setting these policies will NOT be required.  Alternatively, organizations that do not wish for users to have reduced functionality in the Teams client can shift their users to Islands mode or TeamsOnly mode, however that will impact routing as well.

To manually configure the end user experience, administrators use the following policies and settings:


|**Modality (App)**|**Policy.Setting**|
|---|---|
|Chat|TeamsMessagingPolicy.AllowUserChat|
|Calling|TeamsCallingPolicy.AllowPrivateCalling|
|Meeting scheduling|TeamsMeetingPolicy.AllowPrivateMeetingScheduling</br>TeamsMeetingPolicy.AllowChannelMeetingScheduling|
|||


Administrators should set each of these settings to the following values for a given mode:

|Mode|AllowUserChat|AllowPrivateCalling|AllowPrivateMeetingScheduling|AllowChannelMeetingScheduling|
|---|---|---|---|---|
|TeamsOnly or Islands|Enabled|Enabled|Enabled|Enabled|
|SfBWithTeamsCollabAndMeetings|Disabled|Disabled|Enabled|Enabled|
|SfBWithTeamsCollab or SfBOnly|Disabled|Disabled|Disabled|Disabled|
||||||

Note that once automatic conformance of the user experience based on mode is available, it is not necessary to set these policies. The value of TeamsUpgradePolicy mode will take precedence over the values of these specific settings. Automatic conformance is achieved based on how the policy infrastructure resolves the effective policy setting for users. In case of conflict, the behavior based on mode will win over the values of AllowUserChat, AllowPrivateCalling, AllowPrivateMeetingScheduling and AllowChannelMeetingScheduling.

