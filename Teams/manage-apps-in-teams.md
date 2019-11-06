---
title: Manage apps in the Microsoft Teams admin center
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
Manage apps in the Microsoft Teams admin center
======================================================

The **Manage apps** page in the Teams admin center is where you (currently limited to Global Administrators or Teams Service Administrators) can view and manage all Teams apps in your organization's app catalog.

## View apps in your organization's app catalog

As an admin, you'll see every app available in your tenant app catalog on the **Teams apps** > **Manage apps** page. This app catalog gives you the information you need to decide which apps to allow or block for users in your organization.

{Screen Shot}

## Upload a new app

You can also upload new custom apps on the Manage apps page. Click **Upload new app** to upload your app manifest zip file. If the zip file isn't a valid Teams app manifest zip, the upload will fail.

You can still [upload apps in the Teams client](https://support.office.com/article/add-an-app-to-teams-b2217706-f7ed-4e64-8e96-c413afd02f77).

## View app certification information

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

## Manage org-wide app settings

Use org-wide app settings to control whether users can install third-party apps and whether users can upload or interact with custom (sideloaded) apps in your organization. Org-wide app settings govern the behavior for all users and override any other app permission policies assigned to users. You can use them to control malicious or problematic apps.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. Select **Org-wide settings**. You can then configure the settings you want in the panel. 
    ![Screenshot of org-wide app settings](media/app-permission-policies-org-wide-settings.png)
3. Under **Third-party apps**, turn off or turn on these settings to control access to third-party apps:

    - **Allow third-party apps in Teams**: This controls whether users can use third-party apps.
    - **Allow any new third-party apps published to the store by default**: This controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.

4. Under **Custom apps**, turn off or turn on **Allow interaction with custom apps**. This setting controls whether users can interact with custom (sideloaded) apps. Keep in mind that this is different from allowing users to *upload* custom apps.
5. Click **Save** for org-wide app settings to take effect.