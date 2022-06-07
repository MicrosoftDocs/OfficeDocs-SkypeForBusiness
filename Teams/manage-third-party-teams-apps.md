---
title: Manage access to Teams apps across Microsoft 365
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
description: In this learning module, you'll learn how to manage access to Teams apps for end-users across Microsoft 365. 
---

# Manage access to Teams apps across Microsoft 365

App developers can enhance their Microsoft Teams apps to work in Outlook and on Office.com, in addition to the app working in Teams. The end-users can use the enhanced apps on Teams, in Microsoft Outlook and Microsoft Office.com after the enhancement. Currently, only the end-users in Targeted release can view and use these specific apps in Teams, Outlook, and Office.com. The existing Teams admin experience applies to govern access to these apps. A notification about this change is available in the [message center](https://admin.microsoft.com/AdminPortal/Home#/MessageCenter/:/messages/MC334280). As a Teams administrator, you can allow specific end-users to use the enhanced apps or manage their access to the enhanced apps in Teams, in Outlook, and on Office.com. Teams administrators use the Teams admin center to manage app access.

For use in Outlook and Office.com, an enhanced app continues to use the existing permissions granted in Teams. There is [no change in the permissions of the enhanced app](https://devblogs.microsoft.com/microsoft365dev/ignite-2021-building-apps-for-collaboration-in-a-hybrid-world/#personal-tabs).

The following is a list of the enhanced apps:

* [Monday.com](https://teams.microsoft.com/l/app/eab2d3ce-6d6a-4415-abc4-5f40a8317b1f)
* [Mural](https://teams.microsoft.com/l/app/c738b607-88dd-4f16-aefe-6a824c65d25d)
* [Power BI](https://teams.microsoft.com/l/app/1c4340de-2a85-40e5-8eb0-4f295368978b)
* [SurveyMonkey](https://teams.microsoft.com/l/app/0fd925a0-357f-4d25-8456-b3022aaa41a9)
* [Zoho Projects](https://teams.microsoft.com/l/app/4a39aea9-8537-4c2f-b66d-ca364eb3b80d)
* [YouTube](https://teams.microsoft.com/l/app/com.microsoft.teamspace.tab.youtube)

You can control end-user access to the Teams apps using the following methods. If you're an Office Apps admin, contact your Global admin or Teams admin to manage app access.

| Options to manage access |Portal|Global admin|Teams administrator|
|--|---|---|--|
| Only the end-users in Targeted release can access the new app. Move the users to Standard release. See [Set up the Standard or Targeted release options](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true) | Microsoft 365 admin center | Yes | No |
| Manage access to the new app for specific end-users. See [Add a custom permission policy](teams-app-permission-policies.md#create-a-custom-app-permission-policy) and [assign the custom policy to a user](policy-assignment-overview.md). | Teams admin center | Yes | Yes |
| Manage access to the new apps for all end-users across your organization. See [Allow or block apps](manage-apps.md#allow-and-block-apps). | Teams admin center | Yes | Yes |

> [!NOTE]
> We recommend using [the Standard release option](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true) to manage end-user access. The other options remove the end-user access and they will no longer be able to use the existing app in Teams.

> [!NOTE]
> Users who have installed an existing in-market add-ins of the same app in Outlook and Office will continue to use that app. The add-ins are not Teams apps and Teams administrators can not govern the access.

## See also

* [Microsoft Teams apps designed for Microsoft 365 coming in Preview to Outlook and Office.com](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-teams-apps-designed-for-microsoft-365-coming-in/ba-p/3269538)
* [Understand admin roles in Microsoft 365](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide&preserve-view=true)  
* [About Outlook add-ins](/office/dev/add-ins/outlook/outlook-add-ins-overview)
* [How developers extend Teams apps to work across Microsoft 365](/microsoftteams/platform/m365-apps/overview)
