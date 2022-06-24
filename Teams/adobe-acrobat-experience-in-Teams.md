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

# Adobe Acrobat experience in Teams

You can set Adobe Acrobat as the default app to view and edit PDF files in the Microsoft Teams. Users don't need an Adobe Acrobat subscription or an Adobe ID to use the Adobe Acrobat app.

## Set up Adobe Acrobat as default app

To set up Adobe Acrobat as default app, follow these steps:

1. Log in to [Teams admin center](https://admin.teams.microsoft.com/).

1. Go to **Teams app** > **Manage apps**.

1. Search for the Adobe Acrobat app and select **Adobe Acrobat** app.

   :::image type="content" source="media/teams-admin-center-teams-app-adobe.PNG" alt-text="adobe-acrobat in teams-admin-center":::

1. On the Permissions tab, select **Review permission**. The consent request page appears.

1. Select **Accept**.

   :::image type="content" source="media/teams-app-adobe-acrobat-permission.PNG" alt-text="app permission in Teams admin center":::

   Now you've successfully added Adobe Acrobat as a default app.

   :::image type="content" source="media/consent-permission.png" alt-text="Teams admin center adobe app consent":::

After you set Adobe Acrobat as default app, all PDF files from the chat, channel, and files app open directly in the Adobe Acrobat app within Teams.

## Assign Adobe Acrobat app for all users

You can use the Global (Org-wide default) policy to assign and make the Adobe Acrobat app available for all users. To assign the Adobe Acrobat app for all users, follow these steps:

1. In Teams admin center, go to **Teams app** > [**Setup policies**](https://admin.teams.microsoft.com/policies/app-setup).

1. Under Manage policies, select **Global (Org-wide default)**, and then select **Edit**.

   :::image type="content" source="media/setup-policies.PNG" alt-text="setup-policies in Teams admin center":::

1. Select **Add apps**. A Add installed app pane appears.

1. Search **Adobe Acrobat** and select the app and select **Add**.

1. Select **Save**.

   :::image type="content" source="media/add-adobe-acrobat-app.PNG" alt-text="add app in teams admin center":::

> [!NOTE]
>
> * After the policy is setup, it typically takes few hours for users to view the app.
> * Currently, Adobe Acrobat doesn't allow users to pin PDF files as a tab on a channel.
> * PDF experience inside Assignments app will remain within Teams experience.
