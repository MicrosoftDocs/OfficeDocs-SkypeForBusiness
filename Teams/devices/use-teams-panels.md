---
title: "How to use Microsoft Teams panels devices"
ms.author: v-mdhiman
author: ManikaDhiman
manager: serdars
ms.reviewer: weizxue
ms.topic: reference
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-voice
search.appverid: MET150
localization_priority: Normal
description: "This article provides guidance on how to use Teams panels devices."
---

# Use Microsoft Teams panels

Microsoft Teams panels are compact digital display devices that are mounted right outside of your meeting spaces, typically near the entrance. These touchscreen panels are dedicated Microsoft Teams devices that provide at-a-glance view about your meeting space and the scheduled meeting. With the vibrant color-coded LED and Home screen indicators, you can determine if the space is available or reserved from a distance. You can use Teams panels to reserve an available meeting space for an ad-hoc meeting, on the spot.

Teams panels devices come preinstalled with Microsoft Teams and display meeting details that are scheduled through Outlook or Teams calendars.

This article provides guidance, to both end users and admins, on how to use the Teams panels devices. It also provides answers to the most [frequently asked questions](#frequently-asked-questions) about using these devices.

For an overview of the Teams panels devices, and the guidance on how to plan, deliver, and manage them in your organization, see [Deploy Microsoft Teams panels](teams-panels.md).

## Teams panels end-user experience

Explore the [Home screen](#explore-teams-panels-home-screen) of your Teams panels device to view meeting space and meeting details. Or, tap and scroll on the touchscreen panel to do other actions.

Use your Teams panels devices to:

- [View meeting space details and availability, meeting details, upcoming reservations](#explore-teams-panels-home-screen)
- [Reserve an available meeting space](#reserve-meeting-spaces-for-ad-hoc-meetings)
- [Report a problem](#report-a-problem)
- [View or update a device setting](#view-or-update-a-device-setting)

## Explore Teams panels Home screen

The Home screen is the main visual interface of your Teams panels device.  

From the Home screen, you can view location and meeting details, reserve a space, view upcoming reservations, and identify current availability status.

The following screenshot shows different areas on the Teams panels Home screen:

:::image type="content" source="../media/panels-home-screen-explanation.png" alt-text="This screenshot displays different areas on the Teams panels Home screen":::

Refer to the following table for a description of each area:

Area | Description
:---|:---
**1-Current time, day, date, and meeting space details** | Displays current time, day, date, and meeting space name. The meeting space name is the name of the resource account signed in to the panels device.
**2-Meeting space availability and meeting details** | Indicates meeting space availability and displays meeting details. See [Meeting space availability and meeting details pane](#meeting-space-availability-and-meeting-details-pane).
**3-Upcoming Calendar** | Displays the meeting space calendar and availability for up to 24 hours from the current time. Scroll down to view the upcoming calendar of the meeting space.
**4-Settings icon** | Opens the **Settings** pane. Report a problem or update available device settings.

### Meeting space availability and meeting details pane

The appearance of this pane and its capabilities differ depending on the meeting space availability and type of reservation.

#### Meeting space is reserved for a scheduled meeting

If the meeting space is reserved for a scheduled meeting (scheduled via Outlook or Teams), the pane appears in purple. It displays meeting title in prominent text, meeting start and end times, and meeting organizer's name. If it's a Teams meeting, the Teams logo also appears. With meeting details prominently displayed, attendees can easily confirm they’re in the right meeting space, at the right time, and for the right meeting.

:::image type="content" source="../media/panels-right-pane-scheduled-meeting.png" alt-text="Teams panels Home screen showing that the meeting space is reserved for a scheduled meeting":::

> [!NOTE]
>
> - After you schedule a meeting, it can take up to 90 seconds for the calendar to sync and reflect it on the panels screen.
> - For a [scheduled meeting that is marked as private](https://support.microsoft.com/office/make-an-appointment-or-meeting-private-dc3898f0-22f5-45c6-8cc8-b4d4db84111d), the panels displays **Private meeting** in the meeting title instead of the actual meeting title.

#### Meeting space is reserved for an ad-hoc meeting

If the meeting space is [reserved for an ad-hoc meeting](#reserve-meeting-spaces-for-ad-hoc-meetings), the pane appears in purple. It displays **Reserved** in prominent text, and meeting start and end times. If you schedule an ad-hoc meeting from the panel (instead of Outlook or Teams calendars), you actually book the calendar of that meeting space. Such ad-hoc meetings are automatically scheduled as Teams meetings and always display the Teams logo.

:::image type="content" source="../media/panels-right-pane-reserved-adhoc.png" alt-text="Teams panels Home screen showing that the meeting space is reserved for an ad-hoc meeting":::

#### Meeting space is available

If the meeting space is available, the pane appears in green, and displays **Available** in prominent text. A **Reserve** button also appears that you can tap to [reserve the meeting space for an ad-hoc meeting](#reserve-meeting-spaces-for-ad-hoc-meetings). You can check the upcoming calendar of the meeting space (right bottom pane) to decide the end time for your ad-hoc meeting.

:::image type="content" source="../media/panels-right-pane-available-status.png" alt-text="This screenshot shows how the Teams panels Home screen appears when the meeting space is available":::

## Reserve meeting spaces for ad-hoc meetings

You can reserve an [available meeting space](#meeting-space-is-available) directly from the panels device for an ad-hoc meeting. All ad-hoc meetings are automatically scheduled as Teams meetings. However, once the meeting space is reserved for an ad-doc meeting, you can't release or unreserve the meeting space from the panels device itself. Only admins of the device's resource account can cancel the ad-hoc meeting (via Outlook or Teams calendar) to unreserve the space.

For ad-hoc meetings that are booked directly on the panel:

- The start time is always the current time and as such you can't schedule it for a future time.
- The end time can be until the next scheduled meeting or up to 24 hours from the current time, whichever is earlier. Check the **Upcoming Calendar** pane on the Home screen for the meeting space availability.
- The duration can't be less than five minutes. Exception to this is when there is less than 5 minutes to the hour and there's another meeting scheduled starting from the next hour, then you can book the space until the next meeting start time. For example, current time is 1:57 PM but there is another scheduled meeting at 2:00 PM, in this case, you can schedule an ad-hoc meeting for 3 mins.

To reserve an available meeting space for an ad-hoc meeting:

1. On the Home screen, tap the **Reserve** button.
    :::image type="content" source="../media/panels-reserve.png" alt-text="Teams panels Home screen showing the Reserve button":::
2. In the **Ad hoc meeting** pane, review the available end time choices. You can use the right or left arrows to browse the available end time choices.

    :::image type="content" source="../media/panels-reserve-endtime.png" alt-text="Ad hoc meeting pane showing end time slots":::

    > [!Note]
    >
    > - The end time choices are displayed in 15-minute intervals of an hour.
    > - The end time defaults to the next 15-minute interval that is at least 5 minutes after the current time. For example, if the current time is 1:57 PM, the default end time displays as 2:15 PM, and not 2:00 PM. This prevents users from reserving a meeting space for less than five minutes.
    > In the screenshot above, since the duration between the current time (1:53 PM) and the next 15-minute interval (2:00 PM) is more than 5 minutes, the default end time is displayed as 2:00 PM.

3. Tap the desired end time interval, and then tap **Reserve**.

    A confirmation window appears with a thumbs up emoji, meeting start and end time, and meeting space name.
    :::image type="content" source="../media/panels-reserve-confirmation.png" alt-text="Ad hoc meeting confirmation message":::
The right pane on the Home screen right now appears in purple and displays the **Reserved** text and the Teams logo. This indicates that the meeting space is now reserved for an ad-hoc Teams meeting.
  
    :::image type="content" source="../media/panels-right-pane-reserved-adhoc.png" alt-text="Home screen showing that meeting space is reserved for an ad-hoc meeting":::

    > [!NOTE]
    > If the meeting space is a Microsoft Teams Room, you can _join_ this Teams meeting with the in-room Microsoft Teams Room or Surface Hub devices.

<!--To learn more, check out [Get started with Teams displays](https://support.microsoft.com/office/get-started-with-teams-displays-ff299825-7f13-4528-96c2-1d3437e6d4e6).-->

### Report a problem

To report an issue with the device or the meeting space, to request a feature update, or to provide any feedback, use the **Setting** icon on the Home screen.

1. Tap the **Settings** gear icon on the Home screen.

2. Tap the **Report an issue** option.

    The **Send Feedback** pane is displayed in a form format.
3. From the **Type** dropdown, select the type of request.
4. From the **Issue** dropdown, select the category.
5. In the **Title** text field, type the title using the device keypad.
6. In the text field below **Title**, type additional details, if necessary.

    > [!NOTE]
    > Do not include any personally identifiable information.

7. Review your entries and tap **Send**.

    Admin of the device resource account receives an email with all the details.

### View or update a device setting

There are several device settings, such as about, accessibility, reboot, privacy policy that you can view or update directly from the device. The available device settings may differ based on the Original Equipment Manufacturer (OEM) of your device. Refer to the OEM's documentation for more information.

To view or update a device setting:

1. Tap the **Settings** icon on the Home screen.
2. In the **Settings** pane, tap **Device settings**.
3. In the **Device Settings** pane, tap the setting that you want to view or update.
4. Follow the prompt on the screen to view or update the setting.

## Teams panels admin experience

If you're the admin of the [Teams panel's resource account](teams-panels.md\#resource-account-provisioning), then you're also the admin of the **Panels App** on the device. As the **Panels App** admin, you can do all the functions mentioned in the [end-user experience](#teams-panels-end-user-experience) section, in addition to managing the **Panels App** settings on the device.

Your Teams panels devices provide two types of admin settings. You must be a device admin to access the available admin settings. End users can't access these settings.

- Admin settings that are specific to the device, such as display, time and date, language, bluetooth, WiFi, and so on. Refer to the OEM documentation to know more about these settings.
- Admin settings that are specific to **Panels App** on your device, such as wallpaper and LED indicator color. Only an admin of **Panels App** can access these settings. Since **Panels App** settings are available as part of admin settings, you must have admin login credentials for both the device and **Panels App** to access **Panels App** settings.

> [!NOTE]
> Any updates to the **Panels App** settings done via the device are applicable only to that specific device. Those updates will not impact other panels devices in your organization. For example, if you change the Home screen wallpaper image setting from the **Panels App** settings on a device, the wallpaper image will change only for that specific device.
>
> To manage the Teams app settings across multiple devices in your organization, use [Microsoft Teams admin center](device-management.md).

### Access Panels App settings

You can access **Panels App**-specific settings by using the **Panels App Settings** option under the admin settings. The steps to access **Panels App Settings** may differ slightly based on the OEM of your device.

To access the **Panels App Settings** option:

1. Tap the **Settings** icon on the Home screen.
2. On the **Settings** pane, tap **Device settings**.
3. Tap the **Admin Settings**.

    > [!NOTE]
    > Depending on the OEM of your device, you may need to enter the device admin password now to proceed or may need to enter it after the next step.

4. Scroll down to find the **Panels App Settings** option. Tap it.
5. Tap the **Panels App Settings** button on the right pane.
    The pane with the available **Panels App** settings is displayed.

    :::image type="content" source="../media/panels-app-settings-pane.png" alt-text="This screenshot displays the pane with the available Panels app settings":::

    Use this pane to update the following **Panels App** settings for your device:

    - [Wallpaper](#update-the-wallpaper)
    - [LED indicator](#change-the-busy-state-led-color)

#### Update the wallpaper

Change the Home screen wallpaper image.

1. [Access **Panels App Settings**](#access-panels-app-settings).
2. Tap **Wallpapers**.
3. From **Choose your image**, select an image to set as the Home screen background image. The **Background** pane displays the preview of the image.
:::image type="content" source="../media/panels-wallpapers-setting.png" alt-text="This screenshot displays the the wallpaper settings pane":::
4. Go back to the Home screen and verify that the wallpaper is updated.

#### Change the busy state LED color

Change the LED color to indicate busy or reserved state. Admins can choose either red or purple as the LED color to indicate that the meeting space is reserved. The LED color to indicate an available space is always green and you can't change it.

1. [Access **Panels App Settings**](#access-panels-app-settings).
2. Tap **LED Settings**.
3. From **Choose your LED color**, select your desired color option.
:::image type="content" source="../media/panels-led-settings.png" alt-text="This screenshot displays the the LED color busy state settings":::
4. Go back to the Home screen and verify that the LED color for the busy state is updated. If the meeting space is available, schedule a test meeting to verify the change in LED color for the busy state. 

## Frequently asked questions

Find answers to frequently asked questions about the Teams panels devices.

**How far in the future can I see the scheduling details of a meeting space?**  
In the **Upcoming Calendar** pane (bottom right pane) on the Home screen, you can see the scheduling details of a meeting space for up to 24 hours in the future from the current time.

**Can I reserve a meeting space for a future time from the Teams panels device?**  
No, you can't reserve a meeting space for a future time from the Teams panels device. The start time is always the current time for an ad-hoc meeting scheduled via Teams panels.

**How long I can reserve an available meeting space for an ad hoc meeting?**  
You can reserve an available meeting space starting from your current time until the next scheduled meeting time, or up to a maximum of 24 hours from your current time, whichever is earlier. For example, if the current time is 10 AM, and the device displays the next scheduled meeting at 2 PM, you can reserve the meeting space from 10 AM until 2 PM.

<!--**Can I run Teams panels app from an Android device other than Teams panels device?**  
Teams panels app on the Teams panels device runs on Android operating system. However, you can't simply download this app and run it on any Android devices. You need to purchase devices which are certified by Microsoft.

**Can I change the device settings available for my Teams panels device?**

All users can access device settings, such as **About**, **Accessibility**, **Reboot**, and **Privacy policy** that are displayed under the **Device settings** pane (Tap **Settings** icon on the Home screen > **Device settings**). However, you should be a device admin to access admin settings. Device settings are specific to the OEM. Refer to OEM documentation to know more about them. -->

## Known issues
<!--Gary to provide list of known issues and their workarounds-->