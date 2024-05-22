---
title:  Prevent users from joining external Microsoft Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: vivekmo
ms.date: 5/8/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
description: Learn how to prevent or block users in your organization from joining external meetings for IT Admins in Microsoft Teams. 
---

# Prevent users from joining external Microsoft Teams meetings

**APPLIES TO:** ✔️Meetings ✖️Webinars ✖️Town halls

As an admin, you can control which types of Microsoft Teams meetings users in your org can join. Managing the types of meetings your users can join can be helpful in privacy and compliance scenarios, where you might not want specific users or groups in your org joining meetings with external non-trusted trusted or even trusted organizations.

To learn more about trusted organizations, see [IT Admins - Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md).

The following table describes how different roles in Teams interact with this policy:

|User role| Policy effect|
|---------|---------------|
|Trusted org participant| When this policy is set to **Anyone** or **Only people in trusted orgs**, users in your org can join meetings that trusted organizations (as defined in External access) host. <br><br> When this policy is set to **No one**, users in your org can't join externally hosted Teams meetings while using your org’s accounts. However, your users can still join external meetings as anonymous if they aren’t logged in to Teams. |
|Guest| This policy doesn’t affect meetings in other organizations where your users are signed in as guests.|
|Anonymous| This policy doesn't prevent users from joining external meeting anonymously if they’re not signed into Teams.|
|External participant in a shared channel meeting| This policy doesn't prevent users from joining external shared channel meetings.|

## Manage the types of meetings your users can join

You can manage the types of meetings your users can join through the Teams admin center or PowerShell.

|Teams admin center policy option|Parameter value in PowerShell| Behavior|
|---------|---------|---------------|
|Anyone|EnabledForAnyone| **This is the default value.** Users with this policy can join any meeting they’re invited to. |
|Only people in trusted orgs|EnabledForTrustedOrgs| Users with this policy can only join in org meetings and meetings that organizations you have a trusted relationship with host.|
|No one|Disabled| Users with this policy can only join in org meetings.|

### Prevent users from joining external meetings using the Teams admin center

Follow these steps in the Teams admin center to manage the types of meetings your users can join:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Expand **Meetings** and select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Navigate to the **Meeting join & lobby** section.
6. Set **People can join external meetings hosted by** to your chosen value of either **Anyone**, **Only people in trusted orgs**, or **No one**.
7. Select **Save**

### Prevent users from joining external meetings using PowerShell

You can use the **`-ExternalMeetingJoin`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet to manage the types of external meetings your users can join.

Before you can run these cmdlets, you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

For more information on PowerShell cmdlets for Teams meetings, see the [Related topics](#related-topics) section.

For users to only join meetings that are in org or hosted by orgs that you have a trusted relationship with, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -ExternalMeetingJoin  EnabledForTrustedOrgs
```

To only allow users to join in org meetings, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -ExternalMeetingJoin  Disabled
```

## Related topics

- [Plan for meetings with external participants in Microsoft Teams](plan-meetings-external-participants.md)
- [Plan for meetings](plan-meetings.md)
- [Meetings, webinars, and live events overview](quick-start-meetings-live-events.md)
- [Feature comparison](meeting-webinar-town-hall-feature-comparison.md)
- [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy)
- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
- [Grant-CsTeamsMeetingPolicy](/powershell/module/teams/grant-csteamsmeetingpolicy)
- [Get-CsTeamsMeetingPolicy](/powershell/module/teams/get-csteamsmeetingpolicy)
- [Remove-CsTeamsMeetingPolicy](/powershell/module/teams/remove-csteamsmeetingpolicy)
