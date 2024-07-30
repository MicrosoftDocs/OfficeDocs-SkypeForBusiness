---
title: Limit who users can see when searching the directory in Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 02/23/2024
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to limit who users can see when searching the directory in Teams.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---

# Limit who users can see when searching the directory in Teams

Microsoft Teams lets organizations provide custom views of the directory to their users. These views can be useful if:

- Your organization has multiple companies within its tenant that you want to keep separate.
- Your business policies require that you prevent certain groups within your organization from communicating with each other.
- Your school wants to limit chats between faculty and students.

There are two options for limiting who users can see when they search the directory in Teams:

- [Information barriers in Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Address book policies in Exchange Online](/exchange/address-books/address-book-policies/address-book-policies)

If using either option, you must turn on search by name in the Teams admin center.

We recommend using information barriers if your organization meets the [required licenses and permissions](/microsoft-365/compliance/information-barriers#required-licenses-and-permissions).

> [!NOTE]
> Information barriers V1 and address book policies are automatically respected for people search in all people search entry points in new Teams client when configured. There's no need to enable this setting to hide users in search.

To turn on search by name:

1. In the Microsoft Teams admin center, select **Teams** > **Teams settings**.

1. Under **Search by name**, next to **Scope directory search using an Exchange address book policy**, turn the toggle **On**.

> [!NOTE]
> It may take a few hours for this change to take effect.
>
> Turning on search by name hides the **Search teams** box and public teams listing in **Join or create a team** in Teams. It will also disable joining a team by typing `/join` in the command box at the top of Teams.

When **Scope directory search using an Exchange address book** policy is turned on, most accounts that are marked as hidden in Exchange don't show up in Teams searches. Personal contacts show up regardless of the Search by Name setting.
