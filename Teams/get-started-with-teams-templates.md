---
title: Get started with team templates using Microsoft Graph
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: Admin
ms.topic: conceptual
ms.service: msteams
ms.reviewer: yinchang
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn about the team templates that are available only with Microsoft Graph. 
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
  - seo-marvel-apr2020
appliesto: 
  - Microsoft Teams
---

# Get started with team templates using Microsoft Graph

> [!NOTE]
> Team templates currently don't support creating private channels. Private channel creation isn't included in template definitions.

A team template in Microsoft Teams is a definition of a team's structure designed around a business need or project. With team templates, you can quickly and easily create rich collaboration spaces with predefined settings, channels, and apps. Team templates can help you to deploy consistent teams across your organization.

With Microsoft Graph, you can create your own templates or use the pre-built team templates that are included with Teams to create teams. In this article, you'll learn about the properties that can be defined in templates and the pre-built templates that are available only with Microsoft Graph.

This article is for you if you're:

- Responsible for planning, deploying, and managing multiple teams across your organization<br>
- A developer wanting to programmatically create a team with predefined channels and apps

## Team template capabilities

Most properties in a team are included and supported by templates. But there are a few properties and features that aren't currently supported. Here's a quick summary of what's included and what's not included in team templates.

| **Team properties supported by team templates** | **Team properties not yet supported by team templates** |
| ------------------------------------------------ | -------------------------------------------------------- |
| Template type | Team membership |
| Team name | Team picture |
| Team description | Channel settings |
| Team visibility (public or private) | Connectors |
| Team settings (for example, member, guest, @ mentions) | Files and content |
| Auto-favorite channel | |
| Installed app | |
| Pinned tabs | |

> [!NOTE]
> We'll be adding more template capabilities in future releases of Microsoft Teams, so check back for the most up-to-date information on supported properties.

## Custom templates

To learn more about how to create your own templates using Graph, see 

## Pre-built templates

Pre-built team templates are templates that we created for specific industries. Here's the pre-built templates that are available only with Microsoft Graph.

| Template type | TemplateId | Properties that come with this template |
| ------------------ | -------------- | ----------------------------------------------------- |
| Standard | `https://graph.microsoft.com/v1.0/`<br>`teamsTemplates('standard')` | No additional apps and properties |
| Education -<br>Class Team | `https://graph.microsoft.com/v1.0/`<br>`teamsTemplates('educationClass')` | Apps:<ul><li>OneNote Class Notebook (pinned to the **General** tab) </li><li>Assignments app (pinned to the **General** tab)</li></ul> Team properties:<ul><li>Team visibility set to **HiddenMembership** (cannot be overridden)</li></ul> |
| Education -<br>Staff Team | `https://graph.microsoft.com/v1.0/`<br>`teamsTemplates('educationStaff')` | Apps:<ul><li>OneNote Staff Notebook (pinned to the **General** tab)</li></ul> |
|Education -<br>PLC team |`https://graph.microsoft.com/v1.0/`<br>`teamsTemplates('educationProfessionalLearningCommunity')` | Apps:<ul><li>OneNote PLC Notebook (pinned to the **General** tab)</ul></li>|

> [!NOTE]
> For a list of pre-built templates that you can use in the Teams client and with Microsoft Graph, see [Get started with team templates in the Teams admin center](get-started-with-teams-templates-in-the-admin-console.md).

## Related articles

- [Get started with team templates in the Teams admin center](get-started-with-teams-templates-in-the-admin-console.md)
- [Create a team](/graph/api/team-post?view=graph-rest-beta) (in preview)
- [New-Team](/powershell/module/teams/New-Team?view=teams-ps)
