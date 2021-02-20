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

# Microsoft Teams panels

Microsoft Teams panels are compact digital display devices that are mounted right outside of your meeting spaces. These touch screen panels are dedicated Microsoft Teams devices that provide at-a-glance view about your meeting space and the scheduled meeting. With the vibrant color-coded LED and Home screen indicators, you can determine if the space is available or reserved even from a distance. You can use Teams panels to reserve an available room for an ad-hoc meeting, on the go.

Teams panels are come pre-integrated with Microsoft Teams and display meeting details that are scheduled through Outlook or Teams calendars. 

This article is intended for both end users and admins, and provides guidance on how to perform different actions right from the mounted Teams panels devices.

This article also provides answers to the frequently asked questions about the Teams panels device. 

For an overview of Teams panels devices, and how to plan, deliver, and manage them in your organization, see [Deploy Microsoft Teams panels](teams-panels.md).

## Teams panels end-user experience
As Teams panels devices are touchscreens, you can tap, scroll, type, or simply view different areas on the [Home screen](#teams-panels-home-screen) to perform various actions:

- View meeting space and meeting details
- View upcoming reservations and space availability
- Reserve an available meeting space on the go
- Report a problem

## Teams panels Home screen
Home screen is the main visual interface that is displayed on your Teams panels.  

From the Home screen, you can view location and meeting details, reserve a space, view upcoming reservations and easily identify current availability status.

The following screenshot shows different areas on the Home screen: 

:::image type="content" source="../media/panels-home-screen-explanation.png" alt-text="This screenshot displays different areas on the Teams panels Home screen":::

Refer to the following table for a description of each area:

Area | Description
:---|:---
**1-Current time, day, date, and meeting space details** | Displays current time, day, date, and meeting space name.  
**2-Meeting space availability and meeting details** | Indicates meeting space availability and displays meeting details. See [Meeting space availability and meeting details pane](#meeting-space-availability-and-meeting-details-pane).
**3-Upcoming Calendar** | Displays the meeting space calendar and availability for up to 24 hours from the current time. You can scroll down to view the upcoming calendar of the meeting space. 
**4-Settings icon** | Opens the **Settings** pane. In the 

### Meeting space availability and meeting details pane
The appearance of this pane and its capabilities differ depending on the space availability and type of reservation.

**Meeting space is reserved for a scheduled meeting**  
If the meeting space is reserved for a scheduled meeting (scheduled either via Outlook or Teams), the pane appears in purple and displays meeting title in prominent text, meeting start and end times, and meeting organizer's name. If it's a Teams meeting, the Teams logo also appears. With meeting details prominently displayed, attendees can easily confirm they’re in the right room, at the right time, and for the right meeting.

:::image type="content" source="../media/panels-right-pane-scheduled-meeting.png" alt-text="Teams panels Home screen showing that the meeting space is reserved for a scheduled meeting":::

**Meeting space is reserved for an ad hoc meeting**  
If the meeting space is [reserved for an ad hoc meeting](#reserve-meeting-spaces-for-ad-hoc-meetings), the pane appears in purple and displays **Reserved** in prominent text, and meeting start and end times. Meeting spaces reserved via Teams panels (instead of Outlook or Teams calendars), automatically schedules the meeting as Teams meeting and displays the Teams logo on the pane.

:::image type="content" source="../media/panels-right-pane-reserved-adhoc.png" alt-text="Teams panels Home screen appears showing that the meeting space is reserved for an ad hoc meeting":::

**Meeting space is available**  
If the meeting space is available, the pane appears in green, and displays **Available** in prominent text. A **Reserve** button also appears, which you can tap to [reserve the meeting space for an ad hoc meeting](#reserve-meeting-spaces-for-ad-hoc-meetings).
 
:::image type="content" source="../media/panels-right-pane-available-status.png" alt-text="This screenshot shows how the Teams panels Home screen appears when the meeting space is available":::

## Reserve meeting spaces for ad hoc meetings

You can reserve an [available meeting space](#meeting-space-is-available) from the panels itself for an ad-hoc meeting. Ad hoc meetings are automatically scheduled as Teams meetings. However, once the meeting space is reserved for an ad-doc meeting, you cannot release or unreserve the meeting space from the panels itself. Only admins of the device's resource account can cancel the meeting (via Outlook or Teams calendar) to unreserve the space.

The start time for an ad-hoc meeting is always the current time and it can be scheduled until the next scheduled meeting or up to 24 hours, whichever is earlier. However, you cannot reserve a meeting space for less than five minutes.
 
To reserve an available meeting space for an ad hoc meeting:

1. On the Home screen, tap the **Reserve** button.
    :::image type="content" source="../media/panels-reserve.png" alt-text="Teams panels Home screen showing the Reserve button":::
2. In the **Ad hoc meeting** pane, review the available end time choices. You can use the right arrow to see additional times.

    > [!Note]

    > - The end time choices are displayed in 15-minute increments.
    > - The default end time depends on the difference between the current time and the next 15-minute interval. If the difference is less than five minutes, the default end time skips the nearest 15-minute interval, instead displays the next. For example, if the current time is 1:57 PM (which is less than five minutes from 2:00 PM), the default end time displays as 2:15 PM, and not 2 PM. This prevents users to schedule meetings for 5 minutes or less.
 
3. Tap the desired end time to select it, and tap **Reserve**

    :::image type="content" source="../media/panels-reserve-endtime.png" alt-text="Ad hoc meeting pane showing end time slots":::

    A confirmation window appears showing a thumbs up emoji, meeting start and end time, and meeting space name. The right pane on the Home screen now appears in purple, displaying **Reserved** text and the Teams logo, to indicate that the space is reserved for a Teams meeting.
  
    :::image type="content" source="../media/panels-right-pane-reserved-adhoc.png" alt-text="Ad hoc meeting pane with meeting end time selected":::

If this meeting space is a Microsoft Teams Room, you can join this Teams meeting in the in-room Microsoft Teams Room or Surface Hub devices.

<!--To learn more, check out [Get started with Teams displays](https://support.microsoft.com/office/get-started-with-teams-displays-ff299825-7f13-4528-96c2-1d3437e6d4e6).-->

### Report a problem
To report an issue with the device or the meeting space, or if there's any feedback that you'd like to give, use the **Setting** icon on the Home screen.

1. Tap the **Settings** gear icon on the Home screen.
   The **Settings** pane is displayed.
2. Tap the **Report an issue** option.
   The **Send Feedback** pane opens in a form format.
3. From the **Type** dropdown, select the desired option.
4. From the **Issue** dropdown, select the desired option.
5. In the **Title** text field, type the title using the device keypad.
6. In the text field below **Title**, type additional details, if required.

> [!NOTE]
> Do not include any personally identifiable information.

7. Review your entries and tap **Send**.
The admin who manages the device's resource account will receive an email with all the details.

## Teams panels admin experience
Admins of the Teams app on the Teams panels device are the users who manage the [resource account of the device](teams-panels.md\#resource-account-provisioning). Teams app admins of the Teams panels can perform all the functions mentioned in the end-user experience section, and much more.

Any Teams app settings that you update right from the device, apply only to that particular device. To manage the Teams app settings across multiple devices in your organization, use [Microsoft Teams admin center](device-management.md).


In order to modify any admin-specific settings, you must also be the admin of the device. All Teams admin specific settings are available behind the device admin password. This prevents end users to access admin settings. admin-specific functions, tap the **Settings** icon on the Home screen > tap **Device Settings** > **Admin Settings**.

Your Teams panels devices provide two types of admin settings. Only device admins can access the **Admin Settings** interface on the device. End users don't have access to the admin settings available on the device.

- Admin settings specific to the device: These are OEM specific settings. Refer to your OEM's documentation for more information.
- Admin settings specific to the Panels app: These are Teams panels app specific settings. These settings are available behind the device admin login. Hence, you must have admin login credentials for both the device and the Teams app in order to access the Teams panels app settings.

### Access Panels App Settings
To access **Panels App Settings**:
1. Tap the **Settings** icon on the Home screen.
2. On the **Settings** pane, tap **Device settings**.
3. On the **Device Settings** pane, tap **Admin Settings**.
  The **Admin Settings** window appears to enter your device admin password.

:::image type="content" source="../media/panels-admin-settings-password.png" alt-text="Admin Settings window to enter admin password of the device":::

4. Enter the admin password of the device and tap **Log In**.
The **Admin Settings** pane is displayed.
5. Scroll down to find **Panels App Settings** option. Tap it.
6. Tap the **Panels App Settings** button on the right pane.
The pane with the available Panels app settings is displayed.

:::image type="content" source="../media/panels-app-settings-pane.png" alt-text="This screenshot displays the pane with the available Panels app settings":::

You can update the following panels app settings:
- Wallpaper: To change the Home screen wallpaper image
- LED indicator: To change the LED color to indicate busy or reserved state

#### Update the wallpaper
1. [Acess **Panels App Settings**](#access-panels-app-settings).
2. Tap **Wallpapers**.
3. From **Choose your image**, select an image to set as the Home screen background image. The **Background** pane displays the preview of the image. 

:::image type="content" source="../media/panels-wallpapers-setting.png" alt-text="This screenshot displays the the wallpaper settings pane":::

4. Go back to the Home screen and verify that the wallpaper is updated.

#### Change the busy state LED color
Admins can choose either red or puruple as the LED color to indicate a busy state or that the meeting space is reserved.

1. [Acess **Panels App Settings**](#access-panels-app-settings).
2. Tap **LED Settings**.
3. Select your desired color option.

:::image type="content" source="../media/panels-led-settings.png" alt-text="This screenshot displays the the LED color busy state settings":::

4. Go back to the Home screen to verify if the LED color for busy state is updated.


## Frequently asked questions
Find answers to frequently asked questions about Teams panels.

**How far in the future can I see the room’s scheduling details?**  
You can see a room’s scheduling details for up to 24 hours in the future from the current time.

**Can I use Teams panels device to reserve a room for a future meeting on the fly?**  
No, you cannot reserve a meeting space for a future time by using the Teams panels device. The start time is always the current time to reserve an available meeting space.

**For how long can I reserve an available meeting space for an ad hoc meeting?**  
You can reserve an available meeting space starting from your current time until the next scheduled meeting time, or up to a maximum of 24 hours from your current time, whichever is earlier. For example, if the current time is 10 AM, and the device displays the next scheduled meeting at 2 PM, you can reserve the meeting space from 10 AM until 2 PM.

<!--**Can I run Teams panels app from an Android device other than Teams panels device?**  
Teams panels app on the Teams panels device runs on Android operating system. However, you can't simply download this app and run it on any Android devices. You need to purchase devices which are certified by Microsoft.-->

**I can see a number of device settings when I tap **Settings** icon > Device settings. Can I change them?**  
Device settings displayed under the **Device settings** pane are specific to Original Equipment Manufacturer (OEM). Refer to the OEM documentation to learn more about those device settings and how to change them.

## Known issues
<!--Gary to provide list of known issues and their workarounds-->