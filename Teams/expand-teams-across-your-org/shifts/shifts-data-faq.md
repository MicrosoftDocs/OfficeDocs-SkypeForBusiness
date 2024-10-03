---
title: Shifts data FAQ
author: lana-chin
ms.author: v-chinlana
manager: jtremper
ms.topic: conceptual
ms.reviewer: harrywong
audience: admin
ms.service: msteams
search.appverid: MET150
searchScope: 
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
description: Get answers to frequently asked questions about Shifts data, including data storage location, security and compliance, and access control.
f1.keywords: 
  - NOCSH
ms.localizationpriority: Medium
ms.collection: 
  - M365-collaboration
  - microsoftcloud-healthcare
  - m365-frontline
  - teams-1p-app-admin
  - highpri
appliesto: 
  - Microsoft Teams
  - Microsoft 365 for frontline workers
ms.custom: seo-marvel-mar2020
ms.date: 03/25/2024
---

# Shifts data FAQ

This article covers frequently asked questions about Shifts data.

## Data storage location

### Where is Shifts data stored?

Upon setting up Teams, a country/region is chosen at the subscription level. Shifts honors this selection and Shifts data is stored in the corresponding country/region specified for Teams. If the country/region specified for Teams isn't supported in Shifts, we ensure that data is stored in a nearby supported region.

Shifts data is stored in one of the following region geographies (geos): Asia Pacific (APAC), European Union (EU), or United States. Within the supported geo, your Shifts data is stored in two Azure data centers for High Availability (HA) and Disaster Recovery (DR) purposes.

Additionally, Shifts offers data residency locally in Australia, Canada, France, Japan, and the United Kingdom.

Examples:

- For a Microsoft 365 tenant whose country/region is set to France, Shifts customer data is provisioned in France because Shifts supports data residency locally in France.
- For a Microsoft 365 tenant whose country/region is set to Sweden, Shifts customer data is provisioned within the EU geo because Shifts doesn't support data residency locally in Sweden.

To see where your Teams data is stored, in the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal/), go to **Settings** > **Org settings**, choose the **Organization profile** tab, and then choose **Data location**.

To learn more, see [Location of data in Microsoft Teams](../../privacy/location-of-data-in-teams.md) and [Data residency in Teams](/microsoft-365/enterprise/m365-dr-workload-teams).

> [!IMPORTANT]
> Migration of existing data, if stored in a nearby region, to the region provisioned in Teams is possible. However, Shifts data is only migrated when a signal is received from the Teams side. To learn more, see [Advanced data residency in Microsoft 365](/microsoft-365/enterprise/advanced-data-residency).

### Can Shifts data be moved in a tenant-to-tenant migration?

To migrate your existing Shifts data to another tenant, you need to export Shifts schedules for a date range, modify usernames (if necessary), and then import the schedules to the destination tenant. You can export up to 100 days of Shifts data at a time. The date range can be in the past or future. If you need to export data for a longer timeframe than 100 days, repeat the process.

Before you migrate your Shifts data, make sure the following requirements are met:

- The destination tenant domain, teams, and team members must already exist. The migration doesn't create teams or change team membership or ownership.
- The Shifts app must be set up in teams in the destination tenant and have an empty schedule. Keep in mind that the migration doesn't replace or delete existing data. This means that if a team has an existing schedule, users might see duplicate or conflicting shifts, which need to be manually resolved.
- Open requests (such as swap and time off requests) that are pending approval aren't migrated. We recommend closing any open requests before you start migrating data.

Here's an overview of the steps to migrate your Shifts data to another tenant.

1. In the source tenant, for each team, export the Shifts schedule:
    1. In Shifts, on the **Schedule** page, go to **More options (...)** > **Export schedule**.
    1. Select a date range.
    1. Turn on **Export in a format that can be imported**, and then select **Export**. Shifts schedule data is exported to an Excel file.
1. As part of the migration, if any team members are switching their email domain, manually update the Excel file to change the user principal name (UPN) of those users to the destination tenant domain.
1. In the destination tenant, import the schedule to each team.
    1. In Shifts, on the **Schedule** page, go to **More options (...)** > **Import schedule**.
    1. Select **Upload file**, go to the Excel file for that team, and then select **Open**.

## Data security and compliance

### Shifts and Microsoft Purview solutions

Currently, Shifts supports Microsoft 365 audit logs for Shifts events. Shifts doesn’t yet support data retention policies and/or content search for eDiscovery.

To learn more about the events that are logged for Shifts activities in the Microsoft 365 audit log, see [Teams Shifts activities](/purview/audit-log-activities#microsoft-teams-shifts-activities).

### What type of encryption does Shifts use for data at rest and in transit?

Shifts data is encrypted at rest by Azure Cosmos DB and Azure Storage. To learn more, see [Azure Data Encryption at rest](/azure/security/fundamentals/encryption-atrest) and
[Data encryption in Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest).

Shifts follows Microsoft 365 guidelines for encryption of data in transit. To learn more, see [Encryption for data-in-transit](/compliance/assurance/assurance-encryption-in-transit).

Shifts encryption of data at rest and in transit are verified yearly by the SOC2 compliance audit.

### Can I access immutable copies of Shifts data?

We don't store immutable copies of Shifts data. For example, a frontline manager can make changes to a schedule, such as add notes, change shift times, assign tasks, and so on, at any point in time.

### Can Shifts data be edited and/or permanently deleted?

#### Editing Shifts data

Generally, Shifts data can be edited at any point in time. For example, a frontline manager can always edit the details of a shift assigned to a worker, such as notes, unpaid break, and hours. However, shift requests can't be edited.

#### Permanent deletion of Shifts data

This capability isn't natively supported in the Shifts app. The two exceptions are if you delete your tenant or delete a team in Teams that has a Shifts schedule associated with it.

- If you delete your tenant, Shifts data is permanently deleted after the retention period ends. To learn more, see [Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).
- If you delete a team in Teams, Shifts data associated with that team is permanently deleted after the retention period ends. If you restore your team before the retention period ends, you can still restore the schedule in Shifts. To learn more, see [Restore a deleted Microsoft 365 group](/microsoft-365/admin/create-groups/restore-deleted-group) and [Manage teams in the Teams admin center](../../manage-teams-in-modern-portal.md#restore-deleted-teams).

Although we don't support this natively, it's possible to use [Shifts Graph APIs](/graph/api/resources/shift) to [create an app using Power Apps](/powerapps/maker/) to retain data only for a specified period of time.

> [!IMPORTANT]
> Turning off Shifts in your organization *does not* delete data. If you turn off Shifts, and then later turn on Shifts, your Shifts data is still available.

## Data access control

### Can I access and export or delete a user's personal data in Shifts?

Shifts is General Data Protection Regulation (GDPR) compliant. A formal request by a person (known as a data subject) to take an action on their personal data is called a Data Subject Request (DSR). You can find and act on personal data in Shifts in response to a DSR. To learn more, see [Office 365 Data Subject Requests for the GDPR and CCPA](/microsoft-365/compliance/gdpr-dsr-office365).

You can use export Shifts schedule and time clock data to Excel in the Shifts app. To learn more, see [Export Shifts schedule data](https://support.microsoft.com/office/export-shifts-schedule-data-8e604434-de77-4aae-8e87-561eaab902cf) and [Export time reporting in Shifts](https://support.microsoft.com/office/export-time-reporting-in-shifts-c3b06e42-3ad2-4b88-87a0-4e481d432110).

You can also manually delete schedule data in Shifts by either selecting individual or multiple shifts, using a right-click, long press, or other method to bring up the shortcut menu, and selecting **Delete** on that menu.

### Can I recover a Shifts schedule that was deleted?

You can recover a deleted schedule if the Microsoft 365 group that backs it or the team in Teams is restored within the retention period. To learn more, see [Restore a deleted Microsoft 365 group](/microsoft-365/admin/create-groups/restore-deleted-group?tabs=admin-center).

We advise customers to use the [export Shifts schedule data capability](https://support.microsoft.com/office/export-shifts-schedule-data-8e604434-de77-4aae-8e87-561eaab902cf) in Shifts to periodically back up data for safeguarding in case of restoration issues.

If a team was restored within the retention period timeframe, Shifts users on mobile devices might experience some issues when viewing their schedule data if their Teams app version is earlier than 1416/1.0.0.2024042104 (2024042140). In this scenario, users should sign out of Teams, and then sign in again.  

If for some reason, the issues persist, follow these steps.

**On Android devices:**

1. In Teams, tap your profile picture, select **Settings**, and then choose **Shifts**.
1. Tap **Clear Shifts app data**.

**On iOS devices:**

1. In Teams, tap your profile picture, select **Settings**, and then choose **Shifts**.
1. Tap **Clear Shifts app data**.
1. Open the Shifts app, go to the team that was restored, tap **Teams shifts** or **Your shifts**, and then pull down the page to refresh it.

### Can I retrieve Shifts data for a user whose license was revoked?

Today, we don't offer the ability to retrieve data for a user whose license was revoked. This capability is something we're working towards.

### My organization uses a workforce management system for scheduling. Can we integrate with and access Shifts data?

Shifts Graph APIs let you integrate Shifts data with external workforce management (WFM) systems. To learn more, see [Shifts Graph APIs](/graph/api/resources/shift).

We also offer managed Shifts connectors. With these connectors, you can integrate your WFM system directly with Shifts. To learn more about Shifts connectors and supported WFM systems, see [Shifts connectors](/microsoft-365/frontline/shifts-connectors).

## Related articles

- [Shifts for Teams](../shifts-for-teams-landing-page.md)
- [Manage the Shifts app](manage-the-shifts-app-for-your-organization-in-teams.md)
