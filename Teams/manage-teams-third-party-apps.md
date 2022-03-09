---
title: Manage Teams third-party apps
author: v-ypalikila
ms.author: v-ypalikila
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
description: Manage access to third party apps in Teams. 
---

# Manage Teams third-party apps

Microsoft Teams allows you to extend your Teams apps across Microsoft Office and Outlook. To extend this functionality, we're making Teams third-party apps available for users in Outlook and Office.com. Users in Targeted Release can receive and view these apps in Teams, Outlook, or Office.com. For more information, see [Message Center (MC)](https://admin.microsoft.com/AdminPortal/Home#/MessageCenter/:/messages/MC334280).

Teams third-party apps are subject to the Teams administration policies available at [Teams admin center](https://admin.teams.microsoft.com/dashboard).

> [!Note]
> Third-party apps may be subject to their own terms and privacy policies.

<!--- 
As an admin, you can manage access to the new Teams third party apps for your users:

1. Change the release option to Standard release in TAC. For more information, see [Set up the Standard or Targeted release options](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true).

1. If you're unable to change users to Standard release, [add a custom permission policy](teams-app-permission-policies.md#create-a-custom-app-permission-policy) to block the app and [assign the custom policy to the user](policy-assignment-overview.md).

1. If you're unable to remove the user assignment to the app in Teams, you can block the new third party app for all users. For more information, see [Allow or block apps](manage-apps.md#allow-and-block-apps)

   > [!NOTE]
   > Users who have installed an existing in-market add-ins of the same app in Outlook and Office will continue to see the app.

 --->

You can check the following table to control user access to the Teams third party apps:

Office app admins can't control Teams third-party apps. If you're an office app admin, reach out to Global admin.

|Scenario|Portal|Global Admin|Teams Administrator|
|--|---|---|--|
|Only select users who are part of Targeted release can access the new app. <br> Move the users to Standard release.  See [Set up the Standard or Targeted release options](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true)|Microsoft admin center|Yes|No|
|Remove access to the new app for specific users by modifying app permission policy.<br>[Add a custom permission policy](teams-app-permission-policies.md#create-a-custom-app-permission-policy) to block the app and [assign the custom policy to the user](policy-assignment-overview.md).|Teams admin center|Yes|Yes|
|Remove access to the new apps for all users by blocking the app across your organization. For more information, see [Allow or block apps](manage-apps.md#allow-and-block-apps).|Teams admin center|Yes|Yes|

## See also
[About admins roles in Microsoft 365](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide&preserve-view=true)
