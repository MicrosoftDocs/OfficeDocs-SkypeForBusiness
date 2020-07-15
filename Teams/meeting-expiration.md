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

Meeting policies are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization. You can use the global (Org-wide default) policy that's automatically created or create and assign custom policies. You manage meeting policies in the Microsoft Teams admin center or by using [PowerShell](teams-powershell-overview.md). To learn more, see [Manage meeting policies in Teams](meeting-policies-in-teams.md).

As an admin, you may want more granular control of 

## Meeting policy settings - General

- [Allow Meet now in channels](#allow-meet-now-in-channels)
- [Allow channel meeting scheduling](#allow-channel-meeting-scheduling)
- [Allow scheduling private meetings](#allow-scheduling-private-meetings)
- [Allow Meet now in private meetings](#allow-meet-now-in-private-meetings)

### Allow Meet now in channels

This is a per-user policy and applies before a meeting starts. This setting controls whether a user can start an ad hoc meeting in a Teams channel. If you turn this on, when a user posts a message in a Teams channel, the user can click **Meet now** under the compose box to start an ad hoc meeting in the channel. The default value is True.

![Screenshot showing the Meet now icon below a message](media/meeting-policies-meet-now.png)

### Allow channel meeting scheduling

This is a per-user policy and applies before a meeting starts. This setting controls whether users can schedule a meeting in a Teams channel.  If you turn this off, the **Schedule a meeting** option won't be available to the user when they start a meeting in a Teams channel and the **Add channel** option is disabled for users in Teams. The default value is True.

![Screenshot showing the Schedule a meeting option in Teams](media/meeting-policies-schedule-a-meeting.png)

![Screenshot showing the Select a channel to meet in option](media/meeting-policies-select-a-channel-to-meet-in.png)

### Allow scheduling private meetings

This is a per-user policy and applies before a meeting starts. This setting controls whether users can schedule private meetings in Teams. A meeting is private when it's not published to a channel in a team.

Note that if you turn off **Allow scheduling private meetings** and **Allow channel meeting scheduling**,  the **Add required attendees** and **Add channel** options are disabled for users in Teams. The default value is True.

### Allow Meet now in private meetings

This is a per-user policy and applies before a meeting starts. This setting controls whether a user can start an ad hoc private meeting.  The default value is True.

<a name="bkaudioandvideo"> </a>

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies to your users in Teams](assign-policies.md)
