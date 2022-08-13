---
title: How to use Microsoft Teams panels devices
ms.author: dstrome
author: dstrome
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
  - Teams_ITAdmin_Devices
search.appverid: MET150
ms.localizationpriority: medium
description: This article provides guidance on how to use Teams panels devices.
---

# How to use Microsoft Teams panels

Microsoft Teams panels are compact digital display devices that are mounted right outside of your meeting spaces, typically next to entrances. These touchscreen panels are dedicated Microsoft Teams devices that provide at-a-glance view about your meeting space and the scheduled meeting. With the vibrant color-coded LED and Home screen indicators, you can determine if the space is available or reserved from a distance. You can use Teams panels to reserve an available meeting space for an ad hoc meeting, on the spot.

Teams panels devices come preinstalled with Microsoft Teams and display meeting details that are scheduled through Outlook or Teams calendars.

This article provides guidance, to both end users and admins, on how to use the Teams panels devices. It also provides answers to the [frequently asked questions](#frequently-asked-questions) about using these devices.

For an overview of the panels devices, and the guidance on how to plan, deliver, and manage them in your organization, see [Deploy Microsoft Teams panels](teams-panels.md).

For a quick start, check out [Get started with Teams panels](https://support.microsoft.com/office/get-started-with-teams-panels-fa5e85d1-7ff3-4f11-b0b0-277e2302c8be).

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

The following screenshot shows different parts or tiles on the Teams panels Home screen:

:::image type="content" source="../media/panels-home-screen-explanation.png" alt-text="This screenshot displays different areas on the Teams panels Home screen.":::

Refer to the following table for a description of each tile:

Tile | Description
:---|:---
**1-Current time, day, date, and meeting space details** | Displays current time, day, date, and meeting space name. The meeting space name is the name of the resource account that signed in to panels.
**2-Meeting space availability and meeting details** | Indicates meeting space availability and displays meeting details. See [Meeting space availability and meeting details tile](#meeting-space-availability-and-meeting-details-tile).
**3-Upcoming Calendar** | Displays the meeting space calendar and availability for up to 24 hours from the current hour. Scroll up or down to determine which time slots are available and which are reserved.
**4-Settings** | Displays the **Settings** icon. Tap it to report a problem or update available device settings.

### Meeting space availability and meeting details tile

The appearance of this tile and its capabilities vary depending on the meeting space availability and type of reservation.

#### Meeting space is reserved for a scheduled meeting

The tile appears in purple for a meeting space that is reserved for a scheduled meeting (scheduled via Outlook or Teams). It displays meeting title in prominent text, meeting start and end times, and meeting organizer's name. For a Teams meeting, the Teams logo also appears. With meeting details prominently displayed, attendees can easily confirm they’re in the right meeting space, at the right time, and for the right meeting.

:::image type="content" source="../media/panels-right-tile-scheduled-meeting.png" alt-text="Teams panels Home screen showing that the meeting space is reserved for a scheduled meeting.":::

> [!NOTE]
>
> - After you schedule a meeting, it can take up to 90 seconds for the calendar to sync and reflect it on the panels screen.
> - For a [scheduled meeting that is marked as private](https://support.microsoft.com/office/make-an-appointment-or-meeting-private-dc3898f0-22f5-45c6-8cc8-b4d4db84111d), **Private meeting** is displayed instead of the actual meeting title.

#### Meeting space is reserved for an ad hoc meeting

The tile appears in purple for a meeting space that is [reserved for an ad hoc meeting](#reserve-meeting-spaces-for-ad-hoc-meetings). It displays **Reserved** in prominent text along with the meeting start and end times. Ad-hoc meetings are automatically scheduled as Teams meetings, hence the Teams logo always appears on the screen.

:::image type="content" source="../media/panels-right-tile-reserved-adhoc.png" alt-text="Teams panels Home screen showing that the meeting space is reserved for an ad hoc meeting.":::

#### Meeting space is available

The tile appears in green for an available meeting space. It displays **Available** in prominent text, and a **Reserve** button also appears that you can tap to [reserve the meeting space for an ad hoc meeting](#reserve-meeting-spaces-for-ad-hoc-meetings). You can check the upcoming calendar of the meeting space (right bottom tile) to decide the end time for your ad hoc meeting.

:::image type="content" source="../media/panels-right-tile-available-status.png" alt-text="This screenshot shows how the Teams panels Home screen appears when the meeting space is available.":::

## Reserve meeting spaces for ad hoc meetings

You can reserve an [available meeting space](#meeting-space-is-available) directly from panels for an ad hoc meeting. All ad hoc meetings are automatically scheduled as Teams meetings. However, once reserved, you can't release or unreserve that meeting space through panels. Only admins of the device's resource account can cancel the ad hoc meeting (via Outlook or Teams calendar) to unreserve the space.

For ad hoc meetings that are booked directly from panels:

- The start time is always the current time and as such you can't schedule it for a future time.
- The end time can be until the next scheduled meeting or up to 24 hours from the current hour, whichever is earlier. Check the **Upcoming Calendar** tile on the Home screen to determine the time slots during which the meeting space is available or booked.

To reserve an available meeting space for an ad hoc meeting:

1. On the Home screen, tap the **Reserve** button.
    :::image type="content" source="../media/panels-reserve.png" alt-text="Teams panels Home screen showing the Reserve button.":::
2. In the **Ad hoc meeting** screen, review the available end time choices. You can use the right or left arrows to browse the available end time choices.

    :::image type="content" source="../media/panels-reserve-endtime.png" alt-text="Ad hoc meeting screen showing end time slots.":::

    > [!Note]
    >
    > - The end time choices are displayed in 15-minute intervals of an hour.
    > - The end time defaults to the next 15-minute interval that is at least five minutes after the current time. For example, if the current time is 1:57 PM, the default end time displays as 2:15 PM, and not 2:00 PM. This prevents users from booking the space for five minutes or less. In the above screenshot, the default end time displays as 2:00 PM, which is the next 15-minute interval that is at least five minutes after the current time (1:53 PM).
    > - An exception to the above rule is when the start time of the next meeting is within five minutes from the current time. In such cases, you can book the space until the next meeting start time. For example, if the current time is 1:57 PM and the next meeting start time is 2:00 PM, then 2:00 PM displays as the only end time option and you can reserve the space for three minutes.

3. Tap the desired end time interval, and then tap **Reserve**.

    A confirmation window appears with a thumbs up emoji, meeting start and end time, and meeting space name.
    :::image type="content" source="../media/panels-reserve-confirmation.png" alt-text="Ad hoc meeting confirmation message.":::
The right tile on the Home screen now appears in purple and displays the **Reserved** text and the Teams logo. This indicates that the meeting space is now reserved for an ad hoc Teams meeting.
  
    :::image type="content" source="../media/panels-right-tile-reserved-adhoc.png" alt-text="Home screen showing that meeting space is reserved for an ad hoc meeting.":::

    > [!NOTE]
    > If the meeting space is a Microsoft Teams Room, you can _join_ this Teams meeting with the in-room Microsoft Teams Rooms or Surface Hub devices.

### Report a problem

To report an issue with the device or the meeting space, to request a feature update, or to provide any feedback, use the **Setting** icon on the Home screen.

1. Tap the **Settings** gear icon on the Home screen.

2. Tap the **Report an issue** option.

    The **Send Feedback** screen is displayed in a form format.
3. From the **Type** dropdown, select the type of request.
4. From the **Issue** dropdown, select the category.
5. In the **Title** text field, type the title using the panels keypad.
6. In the text field below **Title**, type additional details, if necessary.

    > [!NOTE]
    > Do not include any personally identifiable information.

7. Review your entries and tap **Send**.

### View or update a device setting

There are several device settings, such as about, accessibility, reboot, and privacy policy that you can view or update directly from panels. The available device settings may differ based on the Original Equipment Manufacturer (OEM) of your device. For information on settings specific to your device, see the OEM documentation.

To view or update a device setting:

1. Tap the **Settings** icon on the Home screen.
2. In the **Settings** screen, tap **Device settings**.
3. In the **Device Settings** screen, tap the setting that you want to view or update.
4. Follow the prompt on the screen to view or update the setting.

## Teams panels admin experience

If you're the admin of [Teams panel's resource account](teams-panels.md\#resource-account-provisioning), then you're also the admin of **Panels App** on the device. As the **Panels App** admin, you can do all the functions that are mentioned in the [end-user experience](#teams-panels-end-user-experience) section, in addition to managing the **Panels App** settings on the device.

Your panels devices provide two types of admin settings. You must be a device admin to access the available admin settings. End users can't access these settings.

- Admin settings that are specific to the device, such as display, time and date, language, bluetooth, WiFi, and so on. Refer to the OEM documentation to know more about these settings.
- Admin settings that are specific to **Panels App** on your device, such as wallpaper and LED indicator color. Only an admin of **Panels App** can access these settings. Since **Panels App** settings are available as part of admin settings, you must have admin sign in credentials for both the device and **Panels App** to access **Panels App** settings.

> [!NOTE]
> Any updates to the **Panels App** settings done via the device are applicable only to that specific device. Those updates will not impact other panels devices in your organization. For example, if you change the Home screen wallpaper image from the **Panels App** settings, the wallpaper image will change only for that specific device.

### Access Panels App settings

You can access **Panels App**-specific settings by using the **Panels App Settings** option under the admin settings. The steps to access **Panels App Settings** may differ based on the OEM of your device.

To access the **Panels App Settings** option:

1. Tap the **Settings** icon on the Home screen.
2. On the **Settings** screen, tap **Device settings**.
3. Tap the **Admin Settings**.

    > [!NOTE]
    > Depending on the OEM of your device, you may need to enter the device admin password now or after the next step.

4. Scroll down to find the **Panels App Settings** option. Tap it.
5. Tap the **Panels App Settings** button on the right screen.
    The screen with the available **Panels App** settings is displayed.

    :::image type="content" source="../media/panels-app-settings-screen.png" alt-text="This screenshot displays the screen with the available Panels app settings.":::

    Use this screen to update the following **Panels App** settings for your device:

    - [Wallpaper](#update-the-wallpaper)
    - [LED indicator](#change-the-busy-state-led-color)

#### Pair a Teams panel with a Microsoft Teams Rooms on Android

To pair a Teams panel and Teams Rooms on Android, both devices must be signed into the same resource account.

On the Teams panel, sign in using your admin credentials.

1. Go to **Settings > Device Settings > Admin Settings > Panels App Settings > Meetings > Device Pairing.**

2. A six-digit code will appear on the Teams Rooms on Android front of room display. Enter the code on the Teams Panel.  

#### Meeting check-in and room release

Check-in and room release settings let users check in to a meeting on Teams Panels at the room they reserved at the start of the meeting. If a user doesn’t check-in within a set amount of time after the meeting start time, the room is released and becomes available for others to reserve.

When Teams Panels is paired with a Microsoft Teams Rooms on Android, check-in notifications can be enabled to appear on the front-of-room display when meetings run late.

To enable check-in and room release, see [Check-in and room release on Microsoft Teams Panels](check-in-and-room-release.md).

#### Room capacity warning

Teams panels that are paired with a Teams Rooms on Android can display a warning message when a meeting room is at or over capacity. To use this feature, the Teams Rooms must have a camera that supports people counting. Teams Rooms on Android support room capacity warnings without a Teams panel.

Room capacity warnings are turned off by default. To turn the setting on from the Teams panel, first [pair a Teams panel with a Microsoft Teams Rooms on Android](#pair-a-teams-panel-with-a-microsoft-teams-room-on-android). The panel and the Teams Rooms must be signed into the same resource account.

 Then, go to **Settings > Device settings > Admin settings > Panel app settings**. Then, under **Meetings**, turn on **Max room occupancy notification**.

#### View room equipment

When this feature is turned on, end-users can view what equipment is available in a space on a Teams panel.

This feature is off by default, and it can be enabled per device. To turn it on, use [Set-Place](/powershell/module/exchange/set-place?view=exchange-ps) in PowerShell to configure the display names for `AudioDeviceName`, `DisplayDeviceName`, `VideoDeviceName`, `Tags`, and `IsWheelChairAccessible`.

Or, you can enable this feature in the Exchange admin center. See [Edit a resource](/exchange/recipients-in-exchange-online/manage-resource-mailboxes#edit-a-resource) for more information.



#### Update the wallpaper

Change the Home screen wallpaper image.

1. [Access **Panels App Settings**](#access-panels-app-settings).
2. Tap **Wallpapers**.
3. From **Choose your image**, select an image to set as the Home screen background image. Preview the selected image under **Background**.
:::image type="content" source="../media/panels-wallpapers-setting.png" alt-text="This screenshot displays the wallpaper settings screen.":::
4. Go back to the Home screen and verify that the wallpaper is updated.

#### Change the busy state LED color

Admins can choose either red or purple as the LED color to indicate that the meeting space is busy or reserved. The LED color to indicate an available space is always green and can't be changed.

1. [Access **Panels App Settings**](#access-panels-app-settings).
2. Tap **LED Settings**.
3. From **Choose your LED color**, select the desired color.
:::image type="content" source="../media/panels-led-settings.png" alt-text="This screenshot displays the LED color busy state settings.":::
4. Go back to the Home screen and verify that the LED color for the busy state is updated. If the meeting space is currently available, try to schedule a test meeting to verify the change in LED color for the busy state.

## Frequently asked questions

Find answers to frequently asked questions about the Teams panels devices.

**How far in the future can I see the scheduling details of a meeting space?**  
In the **Upcoming Calendar** tile (bottom right) on the Home screen, you can see the scheduling details of a meeting space for up to 24 hours in the future from the current hour.

**Can I reserve a meeting space for a future time from the Teams panels device?**  
No, you can't reserve a meeting space for a future time from panels. The start time is always the current time for an ad hoc meeting scheduled from panels.

**How long I can reserve an available meeting space for an ad hoc meeting?**  
You can reserve an available meeting space starting from your current time until the next scheduled meeting time, or up to a maximum of 24 hours from your current hour, whichever is earlier. For example, if the current time is 10 AM, and the next meeting start time is 2 PM, you can reserve the meeting space from 10 AM until 2 PM.
