---
title: Set up Meeting Registration in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: sherimehmood
ms.date: 7/15/2024
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

**APPLIES TO:** ✔️Meetings ✖️Webinars ✖️Town halls

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

> [!NOTE]
> While meetings with registration are no longer supported, you and your users can use webinars. To learn more about setting up webinars for your org, see [Plan for Teams webinars](plan-webinars.md) Meetings with registration that were previously scheduled, or created with Graph API are still supported until December 31st, 2024.

This article describes how you, as an admin, can set up and manage meeting registration for your end users in Microsoft Teams meetings.

A meeting is a collaborative virtual meeting where organizers can require participants to register. During meetings, participants can discuss and share information with each other. These meetings can accommodate up to 20k participants. Meetings can include an attendance report and require registration from attendees. However, meeting registration has limited branding and event page configuration. Webinars, on the other hand, allow organizers to include custom branding, and use extra registration settings, management features, and more. For information on how to set up webinars, see [Set up webinars.](set-up-webinars.md)

Read more about the meeting registration experience for your end users in [Schedule a Teams meeting with registration](https://support.microsoft.com/office/schedule-a-teams-meeting-with-registration-435b2b67-c1bd-411e-9be6-9ed1b4a9f04a)

> [!NOTE]
> Meeting registration isn't available for Microsoft 365 GCC High or Microsoft 365 DoD.

## Prerequisites

Before setting up meeting registration in Teams meetings, check to make sure you have the following items:

- The **Private meeting scheduling** setting must be on for meeting registration to work. To read more on private meeting scheduling, see [Configure private meeting scheduling](manage-who-can-schedule-meetings.md#private-meetings). For students in education tenants, the private meeting scheduling policy is turned off by default. For more information on how to enable private meeting scheduling for students, see [Teams for Education policies and policy packages](policy-packages-edu.md).

## Set up and manage meeting registration

You can use the Teams admin center or PowerShell to create and manage meeting registration.

### Using the Teams admin center

To set up meeting registration for users in your organization, you can use the Teams admin center.

#### Turn meeting registration on or off

Follow these steps in the Teams admin center to turn meeting registration on or off:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Within your chosen policy, navigate to the **Meeting scheduling** section.
6. Turn **Meeting Registration** setting **On** or **Off**.
7. Select **Save**

### Using PowerShell

You can also use PowerShell to set up meeting registration for users in your organization.

To set up meeting registration, use the "**`-AllowMeetingRegistration`**" parameter within the PowerShell **CsTeamsMeetingPolicy** cmdlet.

The following table shows the behaviors of the settings for **`-AllowMeetingRegistration`**:

|Setting value| Behavior|
|---------|---------------|
|True| Users with this policy can require registration for their meetings. |
|False| Users with this policy can't require registration for their meetings.|

Before you can run the following cmdlets, you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

#### Turn on meeting registration in PowerShell

Turn on meeting registration for an existing policy, use the following script:

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingRegistration $True
  ```

#### Turn off meeting registration in PowerShell

Turn off meeting registration, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingRegistration $False 
```

## Who can register for meetings

**Who can register** is set to **Everyone** by default, but in education tenants, the default setting is **People in my organization**. Once you turn on meeting registration, you can use the Teams admin center or PowerShell to manage the types of users organizers can require to register for meetings.

You could use the following steps to manage who can register in the Teams admin center:

1. Navigate to the Teams admin center and go to **Meetings** > **Meeting Policies**
2. Either select an existing policy or create a new one
3. Within your chosen policy, navigate to the **Meeting scheduling** section
4. Select your desired behavior under the **"Who can register"** dropdown from the options of **Everyone** or **People in my organization**
5. Select **Save**.

Or, you could use the following PowerShell scripts to manage who can register for meetings:

- To allow only users in your organization to register for meetings:

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <policy name> -WhoCanRegister EveryoneInCompany
  ```

- Allow everyone, including anonymous users, to register for meetings:

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <policy name> -WhoCanRegister Everyone
  ```

> [!IMPORTANT]
> If **Anonymous users can join a meeting** is turned off, anonymous users can't join meetings. To learn more and enable this setting, see [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md).

For more information, on **Who can register** for education tenants, see [Teams for Education Policy Wizard](easy-policy-setup-edu.md).

## Related topics

[Teams policies reference - Meetings](settings-policies-reference.md#meetings)

[Meetings, webinars, and live events](quick-start-meetings-live-events.md)

[Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)

[Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)

[Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)

[Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)

[New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy)

[Grant-CsTeamsMeetingPolicy](/powershell/module/teams/grant-csteamsmeetingpolicy)

[Get-CsTeamsMeetingPolicy](/powershell/module/teams/get-csteamsmeetingpolicy)

[Remove-CsTeamsMeetingPolicy](/powershell/module/teams/remove-csteamsmeetingpolicy)
