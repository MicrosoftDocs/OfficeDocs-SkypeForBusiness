---
title: Shared channels in Microsoft Teams
author: MikePlumleyMSFT
ms.author: mikeplum
manager: serdars
ms.reviewer: jasonlewis
ms.date: 08/15/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.custom: chat-teams-channels-revamp
ms.collection: 
  - M365-collaboration
  - m365initiative-securecollab
f1.keywords: 
  - NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use and manage shared channels in Microsoft Teams.
---

# Shared channels in Microsoft Teams

Shared channels in Microsoft Teams create collaboration spaces where you can invite people who are not in the team. Only the users who are owners or members of the shared channel can access the channel. While guests (people with Azure Active Directory guest accounts in your organization.) can't be added to a shared channel, you can invite people outside your organization to participate in a shared channel by using Azure AD B2B direct connect.

You might want to use a shared channel if you want to collaborate with a group of people who are all members of different teams. For example, people from engineering, sales, and support who all work on different aspects of the same project or product could use a shared channel to collaborate.

Only members of shared channels can see and participate in shared channels that they are added to. Other members of the team to which the shared channel is connected won't see the channel.

When a shared channel is created, it's linked to the parent team and can't be moved to a different team. Additionally, shared channels can't be converted to standard channels and vice versa.

[Compare shared channels with other types of channels](/microsoftteams/teams-channels-overview#channel-feature-comparison).

## Getting started with shared channels

Shared channels is enabled by default in Teams. You can choose if people can create shared channels, if they can share them with people outside your organization, and if they can participate in external shared channels by [creating a channel policy](/MicrosoftTeams/teams-policies).

If you plan to share channels with people outside your organization, read [Plan external collaboration](/microsoft-365/solutions/plan-external-collaboration) for important planning considerations.

Sharing channels with people outside your organization also requires that you configure cross-tenant access settings in Azure AD. Each organization that you want to share channels with must also complete this configuration. See [Collaborate with external participants in a channel](/microsoft-365/solutions/collaborate-teams-direct-connect) for details.

## Shared channel creation

Only team owners can create a shared channel. Team members can't create them. The ability to create shared channels can be managed at the organization level. Use policies to control which users in your organization are allowed to create shared channels.

The person who creates a shared channel becomes the shared channel owner and only the shared channel owner can directly add or remove people from it. (You can add more than one owner if you want.) A shared channel owner can add anyone from the organization to a shared channel they created. Members of a shared channel have a secure conversation space, and when new members are added, they can see all conversations (even old conversations) in that shared channel.

Team owners can see the names of all shared channels in their team and can also delete any shared channel in the team. Team owners can't see the files in a shared channel or the conversations and member list of a shared channel unless they are members of that shared channel.

Team members can only see shared channels that they've been added to.

Cloning a team will not clone the associated shared channels.

## Shared channel deletion

Deleted shared channel can be restored within 30 days after deletion. When a deleted shared channel is restored, all previous memberships (individual and team sharing) will be restored.

Deleted teams can be restored within 30 days after deletion. When a team is deleted, all shared channels will also be deleted. When a deleted team is restored, all shared channels will be restored as well with all sharing relationships.

When a team is archived, individual sharing will remain intact, but sharing with teams other than the parent team will be removed. When archived team is unarchived, all shared channels will be restored with individual sharing only.

## Adding and removing owners and members

A shared channel owner can't be removed through the Teams client if they are the last owner of one or more shared channels.

If the last shared channel owner leaves your organization or if they are removed from the Microsoft 365 group associated with the team, a member of the shared channel from your organization is automatically promoted to be the shared channel owner. If there are no members from your organization to promote, the shared channel will remain ownerless. A Teams admin will have to manually assign a channel owner. Consider adding more than one owner to avoid this situation.

Guests - including those converted to members (in their user type property) - can't be added to a shared channel.

In the Teams admin center, when adding an external participant who also has a guest account in your organization, you must search on *ext:user@domain.com* to get the external participant's organization account rather than the guest account.

> [!NOTE]
> External participants must be added using their UPN, rather than their email address, if the two don't match in Azure Active Directory.

## Channel owner settings

Each shared channel has its own settings that the channel owner can manage, including the ability to add and remove members, add tabs, and @mentioning for the entire channel. These settings are independent of the parent team settings. When a shared channel is created, it inherits settings from the parent team, after which its settings can be changed independently of the parent team settings.

The shared channel owner can click **Manage channel**, and then use the **Members** and **Settings** tabs to add or remove members and edit settings.

## Shared channel owner and member actions

The following table outlines what actions owners, members, and guests can do in shared channels.

|Action  |Team owner|Team member|Team guest|Shared channel owner|Shared channel member|Shared channel external participant|
|---------|---------|---------|---------|---------|---------|---------|
|Create shared channel|Admin controlled|Admin and team owner controlled|No|N/A|No|No|
|Delete shared channel|Yes|No|No|Yes|No|No|
|Leave shared channel|N/A|N/A|N/A|Yes unless they are the last owner|Yes|Yes|
|Edit shared channel|No|N/A|N/A|Yes|No|No|
|Restore deleted shared channel|Yes|No|No|Yes|No|No|
|Add members|No|N/A|N/A|Yes|No|No|
|Edit settings|No|N/A|N/A|Yes|No|No|
|Manage tabs and apps|No|N/A|N/A|Yes, apps must be installed for the team|Channel owner controlled|No|

## Shared channel SharePoint sites

Each shared channel has [its own SharePoint site](/SharePoint/teams-connected-sites). The separate site is to ensure access to shared channel files is restricted to only members of the shared channel. These sites are created with a document library by default, and can be easily enhanced to a full-featured site through the [site management interface](https://support.office.com/article/A2F2A5C2-093D-4897-8B7F-37F86D83DF04). Each site is created in the same geographic region as the site for the parent team. These sites have a custom template ID, "TEAMCHANNEL#1", for easier management through PowerShell and Graph API. 

A shared channel site inherits the sensitivity label of the parent team. This remains true even if the channel is shared directly with another team.

> [!NOTE]
> Only people with owner or member permissions in the channel will have access to content in the shared channel site. People in the parent team and admins won't have access unless they are also channel members.

Membership to the site owner and member groups are kept in sync with the membership of the shared channel. Site permissions for a shared channel site can't be managed independently through SharePoint. 

Teams manages the lifecycle of the shared channel site. If the site is deleted outside of Teams, it is restored automatically within four hours as long as the shared channel is still active. If the site is permanently deleted, a new site is provisioned for the shared channel.

If a shared channel or a team containing a shared channel is restored, the sites are restored with it. If a shared channel site is restored and it's beyond the 30-day soft delete window for the shared channel, the site operates as a standalone site.

## Shared channel messages

Shared channel messages are stored in a dedicated system mailbox associated with the Shared channel rather than the group mailbox.

For information about performing an eDiscovery search for shared channel messages, see [Conduct an eDiscovery investigation of content in Microsoft Teams](ediscovery-investigation.md).

## Considerations around file access in shared channels

Files and folders in a shared channel can be shared with people outside the channel (but not outside the organization) by using [standard SharePoint file sharing](https://support.microsoft.com/office/1fe37332-0f9a-4719-970e-d2578da4941c).

If a user is granted access to a file, folder, or notebook in a shared channel through SharePoint, removing the user from the team or shared channel won't remove the user's access to the file, folder, or notebook.

If an existing notebook is added as a tab to a shared channel, access to the shared channel isn't changed and the notebook retains its existing permissions.

## Resources for your users

The following articles may be helpful for the users in your organization when they use shared channels.

[Create a shared channel in Teams](https://support.microsoft.com/office/80712457-579e-42b2-b54f-112329578aaa)

[Share a channel with people in Teams](https://support.microsoft.com/office/5f60de2d-0080-4e55-b26f-33a9dafa120e)

[Share a channel with a team](https://support.microsoft.com/office/b2e89992-2708-4583-b11e-bbb6edb4f1c3)

[Why use a shared channel versus other channel types in Teams?](https://support.microsoft.com/office/e6ad61d0-6b3f-4e1b-baac-63e2978bd92e)

[Guests and shared channels in Teams](https://support.microsoft.com/office/612de4ce-e7a3-4579-b086-bb8ff9f2d11e)

[Shared channel owner and member roles in Teams](https://support.microsoft.com/office/75b379f4-8e9c-4202-acf1-6ffc3878a2d7)

## Supported apps in shared channels

For information about how to prepare your app for shared channels, see [How to open your app to cross-organizational collaboration with Microsoft Teams Connect](https://mybuild.microsoft.com/sessions/4d84d73c-08de-4f56-990b-2a73b2037df1).

The following apps are supported for use in shared channels. 

- Activity
- Adobe Acrobat Sign
- Asana
- Calling
- Chat
- Code by Vivani
- Conceptboard
- Excel
- FileBrowser
- Files
- Flipgrid
- Freehand by InVision
- HeyTaco
- Jira Cloud
- Kahoot!
- Lists
- Lucidchart
- Lumio
- MeisterTask
- MindMeister
- Mindomo
- Miro
- Monday.com
- MURAL
- Nearpod
- PDF
- Pear Deck
- PowerPoint
- Priority Matrix
- Quicklinks
- Quizlet
- Saved
- Scrum-Poker
- Search
- SharePoint
- SharePoint Pages
- Slido
- Smartsheet
- SurveyMonkey
- Tasks in a Box
- Teams Manager
- TeamViewer
- Teamwork
- Testportal
- TrackingTime
- Trello
- Vevox
- Visio
- VSTS
- Wakelet
- Web
- Wooclap
- Word
- YouTube
- Zendesk
- Zoho Projects

## Related topics

[Limits for shared channels](limits-specifications-teams.md#limits-for-shared-channels)

[B2B direct connect overview](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Configure cross-tenant access settings for B2B direct connect](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Overview of teams and channels in Teams](teams-channels-overview.md)

[Private channels in Microsoft Teams](/microsoftteams/private-channels)

[Shared channels in Microsoft Teams - Microsoft Mechanics](https://youtu.be/rE_QTfkOtnc)
