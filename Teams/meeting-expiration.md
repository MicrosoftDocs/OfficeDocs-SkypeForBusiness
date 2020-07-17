---
title: Meeting policies and meeting expiration in Microsoft Teams
author: LanaChin
ms.author: v-lanac
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
description: Learn to manage meeting policy settings in Teams and use them to control the features available to meeting participants for meetings scheduled by users.
---
# Meeting policies and meeting expiration in Microsoft Teams

## Overview

[Meeting policies](meeting-policies-in-teams.md) in Microsoft Teams are used to control whether users in your organization can start and schedule meetings and the features that are available to meeting participants for meetings that are scheduled by users. You can use the global (Org-wide default) policy or create and assign custom policies. You manage meeting policies in the Microsoft Teams admin center or by using [PowerShell](teams-powershell-overview.md).

The meeting policy settings that control whether users can start and schedule meetings also control expiration of meetings scheduled by users. When a meeting is expired, no one can join the meeting. These meeting policy settings which determine whether users can start and schedule meetings in Teams, and we'll be referring to them throughout this article.

- [Allow Meet now in channels](meeting-policies-in-teams.md#allow-meet-now-in-channels): Controls whether a user can start an impromptu meeting in a channel.
- [Allow channel meeting scheduling](meeting-policies-in-teams.md#allow-channel-meeting-scheduling): Controls whether a user can schedule a meeting in a channel.
- [Allow scheduling private meetings](meeting-policies-in-teams.md#allow-scheduling-private-meetings): Controls whether a user can schedule a private meeting. A meeting is private when it's not published to a channel in a team.
- [Allow Meet now in private meetings](meeting-policies-in-teams.md#allow-meet-now-in-private-meetings): Controls whether a user can start an impromptu private meeting.

By default, these settings are on. When any of these settings are turned off, any user who is assigned the policy can't start or schedule new meetings of that type. At the same time, all existing meetings of that type that the user previously scheduled are expired.

For example, if a user is assigned a meeting policy in which these meeting policy settings are set to **On**, and then you turn off the **Allow Meet now in channels** setting, that user can no longer start impromptu meetings in channels, and all Meet now meetings that the user previously created are expired. The user can still start and schedule other meeting types.

<!-- As an admin, you can use meeting policies to control the expiration of meetings scheduled by users in your organization *who are no longer* allowed to start or schedule meetings. -->

## What happens when a meeting expires?

When a meeting is expired, no one can join the meeting, either through the meeting join link or by phone. When a user tries to join the meeting through the meeting join link or by dialing in, [WHAT HAPPENS???]. Conversations, files, whiteboards, and other content related to the meeting are retained and users can still access them.

## What happens when you turn on and turn off meeting policy settings?

### Switch a meeting policy setting from on to off

When a meeting policy setting is set to **On**, users who are assigned the policy can start or schedule meetings of that type and everyone can join. When you switch the meeting policy setting to **Off**, users who are assigned the policy can't start or schedule new meetings of that type, and existing meetings that the user previously scheduled are expired.

### Switch a meeting policy setting from off to on

When you switch a meeting policy setting from **Off** to **On**, users who are assigned the policy can start or schedule meetings of that type. If a meeting policy setting is turned off and then turned on again for a user, all previously scheduled (and expired) meetings organized by the user become active and people can join them using the meeting join URL [or by phone???].  

## Meeting expiration scenarios

|If you want to... |Do this  |More information  |
|---------|---------|---------|
|Expire Meet now channel meetings started by a user  |Turn off **Allow Meet now in channels**|No one can join Meet now channel meetings started by the user that occurred in the past.         |
|Expire scheduled channel meetings for a user   |Turn off **Allow channel meeting scheduling**         |No one can join channel meetings scheduled by the user. This prevents people from joining the following:<ul><li>Scheduled channel meetings that occurred in the past.</li> <li>Channel meetings that are scheduled for the future.</li><li>Future instances of recurring channel meetings scheduled by the user.</li></ul>       |
|Row3     |         |         |
|Row4     |         |         |
|Row5     |         |         |
|Row6     |         |         |
|Row7     |         |         |
|Row8     |         |         |
|Row9     |         |         |
|Row10     |         |         |


### Channel meetings

### Private meetings
 
### Allow Meet now in channels

This is a per-user policy and applies before a meeting starts. This setting controls whether a user can start an ad hoc meeting in a Teams channel. If you turn this on, when a user posts a message in a Teams channel, the user can click **Meet now** under the compose box to start an ad hoc meeting in the channel. The default value is True.

### Allow channel meeting scheduling

This is a per-user policy and applies before a meeting starts. This setting controls whether users can schedule a meeting in a Teams channel.  If you turn this off, the **Schedule a meeting** option won't be available to the user when they start a meeting in a Teams channel and the **Add channel** option is disabled for users in Teams. The default value is True.


### Allow scheduling private meetings

This is a per-user policy and applies before a meeting starts. This setting controls whether users can schedule private meetings in Teams. A meeting is private when it's not published to a channel in a team.

Note that if you turn off **Allow scheduling private meetings** and **Allow channel meeting scheduling**,  the **Add required attendees** and **Add channel** options are disabled for users in Teams. The default value is True.

### Allow Meet now in private meetings

This is a per-user policy and applies before a meeting starts. This setting controls whether a user can start an ad hoc private meeting.  The default value is True.

## Related topics

[Manage meeting policies in Teams](meeting-policies-in-teams.md)

[Assign policies to your users in Teams](assign-policies.md)