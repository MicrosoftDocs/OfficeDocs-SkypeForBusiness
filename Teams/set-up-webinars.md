---
title: Admin- Set up webinars
ms.author: wlibebe
author: wlibebe
manager: serdars
ms.reviewer: justle, ritikag
ms.date: 10/01/2023
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
description: Learn how to set up and manage webinar policies for IT Admins in Teams.
---

# Admin- Set up webinars in Microsoft Teams

**APPLIES TO:** ✖️Meetings ✔️Webinars ✖️Town halls

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

Microsoft Teams offers webinars, a two-way interactive virtual event. This article describes how you, as an admin, can set up and manage webinars, including managing webinar features.

A webinar is a two-way interactive virtual event where the presenters deliver information to attendees. This format provides extra control for an organizer over the conversation and participants. Common scenarios for webinars might include trainings, product demos, sales lead generation, customer events, company announcements, and showcasing products. Webinars can accommodate up to 1,000 attendees and allow organizers to gather registration data from attendees before the event.

For more information on how to plan for webinars in your org, see [Plan for Teams meetings](plan-webinars.md)

In addition to the base webinar features, we offer extra webinar functionality through the Teams Premium subscription.

The following list displays webinar features; the Premium features are bolded and marked with an asterisk:

- Allow registered users to bypass the lobby
- Assign a co-organizer
- ***Create a webinar wait list**
- ***Limit the day and time when people can register**
- Limit the number of people who can register
- ***Manage attendees’ view**
- ***Manually approve registrants**
- Require attendees to register
- ***Send reminder emails to registrants**
- ***Set up a green room for webinar presenters**
- Turn on Q&A for webinars with up to 1000 attendees
- ***Use RTMP-In for webinars**
- View attendance reports

To learn more about advanced webinar features, see [Microsoft Teams Premium licensing.](/MicrosoftTeams/teams-add-on-licensing/licensing-enhance-teams)

To learn more about the end user experience, see [Get Started with Teams webinars](https://support.microsoft.com/office/42f3f874-22dc-4289-b53f-bbc1a69013e3)

For instructions on how to set up and manage attendance reports using the Teams admin center or PowerShell, see [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)

> [!NOTE]
> The webinar experience isn't available for Microsoft 365 GCC High or Microsoft 365 DoD.

## Manage webinars using the Teams admin center

You can use the Teams admin center to set up and manage the webinar experience for your organization.

### Turn webinars on or off

Follow these steps in the Teams admin center to turn webinars on or off:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Toggle the **Allow webinars** setting **On** or **Off**.
6. Select **Save**

## Manage webinars using PowerShell

You can use PowerShell to set up and manage the webinar experience for your organization.

To set up webinars, use the **`-AllowWebinars`** parameter within the PowerShell [**CsTeamsEventsPolicy**](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

The following table shows the behaviors of the settings for the **`-AllowWebinars`** parameter:

|Setting value| Behavior|
|---------|---------------|
|Enabled| Users with this policy can create webinars. |
|Disabled| Users with this policy can't create webinars.|

Before you can run these cmdlets, you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

For more information on PowerShell cmdlets for Teams webinars, see the [Related topics](#related-topics) section.

### Turn on webinars

To turn on webinars, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinars Enabled
```

### Turn off webinars

To turn off webinars, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinars Disabled
```

## Who can register for webinars

You can use PowerShell to manage whether organizers can [create public or private webinars](https://support.microsoft.com/office/0719a9bd-07a0-47fd-8415-6c576860f36a):

To allow organizers to only create private webinars, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType EveryoneInCompanyExcludingGuests
```

To allow organizers to create public or private webinars, use the following script. Public webinars may include anonymous users:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType Everyone
```

## Related topics

[Manage the registration form for webinars](manage-registration-form-webinars.md)

[Manage email communications for webinars](manage-email-communications.md)

[Meetings, webinars, and live events](quick-start-meetings-live-events.md)

[Attendance report for meetings and webinars in Microsoft Teams](teams-analytics-and-reports/meeting-attendance-report.md)

[New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)

[Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)

[Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)

[Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)

[Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)
