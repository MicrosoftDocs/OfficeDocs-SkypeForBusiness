---
title: Meeting policies and meeting expiration in Microsoft Teams
author: cichur
ms.author: v-cichur
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: nej
audience: admin
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
description: Learn how to use meeting policy settings to control meeting expiration in Microsoft Teams.
---

# Meeting policies and meeting expiration in Microsoft Teams

[Meeting policies](meeting-policies-in-teams.md) in Microsoft Teams are used to control whether users in your organization can start and schedule meetings and the features that are available to meeting participants for meetings that are scheduled by users. You can use the global (Org-wide default) policy or create and assign custom policies. You manage meeting policies in the Microsoft Teams admin center or by using [Get](/powershell/module/skype/get-csteamsmeetingpolicy), [New](/powershell/module/skype/new-csteamsmeetingpolicy), [Set](/powershell/module/skype/set-csteamsmeetingpolicy), [Remove](/powershell/module/skype/remove-csteamsmeetingpolicy), [Grant](/powershell/module/skype/grant-csteamsmeetingpolicy) -CsTeamsMeetingPolicy PowerShell cmdlets.

The meeting policy settings that control whether users can start and schedule meetings and also control expiration of meetings scheduled by users. When a meeting join link and conference ID for a meeting expires, no one can join the meeting. The following meeting policy settings determine whether users can start and schedule meetings in Teams. We discuss the meeting settings in this article.

- [Allow Meet now in channels](meeting-policies-in-teams-general.md#allow-meet-now-in-channels): Controls whether a user can start an impromptu meeting in a channel.
- [Allow channel meeting scheduling](meeting-policies-in-teams-general.md#allow-channel-meeting-scheduling): Controls whether a user can schedule a meeting in a channel.
- [Allow scheduling private meetings](meeting-policies-in-teams-general.md#allow-scheduling-private-meetings): Controls whether a user can schedule a private meeting in Teams. A meeting is private when it's not published to a channel in a team.
- [Allow the Outlook add in](meeting-policies-in-teams-general.md#allow-the-outlook-add-in): Controls whether a user can schedule a private meeting from Outlook. A meeting is private when it's not published to a channel in a team.
- [Allow Meet now in private meetings](meeting-policies-in-teams-general.md#allow-meet-now-in-private-meetings): Controls whether a user can start an impromptu private meeting.

By default, these settings are on. When any of these settings are turned off, any user who is assigned the policy can't start or schedule new meetings of that type. At the same time, the meeting join links and conference IDs of all existing meetings of that type that the user previously started or scheduled expire.

For example, if a user is assigned a meeting policy in which these meeting policy settings are set to **On**, and then you turn off the **Allow Meet now in channels** setting, that user can no longer start impromptu meetings in channels, and the channel Meet now join links that the user previously created are expired. The user can still start and schedule other meeting types and join meetings organized by other people.

## What happens when the meeting join link and conference ID expire?

When the meeting join link and conference ID for a meeting expires, no one can join the meeting. When a user tries to join the meeting through the link or by phone, they'll get a message that says the meeting is no longer available. Conversations, files, whiteboards, recordings, transcripts, and other content related to the meeting are retained and users can still access them.

## What happens when you turn on and turn off a meeting policy setting?

### Switch a meeting policy setting from on to off

When a meeting policy setting is set to **On**, users who are assigned the policy can start or schedule meetings of that type and everyone can join. When you switch the meeting policy setting to **Off**, users who are assigned the policy can't start or schedule new meetings of that type, and the meeting join links and conference IDs of existing meetings that the user previously scheduled are expired.

Keep in mind that the user can still join meetings organized by other people.

### Switch a meeting policy setting from off to on

When you switch a meeting policy setting from **Off** to **On**, users who are assigned the policy can start or schedule meetings of that type. If a meeting policy setting is turned off and then turned on again for a user, all previously scheduled (and expired) meetings organized by the user become active and people can join them using the meeting join link or by phone.  

## Meeting expiration scenarios

Here's a summary of how meeting expiration works for each of the meeting policy settings discussed in this article.

|If you want to...&nbsp;&nbsp; |Do this&nbsp;&nbsp;&nbsp;&nbsp;  |Meeting join behavior&nbsp;&nbsp;&nbsp;&nbsp;  |
|---------------------------|---------------------|---------|
|Expire private Meet now meetings started by a user&nbsp;&nbsp;|Turn off **Allow Meet now in private meetings**.&nbsp;&nbsp;|No one can join private **Meet now** meetings started by the user.|
|Expire private meetings scheduled by a user&nbsp;&nbsp;|Turn off **Allow scheduling private meetings** _and_ turn off **Allow the Outlook add-in**. &nbsp;&nbsp;|No one can join private meetings scheduled by the user. This prevents people from joining the following meetings:<ul><li>Private meetings that occurred in the past.</li><li>Private meetings that are scheduled for the future and have not yet occurred.</li><li>Future instances of recurring private meetings.</li></ul><br>Both **Allow scheduling private meetings** and **Allow the Outlook add-in** must be off to expire private meetings scheduled by a user. If one setting is off and the other is on, meeting join links and conference IDs of existing meetings remain active and won't be expired.|
|Expire channel **Meet now** meetings started by a user&nbsp;&nbsp;|Turn off **Allow Meet now in channels** _and_ turn off **Allow channel meeting scheduling**.&nbsp;&nbsp;|No one can join channel **Meet now** meetings started by the user.|
|Expire channel meetings scheduled by a user&nbsp;&nbsp;|Turn off **Allow channel meeting scheduling**.&nbsp;&nbsp;|No one can join channel meetings scheduled by the user. This prevents people from joining the following meetings:<ul><li>Channel meetings that occurred in the past.</li><li>Channel meetings that are scheduled for the future and haven't yet occurred.</li><li>Future instances of recurring channel meetings.</li></ul>|

If you want people to access meetings that were previously scheduled or started by a particular user, you can:

- Turn on the meeting policy setting for that user.
- Turn off the meeting policy setting for that user and have another user who has the policy setting enabled create a new meeting to replace the expired meeting.

> [!NOTE]
> If the meeting was sent by a delegate, who was given permissions to send meeting invitations on behalf of another person, such as a manager, the meeting policy setting is applied to the person who granted permission (the manager).

## Related topics

[Manage meeting policies in Teams](meeting-policies-in-teams.md)

[Assign policies to your users in Teams](assign-policies.md)

[Teams PowerShell overview](teams-powershell-overview.md)
