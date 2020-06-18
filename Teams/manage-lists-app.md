---
title: Manage the Lists app for your organization
author: LanaChin
ms.author: v-lanac
ms.reviewer: anach,v-jasuk
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to set up and manage the Lists app in Teams for users in your organization.
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.custom: 
---

# Manage the Lists app for your organization in Microsoft Teams 

## Overview of the Lists app

The Shifts app in Microsoft Teams keeps Firstline Workers connected and in sync. It's built mobile first for fast and effective time management and communication for teams. Shifts lets Firstline Workers and their managers use their mobile devices to manage schedules and keep in touch.

- Managers create, update, and manage shift schedules for teams. They can send messages to one person ("there's a spill on the floor") or the entire team ("the regional GM is arriving in 20 minutes"). They can also send policy documents, news bulletins, and videos. 
- Employees view their upcoming shifts, can see who else is scheduled for the day, request to swap or offer a shift, and request time off. 

It's important to know that Shifts currently doesn't support guest users. This means that guests on a team can't be added to or use shift schedules when Guest access is turned on in Teams. 

## Availability of Lists

Shifts is available in all Enterprise SKUs where Teams is available.

## Location of Shifts data

Shifts data is currently stored in Azure in data centers in North America, Western Europe, and Asia Pacific. For more information about where data is stored, see [Where is my data](http://o365datacentermap.azurewebsites.net/)?

## Set up Lists

### Enable or disable Lists in your organization

Shifts is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](../../manage-apps.md) page in the Microsoft Teams admin center.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps** .
2. In the list of apps, do one of the following:

    - To turn off Shifts for your organization, search for the Shifts app, select it, and then click **Block**.
    - To turn on Shifts for your organization, search for the Shifts app, select it, and then click **Allow**.

### Enable or disable Lists for specific users in your organization

To allow or block specific users in your organization from using Shifts, make sure Shifts is turned on for your organization on the [Manage apps](../../manage-apps.md) page, and then create a custom app permission policy and assign it to those users. To learn more, see [Manage app permission policies in Teams](../../teams-app-permission-policies.md).

### Create an app setup policy to pin Lists to Teams

App setup policies let you customize Teams to highlight the apps that are most important for users in your organization. The apps set in a policy are pinned to the app bar&mdash;the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients&mdash;where users can quickly and easily access them. 

#### Assign the FirstlineWorker policy to users

To assign the FirstlineWorker app setup policy to one user:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click the user.
2. Select the user by clicking to the left of the user name, and then click **Edit settings**.
3. Under **App setup policy**, select **FirstlineWorker**, and then click **Apply**.

To assign a policy to multiple users at a time:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**, and then search for the users or filter the view to show the users you want.
2. In the **&#x2713;** (check mark) column, select the users. To select all users, click the &#x2713; (check mark) at the top of the table.
3. Click **Edit settings**, under **App setup policy**, select **FirstlineWorker**, and then click **Apply**.  

Or, you can also do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Setup policies**.
2. Select the FirstlineWorker policy by clicking to the left of the policy name.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.
5. After you finish adding users, select **Apply**.


## Search the audit log for Lists events

**(in preview)**

You can search the audit log to view Lists activity in your organization.  To learn more about how to search the audit log and to see a list of [Shifts activities](../../audit-log-events.md#shifts-in-teams-activities) that are logged in the audit log, see [Search the audit log for events in Teams](../../audit-log-events.md).

Before you can search the audit log, you have to first turn on auditing in the [Security & Compliance Center](https://protection.office.com). To learn more, see [Turn audit log search on or off](https://support.office.com/article/Turn-Office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014). Keep in mind that audit data is only available from the point at which you turned on auditing.

## Related topics

- [Assign policies to your users in Teams](../../assign-policies.md)
