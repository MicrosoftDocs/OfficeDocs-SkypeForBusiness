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

# Set up a meeting with registration in Microsoft Teams meetings

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

## Overview

This article describes how to set up and manage a meeting with registration for Microsoft Teams meetings.

A meeting with registration is a virtual meeting where organizers can require registration from participants. This meeting format includes basic webinar functionality, the ability to require registration for meetings, and an attendance report.

For more information about the differences between meetings, webinars, and live events, see [Meetings, webinars, and live events](quick-start-meetings-live-events.md).

Previously, the parameters for webinars and meetings with registration were grouped together, so for the webinar experience, you had to enable **both**:

- Meeting with registration using the Teams meeting policy parameter **`-AllowMeetingRegistration`**,
- Webinars using the Teams events policy parameter **`-AllowWebinars`**

Now, **we’ve separated meeting registration and webinars.**

If you want your users to **only** use **meeting registration** and not the new webinar experience, make sure `-AllowWebinars` is disabled and “`-AllowMeetingRegistration`” is enabled.

If you want your users to still have a **webinar** entry point to create webinars, you need to verify that the **`-AllowWebinars`** parameter is still enabled.
If you currently have webinars turned off, they'll remain off as the new experience rolls out. For information on how to set up webinars, see [Set up webinars.](set-up-webinars.md)

Read more about the new features available for your end users in [Get started with Teams webinars](https://support.microsoft.com/office/42f3f874-22dc-4289-b53f-bbc1a69013e3).

> [!NOTE]
> For on-premises users, the new webinar experience isn't available yet.
>
> The new webinar experience isn't available for Microsoft 365 GCC, Microsoft 365 GCC High, or Microsoft 365 DoD. The existing webinar experience isn't available for Microsoft 365 GCC High or Microsoft 365 DoD.

## Prerequisites

Before setting up meeting with registration in Teams meetings, check to make sure you have the following items:

- The **Private meeting scheduling** setting must be on for meeting with registration to work. To read more on private meeting scheduling, see [Configure private meeting scheduling](manage-who-can-schedule-meetings.md#private-meetings). For students in education tenants, the private meeting scheduling policy is turned off by default. For more information on how to enable private meeting scheduling for students, see [Teams for Education policies and policy packages](policy-packages-edu.md).
- If you'd like to manage who can register for meetings, you must first [turn on meeting registration.](#set-up-and-manage-meeting-registration)

## Who can register for meetings

The Teams admin center setting **"Who can register"** and PowerShell parameter **`-WhoCanRegister`** control which users can register for meetings. This setting's two options are only available if **Meeting registration** is turned **on**. If **Meeting registration** is turned **off**, no one can register for meetings.

The following table shows the behaviors of the settings for **"Who can register"** in the admin center and PowerShell:

|Setting value| Behavior|
|---------|---------------|
|Everyone| **This is the default setting.** All users, including anonymous users, can register for meetings.|
|**"People in my organization"** in the admin center or **"EveryoneInCompany"** in PowerShell| No one can register for meetings. **For ***education tenants*** only, this is the default setting.**|

For more information, on **Who can register** for education tenants, see [Teams for Education Policy Wizard](easy-policy-setup-edu.md).

To control who can register for meetings, see the sections for [Manage who can register in the admin center](#manage-who-can-register-in-the-admin-center) and [Manage who can register for meetings in PowerShell.](#manage-who-can-register-for-meetings-in-powershell)

## Set up and manage meeting registration

You can use the [Teams admin center](#using-the-teams-admin-center) or [PowerShell](#using-powershell) to create and manage meeting registration.

### Using the Teams admin center

To set up meeting registration for users in your organization, you can use the Teams admin center.

#### Set up meeting registration in the admin center

Follow these steps in the Teams admin center to turn on meeting registration:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Within your chosen policy, navigate to the **Meeting scheduling** section.
6. Toggle the **"Meeting Registration"** setting from **Off** to **On** to turn on meeting registration.
7. Select **Save** to enable meeting registration.

#### Manage who can register in the admin center

Follow these steps in the Teams admin center to manage who can register for meetings:

1. Navigate to the Teams admin center and go to **Meetings** > **Meeting Policies**
2. Either select an existing policy or create a new one
3. Within your chosen policy, navigate to the **Meeting scheduling** section
4. Choose your desired behavior under the **"Who can register"** dropdown from the options of **Everyone** or **People in my organization**
5. Select **Save**.

### Using PowerShell

You can also use PowerShell to set up meeting registration for users in your organization.

To set up meeting registration, use the "**`-AllowMeetingRegistration`**" parameter within the Windows PowerShell **CsTeamsMeetingPolicy** cmdlet.

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

Turn on meeting registration for an existing policy.

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingRegistration $True
  ```

#### Manage who can register for meetings in PowerShell

- Allow ***only*** users in your organization to register for meetings

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <policy name> -WhoCanRegister EveryoneInCompany
  ```

- Allow ***everyone, including anonymous users***, to register for webinars and meetings

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <policy name> -WhoCanRegister Everyone
  ```

> [!IMPORTANT]
> If **Anonymous users can join a meeting** is turned off in **Meeting settings**, anonymous users can't join webinars. To learn more and enable this setting, see [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md).

## Turn off meeting registration

You can turn off meeting registration using PowerShell or the Teams admin center.

You could use the following steps to turn off meeting registration in the **Teams admin center**:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one
5. Within your chosen policy, navigate to the **Meeting scheduling** section.
6. Toggle the **"Meeting Registration"** setting from **On** to **Off** to turn off meeting registration.
7. Select **Save** to disable meeting registration.

Or, you can use the following **PowerShell script** to turn off meeting registration:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingRegistration $False 
```

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
