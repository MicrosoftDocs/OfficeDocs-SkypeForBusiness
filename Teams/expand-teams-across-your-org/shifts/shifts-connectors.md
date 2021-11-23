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

Shifts connectors enable you to integrate Shifts, the schedule management tool in Microsoft Teams, with your workforce management (WFM) system. After you set up a connection, your frontline workers can seamlessly view and manage their schedules in your WFM system from within Shifts.

Connecting your WFM system to Teams empowers your frontline workforce to manage schedules more effectively and streamlines everyday processes for higher engagement and productivity. Your frontline workers have one place for their scheduling, communication, and collaboration needs to get work done, from anywhere, on any device.

We offer managed and open-source Shifts connectors. In this article, you'll learn about Shifts connectors and how they work.

## How Shifts connectors work

Connectors sync schedule data between your WFM system and Shifts, bringing your organization’s schedules into Teams. Shifts is where your frontline workers engage for their scheduling needs. Your WFM system is the system of record and source of truth for business rules, compliance, and intelligence.

Data flows via the connector both ways to ensure schedules are always up to date. Schedules in your WFM system are synced to Shifts. Changes made to schedules in Shifts are synced back to your WFM system. As the system of record, all business rules are enforced by your WFM system before data is saved to Shifts.

## Managed Shifts connectors

Managed Shifts connectors are connectors that we build in collaboration with our partners. Managed connectors are hosted and managed either by us or our partners. With managed connectors, integration is easy as only minimal setup is needed.

### Shifts to Blue Yonder connector

The Shifts to Blue Yonder connector is hosted and managed by Microsoft. With this connector, you can integrate Shifts with Blue Yonder 2020.3, 2021.1, and 2021.2 to manage your schedules and keep them up to date.

Frontline managers can:

- Publish shifts and schedules in Blue Yonder and view them in Shifts.
- Create, manage, and assign open shifts in Blue Yonder and view them in Shifts.
- Create, edit, and delete time off in Blue Yonder and view them in Shifts.
- View schedule requests from workers and approve them in Blue Yonder and in Shifts.
- Create and update worker availability in Blue Yonder.

Frontline workers can:

- See their own and their team's shifts and schedules in Shifts.
- Request time off, open shifts, and swap shifts in Shifts.
- Set their availability in Shifts.

#### Example scenario

Eden, a manager, publishes a schedule in Blue Yonder, which is synced to Shifts in Teams through the connector. Alex, a staff member, gets notified in Teams on his mobile device, and views his schedule and assigned shifts.

Alex needs to take some time off and requests a day off using Shifts. The request is sent to Blue Yonder through the connector. Blue Yonder ensures that the request is compliant with business rules and the request is created. Eden sees and approves the request in Blue Yonder. The approval is synced to Teams. (Eden can also see and approve the request in Shifts). Alex is notified in Teams that his request is approved, and views his updated schedule.

#### Set up a connection

Integrating Shifts with Blue Yonder using the connector takes just a few steps. You can use the Shifts connector wizard in the Microsoft 365 admin center to quickly and easily set up a connection. The wizard configures the connector, creates the connection, and applies the sync settings and team mappings that you choose. If you prefer to use PowerShell, we also provide PowerShell scripts that you can use to get connected.

For step-by-step guidance, see:

- [Use the Shifts connector wizard to connect your workforce management system](shifts-connector-wizard.md)
- [Use PowerShell to connect Shifts to your Blue Yonder workforce management system](shifts-connector-blue-yonder-powershell-setup.md)

After a connection is set up, you can update and change connection settings at any time, as needed. As for the connector itself, you don't need to worry about upgrades or maintenance. We take care of that.

### Shifts to Zebra-Reflexis connector

The Shifts to Zebra-Reflexis connector, currently in private preview, is hosted and managed by Zebra.

## Open-source Shifts connectors

Open-source Shifts connectors are community-driven integrations built on [Shifts Graph APIs](/graph/api/resources/shift). The following open-source connectors are available:

- Kronos-to-Teams WFC on premises
- JDA-to-Teams Shifts connector (for Blue Yonder version 2017 to 2020.2)

Each connector comes with detailed deployment and configuration guidance. They include Azure Resource Manager (ARM) deployment scripts that allow you to host all necessary services in Microsoft Azure. The source code and deployment scripts are available for download in a GitHub repository. You can deploy as is or customize or extend to meet your needs.

To learn more, see [Production-ready Shifts connectors](/microsoftteams/platform/samples/shifts-wfm-connectors).

## Related articles

- [Manage the Shifts app in Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
