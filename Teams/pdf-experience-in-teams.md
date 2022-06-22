---
title: Pdf experience in Teams
author: ashishgupta
ms.author: ashishgupta
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
description: Learn how to set adobe acrobat PDF viewer as a default app to view and edit PDF files in Teams with Microsoft Teams admin center.
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
---

# Adobe acrobat PDF experience in Teams

You can set Adobe Acrobat as the default app to view and edit PDF files in the Microsoft Teams by setting up a policy to install the app and giving required permissions to the app in the Teams admin center.

Once the app is set as default, all PDF files from the chat, channel, and files app will open directly in the Acrobat app within Teams. Your tenant users do not need an Adobe Acrobat subscription or an Adobe ID to view the PDFs, view bookmarks, search a PDF, and comment or annotate in PDFs.

## Set up Adobe Acrobat app to work in the tenant

To set Adobe Acrobat as default PDF handler, follow these steps:

1. Log in to [Teams admin center](https://admin.teams.microsoft.com/).

   :::image type="content" source="media/TAC-main-page.PNG" alt-text="TAC-dashboard":::

1. Go to Teams app and select **Manage apps** from left pane.

   :::image type="content" source="media/TAC-teams-app.PNG" alt-text="manage apps TAC":::

1. Search for the Adobe Acrobat app and select the **Adobe Acrobat** app.

   :::image type="content" source="media/TAC-teams-app-adobe.PNG" alt-text="adobe-acrobat-tac":::

1. On the Permissions tab, select **Review permission**. The consent request page appears.
[]
1. Select **Accept** to grant consent.

   :::image type="content" source="media/TAC-teams-app-adobe-acrobat-permission.PNG" alt-text="TAC-teams-permission":::

Now you've successfully added Adobe Acrobat app to work in the Teams tenant.

:::image type="content" source="media/TAC-consent.png" alt-text="TAC-adobe-consent":::

## Make Adobe Acrobat app available for users

1. Log in to [Teams admin center](https://admin.teams.microsoft.com/).

1. Go to Teams app and select **Setup policies** from left pane.

1. Select **Global (Org-wide default)**, and then select **Edit**.

   :::image type="content" source="media/TAC-setup-policies.PNG" alt-text="setup-policies":::

1. Select **Add**.

1. Search **Adobe Acrobat** app and select **Add**, and save the policy.

   :::image type="content" source="media/TAC-add-app.PNG" alt-text="TAC-adobe-app-add":::

Users receives a welcome message from Adobe Acrobat app in Teams.

:::image type="content" source="media/adobe-pdf-teams.PNG" alt-text="Teams-adobe":::

## Limitations

1. Pinning PDF files (powered by Adobe) as a tab on channel is not supported as of now.

1. PDF experience inside Assignments app will remain within Teams experience.
