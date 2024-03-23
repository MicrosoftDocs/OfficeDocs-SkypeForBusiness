---
title: Meeting provider for Islands mode
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: lsomi
ms.date: 03/05/2024
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
description: Learn to use the Teams Meeting add-in or both the Teams Meeting and Skype for Business Meeting add-ins to schedule meetings in Outlook.
---

# Meeting provider for Islands mode

Islands mode allows users to run Teams alongside Skype for Business with similar functionality available in both clients.

As an admin, you can use this per-user policy to control which Outlook meeting add-in is used for users who are in Islands mode. You can specify whether users can only use the Teams Meeting add-in or both the Teams Meeting and Skype for Business Meeting add-ins to schedule meetings in Outlook.

You can only apply this policy to users who are in Islands mode and have the -**`AllowOutlookAddIn`** parameter set to **True** in their Teams meeting policy. To learn more about the Outlook add-in, see [Admin - authentication requirements and functionality of the Teams Meeting add-in in Outlook](outlook-add-in-authentication-policy-requirements.md).

## Manage the meeting provider for Islands mode with PowerShell

You must use the -**`PreferredMeetingProviderForIslandsMode`** parameter in PowerShell to control which Outlook meeting add-in is used for users who are in Islands mode. You can edit an existing Teams meeting policy by using the [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet. Or, create a new Teams meeting policy by using the [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy) cmdlet and assign it to users.

To specify which meeting add-in you want to be available to users, set the -**`PreferredMeetingProviderForIslandsMode`** parameter as follows:

### TeamsAndSfB

**This setting is the default value.** To enable both the Teams Meeting add-in and Skype for Business add-in in Outlook for users with this policy, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -PreferredMeetingProviderForIslandsMode TeamsAndSfB
```

If you set the value to **Teams**, and then switch back to **TeamsAndSfB**, both meeting add-ins are enabled. However, existing Teams meeting join links aren't migrated to Skype for Business. Only Skype for Business meetings scheduled after the change have a Skype for Business meeting join link.

### Teams

To only enable the Teams Meeting add-in in Outlook for users with this policy, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -PreferredMeetingProviderForIslandsMode Teams
```

The **Teams** value ensures that all future meetings have a Teams meeting join link, but doesn't migrate existing Skype for Business meeting join links to Teams. This value doesn't affect presence, chat, Public Switched Telephone Network (PSTN) calling, or any other capabilities in Skype for Business, allowing users to keep using Skype for Business for these capabilities.

## Related topics

- [Teams policies reference](settings-policies-reference.md#meetings)
- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies in Teams](policy-assignment-overview.md)
