---
title: Shifts connectors
author: lanachin
ms.author: v-lanachin
ms.reviewer: aaku
manager: samanro
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn about Shifts connectors and how to use them to connect Shifts to your workforce management system. 
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

We offer managed and open-source Shifts connectors. This article gives you an overview of Shifts connectors and how they work.

## How Shifts connectors work

Connectors sync schedule data between your WFM system and Shifts, bringing your organization’s schedules into Teams. Shifts is where your frontline workers engage for their scheduling needs. Your WFM system is the system of record for business rules, compliance, and intelligence.

Data flows via the connector both ways to ensure schedules are always up to date. Schedules in your WFM system are synced to Shifts. And, changes made to schedules in Shifts are synced back to your WFM system in real time. As the system of record, all business rules are enforced by your WFM system before data is saved to Shifts.

## Managed Shifts connectors

Managed Shifts connectors are connectors developed in collaboration with our partners. Managed connectors are hosted and managed either by us or our partners. With managed connectors, only minimal setup is needed.

### Reflexis Shifts connector for Microsoft Teams

The Reflexis Shifts connector for Microsoft Teams is hosted and managed by Zebra. With this connector, you can integrate Shifts with the Reflexis WFM system to manage your schedules and keep them up to date.

Frontline workers have access to their schedule in Shifts in Teams, and their requests are synchronized from Shifts to Reflexis Workforce Scheduler (RWS). The status of requests and shifts created in RWS are synced to Shifts in Teams.

:::image type="content" source="../../media/shifts-connector-reflexis.png" alt-text="Screenshot showing list of shifts on a mobile device and a schedule in Reflexis" lightbox="../../media/shifts-connector-reflexis.png":::

Frontline managers can:

- Publish shifts and schedules in Reflexis and view them in Shifts.
- Edit shifts in both Reflexis and Shifts.
- Create, manage, and assign open shifts in both Reflexis and Shifts.
- View and approve schedule requests from workers in both Reflexis and Shifts.

Frontline workers can:

- See their own and their team's shifts and schedules in Shifts.
- Request time off, open shifts, and swap and offer shifts in Shifts.

To learn more, go to https://connect.zebra.com/microsoft-connectors.

## Open-source Shifts connectors

Open-source Shifts connectors are community-driven integrations built on [Shifts Graph APIs](/graph/api/resources/shift). The following open-source connectors are available:

- Kronos-to-Teams WFC on-premises
- JDA-to-Teams Shifts connector (for Blue Yonder version 2017 to 2020.2)

Each connector comes with detailed deployment and configuration guidance. They include Azure Resource Manager (ARM) deployment scripts that allow you to host all necessary services in Microsoft Azure. The source code and deployment scripts are available for download in a [GitHub repository](https://github.com/OfficeDev/Microsoft-Teams-Shifts-WFM-Connectors). You can deploy as is or customize or extend to meet your needs.

To learn more, see [Production-ready Shifts connectors](/microsoftteams/platform/samples/shifts-wfm-connectors).

## Related articles

- [Manage the Shifts app](manage-the-shifts-app-for-your-organization-in-teams.md)
