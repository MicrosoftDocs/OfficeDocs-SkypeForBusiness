---
title: Set up for webinars in Microsoft Teams 
author: KarliStites
ms.author: kastites
manager: serdars
ms.reviewer: sachung, emryan
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Learn how to manage Webinar policies for Teams meetings.
---

# Set up for webinars in Microsoft Teams

This article will help you set up your organization to host webinars.

## What are webinars?

Webinars are structured meetings where instructors and participants have clear roles, often used for training purposes or sales and marketing lead generation scenarios.

After setting up webinars in your organization, your users can schedule webinars and open registration to attendees. Unlike traditional meetings that include many discussions and task assignment, webinars are meant for interactive presentations and provide tools for attendee analysis.

## Allow users to schedule webinars using PowerShell

You can use the following attributes within the Windows PowerShell **Set-CsTeamsMeetingPolicy** cmdlet to set up for webinars in Teams.

- AllowMeetingRegistration
- WhoCanRegister
- AllowPrivateMeetingScheduling

Read [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) for more information on the cmdlet.

> [!NOTE]
> Before you can run these cmdlets you must be connected to Skype for Business Online PowerShell. For more information, see [Manage Skype for Business Online with Microsoft 365 or Office 365 PowerShell](/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

### Allow users to schedule webinars

To allow users in your organization to schedule webinars, run:

```powershell
Set-CsTeamsMeetingPolicy -AllowMeetingRegistration True
```
### Configure who can register for webinars

You can restrict registration to users only in your organization or open it up to everyone both inside and outside your tenant. By default, **WhoCanRegister** is enabled and set to **Everyone**. If you want to turn off meeting registration, set **WhoCanRegister** to **False**.

> [!IMPORTANT]
> Keep in mind that **AllowPrivateMeetingScheduling** must be set to **True** for **WhoCanRegister** to work. Additionally, Microsoft Lists needs to be set up in SharePoint. To learn more, see [Control settings for Microsoft Lists](/sharepoint/control-lists).

**To allow *only* users in your organization to register for webinars, run:**

```powershell
Set-CsTeamsMeetingPolicy -AllowPrivateMeetingScheduling True
```

Then, run:

```powershell
Set-CsTeamsMeetingPolicy -WhoCanRegister EveryoneInCompany
```

**To allow anyone, including anonymous users, to register for webinars, run:**

```powershell
Set-CsTeamsMeetingPolicy -AllowPrivateMeetingScheduling True
```

Then, run:

```powershell
Set-CsTeamsMeetingPolicy -WhoCanRegister Everyone
```

> [!IMPORTANT]
> If anonymous join is turned off in meeting settings, anonymous users can't join webinars. To learn more and enable this setting, see [Meeting settings in Teams](meeting-settings-in-teams.md).

### Collect meeting attendance

If you want organizers to analyze who registered and attended webinars, you'll need to turn on the **AllowEngagementReport** policy. To do this, run the following command in PowerShell.

```powershell
Set-CsTeamsMeetingPolicy -AllowEngagementReport Enabled
```

### Configure webinar settings

After enabling your environment for webinars, no further admin management is required. The policy controls which options show up for webinar organizers.

## Related topics

- [Meeting policies in Teams - General](meeting-policies-in-teams-general.md)
- [Set-CsTeamsMeetingPolicy documentation](/powershell/module/skype/set-csteamsmeetingpolicy)
