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

Each policy type in Teams includes a built-in global (Org-wide default) policy that users automatically get unless you create and assign a custom policy. Organizations have different types of users with unique needs and policies that you create and assign let you tailor policy settings to different sets of users based on those needs.

To make it easier to manage policies in your organization, Teams offers several ways to assign policies to users. The option that you choose depends on the number of policies that you're assigning and the number of users that you're assigning to. This article describes the different ways that you can assign policies to users and the recommended scenarios for when to use what.

## Overview

Here's an overview of the ways that you can assign policies to users and the recommended scenarios for each. Click the links to learn more.

|Do this  |If...  |
|---------|---------|
|[Assign a policy to individual users](#assign-a-policy-to-individual-users)    | You're new to Teams and just getting started or you only need to assign one or a couple of policies to a small number of users.       |
| [Assign a policy package](#assign-a-policy-package)    | You need to assign multiple policies to specific sets of users in your organization who have the same or similar roles. For example, assign the Education_Teacher policy package to teachers in your school to give them full access to chats, calling, and meetings and assign the Education_SecondaryStudent policy package to limit capabilities like meetings creation, chat management, and private calling for secondary students.  |
|[Assign a policy to a batch of users](#assign-a-policy-to-a-batch-of-users)    | You need to assign policies to large sets of users. For example, you want to assign a policy to hundreds or thousands of users in your organization at a time.   |
|[Assign a policy to a group](#assign-a-policy-to-a-group)    |You need to assign policies based on a user's group membership. For example, you want to assign a policy to all users in a security group or organizational unit.       |

## Assign a policy to individual users

Follow these steps to assign a policy to an individual user or to a small number of users at a time.

### Using the Microsoft Teams admin center

To assign a policy to a user:

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

### Using PowerShell

Each policy type has it's own set of cmdlets for managing it. Use the **Grant-** cmdlet for a given policy type to assign the policy. For example, use the ```Grant-CsTeamsMeetingPolicy``` cmdlet to assign a Teams meeting policy to users. These cmdlets are included in Skype for Business Online PowerShell module and are documented in the [Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps).

 Download and install the [Skype for Business Online PowerShell module](https://www.microsoft.com/en-us/download/details.aspx?id=39366) (if you haven't already), and then run the following to connect to Skype for Business Online and start a session.

```
Import-Module SkypeOnlineConnector
$Cred = Get-Credential
$CSSession = New-CsOnlineSession -Credential $Cred
Import-PSSession -Session $CSSession
```

In this example, we assign a policy named New Hire Feedback Policy to a user named user1.

```
Grant-CsTeamsFeedbackPolicy -Identity user1@contoso.com -PolicyName "New Hire Feedback Policy"
```

To learn more, see [Managing policies via PowerShell](teams-powershell-overview.md#managing-policies-via-powershell).

## Assign a policy package

A policy package in Teams is a collection of predefined policies and policy settings that you can assign to users who have the same or similar roles in your organization. Each policy package is designed around a user role and includes predefined policies and policy settings that support activities typical for that role. Some examples of policy packages are the Education_Teacher package and the SmallMediumBusiness_BusinessVoice package.

When you assign a policy package to users, the policies in the package are created and you can then customize the settings of each policy in the package to meet users' needs.

To learn more about policy packages, including step-by-step guidance on how to assign and manage them, see [Manage policy packages in Teams](manage-policy-packages.md).

## Assign a policy to a batch of users
 
With batch policy assignment, you can assign a policy to large sets of users at a time without having to use a script. You use the [New-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicyassignmentoperation) cmdlet to submit a batch of users and the policy that you want to assign. The assignments are processed as a background operation and an operation Id is generated for each batch.

You can then use the [Get-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/get-csbatchpolicyassignmentoperation) cmdlet to track the progress and status of the assignments in a batch.

A batch can contain up to 20,000 users. You can specify users by their object Id, user principal name (UPN), Session Initiation Protocol (SIP) address, or email address.

> [!NOTE]
> Currently, batch policy assignment isn't available for all Teams policy types. See [New-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicyassignmentoperation) for the list of supported policy types.

### Install and connect to the Microsoft Teams PowerShell module

If you haven't already, download and install the [Microsoft Teams Powershell module](https://www.powershellgallery.com/packages/MicrosoftTeams), and then run the following to connect to Teams and start a session.

```
Connect-MicrosoftTeams
```

When you're prompted, sign in using your admin credentials.

### Install and connect to the Azure AD PowerShell for Graph module (optional)

You may also want to [download and install the Azure AD PowerShell for Graph module](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) (if you haven't already) and connect to Azure AD so that you can retrieve a list of users in your organization.

Run the following to connect to Azure AD.

```
Connect-AzureAD
```

When you're prompted, sign in using the same admin credentials that you used to connect to Teams.

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

## Assign a policy to a group

Group policy assignment lets you assign a policy to a group of users, such as a security group or organizational unit. The policy assignment is propagated to members of the group according to inheritance rules.  When the membership of a group that's assigned the policy changes or when a policy is removed from a group, the users' policies are updated according to precedence rules.

> [!NOTE]
> Currently, group policy assignment isn't available for all Teams policy types. See [New-GroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/new-csgrouppolicyassignment) for the list of supported policy types.

### What you need to know about group policy assignment

#### Effective policy rules of precedence

Every user has one effective policy for each policy type. For a given policy type, a user's effective policy is determined according to the following:

1. Direct policy assignment: A policy that's directly assigned to a user takes precedence over any
policy of the same type that would be inherited through membership in a group. This lets you
override group-assigned policies for specific users, as needed.
2. Group policy inheritance: If a user doesn't have a policy directly assigned to them and is a
member of one or more groups that have a policy of the given type assigned, the user inherits
the effective policy from one of the groups based on the group assignment priority.
3. Global policy: If a user doesn't have a policy directly assigned to them and hasn't
inherited a policy from a group, their effective policy is the global policy for that policy type, if defined.
4. System default policy: If the global policy isn't defined, a user’s effective 
is the system default policy for that policy type.

#### Group assignment priority
 
When you assign a policy to a group, set a priority. The priority indicates which group membership is more important or more relevant than other group memberships with regards to policy inheritance.
 
Say, for example, an organization has two groups, Store Employees and Store Managers. Both groups are assigned a Teams calling policy, Store Employees Calling Policy and Store Managers Calling Policy. For a store manager who is in both groups, their role as a manager is more relevant than their role as an employee, so the calling policy that's assigned to the Store Managers group should take precedence.

If you don't set a priority, the policy assignment is given the lowest priority. 

### Assign a policy to a group

### Get policy assignments for a group

### Remove a policy from a group

### Update a policy assignment for a group

### Get the policies for a user

### Get the status of initial policy propagation

## Related topics

- [Manage policy packages in Teams](manage-policy-packages.md)
- [Teams PowerShell Overview](teams-powershell-overview.md)