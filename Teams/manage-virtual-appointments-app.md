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
appliesto: 
  - Microsoft Teams
---

# Manage the Virtual Appointments app for your organization in Microsoft Teams

[!INCLUDE [preview-feature](includes/preview-feature.md)]

The Virtual Appointments app provides a central hub for all your virtual appointments needs in Microsoft Teams. The app enables a seamless end-to-end experience for business-to-customer engagements, integrating schedules from the [Bookings app](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5), analytics, and management options, all in one place.

You can schedule, view, and manage virtual appointments, get real-time status updates in a queue view, send appointment reminders, view analytics and reports to gain insight into virtual appointments activity, and configure calendar, staff, and booking page settings.

With any Microsoft 365 license, you can use basic Virtual Appointments capabilities to schedule and join business-to-customer meetings. For example, you can schedule appointments in the Bookings calendar and external attendees can [join through a browser](/microsoft-365/frontline/browser-join) without having to download Teams. [Teams Premium](teams-add-on-licensing/licensing-enhance-teams) (Preview) unlocks advanced Virtual Appointments capabilities that your organization can use to manage and personalize the experience. These include a queue view of scheduled and on-demand appointments, SMS text notifications, custom waiting rooms, and analytics.

## Overview of the Virtual Appointments app

The Virtual Appointments app has the following tabs.

- [Home](#home)
- [Bookings schedule](#bookings-schedule)
- [Queue](#queue)
- [Analytics](#analytics)
- [Manage](#manage)

Here's an overview of what's on each tab.

### Home

![Information icon](media/info.png) **The Queue and Analytics tiles are part of [Teams Premium](teams-add-on-licensing/licensing-enhance-teams) (Preview).**

Get easy access to key actions and information. The Home page provides a quick view of the Bookings schedule, a summary of the queue of appointments, a snapshot of appointment analytics, and management options.

:::image type="content" source="media/manage-virtual-appointments-app-home.png" alt-text="Screenshot of the Home page in the Virtual Appointments app" lightbox="media/manage-virtual-appointments-app-home.png":::

### Bookings schedule

![Information icon](media/info.png) **SMS notifications are now part of [Teams Premium](teams-add-on-licensing/licensing-enhance-teams) (Preview). Users can continue using this feature during the preview period. After the preview, users need a Teams Premium license.**

Access your Bookings calendar to schedule virtual appointments such as healthcare visits, financial consultations, interviews, virtual fittings and consultations, and more. You can connect an existing Bookings calendar or create a new one. To learn more, see [Virtual Appointments with Teams and the Bookings app](https://review.learn.microsoft.com/microsoft-365/frontline/bookings-virtual-appointments?branch=v-lanachin-bookings-prem) and [What is Bookings?](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5).

:::image type="content" source="media/manage-virtual-appointments-app-bookings-schedule.png" alt-text="Screenshot of the Bookings schedule page in the Virtual Appointments app" lightbox="media/manage-virtual-appointments-app-bookings-schedule.png":::

### Queue

![Information icon](media/info.png) **The scheduled queue view and SMS notifications are now part of [Teams Premium](teams-add-on-licensing/licensing-enhance-teams) (Preview). Users can continue using these features during the preview period. After the preview, users need a Teams Premium license. To access the on-demand queue during the preview period, users need a Teams Premium trial license.**

View and monitor all scheduled and on-demand virtual appointments in the Bookings calendar that you pinned, with updates in real time.

From here, schedulers can add a new booking, view relevant appointment details, and see appointment statuses throughout the day. They can also send email reminders to assigned staff and attendees and send SMS text notifications to attendees for scheduled appointments. Staff can join appointments directly from the queue.

To learn more, see [Monitor appointments and get real-time status updates](/microsoft-365/frontline/bookings-virtual-appointments#monitor-appointments-and-get-real-time-status-updates-in-the-queue-view).

:::image type="content" source="media/manage-virtual-appointments-app-queue.png" alt-text="Screenshot of the Queue page in the Virtual Appointments app" lightbox="media/manage-virtual-appointments-app-queue.png":::

### Analytics

Get insight into usage activity and trends to help optimize Virtual Appointments and deliver better business outcomes.

The Teams Virtual Appointments usage report gives admins, decision makers, and users an overview of virtual appointments activity in your organization. The report provides key metrics such as total number of appointments, appointment duration, lobby wait time, and no shows.

You can view detailed activity for virtual appointments scheduled and conducted through multiple scheduling entry points and drill down into individual appointment data.

The analytics experience depends on user role. Admins get [organizational analytics](#organizational-analytics) and non-admins get [departmental or inividual analytics](#departmental-and-individual-analytics).

#### Organizational analytics

![Information icon](media/info.png) **This feature is available as part of [Teams Premium](teams-add-on-licensing/licensing-enhance-teams) (Preview). After the preview period, a Teams Premium license is required.**

Admins see an org-level report that shows aggregated analytics across all departments within your organization.

:::image type="content" source="media/manage-virtual-appointments-app-analytics-org.png" alt-text="Screenshot of the Analytics page in the Virtual Appointments app, showing the Virtual Appointments usage report for admins" lightbox="media/manage-virtual-appointments-app-analytics-org.png":::

To learn more, see [Virtual Appointments usage report](/microsoft-365/frontline/virtual-appointments-usage-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json).

#### Departmental and individual analytics

![Information icon](media/info.png) **To access this feature during the preview period, users need a [Teams Premium](teams-add-on-licensing/licensing-enhance-teams) trial license.**

Non-admins see a department-level report that provides data for the given department.

:::image type="content" source="media/manage-virtual-appointments-app-analytics-dept.png" alt-text="Screenshot of the Analytics page in the Virtual Appointments app, showing the Virtual Appointments usage report for non-admins" lightbox="media/manage-virtual-appointments-app-analytics-dept.png":::

If a staff member isn’t associated with a department, they’ll see a report showing data for the appointments that they conducted.

### Manage

Manage your Bookings calendar settings. You can update your business details, customize appointment types, add staff and assign roles, and configure your booking page settings.

:::image type="content" source="media/manage-virtual-appointments-app-manage.png" alt-text="Screenshot of the Manage page in the Virtual Appointments app" lightbox="media/manage-virtual-appointments-app-manage.png":::

## Set up the Virtual Appointments app

### Enable or disable the Virtual Appointments app in your organization

The Virtual Appointments app is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](manage-apps.md) page in the Microsoft Teams admin center.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps** .
2. In the list of apps, search for the Virtual Appointments app, select it, and then switch the **Status** toggle to **Blocked** or **Allowed**.

### Enable or disable the Virtual Appointments app for specific users in your organization

To allow or block specific users in your organization from using the app, make sure the app is turned on for your organization on the [Manage apps](manage-apps.md) page. Then create a custom policy for app permissions and assign it to those users. To learn more, see [Manage app permission policies in Teams](teams-app-permission-policies.md).

### Use an app setup policy to pin the Virtual Appointments app to Teams

App setup policies let you customize Teams to highlight the apps that are most important for users in your organization. The apps you set in a policy are pinned to the app bar—the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients—where users can quickly and easily access them.

To pin the Virtual Appointments app for your users, you can edit the global (Org-wide default) policy. Or, you can create and assign a custom app setup policy. To learn more, see [Manage app setup policies in Teams](teams-app-setup-policies.md).

## Terms of service

See [Terms of service](virtual-appointments-app-terms-of-service.md).

## Related articles

- [Virtual Appointments guided tour](https://guidedtour.microsoft.com/guidedtour/industry-longform/virtual-appointments/1/1)
- [Teams Premium licensing](teams-add-on-licensing/licensing-enhance-teams)
