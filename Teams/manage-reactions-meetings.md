--- 
title: Manage reactions in Teams meetings and webinars
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: defnea
ms.date: 10/12/2023
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - Tier2
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.participantandguests
description: Learn to manage meeting reactions in Teams meetings.
---

# Manage reactions in Teams meetings and webinars

**APPLIES TO:** ✔️Meetings ✔️Webinars ✖️Town halls

## Overview

Reactions in Microsoft Teams meetings and webinars enhance communication and engagement by allowing participants to express their feedback in real time. As an admin, you set the default value for reactions in your organizers' **Meeting options**. Organizers can change the setting for each meeting and webinar they create.

For details on how your users can use reactions, see [Express yourself in Microsoft Teams meetings with live reactions](https://support.microsoft.com/office/express-yourself-in-microsoft-teams-meetings-with-live-reactions-a8323a40-3d07-4129-934b-305370a36e21).

> [!NOTE]
> This policy doesn't apply to town halls. To learn more about town hall attendee reactions, see [Schedule a town hall in Microsoft Teams](https://support.microsoft.com/office/schedule-a-town-hall-in-microsoft-teams-d493b5cc-9f61-4dac-8027-d837dafb7a4c#bkmk_townhall_reactions).

## Manage reactions

By default, meeting reactions are set to **On** in your organizers' **Meeting options**.

### Teams admin center

To manage the default value for meeting reactions through the Teams admin center, follow these steps:

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
1. Select the policy that you want to edit.
1. Scroll to the **Meeting engagement** section.
1. Toggle the **Reactions** setting **On** or **Off**.
1. Select **Save**

### PowerShell

You can use PowerShell to manage the default value for meeting reactions through the **`-AllowMeetingReactions`** parameter within the [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet.

To set the default for meeting reactions to **Off** for organizers with this policy, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowMeetingReactions Disabled
```

## Related topics

- [Express yourself in Teams meetings with live reactions](https://support.microsoft.com/office/a8323a40-3d07-4129-934b-305370a36e21)
- [Plan for Teams town halls](plan-town-halls.md)
- [Teams policy reference](settings-policies-reference.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
