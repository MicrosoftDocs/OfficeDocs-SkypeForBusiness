---
title: Set up for webinars in Microsoft Teams 
author: KarliStites
ms.author: kastites
manager: serdars
ms.reviewer: sachung
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

Webinars are structured meetings where instructors and participants have clear roles, often used for training purposes.

## Allow users to schedule webinars using PowerShell

You can use the following attributes within the Windows PowerShell **Set-CsTeamsMeetingPolicy** cmdlet to set up for webinars in Teams.

- AllowMeetingRegistration
- WhoCanRegister
- AllowPrivateMeetingRegistration

Read [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy?view=skype-ps) for more information on the cmdlet.

> [!NOTE]
> Before you can run these cmdlets you must be connected to Skype for Business Online PowerShell. For more information, see [Manage Skype for Business Online with Microsoft 365 or Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

### Allow users to schedule webinars

To allow users in your organization to schedule webinars, run:

```powershell
Set-CsTeamsMeetingPolicy -AllowMeetingRegistration True
```

### Configure who can register for webinars

You can restrict registration to users only in your organization or open it up to everyone both inside and outside your tenant. If meeting registration is not enabled, the default value is **False**. If meeting registration is enabled, the default value is **EveryoneInCompany**.

> [!CAUTION]
> Keep in mind that **AllowPrivateMeetingScheduling** must be set to **True** for **WhoCanRegister** to work.

**To allow *only* everyone in your company to register for webinars, run:**

```powershell
Set-CsTeamsMeetingPolicy -AllowPrivateMeetingScheduling True
```

Then, run:

```powershell
Set-CsTeamsMeetingPolicy -WhoCanRegister EveryoneInCompany
```

**To allow both people in your organization *and* guests to register for webinars, run:**

```powershell
Set-CsTeamsMeetingPolicy -AllowPrivateMeetingScheduling True
```

Then, run:

```powershell
Set-CsTeamsMeetingPolicy -WhoCanRegister Everyone
```

### Configure webinar settings

After enabling your environment for webinars, no further admin management is required. The policy controls which options show up for webinar organizers.

## Related topics
