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

Microsoft Teams offers webinars, a two-way interactive virtual event. This article describes how you, as an admin, can configure your settings to use and manage webinar functionality.

In addition to the base webinar features, we offer additional webinar functionality through the Teams Premium subscription. To learn more about advanced webinars, see [Microsoft Teams Premium licensing.](/MicrosoftTeams/teams-add-on-licensing/licensing-enhance-teams#webinars)

Previously, to use webinars, you had to enable **both**:

- Meeting registration using the Teams meeting policy parameter **`-AllowMeetingRegistration`**,
- Webinars using the Teams events policy parameter **`-AllowWebinars`**.

Now, we’ve separated the parameters for meeting registration and webinars, which allows you to configure each feature independently. As a result, your users can use webinars and meetings with registration individually.

If you want your users to still have a **webinar** entry point to create webinars, you need to verify that the **`-AllowWebinars`** parameter is still enabled.

If you want your users to **only** use **meeting with registration** and not the webinar experience, make sure `-AllowWebinars` is disabled and “`-AllowMeetingRegistration`” is enabled.
> [!NOTE]
> If `-AllowWebinars` is disabled, your end users will have no webinar entry point available to them, and they can't create webinars.

To learn more about the meeting with registration experience, see [Set up meeting registration.](set-up-meeting-registration.md)

> [!NOTE]
> The webinar experience isn't available for Microsoft 365 GCC High or Microsoft 365 DoD.

## What’s the difference between a webinar and meeting registration?

Webinars and meetings are both virtual events that allow participants to connect remotely. However, there are differences in their ability to run structured events.

A webinar is a two-way interactive virtual event where the presenters deliver information to attendees. This format provides extra control for an organizer over the conversation and participants. Common scenarios for webinars might include trainings, product demos, sales lead generation, customer events, company announcements, and showcasing products. Webinars have the capacity for up to 1,000 people to attend and allows for collection of pre-event attendee registration data.

Webinar attendees are required to register in advance to reserve their spot. With meetings, attendees can join the meeting without any prior reservation, but for instances where an organizer wants registration, you'd enable meeting registration.

A meeting is a collaborative virtual event where participants can discuss and share information with each other. This collaborative format allows up to 20k participants.
Meeting with registration includes basic webinar functionality, an attendance report, and the ability to require registration for meetings. However, meeting has limited branding and event page configuration. Webinars, on the other hand, will allow organizers to include custom branding, and use additional registration settings, management features, and more.

The entry points your end users use to set up a webinar vs meeting registration are in separate places.
**NEED TO ADD SCREENSHOTS HERE TO SHOW ENTRY POINTS**

To learn more about the end user experience, see [Get Started with Teams webinars](/office/manage-webinar-registration) and [Schedule a Teams meeting with registration.](/office/schedule-a-teams-meeting-with-registration)

For more information about the differences between meetings, webinars, and live events, see [Meetings, webinars, and live events](quick-start-meetings-live-events.md).

## Set up webinars

You must use PowerShell to set up and manage the webinar experience for your organization. The ability to configure webinars in the Teams admin center isn't available yet.

To set up webinars, use the **`-AllowWebinars`** parameter within the Windows PowerShell **CsTeamsEventsPolicy** cmdlet.

The following table shows the behaviors of the settings for the **`-AllowWebinars`** parameter:

|Setting value| Behavior|
|---------|---------------|
|Enabled| The webinar entry point is available for your users to create webinars. |
|Disabled| There's no webinar entry point for your users to create webinars.|

Before you can run these cmdlets, you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

### Create and manage webinars using PowerShell

You can manage the events policy using the following PowerShell cmdlets:

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

## Email communications for webinars

Admins can now decide if event organizers and co-organizers can use email templates for webinars. With email templates, organizers and co-organizers can manage waitlists, remind attendees about webinars they've registered for, and provide clear instructions to attendees before, during, and after the event.

For more information on the email communications experience for your end users, see [**PLACEHOLDER FOR END USER EMAIL COMMUNICATIONS DOC**].

### Manage emails communications for webinars with PowerShell

Through PowerShell, you can manage whether organizers and co-organizers can edit the following email templates:

- Registration Confirmation
- Webinar update
- Webinar cancellation
- Reminder email
- Attendee cancellation
- Attendee in waitlist
- Attendee pending approval
- Attendee registers after waitlist

The **`-EnableEventEmailEditing`** parameter in the **CsTeamsEventsPolicy** cmdlet controls the availability of email communication templates for your users.

The following table shows the behaviors of the settings for the **`-EnableEventEmailEditing`** parameter:

|Setting value| Behavior|
|---------|---------------|
|Enabled| **This is the default value.** Event organizers and co-organizers can edit all email templates for every event they organize.|
|Disabled| Event organizers and co-organizers can’t edit any email templates.|

The following example turns off **`-EnableEventEmailEditing`** so organizers and co-organizers can’t edit any email templates:

**BELOW COMMAND IS A PLACEHOLDER. I NEED AN ACTUAL EXAMPLE. REVISE BEFORE PUBLISHING.**

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -EnableEventEmailEditing Enabled
```

To learn more about `-EnableEventEmailEditing`, see [**PLACEHOLDER FOR CMDLET REFERENCE**.]

## Collect webinar attendance information

### Attendance report for Teams webinars

The attendance report for Teams webinars shows meeting organizers who attended a webinar, what time each person joined and left, and more. The attendance report setting controls whether organizers can view or download the attendance report for the webinars they've set up.

In the Teams admin center, the attendance report setting is called "**Attendance report**" and in PowerShell, its parameter is called "**`-AllowEngagementReport`**."

The following table shows the behavior of the settings for "**`-AllowEngagementReport`**" and "**Attendance report**":

|Setting value| Behavior|
|---------|---------------|
|Everyone, unless organizers opt out| **This is the default setting.** Webinar organizers control whether attendance reports are on or off for a webinar. |
|No one| Webinar organizers can't view or download attendance reports for a webinar they've organized.|
|Everyone| Webinar organizers can't turn off attendance reports for webinars they create. The attendance report is available for them.|

For instructions on how to set up and manage attendance reports using the Teams admin center or PowerShell, see [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)

For more information on `-AllowEngagementReport`, see [Set-CsTeamsMeetingPolicy.](/powershell/module/teams/set-csteamsmeetingpolicy)

### Who is in the attendance report for Teams webinars

The **"Who is in the attendance report"** setting controls whether participants in the webinar can opt in or out of offering their attendance information to be included in the organizer's attendance report. You can manage this setting in the Teams admin center.

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
- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)
