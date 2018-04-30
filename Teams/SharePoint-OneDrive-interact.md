---
title: How SharePoint Online and OneDrive for Business interact with Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
ms.reviewer: snigdhav
description: Learn how SharePoint Online and OneDrive for Business interact with Microsoft Teams such as how private chat files are stored, and the relationship between team, channel, and the document library.
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

How SharePoint Online and OneDrive for Business interact with Microsoft Teams
=============================================================================

Each team in Microsoft Teams has a team site in SharePoint Online, and each channel in a team gets a folder within the default team site document library. Files shared within a conversation are automatically added to the document library, and permissions and file security options set in SharePoint are automatically reflected within Teams.

Private chat files are stored in the sender’s OneDrive for Business folder, and permissions are automatically granted to all participants as part of the file sharing process.

If you don't have SharePoint Online enabled in your tenant, Teams users can't share files in teams. Users in private chat also can't share files because OneDrive for Business (which is tied to the SharePoint license) is required for that functionality.

By storing the files in the SharePoint Online document library and OneDrive for Business, all compliance rules configured at the tenant level will be followed. Please note: Integration with Sharepoint On-premise is not supported for Microsoft Teams at this time.

The following is the example of relationships between team, channel, and document library.

For every team, a SharePoint site is created, and the **Shared Documents** folder is the default folder created for the team. Each channel, including the **General** channel (the default channel for each team) has a folder in **Shared Documents**.

![Diagram of Shared Documents folders In SharePoint Online for a team and its channels in Microsoft Teams.](media/Understand_how_SharePoint_Online_and_OneDrive_for_Business_interact_with_Microsoft_Teams_image1.png)

> [!NOTE]
> It's not currently possible to replace the default SharePoint site and document library with another one. We've heard from you that you want it, and we're considering it. Check the [Teams Roadmap](https://aka.ms/teamsroadmap) or [Teams UserVoice](https://aka.ms/TeamsUserVoice) to stay on top of upcoming features.

For every user, the OneDrive folder **Microsoft Teams Chat Files** is used to store all files shared within private chats with other users (1:1 or 1:many), with permissions configured automatically to restrict access to the intended user only.

![Diagram of the OneDrive folder named Microsoft Teams Chat Files for each user's chats.](media/Understand_how_SharePoint_Online_and_OneDrive_for_Business_interact_with_Microsoft_Teams_image2.png)
