---
title:  Prevent users from joining external Microsoft Teams meetings
ms.author: wlibebe
author: wlibebe
manager: serdars
ms.reviewer: vivekmo
ms.date: 11/13/2023
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

As an admin, you can control which types of Microsoft Teams meetings your users can join. Managing the types of meetings users can join can be helpful in privacy and compliance scenarios, where you might not want specific users or groups in your org joining meetings with trusted or nontrusted organizations.

To learn more about trusted organizations, see [IT Admins - Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md).

The following table describes how different roles in Teams interact with this policy.

|User role| Policy effect|
|---------|---------------|
|Trusted org participant| When this policy is set to Anyone or Only people in trusted orgs, users can join meetings with trusted organizations defined in external access. When this policy is set to No one, users can still join these meetings as anonymous if they aren’t logged in to Teams. |
|Guest| This policy doesn’t affect meetings in other organizations where your users are signed in as guests.|
|Anonymous| This policy doesn't prevent users from joining external meeting anonymously if they’re not signed into Teams.|
|External participant in a shared channel meeting| This policy doesn't prevent users from joining external shared channel meetings.|

## Manage the types of meetings your users can join

You can manage the types of meetings your users can join through the Teams admin center or PowerShell.

### Prevent users from joining external meetings using the Teams admin center

Follow these steps in the Teams admin center to turn town halls on or off:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Navigate to the **Meeting join & lobby** section.
6. Set **People can join external meetings hosted by** to your chosen value of either **Anyone**, **Only people in trusted orgs**, or **No one**.
7. Select **Save**

### Prevent users from joining external meetings using PowerShell

You can use the **`-JoinMeetingsHostedAt`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet to manage the types of external meetings your users can join.
The following table shows the behaviors of the settings for the **`-JoinMeetingsHostedAt`** parameter:

|Setting value| Behavior|
|---------|---------------|
|All| **This is the default.**Users with this policy can join any meeting they’re invited to. |
|Current&TrustedOrgs| Users with this policy can only join in org meetings and meetings that organizations you have a trusted relationship with host.|
|CurrentOrgOnly| Users with this policy can only join in org meetings.|

Before you can run these cmdlets, you must be connected to Microsoft Teams PowerShell. For more information, see [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams).

For more information on PowerShell cmdlets for Teams meetings, see the [Related topics](#related-topics) section.

For users to only join meetings that are in org or hosted by orgs that you have a trusted relationship with, run the following script, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -JoinMeetingsHostedAt  Current&TrustedOrgs
```

To only allow users to join in org meetings, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -JoinMeetingsHostedAt  CurrentOrgOnly
```

## Related topics

- [Plan for meetings with external participants in Microsoft Teams](plan-meetings-external-participants.md)
- [Plan for meetings](plan-meetings.md)
- [Meetings, webinars, and live events overview](quick-start-meetings-live-events.md)
- [Feature comparison](meeting-webinar-town-hall-feature-comparison.md)
- [New-CsTeamsMeetingPolicy](/powershell/module/skype/new-csteamsmeetingpolicy)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
- [Grant-CsTeamsMeetingPolicy](/powershell/module/skype/grant-csteamsmeetingpolicy)
- [Get-CsTeamsMeetingPolicy](/powershell/module/skype/get-csteamsmeetingpolicy)
- [Remove-CsTeamsMeetingPolicy](/powershell/module/skype/remove-csteamsmeetingpolicy)
