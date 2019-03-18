---
title: Get started with Teams templates in retail
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 03/11/2019
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: phecda louie
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
localization_priority: Normal
search.appverid: MET150
description: "Learn how to use Teams templates to create team structures designed for retailer needs."
ms.custom:
- NewAdminCenter_Update
appliesto: 
- Microsoft Teams
---

# Get started with Teams templates in retail 

Teams templates allow you to quickly and easily create teams by providing a predefined template of settings, channels, and pre-installed apps.

Teams templates have pre-built definitions of team structures designed around retailer needs. You can use Teams templates to quickly create the types of teams that work well for retailers and deploy them across your organization. You can also extend the Teams templates to create teams that are tailored to your specific organizational needs.

In this article, we will introduce each of the Teams templates and how we recommend using them.

This article is for you if you're responsible for planning, deploying, and managing multiple teams across your retail organization.

To learn more about team templates in general, please refer to [Get started with Teams templates](get-started-with-teams-templates.md).

## Store template

The Store template is ideal for creating a team to represent an individual retail store location. Using the Store template, you can create a team for each retail store location in your organization.

| Base template type | baseTemplateId | Properties that come with this base template |
| ------------------ | -------------- | ----------------------------------------------------- |
| Retail - <br>Store | `https://graph.microsoft.com/beta/`<br>`teamsTemplates('retailStore')`| Channels <ul><li>Shifts handoff\*</li><li>Learning\*</li></ul>\*Auto-favorited channels<br><br>Team properties <ul><li>Team visibility set to Public</li></ul> <br>Member permissions <ul><li>Cannot create/update/delete channels </li><li>Cannot add/remove apps </li><li>Cannot create/update/remove tabs</li><li>Cannot create/update/remove connectors</li><ul>|
||||

Recommended ways to customize the Store template for your organization:

- If your organization has departments within each store, add a channel for each department. This will facilitate communication and collaboration within the department.

- If your organization has any internal websites (for example, a SharePoint site), consider pinning them as tabs in the relevant team channel. Refer to [Get started with Teams templates](get-started-with-teams-templates.md) for instructions.

## Manager Collaboration template

The Manager Collaboration template is another one of the Teams templates designed around retailer needs. The Manager Collaboration template is ideal for creating a team for a set of managers to collaborate across stores/regions, etc. For example, if your organization has regions, you might create a Manager Collaboration team for the California Region and include all the store managers in that region, as well as the regional manager for that region.

| Base template type | baseTemplateId | Properties that come with this base template |
| ------------------ | -------------- | ----------------------------------------------------- |
| Retail - <br>Store | `https://graph.microsoft.com/beta/`<br>`teamsTemplates('retailManagerCollaboration')`| Channels <ul><li>Operations\*</li><li>Learning\*</li></ul>\*Auto-favorited channels<br><br>Team properties <ul><li>Team visibility set to Private</li></ul> <br>Member permissions <ul><li>Can create/update/delete channels </li><li>Can add/remove apps </li><li>Can create/update/remove tabs</li><li>Can create/update/remove connectors</li><ul>|
||||

Recommended ways to customize the Manager Collaboration template for your organization:

- If your organization has any internal websites (for example, a SharePoint site) that are relevant for managers, consider pinning them as tabs in a relevant team channel (refer to documentation [here](get-started-with-teams-templates.md) for instructions).