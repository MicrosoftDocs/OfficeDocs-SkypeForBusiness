---
title: Manage general meeting policies
ms.author: mabond
author: mkbond007
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: sonua, shalenc
ms.date: 03/15/2021
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.general
  - seo-marvel-apr2020
description: Learn to manage general meeting policy settings in Teams.
---

# Meeting policy settings - General

<a name="bkgeneral"> </a>

This article describes the following general policy settings for Teams meetings:

- [Meet now in channel meetings](#meet-now-in-channel-meetings)
- [Outlook add-in](#outlook-add-in)
- [Channel meeting scheduling](#channel-meeting-scheduling)
- [Private meeting scheduling](#private-meeting-scheduling)
- [Engagement report](#engagement-report)
- [Meeting registration](#meeting-registration)
- [Webinars](#webinars)
- [Meeting provider for Islands mode](#meeting-provider-for-islands-mode)
- [Speaker Coach](#speaker-coach)

## Meet now in channel meetings

This is a per-user policy and applies before a meeting starts. This setting controls whether a user can start an instant meeting in a Teams channel. If you turn on this setting, users can click the **Meet** button to start an unplanned meeting or schedule a meeting in the channel. This setting is on by default.

To find out more about instant channel meetings, read [Manage who can start and schedule meetings](manage-who-can-schedule-meetings.md).

## Outlook add-in

This is a per-user policy and applies before a meeting starts. This setting controls whether Teams meetings can be scheduled from within Outlook (Windows, Mac, web, and mobile).

If you turn this setting off, users are unable to schedule Teams meetings when they create a new meeting in Outlook. For example, in Outlook on Windows, the **New Teams Meeting** option won't show up in the ribbon.

To find out more about the Outlook add-in and private meeting scheduling, read [Manage who can start and schedule meetings](manage-who-can-schedule-meetings.md).

## Channel meeting scheduling

This is a per-user policy and applies before a meeting starts. This setting controls whether users can schedule a meeting in a Teams channel. By default, this setting is turned on.

If this policy is turned off, users won't be able to create new channel meetings. However, existing channel meetings can be edited by the organizer of the event.

To find out more about channel meeting scheduling, read [Manage who can start and schedule meetings](manage-who-can-schedule-meetings.md).

## Private meeting scheduling

This is a per-user policy and applies before a meeting starts. This setting controls whether users can schedule private meetings in Teams. A meeting is private when it's not published to a channel in a team. **Private meeting scheduling** is turned on by default.

To find out more about private meeting scheduling, read [Manage who can start and schedule meetings](manage-who-can-schedule-meetings.md).

## Engagement report

This is a per-user policy. This setting controls whether meeting organizers can download the engagement report for a meeting or webinar.

This policy is on by default and allows your organizers to see who registered and attended the meetings and webinars they set up. To turn it off in the Teams admin center, go to **Meetings** > **Meeting policies**, and set the **Engagement report** setting to **Off**.

When this policy is enabled, the option to download the meeting engagement report is displayed in the **Participants** pane.

For more information on engagement reports, read [Microsoft Teams meeting attendance report](../meeting-attendance-report.md).

## Meeting registration

This is a per-user policy. If you turn this setting on, users in your organization can add registration to a meeting. This policy is enabled by default.

To find out more about meeting registration, read [Configure meeting registration](set-up-webinars.md#configure-meeting-registration).

## Webinars

This is a per-user policy. If you enable webinars, users in your organization can create webinars with robust registration management, customizable event and registration sites, and event-oriented default meeting options. This policy is enabled by default.

Read more about webinars in [Set up webinars](set-up-webinars.md).

For more information about the differences between meetings, webinars, and live events, see [Meetings, webinars, and live events](quick-start-meetings-live-events.md).

## Meeting provider for Islands mode

This is a per-user policy. This setting controls which Outlook meeting add-in is used for *users who are in Islands mode*. You can specify whether users can only use the Teams Meeting add-in or both the Teams Meeting and Skype for Business Meeting add-ins to schedule meetings in Outlook.

You can only apply this policy to users who are in Islands mode and have the **AllowOutlookAddIn** parameter set to **True** in their Teams meeting policy.

Currently, you can only use PowerShell to set this policy. You can edit an existing Teams meeting policy by using the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet. Or, create a new Teams meeting policy by using the [New-CsTeamsMeetingPolicy](/powershell/module/skype/new-csteamsmeetingpolicy) cmdlet and assign it to users.

To specify which meeting add-in you want to be available to users, set the **PreferredMeetingProviderForIslandsMode** parameter as follows:

- Set the parameter to **TeamsAndSfB** to enable both the Teams Meeting add-in and Skype for Business add-in in Outlook. **TeamsAndSfB** is the default value.
- Set the parameter to **Teams** to enable only the Teams Meeting add-in in Outlook. This policy setting ensures that all future meetings have a Teams meeting join link. It doesn't migrate existing Skype for Business meeting join links to Teams. This policy setting doesn't affect presence, chat, PSTN calling, or any other capabilities in Skype for Business, which means that users will continue to use Skype for Business for these capabilities.

  If you set the parameter to **Teams**, and then switch back to **TeamsAndSfB**, both meeting add-ins are enabled. However, note that existing Teams meeting join links won't be migrated to Skype for Business. Only Skype for Business meetings scheduled after the change will have a Skype for Business meeting join link.

## Speaker Coach

This setting lets users turn on Speaker Coach during a Teams meeting. Speaker Coach listens to the audio of the user while they present and provides private real-time feedback and suggestions for improvement. The user also gets a summary report of their feedback after the meeting.

> [!NOTE]
> The user who turned on Speaker Coach during the meeting is the only one who can see the summary report of feedback. Admins won't have access to any of this data.

Currently, you can only set and edit this policy in PowerShell. by using the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet. Or, create a new Teams meeting policy by using the [New-CsTeamsMeetingPolicy](/powershell/module/skype/new-csteamsmeetingpolicy) cmdlet and assign it to users.

This setting is enabled by default. To turn it off, set **AllowMeetingCoach** to **False**.

## Related topics

- [Teams policies reference](settings-policies-reference.md#meetings)
- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies in Teams](policy-assignment-overview.md)
- [Remove the RestrictedAnonymousAccess Teams meeting policy from users](meeting-policies-restricted-anonymous-access.md)
