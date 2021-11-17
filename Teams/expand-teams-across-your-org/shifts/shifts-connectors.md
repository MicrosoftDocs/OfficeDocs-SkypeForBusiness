---
title: Shifts connectors
author: lanachin
ms.author: v-lanachin
ms.reviewer: 
manager: samanro
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: 
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Shifts connectors

## Overview

Shifts connectors enable you to integrate Shifts, the schedule management tool in Microsoft Teams, with your workforce management (WFM) system. After a connection is set up, your frontline workers can seamlessly view and manage their schedules in your WFM system from within Shifts.

Connecting your WFM system empowers your frontline workforce to manage schedules more effectively and streamlines everyday processes for higher engagement and productivity. Frontline workers can manage their scheduling needs in Shifts and use the rich communication and collaboration features of Teams to get work done, from anywhere, on any device.

*Your frontline workers have one place for their scheduling, communication, and collaboration needs to get work done, from anywhere, on any device.*

We offer managed and open-source Shifts connectors. This article gives you an overview of these connectors, how they work, and how to connect Shifts with your WFM system.

## How Shifts connectors work

Connectors sync schedule data between your WFM system and Shifts, bringing your organization’s schedules and business rules into Teams. Your WFM is the system of record and enforces all business rules.

Schedule data flows both ways. Schedules in your WFM system are synced to Shifts. Any changes made in Shifts are synced back to your WFM system to ensure schedules are always up to date.

Frontline workers can easily view their schedule, swap shifts, and request schedule changes from within Shifts. For example, they can:

- See their assigned shifts
- Swap shifts
- Set availability
- Offer shifts
- Request open shifts
- Request time off

Frontline managers can continue to use your WFM system or use Shifts to set up and manage schedules.

## Managed Shifts connectors

Managed Shifts connectors are connectors that we built in collaboration with our partners. These connectors are owned, hosted, and managed either by us or our partners and require minimal setup.

### Shifts to Blue Yonder connector

The Shifts to Blue Yonder connector is hosted and managed by Microsoft. You can use the Shifts connector wizard in the Microsoft 365 admin center or PowerShell to easily and quickly set up a connection to your Blue Yonder WFM system.

For step-by-step guidance, see:

- [Use the Shifts connector wizard to connect your workforce management system](shifts-connector-wizard.md)
- [Use PowerShell to connect Shifts to your Blue Yonder workforce management system](shifts-connector-blue-yonder-powershell-setup.md)

### Shifts to Zebra-Reflexis connector

The Shifts to Zebra-Reflexis connector is hosted and managed by Zebra.

## Open-source Shifts connectors

Open-source Shifts connectors are community-driven integrations built on Graph APIs. The following open-source connectors are available:

- Kronos-to-Teams WFC on premises
- JDA-to-Teams Shifts connector

Each connector comes with detailed deployment and configuration guidance. They include Azure Resource Manager (ARM) deployment scripts that allow you to host all necessary services in Microsoft Azure. The source code and deployment scripts are available for download in a GitHub repository. You can deploy as is or customize or extend to meet your needs.

To learn more, see [Production-ready Shifts connectors](/microsoftteams/platform/samples/shifts-wfm-connectors).

## Related articles

- [Manage the Shifts app in Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
