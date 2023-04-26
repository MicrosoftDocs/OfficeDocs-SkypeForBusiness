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

Microsoft Teams offers webinars, a two-way interactive virtual event. This article describes how you, as an admin, can set up and manage webinars, including managing webinar features.

In addition to the base webinar features, we offer additional webinar functionality through the Teams Premium subscription.

The following list displays webinar features; the Premium features are bolded and marked with an asterisk:

- Require attendees to register
- Assign a co-organizer
- ***Manage attendees’ view**
- Limit the number of people who can register
- Allow registered users to bypass the lobby
- ***Set up a green room for webinar presenters**
- Turn on Q&A for webinars with up to 1000 attendees
- View attendance reports
- Integrate with Dynamics 365
- ***Send reminder emails to registrants**
- ***Create a webinar wait list**
- ***Manually approve registrants**
- ***Limit the day and time when people can register**
- ***Use RTMP-In for webinars**

To learn more about advanced webinar features, see [Microsoft Teams Premium licensing.](/MicrosoftTeams/teams-add-on-licensing/licensing-enhance-teams)

A webinar is a two-way interactive virtual event where the presenters deliver information to attendees. This format provides extra control for an organizer over the conversation and participants. Common scenarios for webinars might include trainings, product demos, sales lead generation, customer events, company announcements, and showcasing products. Webinars can accommodate up to 1,000 attendees and allow organizers to gather registration data from attendees before the event.

To learn more about the end user experience, see [Get Started with Teams webinars](/office/manage-webinar-registration)

For instructions on how to set up and manage attendance reports using the Teams admin center or PowerShell, see [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)

> [!NOTE]
> The webinar experience isn't available for Microsoft 365 GCC High or Microsoft 365 DoD.

## Set up webinars

If you'd like to set up and manage the webinar experience for your organization, you must use PowerShell.

To set up webinars, use the **`-AllowWebinars`** parameter within the PowerShell [**CsTeamsEventsPolicy**](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

The following table shows the behaviors of the settings for the **`-AllowWebinars`** parameter:

|Setting value| Behavior|
|---------|---------------|
|Enabled| The webinar entry point is available for your users to create webinars. |
|Disabled| There's no webinar entry point for your users to create webinars.|

Before you can run these cmdlets, you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

For more details on PowerShell cmdlets for Teams webinars, see the [Related topics](#related-topics) section.

### Create and manage webinars using PowerShell

#### Turn on webinars

To turn on webinars for a new policy, use the following script:

```powershell
New-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinars Enabled
```

#### Turn off webinars

To turn off webinars, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinars Disabled
```

## Who can register for webinars

You can use the following cmdlets to manage who can register for webinars in your organization:

To allow **only** users in your organization to register for webinars, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType EveryoneInCompanyExcludingGuests
```

To allow everyone, including anonymous users, to register for webinars, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType Everyone
```

> [!IMPORTANT]
> If **Anonymous users can join a meeting** is turned off in **Meeting settings**, anonymous users can't join webinars. To learn more and enable this setting, see [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md).

## Email communications for webinars

With a Teams premium license, you can decide if event organizers and co-organizers can use email templates for webinars. With email templates, organizers and co-organizers can manage waitlists, remind attendees about webinars they've registered for, and provide clear instructions to attendees before, during, and after the event.

Your organizers and co-organizers can edit the following email communication templates:

- Registration Confirmation
- Webinar update
- Webinar cancellation
- Reminder email
- Attendee cancellation
- Attendee in waitlist
- Attendee pending approval

For more information on the email communications experience for your end users, see [**PLACEHOLDER FOR END USER EMAIL COMMUNICATIONS DOC**].

### Manage email communications for webinars with PowerShell

Through PowerShell, you can manage whether organizers and co-organizers can edit email templates.

The **`-EnableEventEmailEditing`** parameter in the **CsTeamsEventsPolicy** cmdlet controls whether your users can edit email communication templates.

The following table shows the behaviors of the settings for the **`-EnableEventEmailEditing`** parameter:

|Setting value| Behavior|
|---------|---------------|
|Enabled| **This is the default value.** Event organizers and co-organizers can edit the email templates for their webinars .|
|Disabled| Event organizers and co-organizers can’t edit any email templates.|

The following example turns off **`-EnableEventEmailEditing`** so organizers and co-organizers can’t edit any email templates:

[**BELOW COMMAND IS A PLACEHOLDER. I NEED AN ACTUAL EXAMPLE. REVISE BEFORE PUBLISHING.**]

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -EnableEventEmailEditing Enabled
```

To learn more about `-EnableEventEmailEditing`, see [**PLACEHOLDER FOR CMDLET REFERENCE**.]

## Related topics

- [Teams policies reference - Meetings](settings-policies-reference.md#meetings)
- [Meetings, webinars, and live events](quick-start-meetings-live-events.md)
- [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)
- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)
