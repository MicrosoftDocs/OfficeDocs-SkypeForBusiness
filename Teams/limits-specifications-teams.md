---
title: Limits and specifications for Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 03/06/2018
ms.topic: article
ms.service: msteams
ms.reviewer: 
description: Learn about the limits, specifications, and other requirements that apply to Microsoft Teams.
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

Limits and specifications for Microsoft Teams
=============================================

This article describes some of the limits, specifications, and other requirements that apply to Microsoft Teams. 

Teams and channels 
------------------

|Feature    | Maximum limit |
|-----------|---------------|
|Number of teams a user can create | 250         |
|Number of members a team owner can add to a team | 2,500       |
|Number of teams a global admin can create        | Unlimited   |
|Number of teams an Office 365 tenant can have    | 500,000     |
|Number of channels a user can create per team    | 200         |

Meetings and calls 
------------------

|Feature     | Maximum limit |
|------------|---------------|
|Number of people in a meeting  | 80    |
|Number of people in a private chat  | 20    |

Storage
-------

Each team in Microsoft Teams has a team site in SharePoint Online, and each channel in a team gets a folder within the default team site document library. Files shared within a conversation are automatically added to the document library, and permissions and file security options set in SharePoint are automatically reflected within Teams.

If you don't have SharePoint Online enabled in your tenant, Microsoft Teams users cannot always share files in teams. Users in private chat also cannot share files because OneDrive for Business (which is tied to the SharePoint license) is required for that functionality.

By storing the files in the SharePoint Online document library and OneDrive for Business, all compliance rules configured at the tenant level will be followed. (For more, see [How SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md).)

Because Teams runs on a SharePoint Online backend for file sharing, SharePoint limitations apply to the Files section within a Team. Here are the applicable storage limits for SharePoint Online.

|Feature                 |Office 365 Business Essentials  |Office 365 Business Premium   |Office 365 Enterprise E1  |Office 365 Enterprise E3  |Office 365 Enterprise E5  |Office 365 Enterprise F1  |
|------------------------|---------|---------|---------|---------|---------|---------|
|Storage                 |1 TB per organization plus 0.5 GB per license purchased  |1 TB per organization plus 0.5 GB per license purchased  |1 TB per organization plus 0.5 GB per license purchased   |1 TB per organization plus 0.5 GB per license purchased |1 TB per organization plus 0.5 GB per license purchased  |1 TB per organization           |
|Terms in store          |200,000  |200,000  |200,000  |200,000  |200,000  |200,000  |
|Storage for Teams Files |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |
|File upload limit       |15 GB    |15 GB    |15 GB    |15 GB    |15 GB    |15 GB    |

Each Files tab in Teams runs on a SharePoint Online backend, so the storage limits above apply to each Channel within a Team.

For more information, see [SharePoint Online limits](https://support.office.com/en-us/article/SharePoint-Online-limits-8f34ff47-b749-408b-abc0-b605e1f6d498).

Messaging
---------

Users who participate in conversations that are part of the Chat list in Microsoft Teams must have an Exchange Online (cloud-based) mailbox for an admin to search chat conversations. That's because conversations that are part of the Chat list are stored in the cloud-based mailboxes of the chat participants. If a chat participant doesn't have an Exchange Online mailbox, the admin won't be able to search or place a hold on chat conversations. For example, in an Exchange hybrid deployment, users with on-premises mailboxes might be able to participate in conversations that are part of the Chat list in Microsoft Teams. However, in this case, content from these conversations isn't searchable and can't be placed on hold because the users don't have cloud-based mailboxes. (For more, see [How Exchange and Microsoft Teams interact](exchange-teams-interact.md).)

Microsoft Teams chat function works on a Microsoft Exchange backend, so you can apply the Exchange messaging limits to the chat function within Microsoft Teams. Here are the applicable organizational messaging limits for Exchange Online.

|Feature  |Office 365 Enterprise E1  |Office 365 Enterprise E3  |Office 365 Enterprise E5  |Office 365 Enterprise F1  |
|---------|---------|---------|---------|---------|
|Message size limit - Outlook |150 MB   |150 MB   |150 MB   |150 MB   |
|Message size limit - OWA     |112 MB   |112 MB   |112 MB   |112 MB   |
|Message size limit - Outlook for Mac   |150 MB   |150 MB   |150 MB   |150 MB  |
|Message size limit - migration |150 MB |150 MB   |150 MB   |150 MB   |
|Size limit for encrypted messages      |25 MB    |25 MB    |25 MB    |25 MB   |
|Subject length limit |255 char |255 char  |255 char  |255 char  |
|File attachments limit     |250     |250     |250     |250    |
|File attachment size limit - Outlook |150 MB   |150 MB   |150 MB   |150 MB   |
|File attachment size limit - OWA     |35 MB    |35 MB    |35 MB    |35 MB    |
|File attachment size limit - Outlook for Mac |150 MB   |150 MB   |150 MB   |150 MB   |
|Multipart message limit  |250 parts  |250 parts  |250 parts  |250 parts  |
|Embedded message depth limit |30       |30       |30       |30       |

For more information, see [Exchange Online limits](https://technet.microsoft.com/library/exchange-online-limits.aspx).

Operating systems and browsers 
------------------------------

For information about operating system and browser requirements, see [Get clients for Microsoft Teams](get-clients.md).


