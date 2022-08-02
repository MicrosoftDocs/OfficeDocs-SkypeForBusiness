---
title: Apps update experience in Microsoft Teams
author: guptaashish
ms.author: guptaashish
manager: prkosh
ms.reviewer: v-tbasra
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: In this article, learn how Microsoft apps, custom apps, and third-party apps in Microsoft Teams are updated.
---

# Update apps in Microsoft Teams

In most cases, after app developers publish an app update, the new version automatically appears for users. However, there are some updates to the [Microsoft Teams manifest](/microsoftteams/platform/resources/schema/manifest-schema) that require user acceptance to complete:

* A bot was added or removed.
* An existing bot's "botId" property changed.
* An existing bot's "isNotificationOnly" property changed.
* A bot's SupportsCalling, SupportsVideo, and SupportsFiles capability was added.
* A messaging extension was added.
* A new connector was added.
* Permissions inside "Authorization" were added or changed.

:::image type="content" source="media/manage-your-custom-apps-update1.png" alt-text="New version available." lightbox="media/manage-your-custom-apps-update1.png":::

:::image type="content" source="media/manage-your-custom-apps-update2.png" alt-text="Upgrade option for an app." lightbox="media/manage-your-custom-apps-update2.png":::

> [!NOTE]
> The update process applies to all app updates for Microsoft apps, custom apps, and third-party apps.
