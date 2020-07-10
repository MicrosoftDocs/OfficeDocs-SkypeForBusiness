---
title: Sharing files in Microsoft Teams
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: haagaraw
audience: admin
search.appverid: MET150
description: Learn about the Sharelink feature in Microsoft Teams, which lets users share content with out Teams users within and outside their organization. 
localization_priority: Normal
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Sharing files in Microsoft Teams

The Sharelink feature in Microsoft Teams lets users share content with other Teams users within and outside their organization. Sharing in Teams is based on the settings configured in SharePoint and OneDrive, so whatever you set up for SharePoint and OneDrive will control sharing in Teams as well.

![Diagram showing how Teams, SharePoint, and OneDrive work together](media/teams-share-and-work.png)

With the Sharelink feature:

- Users can share files from OneDrive and from teams and sites they have access to.
- Users can share a file either by browsing to the file from OneDrive or teams and channels or by copying and pasting a link in the **Compose** box.

When users share a file by browsing through OneDrive and teams and channels in the **Compose** box, all recipients are granted access along with the [default permission set at the organization level](https://docs.microsoft.com/sharepoint/change-default-sharing-link). When a user copies and pastes a file link, the permissions set on that file link is honored and the SharePoint file link is shortened with the file name.

Teams shortens long SharePoint URLs and browser URLs that point to a file. Teams uses just the file name to link to a file. 

When users share a file from within Teams, they have the option to manage access to anyone, people within your organization, people with existing access, or specific people, including those in a 1:1 chat, group chat, or channels.

When users share a file in a chat or channel, they're notified if some or all the recipients don't have permission to view the file. They can change permissions before sharing by clicking on the file chiclet.

Once a file is shared, the file opens by default within Teams and is available as a chiclet with all file actions. In some cases, the file link may not have converted to a chiclet by the time the users send the message. The chiclet will be generated asynchronously, but the file link will not be shortened to the file name in this case.

The **Get link** option has been changed to **Copy link**. Users can copy a SharePoint file link and modify sharing permissions like it is across Microsoft 365. The default permission of the link will be same as the default set at organization level unless it is overridden at SharePoint site level.

## Configure sharing in OneDrive and SharePoint

For more information about sharing files in OneDrive and SharePoint, including how to configure sharing and how to turn sharing on and off, see:

- [External sharing overview](https://docs.microsoft.com/sharepoint/external-sharing-overview) - describes what happens when users share, depending on what they're sharing and with whom.

- [Turn external sharing on or off](https://docs.microsoft.com/sharepoint/turn-external-sharing-on-or-off) - describes how global and SharePoint admins can change their organization-level sharing settings for SharePoint and OneDrive.

- [Change external sharing for a site](https://docs.microsoft.com/sharepoint/change-external-sharing-site) – describes how global and SharePoint admins can turn external sharing on or off for a site.

- [Change the default link type when users get links for sharing](https://docs.microsoft.com/sharepoint/change-default-sharing-link) - describes how to set the default link type so that it's more restrictive.

## More information

- [How SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md)

- [SharePoint and Teams: better together](https://techcommunity.microsoft.com/t5/Microsoft-SharePoint-Blog/SharePoint-and-Teams-Better-Together/ba-p/189593)

- [Share OneDrive files and folders](https://support.office.com/article/Share-OneDrive-files-and-folders-9fcc2f7d-de0c-4cec-93b0-a82024800c07#OS_Type=OneDrive_-_Business)

- [Share SharePoint files or folders](https://support.office.com/article/share-sharepoint-files-or-folders-1fe37332-0f9a-4719-970e-d2578da4941c)
