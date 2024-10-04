---
title: Custom emojis in Microsoft Teams
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.topic: article
ms.date: 07/15/2024
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
ms.reviewer: 
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about adding custom emojis to Microsoft Teams chats.
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
---

# Custom emojis in Microsoft Teams

Microsoft Teams now allows users to add their own custom emojis and reactions by uploading an image or GIF file. These emojis and reactions are also accessible to all users in the tenant alongside the standard Teams emojis and reactions. Up to 5,000 custom emojis can be added per tenant. This feature is currently not available for EDU tenants.

The new custom emojis and reactions feature will be turned on by default. Users in the tenant will be able to upload emojis. You can preemptively turn this feature off or restrict which users can create new emojis via the Teams Admin Center controls described in this article.

> [!NOTE]
> Custom emojis are available in cross-tenant and federated scenarios. Users outside of your tenant will not have access to your custom emojis unless emojis are sent in conversations with them.

## Timelines

- Targeted Release: This was completed in mid-July 2024.
- Worldwide, GCC: We began rolling out early July 2024 and expect to complete by early August 2024.
- GCC High, DoD: We'll begin rolling out early August 2024 and expect to complete by early September 2024.

## How to use this feature

Custom emojis and reactions are found in the emoji and reaction menus in the **Custom** category. Users with upload abilities can add new content through the **Plus** (**+**) button. Users with delete abilities can select any custom emoji to delete.

> [!NOTE]
> Deleted emojis may take up to 24 hours to reflect for all users in the tenant. Users may clear the cache on their own devices to see the removal sooner.

## How to manage this feature

This feature can be managed through the Teams admin center. Admins have access to the following controls:

- Turn the feature on/off for the whole tenant via the Messaging Settings page (on by default).
- Set which users can create new emojis via the Messaging Policy groups (on for all users by default).
- Set which users can delete emojis via the Messaging Policy groups (off for all users except admins by default).

The Teams Admin Center controls are available now, by going to the **Messaging Settings** section and turning the **use custom emojis** option, found under the **Custom emojis** section, on or off. We recommend adjusting your settings as needed prior to late June 2024 to ensure that they're in place when the feature rolls out.

The **Messaging policies** section of the Teams admin center will allow you to turn the **Upload custom emojis** and **Delete custom emojis** settings on or off.

> [!NOTE]
> Uploading custom emojis is enabled for all users by default, and the deletion of custom emojis is enabled for Admins by default.
