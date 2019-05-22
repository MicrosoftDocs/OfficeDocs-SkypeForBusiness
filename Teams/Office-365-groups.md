---
title: Office 365 Groups and Microsoft Teams
ms.reviewer: phlouie
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 04/16/2019
ms.topic: conceptual
ms.service: msteams
description: Learn about how Office 365 groups and group memberships work with Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Office 365 Groups and Microsoft Teams
=====================================

> [!Tip]
> Watch the following session to learn how Teams interacts with Azure Active Directory (Azure AD), Office 365 Groups, Exchange, SharePoint and OneDrive for Business: [Foundations of Microsoft Teams](https://aka.ms/teams-foundations)

Office 365 Groups is the cross-application membership service in Office 365. At the basic level, an Office 365 Group is an object in Azure Active Directory with a list of members and a loose coupling to related workloads including a SharePoint team site, Yammer Group, shared Exchange mailbox resources, Planner, Power BI and OneNote. You can add or remove people to the group just as you would any other group-based security object in Active Directory.

An Office 365 administrator can define an Office 365 Group, add members, and benefit from features such as an Exchange shared mailbox, SharePoint document library, Yammer Group, and so on. For more information about Office 365 Groups, see [Learn about Office 365 Groups](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

Don't miss the poster [Groups in Microsoft 365 for IT Architects](teams-architecture-solutions-posters.md#groups-in-microsoft-365).

How Office 365 Groups work
--------------------------

When you create a team, on the backend, you’re creating an Office 365 Group and the associated SharePoint document library and OneNote notebook, along with ties into other Office 365 cloud applications. If the person creating the team is an owner of an existing Office 365 Public or Private Group, they can add Teams functionality to the group if it has less than 5000 people and has never been added to Teams. This creates one default **General** channel in which chat messages, documents, OneNote, and other objects reside. Viewing the document library for the channel will reveal the **General** folder representing the channel in the team. More importantly, if you create your own folder structure within a document library **it does not propagate** to Teams as a channel; for now, it only flows from Teams into SharePoint.

> [!NOTE]
> Based on customer feedback, new Office 365 Groups generated as a result of creating a team in Microsoft Teams will no longer show in Outlook by default. For customers that want to continue with the existing behavior of showing these groups in Outlook, an Exchange Online PowerShell cmdlet will be provided which can enable the group for the Outlook experience. Groups created through Outlook and then later enabled for Teams will continue to show in both Outlook and Teams. This update will gradually roll out across Outlook and Teams in the coming months.

> [!NOTE]
> Deleting an Office 365 Group will remove the mailbox alias for persistent Outlook/OWA conversations and Teams meeting invites, and mark the SharePoint site for deletion. It takes approximately 20 minutes between the removal of a team and its effect on Outlook. Deleting a team from the Teams client will remove it immediately from view to all who are members of the team. If you remove members of an Office 365 Group that has had Teams functionality enabled on it, there could be a delay of approximately two hours before the team is removed from view in the Teams client for the affected people who were removed.
>
>Read [this](https://support.office.com/article/Restore-a-deleted-Office-365-Group-b7c66b59-657a-4e1a-8aa0-8163b1f4eb54) for information about restoring an Office 365 Group that you deleted.

Group membership
----------------

Group features and capabilities for your users depend on where you drive group membership from. For example, if you remove a member of a team, they are removed from the Office 365 Group as well. Removal from the group immediately removes the team and channels from the Teams client. If you remove a person from a group using the Microsoft 365 admin center, they will no longer have access to the other collaborative aspects such as SharePoint Online document library, Yammer group, or shared OneNote. However, they will still have access to the team’s chat functionality for approximately two hours.

As a best practice for managing Teams members, add and remove members from the Teams client to ensure that the correct cascading access control to other dependent cloud applications is applied. Additionally, you will avoid a disjointed experience leaving people with the impression they still have access to the resources they used to (until the next sync cycle either adds or revokes access to a particular component of the service). If you DO add or remove team members outside of the Teams client (by using the Microsoft 365 admin center, Azure AD, or Exchange Online PowerShell), it can take up to two hours for changes to be reflected in Teams.
