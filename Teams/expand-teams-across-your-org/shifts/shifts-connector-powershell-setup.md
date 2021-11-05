---
title: Use PowerShell to connect Shifts to your Blue Yonder workforce management system
author: LanaChin
ms.author: v-lanachin
ms.reviewer: 
manager: samanro
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to manage shift-based access in Teams for Frontline Workers in your organization.
ms.localizationpriority: high
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Use PowerShell to connect Shifts to your Blue Yonder workforce management system

## Overview

## Set up your environment


## Test your connection settings

## Configure and create the connection

## Map sites to teams



## Manage shift-based access

As an admin, you use policies to control shift-based presence for frontline workers in your organization. You manage these policies by using the following PowerShell cmdlets:

- [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy)
- [Get-CsTeamsShiftsPolicy](/powershell/module/teams/get-csteamsshiftspolicy)
- [Set-CsTeamsShiftsPolicy](/powershell/module/teams/set-csteamsshiftspolicy)
- [Grant-CsTeamsShiftsPolicy](/powershell/module/teams/grant-csteamsshiftspolicy)
- [Remove-CsTeamsShiftsPolicy](/powershell/module/teams/remove-csteamsshiftspolicy)

Use the New-CsTeamsShiftsPolicy cmdlet to create a new policy, set the policy settings that you want, and then use the Grant-CsTeamsShiftsPolicy cmdlet to assign the policy to users.

Here's some examples. For detailed information about each policy setting and parameter, including the list of predefined off shift messages that you can choose from, see [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### Example 1

In this example, we create a new policy named Off Shift Teams Access Default Message. In this policy, shift-based presence is turned on and the default message is displayed every time a user who is assigned this policy accesses Teams when off shift. The user can use Teams when off shift if they accept the message, and the grace period between when the first shift starts or last shift ends and when access is restricted is 10 minutes.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Off Shift Teams Access Default Message" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType DefaultMessage -AccessType UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 10
```

> [!NOTE]
> Use the **ShiftNoticeMessageType** parameter to set the message that you want to display. To see a list of the pre-defined messages that you can choose from for this parameter, see [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### Example 2 

In this example, we create a new policy named Off Shift Teams Access Custom Message. In this policy, shift-based presence is turned on and a custom message is displayed every time a user who is assigned this policy accesses Teams when off shift. The user can use Teams when off shift if they accept the message, and the grace period between when the first shift starts or last shift ends and when access is restricted is 15 minutes.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Off Shift Teams Access Custom Message" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType CustomMessage -ShiftNoticeMessageCustom "Your time on Teams when on off shift won't count toward payable hours" -AccessType UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 15
```

> [!NOTE]
> Use the **ShiftNoticeMessageType** parameter to set the message that you want to display. To learn more, see [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### Example 3

In this example, we create a new policy named Off Shift Teams Access Message1. In this policy, shift-based presence is turned on and the following predefined message is displayed every time a user who is assigned this policy accesses Teams when off shift.

  "Your employer does not authorize or approve of the use of its network, applications, systems, or tools by non-exempt or hourly employees during their non-working hours. By accepting, you acknowledge that your use of Teams while off shift is not authorized and you will not be compensated." 

The user can use Teams when off shift if they accept the message, and the grace period between when the first shift starts or last shift ends and when access is restricted is three minutes.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Off Shift Teams Access Message1" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType Message1 -AccessType  UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 3
```

> [!NOTE]
> Use the **ShiftNoticeMessageType** parameter to set the message that you want to display. To see a list of the pre-defined messages that you can choose from for this parameter, see [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### Example 4

In this example, we assign a policy named Off Shift Teams Access Custom Message to a user named remy@contoso.com.

```powershell
Grant-CsTeamsShiftsPolicy -Identity remy@contoso.com -PolicyName "Off Shift Teams Access Custom Message"
```

## Related topics

- [Manage the Shifts app for your organization in Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
- [Teams PowerShell overview](../../teams-powershell-overview.md)