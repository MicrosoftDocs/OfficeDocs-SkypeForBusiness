---
title: Use Microsoft Teams scoped directory search
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.date: 06/21/2019
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: sbhatta
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to use Microsoft Teams scoped directory search to provide customized views of the directory.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---


# Use Microsoft Teams scoped directory search

Microsoft Teams scoped directory search allows organizations to create virtual boundaries that control how users can find and communicate with other users in their organization. 

Microsoft Teams lets organizations provide custom views of the directory to their users. Microsoft Teams uses [Information Barrier policies](/microsoft-365/compliance/information-barriers) to support these custom views. Once the policies are enabled, the results returned by searches for other users (for example, to initiate a chat or to add members to a team) will be scoped according to the configured policies. Users will not be able to search or discover any teams when scoped search is in effect, but existing members in those teams can add users, as allowed by active Information Barrier policies.

> [!NOTE]
> In Exchange hybrid environments, this feature only works with Exchange Online mailboxes, and not with on-premises mailboxes.

## When should you use scoped directory searches?

Scenarios that benefit from scoped directory searches are similar to address book policy scenarios. For example, you may want to use scoped directory search in the following situations:

- Your organization has multiple companies within its tenant that you want to keep separate. 
- Your school wants to limit chats between faculty and students. 
 
To learn how to use address book policies, read [Information Barrier policies in Exchange Online](/microsoft-365/compliance/information-barriers).

> [!IMPORTANT]
> Address book policies provide only a virtual separation of users from directory perspective. It is also important to note that any user data that had already been cached, prior to the enforcement of new or updated address book policies, will remain available to users for up to 30 days.

## Turn on scoped directory search

1. Use Information Barrier policies to configure your organization into virtual subgroups. For more information, see [Define Information Barrier policies](/microsoft-365/compliance/information-barriers-policies).

2. In the Microsoft Teams admin center, select **Org-wide settings** > **Teams settings**.

3. Under **Search**, next to **Scope directory search in Teams using an Exchange address book policy (ABP)**, turn the toggle **On**.

    ![Scoped directory search in Microsoft Teams admin center](media/teams-scoped-directory-search-image1.png)


> [!IMPORTANT]
> This change can take a few hours to replicate.