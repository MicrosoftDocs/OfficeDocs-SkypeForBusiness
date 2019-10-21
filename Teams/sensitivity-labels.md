---
title: Sensitivity labels for Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: abgupta
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
description: Learn how to define and use sensitivity labels in Microsoft Teams.
---

# Sensitivity labels for Microsoft Teams

[Sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) allow Teams admins to regulate access to sensitive organizational content created during collaboration within teams. You can define sensitivity labels and their associated policies in the [Security & Compliance Center](https://docs.microsoft.com/microsoft-365/compliance/go-to-the-securitycompliance-center). These labels and policies are automatically applied to teams in your organization.  

## What's the difference between sensitivity labels and Teams classification labels?

Sensitivity labels are different from classification labels that require you to create them using PowerShell. Classification labels are text strings that can be associated with a group but don't have any actual policies associated with them. You use classification labels as metadata to manually enforce policies through internal tools and scripts.

On the other hand, sensitivity labels and their policies are automatically enforced end-to-end through a combination of the Groups platform, Security & Compliance Center, and Teams services. Sensitivity labels provide powerful infrastructure support for securing your organization's sensitive data.  

## Create and publish sensitivity labels for Teams

For how to create and publish sensitivity labels, see [Overview of sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels).

## Using sensitivity labels with Teams

Here are some example scenarios of how you can use sensitivity labels with Teams in your organization.

### Privacy setting of teams

You can create a sensitivity label that, when applied during team creation, allows users to create teams with a specific privacy (public or private) setting.

For example, you create a label named “Confidential” in the Security & Compliance Center and you configure Teams so that any team that's created with this label must be a private team. When a user creates a new team and selects the **Confidential** label, the only privacy option that's available to the user is **Private**. Other privacy options such as Public and Org-wide are disabled for the user.

![Screenshot of Confidential sensitivity label](media/sensitivity-labels-confidential-example.png)

Similarly, if the user selects **General** when they create a new team, they can only create public or org-wide teams.

![Screenshot of General sensitivity label](media/sensitivity-labels-general-example.png)

When the team is created, the sensitivity label is visible in the upper-right corner of channels in the team.

![Screenshot of sensitivity label in team channel](media/sensitivity-labels-channel.png)

A team owner can change the sensitivity label and the privacy setting of the team at any time by going to the team, and then clicking **Edit team**.

![Screenshot of sensitivity label in team channel](media/sensitivity-labels-edit-team.png)

### Guest access to teams

You can specify whether a team created with a specific label allows guest access. Teams created with a label that doesn't allow guest access are only available to users in your organization. People outside your organization can't be added to the team.

## Known issues

**Support for sensitivity labels in the Microsoft Teams admin center**

Currently, sensitivity labels are not visible in the Microsoft Teams admin center. If you use sensitivity labels, you'll see that the **Classification** column on the Manage teams page of the Microsoft Teams admin center is no longer visible. Classification labels are also not visible in team properties.

**Applying sensitivity labels to existing teams**

Currently, we don't have support to programmatically add labels to existing teams. Teams owners can manually apply a label to a team by going to **Edit team**.