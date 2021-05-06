---
title: Customized apps update experience in Microsoft Teams
author: cichur
ms.author: v-cichur
manager: serdars
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
localization_priority: Normal
search.appverid: MET150
description: Learn how to update customized apps in Microsoft Teams. 
---

# Update custom apps in Microsoft Teams

In most cases, after you publish an app update, the new version automatically appears for users. However, there are some updates to the <a href="/microsoftteams/platform/resources/schema/manifest-schema" target="_blank">Microsoft Teams manifest</a> that require user acceptance to complete:

* A bot was added or removed
* An existing bot's "botId" property changed
* An existing bot's "isNotificationOnly" property changed
* The bot's "supportsFiles" property changed
* A messaging extension was added or removed
* A new connector was added
* A new static tab was added
* A new configurable tab was added
* Properties inside "webApplicationInfo" changed

![new version available](media/manage-your-custom-apps-update1.png)

![upgrade option for an app](media/manage-your-custom-apps-update2.png)

## Related topics

[Manage custom apps](manage-apps.md)