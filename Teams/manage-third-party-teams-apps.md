---
title: Manage access to third-party Teams apps across Microsoft 365
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
ms.localizationpriority: medium
search.appverid: MET150
description: Manage access to third-party Teams apps across Microsoft 365. 
---

# Manage access to third-party Teams apps across Microsoft 365

App developers can update their Microsoft Teams apps to work in Outlook and on Office.com, in addition to working in Teams. The end-users can use the updated apps on Teams, in Microsoft Outlook and Microsoft Office.com after the updates. Currently, only the end-users in Targeted release can view and use a few specific apps in Teams, Outlook, and Office.com. The existing Teams admin experience applies to govern access to these apps. A notification about this change is available in the [message center](https://admin.microsoft.com/AdminPortal/Home#/MessageCenter/:/messages/MC334280). As a Teams administrator, you can allow specific end-users to use the updated apps or manage the access to the updated apps in Teams, in Outlook, and on Office.com. Teams administrators use the Teams admin center to manage app access.

<!--- TBD: Check later if this is not already true. "Third-party apps may be subject to their own terms and privacy policies."
 --->

You can control end-user access to the Teams third-party apps using the following methods. If you're an Office Apps admin, contact your Global admin or Teams admin to manage app access.

|Scenario|Portal|Global admin|Teams administrator|
|--|---|---|--|
| Only the end-users in Targeted release can access the new app. <br> Move the users to Standard release. See [Set up the Standard or Targeted release options](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true) | Microsoft 365 admin center | Yes | No |
| Manage access to the new app for specific users. <br> See [Add a custom permission policy](teams-app-permission-policies.md#create-a-custom-app-permission-policy) and [assign the custom policy to a user](policy-assignment-overview.md). | Teams admin center | Yes | Yes |
| Manage access to the new apps for all users across your organization. <br> See [Allow or block apps](manage-apps.md#allow-and-block-apps). | Teams admin center | Yes | Yes |

> [!NOTE]
   > Users who have installed an existing in-market add-ins of the same app in Outlook and Office continues to use the app. The add-ins are not Teams apps and Teams administrators can not govern the access.

## See also

* [Understand admin roles in Microsoft 365](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide&preserve-view=true)  
* [About Outlook add-ins](/office/dev/add-ins/outlook/outlook-add-ins-overview)
* [How developers extend Teams apps to work across Microsoft 365](/microsoftteams/platform/m365-apps/overview)
