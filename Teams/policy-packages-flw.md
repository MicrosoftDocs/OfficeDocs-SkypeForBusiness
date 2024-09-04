---
title: Teams policy packages for frontline workers
author: lana-chin
ms.author: v-chinlana
manager: jtremper
ms.reviewer: 
ms.date: 07/25/2024
ms.topic: conceptual
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365-frontline
  - highpri
appliesto: 
  - Microsoft Teams
  - Microsoft 365 for frontline workers
f1.keywords:
ms.custom: 
ms.localizationpriority: high
search.appverid: MET150
searchScope:
  - Microsoft Teams
  - Microsoft 365 for frontline workers
description: Learn how to use and manage Teams policy packages for frontline workers in your organization.
---

# Teams policy packages for frontline workers

## Overview

A policy package in Microsoft Teams is a collection of predefined policies and policy settings that you can assign to users who have similar roles in your organization. Policy packages simplify, streamline, and help provide consistency when managing policies. To learn more, see [Managing policy packages in Teams](manage-policy-packages.md).

You can customize the settings of the policies in a package to suit the needs of your users. When you change the settings of policies in a policy package, all users who are assigned to that package get the updated settings. You can manage policy packages by using the Microsoft Teams admin center or PowerShell.

This article gives you an overview of the **Frontline manager** and **Frontline worker** policy packages included in Teams.

|Package name in the Teams admin center|Description |
|---------|---------|
|**Frontline manager** |Creates a set of policies and applies those settings to frontline managers in your organization. |
|**Frontline worker**  |Creates a set of policies and applies those settings to frontline workers in your organization.|

:::image type="content" source="media/policy-packages-flw.png" alt-text="Screenshot of frontline policy packages." lightbox="media/policy-packages-flw.png":::

Each individual policy is given the name of the policy package so you can easily identify the policies that are linked to a policy package. For example, when you assign the Frontline manager policy package to store managers in your organization, a policy named Frontline_Manager is created for each policy in the package.

:::image type="content" source="media/policy-packages-flw-frontline-manager.png" alt-text="Screenshot of policies in the Frontline manager policy package." :::

## Use policy packages

### View

View the settings of each policy in a policy package before you assign a package. In the left navigation of the  Teams admin center, go to **Policy packages**, select the package name, and then select the policy name.

Decide whether the predefined values are appropriate for your organization or whether you need to customize them to be more restrictive or lenient based on your organization's needs.

### Customize

Customize the settings of policies in the policy package, as needed, to fit the needs of your organization. Any changes you make to policy settings are automatically applied to users who are assigned the package.

To edit the settings of a policy in a policy package, in the left navigation of the Teams admin center, go to **Policy packages**, select the policy package, select name of the policy you want to edit, and then select **Edit**.

> [!NOTE]
> You can also change the settings of policies in a package after you assign the policy package.

### Assign

You can assign a policy package to an individual user, multiple users, a group of users such as a security group or distribution list, or a large set (batch) of users. To learn more, see [Assign policy packages to users and groups](assign-policy-packages.md).

## Related articles

- [Manage policy packages in Teams](manage-policy-packages.md)
- [Assign policy packages to users and groups](assign-policy-packages.md)
