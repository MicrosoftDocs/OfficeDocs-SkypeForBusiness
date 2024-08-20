---
title: Manage email communications for events
author: wlibebe
ms.author: wlibebe
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: sherimehmood
ms.date: 8/14/2024
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Learn how to manage email communications for webinars in Microsoft Teams for admins.
appliesto: 
  - Microsoft Teams
---
# Manage email communications for events

**APPLIES TO:** ✖️Meetings ✔️Webinars ✔️Town halls

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

## Overview

With a Teams Premium license, you can decide whether event organizers and coorganizers can edit email templates for their webinars and town halls. With email templates, organizers and co-organizers can manage waitlists, remind attendees about webinars they registered for, and provide clear instructions for attendees before, during, and after the event.

Your webinar organizers and co-organizers can edit the following email communication templates:

- Attendee cancellation
- Attendee pending approval
- Attendee registration
- Attendee rejection
- Attendee waitlisting
- Event recording available
- Webinar cancellation
- Webinar date time update
- Webinar reminder

For more information on the webinar email communications experience for your users, see [Manage webinar emails in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-emails-in-microsoft-teams-d0006848-f707-494f-b0a4-eeebcbc723be).

Your town hall organizers and co-organizers can edit the following email communication templates:

- Event invitation
- Event recording available

For more information on the town hall email communications experience for your users, see [Schedule a town hall in Microsoft Teams](https://support.microsoft.com/office/schedule-a-town-hall-in-microsoft-teams-d493b5cc-9f61-4dac-8027-d837dafb7a4c#bkmk_town_hall_invites).

## Manage email communications for webinars and town halls

|Teams admin center policy option|Parameter value in PowerShell| Behavior|
|---------|---------|---------------|
|On|Enabled| **This is the default value.** Organizers and co-organizers can edit all email templates for their webinars and town halls. |
|Off|Disabled| Organizers and co-organizers can’t edit any email templates for their webinars and town halls.|

### Manage email communications in the Teams admin center

You can use the Teams admin center to manage whether organizers and co-organizers can edit email templates for their webinars and town halls.

Follow these steps in the Teams admin center to manage the email communications for webinars and town halls:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Toggle the **Customize event emails** setting **On** or **Off**.
6. Select **Save**

### Manage email communications through PowerShell

Through PowerShell, you can manage whether organizers and co-organizers can edit email templates for their webinars and town halls. The **`-AllowEmailEditing`** parameter in the **CsTeamsEventsPolicy** cmdlet controls whether your users can edit email communication templates.

The following example turns off **`-AllowEmailEditing`** so organizers and co-organizers can’t edit any email templates:

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowEmailEditing Disabled
```

To learn more about **`-AllowEmailEditing`**, see the following cmdlet topics:

- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)

## Related articles

- [Issues that affect Teams webinars](/microsoftteams/troubleshoot/meetings/issues-with-webinars)
- [Set up webinars](set-up-webinars.md)
- [Set up town halls](set-up-town-halls.md)
