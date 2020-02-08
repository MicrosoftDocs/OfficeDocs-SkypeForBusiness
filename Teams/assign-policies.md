---
title: Assign policies to your users in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: tomkau, saragava, ritikag
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
description: Learn the different ways to assign policies to your users in Microsoft Teams.
f1keywords: 
---

# Assign policies to your users in Microsoft Teams

As an admin, you use policies to control the Microsoft Teams features that are available to users in your organization. For example, you can set app policies to control what apps are available to Teams users, meeting policies to define the meeting experience, and messaging policies to control what chat and channel features are available to users.

Organizations have different types of users with unique needs and custom policies that you create and assign let you tailor policy settings to different sets of users based on those needs.

To make it easier to manage policies in your organization, Teams offers several ways to assign policies to users. You can assign a policy directly to users, either individually or at scale through a batch assignment, or to a group that the user is a member of. You can also use policy packages to assign a preset collection of policies to users in your organization who have similar roles. The option that you choose depends on the number of policies that you're managing and the number of users that you're assigning to.

This article describes the different ways that you can assign policies to users and the recommended scenarios for when to use what.

## Which policy takes precedence?

A user has one effective policy for each policy type. It's possible or even likely that a user is directly assigned a policy and is also a member of one or more groups that's assigned a policy of the same type. In these kinds of scenarios, which policy takes precedence?

A user's effective policy is determined according to rules of precedence, as follows.  

If a user is directly assigned a policy (either individually or through a batch assignment), that policy takes precedence. If the user isn't directly assigned a policy of a given type, the policy assigned to a group that the user is a member of takes precedence. If a user is a member of multiple groups, the policy that has the highest [group assignment priority](#group-assignment-priority) for the given policy type takes precedence. If a user isn't a member of any groups that are assigned a policy, the user gets the global (Org-wide default) policy for that policy type. To learn more, see [Precedence rules](#precedence-rules).

The following diagrams show examples of how these rules are applied. The check mark in each diagram indicates a user's effective policy.

## Ways to assign policies

Here's an overview of the ways that you can assign policies to users and the recommended scenarios for each. Click the links to learn more.

|Do this  |If...  | Using...
|---------|---------|----|
|[Assign a policy to individual users](#assign-a-policy-to-individual-users)    | You're new to Teams and just getting started or you only need to assign one or a couple of policies to a small number of users. |The Microsoft Teams admin center or PowerShell cmdlets in the Skype for Business Online PowerShell module
| [Assign a policy package](#assign-a-policy-package)   | You need to assign multiple policies to specific sets of users in your organization who have the same or similar roles. For example, assign the Education (Teacher) policy package to teachers in your school to give them full access to chats, calling, and meetings and the Education (Secondary school student) policy package to secondary students to limit certain capabilities like private calling.  |The Microsoft Teams admin center or PowerShell cmdlets in the Teams PowerShell module|
|[Assign a policy to a batch of users](#assign-a-policy-to-a-batch-of-users)    | You need to assign policies to large sets of users. For example, you want to assign a policy to hundreds or thousands of users in your organization at a time.  |PowerShell cmdlets in the Teams PowerShell module|
|[Assign a policy to a group](#assign-a-policy-to-a-group)    |You need to assign policies based on a user's group membership. For example, you want to assign a policy to all users in a security group or organizational unit.| PowerShell cmdlets in the Teams PowerShell module|
| Assign a policy package to a batch of users (coming soon) |||
| Assign a policy package to a group (coming soon)   | ||

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

Each policy type has it's own set of cmdlets for managing it. Use the ```Grant-``` cmdlet for a given policy type to assign the policy. For example, use the ```Grant-CsTeamsMeetingPolicy``` cmdlet to assign a Teams meeting policy to users. These cmdlets are included in the Skype for Business Online PowerShell module and are documented in the [Skype for Business cmdlet reference](https://docs.microsoft.com/powershell/skype/intro?view=skype-ps).

 Download and install the [Skype for Business Online PowerShell module](https://www.microsoft.com/en-us/download/details.aspx?id=39366) (if you haven't already), and then run the following to connect to Skype for Business Online and start a session.

```
Import-Module SkypeOnlineConnector
$Cred = Get-Credential
$CSSession = New-CsOnlineSession -Credential $Cred
Import-PSSession -Session $CSSession
```

In this example, we assign a Teams feedback policy named New Hire Feedback Policy to a user named user1.

```
Grant-CsTeamsFeedbackPolicy -Identity user1@contoso.com -PolicyName "New Hire Feedback Policy"
```

To learn more, see [Managing policies via PowerShell](teams-powershell-overview.md#managing-policies-via-powershell).

## Assign a policy package

A policy package in Teams is a collection of predefined policies and policy settings that you can assign to users who have the same or similar roles in your organization. Each policy package is designed around a user role and includes predefined policies and policy settings that support activities typical for that role. Some examples of policy packages are the Education (Teacher) package and Healthcare (Clinical worker) package.

When you assign a policy package to users, the policies in the package are created and you can then customize the settings of each policy in the package to meet users' needs.

To learn more about policy packages, including step-by-step guidance on how to assign and manage them, see [Manage policy packages in Teams](manage-policy-packages.md).

## Assign a policy to a batch of users
 
With batch policy assignment, you can assign a policy to large sets of users at a time without having to use a script. You use the ```New-CsBatchPolicyAssignmentOperationd``` cmdlet to submit a batch of users and the policy that you want to assign. The assignments are processed as a background operation and an operation Id is generated for each batch. You can then use the ```Get-CsBatchPolicyAssignmentOperation``` cmdlet to track the progress and status of the assignments in a batch.

A batch can contain up to 20,000 users. You can specify users by their object Id, user principal name (UPN), Session Initiation Protocol (SIP) address, or email address.

> [!NOTE]
> Currently, batch policy assignment isn't available for all Teams policy types. See [New-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicyassignmentoperation) for the list of supported policy types.

### Install and connect to the Microsoft Teams PowerShell module

> [!NOTE]
> The cmdlets are in the pre-release version of the Teams PowerShell module. Follow these steps to first uninstall the Generally Available version of the Teams PowerShell module (if it's installed), and then install the latest pre-release version of the module from the PowerShell Test Gallery.

If you haven't already, run the following to register the PowerShell Test Gallery as a trusted source.

```
Register-PSRepository -SourceLocation https://www.poshtestgallery.com/api/v2 -Name PsTestGallery -InstallationPolicy Trusted
```

If you have the Generally Available version of the Teams PowerShell module installed, run the following to uninstall it.

```
Uninstall-Module MicrosoftTeams -AllVersions
```

Run the following to install the latest Microsoft Teams PowerShell module from the PowerShell Test Gallery.

```
Install-Module MicrosoftTeams -Repository PSTestGallery
```

Run the following to connect to Teams and start a session.

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

In this example, we use ```New-CsBatchPolicyAssignmentOperation``` to assign an app setup policy named HR App Setup Policy to a batch of users listed in the Users_ids.text file.

```
$user_ids = Get-Content .\users_ids.txt
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsAppSetupPolicy -PolicyName "HR App Setup Policy" -Identity $users_ids -OperationName "Example 1 batch"
```

In this example, we connect to Azure AD to retrieve a collection of users and then assign a messaging policy named Kiosk to a batch of users specified by using their UPNs.

```
Connect-AzureAD
$users = Get-AzureADUser
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsMessagingPolicy -PolicyName Kiosk -Identity $users.UserPrincipalName -OperationName "Example 2 batch"
```

To learn more, see [New-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicyassignmentoperation).

### Get the status of a batch assignment

Run the following to get the status of a batch assignment, where OperationId is the operation Id that's returned by the ```New-CsBatchPolicyAssignmentOperation``` cmdlet for a given batch.

```
$Get-CsBatchPolicyAssignmentOperation -OperationId f985e013-0826-40bb-8c94-e5f367076044 | fl
```

If the output shows that an error occurred, run the following to get more information about errors, which are in the ```UserState``` property.

```
Get-CsBatchPolicyAssignmentOperation -OperationId f985e013-0826-40bb-8c94-e5f367076044 | Select -ExpandProperty UserState
```

To learn more, see [Get-CsBatchPolicyAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/get-csbatchpolicyassignmentoperation).

## Assign a policy to a group

Group policy assignment lets you assign a policy to a group of users, such as a security group or organizational unit. The policy assignment is propagated to members of the group according to precedence rules. As members are added to or removed from a group, their inherited policy assignments are updated accordingly.

You use the ```New-CsGroupPolicyAssignment``` cmdlet to assign a policy to a group. You can specify a group by using the object Id, SIP address, or email address. The cmdlet returns an operation Id that you can use together with the ```Get-CsBatchPolicyAssignmentOperation``` cmdlet to check the status of the propagation of the policy to members of the group.

When you assign the policy, it's immediately assigned to the group. However, note that the propagation of the policy assignment to members of the group is performed as a background operation and may take some time, depending on the size of the group. The same is true when a policy is unassigned from a group, or when members are added to or removed from a group.

> [!NOTE]
> Currently, group policy assignment isn't available for all Teams policy types. See [New-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/new-csgrouppolicyassignment) for the list of supported policy types.

### What you need to know about group policy assignment

Before you get started, it's important to understand precedence rules and group policy assignment priority.

#### Precedence rules

For a given policy type, a user's effective policy is determined according to the following:

- A policy that's directly assigned to a user takes precedence over any other policy of the same type that's assigned to a group. In other words, if a user is directly assigned a policy of a given type, that user won't inherit a policy of the same type from a group. This also means that if a user has a policy of a given type that was directly assigned to them, you have to remove that policy from the user before they can inherit a policy of the same type from a group.
- If a user doesn't have a policy directly assigned to them and is a member of two or more groups and each group has a policy of the same type assigned to it, the user inherits the policy of the group assignment that has the highest priority.
- If a user isn't a member of any groups that are assigned a policy, the global (Org-wide default) policy for that policy type applies to the user.

A user's effective policy is updated according to these rules when a user is added to or removed from a group that's assigned a policy, a policy is unassigned from a group, or a policy that's directly assigned to the user is removed.

#### Group assignment priority
 
When you assign a policy to a group, you set a priority for the group assignment. This is used to determine which policy a user should inherit as their effective policy if the user is a member of two or more groups and each group is assigned a policy of the same type.

The group assignment priority is relative to other group policy assignments of the same type. For example, if you're assigning a calling policy to two groups, set the priority of one assignment to 1 and the other to 2, with 1 being the highest priority. The group assignment priority indicates which group membership is more important or more relevant than other group memberships with regards to inheritance.
 
Say, for example, you have two groups, Store Employees and Store Managers. Both groups are assigned a Teams calling policy, Store Employees Calling Policy and Store Managers Calling Policy, respectively. For a store manager who is in both groups, their role as a manager is more relevant than their role as an employee, so the calling policy that's assigned to the Store Managers group should have a higher priority.

|Group |Teams calling policy name  |Priority|
|---------|---------|---|
|Store Managers   |Store Managers Calling Policy         |1|
|Store Employees    |Store Employees Calling Policy      |2|

If you don't set a priority, the policy assignment is given the lowest priority.

### Install and connect to the Microsoft Teams PowerShell module

> [!NOTE]
> The cmdlets are in the pre-release version of the Teams PowerShell module. Follow these steps to first uninstall the Generally Available version of the Teams PowerShell module (if it's installed), and then install the latest pre-release version of the module from the PowerShell Test Gallery.

If you haven't already, run the following to register the PowerShell Test Gallery as a trusted source.

```
Register-PSRepository -SourceLocation https://www.poshtestgallery.com/api/v2 -Name PsTestGallery -InstallationPolicy Trusted
```

If you have the Generally Available version of the Teams PowerShell module installed, run the following to uninstall it.

```
Uninstall-Module MicrosoftTeams -AllVersions
```

Run the following to install the latest Microsoft Teams PowerShell module from the PowerShell Test Gallery.

```
Install-Module MicrosoftTeams -Repository PSTestGallery
```

Run the following to connect to Teams and start a session.

```
Connect-MicrosoftTeams
```

When you're prompted, sign in using your admin credentials.

### Assign a policy to a group

In this example, we use the ```New-CsGroupPolicyAssignment``` cmdlet to assign a Teams meeting policy named AllOn to a group with an assignment priority of 1.

```
New-CsGroupPolicyAssignment -GroupId d8ebfa45-0f28-4d2d-9bcc-b158a49e2d17 -PolicyType TeamsMeetingPolicy -PolicyName AllOn -Priority 1 dc4beaf9-5ca7-4148-a942-1652d5d0f7a6
```

To learn more, see [New-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/new-csgrouppolicyassignment).

### Get policy assignments for a group

Use the ```Get-CsGroupPolicyAssignment``` cmdlet to get all policies assigned to a group. Note that groups are always listed by their group Id even if its SIP address or email address was used to assign the policy.

In this example, we retrieve all policies assigned to a specific group.

```
Get-CsGroupPolicyAssignment -GroupId e050ce51-54bc-45b7-b3e6-c00343d31274
```

In this example, we return all groups that are assigned a Teams meeting policy.

```
Get-CsGroupPolicyAssignment -PolicyType TeamsMeetingPolicy
```

To learn more, see [Get-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/get-csgrouppolicyassignment).

### Remove a policy from a group

Use the ```Remove-CsGroupPolicyAssignment``` cmdlet to remove a policy from a group. When you remove a policy from a group, the priorities of other policies of the same type assigned to that group and that have a lower priority are updated. For example, if you remove a policy that's assigned with priority 2, policies that are assigned with priority 3 and priority 4 are updated to reflect their new priority. The following two tables show this example.

Here's a list of the policy assignments and priorities for a Teams meeting policy.

|Group name  |Policy name  |Priority|
|---------|---------|---------|
|Sales    |Sales policy       | 1        |
|West Region     |West Region policy         |2         |
|Division    |Division policy         |3         |
|Subsidiary   |Subsidiary policy        |4         |

If we remove the West Region policy from the West Region group, the policy assignments and priorities are updated as follows.

|Group name  |Policy name  |Priority|
|---------|---------|---------|
|Sales    |Sales policy       | 1        |
|Division    |Division policy         |2         |
|Subsidiary   |Subsidiary policy        |3        |

In this example, we remove the Teams meeting policy from a group.

```
Remove-CsGroupPolicyAssignment -PolicyType TeamsMeetingPolicy  -GroupId f985e013-0826-40bb-8c94-e5f367076044 5d2c995d-282d-45ba-940b-a2d4052019a0
```

To learn more, see [Remove-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/remove-csgrouppolicyassignment).

### Change a policy assignment for a group

After you assign a policy to a group, you can use the ```Set-CsGroupPolicyAssignmentd``` cmdlet to change that group's policy assignment as follows:

- Change the priority
- Change the policy of a given policy type
- Change the policy of a given policy type and the priority

In this example, we change a group's Teams call park policy to a policy named SupportCallPark and the assignment priority to 3.

```
Set-CsGroupPolicyAssignment -GroupId 566b8d39-5c5c-4aaa-bc07-4f36278a1b38 -PolicyType TeamsMeetingPolicy -PolicyName SupportCallPark -Priority 3 d3b65ad6-a9d4-48f6-bb6f-5191ea7c0ff4
```

To learn more, see [Set-CsGroupPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/set-csgrouppolicyassignment).

### Change the effective policy for a user

Here's an example of how to change the effective policy for a user who is directly assigned a policy.

First, we use the ```Get-CsUserPolicyAssignment``` cmdlet together with the ```PolicySource``` parameter to get details of the Teams meeting broadcast policies associated with the user. To learn more, see [Get-CsUserPolicyAssignment](https://docs.microsoft.com/powershell/module/teams/get-csuserpolicyassignment).

```
Get-CsUserPolicyAssignment -Identity 3b90faad-9056-49ff-8357-0b53b1d45d39 -PolicyType TeamsMeetingBroadcastPolicy | select -ExpandProperty PolicySource
```

The output shows that the user was directly assigned a Teams meeting broadcast policy named Employee Events, which takes precedence over the policy named Vendor Live Events that's assigned to a group the user belongs to.

```
AssignmentType PolicyName         Reference
-------------- ----------         ---------
Direct         Employee Events
Group          Vendor Live Events 566b8d39-5c5c-4aaa-bc07-4f36278a1b38
```

Now, we remove the Employee Events policy from the user. This means that the user no longer has a Teams meeting broadcast policy directly assigned to them and will inherit the Vendor Live Events policy that's assigned to the group the user belongs to.

```
Remove-CsTeamsMeetingBroadcastPolicy -Identity 3b90faad-9056-49ff-8357-0b53b1d45d3
```

## Related topics

- [Teams PowerShell Overview](teams-powershell-overview.md)