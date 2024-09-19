---
title:  Manage who can schedule town halls in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: sachung
ms.date: 9/18/2024
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
description: Learn how to set up and manage town hall policies for IT Admins in Microsoft Teams. Learn how to manage who can schedule town halls in your organization.
---

# Manage who can schedule town halls in Microsoft Teams

**APPLIES TO:** ✖️Meetings ✖️Webinars ✔️Town halls

## Overview

Town halls in Microsoft Teams are a one-to-many interactive virtual event. This article describes how you, as an admin, can decide which users can create town halls in your organization. To learn more about town hall features and capabilities, see [Plan for town halls](plan-town-halls.md).

For details on how your organizers can create town halls, see [Schedule a town hall in Microsoft Teams](https://support.microsoft.com/office/schedule-a-town-hall-in-microsoft-teams-d493b5cc-9f61-4dac-8027-d837dafb7a4c).

### Manage who can schedule town halls

You can use the Teams admin center or PowerShell to manage who can schedule town halls in your organization.

|Teams admin center value| PowerShell value|Behavior|
|---------|---------------|---------------|
|On|Enabled| **This is the default.** Users with this policy can create town halls. |
|Off|Disabled| Users with this policy can't create town halls.|

### Manage who can schedule town halls using the Teams admin center

To manage who can schedule town halls through the Teams admin center, use the following steps:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Toggle the **Allow town halls** setting **On** or **Off**.
6. Select **Save**

## Manage who can schedule town halls through PowerShell

You can use PowerShell to manage who can schedule town halls in your organization.

To manage who can schedule town halls, use the **`-AllowTownhalls`** parameter within the PowerShell [**CsTeamsEventsPolicy**](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

### Turn off town halls

To prevent organizers with this policy from creating town halls, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowTownhalls Disabled
```

### Turn off public town halls

To prevent organizers with this policy from scheduling public town halls, use the following script:

> [!NOTE]
> The EveryoneInCompanyExcludingGuests value allows only in org attendees to join town halls created by organizers with this policy. For town halls, in org attendees include guests. However, for webinars, guests aren't considered in org.

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType EveryoneInCompanyExcludingGuests
```

## Related topics

- [Plan for town halls](plan-town-halls.md)
- [Meetings, webinars, and live events overview](quick-start-meetings-live-events.md)
- [Feature comparison](meeting-webinar-town-hall-feature-comparison.md)
- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)
