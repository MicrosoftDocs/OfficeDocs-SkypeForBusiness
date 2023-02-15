---
title: Manage general meeting policies
ms.author: mabond
author: mkbond007
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: sonua, shalenc
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
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
- [Attendance report](#attendance-report)
- [Meeting registration](#meeting-registration)
- [Webinars](#webinars)
- [Meeting provider for Islands mode](#meeting-provider-for-islands-mode)
- [Reactions](#reactions)
- [Speaker Coach](#speaker-coach)

## Meet now in channel meetings 

This is a per-user policy and applies before a meeting starts. This setting controls whether a user can start an unplanned meeting in a Teams channel. If you turn on this setting, users can click the **Meet** button to start an unplanned meeting or schedule a meeting in the channel. This setting is on by default.

[![Screenshot showing the Meet now icon below a message.](media/meeting-policies-meet-now.png)](media/meeting-policies-meet-now.png#lightbox)

## Outlook add-in

This is a per-user policy and applies before a meeting starts. This setting controls whether Teams meetings can be scheduled from within Outlook (Windows, Mac, web, and mobile).

![Screenshot showing the ability to schedule a new meeting.](media/meeting-policies-outlook-add-in.png)

If you turn this setting off, users are unable to schedule Teams meetings when they create a new meeting in Outlook. For example, in Outlook on Windows, the **New Teams Meeting** option won't show up in the ribbon.

## Channel meeting scheduling

Use the existing AllowChannelMeetingScheduling policy to control the types of events that can be created on the team channel calendars. This is a per-user policy and applies before a meeting starts. This setting controls whether users can schedule a meeting in a Teams channel. By default, this setting is turned on.

If this policy is turned off, users won't be able to create new channel meetings. However, existing channel meetings can be edited by the organizer of the event.

Schedule a meeting will be disabled.

![Screenshot showing the Schedule a meeting option in Teams.](media/schedule-meeting-option.png)

Channel selection is disabled.

[![Screenshot showing the calendar option for selecting a channel that you want to schedule a meeting in.](media/meeting-policies-select-a-channel-to-meet-in.png)](media/meeting-policies-select-a-channel-to-meet-in.png#lightbox)

In the channel posts page, the following functionalities will be disabled:

- **Schedule a meeting** button on the channel reply compose box.
  ![Screenshot showing the calendar option for selecting a channel in which you want to schedule a meeting.](media/schedule-meeting-disabled-in-chat2.png)
  
- **Schedule a meeting** button on the channel header.
  ![Screenshot showing the calendar option for selecting a channel through which you want to schedule a meeting.](media/schedule-now-in-header.png)

In the channel calendar:

- **Add new event** button on channel calendar header will be disabled.
  ![Screenshot showing the calendar option for selecting a channel that will enable you to schedule a meeting.](media/add-new-event-disabled.png)

- Users won't be able to drag and select a time block on the channel calendar to create a channel meeting.

- Users can't use Keyboard shortcuts to create a meeting on the channel calendar.

In the admin center:

The channel calendar app will show up in the **Microsoft apps** section on the app permission policies page.

![Screenshot showing the app permissions policy in the Teams admin center.](media/manage-microsoft-apps-policy.png)

## Private meeting scheduling

This is a per-user policy and applies before a meeting starts. This setting controls whether users can schedule private meetings in Teams. A meeting is private when it's not published to a channel in a team. **Private meeting scheduling** is turned on by default.

If you turn off both the **Private meeting scheduling** and **Channel meeting scheduling** settings, the **Add required attendees** and **Add channel** options are disabled for users in Teams.

## Attendance report

This is a per-user policy. Attendance reports are enabled by default with **Everyone, unless organizers opt-out**. These reports allow your meeting organizers to see who registered and attended the meetings and webinars they've set up, giving them the option to download the report from the **Participants** pane of a meeting or webinar.

To find out more about attendance reports and the corresponding **Who's in the report** and **Attendance information collection** policy settings, read [Microsoft Teams meeting attendance report](\teams-analytics-and-reports\meeting-attendance-report.md).

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

## Reactions

The availability of reactions can be configured through either the Teams admin center interface or using PowerShell. Reactions are enabled by default.

In the Teams admin center, reactions can be enabled or disabled under the **Meetings** > **Meeting policies** under the **Meeting engagement** section of a meeting policy.

To configure the setting in PowerShell, use the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet. To turn it off, set **AllowMeetingReactions** to **False**.

Turning off reactions for a user doesn't mean a user can't use reactions in meetings they schedule. The meeting organizer can still turn on reactions from the meeting option page, regardless of the default setting.

## Speaker Coach

This setting lets users turn on Speaker Coach during a Teams meeting. Speaker Coach listens to the audio of the user while they present and provides private real-time feedback and suggestions for improvement. The user also gets a summary report of their feedback after the meeting.

> [!NOTE]
> The user who turned on Speaker Coach during the meeting is the only one who can see the summary report of feedback. Admins won't have access to any of this data.

Currently, you can only set and edit this policy in PowerShell. by using the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet. Or, create a new Teams meeting policy by using the [New-CsTeamsMeetingPolicy](/powershell/module/skype/new-csteamsmeetingpolicy) cmdlet and assign it to users.

This setting is enabled by default. To turn it off, set **AllowMeetingCoach** to **False**.

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies in Teams](policy-assignment-overview.md)
- [Remove the RestrictedAnonymousAccess Teams meeting policy from users](meeting-policies-restricted-anonymous-access.md)
