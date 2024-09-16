---
title: Limits and specifications for Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: siunies
ms.date: 03/02/2018
description: This article describes the limits, specifications, and other requirements that apply to Microsoft Teams.
ms.localizationpriority: high
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
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
|Number of teams a user can be a member of|1,000&sup2;|
|Number of members in a team | 25,000<sup>6</sup>     |
|Number of owners per team | 100   |
|Number of org-wide teams allowed in a tenant | 5&sup2;     |
|Number of members in an [org-wide team](create-an-org-wide-team.md) | 10,000       |
|Number of teams a global admin can create        |  500,000   |
|Number of teams a Microsoft 365 or Office 365 organization can have    | 500,000&sup3;     |
|Number of channels per team    | 1,000 (includes deleted channels)<sup>4,7</sup>         |
|Number of Private channels per team    | 30 (includes deleted channels)<sup>4</sup>        |
|Number of members in a Private channel    |250|
|Maximum size of distribution list, security group or Microsoft 365 group that can be imported in to a team    |3,500|
|Maximum number of members in a Microsoft 365 group that can be converted to a team    |10,000<sup>6</sup>     |
|Channel conversation post size | Approximately 28 KB per post<sup>5</sup> |

<sup>1</sup> Any directory object in Microsoft Entra ID counts towards this limit. Global admins are exempt from this limit, as are apps calling Microsoft Graph using [application permissions](/graph/permissions-reference).

<sup>2</sup> This limit includes archived teams.

<sup>3</sup> To further increase the number of teams, you must contact Microsoft support and request further increase to the number of Microsoft Entra objects in your tenant. Increase is only made for real-life production scenarios.

<sup>4</sup> Deleted channels can be restored within 30 days. During these 30 days, a deleted channel continues to be counted towards the 1,000 channel or 30 private channel per team limit. After 30 days, a deleted channel and its content are permanently deleted and the channel no longer counts toward the per-team limit.

<sup>5</sup> 28 KB is an approximate limit because it includes the message itself (text, image links, etc.), @-mentions, number of connectors, and reactions.

<sup>6</sup> Shared channels members from outside the team count toward this limit. Further note that teams/channel mentions are blocked in teams with over 10,000 members.

<sup>7</sup> Any combination of standard and shared channels including up to 30 private channels for a total of 1,000 channels per team.

### Limits for shared channels

The following table describes the maximum number of channels and members.

|Maximum...|Value|Notes|
|:---------|:----|:----|
|Members in a team|25,000|Includes all users in the team and direct members in shared channels.|
|Shared channels per team|up to 1,000 |Hosted and shared with the team. (Includes deleted channels during their 30-day recovery window.)|
|Teams a channel can be shared with|50|Excluding parent team|
|Members in a shared channel|5,000 direct members, including up to 50 teams. (Each team the channel is shared with counts as one member for purposes of this limit.)|Real time updates are only available to 25,000 users at a time and only 25,000 users will appear in the channel list.|

The following limitations also apply:

- Only Microsoft Entra work or school accounts are supported for external participants.

- Shared channels support tabs except for Stream, Planner, and Forms.

- Bots, connectors, and message extensions aren't supported.

- Org-wide teams aren't supported to be added as members of a shared channel.

- When you create a team from an existing team, any shared channels in the existing team aren't copied over.

- Notifications from shared channels aren't included in missed activity emails.

- Shared channels aren't supported in class teams.

## Messaging

### Chat

Users who participate in conversations that are part of the chat list in Teams must have an Exchange Online (cloud-based) mailbox for an admin to search chat conversations. That's because conversations that are part of the chat list are stored in the cloud-based mailboxes of the chat participants. If a chat participant doesn't have an Exchange Online mailbox, the admin can't search or place a hold on chat conversations. For example, in an Exchange hybrid deployment, users with on-premises mailboxes might be able to participate in conversations that are part of the chat list in Teams. However, in this case, content from these conversations isn't searchable and can't be placed on hold because the users don't have cloud-based mailboxes. (For more, see [How Exchange and Microsoft Teams interact](exchange-teams-interact.md).)


|Feature  | Maximum limit  |
|---------|---------|
|Number of people in a private chat<sup>1</sup>  | 250<sup>2</sup> |
|Number of people in a video or audio call from chat | 20 |
|Number of file attachments<sup>3</sup>  |10     |
|Chat size | Approximately 28 KB per post<sup>4</sup> |

<sup>1</sup> If you have more than 20 people in a chat, the following chat features are turned off: Outlook automatic replies and Teams status messages; typing indicator; video and audio calling; sharing; read receipts. The "Set Delivery Options" button (!) is also removed when private group chats contain more than 20 members.

<sup>2</sup> Only 200 members can be added to a group chat at the same time.

<sup>3</sup> If the number of attachments exceeds this limit, you'll see an error message.

<sup>4</sup> 28 KB is an approximate limit because it includes the message itself (text, image links, etc.), @-mentions, and reactions.

### Emailing a channel

 If users want to send an email to a channel in Teams, they use the channel email address. When an email is part of a channel, anyone can reply to it to start a conversation. Here are some of the applicable limits for sending email to a channel.

|Feature  | Maximum limit  |
|---------|---------|
|Message size<sup>1<sup> | 24 KB |
|Number of file attachments<sup>2</sup>  |20     |
|Size of each file attachment | Less than 10 MB |
|Number of inline images<sup>2</sup> |50   |

> [!NOTE]
> There is a throttling limit on how many emails you can send to a channel. The limit is six emails per ten seconds per channel per user and eight emails per ten seconds per tenant per user.

<sup>1</sup> If the message exceeds this limit, a preview message is generated and the user is asked to download and view the original email from the link provided.<br/>
<sup>2</sup> If the number of attachments or images exceeds this limit, you'll see an error message.

For more information, see [Exchange Online limits](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).

> [!NOTE]
> Message size, file attachments, and inline images limits are the same across all Microsoft 365 and Office 365 licenses. Emailing a channel is not available in Teams for Office GCC/GCCH/DOD organizations.

## Channel names

Channel names can't contain the following characters or words:

|Type|Example|
|---------|---------|
|Characters     | ~ # % & * { } + / \ : < > ? &#124; ' " , ..        |
|Characters in these ranges    | 0 to 1F<br>80 to 9F        |
|Words     | forms, CON, CONIN$, CONOUT$, PRN, AUX, NUL, COM1 to COM9, LPT1 to LPT9, desktop.ini,  &#95;vti&#95;|

Channel names also can't start with an underscore (_) or period (.), or end with a period (.).

## Meetings and calls

|Feature     | Maximum limit |
|------------|---------------|
|Number of people in a meeting (can chat and call in)  | With Microsoft Teams Essentials, Microsoft 365 Business Basic, Microsoft 365 Business Standard, Microsoft 365 Business Premium, and Microsoft 365 A1 plans, you can host online meetings and video calls for up to 300 people using Microsoft Teams. With Microsoft 365 E3/E5, Microsoft 365 A3/A5, and Microsoft 365 Government G3/G5 plans, this limit increases up to 1,000 people.|
|Number of people in a video or audio call from chat | 20 |
|Max PowerPoint File Size | 2 GB|
|Teams keeps [meeting recordings](meeting-recording.md) that don't get uploaded to Microsoft Stream, available for local download | 20 days |
| Meeting recording maximum length | 4 hours or 1.5 GB. When this limit is reached, the recording ends and automatically restarts.

For more information, see [Meetings, webinars, and live events](/microsoftteams/quick-start-meetings-live-events).  
  
> [!NOTE]
> Breakout rooms can only be created in meetings that have fewer than 300 attendees. In addition, creating breakout rooms in a meeting automatically limits the number of meeting attendees to 300. Advise your end-users to not initiate breakout rooms in meetings where they expect more than 300 participants. For more information on large Team meetings, share the guidance [Best practices for a large Teams meeting](https://support.microsoft.com/office/best-practices-for-a-large-teams-meeting-ce2cdb9a-0546-43a4-bb55-34ab98ab6b16) with your end-users.

### Meeting expiration

> [!NOTE]
> A meeting URL will never stop working. The expiry only relates to any PSTN dial-in numbers, CVI coordinates, and/or underlying meeting policies and settings.

|Meeting type  |Meeting expires after this much time  |Each time you start or update a meeting, expiration extends by this much time  |
|---------|---------|---------|
|Meet now     |Start time + 8 hours         |N/A         |
|Regular with no end time     |Start time + 60 days         | 60 days        |
|Regular with end time     |End time + 60 days         |60 days         |
|Recurring with no end time     |Start time + 60 days         |60 days         |
|Recurring with end time     |End time of last occurrence + 60 days         |60 days         |

> [!NOTE]
> Microsoft Teams meetings have a time limit of 30 hours.

## Live Events
  
> [!NOTE]
> Teams Live Events will no longer be deprecated on September 30, 2024, as previously announced. While we still recommend that customers upgrade to [Teams town hall](plan-town-halls.md) when ready to take advantage of new features and experiences, Live Events users can now schedule events beyond September 2024. For more information, please read our recent [blog post](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/extension-for-teams-live-events-retirement/ba-p/4148352).

Live events are structured meetings that enable your organization to schedule and produce events that stream to large online audiences—up to 20,000 people. With live events, the audience interaction is a managed Q&A experience.

|Feature     | Maximum limit |
|------------|---------------|
|Audience size | Up to 20,000 attendees <sup>1</sup> |
|Duration of event | 16 hours <sup>2>/sup> |
|Concurrent Live Events running in a Microsoft 365 or Office 365 organization <sup>3</sup> | 50<sup>4</sup> |

<sup>1</sup>  The usual 10,000 is increased to 20,000 until further notice. You can schedule even greater numbers with live events in Viva Engage and/or Microsoft Stream. For more information, see [Live events across Microsoft 365](/stream/live-event-m365). Events over 20,000 attendees require the [Live Events Assistance Program](/stream/live-events-assistance).

<sup>2</sup> The usual 4 hours is increased to 16 hours until further notice.

<sup>3</sup> You can schedule as many Live Events as you want, but you can only run 15 at a time. As soon as the producer joins a live event, it's considered to be running. The producer who attempts to join the 16th live event gets an error.

<sup>4</sup>  The usual 15 is increased to 50 until further notice.

For more information about live events, go to [Teams live events](teams-live-events/plan-for-teams-live-events.md#teams-live-events). See also [Schedule a Teams live event](https://support.microsoft.com/office/schedule-a-live-event-in-microsoft-teams-7a9ce97c-e1cd-470f-acaf-e6dfc179a0e2).

> [!IMPORTANT]
> **Microsoft 365 live event limit increases**
>
> **To continue supporting our customers' needs, we will extend temporary limit increases for live events until further notice, including:**
>
>- Event support for up to 20,000 attendees
>- 50 events can be hosted simultaneously across a tenant
>- Event duration of 16 hours per broadcast
>
> Additionally, Live Events with up to 100,000 attendees can be planned through the Microsoft 365 assistance program. The team will assess each request and work with you to determine options that may be available. [Learn more](https://aka.ms/Stream/Blog/LiveEventOptions).

## Presence in Outlook

Teams presence in Outlook is supported on the Outlook 2013 desktop app and later. To learn more about presence in Teams, see [User presence in Teams](presence-admins.md).

## Storage

Each team in Microsoft Teams has a team site in SharePoint Online, and each channel in a team gets a folder within the default team site document library. Files shared within a conversation are automatically added to the document library, and permissions and file security options set in SharePoint are automatically reflected within Teams.

> [!NOTE]
> Each [private channel](./private-channels.md) has its own SharePoint site (previously called "site collection").

If you don't have SharePoint Online enabled in your tenant, Microsoft Teams users can't always share files in teams. Users in private chat also can't share files because OneDrive for Business (which is tied to the SharePoint license) is required for that functionality.

By storing the files in the SharePoint Online document library and OneDrive for Business, all compliance rules configured at the tenant level are followed. (For more, see [How SharePoint Online and OneDrive for Business interact with Microsoft Teams](sharepoint-onedrive-interact.md).)

Because Teams runs on a SharePoint Online backend for file sharing, SharePoint limitations apply to the Files section within a Team. Here are the applicable storage limits for SharePoint Online.

|Feature                 |Microsoft 365 Business Basic  |Microsoft 365 Business Standard   |Office 365 Enterprise E1  |Office 365 Enterprise E3  |Office 365 Enterprise E5  |Office 365 Enterprise F1  |
|------------------------|---------|---------|---------|---------|---------|---------|
|Storage                 |1 TB per organization plus 10 GB per license purchased  |1 TB per organization plus 10 GB per license purchased  |1 TB per organization plus 10 GB per license purchased   |1 TB per organization plus 10 GB per license purchased |1 TB per organization plus 10 GB per license purchased  |1 TB per organization           |
|Storage for Teams Files |Up to 25 TB per site or group |Up to 25 TB per site or group |Up to 25 TB per site or group |Up to 25 TB per site or group |Up to 25 TB per site or group |Up to 25 TB per site or group |
|File upload limit  (per file)    |250 GB    |250 GB    |250 GB    |250 GB    |250 GB    |250 GB    |

Channels are backed by folders within the SharePoint Online site (previously called "site collection") created for the team, so file tabs within Channels share the storage limits of the team they belong to.

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
|Number of members to use Assignments in a class team    | 300        |
|Number of members to use a OneNote Class Notebook in a class team     |300         |

A class team can support more than 300 members. However, if you plan to use either the Assignments app or Class Notebook app within your team, you need to keep the number of members below the maximum limits above.

## Tags

|Feature  |Maximum limit  |
|---------|---------|
|Number of tags per team    | 200        |
|Number of suggested default tags per team    | 25        |
|Number of team members assigned to a tag    |200         |
|Number of tags assigned to a user per team    |25         |

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
