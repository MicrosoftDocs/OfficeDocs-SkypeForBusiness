---
title: Overview of teams and channels in Microsoft Teams
author: MikePlumleyMSFT
ms.author: mikeplum
ms.reviewer: 
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.subservice: teams-chat
audience: admin
search.appverid: MET150
description: Learn about the different teams, channels, and apps available to a wide variety of requirements such as finance, event planning, sales, and more.
ms.localizationpriority: high
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.dashboard.helparticle.msteamsfiles
  - ms.teamsadmincenter.dashboard.helparticle.teamsandchannels
  - ms.teamsadmincenter.teamschannel.overview
  - ms.teamsadmincenter.teamssettings.overview
  - okr_smb
  - intro-overview
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Overview of teams and channels in Microsoft Teams

Let's get started by thinking about how Microsoft Teams allows individual teams to self-organize and collaborate across business scenarios:

- **Teams** are a collection of people, content, and tools surrounding different projects and outcomes within an organization.

    - Teams can be created to be private to only invited users.
    - Teams can also be created to be public and open and anyone within the organization can join (up to 10,000 members).
    
    A team is designed to bring together a group of people who work closely to get things done. Teams can be dynamic for project-based work (for example, launching a product, creating a digital ship room), as well as ongoing, to reflect the internal structure of your organization (for example, departments and office locations). Conversations, files and notes across team channels are only visible to members of the team.

- **Channels** are dedicated sections within a team to keep conversations organized by specific topics, projects, disciplines—-whatever works for your team. Files that you share in a channel (on the Files tab) are stored in SharePoint. To learn more, read [How SharePoint Online and OneDrive for Business  interact with Teams](SharePoint-OneDrive-interact.md).

    - Channels are places where conversations happen and where the work actually gets done. Channels can be open to all team members (standard channels), selected team members ([private channels](private-channels.md)), or selected people both inside and outside the team ([shared channels](shared-channels.md)).
    - Channels are most valuable when extended with apps that include tabs, connectors, and bots that increase their value to the members of the team. To learn more, see [Apps, bots, & connectors in Teams](deploy-apps-microsoft-teams-landing-page.md).
    
For help using teams and channels, check out [Teams and channels](https://support.office.com/article/df38ae23-8f85-46d3-b071-cb11b9de5499).

See [Limits and specifications for Microsoft Teams](/microsoftteams/limits-specifications-teams) for information on the limits associated with using Teams.

## Membership, roles, and settings

**Team membership**

When Teams is activated for your entire organization, team owners can invite anyone at your organization they work with to join their team. Teams makes it easy for team owners to add people in the organization based on their name. Depending on your organization's settings people from outside of your organization can be added to your teams as guests or as external participants in shared channels. See [Guest Access in Microsoft Teams](guest-access.md) for more information. 

Team owners can also create a team based on an existing Microsoft 365 group. Any changes made to the group membership will be synced with Teams automatically.

**Team roles**

There are two main roles in Teams: 

- **Team owner** - The person who creates the team. Team owners can make any member of their team a co-owner when they invite them to the team or at any point after they've joined the team. Having multiple team owners lets you share the responsibilities of managing settings and membership, including invitations.
- **Team members** - The people who the owners invite to join their team.

In addition, if moderation is set up, team owners and members can have moderator capabilities for a channel. Moderators can start new posts in the channel and control whether team members can reply to existing channel messages. Team owners can assign moderators within a channel. (Team owners have moderator capabilities by default.) Moderators within a channel can add or remove other moderators within that channel. For more information, see [Set up and manage channel moderation in Microsoft Teams](manage-channel-moderation-in-teams.md).

> [!NOTE]
> When you add a team owner, they are also added as a member, except when the team is created in the Teams admin center or when a team is added to a new or existing Microsoft 365 group.

**Team settings** 

Team owners can manage team-wide settings directly in Teams. Settings include the ability to add a team picture, set permissions across team members for creating standard, private, and shared channels, adding tabs and connectors, @mentioning the entire team or channel, and the usage of GIFs, stickers, and memes.

If you are a Teams administrator in Microsoft 365, you have access to system-wide settings in the Teams admin center. These settings can impact the options and defaults team owners see under team settings. For example, you can enable a default channel, "General", for team-wide announcements, discussions, and resources, which will appear across all teams.

By default, all users have permissions to create a team. To modify this, see [Assign roles and permissions in Teams](assign-roles-permissions.md).

One key early planning activity to engage users with Teams is to help people think and understand how Teams can enhance collaboration in their day to day lives. Talk with people and help them select business scenarios where they are currently collaborating in fragmented ways. Bring them together in a channel with the relevant tabs that will help them get their work done. One of the most powerful use cases of Teams is any cross-organizational process.

> [!NOTE]
> When you create a new team or a private or shared channel in Teams, a team site in SharePoint gets automatically created. To edit the site description or classification for this team site, go to the corresponding channel's [settings in Microsoft Teams](https://support.microsoft.com/office/bf39798f-90d2-44fb-a750-55fa05a56f1d).
>
> Learn more about managing [Microsoft Teams connected teams sites](/SharePoint/teams-connected-sites).

This video shows the steps to view and manage a user's team membership.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE53x1L?autoplay=false]

## Channel feature comparison

The following table shows a comparison of Teams features for each channel type.

|Features|Standard channel|Private channel|Shared channel|
|:-------|:---------------|:--------------|:-------------|
|People can be added to the channel without adding them to the team.|No|No|Yes|
|Channel membership can be limited to a subset of the team.|No|Yes|Yes|
|Channel can be shared directly with other teams.|No|No|Yes|
|Channel can be shared directly with its parent team.|N/A|No|Yes|
|Guests can participate in the channel.|Yes|Yes|No|
|External participants (B2B Direct Connect) can participate in the channel.|No|No|Yes|
|Moderation|Yes|No|No|
|Breakout rooms|Yes|No|No|
|Copy link to channel|Yes|No|No|
|Each channel has a dedicated SharePoint site.|No|Yes|Yes|
|Scheduled meetings|Yes|No|Yes|
|Planner|Yes|No|No|
|Bots, connectors, and messaging extensions|Yes|No|No|
|Supported in class teams|Yes|Yes|No|
|Tags|Yes|No|No|
|Analytics|Yes|Yes|No|

## Org-wide teams

If your organization has no more than 10,000 users, you can create an org-wide team. Org-wide teams provide an automatic way for everyone in an organization to be a part of a single team for collaboration. For more information, including best practices for creating and managing an org-wide team, see [Create an org-wide team in Microsoft Teams](create-an-org-wide-team.md).

## Next steps

Read [Chat, teams, channels, & apps in Teams](deploy-chat-teams-channels-microsoft-teams-landing-page.md) to walk through a list of decisions important to your Teams rollout.
