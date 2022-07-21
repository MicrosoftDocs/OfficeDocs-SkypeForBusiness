---
title: Adobe Acrobat as a default PDF viewer in Teams
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

# Adobe Acrobat as a default PDF viewer in Teams

> [!NOTE]
> Adobe Acrobat as a default PDF experience in Teams is currently available only in public preview. [Enable public preview](public-preview-doc-updates.md#enable-public-preview) for your tenant, before you use this feature. Ensure that you change your Teams client version to public to experience Adobe Acrobat as PDF viewer in Teams.

As an admin, you can set Adobe Acrobat as the default app to view and edit PDF files in the Microsoft Teams. Your end-users don't need an Adobe Acrobat subscription or an Adobe ID to view, search, comment and annotate PDFs.

## Set up Adobe Acrobat app

To set up Adobe Acrobat as the default app to view PDF files, follow these steps:

1. Log in to Teams admin center and go to **Teams app** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Search for the Adobe Acrobat app and select **Adobe Acrobat** app.

   > [!NOTE]
   > Ensure the Adobe Acrobat app status is set to **Allowed**. Else, enable the **Allowed** toggle.

1. In the **Permissions** tab, select **Review permission**.

1. Select **Accept**.

   :::image type="content" source="media/permission-policy.png" alt-text="App permission in Teams admin center." lightbox="media/teams-app-adobe-acrobat-permission.PNG":::

## Install Adobe Acrobat app for all users

You can use the Global (Org-wide default) policy to assign and make the Adobe Acrobat app available for all users. To assign the Adobe Acrobat app for all users, follow these steps:

1. In Teams admin center, go to **Teams app** > [**Setup policies**](https://admin.teams.microsoft.com/policies/app-setup).

1. Under **Manage policies** tab, select **Global (Org-wide default)**, and then select **Edit**.

   :::image type="content" source="media/setup-policies.png" alt-text="Setup policies for Adobe Acrobat app in Teams admin center.":::

1. Under Installed apps, select **Add apps**.

1. Search **Adobe Acrobat**, select **Add** next to the app name and then select **Add**.

   :::image type="content" source="media/add-adobe-acrobat.png" alt-text="Add Adobe Acrobat app for all users." lightbox="media/add-adobe-acrobat-app.PNG":::

1. Select **Save**.

After you select save, the Adobe Acrobat app is configured with Teams to open any PDF files in the Adobe Acrobat app from the chat, channel, or files app.

If you want to selectively allow the Adobe Acrobat app for a few specific individuals or for a group, you can assign a [custom app permission policy](teams-app-permission-policies.md).

Know the following information about this functionality:

* After the policy is set up, it typically takes [few hours](teams-app-setup-policies.md) for users to view the installed app.
* Pinning PDFs in channels is powered by native Teams experience.
* PDF viewing experience in the Assignments app continues to remain the same.
* Adobe Acrobat as PDF experience in Teams works only on desktop and web clients. It is not supported on mobile apps.

> [!NOTE]
> From Teams desktop client, if you face any issues while signing to Adobe Acrobat app, you can open Teams in browser and sign in. This is a known issues and will be resolved by September 2022.
