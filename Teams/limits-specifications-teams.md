---
title: Limits and specifications for Microsoft Teams
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: 
description: This article describes the limits, specifications, and other requirements that apply to Microsoft Teams.
localization_priority: Priority
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - SPO_Content
search.appverid: MET150
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Limits and specifications for Microsoft Teams

This article describes some of the limits, specifications, and other requirements that apply to Teams.

## Teams and channels

|Feature    | Maximum limit |
|-----------|---------------|
|Number of teams a user can create | Subject to a 250 object limit&sup1;         |
|Number of teams a user can be a member of|1,000|
|Number of members in a team | 10,000       |
|Number of owners per team | 100   |
|Number of org-wide teams allowed in a tenant | 5     |
|Number of members in an [org-wide team](create-an-org-wide-team.md) | 5,000       |
|Number of teams a global admin can create        |  500,000   |
|Number of teams a Microsoft 365 or Office 365 organization can have    | 500,000&sup2;     |
|Number of channels per team    | 200 (includes deleted channels)&sup3;         |
|Number of Private channels per team    |30|
|Number of members in a Private channel    |250|
|Maximum number of members in an Office 365 group that can be converted to a team    |10,000|
|Channel conversation post size | Approximately 28 KB per post<sup>4</sup> |

<sup>1</sup> Any directory object in Azure Active Directory counts towards this limit. Global admins are exempt from this limit, as are apps calling Microsoft Graph using [application permissions](https://docs.microsoft.com/graph/permissions-reference).

<sup>2</sup> This limit includes archived teams.

<sup>3</sup> Deleted channels can be restored within 30 days. During these 30 days, a deleted channel continues to be counted towards the 200 channel per team limit. After 30 days, a deleted channel and its content are permanently deleted and the channel no longer counts towards the 200 channels per team limit.

<sup>4</sup> 28 KB is an approximate limit because it includes the message itself (text, image links, etc.), @-mentions, number of connectors, and reactions.

## Messaging

### Chat

Users who participate in conversations that are part of the chat list in Teams must have an Exchange Online (cloud-based) mailbox for an admin to search chat conversations. That's because conversations that are part of the chat list are stored in the cloud-based mailboxes of the chat participants. If a chat participant doesn't have an Exchange Online mailbox, the admin won't be able to search or place a hold on chat conversations. For example, in an Exchange hybrid deployment, users with on-premises mailboxes might be able to participate in conversations that are part of the chat list in Teams. However, in this case, content from these conversations isn't searchable and can't be placed on hold because the users don't have cloud-based mailboxes. (For more, see [How Exchange and Microsoft Teams interact](exchange-teams-interact.md).)

Teams chat works on a Microsoft Exchange backend, so Exchange messaging limits apply to the chat function within Teams.

|Feature  | Maximum limit  |
|---------|---------|
|Number of people in a private chat<sup>1</sup>  | 250 |
|Number of people in a video or audio call from chat | 20 |
|Number of file attachments<sup>2</sup>  |10     |
|Chat size | Approximately 28 KB per post<sup>3</sup> |

<sup>1</sup> If you have more than 20 people in a chat, the following chat features are turned off: Outlook automatic replies and Teams status messages; typing indicator; video and audio calling; sharing; read receipts. The "Set Delivery Options" button (!) is also removed when private group chats contain more than 20 members.

<sup>2</sup> If the number of attachments exceeds this limit, you'll see an error message.

<sup>3</sup> 28 KB is an approximate limit because it includes the message itself (text, image links, etc.), @-mentions, and reactions.

### Emailing a channel

 If users want to send an email to a channel in Teams, they use the channel email address. When an email is part of a channel, anyone can reply to it to start a conversation. Here are some of the applicable limits for sending email to a channel.

|Feature  | Maximum limit  |
|---------|---------|
|Message size<sup>1<sup> | 24 KB |
|Number of file attachments<sup>2</sup>  |20     |
|Size of each file attachment | Less than 10 MB |
|Number of inline images<sup>2</sup> |50   |

<sup>1</sup> If the message exceeds this limit, a preview message is generated and the user is asked to download and view the original email from the link provided.

<sup>2</sup> If the number of attachments or images exceeds this limit, you'll see an error message.

For more information, see [Exchange Online limits](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).

> [!NOTE]
> Message size, file attachments, and inline images limits are the same across all Microsoft 365 and Office 365 licenses.

## Channel names

Channel names can't contain the following characters or words.

|||
|---------|---------|
|Characters     | ~ # % & * { } + / \ : < > ? &#124; ' " , .        |
|Characters in these ranges    | 0 to 1F<br>80 to 9F        |
|Words     | forms, CON, CONIN$, CONOUT$, PRN, AUX, NUL, COM1 to COM9, LPT1 to LPT9, desktop.ini,  &#95;vti&#95;|

Channel names also can't start with an underscore (_) or period (.), or end with a period (.).

## Meetings and calls

> [!IMPORTANT]
> **Microsoft 365 live event limit increases**
>
> **To help support our customers, through January 1, 2021, we will extend temporary limit increases for live events hosted in Teams, Stream, and Yammer, including**:
>
>- Up to 20,000 attendees per event
>- Up to 50 simultaneous events per Teams tenant
>- Up to 16 hours per broadcast
>
> Additionally, live events with up to 100,000 attendees can be planned through the Microsoft 365 assistance program. The team will assess each request and work with you to determine options that may be available. [Learn more](https://aka.ms/Stream/Blog/LiveEventOptions). **After January 1, 2021, customers who need these limit increases will be required to purchase the [Advanced Communications add-on](teams-add-on-licensing/advanced-communications.md).**


|Feature     | Maximum limit |
|------------|---------------|
|Number of people in a meeting (can chat and call in)  | 300 |
|Number of people in a video or audio call from chat | 20 |
|Max PowerPoint File Size | 2GB|
|Teams keeps [meeting recordings](cloud-recording.md) that don't get uploaded to Microsoft Stream, available for local download | 20 days |

>[!Note]
> The change from using Microsoft Stream to [OneDrive for Business and SharePoint for meeting recordings](tmr-meeting-recording-change.md) will be a phased approach. At launch you'll be able to opt-in to this experience, in November you'll have to opt-out if you want to continue using Stream, and some time in early 2021 we'll require all customers to use OneDrive for Business and SharePoint for new meeting recordings.

### Meeting expiration

|Meeting type  |Meeting expires after this much time  |Each time you start or update a meeting, expiration extends by this much time  |
|---------|---------|---------|
|Meet now     |Start time + 8 hours         |N/A         |
|Regular with no end time     |Start time + 60 days         | 60 days        |
|Regular with end time     |End time + 60 days         |60 days         |
|Recurring with no end time     |Start time + 60 days         |60 days         |
|Recurring with end time     |End time of last occurrence + 60 days         |60 days         |

> [!NOTE]
> Microsoft Teams meetings have a time limit of 24 hours.

## Teams live events

|Feature     | Maximum limit |
|------------|---------------|
|Audience size | 10,000 attendees |
|Duration of event | 4 hours |
|Concurrent live events running in a Microsoft 365 or Office 365 organization <sup>1</sup> | 15 |

<sup>1</sup> You can schedule as many live events as you want, but you can only run 15 at a time. As soon as the producer joins a live event, it's considered to be running. The producer who attempts to join the 16th live event gets an error.

For more information about live events and a comparison of Teams live events to Skype Meeting Broadcast, go to [Teams live events and Skype Meeting Broadcast](teams-live-events/plan-for-teams-live-events.md#teams-live-events-and-skype-meeting-broadcast).

> [!IMPORTANT]
> **Microsoft 365 live event limit increases**
>
> To help customers meet rapidly changing communication needs, we will temporarily raise default limits until January 1, 2021, for live events hosted in Teams, Stream, and Yammer.
>
> - Attendee limit: events can support up to 20,000 attendees
> - Concurrent events: 50 events can be hosted simultaneously across a tenant
> - Event duration: event length has been increased to 16 hours per broadcast
>
> Additionally, live events with up to 100,000 attendees can be planned through the Microsoft live events assistance program. [Learn more](https://aka.ms/Stream/Blog/LiveEventOptions). **After January 1, 2021, customers who need these limit increases will be required to purchase the [Advanced Communications add-on](teams-add-on-licensing/advanced-communications.md).**

## Presence in Outlook

Teams presence in Outlook is supported on the Outlook 2013 desktop app and later. To learn more about presence in Teams, see [User presence in Teams](presence-admins.md).

## Storage

Each team in Microsoft Teams has a team site in SharePoint Online, and each channel in a team gets a folder within the default team site document library. Files shared within a conversation are automatically added to the document library, and permissions and file security options set in SharePoint are automatically reflected within Teams.

> [!NOTE]
> Each [private channel](https://docs.microsoft.com/microsoftteams/private-channels) has its own SharePoint site collection.

If you don't have SharePoint Online enabled in your tenant, Microsoft Teams users cannot always share files in teams. Users in private chat also cannot share files because OneDrive for Business (which is tied to the SharePoint license) is required for that functionality.

By storing the files in the SharePoint Online document library and OneDrive for Business, all compliance rules configured at the tenant level will be followed. (For more, see [How SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md).)

Because Teams runs on a SharePoint Online backend for file sharing, SharePoint limitations apply to the Files section within a Team. Here are the applicable storage limits for SharePoint Online.

|Feature                 |Microsoft 365 Business Basic  |Microsoft 365 Business Standard   |Office 365 Enterprise E1  |Office 365 Enterprise E3  |Office 365 Enterprise E5  |Office 365 Enterprise F1  |
|------------------------|---------|---------|---------|---------|---------|---------|
|Storage                 |1 TB per organization plus 10 GB per license purchased  |1 TB per organization plus 10 GB per license purchased  |1 TB per organization plus 10 GB per license purchased   |1 TB per organization plus 10 GB per license purchased |1 TB per organization plus 10 GB per license purchased  |1 TB per organization           |
|Storage for Teams Files |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |Up to 25 TB per site collection or group |
|File upload limit  (per file)    |100 GB    |100 GB    |100 GB    |100 GB    |100 GB    |100 GB    |

Channels are backed by folders within the SharePoint Online site collection created for the team, so file tabs within Channels share the storage limits of the team they belong to.

For more information, see [SharePoint Online limits](https://support.office.com/article/SharePoint-Online-limits-8f34ff47-b749-408b-abc0-b605e1f6d498).

## Class teams

Microsoft Teams for Education provides templates designed for unique education scenarios, such as classroom teaching. More information about team types, including class teams, is available in [Choose a team type to collaborate in Microsoft Teams](https://support.microsoft.com/office/choose-a-team-type-to-collaborate-in-microsoft-teams-0a971053-d640-4555-9fd7-f785c2b99e67).

A class team is a template type with additional apps included, and with limits separate to the number of team members.

> [!NOTE]
> Using class teams requires an [Office 365 Education license](https://www.microsoft.com/education/products/office).

Limits for class teams are listed in the following table:

|Feature  |Maximum limit  |
|---------|---------|
|Number of members in a team    | See the [Teams and channels](#teams-and-channels) section of this article        |
|Number of members to use Assignments in a class team    | 200        |
|Number of members to use a OneNote Class Notebook in a class team     |200         |

A class team can support more than 200 members. However, if you plan to use either the Assignments app or Class Notebook app within your team, you will need to keep the number of members below the maximum limits above.


## Tags

|Feature  |Maximum limit  |
|---------|---------|
|Number of tags per team    | 100        |
|Number of suggested default tags per team    | 25        |
|Number of team members assign to a tag    |100         |
|Number of tags assigned to a user    |25         |

## Contacts

Teams uses these contacts:

- Contacts in your organization's Active Directory
- Contacts added to the user's Outlook default folder

Teams users can communicate with anyone in your organization's Active Directory and can add anyone in your organization's Active Directory as a contact and to their contact lists by going to **Chat** > **Contacts** or **Calls** > **Contacts**.

Teams users can also add a person who isn't in your organization's Active Directory as a contact by going to **Calls** > **Contacts**.

## Browsers

[!INCLUDE [browser-support](includes/browser-support.md)]

## Operating systems

For information about operating system requirements, see [Get clients for Microsoft Teams](get-clients.md).
