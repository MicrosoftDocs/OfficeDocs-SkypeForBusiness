---
title: Manage who can start instant meetings and schedule meetings
author: mkbond007
ms.author: mabond
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: nej, brgussin
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
description: Learn how to use Teams meeting policy settings to control who can start instant meetings and schedule meetings.
---

# Manage who can start instant meetings and schedule meetings

As an admin, you can restrict which users can start instant meetings and schedule meetings in Teams. This can be especially useful for privacy and security reasons, where you may not want particular users setting up meetings.

The meeting policy settings are turned on by default. These settings can be found in the Teams admin center under **Meetings** > **Meeting policies**.

- **Channel meeting scheduling**: Controls whether a user can schedule a meeting in a channel. This is a per-user policy and applies before a meeting starts. If this policy is turned off, users won't be able to create new channel meetings. However, existing channel meetings can be edited by the organizer of the event. This setting is on by default.
- **Meet now in channels**: Controls whether a user can start an instant meeting in a channel. This is a per-user policy and applies before a meeting starts. If you turn on this setting, users can click the **Meet** button to start an instant meeting in the channel. This setting is on by default.
- **Private meeting scheduling**: Controls whether a user can schedule a private meeting in Teams. A meeting is private when it's not published to a channel in a team. This is a per-user policy and applies before a meeting starts. This setting is on by default.
- **Meet now in private meetings**: Controls whether a user can start an instant private meeting. This is a per-user policy and applies before a meeting starts. This setting is on by default.
- **Outlook add in**: Controls whether a user can schedule a private meeting from Outlook. A meeting is private when it's not published to a channel in a team. This is a per-user policy and applies before a meeting starts. If you turn this setting off, users will be unable to schedule Teams meetings when they create a new meeting in Outlook.

> [!NOTE]
> If the meeting was sent by a delegate, who was given permissions to send meeting invitations on behalf of another person, such as a manager, the meeting policy setting is applied to the person who granted permission (the manager).

## Channel meetings

If you have compliance requirements that mandate only specific people start instant channel meetings and schedule channel meetings, then you can create or update your meeting policy to restrict these settings. You can then create a separate policy attributed to users who you want to start instant channel meetings and schedule channel meetings.

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, click **Add**.
1. Under **General**, toggle the following:
    1. If you want to restrict who can start instant meetings in a channel, toggle **Meet now in channels** to **Off**.
    1. If you want to restrict who can schedule meetings in a channel, toggle **Channel meeting scheduling** to **Off**.
1. Hit **Save** at the bottom of the page.

## Private meetings

If you have compliance requirements that mandate only specific people start instant private meetings and schedule private meetings, then you can create or update your meeting policies to restrict these settings. You can then create a separate policy attributed to users who you want to start instant meetings and schedule private meetings.

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, click **Add**.
1. Under **General**, toggle the following:
    1. If you want to restrict who can start instant private meetings, toggle **Meet now in private meetings** to **Off**.
    1. If you want to restrict who can schedule private meetings in a channel, toggle both **Private meeting scheduling** and **Outlook add-in** to **Off**.
1. Hit **Save** at the bottom of the page.

## Turning off meeting policy settings

After any of these meeting policy settings are turned off, any user assigned to the policy won't be able to start or schedule meetings of that type. The meeting join links and conference IDs of all existing meetings of that type that the user had previously started or scheduled won't work. (The conversations, files, whiteboards, recordings, transcripts, and other content related to the meeting are retained and users can still access them.)

If you turn off both the **Private meeting scheduling** and **Channel meeting scheduling** settings, the **Add required attendees** and **Add channel** options won't be enabled for users in Teams.

With **Channel meeting scheduling** turned off, the **Schedule a meeting** buttons will not be enabled for users on the channel reply compose box or in the channel header within the channel posts page. In the channel calendar, the **Add new event** button on the calendar header won't be enabled and users won't be able to drag and select a time block on the channel calendar to create a channel meeting.

If a meeting policy setting is turned off and then turned on again for a user, all previously scheduled meetings organized by the user will become active and people will be able to join them using the meeting join link or by phone.

## Related topics

[Manage meeting policies in Teams](meeting-policies-overview.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)

[Teams Meeting Policies in PowerShell](powershell/module/skype/set-csteamsmeetingpolicy)

[Meeting policy settings - Participants & guests](meeting-policies-participants-and-guests.md)

[Security and compliance in Microsoft Teams](security-compliance-overview.md)
