---
title: Use Microsoft Teams scoped directory search
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 10/09/2018
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: sbhatta
localization_priority: Normal
search.appverid: MET150
description: Learn how to use Microsoft Teams scoped directory search to provide customized views of the directory.
ms.custom:
- NewAdminCenter_Update
appliesto: 
- Microsoft Teams
---


# Use Microsoft Teams scoped directory search

Microsoft Teams scoped directory search allows organizations to create virtual boundaries that control how users can find and communicate with other users in their organization. 

Microsoft Teams lets organizations provide custom views of the directory to their users. Microsoft Teams uses [Exchange address book policies](https://docs.microsoft.com/en-us/Exchange/email-addresses-and-address-books/address-book-policies/address-book-policies?view=exchserver-2019) to support these custom views. Once the policies are enabled, the results returned by searches for other users (for example, to initiate a chat or to add members to a team) will be scoped according to the configured policies. Users will not be able to search or discover and join new teams outside of these policies. 

## When should you use scoped directory searches?

Scenarios that benefit from scoped directory searches are similar to address book policy scenarios. For example, you may want to use scoped directory search in the following situations:

- Your organization has multiple companies within its tenant that you want to keep separate. 
- Your school wants to limit chats between faculty and students. 
 
You can learn more about how address book policies can be used [here](https://docs.microsoft.com/en-us/Exchange/email-addresses-and-address-books/address-book-policies/abp-scenarios?view=exchserver-2019).

> [!IMPORTANT]
> Address book policies provide only a virtual separation of users from directory perspective. Users can still initiate communications with others by providing complete email addresses. 

## Enable scoped directory search

1.	Use address book policies to configure your organization into virtual subgroups. For more information, see [Procedures for address book policies](https://docs.microsoft.com/en-us/Exchange/email-addresses-and-address-books/address-book-policies/abp-procedures?view=exchserver-2019).

2.  Sign in to the Microsoft 365 admin center, select **Admin centers**, and then select **Teams & Skype**.
 
3.	In the Microsoft Teams & Skype for Business admin center, select **Org-wide settings** > **Teams settings**.

4.	Under **Search**, next to **Scope directory search in Teams using an Exchange address book policy (APB)**, turn the toggle **On**. 

    ![Scoped directory search in Teams & Skype for Business admin center](media/teams-scoped-directory-search-image1.png)

> [!NOTE]
> Hybrid configurations (Teams with Exchange on-premises) do not support scoped search mode. 

