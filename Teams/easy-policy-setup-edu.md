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

The tool sets up policies based on educational institution type (Primary-Secondary or Higher education). You select your institution type, and then the tool does the following:

- **Students**: The tool adjusts the Global (Org-wide default) policy definition of each policy area covered by the tool with new default settings that are appropriate to keep your students safe. This ensures that your current students and all new students get the most restrictive set of policies.
- **Educators and staff**: The tool creates a set of custom policy definitions for each policy area covered by the tool with settings tailored to the needs of educators and staff. Then, it assigns the policy definitions to the group of educators and staff that you choose. In this way, your educators and staff get a more permissive set of policies to enable them to be successful.

See [Policies set up by the tool](#policies-set-up-by-the-tool) for a detailed list of policy definitions set up by the tool.

Now, let's get started!

## How do I run the easy setup tool?

1. In the left navigation of the Microsoft Teams admin center, go to **Dashboard**, and then in the **Easy policy setup for a safe learning environment** tile, select **Quick setup**.
2. Select your educational institution type (**Primary-Secondary** or **Higher education**), and then click **Next**.
3. Search for, and then select a group that contains your educators or staff, and then click **Next**. Educators and staff in the group you select will be assigned a set of policies tailored to their needs. Remember that this set of policies is separate from the policies applied to students, which the tool does automatically.
4. Review your selections.
5. Select **Apply** to apply your changes. This may take a few minutes to complete.
6. You're on your way but you're not done yet! <br/>Your students and educators or staff are now set up with policies created by the tool but there's a few more things to do. 

    Next, make sure you follow the steps in the [What do I need to do after I run the tool?](#what-do-i-need-to-do-after-i-run-the-tool) section.

## What do I need to do after I run the tool?

### Step 1: Remove existing policy assignments that conflict with policies set up by the tool

> [!IMPORTANT]
> Complete this step only if you have existing policies set up *before* you ran the tool. If you're new to Teams and don't have any existing policies other than the policies created by the tool, skip this and go to step 2.

*** 

#### Option 1

In Teams, users can be assigned a policy either directly or to a group that users are a member of. If a user isn't directly assigned a policy or isn't a member of any groups that are assigned a policy, the user automatically gets the Global (Org-wide default) policy for that policy area.

For each policy area, a user has one policy that takes effect. If a user has one or more policies assigned to them either directly or through a group assignment, Teams uses the following order to determine which policy assignment for that policy area takes effect. 

For more info, see [Which policy takes precedence?](assign-policies.md#which-policy-takes-precedence) and [Precedence rules](assign-policies.md#precedence-rules).

***

#### Option 2

For each of the [policy areas set up by the tool](#policies-set-up-by-the-tool), if a user already has one or more existing policies assigned to them either directly or through a group assignment, you'll have to remove those existing policy assignments from the user before the new policy created by the tool can take effect. This is because for a given policy area, a user has one policy assignment that takes effect.

For more info, see [Which policy takes precedence?](assign-policies.md#which-policy-takes-precedence) and [Precedence rules](assign-policies.md#precedence-rules).

Teams uses the following order to determine which policy assignment for a given policy area takes effect for a user.       |

*** 

#### Option 3 

In Teams, for a given policy area, a policy can be applied to a user in the following ways:

- Direct assignment to the user
- Policy assignment to a group the user is a member of
- If the user isn't directly assigned a policy or isn't a member of any groups that are assigned a policy, the user automatically gets the Global (Org-wide default) policy

If more than one of these policy assignments exist for a user, Teams uses the following order to determine which policy assignment takes effect. For more info, see [Which policy takes precedence?](assign-policies.md#which-policy-takes-precedence) and [Precedence rules](assign-policies.md#precedence-rules).

***

|Policy assignments of a user|Policy that takes effect |
|---------|---------|
|Policy assigned to group: No<br/>Policy assigned directly to user: No    |Global (Org-wide) default policy      |
|Policy assigned to group: No<br/>Policy assigned directly to user: Yes    |Policy assigned directly to user         |
|Policy assigned to group: Yes<br/>Policy assigned directly to user: Yes     |Policy assigned directly to user         |
|Policy assigned to group: Yes<br/>Policy assigned directly to user: No     |Policy assigned to group<br/><br/>If the user is a member of multiple groups and each group is assigned a policy of the same policy area, the policy that has the highest [group assignment ranking](assign-policies.md#group-assignment-ranking) takes effect.         |

Because of this order, the policies created by the easy policy setup tool won't take effect if a user has existing direct assignments or group assignments with higher [group assignment rankings](assign-policies.md#group-assignment-ranking). This means that you'll have to remove the existing policy assignments from the user so the policy set up by the tool takes effect.

For each [policy area set up by the tool](#policies-set-up-by-the-tool), do the following:

- Remove all existing policy assignments for your students so that the Global (Org-wide default) policy definition created by the tool takes effect.
- Remove any conflicting direct or group assignments for your educators and staff so that the custom policy definition created by the tool takes effect. Use the table to determine the scenarios that apply to you.

[Learn more](batch-group-policy-assignment-edu.md#remove-a-policy-that-was-directly-assigned-to-users) about how to remove policies that are directly assigned to users.

For example, you assigned a meeting policy directly to educators and your students have the Global (Org-wide default) meeting policy. In this scenario, remove the meeting policy that you directly assigned to educators so that the custom policy definition for the meeting policy created by the tool will take effect. You don't have to do anything with the existing Global (Org-wide default) meeting policy for students because no other meeting policies conflict with it.

### Step 2: Check for other policies that you might need to adjust

The easy policy setup tool automatically adjusts and applies [these policies](#policies-set-up-by-the-tool). There may be additional policies that you may need to manually adjust to tailor Teams to fit the needs of your students and educators. See [Policies to manually adjust](#policies-to-manually-adjust) for a list of recommended policies that you might want to adjust to stay safe.  

See [Keeping students safe while using Teams for distance learning](https://support.microsoft.com/office/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8#ID0EBBAAA) for our full list of safety recommendations. 

Check out our [Teams policies and policy packages for Education](policy-packages-edu.md) and [Assign policies to large sets of users in your school](batch-group-policy-assignment-edu.md) guides for more info about Teams policies and the best way to apply them in your environment.

### Step 3: Check Message Center for policy updates

Currently, the easy policy setup tool applies our recommended policies when you run it. It's important to know that as new policies become available in Teams, they aren't automatically included in the tool. We're working to add this capability.

Until this capability is available, check Message Center (in the Microsoft 365 admin center) frequently to stay up-to-date on new policies and policy settings in Teams. As new features become available, you may have to manually update your policies to keep your learning environment safe.

See [Keeping students safe while using Teams for distance learning](https://support.microsoft.com/office/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8#ID0EBBAAA) for our full list of safety recommendations. 

Check out our [Teams policies and policy packages for Education](policy-packages-edu.md) and [Assign policies to large sets of users in your school](batch-group-policy-assignment-edu.md) guides for more info about Teams policies and the best way to apply them in your environment.

## How do I make changes in the tool?

If you need to make changes after you run the tool, you can re-run it and change your selections. 

1. In the left navigation of the Microsoft Teams admin center, go to **Dashboard**, and then in the **Easy policy setup for a safe learning environment** tile, select **Change**.
2. From here, continue through each page of the tool to make your changes. You can change your institution type, the group of educators and staff to which you want to assign policies, or both.

The following table summarizes what happens when you make a change in the tool.

|Type of change  |Policy behavior  |
|---------|---------|
|Change the educational institution type and the educators and staff group    |<ul><li>**Students**: The Global (Org-wide default) policy definitions based on the new educational institution type are applied to students.</li><li>**Educators and staff**: A set of custom policy definitions based on the new educational institution type is created and assigned to the new educator and staff group. The previous custom policy definitions are removed from the previous educators and staff group.</li></ul>    |
|Change the educational institution type    |<ul><li>**Students**: The Global (Org-wide default) policy definitions based on the new educational institution type are applied to students.</li><li>**Educators and staff**: A set of custom policy definitions based on the new educational institution type is created and assigned to the educators and staff group. The previous custom policy definitions are removed from the  educators and staff group.</li></ul>         |
|Change the educators and staff group   |<ul><li>**Students**: No change to the Global (Org-wide default) policy definitions applied to students.</li><li>**Educators and staff**: The set of custom policy definitions is assigned to the new educators and staff group and removed from the previous educators and staff group.</li></ul>         |

## Policies set up by the tool

Here's a summary of the policies that your students and educators and staff get when you run the tool. 

#### [**Students**](#tab/Students/)

Here's a list of the Global (Org-wide default) policy definitions applied to students. 

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

Here's a list of the custom policy definitions applied to the educators and staff group that you choose in the tool.  

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

* * *

## Policies to manually adjust

Here's a list of policies that you may want to manually adjust to keep your learning environment safe. 

#### [**Students**](#tab/Students/)

Here's a list of recommended Global (Org-wide default) policy definitions that you can set for student safety. 

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

Here's a list of recommended custom policy definitions that you can set for your educators and staff. 

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

* * *

## Related topics

- [Teams policies and policy packages for Education](policy-packages-edu.md)
- [Assign policies to large sets of users in your school](batch-group-policy-assignment-edu.md)
- [Keeping students safe while using Teams for distance learning](https://support.microsoft.com/office/keeping-students-safe-while-using-teams-for-distance-learning-f00fa399-0473-4d31-ab72-644c137e11c8)
- [Assign policies to your users](assign-policies.md)