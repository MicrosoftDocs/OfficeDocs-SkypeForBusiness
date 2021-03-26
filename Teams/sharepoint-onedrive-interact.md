---
title: How SharePoint Online and OneDrive for Business interact with Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: snigdhav
search.appverid: MET150
description: SharePoint Online & OneDrive for Business interaction with Teams; private chat file storage & interaction between team, standard channel, & document library.
localization_priority: Normal
ms.collection: 
  - M365-collaboration
  - SPO_Content
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# How SharePoint Online and OneDrive for Business interact with Microsoft Teams

> [!Tip]
> Watch the following session to learn how Teams interacts with Azure Active Directory (AAD), Microsoft 365 Groups, Exchange, SharePoint and OneDrive for Business: [Foundations of Microsoft Teams](https://aka.ms/teams-foundations)

Each team in Microsoft Teams has a team site in SharePoint Online, and each standard channel in a team gets a folder within the default team site document library. Files shared within a conversation are automatically added to the document library, and permissions and file security options set in SharePoint are automatically reflected within Teams. To see the impact of changing a site address in SharePoint, read [Change a site address](/sharepoint/change-site-address).

> [!NOTE]
> This article applies only to standard channels. The architecture for private channels is different from standard channels. Each private channel has its own SharePoint site collection that's separate from the parent team site. To learn more, see [Private channels in Microsoft Teams](private-channels.md).

Private chat files are stored in the sender's OneDrive for Business folder, and permissions are automatically granted to all participants as part of the file sharing process.

If users aren't assigned and enabled with SharePoint Online licenses, they don't have OneDrive for Business storage in Microsoft 365 or Office 365. File sharing will continue to work in standard channels, but users won't be able to share files in chats without OneDrive for Business storage in Microsoft 365 or Office 365.

By storing the files in the SharePoint Online document library and OneDrive for Business, all compliance rules configured at the tenant level will be followed. 

> [!NOTE]
> Integration with SharePoint On-premises is not supported for Microsoft Teams at this time.

The following is the example of relationships between team, standard channel, and document library.

For every team, a SharePoint site is created, and the **Shared Documents** folder is the default folder created for the team. Each standard channel, including the **General** channel (the default channel for each team) has a folder in **Shared Documents**.

![Diagram of Shared Documents folders In SharePoint Online.](media/Understand_how_SharePoint_Online_and_OneDrive_for_Business_interact_with_Microsoft_Teams_image1.png)

> [!NOTE]
> It's not currently possible to replace the default SharePoint site and document library with another one. We've heard from you that you want it, and we're considering it. Check the [Teams Roadmap](https://aka.ms/teamsroadmap) or [Teams UserVoice](https://aka.ms/TeamsUserVoice) to stay on top of upcoming features.

> [!TIP]
> To add a tab to your team that links to an existing SharePoint site page or to your existing SharePoint document library:
> 1. Select the  plus sign next to the tabs.
> 2. Select either **SharePoint** for an existing SharePoint site page or **Document Library** for an existing document library.
> 3. Select the appropriate page or document library.

For every user, the OneDrive folder **Microsoft Teams Chat Files** is used to store all files shared within private chats with other users (1:1 or 1:many), with permissions configured automatically to restrict access to the intended user only.

![Diagram of the OneDrive folder named Microsoft Teams Chat Files](media/Understand_how_SharePoint_Online_and_OneDrive_for_Business_interact_with_Microsoft_Teams_image2.png)

Note that for public teams, the SharePoint team site is provisioned with "Everyone except external users" access. The public team isn't displayed in Teams for people who aren't members of that team. However, they can access content on the SharePoint team site using the URL of the SharePoint team site. 

## Channel Files tab

> [!INCLUDE [new feature coming soon](includes/new-feature-coming-soon-section.md)]

The **Files** tab in Teams closely resembles the SharePoint documents view. On the **Files** tab, users can:

- See additional options in the **New** file menu.
- Sync files to their local drive.
- On the **All Documents** menu, switch from **List** view to **Compact list** to **Tiles** view.
- Identify files that need attention or have malware.
- Immediately see whether a file is read-only or checked out.
- Check out and check in files.
- Pin, unpin, and change the sort order of files.
- Identify which files need metadata
- Choose from many more filter options.
- Group files based on column headings.
- Modify column settings (move left or right, hide) and column width.

## Default link type setting

SharePoint and OneDrive have an admin setting for specifying the default link type for links that are created for a file. Teams is adopting that same approach by reusing the settings that the admin sets for SharePoint and OneDrive. More details about this approach are described in [Change the default link type when users get links for sharing](/sharepoint/change-default-sharing-link). 

## More information

For more information about how SharePoint works with Teams, see [SharePoint and Teams: better together](https://techcommunity.microsoft.com/t5/Microsoft-SharePoint-Blog/SharePoint-and-Teams-Better-Together/ba-p/189593).

To learn more about the guest experience in Teams, read [What the guest experience is like](guest-experience.md).