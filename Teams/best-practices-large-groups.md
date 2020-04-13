---
title: Manage large teams in Microsoft Teams - best practices
ms.reviewer: pbethi
author: CindyChurch
ms.author: cichur
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
description: Learn about best practices for managing large teams in Microsoft Teams to meet your organization's needs.
f1.keywords:
- NOCSH
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

Manage large teams in Microsoft Teams - best practices
======================================================

Microsoft Teams is equally effective at facilitating communications between small groups with dozens of members and large groups with thousands of members. Review [Limits and specifications for Microsoft Teams](limits-specifications-teams.md) for updates on team sizes.

## Value of large teams

Large teams are very useful in enabling the following collaboration scenarios:

- **Department-wide collaboration**: If your organization has multiple departments such as Finance, Operations, R&D etc., then you can create a single team that includes all members in a specific department. Now all communications relevant to a department can be shared in this team, which facilitates instant reach and engagement from members.

- **Collaboration in employee resource groups**: Organizations often have large groups of people with mutual interests who belong to a different department or workgroup. As an example, there can be a group of people who share a passion for personal finance and investing. It's often hard to connect in a large organization. To develop communities for such groups, tenant admins can create a large team that serves as a public company-wide resource group that anyone can join and take advantage of. Eventually, these communities collect information that both new and existing members can enjoy.

- **Collaboration between internal and external members**: Popular products often develop a community of early adopters who are eager to try new product releases and provide feedback. Early adopters develop a relationship with product groups to help shape the product. In such scenarios, tenant admins can set up a large team which includes both internal product groups and external product evaluators to facilitate a rich product development process. These teams can also provide customer support to a select set of customers.

## Create teams from existing groups

Use contact groups, security groups, or Office groups to jump start your team. You can import a group to make a team or create a team from an Office group.

**Import a group to make a team**: When you import a group with up to 3,500 members into Teams, Teams automatically calculates the total number of members in the group. This is a one-time import only and future changes in the group will not automatically be updated in Teams.

**Create a team from a large Office 365 group**: When you create a team from a large Office 365 group, members are automatically part of the Office 365 group **and** the team. In the future, as team members join or leave the Office 365 group, they're automatically added or removed from the team.

See [Create an org-wide team in Microsoft Teams](create-an-org-wide-team.md) for details.

## Create channels to focus discussions

You can narrow the group discussions by creating focused channels. See [Best practices for organizing teams in Microsoft Teams](best-practices-organizing.md).

## Restrict channel creation

If any team member is allowed to create channels, that team can have channel sprawl. Team owners should turn off channel create, update, delete, and restore for members in **Settings > Member permissions**. See [Overview of teams and channels in Microsoft Teams](teams-channels-overview.md).

![Screen image that shows the member permissions section of the admin console Settings tab.](media/no-channel-creation.png "Screen image that member permissions section of the admin console Settings tab. The allow members to create or delete channels options are unchecked.")

## Add favorite channels

In order to speed up new user engagement and content discovery, you can select favorite channels that are available to the user by default. In the **Channels** pane of the admin controls, check the channels under the **Show for members** column.

![Screen image that shows the channels pane of the admin console.](media/favorite-channels.png "Screen image that shows channels pane of the admin console. Some channels are checked for Show for members.")

 See [Create your first teams and channels in Microsoft Teams](get-started-with-teams-create-your-first-teams-and-channels.md) for details.

## Disable applications and bots in large teams

To prevent addition of distracting applications or bots, team owners can disable, add, remove, and upload apps and connectors for team members. In the admin console under **Settings > Member permissions**, uncheck the three options that allow members to add apps or connectors.

![Screen image that shows the Member permissions section of the Settings pane.](media/disable-bots-connectors.png "Screen image that shows the Member permission section of the Settings pane. The options for allow members to add apps or connectors are unchecked.")

See [Apps, bots, & connectors in Microsoft Teams](deploy-apps-microsoft-teams-landing-page.md).

## Regulate team and channel mentions

Team and channel mentions can be used to draw the attention of the whole team to certain channel posts. Once a mention is used in a post, a notification is sent to thousands of team members. If the notifications are too frequent, then team members can become overloaded and might complain to team owners. To prevent team or channel mentions, turn off team and channel mentions for members by unchecking the boxes in the teams **Settings > @mentions** pane.

![Screen image that shows the at Mentions section of the Settings pane.](media/no-at-mentions.png "Screen image that shows the at Mentions section of the Settings pane. The options for show and give members access to at mentions are unchecked.")

## Consider setting up moderation in your channels

Team owners can turn on moderation for a channel to control who can start new posts and reply to posts in that channel. When you set up moderation, you can choose one or more team members to be moderators. Team owners are moderators by default. For more information, see [Set up and manage channel moderation in Microsoft Teams](manage-channel-moderation-in-teams.md).

## Related topics

- [Best practices for organizing Teams in Microsoft Teams](best-practices-organizing.md)
- [Create an org-wide team in Microsoft Teams](create-an-org-wide-team.md)
