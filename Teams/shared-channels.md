---
title: Shared channels in Microsoft Teams
author: MikePlumleyMSFT
ms.author: mikeplum
manager: serdars
ms.reviewer: arundas
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: Learn how to use and manage shared channels in Microsoft Teams. 
---

# Shared channels in Microsoft Teams

Shared channels in Microsoft Teams create collaboration spaces where you can invite people who are not in the team. Only the users who are owners or members of the shared channel can access the channel. While guests can't be added to a shared channel, you can invite people outside your organization to participate in a shared channel by using Azure AD B2B direct connect.

You might want to use a shared channel if you want to collaborate with a group of people who are all members of different teams. For example, people from engineering, sales, and support who all work on different aspects of the same project or product could use a shared channel to collaborate.

Only members of shared channels can see and participate in shared channels that they are added to. Other members of the team to which the shared channel is connected won't see the channel.

When a shared channel is created, it's linked to the parent team and can't be moved to a different team. Additionally, shared channels can't be converted to standard channels and vice versa.

## Shared channel creation

By default, any team owner or team member can create a shared channel. Guests can't create them. The ability to create shared channels can be managed at the team level and at the organization level. Use [policies](teams-policies.md) to control which users in your organization are allowed to create shared channels. Once you've set the policies, team owners can turn off or turn on the ability for members to create shared channels in the **Settings** tab for a team.

The person who creates a shared channel is the shared channel owner and only the shared channel owner can directly add or remove people from it. A shared channel owner can add anyone from the organization to a shared channel they created. Members of a shared channel have a secure conversation space, and when new 
members are added, they can see all conversations (even old conversations) in that shared channel.

Team owners can see the names of all shared channels in their team and can also delete any shared channel in the team. (A deleted shared channel can be restored within 30 days after it's deleted). Team owners can't see the files in a shared channel or the conversations and member list of a shared channel unless they are members of that shared channel.

Team members can only see shared channels that they've been added to.

## Adding and removing owners and members

A shared channel owner can't be removed through the Teams client if they are the last owner of one or more shared channels.

If a shared channel owner leaves your organization or if they are removed from the Microsoft 365 group associated with the team, a member of the shared channel is automatically promoted to be the shared channel owner.

## Channel owner settings

Each shared channel has its own settings that the channel owner can manage, including the ability to add and remove members, add tabs, and @mentioning for the entire channel. These settings are independent of the parent team settings. When a shared channel is created, it inherits settings from the parent team, after which its settings can be changed independently of the parent team settings.

The shared channel owner can click **Manage channel**, and then use the **Members** and **Settings** tabs to add or remove members and edit settings.

## Shared channel owner and member actions

The following table outlines what actions owners, members, and guests can do in shared channels.

|Action  |Team owner|Team member|Team guest|Shared channel owner|Shared channel member|Shared channel external participant|
|---------|---------|---------|---------|---------|---------|---------|
|Create shared channel|Admin controlled|Admin and team owner controlled|No|Yes|No|No|
|Delete shared channel|Yes|No|No|Yes|No|No|
|Leave shared channel|N/A|N/A|N/A|Yes unless they are the last owner|Yes|Yes|
|Edit shared channel|No|N/A|N/A|Yes|No|No|
|Restore deleted shared channel|Yes|No|No|Yes|No|No|
|Add members|No|N/A|N/A|Yes|No|No|
|Edit settings|No|N/A|N/A|Yes|No|No|
|Manage tabs and apps|No|N/A|N/A|Yes, apps must be installed for the team|Channel owner controlled|No|

## Shared channel SharePoint sites

Each shared channel has [its own SharePoint site](/SharePoint/teams-connected-sites). The separate site is to ensure access to shared channel files is restricted to only members of the shared channel. These sites are created with a document library by default, and can be easily enhanced to a full-featured site through the [site management interface](https://support.office.com/article/A2F2A5C2-093D-4897-8B7F-37F86D83DF04). Each site is created in the same geographic region as the site for the parent team. These lightweight sites have a custom template ID, "TEAMCHANNEL#0", for easier management through PowerShell and Graph API. 

> [!NOTE]
> Only users with owner or member permissions in the channel will have access to content in the shared channel site.

A shared channel site syncs data classification from the site of the parent team. Membership to the site owner and member groups are kept in sync with the membership of the shared channel. Site permissions for a shared channel site can't be managed independently through SharePoint. 

Teams manages the lifecycle of the shared channel site. If the site is deleted outside of Teams, it is restored automatically within four hours as long as the shared channel is still active. If the site is permanently deleted, a new site is provisioned for the shared channel.

If a shared channel or a team containing a shared channel is restored, the sites are restored with it. If a shared channel site is restored and it's beyond the 30-day soft delete window for the shared channel, the site operates as a standalone site.

## Shared channel message compliance records

Records for messages sent in a shared channel are delivered to the mailbox of all shared channel members, rather than to a group mailbox. The titles of the records are formatted to indicate which shared channel they were sent from.

For more information about performing an eDiscovery search for shared channel messages, see [Conduct an eDiscovery investigation of content in Microsoft Teams](ediscovery-investigation.md).

## Considerations around file access in shared channels

Files, folders, and OneNote notebooks in a shared channel can be shared with people outside the channel by using [standard SharePoint file sharing](https://support.microsoft.com/office/1fe37332-0f9a-4719-970e-d2578da4941c).

If a user is granted access to a file, folder, or notebook in a shared channel through SharePoint, removing the user from the team or shared channel won't remove the user's access to the file, folder, or notebook.

If an existing notebook is added as a tab to a shared channel, access to the shared channel isn't changed and the notebook retains its existing permissions.

## Shared channel limitations

Currently, shared channels support connectors and tabs (except Stream, Planner, and Forms).

Each team can have a maximum of 30 shared channels and each shared channel can have a maximum of 250 members. The 30 shared channel limit is in addition to the 200 standard channel limit per team. 

When you create a team from an existing team, any shared channels in the existing team won't be copied over.

Notifications from shared channels are not included in missed activity emails.

## Related topics

[Overview of teams and channels in Teams](teams-channels-overview.md)

[Private channels in Microsoft Teams](/microsoftteams/private-channels)