---
title: Limits and specifications for Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 05/07/2019
ms.topic: reference
ms.service: msteams
ms.reviewer: karuanag
description: Learn about the limits, specifications, and other requirements that apply to Microsoft Teams.
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
search.appverid: MET150
appliesto: 
- Microsoft Teams
---

# Limits and specifications for Microsoft Teams

This article describes some of the limits, specifications, and other requirements that apply to Teams.

## Teams and channels 

|Feature    | Maximum limit |
|-----------|---------------|
|Number of teams a user can create | Subject to a 250 object limit&sup1;         |
|Number of members in a team | 5,000       |
|Number of members in an [org-wide team](create-an-org-wide-team.md) | 5,000       |
|Number of teams a global admin can create        |  500,000   |
|Number of teams an Office 365 tenant can have    | 500,000&sup2;     |
|Number of channels per team    | 200 (includes deleted channels)&sup3;         |

&sup1;Any directory object in Azure Active Directory counts towards this limit. Global admins are exempt from this limit, as are apps calling Microsoft Graph using [application permissions](https://docs.microsoft.com/graph/permissions-reference).

&sup2;This limit includes archived teams.

&sup3;Deleted channels can be restored within 30 days. During these 30 days, a deleted channel continues to be counted towards the 200 channel per team limit. After 30 days, a deleted channel and its content are permanently deleted and the channel no longer counts towards the 200 channels per team limit.

## Meetings and calls 

|Feature     | Maximum limit |
|------------|---------------|
|Number of people in a meeting  | 250    |
|Number of people in a private chat  | 50    |

## Storage

Each team in Microsoft Teams has a team site in SharePoint Online, and each channel in a team gets a folder within the default team site document library. Files shared within a conversation are automatically added to the document library, and permissions and file security options set in SharePoint are automatically reflected within Teams.

If you don't have SharePoint Online enabled in your tenant, Microsoft Teams users cannot always share files in teams. Users in private chat also cannot share files because OneDrive for Business (which is tied to the SharePoint license) is required for that functionality.

By storing the files in the SharePoint Online document library and OneDrive for Business, all compliance rules configured at the tenant level will be followed. (For more, see [How SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md).)

Because Teams runs on a SharePoint Online backend for file sharing, SharePoint limitations apply to the Files section within a Team. Here are the applicable storage limits for SharePoint Online.

|Feature                 |Office 365 Business Essentials  |Office 365 Business Premium   |Office 365 Enterprise E1  |Office 365 Enterprise E3  |Office 365 Enterprise E5  |Office 365 Enterprise F1  |
|------------------------|---------|---------|---------|---------|---------|---------|
|Storage                 |1 TB per organization plus 10 GB per license purchased  |1 TB per organization plus 10 GB per license purchased  |1 TB per organization plus 10 GB per license purchased   |1 TB per organization plus 10 GB per license purchased |1 TB per organization plus 10 GB per license purchased  |1 TB per organization           |
|Storage for Teams Files |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |
|File upload limit  (per file)    |15 GB    |15 GB    |15 GB    |15 GB    |15 GB    |15 GB    |

Each Files tab in Teams runs on a SharePoint Online backend, so the storage limits above apply to each Channel within a Team.

For more information, see [SharePoint Online limits](https://support.office.com/article/SharePoint-Online-limits-8f34ff47-b749-408b-abc0-b605e1f6d498).

## Messaging

Users who participate in conversations that are part of the Chat list in Microsoft Teams must have an Exchange Online (cloud-based) mailbox for an admin to search chat conversations. That's because conversations that are part of the Chat list are stored in the cloud-based mailboxes of the chat participants. If a chat participant doesn't have an Exchange Online mailbox, the admin won't be able to search or place a hold on chat conversations. For example, in an Exchange hybrid deployment, users with on-premises mailboxes might be able to participate in conversations that are part of the Chat list in Microsoft Teams. However, in this case, content from these conversations isn't searchable and can't be placed on hold because the users don't have cloud-based mailboxes. (For more, see [How Exchange and Microsoft Teams interact](exchange-teams-interact.md).)

Microsoft Teams chat function works on a Microsoft Exchange backend, so you can apply the Exchange messaging limits to the chat function within Microsoft Teams. If users want to send an email to a channel in Teams, they use the channel email address. Once an email is part of a channel, anyone can reply to it to start a conversation. Here are some of the applicable limits for sending email to a channel. 

|Feature  |Office 365 Enterprise E1  |Office 365 Enterprise E3  |Office 365 Enterprise E5  |Office 365 Enterprise F1  |
|---------|---------|---------|---------|---------|
|Message size limit &dagger;  |25 KB   |25 KB   |25 KB   |25 KB   |
|File attachments limit &Dagger;  |10     |10     |10     |10    |
|Inline images limit &Dagger; |50   |50   |50   |50   |

&dagger; If the message exceeds this limit, a preview message is generated and the user is asked to view/download the original email from the link provided.

&Dagger; If the number of attachments or images exceeds this limit, the message will not be processed and an NDR e-mail will be sent back to the sender notifying them of the error.

> [!NOTE]
> The message size, file attachments, and inline images limits are the same across all Office 365 licenses.

For more information, see [Exchange Online limits](https://technet.microsoft.com/library/exchange-online-limits.aspx).

## Browsers

[!INCLUDE [browser-support](includes/browser-support.md)]

## Operating systems

For information about operating system requirements, see [Get clients for Microsoft Teams](get-clients.md).
