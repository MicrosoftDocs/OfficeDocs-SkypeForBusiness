---
title: Shifts data FAQ
author: lanachin
ms.author: v-lanachin
ms.reviewer: aaku
manager: samanro
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
searchScope:
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
description:  
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

# Shifts data FAQ

## Overview


## Where is Shifts data stored

Shifts data is stored in data centers in the United States, European Union, and Asia Pacific. Each geo stores data in at least two Azure data center regions for HA/DR.??? Today, the United States geo uses data centers in North Central and South Central United States. To learn more, see [Where is Microsoft 365 customer data stored](/microsoft-365/enterprise/o365-data-locations).

Currently, Shifts offers data residency in Australia, Canada, France, Japan, and the United Kingdom. We're actively working to expand support to additional locations.

## Can I choose where Shifts data is stored

When you first set up Teams, you choose a country or region, which is set at the subscription level. Shifts honors this selection and uses the locale and region that's set in Teams if we support that region. If we aren't yet in that region, we store data in a nearby region that we support. In the future, we plan to migrate existing data, if stored in a nearby region, to the region that's provisioned in Teams.

## GDPR


## Can I recover a Shifts schedule that was deleted?

You can recover a deleted Shifts if the Microsoft 365 group that backs it (or the team in Teams) is restored.

By default, a deleted Microsoft 365 group is retained for 30 days. This 30-day period is called "soft-delete" because you can restore the group. To learn more, see [Restore a deleted Microsoft 365 group](/microsoft-365/admin/create-groups/restore-deleted-group?view=o365-worldwide&tabs=admin-center).

## Can I use custom retention policies for Shifts data?

Currently, Shifts doesn't support custom retention policies.

To learn more about retention policies in Teams, see [Learn about retention for Teams](/microsoft-365/compliance/retention-policies-teams) and [Manage retention policies for Teams](../../retention-policies.md).

## Can I retrieve Shifts data for a user whose license was revoked?

Today, we don't offer the ability to retrieve data for a user whose license was revoked. This capability is something we're working towards.

For specific customer escalation scenarios, we're able to provide access.

## Which tier of compliance is Shifts?

Today, Shifts is Tier-C compliant. We're working towards Tier-D compliance.

## What type of encryption does Shifts use for data at rest and in transit?

Shifts data is encrypted at rest by Azure Cosmos DB and Azure Storage. To learn more, see [Azure data encryption at rest](/azure/security/fundamentals/encryption-atrest) and
[Data encryption in Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest).

Shifts follows Microsoft 365 guidelines for encryption of data in transit. To learn more, see [Encryption for data-in-transit](/compliance/assurance/assurance-encryption-in-transit).

Shifts encryption of data at rest and in transit are verified yearly by the SOC2 compliance audit.

## Can I access immutable copies of Shifts data

We don't store immutable copies of Shifts data. For example, a manager can make changes to the schedule, such as add notes, change shift times, assign tasks, and so on. 

## Data retrieval

### Graph API

### Ability to edit

There are certain aspects of Shifts that can't be changed and certain aspects that can be changed. For example, Shifts details such as notes or colors can be edited similar to how they are in the Shifts app. Shifts requests can't be edited. \

To see which field have been changed, you an search the Microsoft 365 audit log for Shifts events. 

To learn more about the events that are logged for Shifts activities in Teams in the Microsoft 365 audit log, see [Shifts in Teams activities](../../audit-log-events.md#shifts-in-teams-activities).

## What happens to Shifts data if I turn off Shifts for my organization

Turning off Shifts in your organization does not delete data. If you turn off Shifts, and then later turn on Shifts, your Shifts data will still be available.

If you delete your tenant, all Shifts data is deleted after the retention period ends.

There's no option to delete only Shifts data. If you delete a team in Teams, Shifts schedule data that's associated with that team is deleted after the retention period ends. To learn more, see [Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

## Can Shifts data be moved in a tenant-to-tenant migration?

Shifts data can be migrated from one tenant to another by the Shifts service team upon specific request. For example, if you're consolidating tenants and want to move your Shifts data in one tenant to another tenant.

## Related articles
