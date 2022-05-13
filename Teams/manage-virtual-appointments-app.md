---
title: Manage the Virtual appointments app in Microsoft Teams
author: LanaChin
ms.author: v-lanachin
manager: samanro
ms.topic: conceptual
ms.service: msteams
ms.reviewer: 
search.appverid: MET150
searchScope:
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
  - Microsoft Cloud for Retail
audience: admin
description: Learn how to manage the Virtual appointments app for users in your organization.
ms.localizationpriority: medium
MS.collection: 
  - Teams_ITAdmin_Help
  - M365-collaboration
  - microsoftcloud-healthcare
  - microsoftcloud-retail
appliesto: 
  - Microsoft Teams
---

# Manage the Virtual appointments app for your organization in Microsoft Teams

## Overview of the Virtual appointments app

The Virtual appointments app provides a central hub for all your virtual appointment needs in Microsoft Teams. The app brings a cohesive schedule management experience to Teams, integrating virtual appointments from the [Bookings app](expand-teams-across-your-org/bookings-virtual-visits.md), the [Teams Electronic Health Record (EHR) connector](expand-teams-across-your-org/healthcare/teams-in-hc.md#virtual-appointments-and-electronic-healthcare-record-ehr-integration), and analytics, all in one place.

You can schedule and manage virtual appointments from Bookings, Teams, and Outlook, view reports to gain insight into virtual appointment activity, get real-time status updates in a queue view, and send appointment reminders to attendees.

:::image type="content" source="media/manage-virtual-appointments-app-home.png" alt-text="Screenshot of the Home page in the Virtual appointments app" lightbox="media/manage-virtual-appointments-app-home.png":::

The Virtual appointments app includes the following tabs:

- **Home**: This tab gives you quick access to key information, actions, and updates. From here, you can
- **Bookings schedule**: Access your Bookings calendar to schedule virtual appointments such as healthcare visits, financial consultations, interviews, education office hours, and virtual fittings and consultations. You can connect an existing Bookings calendar or create a new one. To learn more, see [Virtual appointments with Teams and the Bookings app](expand-teams-across-your-org/bookings-virtual-visits.md).
- **Queue**: View and monitor all virtual appointments in the Bookings calendar that you pinned, with updates in real time. From here, you can add a new booking, view relevant appointment details, see appointment statuses throughout the day, and send appointment reminders to assign staff and attendees. Staff can even join appointments directly from the queue. To learn more, see [Monitor appointments and get real-time status updates](expand-teams-across-your-org/bookings-virtual-visits.md#monitor-appointments-and-get-real-time-status-updates).
- **Analytics**: Get insight into usage activity and trends in your organization to help optimize virtual appointments to deliver better business outcomes. You can view key metrics such as total number of appointments, appointment duration, lobby wait time, and no shows. To learn more, see [Teams Virtual Visits usage report](teams-analytics-and-reports/virtual-visits-usage-report.md)
- **Manage**: Customize appointment types, set reminders, update business details, add staff and assign roles.


## What you need to know about Virtual appointments

Roles


## Set up the Virtual appointments app

### Enable or disable Virtual appointments in your organization

Virtual appointments is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](manage-apps.md) page in the Microsoft Teams admin center.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps** .
2. In the list of apps, search for the Virtual appointments app, select it, and then switch the **Status** toggle to **Blocked** or **Allowed**.

### Enable or disable Virtual appointments for specific users in your organization

To allow or block specific users in your organization from using Virtual appointments, make sure Virtual appointments is turned on for your organization on the [Manage apps](manage-apps.md) page. Then create a custom app permission policy and assign it to those users. To learn more, see [Manage app permission policies in Teams](teams-app-permission-policies.md).

### Use an app setup policy to pin the Virtual appointments app to Teams

App setup policies let you customize Teams to highlight the apps that are most important for users in your organization. The apps you set in a policy are pinned to the app bar—the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients—where users can quickly and easily access them.

To pin the Virtual appointments app for your users, you can edit the global (Org-wide default) policy. Or, you can create and assign a custom app setup policy. To learn more, see [Manage app setup policies in Teams](teams-app-setup-policies.md).

## Related articles