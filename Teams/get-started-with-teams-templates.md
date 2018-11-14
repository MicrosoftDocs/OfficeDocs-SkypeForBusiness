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
robots: NOINDEX, NOFOLLOW
search.appverid: MET150
description: Learn how to use Teams templates to create a team with predefined channels.
ms.custom:
- NewAdminCenter_Update
appliesto: 
- Microsoft Teams
---

# Get started with Teams templates 

Team templates are pre-built definitions of a team's structure designed around a business need or project. You can use team templates to quickly create rich collaboration spaces with channels for different topics and preinstall apps to pull in mission-critical content and services. Team templates provide a predefined team structure that can help you easily create consistent teams across your organization. 

In this article, we'll explain the properties that can be defined in templates, what base template types are, and how you can use a few sample requests to create a team from a template.
 
This article is for you if you're:

•	Responsible for planning, deploying, and managing multiple teams across your organization
•	A developer looking to create a team with predefined channels and apps programmatically

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
| Education - Class team<sup>1</sup> | [https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Education-CT.json#](https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Education-CT.json#) | Apps:<br/> - OneNote Class Notebook (pinned to the **General** tab) <br/> - Assignments app (pinned to the **General** tab) <br/><br/> Team properties <br/> - Team visibility set to **HiddenMembership** (cannot be overridden) |
| Education - Staff team<sup>1</sup> | [https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Education-ST.json#](https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Education-ST.json#) | Apps<br/> - OneNote Staff Notebook (pinned to the **General** tab) |

<sup>1</sup> Publication in late October, 2018

> [!NOTE]
> We'll be adding more base template types in future releases of Microsoft Teams, so check back for the most up-to-date information on supported properties.

## Examples 

You can start creating a team via template by installing [Microsoft Graph](https://developer.microsoft.com/en-us/graph/docs/concepts/overview).

### Create a team from a template

#### Requests

**Request to create a team with the standard base template**

~~~
POST   /teams
Authorization: Bearer <TOKEN>
Content-Type: application/json
{
    "baseTemplateId": "https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Standard.json",
    "schemaVersion": "1.0",
    
    "teamDisplayName": "My Sample Team",
    "teamDescription": "My Sample Team’s Description",
}

~~~

**Request to create a team with an extra channel and disallow members from deleting channels**

~~~
POST   /teams
Authorization: Bearer <TOKEN>
Content-Type: application/json
{
    "baseTemplateId": "https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Standard.json",
    "schemaVersion": "1.0",
    
    "teamDisplayName": "My Sample Team",
    "teamDescription": "My Sample Team’s Description",
    "channels": [
        {
            "displayName": "Interns",
            "autoFavorite": false
        }
    ],
    "memberSettings": {
        "allowDeleteChannels": false,
    }
}

~~~

**Request to create a team with all supported properties**

~~~
POST   /teams
Authorization: Bearer <TOKEN>
Content-Type: application/json
{
    "baseTemplateId": "https://teams.microsoft.com/templates/schemas/1.0/TeamTemplate.Standard.json",
    "schemaVersion": "1.0",
 
    "teamType": "Healthcare_CareCoordination",
    "visibility": "Private",
    "teamDisplayName": "My Care Team",
    "teamDescription": "My Care Team’s description",
 
    "channels": [
        {
            "displayName": "General  ",
            "autoFavorite": true,
            "tabs": [
                   {
                       "appId": "0d820ecd-def2-4297-adad-78056cde7c78",
                       "tabDisplayName": "Intranet”
                   }
               ]
        },
        {
            "displayName": "Announcements",
            "autoFavorite": true
        },
        {
            "displayName": "Diabetes",
            "autoFavorite": true
        },
        {
            "displayName": "Cardiovascular",
            "autoFavorite": true
        },
        {
            "displayName": "Registered Nurses",
            "autoFavorite": true
        }
    ],
 
     "memberSettings": {
        "allowCreateUpdateChannels": true,
        "allowDeleteChannels": true,
        "allowAddRemoveApps": true,
        "allowCreateUpdateRemoveTabs": true,
        "allowCreateUpdateRemoveConnectors": true
      },
 
      "guestSettings": {
        "allowCreateUpdateChannels": false,
        "allowDeleteChannels": false
      },
 
      "messagingSettings": {
        "allowUserEditMessages": true,
        "allowUserDeleteMessages": true,
        "allowOwnerDeleteMessages": true,
        "allowTeamMentions": true,
        "allowChannelMentions": true
      },
 
      "funSettings": {
        "allowGiphy": true,
        "giphyContentRating": "moderate",
        "allowStickersAndMemes": true,
        "allowCustomMemes": true
      }
 
 
    "installedApplications": [
      {
        "id": "0d820ecd-def2-4297-adad-78056cde7c78"
      }
    ]
}
~~~

#### Response

~~~
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: /workflow/status/c953c202-7b44-4a63-aa33-364fcb2d65aa
{
    "workflowId": "c953c202-7b44-4a63-aa33-364fcb2d65aa",
    "statusUri": "https://<apihostandpath>/workflow/status/c953c202-7b44-4a63-aa33-364fcb2d65aa"
}
~~~

### Get status

#### Request

~~~
GET   /workflow/status/c953c202-7b44-4a63-aa33-364fcb2d65aa
Authorization: Bearer <TOKEN>
~~~

#### Response

~~~
HTTP/1.1 200 OK
Content-Type: application/json
{
    "status": "[InProgress|Completed|Cancelled|Failed]"
}
~~~

## Related topics

- [Create team](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/team_put_teams) (in preview)
- [New-Team](https://docs.microsoft.com/powershell/module/teams/New-Team?view=teams-ps)
- [Admin training for Microsoft Teams](itadmin-readiness.md)