---
title: Manage tags in Microsoft Teams
author: lana-chin
ms.author: v-chinlana
manager: jtremper
ms.reviewer: yinchang
ms.date: 03/08/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.custom: chat-teams-channels-revamp
ms.collection: 
  - M365-collaboration
  - m365-frontline
appliesto: 
  - Microsoft Teams
  - Microsoft 365 for frontline workers
ms.localizationpriority: medium
search.appverid: MET150
description: Learn to manage how tags are used in your organization in Microsoft Teams.
---

# Manage tags in Microsoft Teams

Tags in Microsoft Teams let users quickly and easily connect with a subset of people on a team. There are three kinds of tags in Teams.

- **Custom tags**: Team owners and team members (if they have permissions) can manually create and assign tags to people based on attributes, such as role, project, skill, or location. For example, a "Designer" tag reaches that set of people on a team without having to type their names.

- **Tagging by shift**: With this feature, people are automatically assigned tags that match their schedule and shift group name in the [Shifts app](https://support.microsoft.com/office/get-started-in-shifts-5f3e30d8-1821-4904-be26-c3cd25a497d6) in Teams. For example, the "EngineerOnCall" tag reaches all engineers who are scheduled in Shifts to work at the time the tag is used in a chat or channel post. With tagging by shift, Teams takes the guesswork out of knowing the name of on-shift staff when users need to quickly relay information.

- **Automatic tags** (coming soon): Use automatic tags to reach groups of people by department or job title in Teams channel conversations. For example, the "Store Associate" tag and the "Sales" tag reaches those specific groups of people. These tags are automatically created and assigned based on values mapped from Microsoft Entra attributes that you set through the [deploy frontline dynamic teams experience](/microsoft-365/frontline/deploy-dynamic-teams-at-scale) in the Teams admin center. [Learn more about attribute mapping and targeted communications](/microsoft-365/frontline/set-up-targeted-communications).

After a tag is added to one or multiple team members, it can be used in @mentions by anyone on the team in a channel post to notify only those people who are assigned that tag of a conversation.

If you're a team owner and you want to manage tags for your team, see [Using tags in Teams](https://support.office.com/article/using-tags-in-teams-667bd56f-32b8-4118-9a0b-56807c96d91e).

> [!NOTE]
> Tags are now supported in [private channels](private-channels.md) and [shared channels](shared-channels.md). For shared channels, only direct members of a shared channel can be added to a shared channel tag. People who inherit membership to a shared channel when it's shared with a team can't be added to a shared channel tag.

## How tags work

A tag can be manually added (custom tags), automatically assigned based on shift and schedule information in Shifts, or automatically assigned based on department or job title (automatic tags).

The tag can then be used in @mentions on the **To** line to start a chat (custom tags and shift-based tags) or in a post on any standard channel of the team. Here are some examples of how tags can be used in Teams:

- A store manager posts an announcement to a channel to notify all store associates.
- A hospital administrator sends a message to all radiologists in a channel.
- A marketing manager starts a group chat with all designers.
- A nurse sends a message to all on-call cardiologists.
- A system engineer posts an announcement to a channel to notify all on-shift field engineers.

When a tag is @mentioned in a channel conversation, team members associated with the tag get notified, just like any other @mention.

## Manage tags for your organization

As an admin, you can control how tags are used across your organization in the Microsoft Teams admin center. You can’t use PowerShell to manage tags.

:::image type="content" source="media/manage-tags-admin-settings-shifts.png" alt-text="Screenshot of tagging settings in the Microsoft Teams admin center.":::

A team can have up to 200 tags, up to 200 team members can be assigned to a tag, and up to 25 tags in the same team be assigned to a single user.

### Set who can manage tags

You can change the **Who can manage tags** setting to specify who can manage tags, or you can turn off tags for your organization.

If you haven't selected an option for **Who can manage tags**, the **Microsoft default** setting is used. **Microsoft default** is set to both team owners and members. If you're using Teams for Education, non-owner students can't manage tags when **Who can manage tags** is set to **Team owners** or **Microsoft default**.

We recommend you select a specific value other than **Microsoft default** to ensure that your preferred tag settings are used if the **Microsoft default** setting changes in the future.

1. In the left navigation of the Microsoft Teams admin center, choose **Teams** > **Teams settings**.

2. Under **Tagging**, next to **Who can manage tags**, select one of the following options:

    - **Team owners, members, and guests**: Allow team owners, team members, and guests to manage tags.
    - **Team owners and members**: Allow team owners and team members to manage tags.
    - **Team owners**: Allow team owners to manage tags.
    - **Not enabled**: Turn off tags.

### Configure tagging settings

You can configure the following tags settings to control how tags are used across your organization.

1. In the left navigation of the Teams admin center, choose **Teams** > **Teams settings**.

2. Under **Tagging**, set the following, depending on the needs of your organization.

    - **Team owners can change who can manage tags**: When you turn on this setting, team owners can set whether team members can create and manage tags within a team and the value of the **Who can manage tags** setting is the default value for each team. If you turn off this setting, the **Who can manage tags** setting can’t be changed per team.
    - **Suggested tags**: Use this option to add a set of default tags. You can add up to 25 tags, and each tag can contain a maximum of 25 characters. Team owners and members (if the feature is enabled for them) can use these suggestions, add to them, or create a new set of tags.

      > [!NOTE]
      > Suggested tags is available in classic Teams but will no longer be available in [new Teams](new-teams-desktop-admin.md).

    - **Custom tags**: Turn on this setting to let people add tags other than the suggested default tags that you set. If this setting is turned off, people can only use the suggested default tags. If you turn off this setting, make sure that you add one or more default tags.
    - **Shifts app can apply tags**: Turn on this setting to enable the Shifts app to automatically assign tags to people who are on-shift in real time. These tags match a user's schedule and group name in Shifts. Notifications are only sent to those people who are on-shift at the time the tag is used in a chat or channel post.

## Related articles

- [Set up targeted communications for your frontline](/microsoft-365/frontline/set-up-targeted-communications)
- [Manage the Shifts app](expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams.md)
