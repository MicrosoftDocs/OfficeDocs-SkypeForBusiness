---
title: Manage tags in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: acolonna, salu
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn to manage how tags are used in your organization in Microsoft Teams.
---

# Manage tags in Microsoft Teams

Tags in Microsoft Teams let users quickly and easily connect with a subset of people on a team. You can create and assign custom tags to categorize people based on attributes, such as role, project, skill, or location. Or, tags can be automatically assigned to people based on their schedule and shift information in the [Shifts app](https://support.microsoft.com/office/get-started-in-shifts-5f3e30d8-1821-4904-be26-c3cd25a497d6). After a tag is added to one or multiple team members, it can be used in @mentions by anyone on the team in a channel post to notify only those people who are assigned that tag of a conversation.

As mentioned earlier, there are two kinds of tags in Teams.

- **Custom tags**: Team owners and team members (if they have the permissions) can manually create and assign tags to people. For example, a “Designer” or “Radiologist” tag will reach those sets of people on a team without having to type their names.
- **Tagging by shift**: With this feature, people are automatically assigned tags that match their schedule and shift group name in the [Shifts app](https://support.microsoft.com/office/get-started-in-shifts-5f3e30d8-1821-4904-be26-c3cd25a497d6#bkmk_usetags) in Teams. For example, the “EngineerOnCall” tag reaches all engineers who are scheduled in Shifts to work at the time the tag is used in a chat or channel post. With tagging by shift, Teams takes the guesswork out of knowing the name of on-shift staff when users need to quickly relay information.

> [!NOTE]
> Tags are not supported in private or shared channels.

## How tags work

A tag can be manually added (custom tag) or automatically assigned to a person on a specific team (by setting up Shifts in the Shifts app). The tag can then be used in @mentions on the **To** line in a chat or in a post on any standard channel of the team. Here are some examples of how tags can be used in Teams:

- A store manager posts an announcement to a channel to notify all cashiers.
- A hospital administrator sends a message to all radiologists in a channel.
- A marketing manager starts a group chat with all designers.
- A nurse sends a message to all on-call cardiologists.
- A system engineer posts an announcement to a channel to notify all on-shift field engineers.

When a tag is @mentioned in a channel conversation, team members associated with the tag will get notified, just like any other @mention.

## Manage tags for your organization

As an admin, you can control how tags are used across your organization in the Microsoft Teams admin center. Note that you can’t use PowerShell to manage tags.

:::image type="content" source="media/manage-tags-admin-settings-shifts.png" alt-text="Screenshot of tagging settings in the Microsoft Teams admin center.":::

A team can have up to 100 tags, up to 200 team members can be assigned to a tag, and up to 25 tags in the same team be assigned to a single user.

### Set who can manage tags

By default, team owners can create, edit, and delete tags. You can change the **Who can manage tags** setting to allow team owners and team members to manage tags, or you can turn off tags for your organization.

1. In the left navigation of the Microsoft Teams admin center, click **Teams** \> **Teams settings**.

2. Under **Tagging**, next to **Who can manage tags**, select one of the following options:

    - **Team owners and members**: Allow team owners and members to manage tags.
    - **Team owners**: Allow team owners to manage tags.
    - **Not enabled**: Turn off tags.

### Configure tagging settings

You can configure the following tags settings to control how tags are used across your organization.

1. In the left navigation of the Microsoft Teams admin center, click **Teams** \> **Teams settings**.

2. Under **Tagging**, set the following, depending on the needs of your organization.

    - **Team owners can change who can manage tags**: When you turn on this setting, team owners can set whether team members can create and manage tags within a team and the value of the **Who can manage tags** setting is the default value for each team. If you turn off this setting, the **Who can manage tags** setting can’t be changed per team.
    - **Suggested tags**: Use this to add a set of default tags. You can add up to 25 tags, and each tag can contain a maximum of 25 characters. Team owners and members (if the feature is enabled for them) can use these suggestions, add to them, or create a new set of tags.
    - **Custom tags**: Turn on this setting to let people add tags other than the suggested default tags that you set. If this is turned off, people can only use the suggested default tags. If you turn this off, make sure that you add one or more default tags.
    - **Shifts app can apply tags**: Turn on this setting to enable the Shifts app to automatically assign tags to people who are on-shift in real time. These tags will match a user's schedule and group name in Shifts. Notifications are only sent to those people who are on-shift at the time the tag is used in a chat or channel post.

## Related topics

[Using tags in Teams](https://support.office.com/article/using-tags-in-teams-667bd56f-32b8-4118-9a0b-56807c96d91e)

[Manage the Shifts app](expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams.md)

[Shifts Help documentation](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b)
