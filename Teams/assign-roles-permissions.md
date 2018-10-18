---
title: Assign team owners and members in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 08/27/2018
ms.topic: article
ms.service: msteams
ms.reviewer: dansteve
search.appverid: MET150
description: Learn to assign team owner and member roles and permissions in Microsoft Teams including permissions to create teams.
localization_priority: Normal
MS.collection: Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
---

Assign team owners and members in Microsoft Teams
=================================================

> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]

Within Microsoft Teams there are two user roles: **Owner** and **Member**. By default, a user who creates a new team is granted the Owner status. If a team is created from an existing Office 365 Group, permissions are inherited.

The table below shows the difference in permissions between an owner and a member:


|                                   | Team Owner | Team Member |
|-----------------------------------|------------|-------------|
|          **Create team**          |    Yes     |     No      |
|          **Leave team**           |    Yes     |     Yes     |
|  **Edit team name/description**   |    Yes     |     No      |
|          **Delete team**          |    Yes     |     No      |
|          **Add channel**          |    Yes     |    Yes\*    |
| **Edit channel name/description** |    Yes     |    Yes\*    |
|        **Delete channel**         |    Yes     |    Yes\*    |
|          **Add members**          |  Yes\*\*   |     No      |
|           **Add tabs**            |    Yes     |    Yes\*    |
|        **Add connectors**         |    Yes     |    Yes\*    |
|           **Add bots**            |    Yes     |    Yes\*    |

\* These items can be turned off by an owner at a team level, in which case members would not have access to them.

\*\*After adding a member to a team, an Owner can also promote a Member to Owner status. It is also possible for an Owner to demote their own status to a Member.



> [!NOTE]
> Owners can make other members owners in the View teams option. A team can have up to 100 owners. It's recommended to have at least a few owners to help manage the team; this will also prevent orphaned groups if the sole owner leaves your organization. For more information about orphaned groups, see [Assign a new owner to an orphaned group](https://support.office.com/article/Assign-a-new-owner-to-an-orphaned-group-86bb3db6-8857-45d1-95c8-f6d540e45732).


Permissions to create teams
---------------------------

By default, all users with a mailbox in Exchange Online have permissions to create Office 365 groups and therefore a team within Microsoft Teams. You can have tighter control and restrict the creation of new teams and thus the creation of new Office 365 groups by delegating group creation and management rights to a set of users. For instructions, see [Manage who can create Office 365 Groups](https://support.office.com/article/manage-who-can-create-office-365-groups-4c46c8cb-17d0-44b5-9776-005fced8e618).


||||
|---------|---------|---------|
| ![Decision Point icon.](media/Assign_roles_and_permissions_in_Microsoft_Teams_image2.png)     |Decision Point         |Will all Microsoft Teams users be able to create Teams (recommended)?         |
| ![Next Steps icon.](media/Assign_roles_and_permissions_in_Microsoft_Teams_image3.png)    |Next Steps         |Modify the default permissions for who can create Office 365 groups if you need to limit who can create Teams         |
