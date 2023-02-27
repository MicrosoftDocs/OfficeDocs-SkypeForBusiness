---
title: Search the audit logs for app management events
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
ms.subservice: teams-apps
audience: admin
ms.date: 02/23/2023
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

Microsoft Purview Audit (Standard) in Microsoft 365 lets you search for audit records of activities performed in the various Microsoft 365 services by end-users and administrators.

Before you can search the audit records, ensure that you complete the following prerequisites:

* [Obtain organization's subscription and user licensing](/microsoft-365/compliance/set-up-basic-audit).
* [Turn on auditing in the Microsoft Purview compliance portal](/microsoft-365/compliance/turn-audit-log-search-on-or-off).
* [Assign permissions to search the audit log](/microsoft-365/compliance/set-up-basic-audit).

## Search the audit logs for app events in Teams

The audit logs for app events in Teams help you investigate specific actions related to app management by admins. While you can search the logs for a wide-range of actions, the following table lists some such actions that are logged.

| Teams app action | Activity name in the Portal | Description  |
|-------|-------|:-------|
| **Installed app**                 | `AppInstalled`               | An app is installed or added to a Teams client. |
| **Upgraded app**                  | `AppUpgraded`                | An app is upgraded to its latest version in the catalog. |
| **Uninstalled app**               | `AppUninstalled`             | An app is uninstalled or removed from a Teams client.                                   |
| **Published app**                 | `AppPublishedToCatalog`      | An app is added to the catalog.                          |
| **Updated app**                   | `AppUpdatedInCatalog`        | An app is updated in the catalog.                        |
| **Deleted app**                   | `AppDeletedFromCatalog`      | An app is deleted from the catalog.                      |
| **Deleted all organization apps** | `DeletedAllOrganizationApps` | Deleted all organization apps from the catalog.          |

<!--- organization apps = custom or 3p --->

For a complete list of Teams activities that are audited, see [Teams activities](audit-log-events.md#teams-activities) and [Shifts in Teams activities](audit-log-events.md#shifts-in-teams-activities).

> [!NOTE]
> App events from private channels are also logged as those events are accomplished in Teams and in the standard channels.

To search the audit logs of Teams app activities, follow these steps:

1. Sign in to Microsoft Purview compliance portal and go to **Solutions** > **[Audit](https://compliance.microsoft.com/auditlogsearch)**.
1. On the **Audit** page, update the following fields as required:

   * **Date and time range**: Select the start and end dates of the time period for which you want to check the audit logs.
   * **Activities**: Enter Microsoft Teams activities. From the list, select one or more app activities. To quickly find the Teams activities, you can search for the word `Teams activities` in the **Activities** search field.
   * **File, folder, or site**: Enter file name or a URL or a part of it.
   * **Users**: Add the users whose audit log you want to search.

1. Select **Search**.

   :::image type="content" source="media/compliance-search-teams-activities-trimmed.png" alt-text="Search for Teams activities in the Microsoft Purview compliance portal to audit for Teams events." lightbox="media/compliance-search-teams-activities.png":::

You can export the searched audit records as a CSV file. For more information, see [Export, configure, and view audit logs](/microsoft-365/compliance/export-view-audit-log-records).

> [!NOTE]
> When one of the above activities is performed by a user or admin, Teams generates and stores an audit record. In Audit (Standard), records are retained for 90 days, which means you can search for activities that occurred within the past three months.

> [!TIP]
> As an admin, if you want to create a per-user report to know if a user has blocked or muted a bot, see [Understand who blocked, muted or uninstalled a bot](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?#understand-who-blocked-muted-or-uninstalled-a-bot).

## Related articles

* [Use audit logs to investigate Microsoft Power Platform installation activity](manage-power-platform-apps.md#use-audit-logs-to-check-microsoft-power-platform-installation-activity).
* [Search the audit sign in the compliance portal](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance).
* [Overview of Microsoft Purview Audit Premium](/microsoft-365/compliance/advanced-audit).
* [Turn auditing on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off).
