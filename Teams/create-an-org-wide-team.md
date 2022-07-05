---
title: Create an organization-wide team in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: phlouie
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to create and manage an organization-wide team in Teams to provide an automatic way for everyone in a small to medium-sized organization to collaborate.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection:
  - M365-collaboration
appliesto:
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Create an organization-wide team in Microsoft Teams

Organization-wide teams provide an automatic way for everyone in a small-to-medium-sized organization to be part of a single and collaborative team.

With organization-wide teams, global admins can easily create a public team that has the following characteristics:
- Pulls in every user in the organization
- Keeps the membership up to date with Active Directory as users join and leave the organization.

Only global admins can create organization-wide teams. Currently, an organization-wide team is limited to organizations with no more than 10,000 users. There's also a limit of five organization-wide teams per tenant. When creating a team, if these requirements are met, global admins will see **Org-wide** as an option when they select **Build a team from scratch**.

![Screenshot of the Org-wide option to create an organization-wide team.](media/create-org-wide-team.png "Screen shot of the Org-wide option to create an organization-wide team")

When an organization-wide team is created, all global admins and Teams service administrators are added as team owners and all active users are added as team members. Unlicensed users are also added to the team. The first time an unlicensed user signs in to Teams, the user is assigned a Microsoft Teams Exploratory license. To learn more about the Exploratory license, check out [Manage the Microsoft Teams Exploratory license](teams-exploratory.md).

The following types of accounts won't be added to your organization-wide team:

- Accounts that are blocked from sign-in
- Guest users
- Resource or service accounts (for example, accounts associated with auto attendants and call queues)
- Room or equipment accounts
- Accounts backed by a shared mailbox

As your organization's directory is updated to include new active users or to disable accounts of users who no longer work at your company, changes are automatically synced and the users are added or removed from the team. Team members can't leave an organization-wide team. As a team owner, you can manually add or remove users if needed.

> [!NOTE]
>
> - If you don't see the **Org-wide** option when creating a team and you're a global admin, you might have reached the five organization-wide teams limit, or your organization might have more than the current size limit of 10,000 members. We're looking to increase this limit in the future. Org-wide teams aren't yet available for Teams for Education.
> - Rooms that aren't a part of a room list, equipment, and resource accounts might be added or synced to the organization-wide team. Team owners can easily remove these accounts from the team.
> - All actions by the system to add or remove members are posted in the General channel. The channel will also be marked as having new activity in the Teams client.
> - We'll automatically create an organization-wide team for your organization if your organization is new to Teams and has no more than 5,000 users. The team name will reflect the tenant name and will have a General channel. Global admins can edit this team like any other team.

## Best practices

To get the most out of your organization-wide team, we recommend that team owners do the following tasks:

### Allow only team owners to post to the General channel

Reduce channel noise by having only team owners post to the General channel.

1. Go to the team, locate the General channel, and then select **... More options** > **Manage channel**.
2. On the **Channel settings** tab, click **Permissions**, and then select **Only owners can post messages**.

### Turn off @team and @[team name] mentions

Reduce @mentions to keep them from overloading the entire organization.

1. Go to the team and click **... More options** \> **Manage Team**.
2. On the **Settings** tab, click **@mentions** \> turn off **Show members the option to @team or @[team name]**.

### Automatically show important channels

Show important channels to ensure everyone in your organization engages in specific conversations. To learn more, see [Auto-favorite channels for the whole team](https://support.office.com/article/auto-favorite-channels-for-the-whole-team-a948272c-5aa5-429c-863c-4e1e1cd6b0f6).

### Set up channel moderation

Consider setting up channel moderation and giving moderator capabilities to certain team members. (When moderation is set up, team owners are given moderator capabilities automatically.) Moderators can:

- Control who can start a new post in a channel
- Add and remove moderators
- Control whether team members can reply to existing channel messages
- Control whether bots and connectors can submit channel messages.

For more information, see [Set up and manage channel moderation in Microsoft Teams](manage-channel-moderation-in-teams.md).

### Remove accounts that might not belong

Even though members can't leave an organization-wide team, as a team owner, you can manage the team roster by removing accounts that don't belong. **Make sure you use Teams to remove users from your org-wide team**. If you use another way to remove a user, such as the Microsoft 365 admin center or from a group in Outlook, the user might be added back to the organization-wide team.

## FAQ

### Is there a way to create an organization-wide team other than using the Teams client?

Only global admins can create an organization-wide team by using the Teams client. If your organization limits creating teams to using PowerShell, the recommended workaround is to add your global admins to the security group of users who can create a team.

For more information, see [Manage who can create groups](/microsoft-365/admin/create-groups/manage-creation-of-groups).

If this workaround isn't an option, you can use PowerShell to create a public team and add a global admin as the team owner. Then, have the global admin click **More options** next to the team name, click **Edit team**, and then change the privacy to **Org-wide - Everyone in your organization will be automatically added**.

> [!NOTE]
> Only team owners can access the **Edit team** option and only global admins can see the **Org-wide** option.

### Is there a way to convert an existing team to an organization-wide team?

Global admins can convert an existing team to an organization-wide team by editing it in Teams client. Go to the team name, click **More options** > **Edit team**.

### Can I create an organization-wide team using a team template?

Team templates can't be used to create an organization-wide team. Work for this feature is currently in progress.

## See also

Watch a video about [How to create an org-wide team in Microsoft Teams](https://www.youtube.com/watch?v=x3qGlwwCz_w).
