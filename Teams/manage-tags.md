---
title: Manage tags in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: acolonna
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
description: Learn to manage how tags are used in your organization in Microsoft Teams. 
---

# Manage tags in Microsoft Teams

Tags in Microsoft Teams let users communicate with a subset of people on a team. Tags can be added to one or multiple team members to easily connect with the right subset of people. Team owners and members (if the feature is enabled for them) can add one or more tags to a person. The tags can then be used in @mentions by anyone on the team in a channel post or to start a conversation with only those people who are assigned that tag.

> [!NOTE]
> Tags are not yet supported in private channels. Tags are not yet available in US Government Community Cloud (GCC), GCC High, or Department of Defense (DoD) organizations. 

## How tags work

A tag can be added to a person on a specific team. After a tag is added, it can be used in @mentions in a chat or in any standard channel of the team. Here's some examples of how tags can be used in Teams:

- A store manager wants to post an announcement to a channel and notify all cashiers.
- A group product manager wants to message all product managers in a channel.
- A hospital administrator wants to send a message to all radiologists in a channel.
- A marketing manager wants to start a group chat with all designers. 

To learn more, check out [Using tags in Teams](https://support.office.com/article/using-tags-in-teams-667bd56f-32b8-4118-9a0b-56807c96d91e).

## Manage tags for your organization

As an admin, you can control who can add tags and how tags are used across your organization in the Microsoft Teams admin center.

![Screenshot of tagging settings in the Microsoft Teams admin center](media/manage-tags-admin-settings.png)

### Set who can add tags

By default, team owners can add tags. You can change this setting to allow team owners and team members to add tags or you can turn off tags for your organization.

1. In the left navigation of the Microsoft Teams admin center, click **Org-wide settings** > **Teams settings**.
2. Under **Tagging**, next to **Tagging is enabled for**, select one of the following options:

    - **Team owners and members**: Allow team owners and members to add tags.
    - **Team owners**: Allow team owners to add tags.
    - **Disabled**: Turn off tags.

### Configure tags settings

You can configure the following tags settings to control how tags are used across your organization.

1. In the left navigation of the Microsoft Teams admin center, click **Org-wide settings** > **Teams settings**.
2. Under **Tagging**, set the following, depending on the needs of your organization.

    - **Team owner can override who can apply tags**: When this is turned on, team owners can allow or disallow members to add tags in team settings.
    - **Members can add additional tags**: If you allow team members to add tags, turn this on to let team members add tags other than the suggested default tags that you set. If this is turned off, team members can only use the default tags.
    - **Suggested default tags**: Use this to add a set of default tags. You can add up to 25 tags, and each tag can contain a maximum of 25 characters. Team owners and members (if the feature is enabled for them) can use these suggestions, add to them, or create a new set of tags.

## Manage tags settings for a team

If you turned on the **Team owner can override who can apply tags** setting in the Microsoft Teams admin center, team owners can set whether members can add tags at the team level. To do this, on the **Settings** tab for a team, go to **Tags**, and then choose who can add tags.

![Screenshot of the tags setting at the team level](media/manage-tags-team-settings.png)

## Add tags in Teams

In Teams, the **Members** tab of the Manage team page for a team includes a **Tags** column. Team owners and members (if the feature is enabled for them) can click **Manage tags** next to a member to see the list of suggested tags for that member and add tags to the list.

![Screenshot of how to apply tags in the Teams client ](media/manage-tags-teams.png) 
