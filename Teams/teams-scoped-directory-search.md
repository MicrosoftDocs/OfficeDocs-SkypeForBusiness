---
title: Limit who users can see when searching the directory in Teams
author: MikePlumleyMSFT
ms.author: mikeplum
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: sbhatta
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

Microsoft Teams lets organizations provide custom views of the directory to their users. These can be useful if:

- Your organization has multiple companies within its tenant that you want to keep separate.
- Your business policies require that you prevent certain groups within your organization from communicating with each other.
- Your school wants to limit chats between faculty and students. 

There are two options for limiting who users can see when they search the directory in Teams:

- [Information Barrier policies](/microsoft-365/compliance/information-barriers)
- [Address book policies in Exchange Online](/exchange/address-books/address-book-policies/address-book-policies)

We recommend using information barriers if your organization meets the [required licenses and permissions](/microsoft-365/compliance/information-barriers#required-licenses-and-permissions).

If you choose to use address book policies in Exchange, you must turn on search by name in the Teams admin center.

To turn on search by name

1. In the Microsoft Teams admin center, select **Teams** > **Teams settings**.

1. Under **Search by name**, next to **Scope directory search in Teams using an Exchange address book policy**, turn the toggle **On**.

> [!Note]
> It may take a few hours for this change to take effect.
