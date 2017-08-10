---
title: Understand Office 365 groups and Microsoft Teams | Microsoft Support
author: LolaJacobsen
ms.author: lolaj
manager: serdar
ms.date: 08/10/2017
ms.topic: overview
ms.prod: teams
description: Learn about how Office 365 groups and group memberships work with Microsoft Teams.
---

Understand Office 365 groups and Microsoft Teams
================================================

Office 365 Groups is the cross-application membership service in Office 365. At the basic level, an Office 365 Group is an object in Azure Active Directory with a list of members and a loose coupling to related workloads including a SharePoint team site, Yammer Group, shared Exchange mailbox resources, Planner, PowerBI and OneNote. You can add or remove people to the Group just as you would any other group-based security object in Active Directory.

An Office 365 administrator can define an Office 365 Group, add members, and benefit from features such as an Exchange shared mailbox, SharePoint document library, Yammer Group, etc. For more information about Groups visit: [Learn about Office 365 Groups](https://support.office.com/en-us/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

How Office 365 groups work
--------------------------

When you create a Microsoft Team, on the backend, you’re creating an Office 365 Group along with the associated SharePoint document library, OneNote notebook, along with ties into other Office 365 cloud applications. If the person creating the Team is an owner of an existing Office 365 Public or Private Group, they can add Teams functionality to the Group. This creates one default “General” channel in which chat messages, documents, OneNote, and other objects reside. Viewing the document library for the channel will reveal the “General” folder representing the channel in the Team. More importantly, if you create your own folder structure within a document library **it does not propagate** to Teams as a channel; for now, it only flows from Teams into SharePoint.

|||
|---------|---------|
|  ![](media/Understand_Office_365_groups_and_Microsoft_Teams_image1.emf) Note    |Deleting an Office 365 Group will remove the mailbox alias for persistent Outlook/OWA conversations and Teams meeting invites, and mark the SharePoint site for deletion. It takes approximately 20 minutes between the removal of a Team and its effect on Outlook. Deleting a Team from the Teams client will remove it immediately from view to all who are members of the team. If you remove a member of an Office 365 Group which has had Teams functionality enabled on it, there could be a delay of approximately one hour before the Team is removed from view in the Teams client for the effected people who were removed.         |


Group membership
----------------

Depending on where you drive group membership from, depends on what features and capabilities your users will experience. For example, if you remove a member of a Team, they are removed from the Office 365 Group as well. Removal from the Group immediately removes the Team and channels from the Teams client. If you remove a person from a Group using the Office 365 Admin portal, they will no longer have access to the other collaborative aspects such as SharePoint Online document library, Yammer Group, or shared OneNote. However, they will still have access to the Team’s chat functionality for approximately one hour.

Our guidance with respect to Teams ‘member management’ is to drive the add/remove functionality through the Teams client to ensure the correct cascading access control to other dependent cloud applications is applied. Additionally, you will avoid a disjointed experience leaving people with the impression they still have access to the resources they used to (until the next sync cycle either adds or revokes access to a particular component of the service).
