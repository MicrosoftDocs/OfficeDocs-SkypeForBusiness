---
title: Create a resource account using the Microsoft 365 admin center
description: If you prefer to use a graphical user interface, you can create a resource account for your Microsoft Teams Rooms and collaboration bars for Microsoft Teams using the Microsoft 365 Admin Center.
ms.reviewer: payurevi
manager: serdars
audience: ITPro
keywords: create device account, Microsoft 365 UI, Microsoft 365 admin center
ms.sitesec: library
ms.service: msteams
author: cazawideh
ms.author: czawideh
ms.topic: article
ms.localizationpriority: medium
---

# Create a Microsoft 365 resource account using the Microsoft 365 admin center

Microsoft 365 resource accounts are mailbox and Teams accounts that are dedicated to specific resources, such as a room, projector, and so on. These resource accounts can automatically respond to meeting invites using rules you define when they're created. For example, if you have a common resource such as a conference room, you can set up a resource account for that conference room that will automatically accept or decline meeting invites depending on its calendar availability.

<!-- The steps in this article show you how to set up a resource account using the Microsoft 365 admin center. If you'd rather use PowerShell to create resource accounts, [Create a resource account using the PowerShell](resource-account-ps.md). -->

[!INCLUDE [m365-teams-resource-account-difference](../includes/m365-teams-resource-account-difference.md)]

## Licensing

Before you create a Microsoft 365 resource account, check to see what kind of license it needs. If you'll only use a resource account to book a resource (that is, invite the resource to your meeting and have it automatically accept or decline the invitation), you don't need to assign a license to a resource account. You'll need to assign a license to the resource account in the following situations:

- **Teams meeting** If you want the resource, such as a Microsoft Teams Room, to join a Teams meeting so attendees can use it to present video and audio through it, see [Create and configure resource accounts for Teams devices](../rooms/with-office-365.md) to set up resource accounts with a Meeting Room license.

- **PSTN calls** If you want the resource to make or receive calls to or from an external phone numbers (called a Public Switched Telephone Network or PSTN call), you need a Microsoft 365 Phone System or Microsoft 365 Business Voice license.

For more information about Meeting Room, Phone System, and Business Voice licenses, see [Microsoft Teams add-on licenses](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md)

## Create a resource account in Microsoft 365 admin center

[!INCLUDE [Create a resource account in the Microsoft 365 admin center](../includes/create-m365-resource-account.md)]
