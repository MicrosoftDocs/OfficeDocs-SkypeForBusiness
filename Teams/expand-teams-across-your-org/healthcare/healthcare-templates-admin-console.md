---
title: "Use healthcare team templates"
author: cichur
ms.author: v-cichur
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
searchScope:
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Healthcare
  - microsoftcloud-healthcare
appliesto: 
  - Microsoft Teams
ms.reviewer: 
description: Use team templates in the admin center or with Microsoft Graph to quickly and easily create teams for your healthcare organization.
ms.custom: seo-marvel-mar2020
---
# Use healthcare team templates

Team templates in Microsoft Teams allow you to quickly and easily create teams by providing a predefined template of settings, channels, and pre-installed apps.

For healthcare organizations, templates can be especially powerful, as they help provide structure for staff to become oriented with how to effectively use Teams. As an admin, you can use templates to easily deploy consistent teams across your healthcare organization.

We offer team templates designed specifically for healthcare organizations. Use these templates to quickly create teams for your staff to communicate and collaborate on patient care and operational needs within or between wards and departments. In this article, we introduce you to each of these templates and recommend how to use them.

This article is for you if you're responsible for planning, deploying, and managing multiple teams across your healthcare organization. How you manage and work with team templates depends on whether you're an admin or developer.

|If you're: | Then, you: |
| ---- | --------- |
| An admin or IT pro |[Manage team templates in the Teams admin center](#manage-team-templates-in-the-teams-admin-center) |
| A developer | [Use Microsoft Graph](#use-team-templates-with-microsoft-graph) |

## Manage team templates in the Teams admin center

As an admin, you can manage team templates in the Microsoft Teams admin center. Here, you can view details about each template. You can also apply template policies to control which templates your staff can see in Teams for creating teams. To learn more, see [Get started with team templates in the Teams admin center](../../get-started-with-teams-templates-in-the-admin-console.md).

### Healthcare team templates

To view these templates, in the left navigation of the Teams admin center, go to **Manage Teams** > **Teams templates**.

#### Patient care

 Streamline healthcare communication and collaboration within a ward, pod, or department. You can use this template to facilitate patient management and the operational needs of a ward. This template is meant for communication and collaboration within a ward, pod, or department. 

| Base template type |baseTemplateId| Properties that come with this base template |
| ------------------ |---|----------------------------------------------------- |
| Patient care |`healthcareWard` | Channels:<ul><li>General</li><li>Announcements</li><li>Huddles</li><li>Rounds</li><li>Staffing</li><li>Training</li></ul> Apps: <ul><li>Wiki</li><li>Lists</li></ul>|
||||

#### Hospital

Streamline communication and collaboration between multiple wards, pods, and departments within a hospital. This template includes a set of base channels for hospital operations, and can be self-extended to include specialties, ad hoc.

| Base template type |baseTemplateId | Properties that come with this base template |
| ------------------|-- |----------------------------------------------------- |
|Hospital|`healthcareHospital`|Channels: <ul><li>General</li><li>Announcements</li><li>Compliance</li><li>Custodial</li><li>Human resources</li><li>Pharmacy</li></ul> Apps: <ul><li>Wiki</li><li>Lists </li></ul>|
||||


## Use team templates with Microsoft Graph

Developers can use Microsoft Graph to create teams with the team templates. We currently offer two built-in healthcare templates that you can use for a variety of situations. To learn more about team templates in general, see [Get started with team templates](../../get-started-with-teams-templates.md). And for information about team templates and Microsoft Graph, see [Microsoft Teams API overview](/graph/teams-concept-overview?view=graph-rest-1.0) and [teamsTemplate resource type](/graph/api/resources/teamstemplate?view=graph-rest-1.0).

### Ward template

The ward template is meant for communication and collaboration within a ward, pod, or department. The template can be used to facilitate patient management, as well as the operational needs of a ward. For example, ward announcements can be posted in the *Announcements* channel and shifts can be managed in *Staffing*. If you're looking to streamline your ward operations, then this template is for you.

|Base Template Type |baseTemplateId |Baseline Template channels|
|:--- |:---|:---|
|Healthcare - Ward | `https://graph.microsoft.com/beta/`<br>`teamsTemplates('healthcareWard')`   | Announcements\* <br> Huddles\* <br> Rounds\* <br> Staffing\* <br> Training\* |
|     | |         |

\* Auto-favorited

### Hospital template

The hospital template is meant for communication and collaboration between multiple wards, pods, and departments within a hospital. Included in this template are several operational channels including *Announcements*, *Custodial*, and *Pharmacy*, but we also provide a script below which extends the template with a variety of additional department or specialty-centric channels that you can add to, delete from, or edit to your liking. For example, if you have an *Endocrinology* department, but don't need a channel for *Ophthalmology*, then the script can be adapted to include an *Endocrinology* channel and remove the *Ophthalmology* channel. We recommend that these specialty or ward-modeled channels not be auto-favorited to avoid notification saturation. Users generally favorite any channels that they find relevant.

|Base Template Type |baseTemplateId |Baseline Template channels|
|:--- |:---|:---|
|Healthcare - Hospital | `https://graph.microsoft.com/beta/`<br>`teamsTemplates('healthcareHospital')`   | Announcements\* <br> Compliance\* <br> Custodial <br> Human Resources <br> Pharmacy |
| | |  |

\* Auto-favorited 

### How to use healthcare templates

To use these templates, change the 'template@odata.bind' property in the request body from 'standard' to the TemplateIDs above.  For more information on how to deploy team templates, see the Microsoft Graph article on how to [create a team](/graph/api/team-post?view=graph-rest-beta).

> [!NOTE]
> The channels in the template will be automatically created under the **General** tab.

#### Example: Hospital template extension script

``` Powershell
{ 
          "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('healthcareHospital')",
          "DisplayName": "Contoso Hospital",
          "Description": "Team for all staff in Contoso Hospital",
          "Channels": [
            {
              "displayName": "Ambulatory",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Anesthesiology",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Cardiology",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "CCU",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Ear, Nose, and Throat",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Emergency Care",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Family Medicine",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Gynecology",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "ICU",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Mother-Baby",
              "IsFavoriteByDefault": false
            }, 
            {
              "displayName": "Neonatal",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Neurology",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Oncology",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Ophthalmology",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "PACU",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Psychiatric",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Radiology",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Rehabilitation",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Surgical",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Urology",
              "IsFavoriteByDefault": false
            },
            {
              "displayName": "Women's Health",
              "IsFavoriteByDefault": false
            }
          ],
          "Apps": [
            {
              "Id": "1542629c-01b3-4a6d-8f76-1938b779e48d"
            }
          ]
          }

```

### Related articles

[Get started with team templates using Microsoft Graph](../../get-started-with-teams-templates.md)

[Get started with Team for Healthcare organizations](teams-in-hc.md)