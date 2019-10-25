---
title: Manage apps in the Teams admin center
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: rowille
search.appverid: MET150
f1keywords: 
- ms.teamsadmincenter.manageapps.overview
description: Manage your Microsoft Teams apps in the Teams admin center.
appliesto: 
- Microsoft Teams
localization_priority: Normal
---
Manage apps in the Teams admin center
======================================================

The **Manage apps** page in the Teams admin center is where admins (currently limited to Global Administrators or Teams Service Administrators) can view and manage all Teams apps in an organization's app catalog.

## App catalog view

As an admin, you'll see every app available in your tenant’s app catalog on the **Teams apps** > **Manage apps** page. This app catalog gives you the information you need to decide which apps to allow or block for users in your organization.

{Screen Shot}

## Upload new app
You can also upload new custom apps on the Manage apps page. Click **Upload new app** to upload your app manifest zip file. If the zip file isn't a valid Teams app manifest zip, the upload will fail.

You can still [upload apps in the Teams client](https://support.office.com/article/add-an-app-to-teams-b2217706-f7ed-4e64-8e96-c413afd02f77).


## App certification information

If an application has gone through certification, the **Certification** column will contain one of two indicators:

- Microsoft 365 certified
- Publisher attestation

Click these links to see the certification details for each app.

If you see "--" in the **Certification** column, we don't have certification information for that app. 

To learn more about certified apps in Teams, read [Microsoft Teams App Security and Compliance](https://docs.microsoft.com/teams-app-certification/all-apps).

## Allow and block apps

The **Manage apps** page is where you allow or block individual apps at the org-wide level. Previously, you did this by adding individual apps to the blocked list under **Org-wide settings**. Now, the **Manage apps** page shows every available app and its current org-wide app status.

To change the status of an app, select it and then click **Allow** or **Block**.

## Org-wide status override

You can still override ALL third-party apps in Teams in **Teams apps** > **Permission policies** > **Org-wide app settings**. If you turn off **Allow third party or custom apps**, your users won't be able to install or use any third-party apps. For apps that you've allowed on the **Manage apps** page, the status will be **Allowed but disabled org-wide**.

{Screen Shot}

