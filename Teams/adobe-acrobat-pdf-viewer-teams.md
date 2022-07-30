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

# Adobe Acrobat as a default PDF viewer in Microsoft Teams

> [!NOTE]
> Adobe Acrobat as a default PDF experience in Microsoft Teams is currently available only in public preview. [Enable public preview](public-preview-doc-updates.md#enable-public-preview) for your tenant, before you use this feature. Ensure that the end-users change Teams client version to public preview to experience Adobe Acrobat as PDF viewer in Teams.

As an admin, you can set Adobe Acrobat as the default app to view and edit PDF files in Microsoft Teams. Your end-users can view, search, comment and annotate PDF files without an Adobe Acrobat subscription or an Adobe ID.

## Set up Adobe Acrobat app

Before you set up the app, ensure that you allow apps to be used in your tenant, that you've specifically allowed Adobe Acrobat app, and the app permission policies allow it. To set up Adobe Acrobat as the default app for PDF files, follow these steps:

1. Sign in to Teams admin center and go to **Teams app** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Search for the Adobe Acrobat app and select it.

1. In the **Permissions** tab, select **Review permission**.

   :::image type="content" source="media/permission-policy.png" alt-text="Screenshot of app permission in Teams admin center." lightbox="media/teams-app-adobe-acrobat-permission.png":::

1. Select **Accept**.

## Install Adobe Acrobat app for all users

To assign and make the Adobe Acrobat app available for all users, follow these steps:

1. In Teams admin center, go to **Teams app** > [**Setup policies**](https://admin.teams.microsoft.com/policies/app-setup).

1. Under **Manage policies** tab, select **Global (Org-wide default)**, and then select **Edit**.

   :::image type="content" source="media/setup-policies.png" alt-text="Screenshot of setup policies for Adobe Acrobat app in Teams admin center.":::

1. Under Installed apps, select **Add apps**.

1. Search **Adobe Acrobat**, select **Add** next to the app name and then select **Add**.

   :::image type="content" source="media/add-adobe-acrobat.png" alt-text="Screenshot that shows how to add Adobe Acrobat app for all users." lightbox="media/add-adobe-acrobat-app.png":::

1. Select **Save**.

After you select save, Teams uses Adobe Acrobat app as the default file handler for PDF files.

If you want to selectively allow the Adobe Acrobat app for a few individuals or for a group, you can assign a [custom app permission policy](teams-app-permission-policies.md).

Know the following information about this functionality:

* After the policy is set up, it typically takes a [few hours](teams-app-setup-policies.md) for the app to be available for users.
* After the policy is set up, installed app is available for users after a few hours.
* Viewing of PDF files that are pinned in channels as a tab and viewing of PDF files in assignments app continues to be powered by the native Teams experience.
* Adobe Acrobat as a default PDF viewer in Teams works only on desktop and web clients. It isn't supported on mobile client.
* Users need an Adobe Acrobat plan to use the premium tools such as Export PDF, Organize Pages, Combine Files, Compress PDF, and Protect PDF.
* To uninstall the app, end-users can remove the app from the Teams client. Admin can remove the Adobe Acrobat app by using setup policy.
* If you block Adobe Acrobat app, then remove it from the setup policy. It ensures that the end-user experience reverts to the native PDF file viewer.
* From Teams desktop client, if you face any issues while signing in to Adobe Acrobat app, use Teams in browser to sign in.

<!---
Admins can block the Adobe Acrobat app once it's set as a default handler. Before the admin blocks the app, remove the setup policy to ensure that the end-users are safely brought back to Teams default experience.
--->
