---
title: Create an org-wide team in Microsoft Teams
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.date: 09/27/2018
ms.topic: article
ms.service: msteams
search.appverid: MET150
description: Learn how to create and manage an org-wide team in Teams. 
localization_priority: Normal
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

# Create an org-wide team in Microsoft Teams

Org-wide teams provide an automatic way for everyone in a small to medium-sized organization to be a part of a single team for collaboration. 
 
With org-wide teams, global administrators can easily create a public team that pulls in every user in the organization and keeps the membership up to date with Active Directory as users join and leave the organization. Only global admins can create org-wide teams and currently an org-wide team is limited to organizations with no more than 1,000 users. If these requirements are met, admins will see **Org-wide** as an option under **Privacy** when creating a team.

![Screen shot of the Org-wide option to create an org-wide team](media/create-org-wide-team.png "Screen shot of the Org-wide option to create an org-wide team")

> [!NOTE]
> If you don't see the **Org-wide** option when creating a team and you're a global admin, the feature might still be rolling out or your organization might have more than the current size limit of 1000 members. We're looking to increase this limit in future.

When an org-wide team is created, all global admins are added as team owners and all active users are added as team members. Users who are disabled for Teams, guest users, and most rooms aren't added to the team. As your organization's directory is updated to include new active users or if users no longer work at your company and their Teams license is disabled, changes are automatically synced and the users are added or removed from the team. Team members can't leave an org-wide team. As a team owner, you can manually add or remove users if needed.

> [!NOTE]
> Rooms that aren't a part of a room list, equipment, and resource accounts might be added or synced to the org-wide team. Team owners can easily remove these accounts from the team.

## Best practices
To get the most out of your org-wide team, we recommend team owners do the following.
### Allow only team owners to post to the General channel
Reduce channel noise by having only team owners post to the General channel. Go to the team and click **More options (…)** > **Manage Team**. On the **Settings** tab, click **Member permissions** > select **Only owners can post messages**.
### Turn off @team and @[team name] mentions
 Reduce @mentions to keep them from overloading the entire organization. Go to the team and click **More options (…)** > **Manage Team**. On the **Settings** tab, click **@mentions** > turn off **Show members the option to @team or @[team name]**. 
### Automatically favorite important channels
 Favorite important channels to ensure everyone in your organization engages in specific conversations. To learn more, see [Auto-favorite channels for the whole team](https://support.office.com/article/auto-favorite-channels-for-the-whole-team-a948272c-5aa5-429c-863c-4e1e1cd6b0f6).
