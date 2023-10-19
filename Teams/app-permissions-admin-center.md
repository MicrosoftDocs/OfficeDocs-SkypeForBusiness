---
title: View app permissions and grant admin consent in the Microsoft Teams admin center
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.date: 10/18/2023
ms.reviewer: Orion.OMalley
search.appverid: MET150
description: Learn how to view permissions requested by apps and grant admin consent to apps on the Manage apps page of the Microsoft Teams admin center. 
ms.localizationpriority: medium
ms.collection: M365-collaboration
appliesto: 
- Microsoft Teams
---

# View app permissions and grant admin consent in Teams admin center













## Known issues

The "View details" link isn't displayed in the Permissions column for some third-party apps that request permissions. The ability to review permissions and grant consent isn't available for all third-party apps. Typically, the third-party apps are registered in Azure Active Directory when the apps request permissions. Instead of the **View details** link, you'll see `--` in the **Permissions** column.

## Related articles

* [Understand user and admin consent in Azure AD](/azure/active-directory/manage-apps/user-admin-consent-overview)
* [Permissions and consent in the Microsoft identity platform endpoint](/azure/active-directory/develop/v2-permissions-and-consent)
* [Resource-specific consent in Teams](resource-specific-consent.md)
* [Resource-specific consent (RSC)](/microsoftteams/platform/graph-api/rsc/resource-specific-consent)
* [Navigate the Teams app lifecycle](https://aka.ms/PR132) (Ignite 2020 session)
