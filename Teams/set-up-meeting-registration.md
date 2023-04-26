---
title: Set up Meeting Registration in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: serdars
ms.reviewer: justle, ritikag
ms.date: 03/29/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
description: Learn how to set up and manage meeting registration policies in Teams.
---

# Manage registration for Microsoft Teams meetings

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

This article describes how you, as an admin, can set up and manage meeting registration for your end users in Microsoft Teams meetings.

A meeting is a collaborative virtual meeting where organizers can require participants to register. During meetings, participants can discuss and share information with each other. These meetings can accommodate up to 20k participants. Meetings can include an attendance report and require registration from attendees. However, meeting registration has limited branding and event page configuration. Webinars, on the other hand, allow organizers to include custom branding, as well as use additional registration settings, management features, and more. For information on how to set up webinars, see [Set up webinars.](set-up-webinars.md)

For instructions on how to set up and manage attendance reports using the Teams admin center or PowerShell, see [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)

If you'd like to learn  about the differences between meetings, webinars, and live events, see [Meetings, webinars, and live events](quick-start-meetings-live-events.md).

Read more about the meeting registration experience for your end users in [Schedule a Teams meeting with registration.](/office/schedule-a-teams-meeting-with-registration)

> [!NOTE]
> Meeting registration isn't available for Microsoft 365 GCC High or Microsoft 365 DoD.

## Prerequisites

Before setting up meeting registration in Teams meetings, check to make sure you have the following items:

- The **Private meeting scheduling** setting must be on for meeting registration to work. To read more on private meeting scheduling, see [Configure private meeting scheduling](manage-who-can-schedule-meetings.md#private-meetings). For students in education tenants, the private meeting scheduling policy is turned off by default. For more information on how to enable private meeting scheduling for students, see [Teams for Education policies and policy packages](policy-packages-edu.md).
- If you'd like to manage who can register for meetings, you must first [turn on meeting registration.](#set-up-and-manage-meeting-registration)

## Set up and manage meeting registration

You can use the [Teams admin center](#using-the-teams-admin-center) or [PowerShell](#using-powershell) to create and manage meeting registration.

### Using the Teams admin center

To set up meeting registration for users in your organization, you can use the Teams admin center.

#### Turn on meeting registration

Follow these steps in the Teams admin center to turn on meeting registration:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Within your chosen policy, navigate to the **Meeting scheduling** section.
6. Toggle the **"Meeting Registration"** setting from **Off** to **On** to turn on meeting registration.
7. Select **Save** to enable meeting registration.

#### Turn off meeting registration

Follow these steps in the Teams admin center to turn on meeting registration:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Within your chosen policy, navigate to the **Meeting scheduling** section.
6. Toggle the **"Meeting Registration"** setting from **On** to **Off** to turn on meeting registration.
7. Select **Save** to enable meeting registration.

### Using PowerShell

You can also use PowerShell to set up meeting registration for users in your organization.

To set up meeting registration, use the "**`-AllowMeetingRegistration`**" parameter within the PowerShell **CsTeamsMeetingPolicy** cmdlet.

The following table shows the behaviors of the settings for **`-AllowMeetingRegistration`**:

|Setting value| Behavior|
|---------|---------------|
|True| The "require registration" entry point **is available** for your users to create meeting registration. |
|False| There's **no** "require registration" entry point for your users to meeting registration.|

You can manage meeting registration using the following PowerShell cmdlets:

- [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy)
- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
- [Grant-CsTeamsMeetingPolicy](/powershell/module/teams/grant-csteamsmeetingpolicy)
- [Get-CsTeamsMeetingPolicy](/powershell/module/teams/get-csteamsmeetingpolicy)
- [Remove-CsTeamsMeetingPolicy](/powershell/module/teams/remove-csteamsmeetingpolicy)

Before you can run these cmdlets, you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

#### Turn on meeting registration in PowerShell

Turn on meeting registration for an existing policy:

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingRegistration $True
  ```

#### Turn off meeting registration in PowerShell

Turn off meeting registration:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingRegistration $False 
```

## Who can register for meetings

**Who can register** is set to **on** by default, but in education tenants, the default setting is "People in my organization". You can manage who can register for meetings through the Teams admin center or PowerShell.

You could use the following steps to manage who can register for meetings in the Teams admin center:

1. Navigate to the Teams admin center and go to **Meetings** > **Meeting Policies**
2. Either select an existing policy or create a new one
3. Within your chosen policy, navigate to the **Meeting scheduling** section
4. Select your desired behavior under the **"Who can register"** dropdown from the options of **Everyone** or **People in my organization**
5. Select **Save**.

Or, you could use the following PowerShell scripts to manage who can register for meetings:

- Allow ***only*** users in your organization to register for meetings:

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <policy name> -WhoCanRegister EveryoneInCompany
  ```

- Allow ***everyone, including anonymous users***, to register for webinars and meetings:

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <policy name> -WhoCanRegister Everyone
  ```

> [!IMPORTANT]
> If **Anonymous users can join a meeting** is turned off in **Meeting settings**, anonymous users can't join meetings with registration. To learn more and enable this setting, see [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md).

For more information, on **Who can register** for education tenants, see [Teams for Education Policy Wizard](easy-policy-setup-edu.md).

## Collect meeting registration attendance information

### Attendance report for Teams meetings

The attendance report for Teams meetings shows meeting organizers who attended a meeting, what time each person joined and left, and more. The attendance report setting controls whether organizers can view or download the attendance report for the meetings they've set up.

In the Teams admin center, the attendance report setting is called "**Attendance report**" and in PowerShell, its parameter is called "**`-AllowEngagementReport`**."

The following table shows the behavior of the settings for "**`-AllowEngagementReport`**" and "**Attendance report**":

|Setting value| Behavior|
|---------|---------------|
|Everyone, unless organizers opt out| **This is the default setting.** Meeting organizers control whether attendance reports are on or off for a meeting. |
|No one| Meeting organizers can't view or download attendance reports for a meeting they've organized.|
|Everyone| Meeting organizers can't turn off attendance reports for meetings they create. The attendance report is available for them.|

For instructions on how to set up and manage attendance reports using the Teams admin center or PowerShell, see [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)

For more information on `-AllowEngagementReport`, see [Set-CsTeamsMeetingPolicy.](/powershell/module/teams/set-csteamsmeetingpolicy)

### Who is in the attendance report for Teams meetings

The **"Who is in the attendance report"** setting controls whether participants in the meeting can opt in or out of offering their attendance information to be included in the organizer's attendance report. You manage this setting in the Teams admin center.

The following table shows the behavior of the settings for "**Who is in the attendance report**":

|Setting value| Behavior|
|---------|---------------|
|Everyone, but participants can opt out| **This is the default setting.** The attendance report initially includes all participants, but participants can opt out. Participants can toggle **Identify me in attendance reports** on or off within their Teams settings. |
|No one, but participants can opt in| The attendance report initially excludes all participants, but participants can opt in. Participants can toggle **Identify me in attendance reports** on or off within their Teams settings.|
|Everyone| The attendance report includes all participants, and participants can't opt out.|
|No one| The attendance report excludes all participants, and participants can't opt in.|

For instructions on how to manage who is in the attendance report, see [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)

For information on the end-user experience for attendance reports and who is in the reports, see [View and download meeting attendance reports](https://support.microsoft.com/office/ae7cf170-530c-47d3-84c1-3aedac74d310).

## Related topics

- [Teams policies reference - Meetings](settings-policies-reference.md#meetings)
- [Meetings, webinars, and live events](quick-start-meetings-live-events.md)
- [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
