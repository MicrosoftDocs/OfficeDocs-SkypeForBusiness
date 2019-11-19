---
title: Assign policies to your users in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: tomkau, saragava
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to assign policies to your users in Microsoft Teams.
f1keywords: 
---

# Assign policies to your users in Microsoft Teams

As an admin, you use policies to control how users in your organization use Microsoft Teams to communicate and collaborate. For example, you can set app policies to control what apps are available to Teams users, meeting policies to define the meeting experience, and messaging policies to control what chat and channel features are available to users.

You can use the built-in global (Org-wide default) policy or create custom policies and assign them to users. Users in your organization will automatically get the global policy unless you create and assign a custom policy. To customize Teams for different groups of users in your organization, create and assign one or more custom policies. If a user is assigned a custom policy, that policy applies to the user. If a user isn't assigned a custom policy, the global policy applies to the user.

You can use the Microsoft Teams admin center to assign a policy to users or [Teams PowerShell module](teams-powershell-overview.md) cmdlets to assign a policy to multiple users at a time or to users in a group, such as a security group.

+++++++++++++++++++++++++++++++++++++

## Assign a policy to individual users

Here are steps for how to assign a policy to users in the Microsoft Teams admin center. Use these steps if you're assigning a policy to individual users or a small number of users at a time.

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click the user.
2. Select the user by clicking to the left of the user name, and then click **Edit settings**.
3. Select the policy you want to assign, and then click **Apply**.

To assign a policy to up to 20 users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md).

Or, you can also do the following:

1. In the left navigation of the Microsoft Teams admin center, go to the policy page.
2. Select the policy you want to assign by clicking to the left of the policy name.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.
5. When you're finished adding users, select **Save**.

++++++++++++++++++++++++++++++++++++

## Before you start

### Install and connect to the Microsoft Teams PowerShell module

Download the [Microsoft Teams Powershell module](https://www.powershellgallery.com/packages/MicrosoftTeams), and then follow these steps to install the module and connect to Teams.

Run the following to install the Teams Powershell module.

```
Install-Module -Name MicrosoftTeams
```
Run the following to connect to Teams and start a session.

```
Connect-MicrosoftTeams
```

When you're prompted, sign in using your admin credentials.

### Install and connect to the Azure AD PowerShell for Graph module (optional)

You may also want to [download and install the Azure AD PowerShell for Graph module](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2)(if it's not already installed) and connect to Azure AD so that you can retrieve a list of users in your organization.

Run the following to connect to Azure AD.

```
Connect-AzureAD
```

When you're prompted, sign in using the same admin credentials that you used to connect to Teams.

## Batch policy assignment
 
With batch policy assignment, you can assign a policy to multiple users at a time without having to use a script. You use the [New-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicyassignmentoperation) cmdlet to submit a batch of users and the policy that you want to assign. The assignments are processed as a background operation and an operation Id is generated for each batch.

You can then use the [Get-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/get-csbatchpolicyassignmentoperation) cmdlet to track the progress and status of the assignments in a batch.

You can specify users by their object Id, user principal name (UPN), Session Initiation Protocol (SIP) address, or email address. A batch can contain up to 20,000 users.

> [!NOTE]
> Currently, batch policy assignment isn't available for all Teams policy types. See [New-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicyassignmentoperation) for the list of supported policy types.

### Assign a policy to a batch of users

In this example, we assign an app setup policy named HR App Setup Policy to a batch of users listed in the Users_ids.text file.

```
$user_ids = Get-Content .\users_ids.txt
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsAppSetupPolicy -PolicyName "HR App Setup Policy" -Identity $users_ids -OperationName "Example 1 batch"
```

In this example, we assign a meeting policy named Vendor Meetings to a batch of users using their email addresses.

```
$users_ids = @("psmith@contoso.com","tsanchez@contoso.com","bharvest@contoso.com")
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsMeetingPolicy -PolicyName "Vendor Meetings" -Identity $users_ids -OperationName "Example 1 batch"
```

In this example, we connect to Azure AD to retrieve a collection of users and then assign a messaging policy named Kiosk to a batch of users specified by using their UPNs.

```
Connect-AzureAD
$users = Get-AzureADUser
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsMessagingPolicy -PolicyName Kiosk -Identity $users.UserPrincipalName -OperationName "Example 1 batch"
```

### Get the status of a batch assignment

Run the following to get the status of a batch assignment, where OperationId is the operation Id that's returned by the New-CsBatchPolicyAssignmentOperation cmdlet for a given batch.

```
$Get-CsBatchPolicyAssignmentOperation -OperationId f985e013-0826-40bb-8c94-e5f367076044 | fl 
```

Here's an example of the output that you see

## Group policy assignment

> [!NOTE]
> Currently, group policy assignment isn't available for all Teams policy types. See [New-GroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/new-csgrouppolicyassignment) for the list of supported policy types.

### What you need to know about group policy assignment

#### Effective policy rules of precedence

#### Group assignment priority

### Assign a policy to a group

### Get policy assignments for a group

### Remove a policy from a group

### Update a policy assignment for a group

### Get the policies for a user

### Get the status of initial policy propagation

## Related topics

- [Manage policy packages in Teams](manage-policy-packages.md)
- [Teams PowerShell Overview](teams-powershell-overview.md)