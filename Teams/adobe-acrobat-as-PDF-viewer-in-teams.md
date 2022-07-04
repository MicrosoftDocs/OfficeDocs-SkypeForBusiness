---
title: Adobe Acrobat experience in Teams
author: guptaashish
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: 
search.appverid: 
f1keywords: 
description: Learn how to set Adobe Acrobat as a default PDF viewer to view and edit PDF files in Microsoft Teams.
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
---

# Adobe Acrobat as PDF viewer in Teams

> [!NOTE]
> Adobe Acrobat experience in Teams is currently available only in [public preview](public-preview-doc-updates.md). Enable public preview for your tenant, before you use this feature.

You can set Adobe Acrobat as the default app to view and edit PDF files in the Microsoft Teams. Users don't need an Adobe Acrobat subscription or an Adobe ID to use the Adobe Acrobat app.

To setup Adobe Acrobat as the default app to view PDF files, follow these steps:

1. Log in to [Teams admin center](https://admin.teams.microsoft.com/policies/manage-apps) and go to **Teams app** > **Manage apps**.

1. Search for the Adobe Acrobat app and select **Adobe Acrobat** app.

1. In the **Permissions** tab, select **Review permission**.

1. Select **Accept**.

   :::image type="content" source="media/permission-policy.PNG" alt-text="App permission in Teams admin center." lightbox="media/teams-app-adobe-acrobat-permission.PNG":::

After you set Adobe Acrobat as default app, all PDF files from the chat, channel, and files app open directly in the Adobe Acrobat app within Teams.

## Install Adobe Acrobat app for all users

You can use the Global (Org-wide default) policy to assign and make the Adobe Acrobat app available for all users. To assign the Adobe Acrobat app for all users, follow these steps:

1. In Teams admin center, go to **Teams app** > [**Setup policies**](https://admin.teams.microsoft.com/policies/app-setup).

1. Under **Manage policies** tab, select **Global (Org-wide default)**, and then select **Edit**.

   :::image type="content" source="media/setup-policies.PNG" alt-text="Setup policies for Adobe Acrobat app in Teams admin center.":::

1. Under Installed apps, select **Add apps**.

1. Search **Adobe Acrobat**, select **Add** next to the app name and then select **Add**.

1. Select **Save**.

   :::image type="content" source="media/add-adobe-acrobat.PNG" alt-text="Add Abode Acrobat app for all users." lightbox="media/add-adobe-acrobat-app.PNG":::

If you want to block the Abode Acrobat app for users, either for an individually or for a group, you can assign a [custom app permission policy](teams-app-permission-policies.md).

Know the following information about this fucntionality:

* After the policy is setup, it typically takes few hours for users to view the app.
* Currently, Adobe Acrobat doesn't allow users to pin PDF files as a tab in a channel.
* PDF viewing experience in the Assignments app continues to remain the same as now.
* On Teams mobile, you cannot set Abobe Acrobat as the default PDF viewer.
