---
title: Manage Teams third party apps
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

# Manage access to third party apps in Teams

New Teams third party apps will be available for users in Outlook and Office.com soon. Users in Targeted Release will be able to acquire and use these apps in Teams, Outlook, or Office.com.  For more information on Targeted release rollout, see this post on [Message Center (MC)](https://admin.microsoft.com/AdminPortal/Home#/MessageCenter/:/messages/MC334280).

The New Teams third party apps are subject to the Teams administration policies available at [Teams admin center](https://admin.teams.microsoft.com/dashboard) and also their own terms and privacy policies.

As an admin, you can manage access to the new Teams third party apps for your users.

1. You can restrict access for the new Teams third party apps to view only in Teams by changing the release option to Standard release in TAC. For more information, see [Set up the Standard or Targeted release options](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true).

1. If you're unable to change users to Standard release, [add a custom permission policy](teams-app-permission-policies.md#create-a-custom-app-permission-policy) to block the app and [assign the custom policy to the user](policy-assignment-overview.md).

1. If you're unable to remove the user assignment to the app in Teams, you can block the new Third party app in teams for all users. For more information, see [Allow or block apps](manage-apps.md#allow-and-block-apps)

   > [!NOTE]
   > Users who have installed an existing in-market add-ins of the same app in Outlook and Office will continue to see the app.

## Table format

As an admin, you can check the following table to manage access to the new Teams third party apps for your users:

|Request|Solution|Portal|Global Admin|Teams Services Admin|Office Admin|
|--|--|---|---|--|--|
|I want the user to see the app only in Teams, and not see in Outlook or in Office.|Move the users from the Targeted release to Standard release.|Microsoft admin center|Yes|No|No|
|I cannot move my users from Targeted release to Standard release.|Remove the user’s user assignment to the app in Teams.|Teams Admin Center|Yes|Yes|No|
|I cannot remove their user assignment to the app in Teams, the policies are complicated.|Block the app in Teams. The end users will not see this new app in Teams, Outlook, or Office.|Teams Admin Center|Yes|Yes|No|

## Block a third party app for users

1. In the TAC, go to Teams apps > Permission policies.
1. Click **Add**.
1. Enter the policy name and description.
1. Under Third-party apps, click the drop-down and select **Block specific apps and allow all others**.
1. To add the app you want to block, select **Block apps**.  
A dialog box appears at the right.
1. Enter the app name in the search field, select the app from the list and select **Add**.
1. Select **Block**.
1. Select **Save**.
