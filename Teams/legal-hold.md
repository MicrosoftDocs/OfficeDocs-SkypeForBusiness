---
title: Place a Microsoft Teams user or team on legal hold
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: anach
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn to place a Microsoft Teams user or team on legal hold using the Security & Compliance Center and learn what needs a legal hold based on data requirements.
appliesto: 
  - Microsoft Teams
---

Place a Microsoft Teams user or team on legal hold
==================================================

When a reasonable expectation of litigation exists, organizations are required to preserve electronically stored information (ESI), including Teams chat messages that are relevant to the case. Organizations may need to preserve all messages related to a specific topic or for certain individuals. This article will cover legal hold in Microsoft Teams (To address hold implementation across the M365 space, please review [Manage eDiscovery cases: Place content locations on hold](https://docs.microsoft.com/microsoft-365/compliance/ediscovery-cases#step-4-place-content-locations-on-hold).).

> [!NOTE]
> In Feb 2020, we turned on legal hold or case hold on private channels (private channel chats are stored in user mailboxes, normal channel chats are stored in that Teams’ group mailboxes). If there is already a legal hold in place for a user mailbox, the hold policy will now automatically apply to private channel messages stored in that mailbox. There is no further action needed for an admin to turn this on. Legal hold of files shared in private channels is also supported.

Within Microsoft Teams, an entire team or select users can be put on hold or legal hold. Doing that will make sure that all messages that were exchanged in those teams (including private channels) or messages exchanged by those individuals are discoverable by the organization’s compliance managers or Teams Admins.

> [!NOTE]
> Placing a user on hold does not automatically place a group on hold or vice-versa.

To put a user or a team on Legal Hold:

1. Navigate to the [Security & Compliance Center](https://go.microsoft.com/fwlink/?linkid=854628). When you create a new case, you are presented with the option to place mailboxes or sites on hold.
1. Go to eDiscovery or Advanced eDiscovery and create a case by clicking “+ Create a case”. Once the case is created, open it.
![Microsoft Teams eDiscovery tab is selected, showing the Create a case button.](media/LegalHold1.png)
1. Go to “Holds” section from the top menu and click on “+ Create” to create a hold Putting a user or a team on hold saves all the messages exchanged by those users or messages When you create a new case, you are presented with the option to place mailboxes or sites on hold.
![An image showing the Holds tab selected, and the Create button underneath.](media/LegalHold2.png)
    1. **Name your hold**. Select a descriptive and unique name for the hold you are going to create.
![This screenshot shows the Name your hold tab, where you can enter in a name and description for the hold you are creating.](media/LegalHold3.png)
    1. **Choose location**. Choose whether you want the hold to be applied on a user or on an entire Team (hold cannot be applied on individual channels for now). Note: if a user is on hold, all their messages would be on hold, including whatever they sent in a 1:1 chat, 1:many or group chat, or a channel conversation (including private channels).
    ![Here we have the Choose locations section of Create a new hold, where you can make decisions on what M365 options, including Microsoft Teams, you wish the hold to apply to.](media/LegalHold4.png)
    1. **Create Query**. You can customize the hold if you want more granularity in the hold policy. For example, you can specify keywords to look for, or you can add more conditions, that would need to be satisfied for the hold to take effect.
    1. **Review your settings** before publishing it to your organization.

Once the legal hold has been set, you can discover all the content retained by any hold policy following the [Teams eDiscovery](eDiscovery-investigation.md) article.

> [!IMPORTANT]
> When a user or group is placed on hold, all message copies will be retained. For example, if a user posted a message in a channel and then modified the message, in a hold scenario, both copies of the message are retained. Without the legal hold in-place, only the latest message is retained.

As a helpful guide, you can use the table below to understand what needs to be placed on Legal Hold based on data requirements:

|Scenario  |What to place on hold  |
|---------|---------|
|**Microsoft Teams chat content by a user (on 1:1 chats, 1:many or group chats, private channel conversations, etc.)**     |User mailbox         |
|**Microsoft Teams Channel chats (excluding private channels)**    |Group mailbox used for the team         |
|**Microsoft Teams content (e.g. Wiki, Files)**     |SharePoint site used by the team         |
|**Microsoft Teams Private Channel files**     |Dedicated Private Channel SharePoint Site     |
|**User's private content**     |OneDrive for Business site of the user         |

> [!NOTE]
> To retain communication in private channels, you need to put the user mailboxes ( Private channel users) on hold and when using eDiscovery tool to search, you should search in that user’s mailbox. As was stated earlier, private channel chats are stored in user mailboxes, not in group mailbox of a Team.

If you want to read further on this topic for non-Teams areas in M365, you should review [Manage eDiscovery cases: Place content locations on hold](https://docs.microsoft.com/microsoft-365/compliance/ediscovery-cases#step-4-place-content-locations-on-hold).
