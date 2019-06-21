---
title: Manage policy packages in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: sekrantz
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to manage and assign policy packages in Microsoft Teams. 
---

# Manage policy packages in Microsoft Teams

Policy packages in Microsoft Teams are collections of predefined policies and policy settings that you can assign to users who have similar roles in your organization. Policy packages are designed to simplify, streamline, and help provide consistency when managing policies for groups of users across your organization.  

When you assign a policy package to users, the policies in the package are created and you can then customize the settings in the policies in the package to meet your organization's needs.

For example, use the Education_Teacher policy package to assign policies that apply to all teachers in your school.

## Types of policy packages

Teams includes the following policy packages.

|**Package name**  |**Description** |
|---------|---------|
|Education_Teacher package     |Creates a set of policies and policy settings that apply to teachers.      |
|Education_PrimaryStudent package    |Creates a set of policies and policy settings that apply to primary students.|
|Education_SecondaryStudent package    |Creates a set of policies and policy settings that apply to secondary students.         |
|Education_HigherEducationStudent package    |Creates a set of policies and policy settings that apply to higher education students.|

> [!NOTE]
> We'll be adding more policy packages in future releases of Teams, so check back for the most up-to-date information.  

## Policies included in a policy package

The following policies are created when you assign a policy package to users. Each individual policy includes the name of the policy package, for example, [add an example name here] so you can easily identify the policies that are linked to a policy package.

- **Messaging policy** - Messaging policies are used to control which chat and channel messaging features are available to users in Teams. [Learn more](messaging-policies-in-teams.md).
- **Meeting policy** - Meeting policies are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization.  [Learn more](meeting-policies-in-teams.md).
- **App setup policy** - App setup policies let you customize Teams to highlight the apps that are most important for your users. You choose the apps that you want to pin to the app bar in Teams clients. [Learn more] (teams-app-setup-policies.md).
- **Calling policy** - Calling policies control which calling and call forwarding features are available to users. [Learn more](teams-calling-policy.md).
- **Live events policy** - Live event policies are used to control what features available to users who hold live events in your organization. [Learn more](teams-live-events/set-up-for-teams-live-events.md).

## How policy packages work

The following steps outline how to use a policy package in your organization.

![Overview of how to use policy packages](media/manage-policy-packages-overview.png)

It's important to know that the policies in a policy package aren't created until you assign the package to users, after which you can change the settings of individual policies in the package. Any changes you make to policy settings are automatically applied to users who are assigned the policy package.

You can view the settings of policies in a policy package before you assign it to users but you won't be able to make changes to any policy settings until after you assign the package.

> [!IMPORTANT]
> If a policy is deleted, you can still view the settings but you won't be able to change any settings. The deleted policy will be re-created when you assign the policy package.

## View a policy in a policy package

You can use this page to view the settings of a specific policy that is linked to this policy package. If you haven't assigned the policy package to a user or if the policy linked to the package policy has been deleted or renamed you won't be able to make changes to the settings of the policy.

## Assign a policy package

1. In the left navigation of the Microsoft Teams admin center, go to **Policy package**. 

## Edit a policy in a policy package

You can edit the settings of each policy using the Policy packages icon or by going to the policy page in the left navigation of the Teams admin center.

## Related topics
