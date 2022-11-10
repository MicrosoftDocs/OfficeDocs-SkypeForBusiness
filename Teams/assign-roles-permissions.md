---
title: Manage user roles in Microsoft Teams 
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.reviewer: dansteve
search.appverid: MET150
description: Learn to assign team owner and member roles and permissions in Microsoft Teams including permissions to create teams.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Manage user roles in Microsoft Teams

**Owner** and **member** are the two user roles within Microsoft Teams. The user who creates a new team is granted owner status by default. Owners and members have different types of permissions and capabilities when interacting with a team and its channels. See [Overview of teams and channels in Microsoft Teams](teams-channels-overview.md) to learn more about roles in Teams.

> [!NOTE]
> If a team is created from an existing Microsoft 365 group, permissions are inherited.

## Assign user roles in Teams

1. Under the team you want to manage, select **More options** and then select **Manage team**.
2. In the Members tab, you can add members and assign owner and moderator roles to members.

To learn more about team settings, see [Change team settings in Teams](https://support.office.com/article/ce053b04-1b8e-4796-baa8-90dc427b3acc).

> [!TIP]
> The **Manage team** option won't appear for pinned channels so be sure to select the team name under **Your teams**.

## Restrict permission to create teams

All users with a mailbox in Exchange Online have permissions to create Microsoft 365 groups and a team within Microsoft Teams. Restrict members from creating new teams and Microsoft 365 groups by delegating group creation and management rights to a set of users. For more information, see [Manage who can create Microsoft 365 Groups](https://support.office.com/article/manage-who-can-create-office-365-groups-4c46c8cb-17d0-44b5-9776-005fced8e618).

The table below shows the difference in permissions between an owner and a member.

### Teams

|Task |Team Owner |Team Member  |
|---------|---------|---------|
|Create/Delete team   |    Yes     |     No    |
|Edit team name/description   |     Yes    |     No     |
|Add members     |     Yes    |     No     |
|Request to add new member   |     Yes    |     No     |

### Channels

|Task |Team Owner |Team Member  |
|---------|---------|---------|
|**Standard channel**
|Create/Delete standard channel     |         |         |
|Edit standard channel name/description    |         |         |
|**Private channel**
|Create/Delete private channel    |         |         |
|Create/Delete shared channel |         |         |
|**Shared channel**
|Edit shared channel name/description    |    No     |     No    |

### Apps

|Task |Team Owner |Team Member  |
|---------|---------|---------|
|Add/Remove apps   |     Yes    |     Yes    |

|    Task                               | Team Owner | Team Member |
|-----------------------------------|------------|-------------|
|          **Create team**          |    Yes<sup>1</sup>     |     No      |
|          **Leave team**           |    Yes     |     Yes     |
|  **Edit team name/description**   |    Yes     |     No      |
|          **Delete team**          |    Yes     |     No      |
|          **Add standard channel**          |    Yes     |    Yes<sup>2</sup>|
| **Edit standard channel name/description** |    Yes     |    Yes<sup>2</sup>|
|        **Delete standard channel**         |    Yes     |    Yes<sup>2</sup>|
|          ***Add private channel**          |    Yes     |    Yes<sup>2</sup>|
| ***Edit private channel name/description** |    No     |    N/A|
|        ***Delete private channel**         |    Yes     |    No|
|          **Add shared channel**          |    Yes     |    No|
| **Edit shared channel name/description** |    No     |    No<sup>6</sup>|
|        **Delete shared channel**         |    Yes     |    No<sup>6</sup>|
|          **Add members**          |  Yes<sup>3</sup>   |     No<sup>4</sup>    |
|          **Request to add members**          |  N/A   |     Yes<sup>5</sup>     |
|           **Add apps**            |    Yes     |    Yes<sup>2</sup>|

<sup>1</sup> Team owners can create teams unless they've been restricted from doing so. [Permissions to create teams](#permissions-to-create-teams) below.<br>
<sup>2</sup> An owner can turn off these items at the team level, in which case members would not have access to them.<br>
<sup>3</sup> After adding a member to a team, an owner can also promote a member to owner status. It is also possible for an owner to demote their own status to a member.<br>
<sup>4</sup> Team members can add other members to a public team.<br>
<sup>5</sup> While a team member can't directly add members to a private team, they can request someone to be added to a team they're already a member of. When a member requests someone to be added to a team, team owners receive an alert that they have a pending request that they can accept or deny.<br>
<sup>6</sup> If the team member is a shared channel owner, they can perform this action.

*To learn more about permissions for private channels, see [Private channels in Teams](private-channels.md).

> [!NOTE]
> Owners can make other members owners in the **View teams** option. A team can have up to 100 owners. We recommend that you have at least a few owners to help manage the team; this will also prevent orphaned groups if a sole owner leaves your organization. For more information about orphaned groups, see [Assign a new owner to an orphaned group](https://support.office.com/article/Assign-a-new-owner-to-an-orphaned-group-86bb3db6-8857-45d1-95c8-f6d540e45732).

## Moderator capabilities

In addition to other capabilities, team owners and members can have moderator capabilities for a channel (provided that moderation is turned on for a team). Moderators can start new posts in a channel and control whether team members can reply to existing channel messages. Moderators can also control whether apps with bots and connectors capability can submit channel messages.

Moderator capabilities are assigned at the channel level. Team owners have moderator capabilities by default. Team members have moderator capabilities turned off by default, but a team owner can give moderator capabilities for a channel to a team member. Moderators within a channel can add and remove other moderators within that channel.

For more information about moderator capabilities, see [Set up and manage channel moderation in Microsoft Teams](manage-channel-moderation-in-teams.md).
