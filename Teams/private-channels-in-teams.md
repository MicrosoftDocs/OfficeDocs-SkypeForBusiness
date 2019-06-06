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

Private channels is a new channel type in Microsoft Teams that creates focused spaces for collaboration within your teams. Only those users who are owners or members of the private channel can access the channel. You might want to use a private channel if you want to limit communication to those who have a need to know or if you want to facilitate communication between a group of people assigned to a specific project, without having to create an additional team to manage.

For example, a private channel is useful in the following scenarios:

- A group of people in a team want a focused space to collaborate without having to create a separate team.
- A subset of people in a team want a private channel to discuss sensitive information, such as budgets, resourcing, strategic positioning, and so on.

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

By default, any team owner or member can create a private channel. Guests can't create them. On the **Settings** tab for a team, team owners can set whether members are allowed to create private channels. Admins can also control whether individual user are allowed to create private channels in the Microsoft Teams admin center.

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

Each private channel has its own independent settings, including the ability to add tabs and connectors, and @mentioning for the entire channel.

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

### Channels dashboard

The channels dashboard for each team shows the private channels in the team. A lock icon indicates a private channel. Team owners can see all private channels on the dashboard. Team members can only see those private channels that they are added to.

![Screen shot of private channels in a team](media/private-channels-in-teams.png)

### Private channel settings

Private channel settings are independent of the parent team. To manage settings for a private channel, click **Manage channel**, and then use the **Members** and **Settings** tabs to add or remove members and configure settings.  

![Screen shot of private channel settings](media/private-channels-in-teams-channel-settings.png)

### Classification

Private channels are subject to the same group classification as the parent team. To learn more about group classifications, see <TBD>.

### eDiscovery and General Data Protection Regulation (GDPR)

eDiscovery and GDPR work differently in Private channels than in standard channels. Records for messages sent in a channel are delivered to the mailbox of all channel participants, rather than to a group mailbox. The titles of the records are formatted to indicate which private channel they were sent from.

### Retention

Retention is set to the general policy for all teams and channels. Scoped policy for specific teams won’t apply to the private channels in them.

### Policies

You can set a per-user policy to control private channel creation.

> [!NOTE]
> Microsoft introduced a new policy, TeamsAppPolicy, to control what parts of the Teams client are enabled, such as instant messaging, meetings, chat, and channels. When this new policy is available, TeamsUpgradePolicy will be updated so that when an admin tries to grant an instance of TeamsUpgradePolicy to a user, it will first check to ensure that TeamsAppPolicy is correctly configured for the mode. If not, the action fails with an error explaining how the other policy must first be set.

#### Set a policy to control private channel creation

When private channels rolls out to your organization, the ability to create private channels is enabled by default for all Teams users in your organization. As an admin, you might want to consider taking proactive steps before the feature rolls out by allowing only select pilot users to create private channels and disabling the ability for all other users in your organization.

To do this, follow these steps:

1. Run the following to disable private channel creation for your organization.

    ```
    Set-CsTeamsChannelsPolicy -Identity Global -AllowPrivateChannelCreation $false
    ```
2. Run the following to create a custom TeamsChannelPolicy and assign it to users.

    ```
    New-CsTeamsChannelsPolicy -Identity PrivateChannels -AllowPrivateChannelCreation $true
    ```
    You can also edit and use the default policy.
3. Assign the policy to users. These users can be team owners or team members.

    ```
    Grant-CsTeamsChannelsPolicy -Identity user@domain.com -PolicyName PrivateChannels
    ```

## Related topics
- 