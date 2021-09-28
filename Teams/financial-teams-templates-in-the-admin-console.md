---
title: Use financial team templates
author: lanachin
ms.author: v-lanachin
manager: samanro
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: yinchang
ms.collection: 
  - M365-collaboration
ms.localizationpriority: high
search.appverid: MET150
description: Learn how to manage and use financial team templates in the Teams admin center and with Microsoft Graph to quickly and easily create teams for your financial services organization. 
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
  - seo-marvel-apr2020
appliesto: 
  - Microsoft Teams
---

# Use financial team templates

Team templates in Microsoft Teams allow you to quickly and easily create teams by providing a predefined team structure of settings, channels, and pre-installed apps.

For financial services organizations, team templates can be especially powerful, as they help you to quickly deploy consistent teams across your organization. Templates also help staff to get oriented with how to effectively use Teams.

Teams includes templates designed for financial services organizations. Use these pre-built templates to quickly create teams for staff to communicate and collaborate. In this article, we introduce you to each of these templates and recommend how to use them.

How you manage and work with team templates depends on whether you're an admin or developer.

|If you're: | Then, you: |
| ---- | --------- |
| An admin or IT pro |[Manage team templates in the Teams admin center](#manage-team-templates-in-the-teams-admin-center). View team templates and apply templates policies to control which templates your staff can use in Teams for creating teams. |
| A developer | [Use Microsoft Graph](#use-team-templates-with-microsoft-graph) to create teams from team templates. |

## Manage team templates in the Teams admin center

As an admin, you can manage team templates in the Microsoft Teams admin center. Here, you can view details about each template. You can also [create and assign templates policies](templates-policies.md) to your staff to control which templates they see in Teams for [creating teams](https://support.microsoft.com/office/create-a-team-from-a-template-a90c30f3-9940-4897-ab5b-988e69e4cd9c).

To learn more about team templates in general, see [Get started with team templates in the Teams admin center](get-started-with-teams-templates-in-the-admin-console.md).

We currently offer the following pre-built team templates for financial services organizations. To view them, in the left navigation of the Teams admin center, go to **Teams** > **Team templates**.

### Collaborate within a bank branch

Centralize collaboration for your bank branch employees across huddles, customer meetings, business processes such as mortgage collaboration, and keep everyone in the loop with announcements and kudos.

| Template type |TemplateId| Properties that come with this template |
| ------------------ |--|----------------------------------------------------- |
|Bank branch| `CollaborateWithinABankBranch`|Channels: <ul><li>General<li>Announcements</li><li>Huddles</li><li>Customer meetings</li><li>Approvals request </li><li>Coaching</li><li>Skills development</li><li>Loan processing</li><li>Customer complaints</li><li>Kudos</li><li>Fun stuff</li><li>Compliance</li></ul>Apps:<ul><li>Praise </li><li>Issue Reporter</li><li>Wiki</li><li>Calendar</li><li>Approvals</li><li>Bulletins</li><li>Ideas</li></ul>|
||||

## Use team templates with Microsoft Graph

Developers can use Microsoft Graph to create teams from pre-built team templates. To learn more about using team templates with Microsoft Graph, see [Get started with team templates using Microsoft Graph](get-started-with-teams-templates.md), [Microsoft Teams API overview](/graph/teams-concept-overview?view=graph-rest-1.0), and [teamsTemplate resource type](/graph/api/resources/teamstemplate?view=graph-rest-1.0).

### Bank branch

Centralize collaboration for your bank branch employees across huddles, customer meetings, business processes such as mortgage collaboration, and keep everyone in the loop with announcements and kudos.

| Template type |TemplateId| Template channels |
| ------------------ |--|----------------------------------------------------- |
|Bank branch|`https://graph.microsoft.com/beta/teamsTemplates('CollaborateWithinABankBranch')`|General<br>Announcements<br>Huddles<br>Customer meetings<br>Approvals request<br>Coaching<br>Skills development<br>Loan processing<br>Customer complaints<br>Kudos<br>Fun stuff<br>Compliance|
||||

> [!NOTE]
> For additional templates that apply to financial services organization, see [Team templates built in Microsoft Graph for small and medium businesses](smb-templates.md).