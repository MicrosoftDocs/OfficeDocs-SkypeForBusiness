---
title: People targeting in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: jastark
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
description: Learn how to control whether private teams can be discovered by Microsoft Teams users through suggestions in the team gallery and search results. 
---

# People targeting in Microsoft Teams

People targeting in Microsoft Teams lets users communicate with a subset of people on a team. People targeting uses tags that can be applied to team members or groups to easily connect with the right subset of people. This feature lets team owners and members (if the feature if enabled for them) assign one or more tags to a person or group. The tags can then be used in @mentions to start a conversation with only those people who are assigned that tag.

## How tags work

A tag can be applied at the team level or organization level.

- **Team level**: The tag is applied to a person on a specific team (such as a role or a shift).
- **Organization level**: The tag is applied to a person or team across your entire organization (such as an office location).

After a tag is applied, it can be used in @mentions in any channel of the team.

Here's some examples of how tags can be used in Teams:

 - A store manager wants to notify a group cashiers in a store to ask a question.
 - A charge nurse wants to message all on-call nurses in a ward.  
 - A Human Resources specialist wants to announce benefit changes to employees in a particular location.
 - A regional marketing manager wants to assign a task to all chefs located in the same Southwest region.
 - A hospital administrator wants to start a conversation with all radiologists in a hospital.

## Manage targeting and tags settings for your organization

As an admin, you can control who can apply tags and how tags are used across your organization in the Microsoft Teams admin center.

![Tags settings ](media/people-targeting-settings.png)

### Set who can apply tags

By default, team owners can apply tags. You can change this setting to allow team owners and team members to apply tags or you can turn off targeting for your organization.

1. In the left navigation of the Microsoft Teams admin center, click **Org-wide settings** > **Teams settings**.
2. Under **Targeting**, next to **Teams targeting is enabled for**, select one of the following options:

    - **Team owners & members**: Allow team owners and members to apply tags.
    - **Team owners**: Allow team owners to apply tags.
    - **Disabled**: Turn off targeting.

### Configure tags settings

You can configure the following tags settings to control how tags are used across your organization.

1. In the left navigation of the Microsoft Teams admin center, click **Org-wide settings** > **Teams settings**.
2. Under **Targeting**, set the following, depending on the needs of your organization.

- **Team owner can override who can apply tags**: When this is turned on, team owners can allow or disallow members to apply tags in team settings.
- **Members can add additional tags**:
- **Default tags that will be suggested**: Use this to add a set of suggested tags. You can add up to 25 suggested tags, and each tag can contain a maximum of 25 characters. A team owner or member (if the feature is enabled for them) can use these suggestions, add to them, or create a new set of tags.

## Manage tags settings for a team

Team owners can set whether members can apply tags and whether to automatically apply tags from your organization's directory and other apps.

To do this, on the **Settings** tab for a team, go to **Tags**, and then choose the  settings that you want.

![Team tags settings](media/people-targeting-team-settings.png)

## Apply tags

In Teams, the **Members** tab of the Manage team page for a team includes a **Tag** column. Team owners and members (if the feature is enabled for them) can click **Manage Tags** next to a member to see the list of suggested tags for that member and add tags to the list.

## Related topics
