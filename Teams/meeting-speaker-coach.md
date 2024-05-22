---
title: Speaker Coach in Microsoft Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 10/12/2023
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier2
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.general
description: IT admins - Learn to turn speaker coach on or off for Teams meetings, webinars, and town halls.
---

# Manage Speaker Coach for Microsoft Teams meetings, webinars, and town halls

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

 Speaker Coach processes the audio of the user while they present, and of all unmuted participants during the meeting and provides private real-time feedback and suggestions for improvement. The user who turned on the Speaker Coach also gets a summary report of the feedback after the meeting. Only the user can view the summary report of feedback. Admins don't have access to any of this data.

For town halls, Speaker Coach only applies to organizers, co-organizers, and presenters.

As an admin, you can manage whether users can turn on Speaker Coach during Teams meetings, webinars, and town halls.

## Manage speaker coach using PowerShell

You can only set and edit this policy in PowerShell by using the **`-AllowMeetingCoach`** parameter within the [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet. Or, you can create a new Teams meeting policy by using the [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy) cmdlet and assign it to users.

This setting is enabled by default. To turn off speaker coach, use the following script:

To turn off meeting reactions, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingCoach False
```

## Related topics

- [Teams policies reference](settings-policies-reference.md#meetings)
- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies in Teams](policy-assignment-overview.md)
