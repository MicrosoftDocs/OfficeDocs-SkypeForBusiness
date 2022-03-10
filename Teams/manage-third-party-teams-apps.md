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
description: Manage access to third party Teams apps across Microsoft 365. 
---

# Manage access to third-party Teams apps across Microsoft 365

The app users can now use the existing Teams apps experience across Microsoft Outlook and Microsoft Office.com after these apps are updated to work in Outlook and on Office.com. Currently, only the end-users in Targeted release can view and use a few select apps in Teams, Outlook, or Office.com. The existing Teams admin experience also applies to governing access to these apps. A notification about this change is available in the [message center](https://admin.microsoft.com/AdminPortal/Home#/MessageCenter/:/messages/MC334280). As a Teams administrator, you can allow specific end-users to use the updated apps or block the access to the updated apps in Teams, in Outlook, and on Office.com.

<!--- To be checked:
The Third-party Teams apps are subject to the Teams administration policies available at [Teams admin center](https://admin.teams.microsoft.com/dashboard).
--->

<!--- 
As an admin, you can manage access to the new Teams third party apps for your users:

1. Change the release option to Standard release in TAC. For more information, see [Set up the Standard or Targeted release options](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true).

1. If you're unable to change users to Standard release, [add a custom permission policy](teams-app-permission-policies.md#create-a-custom-app-permission-policy) to block the app and [assign the custom policy to the user](policy-assignment-overview.md).

1. If you're unable to remove the user assignment to the app in Teams, you can block the new third party app for all users. For more information, see [Allow or block apps](manage-apps.md#allow-and-block-apps)

> [!Note]
> Third-party apps may be subject to their own terms and privacy policies.
 --->

You can control user access to the Teams third-party apps using the following methods. If you're an Office Apps admin, contact your Global admin or Teams admin to manage app access.

|Scenario|Portal|Global admin|Teams administrator|
|--|---|---|--|
|Only select users who are part of Targeted release can access the new app. <br> Move the users to Standard release.  See [Set up the Standard or Targeted release options](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true)|Microsoft admin center|Yes|No|
|Remove access to the new app for specific users by modifying app permission policy.<br>[Add a custom permission policy](teams-app-permission-policies.md#create-a-custom-app-permission-policy) to block the app and [assign the custom policy to the user](policy-assignment-overview.md).|Teams admin center|Yes|Yes|
|Remove access to the new apps for all users by blocking the app across your organization. For more information, see [Allow or block apps](manage-apps.md#allow-and-block-apps).|Teams admin center|Yes|Yes|

> [!NOTE]
   > Users who have installed an existing in-market add-ins of the same app in Outlook and Office continues to use the app. The add-ins are not Teams apps and Teams administrators can not govern the access.

## See also

* [Understand admin roles in Microsoft 365](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide&preserve-view=true)  
* [About Outlook add-ins](/office/dev/add-ins/outlook/outlook-add-ins-overview)
