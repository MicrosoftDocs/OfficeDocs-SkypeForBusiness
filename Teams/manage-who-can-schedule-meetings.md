---
title: Manage who can start instant meetings and schedule meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: brgussin
ms.date: 03/06/2023
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - Tier1
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
description: Learn how to use Teams meeting policy settings to control who can start instant meetings and schedule meetings.
---

# Manage who can start instant meetings and schedule meetings

**APPLIES TO:** ✔️Meetings ✖️Webinars ✖️Town halls

As an admin, you can control which users can start instant meetings and schedule meetings in Teams. Managing who can schedule meetings can be especially useful for privacy and compliance reasons, where you might not want particular users setting up meetings.

The meeting scheduling policy settings are turned on by default. These settings are per-user policies and they apply before a meeting starts. These settings can be found in the **Meeting scheduling** section of meeting policies in the Teams admin center.

- **Private meeting scheduling**: Controls whether a user can schedule a private meeting in Teams.
- **Meet now in private meetings**: Controls whether a user can start an instant private meeting.
- **Channel meeting scheduling**: Controls whether a user can schedule a meeting in a channel.
- **Meet now in channel meetings**: Controls whether a user can start an instant meeting in a channel.
- **Outlook add in**: Controls whether a user can schedule a private meeting from Outlook.

You can also use [Microsoft PowerShell](teams-powershell-overview.md) with the [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet to update these meeting policy settings.

> [!NOTE]
> If the meeting was sent by a delegate, who was given permissions to send meeting invitations on behalf of another person, such as a manager, the meeting policy setting is applied to the person who granted permission (the manager).

## Channel meetings

If you need to restrict the ability to start instant channel meetings and schedule channel meetings to specific people, you can create or update your meeting policy to restrict these settings. You can then create a separate policy attributed to users who you want to start instant channel meetings and schedule channel meetings.

### Configure channel meetings in the Teams admin center

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, select **Add**.
1. Under **Meeting scheduling**, toggle the following:
    - If you want to restrict who can start instant meetings in a channel, toggle **Meet now in channel meetings** to **Off**. This setting is on by default.
    - If you want to restrict who can schedule meetings in a channel, toggle **Channel meeting scheduling** to **Off**. If this setting is turned off, users can't create new channel meetings. However, the event organizer can edit existing channel meetings. This setting is on by default.
1. Hit **Save** at the bottom of the page.

### Configure channel meetings using PowerShell

To restrict who can start and schedule channel meetings, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetNow $False
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowChannelMeetingScheduling $False
```
Set these settings to `$True` for policies where you want to allow users to start channel meetings.

## Private meetings

A meeting is private when it's not published to a channel in a team. If you restrict the ability to start instant private meetings and schedule private meetings to specific people, then you can create or update your meeting policies to restrict these settings. You can then create a separate policy attributed to users who you want to start instant meetings and schedule private meetings.

### Configure private meetings in the Teams admin center

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, select **Add**.
1. Under **Meeting scheduling**, toggle the following:
    - If you want to restrict who can start instant private meetings, toggle **Meet now in private meetings** to **Off**. This setting is on by default.
    - If you want to restrict who can schedule private meetings in a channel, toggle both **Private meeting scheduling** and **Outlook add-in** to **Off**. These settings are on by default.
1. Hit **Save** at the bottom of the page.

### Configure private meetings using PowerShell

To restrict who can start and schedule private meetings, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowPrivateMeetNow $False
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowPrivateMeetingScheduling $False
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowOutlookAddIn $False
```

## Turning off meeting policy settings

After any of these meeting policy settings are turned off, any user assigned to the policy won't be able to start or schedule meetings of that type. The meeting join links and conference IDs of all existing meetings of that type that the user previously started or scheduled won't work. (The conversations, files, whiteboards, recordings, transcripts, and other content related to the meeting are retained and users can still access them.)

If a meeting policy setting is turned off and then turned on again for a user, all previously scheduled meetings organized by the user become active and people can join them using the meeting join link or by phone.

## Outlook add-in

This setting controls whether Teams meetings can be scheduled from within Outlook (Windows, Mac, web, and mobile).

If you turn off this setting, users are unable to schedule Teams meetings when they create a new meeting in Outlook. For example, in Outlook on Windows, the **New Teams Meeting** option don't show up in the ribbon.

## Related topics

- [Manage meeting policies in Teams](meeting-policies-overview.md)
- [Teams policy reference - Meetings](settings-policies-reference.md#meetings)
- [Use the Teams Meeting add-in in Outlook](outlook-add-in-authentication-policy-requirements.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Meetings, webinars, and live events](quick-start-meetings-live-events.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
