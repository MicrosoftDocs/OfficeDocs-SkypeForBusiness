---
title: Create an org-wide team in Microsoft Teams
author: LanaChin
ms.author: v-lanac
ms.reviewer: phlouie
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to create and manage an org-wide team in Teams. 
localization_priority: Normal
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# Create an org-wide team in Microsoft Teams

Org-wide teams provide an automatic way for everyone in a small to medium-sized organization to be a part of a single team for collaboration.

With org-wide teams, global admins can easily create a public team that pulls in every user in the organization and keeps the membership up to date with Active Directory as users join and leave the organization. Only global admins can create org-wide teams and currently an org-wide team is limited to organizations with no more than 5,000 users. There's also a limit of five org-wide teams per tenant. If these requirements are met, global admins will see **Org-wide** as an option when they select **Build a team from scratch** when creating a team. 

![Screen shot of the Org-wide option to create an org-wide team](media/create-org-wide-team.png "Screen shot of the Org-wide option to create an org-wide team")

When an org-wide team is created, all global admins are added as team owners and all active users are added as team members. Unlicensed users are also added to the team. The first time an unlicensed user signs in to Teams, the user is assigned a Microsoft Teams Commercial Cloud Trial license. To learn more about the trial license, check out [Manage the Teams Commercial Cloud Trial offer](iw-trial-teams.md). 

These types of accounts won't be added to your org-wide team:

- Accounts that are blocked from sign in
- Guest users
- Service accounts
- Room or equipment accounts
- Accounts backed by a shared mailbox

As your organization's directory is updated to include new active users or if users no longer work at your company and their Teams license is disabled, changes are automatically synced and the users are added or removed from the team. Team members can't leave an org-wide team. As a team owner, you can manually add or remove users if needed.

> [!NOTE]
> - If you don't see the **Org-wide** option when creating a team and you're a global admin, the feature might still be rolling out or your organization might have more than the current size limit of 5,000 members. We're looking to increase this limit in the future.
> - Rooms that aren't a part of a room list, equipment, and resource accounts might be added or synced to the org-wide team. Team owners can easily remove these accounts from the team.

## Best practices

To get the most out of your org-wide team, we recommend team owners do the following.

### Allow only team owners to post to the General channel

Reduce channel noise by having only team owners post to the General channel. Go to the team and click **˙˙˙ More options** > **Manage Team**. On the **Settings** tab, click **Member permissions** > select **Only owners can post messages**.

### Turn off @team and @[team name] mentions

 Reduce @mentions to keep them from overloading the entire organization. Go to the team and click **˙˙˙ More options** > **Manage Team**. On the **Settings** tab, click <strong>@mentions</strong> > turn off **Show members the option to @team or @[team name]**. 

### Automatically favorite important channels

Favorite important channels to ensure everyone in your organization engages in specific conversations. To learn more, see [Auto-favorite channels for the whole team](https://support.office.com/article/auto-favorite-channels-for-the-whole-team-a948272c-5aa5-429c-863c-4e1e1cd6b0f6).

### Set up channel moderation

Consider setting up channel moderation and giving moderator capabilities to certain team members. (When moderation is set up, team owners are given moderator capabilities automatically.) Moderators can control who can start a new post in a channel, add and remove moderators, control whether team members can reply to existing channel messages, and control whether bots and connectors can submit channel messages. For more information, see [Set up and manage channel moderation in Microsoft Teams](manage-channel-moderation-in-teams.md).

### Remove accounts that might not belong

Even though members can’t leave an org-wide team, as a team owner, you can manage the team roster by removing accounts that don’t belong. Make sure you use Teams to remove users from your org-wide team. If you use another way to remove a user, such as the Microsoft 365 admin center or from a group in Outlook, the user might be added back to the org-wide team.

## FAQ

### Is there a way to create an org-wide team other than using the Teams client?

Global admins can only create an org-wide team by using the Teams client. If your organization limits creating teams to using PowerShell, the recommended workaround is to add your global admins to the security group of users who can create a team. For more information, see [Manage who can create Office 365 Groups](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups).

If this isn't an option, you can use PowerShell to create a public team and add a global admin as the team owner. Then, have the global admin click **More options** next to the team name, click **Edit team**, and then change the privacy to **Org-wide - Everyone in your organization will be automatically added**. Note that only team owners can access the **Edit team** option and only global admins can see the **Org-wide** option.

### Is there a way to convert an existing team to an org-wide team?

Global admins can convert an existing team to an org-wide team by editing it in Teams client. Go to the team name, click **More options** > **Edit team**.
