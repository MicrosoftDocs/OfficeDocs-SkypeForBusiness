---
title: Manage email communications for town halls and webinars
author: wlibebe
ms.author: wlibebe
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: sherimehmood
ms.date: 10/03/2023
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Learn how to manage email communications for webinars in Microsoft Teams for admins.
appliesto: 
  - Microsoft Teams
---
# Manage email communications for Teams town halls and webinars

**APPLIES TO:** ✖️Meetings ✔️Webinars ✔️Town halls

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

## Overview

With a Teams Premium license, you can decide if event organizers and co-organizers can edit email templates for their webinars and town halls. With email templates, organizers and co-organizers can manage waitlists, remind attendees about webinars they've registered for, and provide clear instructions to attendees before, during, and after the event.
Your organizers and co-organizers can edit the following email communication templates:

- Registration Confirmation
- Webinar update
- Town hall update
- Webinar cancellation
- Town hall cancellation
- Reminder email
- Attendee cancellation
- Attendee in waitlist
- Attendee pending approval
- Attendee registers after waitlist

For more information on the email communications experience for your end users, see [Manage webinar emails in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-emails-in-microsoft-teams-d0006848-f707-494f-b0a4-eeebcbc723be).

## Use the Teams admin center to manage email communications

You can use the Teams admin center to manage whether organizers and co-organizers can edit email templates for their webinars and town halls.

Follow these steps in the Teams admin center to manage the email communications for webinars and town halls:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Toggle the **Allow email editing** setting **On** or **Off**.
6. Select **Save**

## Manage email communications for webinars and town halls with PowerShell

Through PowerShell, you can manage whether organizers and co-organizers can edit email templates for their webinars and town halls.
The **`-AllowEmailEditing`** parameter in the **CsTeamsEventsPolicy** cmdlet controls whether your users can edit email communication templates.
The following table shows the behaviors of the settings for the **`-AllowEmailEditing`** parameter:

|Setting value| Behavior|
|---------|---------------|
|Enabled| **This is the default value.** Organizers and co-organizers can edit all email templates for their webinars and town halls.|
|Disabled| Organizers and co-organizers can’t edit any email templates for their webinars and town halls.|

The following example turns off **`-AllowEmailEditing`** so organizers and co-organizers can’t edit any email templates:

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowEmailEditing Disabled
```

To learn more about `-AllowEmailEditing`, see the following cmdlet topics:

- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)

## Related articles

- [Set up webinars](set-up-webinars.md)
- [Set up town halls](set-up-town-halls.md)
