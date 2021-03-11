---
title: Manage policy packages in Microsoft Teams
author: cichur
ms.author: v-cichur
manager: serdars
ms.reviewer: sekrantz, aaglick
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
- ms.teamsadmincenter.policypackages.overview
- seo-marvel-apr2020
localization_priority: Normal
search.appverid: MET150
description: Learn how to use and manage policy packages in Microsoft Teams to simplify, streamline, and help provide consistency when managing policies for groups of users.
---

# Manage policy packages in Microsoft Teams

> [!NOTE]
> One of the features discussed in this article, [custom policy packages](#custom-policy-packages), is currently in private preview.

A policy package in Microsoft Teams is a collection of predefined policies and policy settings that you can assign to users who have similar roles in your organization. We built policy packages to simplify, streamline, and help provide consistency when managing policies for groups of users across your organization.  

You can use the [policy packages included in Teams](#policy-packages-included-in-teams) or [create your own custom policy packages](#custom-policy-packages) (in private preview).

:::image type="content" source="media/policy-packages-admin-center.png" alt-text="Screenshot of the Policy packages page in the admin center":::

You can customize the settings of the policies in a policy package to suit the needs of your users. When you change the settings of policies in a package, all users who are assigned to that package get the updated settings. You manage policy packages by using the Microsoft Teams admin center or PowerShell.

## What is a policy package?

Policy packages let you control Teams features that you want to allow or restrict for specific sets of people across your organization. Each policy package in Teams is designed around a user role and includes predefined policies and policy settings that support the collaboration and communication activities that are typical for that role.

Policy packages support the following Teams policy types:

- Messaging policy
- Meeting policy
- App setup policy
- Calling policy
- Live events policy

## Policy packages included in Teams

Teams currently includes the following policy packages.

|**Package name**  |**Description** |
|---------|---------|
|Education (Higher education student)    |Creates a set of policies and policy settings that apply to higher education students.|
|Education (Primary school student)   |Creates a set of policies and policy settings that apply to primary students.|
|Education (Secondary school student)    |Creates a set of policies and policy settings that apply to secondary students.         |
|Education (Teacher)    |Creates a set of policies and policy settings that apply to teachers.      |
|Education (Primary school teacher using remote learning)    |Creates a set of policies that apply to primary teachers to maximize student safety and collaboration when using remote learning.      |
|Education (Primary school student using remote learning)    |Creates a set of policies that apply to primary students to maximize student safety and collaboration when using remote learning.      |
|Frontline manager |Creates a set of policies and applies those settings to Frontline managers in your organization. |
|Frontline worker |Creates a set of policies and applies those settings to Frontline workers in your organization. |
|Healthcare clinical worker  |Creates a set of policies and policy settings that give clinical workers such as registered nurses, charge nurses, physicians, and social workers full access to chat, calling, shift management, and meetings. |
|Healthcare information worker  |Creates a set of policies and policy settings that give information workers such as IT personnel, informatics staff, finance personnel, and compliance officers, full access to chat, calling, and meetings.|
|Healthcare patient room  |Creates a set of policies and policy settings that apply to patient rooms in your healthcare organization.|
|Small and medium business user (Business Voice) |Creates an app setup policy that includes the apps for a business voice experience.|
|Small and medium business user (without Business Voice) |Creates an app setup policy relevant for a small and medium sized business Teams users (non-Business Voice experience).
|Public safety officer   |Creates a set of policies and policy settings that apply to public safety officers in your organization.|

> [!NOTE]
> We'll be adding more policy packages in future releases of Teams, so check back for the most up-to-date information.  

Each individual policy is given the name of the policy package so you can easily identify the policies that are linked to a policy package.
For example, when you assign the Education (Teacher) policy package to teachers in your school, a policy that's named Education_Teacher is created for each policy in the package.

![Screenshot of the Education (Teacher) policy package](media/policy-packages-education_teacher.png)

## Custom policy packages

**This feature is in private preview**

Custom policy packages let you bundle your own set of policies for users with similar roles in you organization. Create your own policy packages by adding the policy types and policies that you need.

To create a new custom policy package:

1. In the left navigation of the Microsoft Teams admin center,  select **Policy packages**, and then click **Add**.
    :::image type="content" source="media/policy-packages-add.png" alt-text="Screenshot of Add button on Policy packages page in the admin center":::
2. Enter a name and description for your package.
    :::image type="content" source="media/policy-packages-add-custom.png" alt-text="Screenshot of adding a  new custom policy package":::
3. Select the policy types and policy names to include in the package.
4. Click **Save**.

## How to use policy packages

The following outlines how to use policy packages in your organization.

![Overview of how to use policy packages](media/manage-policy-packages-overview.png)

- **[View](#view-the-settings-of-a-policy-in-a-policy-package)**: View the policies in a policy package. Then, view the settings of each policy in a package before you assign the package. Make sure that you understand each setting. Decide whether the predefined values are appropriate for your organization or whether you need to change them to be more restrictive or lenient based on your organization's needs.

    If a policy is deleted, you can still view the settings but you won't be able to change any settings. A deleted policy is re-created with the predefined settings when you assign the policy package.

- **[Customize](#customize-policies-in-a-policy-package)**: Customize the settings of policies in the policy package to fit the needs of your organization.

- **[Assign](#assign-a-policy-package)**: Assign the policy package to users.  

> [!NOTE]
> You can also change the settings of policies in a policy package after you assign a package. Any changes you make to policy settings are automatically applied to users who are assigned the package.

Here are the steps for how to view, assign, and customize policy packages in the Microsoft Teams admin center.

### View the settings of a policy in a policy package

1. In the left navigation of the Microsoft Teams admin center, select **Policy packages**, and then select a policy package by clicking to the left of the package name.
2. Click the policy you want to view.

### Customize policies in a policy package

You can edit the settings of a policy through the **Policy packages** page or by going directly to the policy page in the Microsoft Teams admin center.

1. In the left navigation of the Microsoft Teams admin center, do one of the following:
    - Click **Policy packages**, and then select the policy package by clicking to the left of the package name.
    - Click the policy type.  For example, click **Messaging policies**.
2. Select the policy you want to edit. Policies that are linked to a policy package have the same name as the policy package.
3. Make the changes that you want, and then click **Save**.

### Assign a policy package 

#### Assign a policy package to one user

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click the user.
2. On the user's page, click **Policies**, and then next to **Policy package**, click **Edit**.
3. In the **Assign policy package** pane, select the package you want to assign, and then click **Save**.

#### Assign a policy package to multiple users

1. In the left navigation of the Microsoft Teams admin center, go to **Policy packages**, and then select the policy package you want to assign by clicking to the left of the package name.
2. Click **Manage users**.
3. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then click **Add**. Repeat this step for each user that you want to add.
4. When you're finished adding users, click **Save**.

#### Assign a policy package to a group

Policy package assignment to groups let you assign multiple policies to a group of users, such as a security group or distribution list. The policy assignment is propagated to members of the group according to precedence rules. As members are added to or removed from a group, their inherited policy assignments are updated accordingly. This method is recommended for groups of up to 50,000 users but will also work with larger groups.

To learn more, see [Assign a policy package to a group](assign-policies.md#assign-a-policy-package-to-a-group).

#### Assign a policy package to a large set (batch) of users

Use batch policy package assignment to assign a policy package to large sets of users at a time. You use the [New-CsBatchPolicyPackageAssignmentOperation](https://docs.microsoft.com/powershell/module/teams/new-csbatchpolicypackageassignmentoperation) cmdlet to submit a batch of users and the policy package that you want to assign. The assignments are processed as a background operation and an operation ID is generated for each batch.

A batch can contain up to 5,000 users. You can specify users by their object Id, UPN, SIP address, or email address. To learn more, see [Assign a policy package to a batch of users](assign-policies.md#assign-a-policy-package-to-a-batch-of-users).

## Troubleshooting

**You receive an error when you assign a policy package**

This may occur if one or more policies in the package weren't created or applied successfully. Reassign the policy package to your users. Retrying the operation typically fixes this issue.

## Related topics

[Assign policies to your users in Teams](assign-policies.md)

[Teams policy packages for EDU admins](policy-packages-edu.md)

[Teams policy packages for healthcare](policy-packages-healthcare.md)

[Teams policy packages for government](policy-packages-gov.md)
