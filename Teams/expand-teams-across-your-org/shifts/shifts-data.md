---
title: Location of data in the Shifts app
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

# Location of data in the Shifts app

## Overview


## Location of Shifts data

Shifts data is stored in data centers in the United States, European Union, and Asia Pacific. Each geo stores data in at least two Azure data center regions for HA/DR.??? Today, the United States geo uses data centers in North Central and South Central United States. To learn more, see [Where is Microsoft 365 customer data stored](/microsoft-365/enterprise/o365-data-locations).

Currently, Shifts offers data residency in Australia, Canada, France, Japan, and the United Kingdom. We're actively working to expand support to additional locations.

## Can I choose where Shifts data is stored

When you first set up Teams, you choose a country or region, which is set at the subscription level. Shifts honors this selection and uses the locale and region that's set in Teams if we support that region. If we aren't yet in that region, we store data in a nearby region that we support. In the future, we plan to migrate existing data, if stored in a nearby region, to the region that's provisioned in Teams.

## GDPR

## Can I recover a Shifts schedule that was deleted?

You can recover a deleted schedule in Shifts if the Microsoft 365 group that backs it is restored.

By default, a deleted Microsoft 365 group is retained for 30 days. This 30-day period is called "soft-delete" because you can restore the group.To learn more, see [Restore a deleted Microsoft 365 group](/microsoft-365/admin/create-groups/restore-deleted-group?view=o365-worldwide&tabs=admin-center).

## Data retention policies

Currently, Shifts doesn't support retention policies.

To learn more about retention policies in Teams, see [Learn about retention for Teams](/microsoft-365/compliance/retention-policies-teams) and [Manage retention policies for Teams](../../retention-policies.md).

## Which tier of compliance is Shifts?

Today, Shifts is Tier-C compliant. We're working towards Tier-D compliance.

## What type of encryption does Shifts use for data at rest and in transit?

Shifts encryption of data at rest and in transit are verified yearly by the SOC2 compliance audit.

Shifts data is encrypted at rest by Azure Cosmos DB and Azure Storage. To learn more, see [Azure data encryption at rest](/azure/security/fundamentals/encryption-atrest) and
[Data encryption in Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest).

Shifts data in transit uses Microsoft 365 guidelines. To learn more, see [Encryption for data-in-transit](/compliance/assurance/assurance-encryption-in-transit).

## Data immutability

## Data retrieval

### Graph API

### Ability to edit

### Deleting data

### Turning off Shifts and data

## Migrating data to another tenant

## Related articles

