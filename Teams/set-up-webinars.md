---
title: Set up webinars
ms.author: mabond
author: mkbond007
manager: serdars
ms.reviewer: sachung, emryan
ms.date: 04/08/2021
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
description: Learn how to manage webinar and meeting registration policies in Teams.
---

# Set up webinars in Microsoft Teams

> [!NOTE]
> This article describes some features in webinars that are in preview and will require a Teams Premium license.

Microsoft now offers a new webinar experience; this article describes how to update your settings to use these features.

We recommend that you use the new webinar experience if you plan to use webinars.

Meeting registration includes basic webinar functionality, the ability to require registration for meetings, and an attendance report. By enabling the new webinar experience, you have the ability to use meeting registration and many new webinar features, such as:

- Dedicated event and registration page for your webinar
- Co-organizers
- Presenter bios on the event page
- Registration status overview and management

Read more about the new features available for your end users in [Get started with Teams webinars](https://support.microsoft.com/office/42f3f874-22dc-4289-b53f-bbc1a69013e3).

If your organization has meeting registration enabled, all newly created webinars will have the new experience. Previously scheduled webinars will use the previous webinar experience. The new experience uses the TeamsEventsPolicy. If you have webinars turned off, they will remain off as the new experience rolls out.

Currently, the basic webinar experience is controlled by meeting registration using the Teams Meeting policy (Set-CsTeamsMeetingPolicy). In the future, the meeting registration setting won't control webinars; webinars are transitioning over to being controlled by the Teams Events policy (Set-CsTeamsEventsPolicy).

The new webinar experience is configured in PowerShell. See examples on [how to set up the new webinar experience](#set-up-new-webinar-experience).

For more information about the differences between meetings, webinars, and live events, see [Meetings, webinars, and live events](quick-start-meetings-live-events.md).

> [!NOTE]
> For on-premises users, the new webinar experience isn't available yet.
>
> The new webinar experience isn't available for Microsoft 365 GCC, Microsoft 365 GCC High, or Microsoft 365 DoD. The existing webinar experience isn't available for Microsoft 365 GCC High or Microsoft 365 DoD.

## Set up new webinar experience

You must use PowerShell to set up the new webinar experience for your organization. The ability to configure the new webinar experience in the Teams admin center isn't available yet.

Meeting registration must be on to use the new webinar experience.

### Configure the new webinar experience with PowerShell

To set up the new webinar experience, use the following attributes within the Windows PowerShell **Set-CsTeamsEventsPolicy** cmdlet.

|Parameter|Default Setting|Description|
|---------|-----------|---------------|
|AllowWebinars|Enabled|This setting determines if a user can create webinars.|
|EventAccessType|Everyone|This setting determines which users can access the event registration page or the event site to register, as well as which user type is allowed to join the session(s) in the event.|

Before you can run these cmdlets you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

1. Turn on meeting registration.

    ```powershell
    Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingRegistration $True
    ```

1. Activate the new webinar experience.

    ```powershell
    Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinars Enabled
    ```

1. Configure who can register for webinars and meetings.

    - **Allow ***only*** users in your organization to register for webinars and meetings**

        ```powershell
        Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType EveryoneInCompanyExcludingGuests
        ```

    - **Allow everyone, including anonymous users, to register for webinars and meetings**

        ```powershell
        Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType Everyone
        ```

> [!IMPORTANT]
> If **Anonymous users can join a meeting** is turned off in **Meeting settings**, anonymous users can't join webinars. To learn more and enable this setting, see [Meeting settings in Teams](meeting-settings-in-teams.md).

## Configure meeting registration

If you want to use webinars, meeting registration must be turned on.

You can use the Teams admin center under **Meetings** > **Meeting policies** to set up meeting registration and webinars.

### Meeting registration

If you turn on **Meeting registration**, users in your organization can schedule webinars and meetings requiring registration. By default, this setting is turned on. If you want to turn off meeting registration and webinars, set this policy to **Off**.

**Private meeting scheduling** must be on for meeting registration to work. Find out more about [private meeting scheduling](meeting-policies-in-teams-general.md).

For students in education tenants, this policy is turned off by default. For more information on how to enable private meeting scheduling for students, see [Teams for Education policies and policy packages](policy-packages-edu.md).

#### Who can register

> [!NOTE]
> This policy does not apply to the new webinar experience. To configure who can register for the new webinar experience, use `Set-CsTeamsEventsPolicy -EventAccessType`, as shown in [configure the new webinar experience with PowerShell](#configure-the-new-webinar-experience-with-powershell).

This policy controls which users can register and attend webinars with meeting registration only. This policy has two options, which are only available if **Meeting registration** is turned on. By default, **Who can register** is set to **Everyone**.

If you select **Everyone**, all users, including anonymous users, can register for and attend webinars. If you select **Everyone in my organization**, only users in your organization can register for and attend webinars. If meeting registration is turned off, the **Who can register** setting won't be available and no one can register for webinars.

The default value for **Who can register** is **Everyone in my organization** in education tenants. For more information, see [Teams for Education Policy Wizard](easy-policy-setup-edu.md).

## Collect webinar and meeting registration attendance

The attendance report policy setting controls whether meeting organizers can see reports of who registered and attended the webinars or meetings they set up. The default setting is **Everyone, unless organizers opt-out**. You can use the Teams admin center under **Meetings** > **Meeting policies** to turn on or off **Attendance report**; with PowerShell, use the [Set-CsTeamsMeetingPolicy cmdlet](/powershell/module/skype/set-csteamsmeetingpolicy) and `-AllowEngagementReport`.

If **Who's in the report** is set to **Everyone, but users can opt-out**, **No one, but users can opt-in**, or **Everyone**, users will be able to toggle on or off **Identify me in attendance reports** within their Teams settings.

If **Attendance information collection** is set to **All information**, then the webinar or meeting attendees' join times, leave times, and "in-meeting duration" will show up in the attendance report.

To find out more about attendance reports and their associated settings, read [Microsoft Teams meeting attendance report](\teams-analytics-and-reports\meeting-attendance-report.md). For information on the end-user experience, see [View and download meeting attendance reports](https://support.microsoft.com/office/ae7cf170-530c-47d3-84c1-3aedac74d310).

## Turn off webinars

You can turn off webinars using PowerShell. This will turn off the new webinar experience as well as webinars with meeting registration only.

Use the following PowerShell script to turn off webinars:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingRegistration $False
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinars Disabled
```

## Related topics

- [Meeting policies in Teams - General](meeting-policies-in-teams-general.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
