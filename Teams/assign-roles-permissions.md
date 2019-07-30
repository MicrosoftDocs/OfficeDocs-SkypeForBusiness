---
title: Assign team owners and members in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: dansteve
search.appverid: MET150
description: Learn to assign team owner and member roles and permissions in Microsoft Teams including permissions to create teams.
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Assign team owners and members in Microsoft Teams
=================================================

> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]

Within Microsoft Teams there are two user roles: **owner** and **member**. By default, a user who creates a new team is granted the owner status. In addition, owners and members can have moderator capabilities for a channel (provided that moderation has been set up). If a team is created from an existing Office 365 Group, permissions are inherited.

The table below shows the difference in permissions between an owner and a member.


|                                   | Team Owner | Team Member |
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
|          **Add members**          |  Yes<sup>3</sup>   |     No<sup>4</sup>    |
|          **Request to add members**          |  N/A   |     Yes<sup>5</sup>     |
|           **Add tabs**            |    Yes     |    Yes<sup>2</sup>|
|        **Add connectors**         |    Yes     |    Yes<sup>2</sup>|
|           **Add bots**            |    Yes     |    Yes<sup>2</sup>|

<sup>1</sup> Team owners can create teams unless they've been restricted from doing so. [Permissions to create teams](#permissions-to-create-teams) below.<br>
<sup>2</sup> An owner can turn off these items at the team level, in which case members would not have access to them.<br>
<sup>3</sup> After adding a member to a team, an owner can also promote a member to owner status. It is also possible for an owner to demote their own status to a member.<br>
<sup>4</sup> Team members can add other members to a public team.<br>
<sup>5</sup> While a team member can't directly add members to a private team, they can request someone to be added to a team they're already a member of. When a member requests someone to be added to a team, team owners receive an alert that they have a pending request that they can accept or deny.

*To learn more about permissions for private channels, see [Private channels in Teams](private-channels-in-teams.md).

> [!NOTE]
> Owners can make other members owners in the **View teams** option. A team can have up to 100 owners. We recommend that you have at least a few owners to help manage the team; this will also prevent orphaned groups if a sole owner leaves your organization. For more information about orphaned groups, see [Assign a new owner to an orphaned group](https://support.office.com/article/Assign-a-new-owner-to-an-orphaned-group-86bb3db6-8857-45d1-95c8-f6d540e45732).

## Moderator capabilities

In addition to other capabilities, team owners and members can have moderator capabilities for a channel (provided that moderation is turned on for a team). Moderators can start new posts in a channel and control whether team members can reply to existing channel messages. They can also control whether bots and connectors can submit channel messages.

Moderator capabilities are assigned at the channel level. Team owners have moderator capabilities by default. Team members have moderator capabilities turned off by default, but a team owner can give moderator capabilities for a channel to a team member. Moderators within a channel can add and remove other moderators within that channel.

For more information about moderator capabilities, see [Set up and manage channel moderation in Microsoft Teams](manage-channel-moderation-in-teams.md).

## Assign a user role

To assign a user role, in Teams, select the team name and click **More options** > **Manage team**. On the **Members** tab, you can add members and choose owners and moderators (if you have sufficient permissions). For more information , see [Change team settings in Teams](https://support.office.com/article/ce053b04-1b8e-4796-baa8-90dc427b3acc).

## Permissions to create teams

By default, all users with a mailbox in Exchange Online have permissions to create Office 365 groups and therefore a team within Microsoft Teams. You can have tighter control and restrict the creation of new teams and thus the creation of new Office 365 groups by delegating group creation and management rights to a set of users. For instructions, see [Manage who can create Office 365 Groups](https://support.office.com/article/manage-who-can-create-office-365-groups-4c46c8cb-17d0-44b5-9776-005fced8e618).


||||
|---------|---------|---------|
| ![An icon representing a decision point](media/Assign_roles_and_permissions_in_Microsoft_Teams_image2.png)     |Decision Point         |Will all Microsoft Teams users be able to create Teams (recommended)?         |
| ![An icon representing the next steps](media/Assign_roles_and_permissions_in_Microsoft_Teams_image3.png)    |Next Steps         |Modify the default permissions for who can create Office 365 groups if you need to limit who can create Teams         |
