---
title: Remove the RestrictedAnonymousAccess Teams meeting policy from users 
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: cebulnes
audience: admin
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
ms.custom: 
description: Learn how to remove the RestrictedAnonymousAccess Teams meeting policy from users in your organization.
---
# Remove the RestrictedAnonymousAccess Teams meeting policy from users

[Meeting policies](meeting-policies-in-teams.md) in Microsoft Teams are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization. 

Teams includes a built-in policy named RestrictedAnonymousAccess, which contains pre-defined settings that include restricting anonymous users from starting a meeting. (Anonymous users are users who haven't been authenticated.) These predefined settings in the meeting policy can't be edited or changed by admins. 

This article shows you how to remove the RestrictedAnonymousAccess meeting policy from users who are assigned this policy. For example, you may want to do this if...???

## Before you start

Install and connect to the [Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams) and the [Skype for Business PowerShell module](https://www.microsoft.com/download/details.aspx?id=39366). For step-by-step guidance, see [Install Microsoft Teams PowerShell](teams-powershell-install.md). 

To learn more about how to manage Teams using PowerShell, see [Teams PowerShell overview](teams-powershell-overview.md).

## Get the Teams meeting policy assignments for your organization

Run the following to get the Teams meeting policy assignments for your organization.

```powershell
Get-CsOnlineUser | Select-Object objectid, TeamsMeetingPolicy | Group-Object TeamsMeetingPolicy
```

In this example, we get the following output, which shows that two users are assigned the RestrictedAnonymousAccess meeting policy.

:::image type="content" source="media/restricted-anonymous-access.png" alt-text="Screenshot of output of Get-CsOnlineUser command":::

## Unassign the RestrictedAnonymous meeting policy from users

To remove the the RestrictedAnonymous meeting policy from users, you can use the [Grant-CSTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsmeetingpolicy) cmdlet if you have a small number of users (up to 100 users). If you have a large number of users (more than 100 users), it's more efficient to use the  [New-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicyassignmentoperation?view=teams-ps) cmdlet to submit a batch operation.

### Use the Grant-CsTeamsMeeting Policy cmdlet

Run the following to remove the RestrictedAnonymous meeting policy from users.

```powershell
Get-CsOnlineUser | Select-Object objectid, TeamsMeetingPolicy | Group-Object TeamsMeetingPolicy
```

### Use the New-CsBatchPolicyAssignmentOperation cmdlet

With [batch policy assignment](assign-policies.md#assign-a-policy-to-a-batch-of-users), the maximum number of users for which you can remove or update policies is 5,000 at a time. For example, if you have more than 5,000 users, you'll need to submit multiple batches. For best results, do not submit more than a few batches at a time. Allow batches to complete processing before submitting more batches. 

Run the following commands to remove the RestrictedAnonymousAccess meeting policy from a batch of users.

```powershell
$restrictedAnonymousUsers = @(Get-CsOnlineUser |? TeamsMeetingPolicy -eq "RestrictedAnonymousAccess" | %{ $_.ObjectId })
```

```powershell
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsMeetingPolicy -PolicyName $null -Identity $restrictedAnonymousUsers -OperationName "Batch unassign meeting policy"
```

#### Get the status of the batch assignment

Each batch assignment returns an operation ID, which you can use to track the progress and status of the assignments and identify any failures that might occur. For example, run the following:

```powershell
Get-CsBatchPolicyAssignmentOperation -OperationId 62557b78-e734-42d6-952f-41a454ed6115
```

Make sure the **ErrorCount** is **0** (zero) and **OverallStatus** is **Completed**.

## Related topics

- [Manage meeting policies in Teams](meeting-policies-in-teams.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies to your users in Teams](assign-policies.md)
