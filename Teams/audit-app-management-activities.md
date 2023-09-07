---
title: Search the audit logs of app management events
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
ms.subservice: teams-apps
audience: admin
ms.date: 08/06/2023
ms.collection: 
  - M365-collaboration
search.appverid: MET150
f1keywords: 
description: Learn how to audit Teams app activities of users and administrators in your organization.
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
---

# Search audit logs for app management activities and events

Microsoft Purview Audit (Standard) in Microsoft 365 lets you log and search the audited activities performed in the various Microsoft 365 services by users and administrators.

Before you can search the audit records, ensure that you complete the following prerequisites:

* [Obtain organization's subscription and user licensing](/purview/audit-standard-setup#step-1-verify-organization-subscription-and-user-licensing).
* [Turn on auditing in the Microsoft Purview](/purview/audit-log-enable-disable) portal.
* [Assign permissions to search the audit log](/purview/audit-standard-setup#step-2-assign-permissions-to-search-the-audit-log).

## Search the audit logs for app events in Teams

The audit logs for app events in Teams help you investigate specific actions related to app management by admins. While you can search the logs for a wide-range of actions, the following table lists some such actions that are logged.

| Teams app action                  | Activity name in the Portal  | Description                                              |
|-----------------------------------|------------------------------|:---------------------------------------------------------|
| **Installed app**                 | `AppInstalled`               | An app is installed or added to a Teams client.          |
| **Upgraded app**                  | `AppUpgraded`                | An app is upgraded to its latest version in the catalog. |
| **Uninstalled app**               | `AppUninstalled`             | An app is uninstalled or removed from a Teams client.    |
| **Published app**                 | `AppPublishedToCatalog`      | An app is added to the catalog.                          |
| **Updated app**                   | `AppUpdatedInCatalog`        | An app is updated in the catalog.                        |
| **Deleted app**                   | `AppDeletedFromCatalog`      | An app is deleted from the catalog.                      |
| **Deleted all organization apps** | `DeletedAllOrganizationApps` | Deleted all organization apps from the catalog.          |

For a complete list of Teams activities that are audited, see [Teams activities](audit-log-events.md#teams-activities) and [Shifts in Teams activities](audit-log-events.md#shifts-in-teams-activities).

> [!NOTE]
> App events from private channels are also logged as those events are accomplished in Teams and in the standard channels.

To search the audit logs of Teams app activities, follow these steps:

1. Sign in to Microsoft Purview and go to **Solutions** > **[Audit](https://compliance.microsoft.com/auditlogsearch)**.
1. On the **Audit** page, update the following fields as required:

   * **Date and time range**: Select the start and end dates of the time period for which you want to check the audit logs.
   * **Activities**: Enter Microsoft Teams activities. From the list, select one or more app activities. To quickly find the Teams activities, you can search for the word `Teams activities` in the **Activities** search field.
   * **File, folder, or site**: Enter file name or a URL or a part of it.
   * **Users**: Add the users whose audit log you want to search.

1. Select **Search**.

   :::image type="content" source="media/compliance-search-teams-activities-trimmed.png" alt-text="Screenshot that shows how to search for Teams activities in the Microsoft Purview to audit for Teams events." lightbox="media/compliance-search-teams-activities.png":::

You can export the searched audit records as a CSV file. For more information, see [Export, configure, and view audit logs](/purview/audit-log-export-records).

> [!NOTE]
> When one of the above activities is performed by a user or admin, Teams generates and stores an audit record. In Audit (Standard), records are retained for 90 days, which means you can search for activities that occurred within the past three months.

> [!TIP]
> You can commission the custom development of a per-user report to know if a user has blocked or muted a bot. For more information, see [Understand who blocked, muted or uninstalled a bot](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages#understand-who-blocked-muted-or-uninstalled-a-bot).

## Related articles

* [Use audit logs to investigate Microsoft Power Platform installation activity](manage-power-platform-apps.md#use-audit-logs-to-check-microsoft-power-platform-installation-activity).
* [Search the audit logs in Microsoft Purview](/purview/audit-log-search).
* [Overview of Microsoft Purview Audit Premium](/purview/audit-premium).
* [Turn auditing on or off](/purview/audit-log-enable-disable).
