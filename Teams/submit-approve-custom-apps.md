---
title: Use the Teams App Submission API to submit and approve your custom apps
author: cichur
ms.author: v-cichur
manager: serdars
ms.reviewer: joglocke, vaibhava
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
appliesto: 
- Microsoft Teams
f1.keywords:
- NOCSH
localization_priority: Normal
search.appverid: MET150
description: Learn how to approve your custom apps that are submitted using the Teams App Submission API in Microsoft Teams.
---

# Publish a custom app submitted through the Teams App Submission API

## Overview

> [!NOTE]
> When you publish a custom Teams app, it's available to users in your organization's app store. There are two ways to publish a custom app and the way that you use depends on how you get the app. **This article focuses on how to approve and publish a custom app that a developer submits through the Teams App Submission API**. The other method, uploading a custom app, is used when a developer sends you an app package in .zip format. To learn more about that method, see <a href="/microsoftteams/upload-custom-apps" target="_blank">Publish a custom app by uploading an app package</a>. The approve app widget isn't available in GCC tenants. 

> [!IMPORTANT]
> This method is not currently available for GCC environments. You must use the *uploading a custom app* method.

This article provides end-to-end guidance for how to take your Teams app from development to deployment to discovery. You'll get an overview of the connected experiences that Teams provides across the app lifecycle to streamline how to develop, deploy, and manage custom apps in your organization's app store.

We'll cover each step of the lifecycle, including how developers can use the Teams App Submission API to submit custom apps directly to the Microsoft Teams admin center for you to review and approve, how to set policies to manage apps for users in your organization, and how your users discover them in Teams.

![Overview of your app from development to deployment](media/custom-app-lifecycle.png)

This guidance focuses on the Teams aspects of the app and is intended for admins and IT pros. For information about developing Teams apps, see the <a href="/microsoftteams/platform" target="_blank">Teams developer documentation</a>.

## Develop

### Create the app

The Microsoft Teams developer platform makes it easy for developers to integrate your own apps and services to improve productivity, make decisions faster, and create collaboration around existing content and workflows. Apps built on the Teams platform are bridges between the Teams client and your services and workflows, bringing them directly into the context of your collaboration platform. For more information, go to the <a href="/microsoftteams/platform" target="_blank">Teams developer documentation</a>.

### Submit the app

When the app is ready for use in production, the developer can submit the app using the Teams App Submission API, which can be called from  [Graph API](/graph/api/teamsapp-publish?view=graph-rest-beta&tabs=http), an integrated development environment (IDE) such as Visual Studio Code, or a platform such as Power Apps and Power Virtual Agents. Doing this makes the app available on the <a href="/microsoftteams/manage-apps" target="_blank">Manage apps</a> page of the Microsoft Teams admin center, where you, the admin, can review and approve it.this

The Teams App Submission API, <a href="/graph/api/teamsapp-publish?tabs=http&view=graph-rest-beta#example-2-upload-a-new-application-for-review-to-an-organizations-app-catalog" target="_blank">built on Microsoft Graph</a>, allows your organization to develop on the platform of your choice and automates the submission-to-approval process for custom apps on Teams.

Here's an example of what this app submission step looks like in Visual Studio Code:

![submitting an app in Visual Studio Code](media/custom-app-lifecycle-submit-app.png)

Keep in mind that this doesn't publish the app to your organization's app store yet. This step submits the app to the Microsoft Teams admin center where you can approve it for publishing to your organization's app store.

For more information about using the Graph API to submit apps, see <a href="/graph/api/teamsapp-publish?tabs=http&view=graph-rest-beta#example-2-upload-a-new-application-for-review-to-an-organizations-app-catalog" target="_blank">here</a>.

## Validate

The <a href="/microsoftteams/manage-apps" target="_blank">Manage apps</a> page in the Microsoft Teams admin center (in the left navigation, go to **Teams apps** > **Manage apps**), gives you a view into all Teams apps for your organization. The **Pending approval** widget at the top of the page lets you know when a custom app is submitted for approval.

In the table, a newly submitted app automatically shows a **Publishing status** of **Submitted** and **Status** of **Blocked**. You can sort the **Publishing status** column in descending order to quickly find the app.

![publishing status ](media/custom-app-lifecycle-validate-app.png)

Click the app name to go to the app details page. On the **About** tab, you can view details about the app, including description, status, submitter, and app ID.

![app details page for a submitted app](media/custom-app-lifecycle-app-details.png)

For more information about using the Graph API to check the **Publishing status**, see <a href="/graph/api/appcatalogs-list-teamsapps?tabs=http&view=graph-rest-beta#example-3-find-application-based-on-the-teams-app-manifest-id" target="_blank">here</a>.

## Publish

When you're ready to make the app available to users, publish the app.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. Click the app name to go to the app details page, and then in the **Publishing status** box, select **Publish**.

    After you publish the app, the **Publishing status** changes to **Published** and the **Status** automatically changes to **Allowed**.

## Set up and manage

### Control access to the app

By default, all users in your organization can access the app in your organization's app store. To restrict and control who has permission to use the app, you can create and assign an app permission policy. To learn more, see <a href="/microsoftteams/teams-app-permission-policies" target="_blank">Manage app permission policies in Teams</a>.

### Pin and install the app for users to discover

By default, for users to find the app they have to go to your organization's app store and browse or search for it. To make it easy for users to get to the app, you can pin the app to the app bar in Teams. To do this, create an app setup policy and assign it to users. To learn more, see <a href="/microsoftteams/teams-app-setup-policies" target="_blank">Manage app setup policies in Teams</a>.

### Search the audit log for Teams app events

You can search the audit log to view Teams apps activity in your organization. To learn more about how to search the audit log and to see a list of Teams activities that are logged in the audit log, see <a href="/microsoftteams/audit-log-events" target="_blank">Search the audit log for events in Teams</a>.

Before you can search the audit log, you have to first turn on auditing in the <a href="https://protection.office.com" target="_blank">Security & Compliance Center</a>. To learn more, see <a href="https://support.office.com/article/Turn-Office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014" target="_blank">Turn audit log search on or off</a>. Keep in mind that audit data is only available from the point at which you turned on auditing.

## Discover and adopt

Users who have permissions to the app can find it in your organization's app store. Go to **Built for *Your Organization Name*** on the Apps page to find your organization's custom apps.

![Apps page showing published app ](media/custom-app-lifecycle-discovery.png)

If you created and assigned an app setup policy, the app is pinned to the app bar in Teams for easy access for those users who were assigned the policy.

## Update

To update an app, developers should continue to follow the steps in the [Develop](#develop) section.

When the developer submits an update to a published custom app, you'll get notified in the **Pending approval** widget of the <a href="/microsoftteams/manage-apps" target="_blank">Manage apps</a> page. In the table, the **Publishing status** of the app will be set to **Update submitted**.

![Manage apps page showing pending requests and app status ](media/custom-app-lifecycle-update-submitted.png)

To review and publish an app update:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. Click the app name to go to the app details page, and then select **Update available** to review details of the update.

    ![app details page](media/custom-app-lifecycle-update-app.png)
3. When you're ready, select **Publish** to publish the update. Doing this replaces the existing app, updates the version number, and changes the **Publishing status** to **Published**. All app permission policies and app setup policies remain enforced for the updated app.

    If you reject the update, the earlier version of the app remains published.

Keep in mind the following:

- When an app is approved, any one can submit an update to the app. This means other developers, including the developer who originally submitted the app, can submit an update to the app.
- When a developer submits an app and the request is pending, only that same developer can submit an update to the app. Other developers can submit an update only after the app is approved.

For more information about using the Graph API to update apps, see <a href="/graph/api/teamsapp-update?view=graph-rest-beta#example-2-update-a-previously-reviewed-and-published-application-to-the-teams-app-catalog" target="_blank">here</a>.

## Related topics

- [Publish a custom app by uploading an app package](upload-custom-apps.md)
- [Manage your apps in the Microsoft Teams admin center](manage-apps.md)
- [Manage custom app policies and settings in Teams](teams-custom-app-policies-and-settings.md)
- [Manage app permission policies in Teams](teams-app-permission-policies.md)
- [Manage app setup policies in Teams](teams-app-setup-policies.md)
- <a href="/graph/api/resources/teamsapp?view=graph-rest-beta" target="_blank">Microsoft Graph API for Teams apps</a>