---
title: Use PowerShell to set live events policies
author: mkbond007
ms.author: mabond
manager: serdars
ms.date: 07/10/2019
ms.topic: article
ms.service: msteams
ms.reviewer: sonua
audience: admin
search.appverid: MET150
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
description: Examples of how to use PowerShell to set policies in Teams to control who can hold live events in your organization and the features available in the events.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Use PowerShell to set live events policies in Microsoft Teams

You can use the following Windows PowerShell cmdlets to set and assign policy settings for live events in Teams: 
- [Get-CsTeamsMeetingBroadcastPolicy](/powershell/module/skype/get-csteamsmeetingbroadcastpolicy?view=skype-ps)
- [Set-CsTeamsMeetingBroadcastPolicy](/powershell/module/skype/set-csteamsmeetingbroadcastpolicy?view=skype-ps)
- [New-CsTeamsMeetingBroadcastPolicy](/powershell/module/skype/new-csteamsmeetingbroadcastpolicy?view=skype-ps)
- [Grant-CsTeamsMeetingBroadcastPolicy](/powershell/module/skype/grant-csteamsmeetingbroadcastpolicy?view=skype-ps)
- [New-CsGroupPolicyAssignment](/powershell/module/teams/new-csgrouppolicyassignment?view=teams-ps)

Here are some examples.

> [!NOTE]
> Before you can run these cmdlets you must be connected to Skype for Business Online PowerShell. For more information, see [Manage Skype for Business Online with Microsoft 365 or Office 365 PowerShell](/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

## Allow users to schedule live events 

> [!NOTE]
> These examples are for events produced in Teams. For events produced with an external app or device, there are additional steps you must do. For more information, see [Enable users to schedule events that were produced with an external app or device](set-up-for-teams-live-events.md#enable-users-to-schedule-events-that-were-produced-with-an-external-app-or-device).

**Allow a user to schedule live events**

If the user is assigned the global policy, run and verify that *AllowBroadcastScheduling* parameter is set to *True*:
```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```
Then assign the user to the global policy, run:
```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

### User scenarios
**You want all users in your organization to be able to schedule live events**

If users are assigned the global policy, run and verify that *AllowBroadcastScheduling* *is set to *True*:
```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```
If users are assigned a policy other than the global policy, run and verify that *-AllowBroadcastScheduling* is set to *True*:
```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -identity {policy name}
```
**You want live events scheduling to be disabled across your organization**

Disable live events scheduling, run:
```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -identity Global -AllowBroadcastScheduling $false
```
Assign all users in your organization to the global policy, run:
```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

**You want a large number of users to be able to schedule live events and prevent a set of users from scheduling them**

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
**You want to disable live event scheduling for a large number of the users and allow a set of users to schedule them**

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
- [Set up for Teams live events](set-up-for-teams-live-events.md)
- [Teams PowerShell overview](../teams-powershell-overview.md)