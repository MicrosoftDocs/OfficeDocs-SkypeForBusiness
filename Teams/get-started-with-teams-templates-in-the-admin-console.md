---
title: Get started with team templates in the Teams admin center
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
  - m365-frontline
description: Learn about team templates and how to manage them in the Microsoft Teams admin center.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---

# Get started with team templates in the Teams admin center

**The ability to create custom templates is not yet supported for EDU customers.**

> [!NOTE]
> - Private and shared channels are currently not supported in team templates. Private and shared channel creation is not included in  template definitions.
>
> - Sensitivity labels are not supported in team templates in GCC environments. The sensitivity label option in the Create team from template flow will not be applied to the team.

## Overview

A team template in Microsoft Teams is a definition of a team's structure designed around a business need or project. As an admin, you can use templates to easily deploy consistent teams across your organization. With templates, your users can quickly create rich collaboration spaces with predefined settings, channels, and apps.

You can manage team templates in the Microsoft Teams admin center or by using PowerShell. You can use the pre-built templates that we provide and you can also [create your own custom templates](#create-your-own-team-templates). You can also [apply template policies](#apply-team-template-policies) to control which templates are available to your users in Teams.

This article gives you an overview of working with team templates in the Teams admin center. You'll learn about the properties that are supported in templates, the pre-built templates that we provide, template size limits, how to create and manage templates, and more.

> [!NOTE]
> Your users can [create teams from pre-built or custom team templates](https://support.microsoft.com/office/create-a-team-from-a-template-a90c30f3-9940-4897-ab5b-988e69e4cd9c) in the Teams app. Developers can also programmatically create teams from pre-built or custom team templates using Microsoft Graph. To learn more, see [Get started with team templates using Microsoft Graph](get-started-with-teams-templates.md).

## Team template capabilities

Most properties in a team are included and supported by team templates. But there are a few properties and features that aren't currently supported. Here's a summary of what's included and what's not included in team templates.

| **Team properties supported by team templates** | **Team properties not yet supported by team templates** |
| ------------------------------------------------ | -------------------------------------------------------- |
| Template type | Team membership |
| Team name | Team picture |
| Team description | Channel settings |
| Team visibility (public or private) | Connectors |
| Team settings (for example, member, guest, @ mentions) | Files and content |
| Autofavorite channel | |
| Installed app | |
| Pinned tabs | |

> [!NOTE]
> We'll be adding more template capabilities in future releases of Microsoft Teams, so check back for the most up-to-date information on supported properties.

## Pre-built team templates in the Teams admin center

Here are the pre-built team templates that are available in the Teams admin center. Pre-built templates are templates that we created for specific industries. To view these templates, in the left navigation of the Teams admin center, go to **Teams** > **Team templates**.

You can duplicate pre-built templates but you can't edit them. If you want to change the properties in a pre-built template, you can create a new template from an existing one, and then add or remove the properties that you want. Keep in mind that certain properties in some templates can't be changed.

| Template type | TemplateId | Properties that come with this template |
| ------------------ | -------------- | ----------------------------------------------------- |
| Adopt Office 365 |`com.microsoft.teams.template.AdoptOffice365`|  Channels: <ul><li>General</li> <li>Announcements</li> <li>Champions corner</li> <li>Team forms</li><li>Calendar</li></ul> Apps: <ul><li>Wiki</li>  <li>Channel calendar</li> <li>Milestones</li><li>Bulletins</li></ul>|
| Manage a project |`com.microsoft.teams.template.ManageAProject`| Channels: <ul><li>General</li> <li>Announcements</li> <li>Resources</li> <li>Planning</li></ul> Apps:<ul><li>Wiki</li><li>OneNote</li><li>Tasks</li><li>Lists</li><li>Power Automate</li></ul> |
| Manage an event|`com.microsoft.teams.template.ManageAnEvent` | Channels: <ul><li>General</li> <li>Announcements</li> <li>Budget</li> <li>Content</li><li>Logistics</li> <li>Planning</li> <li> Marketing and PR</li></ul> Apps:<ul><li>Wiki</li><li>Website</li> <li>YouTube</li> <li>Tasks</li> <li>OneNote</li> <li>Employee ideas</li> <li>Issue Reporter</li><li>Power Automate</li><li>Bulletins</li><li>Milestones</li></ul> |
|Onboard employees|`com.microsoft.teams.template.OnboardEmployees` | Channels: <ul><li>General</li> <li>Announcements</li> <li>Employee chat</li> <li>Training</li></ul>Apps:<ul><li>Wiki</li><li>Communities</li><li>Tasks</li><li>Employee ideas</li><li>Power Automate</li><li>Bulletins</li><li>Milestones</li></ul>|
|Organize help desk| `com.microsoft.teams.template.OrganizeHelpDesk`|Channels:<ul><li>General</li><li>Announcements</li><li>FAQ</li></ul>Apps:<ul><li>Wiki</li><li>OneNote</li><li>Tasks </li><li>Praise</li><li>Issue Reporter</li><li>Power Automate</li><li>Bulletins</li></ul> |
| Patient care| `com.microsoft.teams.template.healthcareWard`| Channels:<ul><li>General</li><li>Announcements</li><li>Huddles</li><li>Rounds</li><li>Staffing</li><li>Training</li></ul> Apps: <ul><li>Wiki</li><li>Lists  </li><li>Approvals</li><li>Bulletins</li><li>Inspection</li></ul>|
| Crisis communication |`com.microsoft.teams.template.CollaborateOnAGlobalCrisisOrEvent`| Channels: <ul><li>General<li>Announcements</li><li>World news</li><li>Internal comms</li><li>External comms</li><li>Approvals request</li><li>Customer escalations</li><li>Executive update</li><li>Planning</li><li>Logistics</li></ul>Apps: <ul><li>Website</li><li>Tasks</li><li>Issue Reporter</li><li>Approvals</li><li>Bulletins</li><li>OneNote</li><li>Power Automate</li><li>SharePoint</li></ul>|
|Bank branch| `com.microsoft.teams.template.CollaborateWithinABankBranch`|Channels: <ul><li>General<li>Announcements</li><li>Huddles</li><li>Customer meetings</li><li>Approvals Request </li><li>Coaching</li><li>Skills development</li><li>Loan processing</li><li>Customer complaints</li><li>Kudos</li><li>Fun stuff</li><li>Compliance</li></ul>Apps:<ul><li>Praise </li><li>Issue Reporter</li><li>Wiki</li><li>Calendar</li><li>Approvals</li><li>Bulletins</li><li>Ideas</li></ul>|
|Incident response| `com.microsoft.teams.template.CoordinateIncidentResponse`|Channels: <ul><li>General<li>Announcements</li><li>Logistics</li><li>Planning</li><li>Recovery</li><li>Urgent</li></ul> Apps: <ul><li>Wiki</li><li>Excel</li><li>OneNote</li><li>SharePoint</li><li>Tasks</li> <li>Approvals</li> <li>Inspection</li> <li>Power Automate</li><li>Bulletins</li><li>Milestones</li></ul>|
|Hospital| `com.microsoft.teams.template.healthcareHospital` |Channels: <ul><li>General</li><li>Announcements</li><li>Compliance</li><li>Custodial</li><li>Human resources</li><li>Pharmacy</li></ul> Apps: <ul><li>Wiki</li><li>Lists</li><li>Tasks</li><li>Approvals</li><li>Shifts</li><li>Bulletins</li><li>Inspection</li><li>Ideas</li></ul>|
|Organize a store| `com.microsoft.teams.template.retailStore` |Channels: <ul><li>General<li>Shift handoff</li><li>Store readiness</li><li>Learning</li></ul> Apps: <ul><li>Wiki</li><li>Tasks</li><li>Shifts</li><li>Inspection</li></ul>|
|Retail for managers| `com.microsoft.teams.template.retailManagerCollaboration` |Channels: <ul><li>General<li>Operations</li><li>Learning</li></ul> Apps: <ul><li>Wiki</li><li>Tasks</li><li>Inspection</li></ul>|
|Quality and safety |`com.microsoft.teams.template.QualitySafety`|Channels: <ul><li>General<li>Announcements</li><li>Leadership</li><li>Maintenance</li><li>Production Line 1</li><li>Production Line 2</li><li>Production Line 3</li><li>Health and Safety</li><li>Training</li><li>Fun stuff</li></ul> Apps: <ul><li>Wiki</li><li>Tasks</li> <li>Issue Reporter</li> <li>Inspection</li> </ul>|
|Manage volunteers| `com.microsoft.teams.template.ManageVolunteers` |Channels: <ul><li>General<li>Announcements</li><li>Reporting</li><li>Volunteer Management</li><li>Engagement Opportunities</li><li>Volunteer Onboarding</li></ul> Apps: <ul><li>Website</li><li>YouTube</li><li>Power BI</li><li>Power Apps</li><li>Tasks</li><li>SharePoint</li><li>OneNote</li></ul>|
||||

### Team templates by category and industry

For more information about ways to use the pre-built templates in your industry, see:

- [Financial team templates](financial-teams-templates-in-the-admin-console.md)
- [General team templates](general-teams-templates-in-the-admin-console.md)
- [Government team templates](government-teams-templates-in-the-admin-console.md)
- [Healthcare team templates](expand-teams-across-your-org/healthcare/healthcare-templates-admin-console.md)
- [Manufacturing team templates](manufacturing-teams-templates-in-the-admin-console.md)
- [Nonprofit team templates](team-templates-nonprofit.md)
- [Retail team templates](get-started-with-retail-teams-templates.md)

## Team template size limits

Templates are limited to a specific number of channels, tabs, and apps.

 > [!Note]
 > You can add more channels, tabs, and apps to the team after it's created from a template.

|Feature | Limit|
|-|-|
|Channels per template | 15 |
|Tabs per channel in a template | 20 |
|Apps per template | 50|
|||

For more information, see [Limits and specifications of Teams](limits-specifications-teams.md).

## Manage team templates

### Manage team templates in the Teams admin center

#### View team templates

To view team templates, in the left navigation of the Teams admin center, go to **Teams** > **Team templates**. Select a template to see more details, including the channels and apps it contains.

#### Create your own team templates

You can create your own custom templates from scratch, from an existing team, and from an existing template. To learn more, see:

- [Create a custom team template](create-a-team-template.md)
- [Create a template from an existing team](create-template-from-existing-team.md)
- [Create a team template from an existing team template](create-template-from-existing-template.md)

#### Apply team template policies

To control the templates that users see in Teams for [creating teams](https://support.microsoft.com/office/create-a-team-with-team-templates-702a2977-e662-4038-bef5-bdf8ee47b17b), you can set templates policies and assign them to users and groups in your organization. To learn more, see [Manage team templates in the Teams admin center](templates-policies.md).

### Manage team templates using PowerShell

Use the following cmdlets to manage your templates in PowerShell.

- [Get-CsTeamTemplate](/powershell/module/teams/get-csteamtemplate)
- [Get-CsTeamTemplateList](/powershell/module/teams/get-csteamtemplatelist)
- [New-CsTeamTemplate](/powershell/module/teams/new-csteamtemplate)
- [Remove-CsTeamTemplate](/powershell/module/teams/remove-csteamtemplate)
- [Update-CsTeamTemplate](/powershell/module/teams/update-csteamtemplate)

## Related articles

- [Create a team from a template](https://support.microsoft.com/office/create-a-team-with-team-templates-702a2977-e662-4038-bef5-bdf8ee47b17b)
- [Get started with team templates using Microsoft Graph](get-started-with-teams-templates.md)
- [Clone a team](/graph/api/team-clone)
