---
title: Manage on-shift and off-shift presence for Firstline Workers in Teams
author: LanaChin
ms.author: v-lanac
ms.reviewer: aaku
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to manage on-shift and off-shift presence in Teams for Firstline Workers in your organization.
localization_priority: Normal
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Manage on-shift and off-shift presence for Firstline Workers in Teams

> [!IMPORTANT]
> Effective June 30, 2020, Microsoft StaffHub has been retired. We’re building StaffHub capabilities into Microsoft Teams. Today, Teams includes the Shifts app for schedule management and additional capabilities will roll out over time. StaffHub stopped working for all users on June 30, 2020. Anyone who tries to open StaffHub is shown a message directing them to download Teams. To learn more, see [Microsoft StaffHub has been retired](microsoft-staffhub-to-be-retired.md).  

## Overview

Presence in Microsoft Teams indicates a user's current availability and status to other users. The presence of Firstline Workers is often less predictable than other staff as their working hours are typically not the same each day. As an admin, you can configure Teams to show a set of shift-based presence states for the Firstline Workers in your organization to indicate when they are on and off shift.

These shift-based presence states&mdash;![Solid green check mark, indicates On shift](../../media/flw-presence-on-shift.png) **On shift**, ![Gray circle with x, indicates Off shift](../../media/flw-presence-off-shift.png) **Off shift**, ![Solid red circle, indicates Busy](../../media/flw-presence-busy.png) **Busy**&mdash;are separate from the [default set of presence states](../../presence-admins.md) in Teams. With these two sets of presence states, you can configure different experiences for people in your organization based on their role.

With shift-based presence, you can manage access to Teams when Firstline Workers are off shift. For example, you can set up a custom message that Firstline Workers must acknowledge before they can use Teams when they're not on a scheduled shift.  

## Scenario

Here's an example of how your organization can use shift-based presence.

You have Firstline Workers in your organization that should only be paid for hours they work on a shift that their manager scheduled and approved. They shouldn't be paid for time spent working outside a scheduled shift, which includes using the Teams app. You set up a custom message that says "Your time on Teams when on off shift won't count toward payable hours", which is displayed when Firstline Workers try to access Teams when off shift. If they choose to use Teams, they click **I accept** with the understanding that they won't be paid for this time.

You also have information workers in your organization who are salaried and who don't work shifts. You configure your information workers to use the default presence states in Teams while giving your Firstline Workers shift-based presence.

## Shift-based presence states

Here are the shift-based presence states.

|App configured |User configured  |More information  |
|---------|---------|---------|
|![Solid green check mark, indicates On shift](../../media/flw-presence-on-shift.png) On shift     |         |Automatically set at the start of a shift         |
|![Gray circle with x, indicates Off shift](../../media/flw-presence-off-shift.png) Off shift     |         |Automatically set at the end of a shift         |
|![Solid red circle, indicates Busy](../../media/flw-presence-busy.png) Busy      | ![Solid red circle, indicates Busy](../../media/flw-presence-busy.png) Busy         |Automatically set. Can also be manually set when the Firstline Worker is on shift.|

## Off shift access to Teams

This feature lets you manage access to Teams when Firstline Workers are off shift. You can block or allow users to access Teams when they're off shift. You can set Teams to display a message to Firstline Workers if they access Teams when off shift. Firstline Workers must click **I accept** to acknowledge the message before they can use Teams.

You can choose from a set of pre-defined messages or customize the message to display any text that you want. Here's the default message:

![Screenshot of default message](../../media/shifts-presence-message.png)

You can also set the frequency that the message is displayed and set a grace period between when the first shift starts or last shift ends and when access to Teams is blocked.

## Manage shift-based presence

As an admin, you use policies to control shift-based presence for Firstline Workers in your organization. You manage these policies by using the following PowerShell cmdlets:

- New-TeamsShiftsPolicy
- Get-TeamsShiftsPolicy
- Set-TeamsShiftsPolicy
- Grant-TeamsShiftsPolicy

Use the New-TeamsShiftsPolicy cmdlet to create a new policy, set the parameters that you want, and then use the Grant-TeamsShiftsPolicy cmdlet to assign the policy to users.

Here's some examples. For detailed information about each of these parameters, including the list of predefined off shift messages that you can choose from, see New-TeamsShiftsPolicy.

### Example 1

In this example, we create a new policy named Unrestricted Teams Access. In this policy, shift-based presence is turned on and the default message is displayed every time a user who is assigned this policy accesses Teams when off shift. The user can use Teams when off shift if they accept the off shift message, and the grace period between when the first shift starts or last shift ends and when access is blocked is 10 minutes.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Unrestricted Teams Access" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType DefaultMessage -AccessType UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 10
```

### Example 2 

In this example, we create a new policy named Off Shift Teams Access. In this policy, shift-based presence is turned on and a custom message is displayed every time a user who is assigned this policy accesses Teams when off shift. The user can use Teams when off shift if they accept the off shift message, and the grace period between when the first shift starts or last shift ends and when access is blocked is 15 minutes.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Off Shift Teams Access" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType CustomMessage -ShiftNoticeMessageCustom "Your time on Teams when on off shift won't count toward payable hours" -AccessType UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 15
```

### Example 3 

In this example, we create a new policy named Block Off Shift Teams Access. In this policy, shift-based presence is turned on and the predefined "Access to Teams is turned off during non-working hours. You will be able to access the app when your next shift starts." message is displayed every time a user who is assigned this policy tries to access Teams when off shift. The user is blocked from using Teams when off shift, and the grace period between when the first shift starts or last shift ends and when access is blocked is two minutes.

```powershell
New-CsTeamsShiftsPolicy -Identity "Block Off Shift Teams Access" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType Message5 -AccessType OffShift_TeamsAppBlocked -AccessGracePeriodMinutes 2
```

### Example 4

In this example, we assign a policy named Unrestricted Teams Access to a user named remy@contoso.com.

```powershell
Grant-CsTeamsShiftsPolicy -Identity remy@contoso,com -PolicyName "Unrestricted Teams Access"
```

### Turn on or turn off shift-based presence for specific users

By default, shift-based presence is ???. You can turn on or turn off shift-based presence for specific users in your organization.Set the **EnableShiftPresence** parameter to one of the following.

|Setting value  |Behavior |
|---------|---------|
|True     | Turn on shift-based presence.      |
|False    | Turn off shift-based presence.     |

### Manage off shift access to Teams

#### Set the message that's displayed when users access Teams when off shift

You can use the default message, choose from a collection of predefined messages, or create your own custom message. To configure the message that you want to display, set the **ShiftNoticeMessageType** parameter to one of the following.

|Setting value  |Message that's displayed |
|---------|---------|
|DefaultMessage   | You aren't authorized to use Microsoft Teams during non-working hours and will only be compensated for using it during approved working hours.      |
|Message1    | Your employer does not authorize or approve of the use of its network, applications, systems, or tools by non-exempt or hourly employees during their non-working hours. By accepting, you acknowledge that your use of Teams while off shift is not authorized and you will not be compensated.      |
|Message2    | Accessing this app outside working hours is voluntary. You won't be compensated for time spent on Teams. Refer to your employer's guidelines on using this app outside working hours. By accepting, you acknowledge that you understand the statement above.    |
|Message3    | You won't be compensated for time using Teams. By accepting, you acknowledge that you understand the statement above.     |
|Message4    | You're not authorized to use Teams while off shift. By accepting, you acknowledge your use of Teams is against your employer's policy.    |
|Message5    | Access to Teams is turned off during non-working hours. You will be able to access the app when your next shift starts      |
|Message6    |Your employer does not authorize or approve of the use of its network, applications, systems, or tools by non-exempt or hourly employees during their non-working hours. Access to corporate resources are only allowed during approved working hours and should be recorded as hours worked in your employer’s timekeeping system     |
|Message7    | Your employer has turned off access to Teams during non-working hours. Refer to your employer's guidelines on using this app outside working hours.     |

## Related topics

- [Manage the Shifts app for your organization in Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
- [Teams PowerShell overview](../../teams-powershell-overview.md)
