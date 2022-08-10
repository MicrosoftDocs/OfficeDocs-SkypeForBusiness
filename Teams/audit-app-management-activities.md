---
title: Search the audit logs for app management events
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
search.appverid: MET150
f1keywords: 
description: Learn how to audit Teams app activities of users and administrators in your organization.
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
---

# Audit for app management activities and events

Microsoft Purview Audit (Standard) in Microsoft 365 lets you search for audit records of activities performed in the various Microsoft 365 services by end-users and administrators.

Before you can search the audit, ensure you complete the following pre-requisites:

* [Obtain organization subscription and user licensing](/microsoft-365/compliance/set-up-basic-audit).
* [Turn on auditing in the Microsoft Purview compliance portal](/microsoft-365/compliance/turn-audit-log-search-on-or-off).
* [Assign permissions to search the audit log](/microsoft-365/compliance/set-up-basic-audit).

## Search the audit logs for app events in Teams

The audit logs for app events in Teams help you investigate specific actions. While you can search the logs for a wide-range of actions, the following table lists some of the Teams app actions that are logged. In addition, you can search activities related to Connectors, bots, tabs, and so on.

| Teams app action                  | Activity name                | Description                                              |
|-----------------------------------|------------------------------|:---------------------------------------------------------|
| **Installed app**                 | `AppInstalled`               | An app is installed.                                     |
| **Upgraded app**                  | `AppUpgraded`                | An app is upgraded to its latest version in the catalog. |
| **Uninstalled app**               | `AppUninstalled`             | An app is uninstalled.                                   |
| **Published app**                 | `AppPublishedToCatalog`      | An app is added to the catalog.                          |
| **Updated app**                   | `AppUpdatedInCatalog`        | An app is updated in the catalog.                        |
| **Deleted app**                   | `AppDeletedFromCatalog`      | An app is deleted from the catalog.                      |
| **Deleted all organization apps** | `DeletedAllOrganizationApps` | Deleted all organization apps from the catalog.          |

For a complete list of Teams activities that are audited, see [Teams activities](audit-log-events.md#teams-activities) and [Shifts in Teams activities](audit-log-events.md#shifts-in-teams-activities).

> [!NOTE]
> App events from private channels are also logged as those events are for Teams and standard channels.

Use the Audit log search tool in the compliance portal to search for audit records. To search for app event audit logs, follow these steps:

1. Sign in to Microsoft Purview compliance portal and go to **Solutions** > **[Audit](https://compliance.microsoft.com/auditlogsearch)**.
1. On the audit page, update the following fields as per your requirement:

   * **Date and time range**: Select the Start and End date.
   * **Activities**: Enter Microsoft Teams activities. From the list, select one or more app activities. To quickly find the Teams activities, you can search for the word `Teams activities` in the **Activities** search field.
   * **File, folder, or site**: Enter file name or a URL or a part of it.
   * **Users**: Add the users whose audit log you want to search.

1. Select **Search**.

   :::image type="content" source="media/compliance-search-teams-activities-trimmed.png" alt-text="Search for Teams activities in the Microsoft Purview compliance portal to audit for Teams events." lightbox="media/compliance-search-teams-activities.png":::

After searching the audit sign in the compliance portal, you can export the audit records as a CSV file. For more information, see [Export, configure, and view audit logs](/microsoft-365/compliance/export-view-audit-log-records).

> [!NOTE]
> When one of the above activities is performed by a user or admin, Teams generates and stores an audit record. In Audit (Standard), records are retained for 90 days, which means you can search for activities that occurred within the past three months.

## Related articles

* [Use audit logs to investigate Microsoft Power Platform installation activity](manage-power-platform-apps.md#use-audit-logs-to-investigate-microsoft-power-platform-installation-activity)
* [Search the audit sign in the compliance portal](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance).
* [Overview of Microsoft Purview Audit Premium](/microsoft-365/compliance/advanced-audit).
* [Turn auditing on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off).
