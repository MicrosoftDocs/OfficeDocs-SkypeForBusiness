---
title: "Get started with Teams templates for Small and Medium Businesses"
author: kenwith
ms.author: kenwith
manager: serdars
audience: ITPro
ms.topic: conceptual 
ms.service: msteams 
search.appverid: MET150
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration 
appliesto:
- Microsoft Teams
ms.reviewer: lavenkat
description: Get started with Teams templates for Small and Medium Businesses
---

# Get started with Teams templates for Small and Medium Businesses

Microsoft Teams templates allow you to quickly and easily create teams by providing a predefined template of settings, channels, and pre-installed apps.

For small and medium businesses, templates can be especially powerful, as they help administrators to quickly deploy Teams across their organization. Templates also help orient users and get started with using Teams effectively. This article is for you if you're responsible for planning, deploying, and managing multiple teams across your organization.

We currently offer three first party SMB templates that you can leverage for a variety of situations. All templates will create *Private* Teams. Once you have created the Teams and are ready to roll-out to your organization, you can set the privacy to *Org-Wide* or *Public*, as appropriate. To learn more about team templates in general, please see [Get started with Teams templates](get-started-with-teams-templates.md).

## Company-Wide template
The Company-Wide template is meant for communication and collaboration that are relevant for the entire company. You can use the General channel for company-wide announcements, industry news or executive posts. The Human Resources channel is a great place to consolidate all HR-related activities like job posts, new employee onboarding, training and development. The Fun Stuff channel provides a social platform for all random and fun posts.

| Base template type | baseTemplateId | Properties that come with this base template | | ------------------ | -------------- | ----------------------------------------------------- | | SMB - <br>Company-wide | `https://graph.microsoft.com/beta/`<br>` teamsTemplates('SmallBusinessOrgWide')`| Channels <ul><li>General\*</li><li>Human Resources\*</li><li>Fun Stuff\*</li></ul>\*Auto-favorited channels<br> Apps:<ul><li>Company Portal (Website pinned to the **Human Resources** channel) </li><br>Team properties <ul><li>Team visibility set to Private</li></ul> | ||||

To create the Company-Wide team by taking defaults from the pre-defined template, supply the JSON representation of the team object in the request body. To learn more about how to deploy Teams templates, see the Microsoft Graph [article on creating a Team](https://docs.microsoft.com/graph/api/team-post?view=graph-rest-beta).

#### Request 
```http 
POST https://graph.microsoft.com/beta/teams 
Content-Type: application/json 
{
    "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('SmallBusinessOrgWide')",
    "displayName": "Org-wide",
    "description": "All posts that are relevant for entire company (e.g. Company-wide announcements, Exec posts, employee poll/feedback).",
    "visibility": "Private"
}
```

## Executive Team template

The Executive Team template is ideal for creating a team for company executives to communicate and collaborate on company initiatives like annual priorities, fiscal budgets, strategic initiatives, top clients, etc. This template comes with a *Private* channel to invite select users for specific topics.

| Base template type | baseTemplateId | Properties that come with this base template | | ------------------ | -------------- | ----------------------------------------------------- | | SMB - <br>Executives Team | `https://graph.microsoft.com/beta/`<br>` teamsTemplates('SmallBusinessExecutive')`| Channels <ul><li>General\*</li><li>Private \*</li></ul>\*Auto-favorited channels<br> Apps:<ul><li>OneNote (pinned to the **Private** channel)</li>><li>Planner (pinned to the **Private** channel) </li><br>Team properties <ul><li>Team visibility set to Private</li></ul> | ||||

To create the Executives team by taking defaults from the pre-defined template, supply the JSON representation of the team object in the request body. To learn more about how to deploy Teams templates, see the Microsoft Graph [article on creating a Team](https://docs.microsoft.com/graph/api/team-post?view=graph-rest-beta).

#### Request 
```http 
POST https://graph.microsoft.com/beta/teams 
Content-Type: application/json 
{
    "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('SmallBusinessExecutive')",
    "displayName": "Executive",
    "description": "All posts, announcements and daily collaboration and communication for the company’s leadership team.",
    "visibility": "Private"
}
```

## Departmental Team template

The Departmental team template can be used for creating a team for individual departments or for projects. The Finance team template is ideal for all posts, announcements and daily collaboration and communication within the Finance team members (and executive team members as appropriate). The template comes with a *Private* channel to invite select users for specific topics. We also provide the script below for the Finance team which can be used to extend the template to additional departments or specific projects by adding, deleting from or editing to your liking. For example, if you have a *Marketing* department, then the script can be adapted by renaming the team from *Finance* to *Marketing* to create a new Marketing team

| Base template type | baseTemplateId | Properties that come with this base template | | ------------------ | -------------- | ----------------------------------------------------- | | SMB - <br>Finance | `https://graph.microsoft.com/beta/`<br>` teamsTemplates('SmallBusinessFinance')`| Channels <ul><li>General\*</li><li>Private \*</li></ul>\*Auto-favorited channels<br> Apps:<ul><li>OneNote (pinned to the **Private** channel)</li>><li>Planner (pinned to the **Private** channel) </li><br>Team properties <ul><li>Team visibility set to Private</li></ul> | ||||

To create the Finance team by taking defaults from the pre-defined template, supply the JSON representation of the team object in the request body. To learn more about how to deploy Teams templates, see the Microsoft Graph [article on creating a Team](https://docs.microsoft.com/graph/api/team-post?view=graph-rest-beta).

#### Request 
```http 
POST https://graph.microsoft.com/beta/teams 
Content-Type: application/json 
{
    "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('SmallBusinessFinance')",
    "displayName": "Finance",
    "description": "All posts, announcements and daily collaboration and communication within the Finance team members (and exec team members as appropriate).",
    "visibility": "Private"
}
``

### Example: Finance Team template extension script

``` Powershell
{
  "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('standard')",
  "displayName": "Finance",
  "description": "Finance Team",
  "channels": 
   [
        {
            "displayName": "Private",
            "isFavoriteByDefault": true,
            "description": "Invite a more select audience for specific topics.",
             "tabs": 
             [
                {
                    "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('0d820ecd-def2-4297-adad-78056cde7c78')",
                    "name": "OneNote"
                },
                {
                    "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.planner')",
                    "name": "Planner"
                }
            ]
        }
    ],
    "memberSettings": 
    {
        "allowCreateUpdateChannels": true,
        "allowDeleteChannels": true,
       "allowAddRemoveApps": true,
        "allowCreateUpdateRemoveTabs": true,
        "allowCreateUpdateRemoveConnectors": true
    },
    "guestSettings": 
    {
        "allowCreateUpdateChannels": false,
        "allowDeleteChannels": false
    },
    "funSettings": 
    {
        "allowGiphy": true,
        "giphyContentRating": "Moderate",
        "allowStickersAndMemes": true,
        "allowCustomMemes": true
    },
    "messagingSettings": 
    {
        "allowUserEditMessages": true,
        "allowUserDeleteMessages": true,
        "allowOwnerDeleteMessages": true,
        "allowTeamMentions": true,
        "allowChannelMentions": true
    },
    "discoverySettings": 
    {
        "showInTeamsSearchAndSuggestions": true
    },
    "installedApps": 
    [
        {
            "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('0d820ecd-def2-4297-adad-78056cde7c78')"
        },
        {
            "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.planner')"
        }
    ]
}

```

## Related topics

- [Get started with Teams templates](get-started-with-teams-templates.md)
- [Create team](https://docs.microsoft.com/graph/api/team-post?view=graph-rest-beta) (in preview)

