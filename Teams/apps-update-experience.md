---
title: Apps update experience in Microsoft Teams
author: guptaashish
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
f1.keywords: 
  - NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: In this article, learn how Microsoft apps, custom apps, and third-party apps in Microsoft Teams are updated and how admins facilitate it.
---

# Update apps in Microsoft Teams

In most cases, after a new version of an app is available in the Teams Store, the app is automatically updated for users. However, a few specific changes in the new app version require user acceptance for the app to update. The user acceptance ensures awareness about the changes such as functionality or access. If app developers make the following specific changes to the Microsoft Teams apps, then your end-users must approve the app update:

* A bot is added.
* An existing bot's `botId` property or `isNotificationOnly` property is changed.
* A bot's `SupportsCalling`, `SupportsVideo`, and `SupportsFiles` capability is added.
* A messaging extension is added.
* Permissions inside Authorization are added or changed.
* `Id` or `ApplicationPermissionsHash` or both are changed inside the `webApplicationInfo`.

<!--- image update
:::image type="content" source="media/manage-your-custom-apps-update1.png" alt-text="New version available." lightbox="media/manage-your-custom-apps-update1.png":::

:::image type="content" source="media/manage-your-custom-apps-update2.png" alt-text="Upgrade option for an app." lightbox="media/manage-your-custom-apps-update2.png":::
--->

## Related articles

* [Understand manifest schema for updates done in apps](/microsoftteams/platform/resources/schema/manifest-schema).
