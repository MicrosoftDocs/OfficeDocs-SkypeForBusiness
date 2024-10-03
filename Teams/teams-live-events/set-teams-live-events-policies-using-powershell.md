---
title: Use PowerShell to set live events policies
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.date: 10/3/2024
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
> We're currently still supporting live events. While we still recommend you to upgrade to [Teams town halls](../plan-town-halls.md) to take advantage of new features and experiences, your users can continue to schedule events. For more information, see [Updates for Town Hall in Microsoft Teams and Teams Live Events](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/extension-for-teams-live-events-retirement/ba-p/4148352).

You can use the following Windows PowerShell cmdlets to set and assign policy settings for live events in Teams:

- [Get-CsTeamsMeetingBroadcastPolicy](/powershell/module/teams/get-csteamsmeetingbroadcastpolicy)
- [Set-CsTeamsMeetingBroadcastPolicy](/powershell/module/teams/set-csteamsmeetingbroadcastpolicy)
- [New-CsTeamsMeetingBroadcastPolicy](/powershell/module/teams/new-csteamsmeetingbroadcastpolicy)
- [Grant-CsTeamsMeetingBroadcastPolicy](/powershell/module/teams/grant-csteamsmeetingbroadcastpolicy)
- [New-CsGroupPolicyAssignment](/powershell/module/teams/new-csgrouppolicyassignment)

> [!NOTE]
> Before you can run these cmdlets you must be connected to Skype for Business Online PowerShell. For more information, see [Manage Skype for Business Online with Microsoft 365 or Office 365 PowerShell](/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

The following sections provide user scenarios for various PowerShell commands used to manage events produced in Teams:

> [!NOTE]
> These examples are for events produced in Teams.

## Allow a user to schedule live events

1. If the user is assigned the global policy, run the following script and verify that the **`-AllowBroadcastScheduling`** parameter is set to *True*:

```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```

2. Next, to assign the user to the global policy, run the following script:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

## You want all users in your organization to be able to schedule live events

If users are assigned the global policy, run and verify that **`-AllowBroadcastScheduling`** is set to *True*:

```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```

If users are assigned a policy other than the global policy, run and verify that **`-AllowBroadcastScheduling`** is set to *True*:

```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -identity {policy name}
```

## You want to turn off live events scheduling for your organization

To turn off live events scheduling, run the following script:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -identity Global -AllowBroadcastScheduling $false
```

To assign all users in your organization to the global policy,  run the following script:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

## You want a large number of users to be able to schedule live events and prevent a set of users from scheduling them

### 1. Allow a large number of users to schedule live events

1. Run the following script to verify that **`-AllowBroadcastScheduling`**is set to *True*:

```PowerShell
Get-CsTeamsMeetingBroadcastPolicy -Identity Global
```

2. Next, to assign a user or users to the global policy, run the following script:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

### 2. Create a new policy that doesn't allow specific users to schedule live events

1. To create a new policy that doesn't allow specific users to schedule live events, run the following script:

```PowerShell
New-CSTeamsMeetingBroadcastPolicy -Identity DisabledBroadcastSchedulingPolicy
```

2. To turn off live events scheduling, run the following script:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -Identity DisabledBroadcastSchedulingPolicy -AllowBroadcastScheduling $false
```

3. To assign users to this policy, run the following script

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName DisabledBroadcastSchedulingPolicy -Verbose
```

## You want to turn off live event scheduling for a large number of the users and allow a set of users to schedule them

### 1. Turn off live events scheduling for a large number of users

1. To disable live events scheduling, run the following script:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -identity Global -AllowBroadcastScheduling $false
```

2. To assign those users to the global policy, run the following script:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

### 2. Create a new policy that allows specific users to schedule live events

1. To create a policy to allow live events scheduling, run the following script:

```PowerShell
New-CSTeamsMeetingBroadcastPolicy -identity EnableBroadcastSchedulingPolicy
```

2. To turn on live events scheduling, run the following script:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -identity EnableBroadcastSchedulingPolicy -AllowBroadcastScheduling $true
```

3. To assign users to this policy, run the following script:

```PowerShell
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName EnableBroadcastSchedulingPolicy -Verbose
```

## Set who can join live events

To set the global policy to allow users to create events that everyone, including anonymous users, can attend, run the following script:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastAttendeeVisibility Everyone  
```

## Set the recording option for live events

> [!NOTE]
> This setting applies only to events produced in Teams.

To set the global policy to disable recording for live events, run the following script:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastRecordingMode AlwaysDisabled 
```

## Set live captions and subtitles in live events

> [!NOTE]
> This setting applies only to events produced in Teams.

To set the global policy to turn on live captions and subtitles (transcription) for event attendees, run the following script:

```PowerShell
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -AllowBroadcastTranscription $true 
```

### Related topics

- [Set up for Teams live events](set-up-for-teams-live-events.md)
- [Teams PowerShell overview](../teams-powershell-overview.md)
