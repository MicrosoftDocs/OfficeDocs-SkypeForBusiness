---
title: Set up webinars
ms.author: wlibebe
author: wlibebe
manager: serdars
ms.reviewer: justle, ritikag
ms.date: 02/21/2023
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
description: Learn how to set up and manage webinar policies in Teams.
---

# Set up webinars in Microsoft Teams

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

## Overview

Microsoft Teams now offers a new webinar experience; this article describes how to update your settings to use and manage these features.

Previously, to use webinars, you had to enable **both**:

- Meeting registration using the Teams meeting policy parameter **`-AllowMeetingRegistration`**,
- Webinars using the Teams events policy parameter **`-AllowWebinars`**.

Now, we’ve separated meeting registration and webinars.

If you want your users to still have a **webinar** entry point to create webinars, you’ll **only** need to verify that the **`-AllowWebinars`** parameter is still enabled.
If you currently have webinars turned off, they will remain off as the new experience rolls out.

If you want your users to **only** use **meeting with registration** and not the new webinar experience, make sure `-AllowWebinars` is disabled and “`-AllowMeetingRegistration`” is enabled. To learn more about the meeting with registration experience, see [Set up meeting registration.](set-up-meeting-registration.md)

Webinars are created and managed in PowerShell. For examples on how to set up webinars, see the section [How to set up the new webinar experience.](#set-up-webinars)

> [!NOTE]
> For on-premises users, the new webinar experience isn't available yet.
>
> The new webinar experience isn't available for Microsoft 365 GCC, Microsoft 365 GCC High, or Microsoft 365 DoD. The existing webinar experience isn't available for Microsoft 365 GCC High or Microsoft 365 DoD.

## What’s the difference between a webinar and meeting registration?

Webinars and meetings are both virtual events that allow participants to connect remotely. However, there are some key differences in terms of their purpose, format, and registration process.
A meeting is a collaborative virtual event where participants can discuss and share information with each other. This collaborative format allows up to 20k participants.
Meeting registration includes basic webinar functionality, an attendance report, and the ability to require registration for meetings.

A webinar is a two-way interactive virtual event where the presenters deliver information to attendees. This format provides additional control for an organizer over the conversation and participants. Common scenarios for webinars might include trainings, product demos, sales lead generation, customer events, company announcements, and showcasing products. Webinars have the capacity for up to 1,000 people to attend and allows for collection of pre-event attendee registration data.

In terms of registration, webinar attendees typically are required to register in advance to reserve their spot. With meetings, attendees can join the meeting without any pre-reservation, but for instances where an organizer wants registration, this is where you'd enable meeting registration.

The entry points your end users will use to set up a webinar vs meeting registration are in separate places.
**THINKING OF ADDING SCREENSHOTS HERE TO SHOW ENTRY POINTS**

To learn more about the end user experience, see [Get Started with Teams webinars](/office/manage-webinar-registration) and [Schedule a Teams meeting with registration.](/office/schedule-a-teams-meeting-with-registration)

For more information about the differences between meetings, webinars, and live events, see [Meetings, webinars, and live events](quick-start-meetings-live-events.md).

## Basic vs advanced webinars

We offer basic and advanced webinars. Basic webinars are included in your subscription, but advanced webinars are part of the Teams Premium subscription.
**PLACEHOLDER FOR BASIC VS ADVANCED MATRIX**

## Set up webinars

You must use PowerShell to set up the new webinar experience for your organization. The ability to configure the new webinar experience in the Teams admin center isn't available yet.

To set up the new webinar experience, use the **`-AllowWebinars`** parameter within the Windows PowerShell **CsTeamsEventsPolicy** cmdlet.

The table below shows the behaviors of the settings for the **`-AllowWebinars`** parameter:

|Setting value| Behavior|
|---------|---------------|
|Enabled| The webinar entry point is available for your users to create webinars. |
|Disabled| There is no webinar entry point for your users to create webinars.|

Before you can run these cmdlets, you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

### Create and manage webinars using PowerShell

You can manage the new events policy using the following PowersShell cmdlets:

- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)

1. Create a new webinar experience:

    ```powershell
    New-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinars Enabled
    ```

1. Manage who can register for webinars:

    - **Allow ***only*** users in your organization to register for webinars:**

        ```powershell
        Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType EveryoneInCompanyExcludingGuests
        ```

    - **Allow everyone, including anonymous users, to register for webinars:**

        ```powershell
        Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType Everyone
        ```

> [!IMPORTANT]
> If **Anonymous users can join a meeting** is turned off in **Meeting settings**, anonymous users can't join webinars. To learn more and enable this setting, see [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md).

## Turn off webinars

You can turn off webinars using PowerShell.

Use the following PowerShell script to turn off webinars:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinars Disabled
```

## Collect webinar attendance information

The attendance report policy setting controls whether organizers can see reports of who registered and attended the webinars they've set up. The default setting is **Everyone, unless organizers opt-out**. You can use the Teams admin center under **Meetings** > **Meeting policies** to turn on or off **Attendance report**; with PowerShell, use the [Set-CsTeamsMeetingPolicy cmdlet](/powershell/module/skype/set-csteamsmeetingpolicy) and `-AllowEngagementReport`.

If **Who is in the report** is set to **Everyone, but users can opt-out** or **No one, but users can opt-in**, users will be able to toggle on or off **Identify me in attendance reports** within their Teams settings.

To find out more about attendance reports and their associated settings, read [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report). For information on the end-user experience, see [View and download meeting attendance reports](https://support.microsoft.com/office/ae7cf170-530c-47d3-84c1-3aedac74d310).

## Related topics

- [Teams policies reference - Meetings](settings-policies-reference.md#meetings)
- [Meetings, webinars, and live events](quick-start-meetings-live-events.md)
- [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)
- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)
