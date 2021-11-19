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

Connecting your WFM system empowers your frontline workforce to manage schedules more effectively and streamlines everyday processes for higher engagement and productivity. Frontline workers can manage their scheduling needs and use the rich communication and collaboration features of Teams to get work done, from anywhere, on any device. *Your frontline workers have one place for their scheduling, communication, and collaboration needs to get work done, from anywhere, on any device.*

We offer managed and open-source Shifts connectors. In this article, you'll learn about Shifts connectors and how they work.

## How Shifts connectors work

Connectors sync schedule data between your WFM system and Shifts, bringing your organization’s schedules into Teams. Shifts is where your frontline workers engage for their scheduling needs. Your WFM system is the system of record and source of truth for business rules, compliance, and intelligence.

Data flows via the connector both ways to ensure schedules are always up to date. Schedules in your WFM system are synced to Shifts. Changes made to schedules in Shifts are synced back to your WFM system. As the system of record, all business rules are enforced by your WFM system before data is saved to Shifts.

Frontline workers can easily view their schedule, swap shifts, and request schedule changes from within Shifts in Teams. For example, they can:

- See their assigned shifts
- Swap shifts
- Set availability
- Offer shifts
- Request open shifts
- Request time off

Frontline managers can see workers' schedules and review requests for time off, shift swaps, and offers.

## Managed Shifts connectors

Managed Shifts connectors are connectors that we built in collaboration with our partners. Managed connectors are owned, hosted, and managed either by us or our partners. With managed connectors, integration is easy as only minimal setup is needed.

### Shifts to Blue Yonder connector

The Shifts to Blue Yonder connector is hosted and managed by us and supports Blue Yonder 2020.3 and later versions.

With this connector, integrating Shifts with Blue Yonder takes just a few steps.  You can use the Shifts connector wizard in the Microsoft 365 admin center to quickly and easily set up a connection. The wizard configures the connector, creates the connection, and applies the sync settings and team mappings that you choose. If you prefer to use PowerShell, we also provide PowerShell scripts that you can use to get connected.

For step-by-step guidance, see:

- [Use the Shifts connector wizard to connect your workforce management system](shifts-connector-wizard.md)
- [Use PowerShell to connect Shifts to your Blue Yonder workforce management system](shifts-connector-blue-yonder-powershell-setup.md)

After you set up a connection, you can update and change connection settings at any time, as needed. As for the connector itself, you don't need to worry about upgrades or maintenance. We take care of that.

#### Scenarios

- Frontline manager creates and publishes schedules in Blue Yonder. Schedules are synced to Teams through the connector. Frontline manager views copy of schedule in Teams.
- Frontline worker gets notified of published schedule from Teams on their mobile device and views and manage manage their schedule in Teams. Any updates in BY are refreshed in Team, and FLW gets notified.
- FLW requests time off. Request is sent to BY through the connector, BY ensures that the request can be processed. FLM gets notified, sees request in BY, and approves the request. Approval is synced back to Teams. FLW is notified that request is approved, and their schedule is updated. 
Any updates in BY is synced to Teams.
- FLW wants to swap shift with a coworker. Select from a list of shifts that qualify for a swap based on rules in BY. Coworker gets notified and accepts request in Teams. Manager sees request and approves in BY or Shifts. FLW's request is completed and schedule updated in Shifts.

### Shifts to Zebra-Reflexis connector

The Shifts to Zebra-Reflexis connector, currently in private preview, is hosted and managed by Zebra.

## Open-source Shifts connectors

Open-source Shifts connectors are community-driven integrations built on Shifts Graph APIs. The following open-source connectors are available:

- Kronos-to-Teams WFC on premises
- JDA-to-Teams Shifts connector (for Blue Yonder version 2017 to 2020.2)

Each connector comes with detailed deployment and configuration guidance. They include Azure Resource Manager (ARM) deployment scripts that allow you to host all necessary services in Microsoft Azure. The source code and deployment scripts are available for download in a GitHub repository. You can deploy as is or customize or extend to meet your needs.

To learn more, see [Production-ready Shifts connectors](/microsoftteams/platform/samples/shifts-wfm-connectors).

## Related articles

- [Manage the Shifts app in Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
