---
title: Manage policy packages in Microsoft Teams
ms.author: mabond
author: mkbond007
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
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use and manage policy packages in Microsoft Teams to simplify, streamline, and help provide consistency when managing policies for groups of users.
---

# Manage policy packages for Microsoft Teams

A policy package in Microsoft Teams is a collection of predefined policies and policy settings that you can assign to users who have similar roles in your organization. We built policy packages to simplify, streamline, and help provide consistency when managing policies for groups of users across your organization.  

You can use the [policy packages included in Teams](#policy-packages-included-in-teams) or [create your own custom policy packages](#custom-policy-packages).

:::image type="content" source="media/policy-packages-admin-center.png" alt-text="Screenshot of the Policy packages page in the admin center." lightbox="media/policy-packages-admin-center.png":::

You can customize the settings of the policies in a policy package to suit the needs of your users. When you change the settings of policies in a package, all users who are assigned to that package get the updated settings. You manage policy packages by using the Microsoft Teams admin center or PowerShell.

> [!NOTE]
> This feature is temporarily available in public preview for all Microsoft Teams customers. To get this feature after the preview, each user will need the Advanced Communications add-on license. For more information, see [Advanced Communications add-on for Microsoft Teams](/microsoftteams/teams-add-on-licensing/advanced-communications).

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

| Package name | Description |
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
|Healthcare patient room  |Creates a set of policies and policy settings that apply to patient rooms in your healthcare organization. |
|Public safety officer   |Creates a set of policies and policy settings that apply to public safety officers in your organization.|
|Small and medium business user (Business Voice) |Creates an app setup policy that includes the apps for a business voice experience for users.|
|Small and medium business user (without Business Voice) |Creates an app setup policy relevant to small and medium sized business Teams users without any business voice features.

> [!NOTE]
> We'll be adding more policy packages in future releases of Teams, so check back for the most up-to-date information.  

Each individual policy is given the name of the policy package so you can easily identify the policies that are linked to a policy package.
For example, when you assign the Education (Teacher) policy package to teachers in your school, a policy that's named Education_Teacher is created for each policy in the package.

:::image type="content" source="media/teams-policy-packages-education.png" alt-text="Screenshot of the Education (Teacher) policy package." lightbox="media/teams-policy-packages-education.png":::

## Custom policy packages

Custom policy packages let you bundle your own set of policies for users with similar roles in your organization. Create your own policy packages by adding the policy types and policies that you need.

To create a new custom policy package:

1. In the left pane of the Microsoft Teams admin center,  select **Policy packages**, and then click **Add**.

    :::image type="content" source="media/policy-packages-add.png" alt-text="Screenshot of Add button on Policy packages page in the admin center." lightbox="media/policy-packages-add.png":::

2. Enter a name and description for your package.

    :::image type="content" source="media/policy-packages-add-custom.png" alt-text="Screenshot of adding a  new custom policy package." lightbox="media/policy-packages-add-custom.png":::

3. Select the policy types and policy names to include in the package.

4. Select **Save**.

## How to use policy packages

The following outlines how to use policy packages in your organization.

![Overview of how to use policy packages.](media/manage-policy-packages-overview.png)

- **[View](#view-the-settings-of-a-policy-in-a-policy-package)**: View the policies in a policy package. Then, view the settings of each policy in a package before you assign the package. Make sure that you understand each setting. Decide whether the predefined values are appropriate for your organization or whether you need to change them to be more restrictive or lenient based on your organization's needs.

    If a policy is deleted, you can still view the settings but you won't be able to change any settings. A deleted policy is re-created with the predefined settings when you assign the policy package.

- **[Customize](#customize-policies-in-a-policy-package)**: Customize the settings of policies in the policy package to fit the needs of your organization.

- **[Assign](#assign-a-policy-package)**: Assign the policy package to users.  

> [!NOTE]
> You can also change the settings of policies in a policy package after you assign a package. Any changes you make to policy settings are automatically applied to users who are assigned the package.

Here are the steps for how to view, assign, and customize policy packages in the Microsoft Teams admin center.

### View the settings of a policy in a policy package

1. In the left pane of the Microsoft Teams admin center, select **Policy packages**, and then select a policy package by clicking to the left of the package name.

2. Select the policy you want to view.

### Customize policies in a policy package

You can edit the settings of a policy through the **Policy packages** page or by going directly to the policy page in the Microsoft Teams admin center.

1. In the left pane of the Microsoft Teams admin center, do one of the following:
    - Select **Policy packages**, and then select the policy package by clicking to the left of the package name.
    - Select the policy type.  For example, click **Messaging policies**.

2. Select the policy you want to edit. Policies that are linked to a policy package have the same name as the policy package.

3. Make the changes that you want, and then click **Save**.

### Assign a policy package

You can assign a policy package to an individual user, a group, or a batch of users. For more information on how to assign policy packages, see [Assign policy packages to users and groups](assign-policy-packages.md).

## Related topics

- [Assign policy packages](assign-policy-packages.md)
- [Teams policy packages for EDU admins](policy-packages-edu.md)
- [Teams policy packages for healthcare](policy-packages-healthcare.md)
- [Teams policy packages for government](policy-packages-gov.md)
