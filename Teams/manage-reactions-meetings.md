--- 
title: Manage reactions in Teams meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 03/15/2021
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

# Manage reactions in Teams meetings

The availability of reactions can be configured through either the Teams admin center interface or using PowerShell. Reactions are enabled by default. This setting also controls the hand raise feature.

This setting sets the default for new meetings. Meeting organizers can change the setting for each meeting that they create.

To set the default for meeting reactions in new meetings
1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
1. Select the policy that you want to edit.
1. Scroll to the **Meeting engagement** section.
1. Set **Reactions** to **On** or **Off**.
1. Select **Save**.

To configure the setting in PowerShell, use the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet. To turn it off, set **AllowMeetingReactions** to **False**.

## Related topics

[Teams policy reference](settings-policies-reference.md)

[Assign policies to your users in Teams](policy-assignment-overview.md)

[Teams PowerShell overview](teams-powershell-overview.md)

[Express yourself in Teams meetings with live reactions](https://support.microsoft.com/office/a8323a40-3d07-4129-934b-305370a36e21)