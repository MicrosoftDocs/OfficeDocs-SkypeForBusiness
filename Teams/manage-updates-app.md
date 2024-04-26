---
title: Manage the Updates app for your organization
author: lana-chin
ms.author: v-chinlana
manager: jtremper
ms.reviewer: diyu
ms.date: 02/01/2024
ms.topic: how-to
audience: admin
ms.service: msteams
search.appverid: MET150
searchScope:
  - Microsoft Teams
description: Learn how to manage the Updates app in Teams for users in your organization.
f1.keywords:
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - m365-frontline
  - teams-1p-app-admin
  - highpri
appliesto: 
  - Microsoft Teams
ms.custom: 
---

# Manage the Updates app for your organization in Microsoft Teams

## Overview of Updates

The Updates app in Microsoft Teams provides a centralized place for members of your organization to create, review, and submit updates. By creating update requests, you can use the Updates app to keep track of anything your organization needs. Updates is available for both desktop and mobile.

In Teams, users can get the Updates app from the Teams app store. They'll see all of the update requests they need to submit on the **Submit** page. You can share the [Get started in Updates article](https://support.microsoft.com/office/get-started-in-updates-c03a079e-e660-42dc-817b-ca4cfd602e5a) with your users to help them get comfortable using Updates.

[![Image of the Submit page in Teams for desktop.](media/updates-submit-small.png)](media/updates-submit.png#lightbox)

Users can view updates that they assigned on the **Review** page.

[![Image of the Review page in Teams for desktop.](media/updates-home-small.png)](media/updates-home.png#lightbox)

When a user is assigned an update request, it shows up in their Teams activity feed. Users can also view all their current update requests and previous submissions in the Updates app. In addition, anyone can create and send out update requests.

Updates comes with both out-of-the-box templates for common business scenarios and the option to create your own requests. Anyone can create an update request for new types of updates and ask others to submit updates to sync their work status.

## Example scenario

Employees at a clothing store are responsible for opening and closing the store every day. Every morning, the shift leader fills out the Store opening update. In this update, they describe any issues with the previous night's closing, answer questions about the cleanliness of the store, and report any supplies that need replenished. Submitting an update lets them communicate their needs for the store and any problems quickly and efficiently. Daily updates also give the store associates an opportunity to highlight what's going well.

At the store's manufacturing facilities, employees perform safety checks with Updates using mobile devices.

![Image of the Weekly safety walkthrough template on a mobile device.](media/updates-mobile.png)

Meanwhile, a team of remote workers is updating the store's website. They're spread across time zones, so daily stand-up meetings aren't convenient. Instead, each of the team members submits daily Updates reports on their progress to the team leader.

[Download the Updates lookbook](https://go.microsoft.com/fwlink/?linkid=2197649) to see more examples of what you can do with Updates.

## Required permissions and licenses

You need permission for the following items to deploy Updates:

- Permissions to create a Microsoft Dataverse database.

- An account on [powerautomate.microsoft.com](https://powerautomate.microsoft.com/).

- Administrator role in your target environment.

- License for Power Automate, Office 365, or Dynamics 365.

## Storage with Microsoft Dataverse

The Common Data Model (CDM) is the shared data language used by business and analytical applications in the Microsoft Dataverse. It consists of a set of standardized, extensible data schemas published by Microsoft and our partners that enables consistency of data and its meaning across applications and business processes. Learn more about the [Common Data Model](/common-data-model/).

Updates that are created from a template still store data in Microsoft Dataverse, such as their title, details, template ID, and more.

## Updates Teams app permissions

The Updates Teams app lets you access the following features:

- Receive messages and data that you provide to it.

- Send you messages and notifications.

- Render personal apps and dialogs without a Teams-provided header.

- Access your profile information such as your name, email address, company name, and preferred language.

- Receive messages and data that team members provide to it in a channel.

- Send messages and notifications in a channel.

- Access your team's information:
  - Team name
  - Channel list
  - Roster (team members' names and email addresses)

- Use the team's information to contact them.

## Disable the Updates app

The Updates app is available by default. You can disable the app in the Teams admin center.

  1. Sign in to the Teams admin center.

  2. Go to **Teams apps** > **Manage apps**.

  3. Search for the Updates app.

     [![Screenshot of the Admin center navigation with Teams Apps > Manage Apps highlighted.](media/manage-updates-small.png)](media/manage-updates.png#lightbox)

  4. Select **Updates**.

  5. Select the toggle to disable the app for your organization.
    [![Image of the toggle to enable or disable Updates.](media/toggle-updates.png)](media/toggle-updates.png#lightbox)

## Pin Updates to Teams

App setup policies let you customize Teams to pin apps that are most important for your users in your users. The apps are pinned to the app bar—the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients—where users can quickly and easily access them.

To pin the Updates app for your users, you can edit the global (Org-wide default) policy or create and assign a custom policy in app setup policy. Learn more about [Teams app setup policies](teams-app-setup-policies.md).

## Retention policy

Updates created from the Updates app are stored in the default Microsoft Dataverse environment, which doesn’t support backups at this time. Learn more about how to [back up and restore environments](/power-platform/admin/backup-restore-environments).

## Conditional access and permission policies

The Updates app in Teams doesn't currently support Conditional Access policies that are set for Microsoft Teams.

You can use [Teams app permission policies](teams-app-permission-policies.md) to manage Updates.

## Security

From the Teams Updates app, users have access to create new updates and view updates that they sent and received. Users can't view the Updates that are submitted by others unless they're a viewer of the update or update request.

## Power Automate connector

Updates support the Power Automate connector **Updates App(Microsoft 365)**. Using this connector can help you automate your organization's workflow. [Learn more](https://powerautomate.microsoft.com/blog/automate-workflows-with-power-automate-connector-for-updates-in-microsoft-teams/).

## Give feedback or report an issue

To send feedback or report an issue, select **Settings and more** (**…**) in Teams, and then choose **Help** > **Give feedback**. Enter your feedback or details about the issue you're experiencing. Indicate at the beginning of your feedback report that you're sending feedback about Updates so we can easily identify Updates issues.
