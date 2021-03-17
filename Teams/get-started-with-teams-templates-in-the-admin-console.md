---
title: Use Teams templates in the admin center
author: cichur
ms.author: v-cichur
manager: serdars
audience: Admin
ms.topic: conceptual
ms.service: msteams
ms.reviewer: aaglick
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to use Teams templates to create collaboration spaces with channels for different topics using preinstalled templates.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---

# Get started with Teams templates in the admin center

**Ability to create custom templates is not yet supported for EDU customers.**

> [!NOTE]
> Teams templates currently don't support creating private channels. Private channel creation isn't included in template definitions.

Teams templates are pre-built definitions of a team's structure designed around a business need or project. Use pre-built templates or create your own template. Teams templates let you quickly create rich collaboration spaces with channels for different topics and preinstall apps to pull in mission-critical content and services. Teams templates provide a predefined team structure that can help you easily create consistent teams across your organization. Currently you can create a team from a template in Teams or using [Microsoft Graph](get-started-with-teams-templates.md).

This article describes the properties that can be defined in templates, what base template types are, and how you can use a few samples requests to create a team from a template.

This article is for you if you're responsible for planning, deploying, and managing multiple teams across your organization

## Teams template capabilities

Most properties in a team are included and supported by templates. But there are a few properties and features that aren't currently supported. The following table provides a quick summary of what's included and what's not included in Teams templates.

| **Team properties supported by Teams templates** | **Team properties not yet supported by Teams templates** |
| ------------------------------------------------ | -------------------------------------------------------- |
| Base template type | Team membership |
| Team name | Team picture |
| Team description | Channel settings |
| Team visibility (public or private) | Connectors |
| Team settings (for example, member, guest, @ mentions) | Files and content |
| Autofavorite channel | |
| Installed app | |
| Pinned tabs | |

> [!NOTE]
> We'll be adding more template capabilities in future releases of Microsoft Teams, so check back for the most up-to-date information on supported properties.

## What are base template types

Base template types are special templates that Microsoft created for specific industries. These base templates often contain proprietary apps that aren't available in the apps store.

Once a base template type is defined, you can extend or override these special templates with additional properties that you'd like to specify. Some base template types contain properties that can't be overridden.

> [!NOTE]
> Pre-defined base templates provided in Microsoft Teams can be duplicated but not edited.

| Base template type | baseTemplateId | Properties that come with this base template |
| ------------------ | -------------- | ----------------------------------------------------- |
| Adopt Office 365 |`com.microsoft.teams.template.AdoptOffice365`|  Channels: <ul><li>General</li> <li>Announcements</li> <li>Champions corner</li> <li>Team forms</li></ul> Apps: <ul><li>Wiki</li>  <li>Calendar</li> |
| Manage a project |`com.microsoft.teams.template.ManageAProject`| Channels: <ul><li>General</li> <li>Announcements</li> <li>Resources</li> <li>Planning</li></ul> Apps:<ul><li>Wiki</li><li>OneNote</li><li>Planner</li><li>Lists</li>  </ul> |
| Manage an event|`com.microsoft.teams.template.ManageAnEvent` | Channels: <ul><li>General</li> <li>Announcements</li> <li>Budget</li> <li>Content</li><li>Logistics</li> <li>Planning</li> <li> Marketing and PR</li></ul> Apps:<ul><li>Wiki</li><li>Website</li> <li>YouTube</li> <li>Planner</li> <li>OneNote</li></ul> |
|Onboard employees|`com.microsoft.teams.template.OnboardEmployees` | Channels: <ul><li>General</li> <li>Announcements</li> <li>Employee chat</li> <li>Training</li></ul>Apps:<ul><li>Wiki</li><li>Communities</li><li>Planner</li></ul>|
|Organize help desk| `com.microsoft.teams.template.OrganizeHelpDesk`|Channels:<ul><li>General</li><li>Announcements</li><li>FAQ</li></ul>Apps:<ul><li>Wiki</li><li>OneNote</li><li>Planner </li><li>Praise</li></ul> |
| Collaborate on patient care| `healthcareWard`| Channels:<ul><li>General</li><li>Announcements</li><li>Huddles</li><li>Rounds</li><li>Staffing</li><li>Training</li></ul> Apps: <ul><li>Wiki</li><li>Lists  </li></ul>|
| Collaborate on global crisis or event |`com.microsoft.teams.template.CollaborateOnAGlobalCrisisOrEvent`| Channels: <ul><li>General<li>Announcements</li><li>World news</li><li>Business continuity</li><li>Remote working</li><li>Internal comms</li><li>External comms</li><li>Approvals request</li><li>Customer complaints</li><li>Kudos</li><li>Executive update</li></ul>Apps: <ul><li>Praise</li><li>Wiki</li><li>Website</li><li>Planner</li></ul>|
|Collaborate within a bank branch| `com.microsoft.teams.template.CollaborateWithinABankBranch`|Channels: <ul><li>General<li>Announcements</li><li>Huddles</li><li>Customer meetings</li><li>Approvals Request </li><li>Coaching</li><li>Skills development</li><li>Loan processing</li><li>Customer complaints</li><li>Kudos</li><li>Fun stuff</li><li>Compliance</li></ul>Apps:<ul><li>Praise </li></ul>|
|Coordinate incident response| `com.microsoft.teams.template.CoordinateIncidentResponse`|Channels: <ul><li>General<li>Announcements</li><li>Logistics</li><li>Planning</li><li>Recovery</li><li>Urgent</li></ul> Apps: <ul><li>Wiki</li><li>Excel</li><li>OneNote</li><li>SharePoint</li><li>Planner</li></ul>|
|Hospital| `healthcareHospital` |Channels: <ul><li>General</li><li>Announcements</li><li>Compliance</li><li>Custodial</li><li>Human resources</li><li>Pharmacy</li></ul> Apps: <ul><li>Wiki</li><li>Lists  </li></ul>|
|Organize a store| `retailStore` |Channels: <ul><li>General<li>Shift handoff</li><li>Learning</li></ul> Apps: <ul><li>Wiki</li><li>Planner</li></ul>|
|Quality and safety |`com.microsoft.teams.template.QualitySafety`|Channels: <ul><li>General<li>Announcements</li><li>Line 1</li><li>Line 2</li><li>Line 3</li><li>Safety</li><li>Training</li><li>Maintenance</li><li>Fun stuff</li></ul> Apps: <ul><li>Wiki</li><li>Planner</li></ul>|
|Retail - manager collaboration| `retailManagerCollaboration` |Channels: <ul><li>General<li>Operations</li><li>Learning</li></ul> Apps: <ul><li>Wiki</li><li>Planner</li></ul>|
||||

For more information about the template categories, see the following categories:

- [Financial templates](financial-teams-templates-in-the-admin-console.md)
- [General templates](general-teams-templates-in-the-admin-console.md)
- [Government templates](government-teams-templates-in-the-admin-console.md)
- [Healthcare templates](expand-teams-across-your-org/healthcare/healthcare-templates-admin-console.md)
- [Manufacturing templates](manufacturing-teams-templates-in-the-admin-console.md)
- [Retail templates](retail-teams-templates-in-the-admin-console.md)

## Template size limits

Templates are limited to a specific number of channels, tabs, and apps.

 > [!Note]
 > You can add more channels, tabs, and apps to the team after it's been created from a template.

|Feature | Limit|
|-|-|
|Channels per template | 15 |
|Tabs per channel in a template | 20 |
|Apps per template | 50|
|||

See [Limits and specifications of Teams](limits-specifications-teams.md) for more information.

## Related topics

- [Create a custom team template](create-a-team-template.md)
- [Create a team template from an existing team template](create-template-from-existing-template.md)
- [Create a template from an existing team](create-template-from-existing-team.md)
