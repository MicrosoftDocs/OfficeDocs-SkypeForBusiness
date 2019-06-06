---
title: Private channels in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 
ms.reviewer: suchakr
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to use and manage private teams in Microsoft Teams. 
---

# Private channels in Microsoft Teams

Private channels in Microsoft Teams create focused spaces for collaboration within your teams. Only those users who are owners or members of the private channel can access the channel. You might want to use a private channel if you want to limit communication to those who have a need to know or if you want to facilitate communication between a group of people assigned to a specific project, without having to create an additional team to manage.

For example, a private channel is useful in the following scenarios:

- A group of people in a team want a focused space to collaborate without having to create a separate team.
- A subset of people in a team want a private channel to discuss sensitive information, such as budgets, resourcing, strategic positioning, and so on.

A lock icon indicates a private channel. Team owners can see all private channels in a team. Team members can only see those private channels that they are added to.

![Screen shot of private channels in a team](media/private-channels-in-teams.png)

Each private channel has a separate SharePoint site collection. The parent SharePoint site and the private channel SharePoint site settings are synced when the private channel is created and can be changed independently afterwards.

## Private channel limitations

Private channels don't support the following:

- Wikis
- Apps and bots
- Scheduled channel meetings

Each team can have a maximum of 30 private channels and a each private channel can have a maximum of 250 members.

## When to create a private channel

To determine whether a private channel is appropriate, consider the following questions about who you want to work with and what the collaboration is about.

|Is there already a team that has these people as team members?  |Does this work need to be kept private from others?  |Are there multiple distinct topics to discuss?  |Recommendation  |
|---------|---------|---------|---------|
|Yes      |Yes         |Yes         |Create a private channel in the existing team or consider creating dedicated private channels for each topic.         |
|Yes     |Yes         |No         |Create a private channel in the existing team.         |
|Yes     |No         |No         |Create a channel in the existing team.         |
|No     |No         |No         |Consider creating a new team.         |
|No     |No         |Yes         |Consider creating a new team and then, depending on the confidentiality of each topic, consider creating separate standard or private channels for each topic.         |
|No     |Yes         |No         |Create a new team or create a new private channel in an existing team.         |

## Private channel creation and membership

By default, any team owner or team member can create a private channel. Guests can't create them. On the **Settings** tab for a team, team owners can turn off or turn on the ability for members to create private channels. Admins can also use policies to control which users in your organization are allowed to create private channels.

Any team member can be added to a private channel in the team, including guests.
If a member leaves a team, that user will also leave all private channels in the team. If the user is added back to the team, they must be added to private channels in the team.

A team member can't leave a team if they are the last owner of one or more private channels.

Team owners can see the name of all private channels in their team. They can also delete any private channel in the team. (Careful – this can’t be undone!) Team owners can't see the files in a private channel or the conversations and member list of a private channel unless they are members of that private channel.

The following table shows who can view what in a private channel.

|Feature  |Team owner can see |Team members can see |
|---------|---------|---------|
|Name and description    |All private channels in the team]         |Only the private channels that they are added to         |
|Conversations and tabs     |Only when added to the private channel         |Only when added to the private channel         |
|Files and content    |Only when added to the private channel        |Only when added to the private channel         |

Members of a private channel have a secure conversation space, and when new members are added, they can see all conversations (even old conversations) in that private channel.

## Manage private channels

Each private channel has its own independent settings, including the ability to add and remove members, add tabs and connectors, and @mentioning for the entire channel. These settings are also independent of the parent team settings.

The following table outlines which actions are available to owners, members, and guests.

|Action  |Team owner|Team member|Team guest|Private channel owner|Private channel member|Private channel guest|
|---------|---------|---------|---------|---------|---------|---------|
|Create private channel|Yes|Yes<sup>1</sup>|No|N/A|N/A|N/A|
|Delete private channel|Yes|No|No|Yes|No|No|
|Leave private channel|N/A|N/A|N/A|Yes<sup>2</sup>|Yes|Yes|
|Edit private channel|No|N/A|N/A|Yes|No|No|
|Restore deleted private channel|Yes|No|No|Yes|No|No|
|Add members|No|N/A|N/A|Yes|No|No|
|Edit settings|No|N/A|N/A|Yes|No|No|
|Manage tabs, apps, and connectors|No|N/A|N/A|Yes<sup>3</sup>|Yes<sup>4</sup>|No|

<sup>1</sup>Each team has a setting to control whether members can create private channels. Team owners can always private channels.<br>
<sup>2</sup>Assuming the private channel owner isn't the last owner of the channel. <br>
<sup>3</sup>Requires the team to have an app installed for a private channel to use it.<br>
<sup>4</sup>Private channel owners can configure this.

To manage membership and settings for a private channel, the private channel owner can click **Manage channel**, and then use the **Members** and **Settings** tabs to add or remove members and edit settings.  

![Screen shot of private channel settings](media/private-channels-in-teams-channel-settings.png)

### Classification

Private channels are subject to the same group classification as the parent team. To learn more about group classifications, see &lt;TBD&gt;.

### eDiscovery and General Data Protection Regulation (GDPR)

eDiscovery and GDPR work differently in private channels than in standard channels. Records for messages sent in a private channel are delivered to the mailbox of all channel participants, rather than to a group mailbox. The titles of the records are formatted to indicate which private channel they were sent from.

### Retention

Retention is set to the general policy for all teams and channels. Scoped policy for specific teams won’t apply to the private channels in them.

### Policies

Admins can set a per-user policy to control which users in your organization can create private channels.

> [!NOTE]
> Microsoft introduced a new policy, TeamsAppPolicy, to control what parts of the Teams client are enabled, such as meetings, chat, and channels. When TeamsAppPolicy is available, TeamsUpgradePolicy will be updated so that when an admin tries to grant an instance of TeamsUpgradePolicy to a user, it will first check to ensure that TeamsAppPolicy is correctly configured for the mode. If not, the action fails with an error explaining how the other policy must first be set.

#### Apply policies to control which users in your organization can create private channels

By default, all Teams users in your organization can create private channels. As an admin, you might want to allow only certain users the ability to create private channels and turn off the ability for all other users in your organization.

To do this, follow these steps:

1. Run the following to disable the ability to create private channels for all users in your organization.

    ```
    Set-CsTeamsChannelsPolicy -Identity Global -AllowPrivateChannelCreation $false
    ```
2. Run the following to create a custom policy to enable the ability to create private channels, and assign it to specific users.

    ```
    New-CsTeamsChannelsPolicy -Identity PrivateChannels -AllowPrivateChannelCreation $true
    ```
    You can also edit and use the default policy.
3. Assign the custom policy to users. These users can be team owners or team members.

    ```
    Grant-CsTeamsChannelsPolicy -Identity user@domain.com -PolicyName PrivateChannels
    ```
## Related topics

- [Overview of teams and channels in Teams](teams-channels-overview.md)
- [Assign team owners and members in Teams](assign-roles-permissions.md)