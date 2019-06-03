---
title: Use PowerShell to set live events policies in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 10/23/2018
ms.topic: article
ms.service: msteams
ms.reviewer: sonua
search.appverid: MET150
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
description: Examples of how to use PowerShell to set policies in Teams to control who can hold live events in your organization and features that are available in the events that they create
appliesto: 
- Microsoft Teams
---

# Use PowerShell to set live events policies in Microsoft Teams

You can use the following Windows PowerShell cmdlets to set and assign policy settings for live events in Teams: 
- [Get-CsTeamsMeetingBroadcastPolicy](https://docs.microsoft.com/powershell/module/skype/get-csteamsmeetingbroadcastpolicy?view=skype-ps)
- [Set-CsTeamsMeetingBroadcastPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingbroadcastpolicy?view=skype-ps)
- [New-CsTeamsMeetingBroadcastPolicy](https://docs.microsoft.com/powershell/module/skype/get-csteamsmeetingbroadcastpolicy?view=skype-ps)
- [Grant-CsTeamsMeetingBroadcastPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsmeetingbroadcastpolicy?view=skype-ps)

Here's some examples.

## Allow users to schedule live events 

> [!NOTE]
> These examples are for events produced in Teams. For events produced with an external app or device, there are additional steps you must do. For more information, see [Enable users to schedule events produced with an external app or device](set-up-for-teams-live-events.md#enable-users-to-schedule-events-produced-with-an-external-app-or-device).

**Allow a user to schedule live events**

If the user is assigned the global policy, run and verify that *AllowBroadcastScheduling* parameter is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```
Then assign the user to the global policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

### User scenarios
**You want all users in your organization to be able to schedule live events**

If users are assigned the global policy, run and verify that *AllowBroadcastScheduling* *is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```
If users are assigned a policy other than the global policy, run and verify that *-AllowBroadcastScheduling* is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -identity {policy name}
```
**You want live events scheduling to be disabled across your organization**

Disable live events scheduling, run:
```
Set-CsTeamsMeetingBroadcastPolicy -identity Global -AllowBroadcastScheduling $false
```
Assign all users in your organization to the global policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

**You want a large number of users to be able to schedule live events and prevent a set of users from scheduling them**

Run and verify that *AllowBroadcastScheduling* is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -Identity Global
```
Then assign a user or users to the global policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

Create a new policy that doesn't allow scheduling live events, run:
```
New-CSTeamsMeetingBroadcastPolicy -Identity DisabledBroadcastSchedulingPolicy
```
Disable live events scheduling, run:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity DisabledBroadcastSchedulingPolicy -AllowBroadcastScheduling $false
```
Then assign users to this policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName DisabledBroadcastSchedulingPolicy -Verbose
```
**You want to disable live event scheduling for a large number of the users and allow a set of users to schedule them**

Disable live events scheduling, run:
```
Set-CsTeamsMeetingBroadcastPolicy -identity Global -AllowBroadcastScheduling $false
```
Then assign those users to the global policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```
Create a policy to allow live events scheduling, run:
```
New-CSTeamsMeetingBroadcastPolicy -identity EnableBroadcastSchedulingpolicy
```
Enable live events scheduling, run:
```
Set-CsTeamsMeetingBroadcastPolicy -identity EnableBroadcastSchedulingpolicy -AllowBroadcastScheduling $true
```
Then assign users to this policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName EnableBroadcastSchedulingpolicy -Verbose
```
## Set who can join live events
 
Set the global policy to allow users to create events that everyone, including anonymous users, can attend, run:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastAttendeeVisibility Everyone  
```
## Set the recording option for live events
> [!NOTE]
> This setting applies only to events produced in Teams.

Set the global policy to disable recording for live events:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastRecordingMode AlwaysDisabled 
```
## Set transcription and translation in live events (coming soon)
> [!NOTE]
> This setting applies only to events produced in Teams. 

Set the global policy to turn on transcription and translation on for event attendees:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -AllowBroadcastTranscription $true 
```

### Related topics
- [Set up for Teams live events](set-up-for-teams-live-events.md)


