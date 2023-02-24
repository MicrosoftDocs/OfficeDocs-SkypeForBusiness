---
title: Manage who can start instant meetings and schedule meetings
author: mkbond007
ms.author: mabond
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: brgussin
ms.date: 02/24/2023
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - tier1
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
description: Learn how to use Teams meeting policy settings to control who can start instant meetings and schedule meetings.
---

# Manage who can start instant meetings and schedule meetings

As an admin, you can restrict which users can start instant meetings and schedule meetings in Teams. This can be especially useful for privacy and security reasons, where you may not want particular users setting up meetings.

The meeting policy settings are turned on by default. These settings can be found in the Teams admin center under **Meetings** > **Meeting scheduling**.

- **Private meeting scheduling**: Controls whether a user can schedule a private meeting in Teams. A meeting is private when it's not published to a channel in a team.
- **Meet now in channel meetings**: Controls whether a user can start an instant meeting in a channel.
- **Channel meeting scheduling**: Controls whether a user can schedule a meeting in a channel.
- **Meet now in channel meetings**: Controls whether a user can start an instant private meeting.
- **Outlook add in**: Controls whether a user can schedule a private meeting from Outlook. A meeting is private when it's not published to a channel in a team.
- **Meeting registration**: Controls whether a user can register the meeting.
- **Who can register**: Choose **Everyone** from the dropdown list.
- **Engagement report**: Choose **On for everyone** from the dropdown list.

You can also use [Microsoft PowerShell](teams-powershell-overview.md) with the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet to create, update, and remove these meeting policy settings.

> [!NOTE]
> If the meeting was sent by a delegate, who was given permissions to send meeting invitations on behalf of another person, such as a manager, the meeting policy setting is applied to the person who granted permission (the manager).

## Channel meetings

If you have compliance requirements that mandate only specific people start instant channel meetings and schedule channel meetings, then you can create or update your meeting policy to restrict these settings. You can then create a separate policy attributed to users who you want to start instant channel meetings and schedule channel meetings.

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, click **Add**.
1. Under **Meeting scheduling**, toggle the following:
    1. If you want to restrict who can start instant meetings in a channel, toggle **Meet now in channel meetings** to **Off**. This setting is on by default.
    1. If you want to restrict who can schedule meetings in a channel, toggle **Channel meeting scheduling** to **Off**. This setting is on by default.
1. Hit **Save** at the bottom of the page.

## Private meetings

If you have compliance requirements that mandate only specific people start instant private meetings and schedule private meetings, then you can create or update your meeting policies to restrict these settings. You can then create a separate policy attributed to users who you want to start instant meetings and schedule private meetings.

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, click **Add**.
1. Under **Meeting scheduling**, toggle the following:
    1. If you want to restrict who can start instant private meetings, toggle **Meet now in private meetings** to **Off**. This setting is on by default.
    1. If you want to restrict who can schedule private meetings in a channel, toggle both **Private meeting scheduling** and **Outlook add-in** to **Off**. These settings are on by default.
1. Hit **Save** at the bottom of the page.

## Turning off meeting policy settings

After any of these meeting policy settings are turned off, any user assigned to the policy will not be able to start or schedule meetings of that type. The meeting join links and conference IDs of all existing meetings of that type that the user had previously started or scheduled will not work. (The conversations, files, whiteboards, recordings, transcripts, and other content related to the meeting are retained and users can still access them.)

If a meeting policy setting is turned off and then turned on again for a user, all previously scheduled meetings organized by the user become active and people can join them using the meeting join link or by phone.

To restrict who can start and schedule both private and channel meetings, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetNow $False
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowChannelMeetingScheduling $False
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowPrivateMeetNow $False
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowPrivateMeetingScheduling $False
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowOutlookAddIn $False
```

## Related topics

- [Manage meeting policies in Teams](meeting-policies-overview.md)
- [Teams policy reference - Meetings](settings-policies-reference.md#meetings)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Meetings, webinars, and live events](quick-start-meetings-live-events.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
