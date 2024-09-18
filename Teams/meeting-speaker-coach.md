---
title: Speaker Coach in Microsoft Teams meetings and events
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: bryannyce
ms.date: 9/18/2024
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

# Manage Speaker Coach for Microsoft Teams meetings and events

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

Speaker Coach in Teams meetings and events processes the user's audio while they present, as well as the audio of all unmuted participants, providing private real-time feedback and suggestions for improvement. For town halls, Speaker Coach only applies to organizers, co-organizers, and presenters. The user who turns on Speaker Coach receives a summary report of the feedback after the meeting or event, which only they can view, but you don't have access to this data. As an admin, you can manage whether users in your organization can use Speaker Coach during meetings and events.

## Manage Speaker Coach using PowerShell

You must use PowerShell to manage Speaker Coach through the **`-AllowMeetingCoach`** parameter within the [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet. Or, you can create a new Teams meeting policy by using the [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy) cmdlet and assign it to users.

This setting is on by default. To turn off Speaker Coach, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingCoach False
```

## Related topics

- [Plan meetings](plan-meetings.md)
- [Plan webinars](plan-webinars.md)
- [Plan town halls](plan-town-halls.md)
- [Teams policies reference](settings-policies-reference.md#meetings)
- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies in Teams](policy-assignment-overview.md)
