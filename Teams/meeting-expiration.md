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

The meeting policy settings that control whether users can start and schedule meetings also control expiration of existing meetings scheduled by users. When a meeting is expired, no one can join the meeting. The following meeting policy settings determine whether users can start and schedule meetings in Teams:

- [Allow Meet now in channels](meeting-policies-in-teams.md#allow-meet-now-in-channels)
- [Allow channel meeting scheduling](meeting-policies-in-teams.md#allow-channel-meeting-scheduling)
- [Allow scheduling private meetings](meeting-policies-in-teams.md#allow-scheduling-private-meetings)
- [Allow Meet now in private meetings](meeting-policies-in-teams.md#allow-meet-now-in-private-meetings)

When any of these settings is turned off, any user who is assigned the policy can't start or schedule a meeting of that type. At the same time, all existing meetings of that type that the user previously scheduled are expired.

<!-- As an admin, you can use meeting policies to control the expiration of meetings scheduled by users in your organization *who are no longer* allowed to start or schedule meetings. -->

## What happens when a meeting expires?

When a meeting is expired, no one can join the meeting, either through the meeting join link or by phone. Conversations, files, whiteboards, and other content related to the meeting are retained and users can still access them.

##
 
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

- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies to your users in Teams](assign-policies.md)
