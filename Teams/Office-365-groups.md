---
title: Microsoft 365 Groups and Microsoft Teams
ms.reviewer: kblevins
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
description: Learn about how Microsoft 365 groups and group memberships work with Microsoft Teams.
---

# Microsoft 365 Groups and Microsoft Teams

Microsoft 365 Groups is the cross-application membership service in Microsoft 365. At a basic level, a Microsoft 365 Group is an object in Azure Active Directory with a list of members and a coupling to related workloads including a SharePoint team site, shared Exchange mailbox, Planner, and OneNote notebook. You can add or remove people to the group just as you would any other group-based security object in Active Directory.

![Diagram showing Microsoft 365 Groups and related services.](/microsoft-365/media/microsoft-365-groups-hub-spoke.png?view=o365-worldwide)

By default, users in Microsoft 365 can create and manage groups. For more information about Microsoft 365 Groups, see [Learn about Microsoft 365 Groups](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) and the [Groups in Microsoft 365 for IT Architects](teams-architecture-solutions-posters.md#groups-in-microsoft-365) poster.

## How Microsoft 365 Groups work with Teams

When you create a team, a Microsoft 365 group is created to manage team membership. The group's related services, such as a SharePoint site, mailbox, etc. are created at the same time.

People who create teams can choose to use an existing Microsoft 365 group if they are an owner of that group. Each channel in the team has a separate folder in the document library. Creating folders directly in the document library does not create channels in the team.

When creating a Microsoft 365 group in Outlook or SharePoint, the group mailbox is visible in Outlook. When creating a team in Teams, the group mailbox is hidden by default. You can use the [Set-UnifiedGroup](/powershell/module/exchange/users-and-groups/set-unifiedgroup) cmdlet with the **HiddenFromExchangeClientsEnabled** parameter to make a mailbox visible.

## Group membership

If you remove a member of a team, they are removed from the Microsoft 365 group as well. Removal from the group immediately removes the team and channels from the Teams client. If you remove a person from a group using the Microsoft 365 admin center, they will no longer have access to the other collaborative aspects such as SharePoint Online document library, Yammer group, or shared OneNote. However, they will still have access to the team's chat functionality for approximately two hours.

As a best practice for managing team members, add and remove them from the Teams client to ensure that permissions updates for other group-connected workloads occur quickly. If you add or remove team members outside of the Teams client (by using the Microsoft 365 admin center, Azure AD, or Exchange Online PowerShell), it can take up to 24 hours for changes to be reflected in Teams.

## Deleting groups and teams

Deleting a Microsoft 365 group will remove the mailbox alias for persistent Outlook/OWA conversations and Teams meeting invites, and mark the SharePoint site for deletion. It takes approximately 20 minutes between the removal of a team and its effect on Outlook. Deleting a team from the Teams client will remove it immediately from view to all who are members of the team. If you remove members of a Microsoft 365 Group that has had Teams functionality enabled on it, there could be a delay of approximately two hours before the team is removed from view in the Teams client for the affected people who were removed.

For details about groups and teams end of lifecycle options, see  [End of lifecycle options for groups, teams, and Yammer](/microsoft-365/solutions/end-life-cycle-groups-teams-sites-yammer) and [Archive or delete a team in Microsoft Teams](./archive-or-delete-a-team.md).

## Related topics

[Foundations of Microsoft Teams (video)](https://aka.ms/teams-foundations)

[Restore a deleted Group](/microsoft-365/admin/create-groups/restore-deleted-group)
