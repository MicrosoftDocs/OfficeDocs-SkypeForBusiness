---
title: Get started with Teams templates
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/12/2018
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: phecda louie
localization_priority: Normal
search.appverid: MET150
description: Learn how to use Teams templates to create a team with predefined channels.
ms.custom:
- NewAdminCenter_Update
appliesto: 
- Microsoft Teams
---

# Get started with Teams templates 

Team templates are pre-built definitions of a team's structure designed around a business need or project. You can use team templates to quickly create rich collaboration spaces with channels for different topics, and preinstall apps to pull in mission-critical content and services. Team templates provide a predefined team structure that can help you easily create consistent teams across your organization. 

In this article, we'll explain the properties that can be defined in templates, what base template types are, and how you can use a few sample requests to create a team from a template.
 
This article is for you if you're:

•	Responsible for planning, deploying, and managing multiple teams across your organization
•	Developer looking to create a team with predefined channels and apps programmatically

## Team template capabilities

Most properties in a team are included and supported by templates. However, there are a few properties and features that are currently not supported. The following table provides a quick summary of what's included and what's not included in Teams templates.

| **Team properties supported by Teams templates** | **Team properties not yet supported by Teams templates** |
| ------------------------------------------------ | -------------------------------------------------------- |
| Base template type | Team membership |
| Team name | Team picture |
| Team description | Channel settings (for example, auto-favorite and privacy) |
| Team visibility (public or private) | Connectors |
| Team settings (for example, member, guest, @ mentions) | Files and content |
| Auto-favorite channel | |
| Installed app | |
| Pinned tabs | | 

> [!NOTE]
> We'll be adding more template capabilities in future releases of Microsoft Teams, so check back for the most up-to-date information on supported properties.

## What are base template types?

Base template types are special templates that Microsoft created for specific industries. These base templates often contain proprietary apps that aren't available in the store and team properties not yet supported individually in Teams templates.

 Once a base template type is defined, you can extend or override these special templates with additional properties that you'd like to specify. However, some base template types contain properties that can't be overridden. 

By default the base template is set to **Standard** which doesn't contain any additional proprietary apps or special properties. Below is the current list of base templates types available.

| Base template type | baseTemplateId | Base template proprietary apps and special properties |
| ------------------ | -------------- | ----------------------------------------------------- |
| Standard | [https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Standard.json](https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Standard.json) | No additional apps and properties |
| Healthcare - care coordination | [https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Healthcare-CC.json#](https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Healthcare-CC.json#) | Apps:<br/> - Patients app (pinned to the **General** tab)<br/> <br/>Channels: <br/> - Announcements<br/> - Diabetes<br/> - Cardiovascular<br/> - Registered nurses |
| Healthcare - process huddle | [https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Healthcare-PH.json#](https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Healthcare-PH.json#) | Channels:<br/> - Avoidable deaths<br/> - Mortality review <br/> - Preventing falls <br/> - Sepsis plans |
| Education - Class team* | [https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Education-CT.json#](https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Education-CT.json#) |