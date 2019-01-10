---
title: Get started with Teams templates
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/10/2019
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

Teams templates are pre-built definitions of a team's structure designed around a business need or project. You can use Teams templates to quickly create rich collaboration spaces with channels for different topics and preinstall apps to pull in mission-critical content and services. Teams templates provide a predefined team structure that can help you easily create consistent teams across your organization. 

In this article, we'll explain the properties that can be defined in templates, what base template types are, and how you can use a few sample requests to create a team from a template.
 
This article is for you if you're:

- Responsible for planning, deploying, and managing multiple teams across your organization<br>
- A developer wanting to programmatically create a team with predefined channels and apps 

## Teams template capabilities

Most properties in a team are included and supported by templates. But there are a few properties and features that are not currently supported. The following table provides a quick summary of what's included and what's not included in Teams templates.

| **Team properties supported by Teams templates** | **Team properties not yet supported by Teams templates** |
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

## What are base template types?

Base template types are special templates that Microsoft created for specific industries. These base templates often contain proprietary apps that aren't available in the store and team properties that are not yet supported individually in Teams templates.

Once a base template type is defined, you can extend or override these special templates with additional properties that you'd like to specify. But some base template types contain properties that can't be overridden. 

By default the base template is set to **Standard** which doesn't contain any additional proprietary apps or special properties. Below is the current list of base templates types available.

| Base template type | baseTemplateId | Base template proprietary apps and special properties |
| ------------------ | -------------- | ----------------------------------------------------- |
| Standard | `https://graph.microsoft.com/beta/teams`<br>`Templates/standard` | No additional apps and properties |
| Education - <br>Class team<sup>1</sup> | `https://graph.microsoft.com/beta/teams`<br>`Templates/educationClass` | Apps:<ul><li>OneNote Class Notebook (pinned to the **General** tab) </li><li>Assignments app (pinned to the **General** tab)</li></ul> Team properties:<ul><li>Team visibility set to **HiddenMembership** (cannot be overridden)</li></ul> |
| Education -<br>Staff team<sup>1</sup> | `https://graph.microsoft.com/beta/teams`<br>`Templates/educationStaff` | Apps:<ul><li>OneNote Staff Notebook (pinned to the **General** tab)</li></ul> |
|Education -<br>PLC team |`https://graph.microsoft.com/beta/teams`<br>`Templates/educationProfessionalLearningCommunity` | Apps:<ul><li>OneNote PLC Notebook (pinned to the **General** tab)</ul></li>|
|||

<sup>1</sup> Publication in late October, 2018

> [!NOTE]
> We'll be adding more base template types in future releases of Microsoft Teams, so check back for the most up-to-date information on supported properties.

## Examples 

You can start using a template to create a team by using the [Microsoft Graph API](https://docs.microsoft.com/graph/api/team-post?view=graph-rest-beta).

### Create a team from a template

#### Requests

**Request to create a team with the standard base template**

~~~
POST /teams
Authorization: Bearer <TOKEN>
Content-Type: application/json
{
  "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates/standard",
  "displayName": "Sample Team",
  "description": "Sample Team’s Description"
}

~~~

**Request to create a team with an extra channel and disallow members from deleting channels**

~~~
POST /teams
Authorization: Bearer <TOKEN>
Content-Type: application/json
{
  "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates/standard",
  "displayName": "My Sample Team",
  "description": "My Sample Team’s Description",
  "channels": [
    {
        "displayName": "Random",
        "isFavoriteByDefault": true
    }
              ],
    "memberSettings": {
        "allowDeleteChannels": false
    }
}

~~~

**Request to create a team with all supported properties**

~~~
POST /teams
Authorization: Bearer <TOKEN>
Content-Type: application/json
{
    "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('standard')",
    "visibility": "Private",
    "displayName": "Sample Engineering Team",
    "description": "This is a sample engineering team, used to showcase the range of properties 
supported by this API",
    "channels": [
        {
            "displayName": "Announcements 📢",
            "isFavoriteByDefault": true,
            "description": "This is a sample announcements channel that is favorited by default. Use this 
channel to make important team, product, and service announcements."
        },
        {
            "displayName": "Training 🏋️",
            "isFavoriteByDefault": true,
            "description": "This is a sample training channel that is favorited by default and contains an 
example of pinned website and YouTube tabs.",
            "tabs": [
                {
                    "teamsApp@odata.bind":
"https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.web')",
                   "name": "A Pinned Website",
                    "configuration": {
                        "contentUrl": "https://docs.microsoft.com/en-us/microsoftteams/microsoft-teams"
                    }
                },
                {
                    "teamsApp@odata.bind": 
"https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.youtube')",
                    "name": "A Pinned YouTube Video",
                    "configuration": {
                        "contentUrl": "https://tabs.teams.microsoft.com/Youtube/Home/YoutubeTab?
videoId=X8krAMdGvCQ",
                        "websiteUrl": "https://www.youtube.com/watch?v=X8krAMdGvCQ"
                    }
                }
            ]
        },
        {
"displayName": "Planning 📅 ",
            "description": "This is a sample of a channel that is not favorited by default, these channels 
will appear in the more channels overflow menu.",
            "isFavoriteByDefault": false
        },
        {
            "displayName": "Issues and Feedback 🐞",
            "description": "This is a sample of a channel that is not favorited by default, these channels 
will appear in the more channels overflow menu."
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
    "funSettings": {
        "allowGiphy": true,
        "giphyContentRating": "Moderate",
        "allowStickersAndMemes": true,
        "allowCustomMemes": true
    },
    "messagingSettings": {
        "allowUserEditMessages": true,
        "allowUserDeleteMessages": true,
        "allowOwnerDeleteMessages": true,
        "allowTeamMentions": true,
        "allowChannelMentions": true
    },
    "installedApps": [
        {
            "teamsApp@odata.bind": 
"https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')"
        },
        {
            "teamsApp@odata.bind": 
"https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')"
        }
    ]
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

- [Create team](https://docs.microsoft.com/graph/api/team-post?view=graph-rest-beta) (in preview)
- [New-Team](https://docs.microsoft.com/powershell/module/teams/New-Team?view=teams-ps)
- [Admin training for Microsoft Teams](itadmin-readiness.md)