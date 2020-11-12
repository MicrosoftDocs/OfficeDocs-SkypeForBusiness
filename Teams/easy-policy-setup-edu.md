---
title: Set up policies with the Teams for Education easy policy setup tool
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: angch, shajohri
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - remotework
appliesto: 
  - Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to use the Teams for Education easy policy setup tool to set up safe policies for students and educators in your school. 
f1keywords: 
---

# Set up policies with the Teams for Education easy policy setup tool

## Overview

Policies in Teams let you control how Teams behaves in your environment and what features are available to users. For example, there are calling policies, meeting policies, and messaging policies, to name a few, and each policy area has settings that can be adjusted to control access.

To maintain a safe and focused learning environment, it's important to set policies to control what students can do in Teams. For example, you can use policies to control who can use private chat and private calling, who can schedule meetings, and what content types can be shared. You can also use policies to turn on Teams features that enrich the learning experience.

Policies must be adjusted for both students and educators to keep the learning experience safe. Students should get the most conservative settings with the tightest restrictions to reduce the risk of receiving inappropriate levels of access. Educators and staff need a separate set of policies with more permissive settings to be successful. For example, allow educators to schedule meetings and restrict students from doing so.

The Teams for Education easy policy setup tool simplifies managing policies for your students and educators. Use it to quickly set up the most important set of policies to create a safe and productive learning experience.  

This article walks you through how to run the tool and the steps you need to do after you run it.

## What does the easy policy setup tool do?

The easy setup tool creates and assigns a set of core policy definitions to students and a separate set of core policy definitions to educators and staff with settings that are appropriate for each. Here's what happens when you run the tool. 

- **Students**: The tool adjusts the Global (Org-wide default) policy definition for each policy area covered by the tool with settings that are appropriate to keep your students safe. In this way, your current students and all new students get the most restrictive set of policies.
- **Educators and staff**: The tool creates a set of custom policy definitions for each policy area covered by the tool with settings tailored to the needs of educators and staff. Then, it assigns the policy definitions to the group of educators and staff that you choose in the tool. In this way, your educators and staff get a more permissive set of policies to enable them to be successful.

For a detailed listing of the policy definitions created by the tool, see [Policies created by the easy setup tool](#policies-created-by-the-easy-setup-tool).

Now, let's get started!

### Policies created by the easy setup tool

Here's a summary of the policies and policy settings that your students and educators and staff get when you run the tool. 

#### [**Students**](#tab/Students/)

This table lists the values of policy settings in the Global (Org-wide default) policy definition that's assigned to students. 

|Policy area |Column2  |Policy setting  |Primary-Secondary |Higher education |
|---------|---------|---------|---------|---------|
|Teams policies   |         |         |         ||
|Meetings policies    |         |         |         ||
|Row3     |         |         |         ||
|Row4     |         |         |         ||
|Row5     |         |         |         ||
|Row6     |         |         |         ||
|Row7     |         |         |         ||
|Row8     |         |         |         ||
|Row9     |         |         |         ||
|Row10    |         |         |         ||

#### [**Educators and staff**](#tab/educators/)

This table lists the values of policy settings in the custom policy definition that's assigned to the educators and staff group that you choose in the tool.  

|Policy area |Column2  |Policy setting  |Primary-Secondary  |Higher education  |
|---------|---------|---------|---------|---------|
|Teams policies   |         |         |         ||
|Meetings policies    |         |         |         ||
|Row3     |         |         |         ||
|Row4     |         |         |         ||
|Row5     |         |         |         ||
|Row6     |         |         |         ||
|Row7     |         |         |         ||
|Row8     |         |         |         ||
|Row9     |         |         |         ||
|Row10    |         |         |         ||

## How do I run the easy setup tool?

1. In the left navigation of the Microsoft Teams admin center, go to **Dashboard**, and then select **Quick setup**.
2. Select your institution type (**Primary-Secondary** or **Higher education**), and then click **Next**.
3. Search for, and then select a group that contains your educators or staff, and then click **Next**. Educators and staff in the group you select will be assigned a set of policies tailored to their needs. Remember that this set of policies is separate from the policies assigned to students, which the tool does automatically.
4. Review your selections. If you want to find out more about the specific policies that will be assigned, click the links on the page.
5. Select **Apply** to apply your changes. This may take a few minutes to complete.
6. You're on your way but you're not done yet! <br/>Your students and educators or staff are now assigned policies created by the tool but there's a few more things to do. Next, make sure you follow the steps in the [What do I need to do after I run the tool?](#what-do-i-need-to-do-after-i-run-the-tool) section.

## What do I need to do after I run the tool? 

### Step 1: Remove existing policy assignments for policies created by the tool to take effect

> [!IMPORTANT]
> Complete this step only if you have existing policies set up. If you're new to Teams and don't have any existing policies other than the policies created by the easy policy setup tool, skip this step and go to step 2.

Remember that in Teams, for a given policy area, a user automatically gets the Global (Org-wide default) policy unless they're assigned a custom policy. A custom policy can be directly assigned to a user or to a group that the user is a member of. 

If more than one of these policy assignments exist for a given user, Teams respects policies in a specific order: 

|Policy assignments|Policy that takes effect |
|---------|---------|
|Policy assigned to group: No<br/>Policy assigned directly to user: No    |Global (Org-wide) default policy      |
|Policy assigned to group: Yes<br/>Policy assigned directly to user: No     |Policy assigned to group<br/><br/>If the user is a member of multiple groups and each group is assigned a policy of the same policy area, the user gets the policy that has the highest [group assignment ranking](assign-policies.md#group-assignment-ranking).         |
|Policy assigned to group: Yes<br/>Policy assigned directly to user: Yes     |Policy assigned directly to user         |
|Policy assigned to group: No<br/>Policy assigned directly to user: Yes    |Policy assigned directly to user         |

This means that if a user has a policy that was directly assigned to them or is a member of a group that has a policy assigned to it with a higher [group assignment ranking](assign-policies.md#group-assignment-ranking), you have to remove those policies from the user so that the policy assigned by the tool takes effect.

Because of the order that policies take effect, the policies created by the easy policy setup tool won't take effect if you have existing direct assignments for your users or group assignments with higher group rankings. 

- Remove all existing policy assignments for your students so that the Global (Org-wide default) policy values created by the tool are applied.  
- Remove any conflicting direct or group assignments for your educators and staff so that the custom policy values created by the tool are applied.  

### Step 2: Check for other policies that you might need to apply

The easy policy setup tool applies the policies that we listed earlier. There may be additional policies that you may need to apply to tailor Teams to fit the needs of your students and educators or staff. For example, you might want to apply the following policies.

See [Keeping students safe while using Teams for distance learning](https://support.microsoft.com/office/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8#ID0EBBAAA) for our full list of safety recommendations. 

Check out our [Teams policies and policy packages for Education](policy-packages-edu.md) and [Assign policies to large sets of users in your school](batch-group-policy-assignment-edu.md) guides for more info about Teams policies and the best way to apply them in your environment.

### Step 3: Check Message Center for policy updates

Currently, the easy policy setup tool applies our recommended policies when you run it. It's important to know that as new policies become available in Teams, they aren't automatically included in the tool. We're working to add this capability.

Until this capability is available, check Message Center (in the Microsoft 365 admin center) frequently to find out about new policies and policy settings in Teams. You may have to manually update your policies to keep your learning environment safe.

See [Keeping students safe while using Teams for distance learning](https://support.microsoft.com/office/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8#ID0EBBAAA) for our full list of safety recommendations. 

Check out our [Teams policies and policy packages for Education](policy-packages-edu.md) and [Assign policies to large sets of users in your school](batch-group-policy-assignment-edu.md) guides for more info about Teams policies and the best way to apply them in your environment.

## How do I make changes to my selections in the tool? 

1. In the left navigation of the Microsoft Teams admin center, go to **Dashboard**, and then select **Change**.
2. Select your institution type (**Primary-Secondary** or **Higher education**), and then click **Next**.
3. Search for, and then select a group that contains your educators or staff, and then click **Next**. Educators and staff in the group you select will be assigned a set of policies tailored to their needs. Remember that this set of policies is separate from the policies assigned to students, which the tool does automatically.
4. Review your selections. If you want to find out more about the specific policies that will be assigned, click the links on the page.
5. Select **Apply** to apply your changes. This may take a few minutes to complete.
6. You're on your way but you're not done yet! <br/>Your students and educators or staff are now assigned policies created by the tool but there's a few more things to do. Next, make sure you follow the steps in the [What do I need to do after I run the tool?](#what-do-i-need-to-do-after-i-run-the-tool) section.

****

Do you need to give your students and educators access to different features in Microsoft Teams? You can quickly identify the users in your organization by license type and then assign them the appropriate policy. This tutorial shows you how to assign a meeting policy to large sets of users in your school. You can assign policies using the Microsoft Teams admin center and PowerShell and we'll show you both ways.

You can assign a meeting policy to a security group that the users are members of or directly to users at scale through a batch policy assignment. You'll learn how to:

- **Use [policy assignment to groups](#assign-a-policy-to-a-group) to assign a meeting policy to a security group (recommended)**. This method lets you assign a policy based on group membership. You can assign a policy to a security group or distribution list. As members are added to or removed from the group, their inherited policy assignments are updated accordingly. We recommend you use this method because it reduces the time to manage policies for new users or when users' roles change. This method works best for groups of up to 50,000 users but will also work with larger groups.

- **Use [batch policy assignment](assign-policies.md#assign-a-policy-to-a-batch-of-users) to assign a meeting policy directly to users in bulk**. You can assign a policy for up to 5,000 users at a time. If you have more than 5,000 users, you can submit multiple batches. With this method, when you have new users, you'll need to re-run the batch assignment to assign the policy to those new users.

Remember that in Teams, users automatically get the Global (Org-wide default) policy for a Teams policy type unless you create and assign a custom policy. Because the student population is often the largest set of users and they often receive the most restrictive settings, we recommend that you do the following:

- Create a custom policy that allows core capabilities such as private chat and meeting scheduling and assign the policy to your staff and educators.
- Assign the custom policy to your staff and educators.
- Edit and apply the Global (Org-wide default) policy to restrict capabilities for students.

Keep in mind that the Global policy will apply to all users in your school until you create a custom policy and assign it to your staff and educators.

In this tutorial, students will get the Global meeting policy and we'll assign a custom meeting policy named EducatorMeetingPolicy to staff and educators. We assume that you've edited the Global policy to tailor meeting settings for students and [created a custom policy](policy-packages-edu.md) that defines the meeting experience for staff and educators.

![Screenshot of the Meeting policies page in the Teams admin center](media/batch-group-policy-assignment-edu-meeting-policies.png)

## Assign a policy to a group

Follow these steps to create a security group for your staff and educators, and then assign a custom meeting policy named EducatorMeetingPolicy to that security group.

### Before you get started

> [!IMPORTANT]
> When you assign a policy to a group, the policy assignment is propagated to members of the group according to precedence rules. For example, if a user is directly assigned a policy (either individually or through a batch assignment), that policy takes precedence over a policy that's inherited from a group. This also means that if a user has a meeting policy that was directly assigned to them, you'll have to remove that meeting policy from the user before they can inherit a meeting policy from a security group.

Before you get started, it's important to understand [precedence rules](assign-policies.md#precedence-rules) and [group assignment ranking](assign-policies.md#group-assignment-ranking). **Make sure that you read and understand the concepts in [What you need to know about policy assignment to groups](assign-policies.md#what-you-need-to-know-about-policy-assignment-to-groups)**.

You'll need to complete all these steps for your staff and educators to inherit a meeting policy from a security group.

1. [Create security groups](#create-security-groups).
2. [Assign a policy to a security group](#assign-a-policy-to-a-security-group).
3. [Remove a policy that was directly assigned to users](#remove-a-policy-that-was-directly-assigned-to-users).

### Remove a policy that was directly assigned to users

Remember that if a user was directly assigned a policy (either individually or through a batch assignment), that policy takes precedence. This means that if a user has a meeting policy that was directly assigned to them, you'll have to remove that meeting policy from the user before they can inherit a meeting policy from a security group.

To learn more, see [What you need to know about policy assignment to groups](assign-policies.md#what-you-need-to-know-about-policy-assignment-to-groups).

Follow these steps to remove the meeting policy that was directly assigned to your staff and educators.

#### Install and connect to the Microsoft Teams PowerShell module

Run the following to install the [Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams) (if it's not already installed). Make sure you install version 1.0.5 or later.

```powershell
Install-Module -Name MicrosoftTeams
```

Run the following to connect to Teams and start a session.

```powershell
Connect-MicrosoftTeams
```
When you're prompted, sign in using the same admin credentials you used to connect to Azure AD.

#### Unassign a policy that was directly assigned to users

Run the following to remove a meeting policy from users who were directly assigned that policy. You can specify users by email address or object ID.

In this example, the meeting policy is removed from users specified by their email address.

```powershell
$users_ids = @("reda@contoso.com", "nikica@contoso.com", "jamie@contoso.com")
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsMeetingPolicy -PolicyName $null -Identity $users_ids -OperationName "Unassign meeting policy"
```

In this example, the meeting policy is removed from the list of users in a text file named user_ids.txt. 

```powershell
$user_ids = Get-Content .\users_ids.txt
New-CsBatchPolicyAssignmentOperation -PolicyType TeamsMeetingPolicy -PolicyName $null -Identity $users_ids -OperationName "Unassign meeting policy"
```

## Related topics

- [Teams policies and policy packages for Education](policy-packages-edu.md)
- [Assign policies to large sets of users in your school](batch-group-policy-assignment-edu.md)
- [Keeping students safe while using Teams for distance learning](https://support.microsoft.com/office/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8)
- [Assign policies to your users](assign-policies.md)

