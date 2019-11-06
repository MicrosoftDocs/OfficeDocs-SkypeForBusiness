---
title: Publish apps in the Microsoft Teams Tenant Apps Catalog
author: lolajacobsen
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: prem
audience: admin
description: Guidance for publishing apps in the Microsoft Teams Tenant Apps Catalog.
localization_priority: Normal
search.appverid: MET150
f1keywords: 
  - ms.teamsadmincenter.apppermspolicies.publishtenantapps
  - ms.teamsadmincenter.apppolicies.publishtenantapps
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

Publish apps in the Microsoft Teams tenant apps catalog
=======================================================

You can use the Microsoft Teams tenant apps catalog to test and distribute line-of-business applications to your organization.

The Teams tenant apps catalog lets you distribute line-of-business applications that were built specifically for your organization and that you rely on to complete critical business functions.

To publish apps for your organization, sign in to the Teams client using an account with the global admin or teams service admin roles and then follow the steps below.


## Publish an app in the tenant apps catalog from the Teams client

> [!NOTE]
> You need to be signed in to Teams an account that has either the global admin or teams service admin role enabled to publish apps for your organization. Learn more about [using administrator roles to manage Teams](https://docs.microsoft.com/MicrosoftTeams/using-admin-roles).

> [!NOTE]
> These steps describe how to publish an app by using the Teams client. You can also publish an app on the Manage apps page in the Microsoft Teams admin center. To learn more, see TBD.

### Get a Teams app package

A Teams app package is created by using [Teams App Studio](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio). Once you have the app package, you can add it to the tenant app catalog. While all users in your organization can view the app catalog, only global admins and teams service admins have the ability to publish and manage it.

### Go to the tenant apps catalog

Start Teams and sign in using your global or teams service admin credentials. From the Teams store, select the new section named for your specific organization (in this example, Contoso). Users in your organization can view apps in the catalog and install them for teams of which they are a member.

![Screenshot of the Teams App Store showing the app catalog.](media/private-app-store-teams-image01.png)

### Add an app to the tenant apps catalog

1. From the store, select **Upload a custom app** > **Upload for Contoso**.

    ![Screenshot of the Teams App Store showing the app catalog.](media/private-app-store-teams-image02.png)

    (You can also choose **Upload for me or my teams**, which is called *sideloading*. Sideloading makes the app available only to your teams or to teams you select.)

2. Navigate to the app package and select it, and then click **Open**.

    ![Screenshot of the Teams App Store showing the app catalog.](media/private-app-store-teams-image03.png)

When you go back to your tenant apps catalog, the new enterprise app will be there. Remember, only you and members of your organization have access to this app catalog.

### Update an app in the tenant apps catalog

1. From your tenant apps catalog, select “**…**” on the top right of the app you want to update.

2. Navigate to the updated app package and select it, and then click **Open**.

    ![Screenshot of the Teams App Store showing the app catalog.](media/private-app-store-teams-image04.png)

The app will be revised to version 2.0. You can also delete the app for your entire company from this menu.