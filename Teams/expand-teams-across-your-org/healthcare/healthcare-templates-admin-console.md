---
title: "Create a team using Teams healthcare templates"
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
description: Use Microsoft Teams templates in the admin center or with Microsoft Graph to quickly and easily create teams by providing a predefined template of settings, channels, and apps.
ms.custom: seo-marvel-mar2020
---
# Create a team using Teams healthcare templates

Microsoft Teams templates allow you to quickly and easily create teams by providing a predefined template of settings, channels, and pre-installed apps.

For healthcare organizations, templates can be especially powerful, as they provide structure for users to become oriented with how to effectively use Teams. Templates also allow administrators to deploy consistent teams across their organizations. This article is for you if you're responsible for planning, deploying, and managing multiple teams across your healthcare organization.

Choose a method for creating teams with the Teams healthcare templates:

| Who | Method to use: |
| ---- | --------- |
| Admins and IT Professionals | [Use the Teams admin center](#use-the-teams-templates-in-the-teams-admin-center) to create teams based on the healthcare Teams templates.|
| Developers and systems integrators | [Use the Microsoft Graph](#use-the-teams-templates-with-the-microsoft-graph) to create teams based on the healthcare Teams templates. |

## Use the Teams templates in the Teams admin center

Microsoft Teams admins can use the Teams admin center to create teams with the Teams templates. We currently offer two first-party healthcare templates that you can use for a variety of situations. To learn more about team templates in general, see [Get started with Teams templates in the admin center](../../get-started-with-teams-templates-in-the-admin-console.md).

### Collaborate on patient care

 Streamline healthcare communication and collaboration within a ward, pod, or department. The template can be used to facilitate patient management and operational needs of a ward.

| Base template type |baseTemplateId| Properties that come with this base template |
| ------------------ |---|----------------------------------------------------- |
| Collaborate on patient care |`healthcareWard` | Channels:<ul><li>General</li><li>Announcements</li><li>Huddles</li><li>Rounds</li><li>Staffing</li><li>Training</li></ul> Apps: <ul><li>Wiki</li><li>Lists</li></ul>|
||||

### Hospital

Streamline communication and collaboration between multiple wards, pods, and departments within a hospital. This template includes a set of base channels for hospital operations, and can be self-extended to include specialties, ad-hoc.

| Base template type |baseTemplateId | Properties that come with this base template |
| ------------------|-- |----------------------------------------------------- |
|Hospital|`healthcareHospital`|Channels: <ul><li>General</li><li>Announcements</li><li>Compliance</li><li>Custodial</li><li>Human resources</li><li>Pharmacy</li></ul> Apps: <ul><li>Wiki</li><li>Lists </li></ul>|
||||


## Use the Teams templates with the Microsoft Graph

Developers can use the Microsoft Graph to create teams with the Teams templates. We currently offer two first-party healthcare templates that you can use for a variety of situations. To learn more about team templates in general, see [Get started with Teams templates](../../get-started-with-teams-templates.md). And for information about Teams templates and the Microsoft Graph, see [Microsoft Teams API overview](/graph/teams-concept-overview?view=graph-rest-1.0) and [teamsTemplate resource type](/graph/api/resources/teamstemplate?view=graph-rest-1.0).

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

### How to use first-party templates

To use these templates, simply change the 'template@odata.bind' property in the request body from 'standard' to the TemplateIDs above.  For more information on how to deploy Teams templates, see the Microsoft Graph article on how to [create a Team](/graph/api/team-post?view=graph-rest-beta).

> [!NOTE]
> The channels in the template will automatically be created under the General Tab.

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

### Related topics

[Get started with Teams templates](../../get-started-with-teams-templates.md)

[Get started with Teams for Healthcare organizations](teams-in-hc.md)