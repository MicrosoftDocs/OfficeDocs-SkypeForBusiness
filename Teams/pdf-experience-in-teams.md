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

# Adobe acrobat PDF experinece in Teams

You can set Adobe Acrobat as the default app to view and edit PDF files in the Microsoft Teams by setting up a policy to install the app and giving required permissions to the app in the Teams admin center. 

Once the app is set as default, all PDF files from the chat, channel and files app will open directly in the Acrobat app within Teams. Your tenant users do not need an Adobe Acrobat subscription or an Adobe ID to view the PDFs, view bookmarks, search a PDF, or comment and annotate in PDFs. 

However, to Create, Organize, Combine, or Export a PDF, the tenant users will need an Adobe Acrobat subscription and an Adobe ID. 

To set Adobe Acrobat as default PDF handler, follow these steps: 

## Setup Adobe Acrobat app to work in the tenant

1. Log in to Teams admin center.  

1. In the left panel, go to Teams app and select **Manage apps**.  

1. Search for the Adobe Acrobat app and select the **Adobe Acrobat** app to go to the app details page.

1. On the Permissions tab, select **Review permission** requested by the app, then select Accept to grant consent.

## Make Adobe Acrobat app available on users’ Teams client

1. Log in to Teams admin center.  

1. In the left panel, go to Teams app and select **Setup policies**.  

1. Select **Global (Org-wide default)** and then select **Edit**. 

1. Select Add apps. 

1. Search Adobe Acrobat app, add it, and save the policy.
