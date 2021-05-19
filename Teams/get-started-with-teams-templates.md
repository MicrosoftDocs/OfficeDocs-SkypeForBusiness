---
title: Get started with team templates using Microsoft Graph
author: SerdarSoysal
ms.author: serdars
manager: serdars
audience: Admin
ms.topic: conceptual
ms.service: msteams
ms.reviewer: phlouie
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to use team templates in Microsoft Graph to create collaboration spaces with channels for different topics and preinstall apps to provide content and services.
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

Team templates are pre-built definitions of a team's structure designed around a business need or project. You can [create your own template in the admin console](get-started-with-teams-templates-in-the-admin-console.md). With Microsoft Graph, you use the pre-built templates . You can use team templates to quickly create rich collaboration spaces with channels for different topics and preinstall apps to pull in mission-critical content and services. Team templates provide a predefined team structure that can help you easily create consistent teams across your organization.

In this article, we'll explain the properties that can be defined in templates, what base template types are, and how you can use a few samples requests to create a team from a template.

This article is for you if you're:

- Responsible for planning, deploying, and managing multiple teams across your organization<br>
- A developer wanting to programmatically create a team with predefined channels and apps

## Team template capabilities

Most properties in a team are included and supported by templates. But there are a few properties and features that aren't currently supported. The following table provides a quick summary of what's included and what's not included in Teams templates.

| **Team properties supported by team templates** | **Team properties not yet supported by team templates** |
| ------------------------------------------------ | -------------------------------------------------------- |
| Base template type | Team membership |
| Team name | Team picture |
| Team description | Channel settings |
| Team visibility (public or private) | Connectors |
| Team settings (for example, member, guest, @ mentions) | Files and content |
| Auto-favorite channel | |
| Installed app | |
| Pinned tabs | |

> [!NOTE]
> We'll be adding more template capabilities in future releases of Microsoft Teams, so check back for the most up-to-date information on supported properties.

## What are base template types

Base template types are special templates that Microsoft created for specific industries. These base templates often contain proprietary apps that aren't available in the store. In addition, base templates often contain team properties that aren't yet supported individually in Teams templates. Learn how to use the [team templates in Microsoft Graph](get-started-with-teams-templates.md).

Once a base template type is defined, you can extend or override these special templates with additional properties that you'd like to specify. Some base template types contain properties that can't be overridden.

By default the base template is set to **Standard**, which doesn't contain any additional proprietary apps or special properties. Below is the current list of base template types available.

| Base template type | baseTemplateId | Properties that come with this base template |
| ------------------ | -------------- | ----------------------------------------------------- |
| Standard | `https://graph.microsoft.com/beta/`<br>`teamsTemplates('standard')` | No additional apps and properties |
| Education -<br>Class Team | `https://graph.microsoft.com/beta/`<br>`teamsTemplates('educationClass')` | Apps:<ul><li>OneNote Class Notebook (pinned to the **General** tab) </li><li>Assignments app (pinned to the **General** tab)</li></ul> Team properties:<ul><li>Team visibility set to **HiddenMembership** (cannot be overridden)</li></ul> |
| Education -<br>Staff Team | `https://graph.microsoft.com/beta/`<br>`teamsTemplates('educationStaff')` | Apps:<ul><li>OneNote Staff Notebook (pinned to the **General** tab)</li></ul> |
|Education -<br>PLC team |`https://graph.microsoft.com/beta/`<br>`teamsTemplates('educationProfessionalLearningCommunity')` | Apps:<ul><li>OneNote PLC Notebook (pinned to the **General** tab)</ul></li>|
| Retail -<br>Store | `https://graph.microsoft.com/beta/`<br>`teamsTemplates('retailStore')` | Channels:<ul><li>Shift handoff</li><li>Learning</li></ul>Team properties<ul><li>Team visibility set to Public</li></ul>Member permissions<ul><li>Prevent members from creating, updating, or removing channels</li><li>Prevent members from adding or removing apps</li><li>Prevent members from creating, updating, or removing connectors</li></ul> |
| Retail -<br>Manager collaboration | `https://graph.microsoft.com/beta/`<br>`teamsTemplates('retailManagerCollaboration')` | Channels:<ul><li>Learning</li><li>Operations</li></ul>Team properties:<ul><li>Team visibility set to Private</li></ul>Member permissions:<ul><li>Prevent members from creating, updating, or removing channels</li><li>Prevent members from adding or removing apps</li><li>Prevent members from creating, updating, or removing connectors</li></ul>|
| Healthcare -<br>Ward |`https://graph.microsoft.com/beta/`<br>`teamsTemplates('healthcareWard')` |Channels: <ul><li>Announcements\*</li><li>Huddles\*</li><li>Rounds</li><li>Staffing\*</li><li>Training\*</li></ul>\*Auto-favorited channels |
|Healthcare -<br>Hospital | `https://graph.microsoft.com/beta/`<br>`teamsTemplates('healthcareHospital')` |Channels:<ul><li>Announcements\*</li><li>Compliance\*</li><li>Custodial</li><li>Human Resources</li></li><li>Pharmacy</li></ul>\*Auto-favorited channel|
|||


Use the following templates to create teams in both the Teams client as well as Microsoft Graph.


| Base template type | baseTemplateId | Properties that come with this base template |
| ------------------ | -------------- | ----------------------------------------------------- |
| Adopt Office 365 |`com.microsoft.teams.template.`<br>`AdoptOffice365`|  Channels: <ul><li>General</li> <li>Announcements</li> <li>Champions corner</li> <li>Team forms</li></ul> Apps: <ul><li>Wiki</li>  <li>Calendar</li> |
| Manage a project |`com.microsoft.teams.template.`<br>`ManageAProject`| Channels: <ul><li>General</li> <li>Announcements</li> <li>Resources</li> <li>Planning</li></ul> Apps:<ul><li>Wiki</li><li>OneNote</li></ul> |
| Manage an event|`com.microsoft.teams.template.`<br>`ManageAnEvent` | Channels: <ul><li>General</li> <li>Announcements</li> <li>Budget</li> <li>Content</li><li>Logistics</li> <li>Planning</li> <li> Marketing and PR</li></ul> Apps:<ul><li>Wiki</li><li>Website</li> <li>YouTube</li> <li>Planner</li> <li>OneNote</li></ul> |
|Onboard employees|`com.microsoft.teams.template.`<br>`OnboardEmployees` | Channels: <ul><li>General</li> <li>Announcements</li> <li>Employee chat</li> <li>Training</li></ul>Apps:<ul><li>Wiki</li><li>Communities</li></ul>|
|Organize help desk| `com.microsoft.teams.template.`<br>`OrganizeHelpDesk`|Channels:<ul><li>General</li><li>Announcements</li><li>FAQ</li></ul>Apps:<ul><li>Wiki</li><li>OneNote</li></ul> |
| Collaborate on patient care| `healthcareWard `| Channels:<ul><li>General</li><li>Announcements</li><li>Huddles</li><li>Rounds</li><li>Staffing</li><li>Training</li></ul> Apps: <ul><li>Wiki</li>|
| Collaborate on global crisis or event |`com.microsoft.teams.template.`<br>`CollaborateOnAGlobalCrisisOrEvent`| Channels: <ul><li>General<li>Announcements</li><li>World news</li><li>Business continuity</li><li>Remote working</li><li>Internal comms</li><li>External comms</li><li>Customer complaints</li><li>Kudos</li><li>Executive update</li></ul>Apps: <ul><li>Praise</li><li>Wiki</li><li>Website</li></ul>|
|Collaborate within a bank branch| `com.microsoft.teams.template.`<br>`CollaborateWithinABankBranch `|Channels: <ul><li>General<li>Announcements</li><li>Huddles</li><li>Customer meetings</li><li>Coaching</li><li>Skills development</li><li>Loan processing</li><li>Customer complaints</li><li>Kudos</li><li>Fun stuff</li><li>Compliance</li></ul>|
|Coordinate incident response| `com.microsoft.teams.template.`<br>`CoordinateIncidentResponse`|Channels: <ul><li>General<li>Announcements</li><li>Logistics</li><li>Planning</li><li>Recovery</li><li>Urgent</li></ul> Apps: <ul><li>Wiki</li><li>Excel</li><li>OneNote</li><li>SharePoint</li><li>Planner</li></ul>|
|Hospital| `healthcareHospita`l |Channels: <ul><li>General<li>Announcements</li><li>Compliance</li><li>Custodial</li><li>Human resources</li><li>Pharmacy</li></ul> Apps: <ul><li>Wiki</li></ul>|
|Organize a store| `retailStore` |Channels: <ul><li>General<li>Shift handoff</li><li>Learning</li></ul> Apps: <ul><li>Wiki</li></ul>|
|Quality and safety |`com.microsoft.teams.`<br>`template.QualitySafety`|Channels: <ul><li>General<li>Announcements</li><li>Line 1</li><li>Line 2</li><li>Line 3</li><li>Safety</li><li>Training</li><li>Maintenance</li><li>Fun stuff</li></ul> Apps: <ul><li>Wiki</li></ul>|
|Retail - manager collaboration| `retailManagerCollaboration` |Channels: <ul><li>General<li>Operations</li><li>Learning</li></ul> Apps: <ul><li>Wiki</li></ul>|
||||

See [Get started with team templates in the Admin center](get-started-with-teams-templates-in-the-admin-console.md) for more details.

## Related topics

- [Get started with team templates in the admin console](get-started-with-teams-templates-in-the-admin-console.md)
- [Create a team](/graph/api/team-post?view=graph-rest-beta) (in preview)
- [New-Team](/powershell/module/teams/New-Team?view=teams-ps)
- [Admin training for Microsoft Teams](itadmin-readiness.md)