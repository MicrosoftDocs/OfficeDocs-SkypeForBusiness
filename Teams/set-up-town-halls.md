---
title: Set up town halls
ms.author: wlibebe
author: wlibebe
manager: serdars
ms.reviewer: sachung
ms.date: 10/03/2023
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
description: Learn how to set up and manage town hall policies for IT Admins in Teams.
---

# Set up town halls in Microsoft Teams

Microsoft Teams is introducing town halls, a one-to-many interactive virtual event. This article describes how you, as an admin, can set up and manage town halls for your users.

To learn more about town hall features and capabilities, see [Plan for town halls](plan-town-halls.md).

To learn more about the end user experience, see [PLACEHOLDER].

## Manage town halls using the Teams admin center

You can use the Teams admin center to set up and manage the town hall experience for your organization.

### Manage who can schedule town halls

Follow these steps in the Teams admin center to turn town halls on or off:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Toggle the **Allow town halls** setting **On** or **Off**.
6. Select **Save**

## Manage town halls using PowerShell

You can use PowerShell to set up and manage the town hall experience for your organization.

To set up town halls, use the **`-AllowTownhalls`** parameter within the PowerShell [**CsTeamsEventsPolicy**](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

The following table shows the behaviors of the settings for the **`-AllowTownhalls`** parameter:

|Setting value| Behavior|
|---------|---------------|
|Enabled| Users with this policy can create town halls. |
|Disabled| Users with this policy can't create town halls.|

Before you can run these cmdlets, you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

For more information on PowerShell cmdlets for Teams webinars, see the [Related topics](#related-topics) section.

### Turn on town halls

To turn on town halls, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowTownhalls Enabled
```

### Turn off town halls

To turn off town halls, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowTownhalls Disabled
```

### Disable public town halls

To turn off town halls, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType EveryoneInCompanyExcludingGuests
```

## Related topics

[Manage email communications for town halls and webinars placeholder](manage-email-communications.md)

[Set up webinars](set-up-webinars.md)

[Meetings, webinars, and live events](quick-start-meetings-live-events.md)

[New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)

[Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)

[Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)

[Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)

[Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)
