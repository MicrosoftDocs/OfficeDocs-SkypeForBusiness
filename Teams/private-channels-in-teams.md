---
title: Private channels in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 
ms.reviewer: suchakr
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to use and manage private teams in Microsoft Teams. 
---

# Private channels in Microsoft Teams

Microsoft Teams is a rich collaboration tool for communication among individuals in an organization. Private channels is a new channel type that creates focused spaces for collaboration within your teams. Only those users who are owners or members of the private channel have access to the channel. You might want to use a private channel if you want to limit communication to those who have a need to know or if you want to facilitate communication between a group of people assigned to a specific project, without creating an additional team to manage.

For example, a private channel is useful in the following scenarios:

- A group of people in a team want a focused space to collaborate without having to create a separate team.
- A subset of people in a team want a private channel to discuss sensitive information, such as budgets, resourcing, strategic positioning, and so on.

Each private channel has a separate SharePoint site collection. The parent SharePoint site and the private channel SharePoint site settings are synced when the private channel is created and can be changed independently afterwards.

## Private channel limitations

Private channels don't support the following:

- Wikis
- Apps and bots
- Scheduled channel meetings

Each team can have a maximum of 30 private channels and a each private channel can have a maximum of 250 members.

## When to create a private channel

To determine whether a private channel is appropriate, consider the following questions about who you want to work with and what the collaboration is about.

|Is there already a team that has these people as team members?  |Does this work need to be kept private from others?  |Are there multiple distinct topics to discuss?  |Recommendation  |
|---------|---------|---------|---------|
|Yes      |Yes         |Yes         |Create a private channel in the existing team or consider creating dedicated Private Channels for each topic.         |
|Yes     |Yes         |No         |Create a private channel in the existing team.         |
|Yes     |No         |No         |Create a channel in the existing team.         |
|No     |No         |No         |Consider creating a new team.         |
|No     |No         |Yes         |Consider creating a new team and then, depending on the confidentiality of each topic, consider creating separate standard or private channels for each topic.         |
|No     |Yes         |No         |Create a new team or create a new private channel in an existing team.         |

## Private channel creation and membership

By default, any team owner or member can create a private channel. Guests can't create them. Each team has a setting to disable private channel creation for members. In the future, there will be a setting to disable private channel creation for individual users.

Any member of a team can be added to a private channel in the team, including guests.
If a team member leaves a team, that user will also leave all private channels in the team. They must be added to private channels again if they are added back to the team.

A team member can't leave a team if they are the last team owner of one or more private channels.

Team owners can see the name and description of all private channels in their team. They can also delete any private channel in the team. (Careful – this can’t be undone!) Team owners can see the files in a private channel, but they can’t see conversations unless they are members of that private channel. 

The following table shows who can view what in a private channel.

|Feature  |Team owner can see |Team members can see |
|---------|---------|---------|
|Name and description    |All private channels in the team]         |Only the private channels that they are added to         |
|Conversations and tabs     |Only when added to the private channel         |Only when added to the private channel         |
|Files and content    |Only when added to the private channel        |Only when added to the private channel         |

Members of a private channel have a secure conversation space, and when new members are added, they can see all conversations (even old conversations) in that private channel.

## Manage private channels

Each private channel has its own independent settings, including the ability to add tabs and connectors, and @mentioning for the entire channel.

The following table outlines which actions are available to owners, members, and guests.

|Action  |Team owner|Team member|Team guest|Private channel owner|Private channel member|Private channel guest|
|---------|---------|---------|---------|---------|---------|---------|
|Createprivate channel|Yes|Yes<sup>1</sup>|No|N/A|N/A|N/A|
|Delete private channel|Yes|No|No|Yes|No|No|
|Leave private channel|N/A|N/A|N/A|Yes<sup>2</sup>|Yes|Yes|
|Edit private channel|No|N/A|N/A|Yes|No|No|
|Restore deleted private channel|Yes|No|No|Yes|No|No|
|Add members|No|N/A|N/A|Yes|No|No|
|Edit settings|No|N/A|N/A|Yes|No|No|
|Manage tabs, apps, and connectors|No|N/A|N/A|Yes<sup>3</sup>|Yes<sup>4</sup>|No|

## Related topics
- 