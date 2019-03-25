---
title: Teams client experience and conformance to coexistence modes
author: dearbeen
ms.author: bjwhalen
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: bjwhalen
description: Teams client experience and comformance to coexistence modes
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
MS.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

<a name="about-upgrade-basic"></a>

# Teams client experience and conformance to coexistence modes

> [!NOTE]
> This page describes important upcoming changes in the behavior of Teams client when users are in any of the Skype for Business modes (SfBOnly, SfBWithTeamsCollab, SfBWithTeamsCollabAndMeetings).


The purpose of co-existence modes is to provide a simple, predictable experience for end users as organizations transition from Skype for Business to Teams.  For an organization moving to Teams, the TeamsOnly mode is the final destination for each user, though not all users need to be assigned TeamsOnly (or any other mode) at the same time.  Prior to users reaching TeamsOnly mode, organizations can use any of the Skype for Business modes (SfBOnly, SfBWithTeamsCollab, SfBWithTeamsCollabAndMeetings) to ensure predictable communication between users who are TeamsOnly and those who aren’t yet. 

When a user is in any of the Skype for Business modes, all incoming chats and calls are routed to the user’s Skype for Business client. To avoid end user confusion and ensure proper routing, calling and chat functionality in the Teams client is intended to be disabled when a user is in any of the Skype for Business modes. Similarly, meeting scheduling in Teams is intended to be explicitly disabled when users are in the SfBOnly or SfBWithTeamsCollab modes, and explicitly enabled when a user is in the SfBWithTeamsCollabAndMeetings mode.  The functionality to automatically disable chat and calling functionality, as well as enable/disable meeting scheduling based on mode is now starting to rollout to TAP customers.  

Prior to this functionality, Microsoft’s guidance was to ensure the proper user experience by setting the corresponding settings in Messaging, Calling and Meeting policies. However, there was no formal enforcement of this, and since users by default had full access to all functionality in the Teams client, some users may have retained access to some or all of these  experiences in the Teams client, regardless of their mode.  As a result, as this functionality rolls out, some users may see a change in their experience in the Teams client as the user experience begins to conform to their mode.  The table below shows the new behavior:


|User's effective mode|Experience in Teams client|
|---|---|
|Any Skype for Business mode|Calling and Chat<sup>1</sup> are disabled.|
|SfBWithTeamsCollabAndMeetings|Meeting scheduling is available|
|SfBWithTeamsCollab or SfBOnly<sup>2</sup>|Meeting scheduling is not available|
|||

**Notes:**
<sup>1</sup> Meeting chat is still available.

<sup>2</sup> For now, SfBwithTeamsCollab and SfBOnly behave the same, but the intent is for SfBOnly mode to also disable Channels and Files functionality in Teams; however, there is currently no setting that allows this functionality in Teams to be disabled.


## How organizations can prepare for automatic UX conformance to modes

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

Prior to the rollout of automatic conformance of the user experience based on modes, the `Grant-CsTeamsUpgradePolicy` cmdlet checks the configuration of the corresponding settings in TeamsMessagingPolicy, TeamsCallingPolicy, and TeamsMeetingPolicy to determine if these settings are compatible with the specified mode. If any are not configured properly, the grant will succeed but a warning will be provided in PowerShell indicating which specific settings are not configured properly. Below is an example of what the PowerShell warning could look like:

`Grant-CsTeamsUpgradePolicy -Identity user1@contoso.com -PolicyName SfBWithTeamsCollab`

`WARNING: The user 'user1@contoso.com' currently has effective policy enabled values for: AllowUserChat, AllowPrivateCalling, AllowPrivateMeetingScheduling, AllowChannelMeetingScheduling. In the near term, when granting TeamsUpgradePolicy with mode=SfBWithTeamsCollab to a user, you must also separately assign policy to ensure the user has effective policy disabled values for: AllowUserChat, AllowPrivateCalling, AllowPrivateMeetingScheduling, AllowChannelMeetingScheduling. In the future, the capability will automatically honor TeamsUpgradePolicy.`

Upon seeing such a warning, the administrator should subsequently update the indicated policies to deliver a compatible end user experience in Teams. If the administrator decides to take no action as a result of the warning, users may still have access to chat, calling, and/or meeting scheduling capabilities in Teams depending on the values of TeamsMessagingPolicy, TeamsCallingPolicy, and TeamsMeetingPolicy, which may result in a confusing end user experience.

Once automatic conformance of the Teams client experience based on TeamsUpgradePolicy mode is available, it will no longer be necessary to set these policies. The value of TeamsUpgradePolicy mode will take precedence over the values of these specific settings. Automatic conformance is achieved during policy resolution by the policy infrastructure. In case of conflict of the different settings, the behavior based on mode will win over the values of AllowUserChat, AllowPrivateCalling, AllowPrivateMeetingScheduling and AllowChannelMeetingScheduling. Once automatic conformance is delivered, the PowerShell warnings will be updated to inform the administrator that the client experience will automatically apply, despite any values of TeamsMessagingPolicy, TeamsCallingPolicy, and TeamsMeetingPolicy.







