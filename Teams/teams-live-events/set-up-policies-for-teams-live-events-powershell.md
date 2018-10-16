---
title: Set up for live events in Microsoft Teams
author: tonysmith
ms.author: tonysmit
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: tonysmit
search.appverid: MET150
description: Learn the steps to set up live for events in Teams, including preparing your network, assigning licenses, using policies to enable live event features and scheduling for users, and setting up a third-party distribution provider.
appliesto: 
- Microsoft Teams
---

# Set up for live events in Microsoft Teams
> [!INCLUDE [Preview customer token](../includes/preview-feature.md)]

You can use Windows PowerShell to set policy settings for live events. Here's some examples.
## Allow users to schedule live events 

### For quick start events
Use the setting *AllowBroadcastScheduling* in **TeamsMeetingBroadcastPolicy** in Teams PowerShell to control whether a user can create live events in Teams. 

**Allow a user to schedule live events**

If the user is assigned the global policy, run and verify that *AllowBroadcastScheduling* parameter is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```
Then assign the user to the global policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

#### User scenarios
**You want all users in your organization to be able to create live events.**

If users are assigned the global policy, run and verify that *AllowBroadcastScheduling* *is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -identity Global
```
If the users are assigned a policy other than the global policy, run and verify that *-AllowBroadcastScheduling* is set to *True*:
```
Get-CsTeamsMeetingBroadcastPolicy -identity {policy name}
```
**You want live events scheduling to be disabled across your organization.**

Disable live events scheduling, run:
```
Set-CsTeamsMeetingBroadcastPolicy -identity Global -AllowBroadcastScheduling $false
```
Assign all users in your organization to the global policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```

**You want a large number of users to be able to create live events, but want to prevent a set of users from creating them.**

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
New-CSTeamsMeetingBroadcastPolicy -Identity DisabledBroadcastSchedulingpolicy
```
Disable live eventsscheduling, run:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity DisabledBroadcastSchedulingpolicy -AllowBroadcastScheduling $false
```
Then assign users to this policy, run:
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName DisabledBroadcastSchedulingpolicy -Verbose
```
**You want live events to be disabled for a large number of the users, but want to allow a set of users to create them.**

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

### For external encoder events
You must do the following to enable live event scheduling for those users.

#### Step 1: Enable Microsoft Stream for users in your organization**
Microsoft Stream is available as part of eligible Office 365 subscriptions or as a standalone service. See [Stream licensing overview](https://docs.microsoft.com/stream/license-overview) for more details.

> ![NOTE]
> Microsoft Stream is not included in Business Essentials or Business Premium plans.  

Learn more about how you can [assign licenses to users in Office 365](https://support.office.com/article/Assign-licenses-to-users-in-Office-365-for-business-997596B5-4173-4627-B915-36ABAC6786DC) so that users can access Microsoft Stream. Ensure Microsoft Stream is not blocked for the users as defined in [this article](https://docs.microsoft.com/stream/disable-user-organization).

#### Step 2: Ensure users have live event creation permission in Microsoft Stream**
By default, administrators can create external encoder live events. Microsoft Stream administrator can [enable additional users for live event creation](https://docs.microsoft.com/stream/live-event-administration#enabling-and-restricting-users-to-creating) in Stream.  

#### Step 3: Ensure live event organizers have consented to the company policy set by Stream admin**
If a Microsoft Stream administrator has [set up a company guidelines policy](https://docs.microsoft.com/stream/company-policy-and-consent) and requires employees to accept this policy before saving content, then users must do so before creating a live event (with External Encoder production) in Teams. Before you rollout the live events feature in the organization, make sure users who will be creating these live events have consented to the policy. 

## Set attendee visibility options
 
Set the global policy to allow users to create events that everyone, including anonymous users, can attend, run:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastAttendeeVisibility Everyone  
```
## Set recording options
> [!NOTE]
> This option applies only to quick start events.

Set the global policy to disable recording for live events:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastRecordingMode AlwaysDisabled 
```
## Configure real-time transcription and translation in Teams live events (coming soon)
> [!NOTE]
> This option applies only to quick start events. 

Set the global policy to turn on transcription and translation on for event attendees:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -AllowBroadcastTranscription $true 
```

### Related topics
- [What are Teams live events?](what-are-teams-live-events.md)
- [Plan for Teams live events](plan-for-teams-live-events.md)
- [Set up for Teams live event](set-up-for-teams-live-events.md)
- [Confgure live events settings in Teams](configure-teams-live-events.md)

