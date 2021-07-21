---
title: Manage the Shifts app for your organization
author: cichur
ms.author: v-cichur
ms.reviewer: lisawu,gumariam
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
searchScope:
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
description: Learn how to set up and manage the Shifts app in Teams for frontline workers in your organization.
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
  - microsoftcloud-healthcare
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Manage the Shifts app for your organization in Microsoft Teams

> [!IMPORTANT]
> Effective June 30, 2020, Microsoft StaffHub has been retired. We're building StaffHub capabilities into Microsoft Teams. Today, Teams includes the Shifts app for schedule management and additional capabilities will roll out over time. StaffHub stopped working for all users on June 30, 2020. Anyone who tries to open StaffHub is shown a message directing them to download Teams. To learn more, see [Microsoft StaffHub has been retired](microsoft-staffhub-to-be-retired.md).  

## Overview of Shifts

The Shifts app in Microsoft Teams keeps frontline workers connected and in sync. It's built mobile first for fast and effective time management and communication for teams. Shifts lets frontline workers and their managers use their mobile devices to manage schedules and keep in touch.

- Managers create, update, and manage shift schedules for teams. They can send messages to one person ("there's a spill on the floor") or the entire team ("the regional GM is arriving in 20 minutes"). They can also send policy documents, news bulletins, and videos.
- Employees view their upcoming shifts, see who else is scheduled for the day, request to swap or offer a shift, and request time off.

It's important to know that Shifts currently doesn't support guest users. This means that guests on a team can't be added to or use shift schedules when Guest access is turned on in Teams. 

> [!Note]
> For details about Shifts capabilities on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

## Availability of Shifts

Shifts is available in all Enterprise SKUs where Teams is available.

## Location of Shifts data

Shifts data is currently stored in Azure in data centers in North America, Western Europe, and Asia Pacific. For more information about where data is stored, see [Where is my data](http://o365datacentermap.azurewebsites.net/)?

## Set up Shifts

### Enable or disable Shifts in your organization

Shifts is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](../../manage-apps.md) page in the Microsoft Teams admin center.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. In the list of apps, do one of the following actions:

    - To turn off Shifts for your organization, search for the Shifts app, select it, and then select **Block**.
    - To turn on Shifts for your organization, search for the Shifts app, select it, and then select **Allow**.

### Enable or disable Shifts for specific users in your organization

To allow or block specific users in your organization from using Shifts, make sure Shifts is turned on for your organization on the [Manage apps](../../manage-apps.md) page, and then create a custom app permission policy and assign it to those users. To learn more, see [Manage app permission policies in Teams](../../teams-app-permission-policies.md).

### Use the FirstLineWorker app setup policy to pin Shifts to Teams

App setup policies let you customize Teams to highlight the apps that are most important for users in your organization. The apps set in a policy are pinned to the app bar&mdash;the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients&mdash;where users can quickly and easily access them.
 
Teams includes a built-in FirstLineWorker app setup policy that you can assign to frontline workers in your organization. By default, the policy includes the Activity, Shifts, Chat, and Calling apps.

To view the FirstLineWorker policy, in the left navigation of the Microsoft Teams admin center, go to **Teams app** > **App setup policies**.

![Screenshot of the FirstLineWorker app setup policy](../../media/firstline-worker-app-setup-policy.png "Screenshot of the FirstLineWorker app setup policy in the Microsoft Teams admin center")

#### Assign the FirstLineWorker app setup policy to users

[!INCLUDE [assign-policy](../../includes/assign-policy.md)]

## Search the audit log for Shifts events

**(in preview)**

You can search the audit log to view Shifts activity in your organization.  To learn more about how to search the audit log and to see a list of [Shifts activities](../../audit-log-events.md#shifts-in-teams-activities) that are logged in the audit log, see [Search the audit log for events in Teams](../../audit-log-events.md).

Before you can search the audit log, you have to first turn on auditing in the [Security & Compliance Center](https://protection.office.com). To learn more, see [Turn audit log search on or off](https://support.office.com/article/Turn-Office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014). Keep in mind that audit data is only available from the point at which you turned on auditing.

## Related topics

- [Shifts Help for frontline workers](https://support.office.com/article/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b)
- [Assign policies to your users in Teams](../../assign-policies.md)
