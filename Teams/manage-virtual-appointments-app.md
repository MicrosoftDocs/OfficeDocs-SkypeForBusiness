---
title: Manage the Virtual Appointments app in Microsoft Teams
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
description: Learn how to manage the Virtual Appointments app for users in your organization.
ms.localizationpriority: medium
MS.collection: 
  - Teams_ITAdmin_Help
  - M365-collaboration
  - microsoftcloud-healthcare
  - microsoftcloud-retail
appliesto: 
  - Microsoft Teams
---

# Manage the Virtual Appointments app for your organization in Microsoft Teams

[!INCLUDE [preview-feature](includes/preview-feature.md)]

The Virtual Appointments app provides a central hub for all your virtual appointments needs in Microsoft Teams. The app enables a seamless end-to-end experience for business-to-customer engagements, integrating schedules from the [Bookings app](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5), analytics, and management options, all in one place.

You can schedule, view, and manage virtual appointments from Bookings, Teams, and Outlook, get real-time status updates in a queue view, send appointment reminders, view reports to gain insight into virtual appointments activity, and configure calendar, staff, and booking page settings.

With any Microsoft 365 or Office 365 license, you can use basic Virtual Appointments capabilities in the app to schedule and join business-to-customer meetings. With [Teams Premium](https://review.learn.microsoft.com/MicrosoftTeams/enhanced-teams-experience?branch=danismith-t-pre-licensing), your organization gets advanced Virtual Appointments capabilities. These include a queue of scheduled and on-demand appointments, SMS notifications, lobby chat, and departmental and organizational analytics.

[EMBED VIDEO?]

## Overview of the Virtual Appointments app

The Virtual Appointments app has the following tabs.

- [Home](#home)
- [Bookings schedule](#bookings-schedule)
- [Queue](#queue)
- [Analytics](#analytics)
- [Manage](#manage)

Here's an overview of what's on each tab.

### Home

> [!NOTE]
> ADD take-back and Premium messaging (queue/analytics)

Get easy access to key actions and information. The dashboard provides a quick view of the Bookings schedule, a summary of the queue of appointments, a snapshot of appointment analytics, and management options.

:::image type="content" source="media/manage-virtual-appointments-app-home.png" alt-text="Screenshot of the Home page in the Virtual Appointments app" lightbox="media/manage-virtual-appointments-app-home.png":::

### Bookings schedule

Access your Bookings calendar to schedule virtual appointments such as healthcare visits, financial consultations, interviews, virtual fittings and consultations, and more. You can connect an existing Bookings calendar or create a new one. To learn more about Bookings, see [Virtual Appointments with Teams and the Bookings app](expand-teams-across-your-org/bookings-virtual-visits.md) and [What is Bookings?](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5).

:::image type="content" source="media/manage-virtual-appointments-app-bookings-schedule.png" alt-text="Screenshot of the Bookings schedule page in the Virtual Appointments app" lightbox="media/manage-virtual-appointments-app-bookings-schedule.png":::

### Queue

> [!NOTE]
> ADD take-back (scheduled), Premium (on-demand), and promo (SMS) messaging<br>Access to scheduled appointments in the queue and SMS notifications will soon require a Teams Premium license. A Teams Premium license is needed to access on-demand appointments.

View and monitor all scheduled and on-demand virtual appointments in the Bookings calendar that you pinned, with updates in real time.

From here, schedulers can add a new booking, view relevant appointment details, and see appointment statuses throughout the day. They can also send email reminders to assigned staff and attendees, and send SMS text notifications to attendees for scheduled appointments. Staff can even join appointments directly from the queue.

To learn more, see [Monitor appointments and get real-time status updates](https://review.learn.microsoft.com/microsoft-365/frontline/bookings-virtual-appointments?branch=v-lanachin-bookings-prem#monitor-appointments-and-get-real-time-status-updates-in-the-queue-view).

:::image type="content" source="media/manage-virtual-appointments-app-queue.png" alt-text="Screenshot of the Queue page in the Virtual Appointments app" lightbox="media/manage-virtual-appointments-app-queue.png":::

### Analytics

> [!NOTE]
> ADD calendar analytics content (when available), ADD take-back (VA usage) and Premium messaging (calendar analytics)

Get insight into usage activity and trends in your organization to help optimize Virtual Appointments to deliver better business outcomes. The analytics experience here is based on user role.

Admins will see the following reports, showing aggregated analytics across the organization:

- The [Teams Virtual Appointments usage report](https://review.learn.microsoft.com/en-us/microsoft-365/frontline/virtual-appointments-usage-report?branch=v-lanachin-va-report#the-virtual-appointments-usage-report) gives admins an overview of Teams Virtual Appointments activity in your organization. This report provides key metrics such as total number of appointments, appointment duration, lobby wait time, and no shows for appointments created and conducted through multiple scheduling entry points.

  :::image type="content" source="media/manage-virtual-appointments-app-analytics.png" alt-text="Screenshot of the Analytics page in the Virtual Appointments app, showing the Virtual Appointments usage report" lightbox="media/manage-virtual-appointments-app-analytics.png":::

- The [Teams Virtual Appointments active user report](https://review.learn.microsoft.com/microsoft-365/frontline/virtual-appointments-active-user-report?branch=v-lanachin-va-report#the-virtual-appointments-usage-report) provides active user information for advanced Virtual Appointments capabilities that are available with Teams Premium. Admins can see how many users are actively using advanced capabilities, which capabilities they're using, and a detailed breakdown for individual appointments.

    [placeholder for screenshot]

Non-admins, such as schedulers, will see departmental analytics???

[placeholder for screenshot]

### Manage

Manage your Bookings calendar settings. You can update your business details, customize appointment types, add staff and assign roles, and configure your booking page settings.

[NEED NEW SCREENSHOT]<br>
:::image type="content" source="media/manage-virtual-appointments-app-manage.png" alt-text="Screenshot of the Manage page in the Virtual Appointments app" lightbox="media/manage-virtual-appointments-app-manage.png":::

## Set up the Virtual Appointments app

### Enable or disable the Virtual Appointments app in your organization

The Virtual Appointments app is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](manage-apps.md) page in the Microsoft Teams admin center.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps** .
2. In the list of apps, search for the Virtual Appointments app, select it, and then switch the **Status** toggle to **Blocked** or **Allowed**.

### Enable or disable the Virtual Appointments app for specific users in your organization

To allow or block specific users in your organization from using the app, make sure the app is turned on for your organization on the [Manage apps](manage-apps.md) page. Then create a custom app permission policy and assign it to those users. To learn more, see [Manage app permission policies in Teams](teams-app-permission-policies.md).

### Use an app setup policy to pin the Virtual Appointments app to Teams

App setup policies let you customize Teams to highlight the apps that are most important for users in your organization. The apps you set in a policy are pinned to the app bar—the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients—where users can quickly and easily access them.

To pin the Virtual Appointments app for your users, you can edit the global (Org-wide default) policy. Or, you can create and assign a custom app setup policy. To learn more, see [Manage app setup policies in Teams](teams-app-setup-policies.md).

## Related articles

- [Virtual Appointments guided tour](https://guidedtour.microsoft.com/guidedtour/industry-longform/virtual-appointments/1/1)
