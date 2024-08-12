---
title: Use PowerShell to set live events policies
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.date: 01/16/2024
ms.topic: article
ms.service: msteams
ms.reviewer: christi.balaki
audience: admin
search.appverid: MET150
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Examples of how to use PowerShell to set policies in Teams to control who can hold live events in your organization and the features available in the events.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Use PowerShell to set live events policies in Microsoft Teams

> [!NOTE]
> Teams Live Events will no longer be deprecated on September 30, 2024, as previously announced. While we still recommend that customers upgrade to [Teams town hall](../plan-town-halls.md) when ready to take advantage of new features and experiences, Live Events users can now schedule events beyond September 2024. For more information, please read our recent [blog post](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/extension-for-teams-live-events-retirement/ba-p/4148352).

You can use the following Windows PowerShell cmdlets to set and assign policy settings for live events in Teams:

- [Get-CsTeamsMeetingBroadcastPolicy](/powershell/module/teams/get-csteamsmeetingbroadcastpolicy)
- [Set-CsTeamsMeetingBroadcastPolicy](/powershell/module/teams/set-csteamsmeetingbroadcastpolicy)
- [New-CsTeamsMeetingBroadcastPolicy](/powershell/module/teams/new-csteamsmeetingbroadcastpolicy)
- [Grant-CsTeamsMeetingBroadcastPolicy](/powershell/module/teams/grant-csteamsmeetingbroadcastpolicy)
- [New-CsGroupPolicyAssignment](/powershell/module/teams/new-csgrouppolicyassignment)

Here are some examples.

> [!NOTE]
> Before you can run these cmdlets you must be connected to Skype for Business Online PowerShell. For more information, see [Manage Skype for Business Online with Microsoft 365 or Office 365 PowerShell](/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

## Allow users to schedule live events

> [!NOTE]
> These examples are for events produced in Teams.

### Allow a user to schedule live events

If the user is assigned the global policy, run and verify that *AllowBroadcastScheduling* parameter is set to *True*:

```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```

Then assign the user to the global policy, run:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

### User scenarios

#### You want all users in your organization to be able to schedule live events

If users are assigned the global policy, run and verify that *AllowBroadcastScheduling* is set to *True*:

```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```

If users are assigned a policy other than the global policy, run and verify that *-AllowBroadcastScheduling* is set to *True*:

```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -identity {policy name}
```

#### You want live events scheduling to be disabled across your organization

Disable live events scheduling, run:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -identity Global -AllowBroadcastScheduling $false
```

Assign all users in your organization to the global policy, run:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

#### You want a large number of users to be able to schedule live events and prevent a set of users from scheduling them

Run and verify that *AllowBroadcastScheduling* is set to *True*:

```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -Identity Global
```

Then assign a user or users to the global policy, run:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

Create a new policy that doesn't allow scheduling live events, run:

```PowerShell
New-CSTeamsMeetingBroadcastPolicy -Identity DisabledBroadcastSchedulingPolicy
```

Disable live events scheduling, run:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -Identity DisabledBroadcastSchedulingPolicy -AllowBroadcastScheduling $false
```

Then assign users to this policy, run:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName DisabledBroadcastSchedulingPolicy -Verbose
```

#### You want to disable live event scheduling for a large number of the users and allow a set of users to schedule them

Disable live events scheduling, run:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -identity Global -AllowBroadcastScheduling $false
```

Then assign those users to the global policy, run:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

Create a policy to allow live events scheduling, run:

```PowerShell
New-CSTeamsMeetingBroadcastPolicy -identity EnableBroadcastSchedulingpolicy
```

Enable live events scheduling, run:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -identity EnableBroadcastSchedulingpolicy -AllowBroadcastScheduling $true
```

Then assign users to this policy, run:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName EnableBroadcastSchedulingpolicy -Verbose
```

## Set who can join live events

Set the global policy to allow users to create events that everyone, including anonymous users, can attend, run:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastAttendeeVisibility Everyone  
```

## Set the recording option for live events

> [!NOTE]
> This setting applies only to events produced in Teams.

Set the global policy to disable recording for live events:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastRecordingMode AlwaysDisabled 
```

## Set live captions and subtitles in live events

> [!NOTE]
> This setting applies only to events produced in Teams.

Set the global policy to turn on live captions and subtitles (transcription) for event attendees:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -AllowBroadcastTranscription $true 
```

### Related topics

[Set up for Teams live events](set-up-for-teams-live-events.md)

[Teams PowerShell overview](../teams-powershell-overview.md)
