---
title: Manage Microsoft Teams Rooms
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: ayerragangu
ms.date: 08/21/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.assetid: 39d7dc65-22c3-400f-91f1-87ed2fd792b6
description: Learn about how to develop and execute ongoing maintenance and operations to ensure that your Microsoft Teams Rooms systems are available for your users.
ms.custom: seo-marvel-apr2020
---

# Manage Microsoft Teams Rooms and Surface Hubs

If you have Microsoft Teams Rooms device or a Surface Hub in your organization, you have flexible management options.  You can manage the devices yourself in the same central location where you manage all your Teams solutions, Microsoft Teams admin center or in Teams Rooms Pro Management.

With Microsoft Teams admin center, you can:

- Perform device management like restarting devices and downloading device logs
- Apply Teams-specific settings
- Check the health status of Microsoft Teams Rooms and their peripherals, including cameras, displays, microphones, and so on
- Review current and past meeting activity (such as details about call quality, network health and connectivity, and number of participants)
- See peripherals (such as cameras and projectors) connected to Microsoft Teams Rooms (only for Teams Rooms on Windows)

To manage Teams Rooms devices in Teams Room Pro Management, see [Microsoft Teams Rooms Pro Management Portal](rooms-pro-rbac.md)

To manage Teams Rooms devices in Teams Admin Center, open the [Microsoft Teams admin center](https://admin.teams.microsoft.com) and go to **Teams Devices** > **Teams Rooms on Windows** or **Surface Hubs**.

:::image type="content" source="../media/teams-rooms-summary2.png" alt-text="Teams Rooms summary page in Teams admin center.":::

> [!IMPORTANT]
> To manage devices using the Teams admin center, you need to be assigned Teams Administrator or Teams Devices Administrator roles.

 To manage devices using Teams Rooms Pro management, see [Role-based access control in the Microsoft Teams Rooms Pro Management Portal](/microsoftteams/rooms/rooms-pro-rbac).

## Make changes to Teams Rooms devices or Surface Hubs

If you have more than one Teams Rooms or Surface Hub device, you can do most actions on multiple devices at the same time. For example, you can set Teams app settings on all of your Teams Rooms at the same time.

### Device settings

You can change settings on one or more Teams Rooms or Surface Hubs in your organization. To change settings, select the device or devices you want to manage and then select **Edit Settings**. A new pane will open with all of the settings you can change. The following table lists the settings you can change using the Teams admin center. Some settings are only available when you select a single Teams Rooms.

If you select more than one, settings that support bulk editing show the two following options.

- **Keep existing value** If you choose this option, no changes will be made to the setting on the Teams Rooms you selected.
- **Replace existing value with** If you choose this option, you can update the setting on the Teams Rooms you selected with the value you provide.
    > [!CAUTION]
    > Existing values on the settings you choose to update will be replaced with the value you provide. If you want to add to a list of existing values, you need to include the existing values with the value you want to add. For example, if a setting has an existing domain list of `contoso.com, fabrikam.com`, and you want to add `northwindtraders.com`, the value you need to provide would be `contoso.com, fabrikam.com, northwindtraders.com`.
    >
    > If you select multiple Teams Rooms, the setting on all of the devices you select will be changed to the value you provide. If Teams Rooms have different values for a setting, they'll all be updated to the same value.

| Setting                                                      | Accepted values                                        | Supports bulk edit | Supported device types |
|--------------------------------------------------------------|--------------------------------------------------------|--------------------|------------------------|
| *Account*                                                    |                                                        |                    | Teams Rooms on Windows |
| **Email**                                                    | Email address                                          | No                 | Teams Rooms on Windows |
| **Supported meeting mode**                                   | Microsoft Teams only<br>Skype for Business (default) and Microsoft Teams<br>Skype for Business and Microsoft Teams (default)<br>Skype for Business Only|Yes| Teams Rooms on Windows |
| **Modern authentication**                                    | On<br>Off                                              | Yes                | Teams Rooms on Windows |
| **Exchange address**                                         | Email address                                          | No                 | Teams Rooms on Windows |
| **Domain\username (optional)**                               | Account domain and user name                           | No                 | Teams Rooms on Windows |
| **Configure domain**                                         | Comma-separated list                                   | Yes                | Teams Rooms on Windows |
| *Meetings*                                                   |                                                        |                    | Teams Rooms on Windows, Surface Hubs |
| **Automatic screen sharing**                                 | On<br>Off                                              | Yes                | Teams Rooms on Windows |
| **HDMI ingest audio sharing**                                 | On<br>Off                                              | Yes                | Teams Rooms on Windows |
| **Show meeting names**                                       | On<br>Off                                              | Yes                | Teams Rooms on Windows |
| **Auto-leave if everyone else left meeting**                 | On<br>Off                                              | Yes                | Teams Rooms on Windows |
| **Join third-party meetings**                 | Cisco Webex<br>Zoom                                              | Yes                | Teams Rooms on Windows, Surface Hubs |
| **Join with room info**                 | Selected<br>Unselected                                              | Yes                | Teams Rooms on Windows, Surface Hubs |
| **Join with custom info**                 | Selected<br>Unselected                                              | Yes                | Teams Rooms on Windows |
| **Name (required)**                 | Name of room or space                                              | Yes                | Teams Rooms on Windows |
| **Email (required)**                 | Email address                                              | Yes                | Teams Rooms on Windows |
| *Device*                                                     |                                                        |                    | Teams Rooms on Windows |
| **Dual monitor mode**                                        | On<br>Off                                              | Yes                | Teams Rooms on Windows |
| **Allow content duplication** | Selected<br>Unselected                                 | Yes                | Teams Rooms on Windows |
| **Bluetooth beaconing**                                      | On<br>Off                                              | Yes                | Teams Rooms on Windows, Surface Hubs |
| **Automatically accept proximity-based meeting invitations** | Selected<br>Unselected                                 | Yes                | Teams Rooms on Windows, Surface Hubs |
| **Send logs with feedback**                                  | On<br>Off                                              | Yes                | Teams Rooms on Windows |
| **Email address for logs and feedback**                      | Email address                                          | Yes                | Teams Rooms on Windows |
| *Coordinate Meetings*                                                     |                                                        |                    | Teams Rooms on Windows |
| **Coordinated Meetings** | On<br>Off                                 | No                | Teams Rooms on Windows, Surface Hubs |
| **Turn on this device’s microphone** | On<br>Off                                 | No                | Teams Rooms on Windows, Surface Hubs |
| **Let people enable when joining a meeting** | Selected<br>Unselected                                 | No                | Teams Rooms on Windows, Surface hubs |
| **Turn on this device’s camera** | On<br>Off                                 | No                | Teams Rooms on Windows, Surface Hubs |
| **Let people enable when joining a meeting** | Selected<br>Unselected                                 | No                | Teams Rooms on Windows, Surface Hubs |
| **Turn on whiteboarding for this device** | On<br>Off                                 | No                | Teams Rooms on Windows, Surface Hubs |
| **Trusted device accounts (separate with commas)** | List of devices                              | No                | Teams Rooms on Windows, Surface Hubs |
| *Peripherals*                                                |                                                        |                    | Teams Rooms on Windows |
| **Conferencing microphone**                                  | List of available microphones                          | No                 | Teams Rooms on Windows |
| **Conferencing speaker**                                     | List of available speakers                             | No                 | Teams Rooms on Windows |
| **Default volume**                                           | 0-100                                                  | No                 | Teams Rooms on Windows |
| **Default speaker**                                          | List of available speakers                             | No                 | Teams Rooms on Windows |
| **Default volume**                                           | 0-100                                                  | No                 | Teams Rooms on Windows |
| **Content camera**                                           | List of available cameras                              | No                 | Teams Rooms on Windows |
| **Content Camera Enhancements**                              | On<br>Off                                              | No                 | Teams Rooms on Windows |
| **Rotate Content Camera 180 degrees**                        | On<br>Off                                              | No                 | Teams Rooms on Windows |
| *Theming*                                                    |                                                        |                    | Teams Rooms on Windows |
|                                                              | Default<br>No theme<br>Custom<br>List of built-in themes   | Yes                | Teams Rooms on Windows |

See [Manage Microsoft Teams configuration on Surface Hubs](surface-hub-manage-config.md) for more options to configure Surface Hubs.

### Front row layout settings

Front row is meeting view layout option for Teams Rooms on Windows.

| Teams device | App version | Front of room display |
|--------------|-------------|-----------------------|
|Microsoft Teams Rooms on Windows | 4.11.12.0 or higher (The latest version is recommended) | Supports single and dual displays; Minimum size: 46 inches; Aspect ratio 16:9 with 1920x1080 resolution (single and dual display modes) or 21:9 with 2560x1080 resolution (single display mode); All displays should be set at 100% scaling in Windows settings |

See [Microsoft Teams Rooms maintenance and operations](rooms-operations.md#display-resolution-and-scaling), to adjust your display settings to meet Front row's requirements.

To learn how to set Front row as the default layout for a room, or how to turn it off, see [Remotely configure front row on Teams Rooms](manage-front-row.md).

See [Known issues](known-issues.md#Limits) for more information on managing Front row.

## Device restart options

Changes to device settings will only take effect after the device has been restarted. When you make changes that need a restart, you can choose whether to restart immediately or schedule a restart. Here are the available restart options:

- **Immediate restart** If you choose this option, all of the devices you're making changes to will restart as soon as you select this option.
- **Scheduled restart** If you choose this option, you can restart the devices you're making changes to at a time that's less disruptive to your organization.
  - **Select date and time** - Choose the specific date and time to restart the device. The date and time you choose is local to the device being restarted.
  - **Leave update for nightly reboot** Devices are restarted nightly to perform maintenance. Changes you make to devices will be applied during this restart.

> [!CAUTION]
> Teams Rooms and Surface Hubs that are in use at the time of a restart will become unavailable for the duration of the restart process. They'll be disconnected from in-progress meetings and won't be available to join new meetings while the device is restarting.

## Remove device

When you remove a device, the device is removed from your organization and no longer appears in your list of Teams Rooms on Windows or Surface Hubs in the Teams admin center.

If you remove a device and it's still configured with a valid username and password, it will be automatically re-added to your list of Teams Rooms or Surface Hubs if it connects to Microsoft 365 again.

To remove one or more devices, do the following:

1. Go to **Teams Devices** > **Teams Rooms on Windows** or **Surface Hubs** and select the devices you want to remove.
2. Select **Remove**.

## Download device logs

You can download a copy of a device's diagnostic log files if requested to do so by Microsoft support. Log files are compressed into a zip file that can be downloaded from the Teams admin center.

To download logs from a Teams Rooms device to your computer, do the following:

1. Go to **Teams Devices** > **Teams Rooms on Windows** or **Surface Hubs** and select the name of the device you want to download logs from.
1. Select **Download device logs**. It can take several minutes for device logs to become available.
1. Select the **History** tab and then select log file link under **Diagnostics file**. A zip file containing your device's diagnostic log files will be downloaded to your browser's default Downloads folder.

## View device information

From the Teams admin center, you can view the overall status of all devices in your organization and view details of each device individually.

### Teams Rooms system dashboard

The Teams Rooms system dashboard shows you the status and health of all of your devices at a glance.

### Device details view

To view detailed information about a device, select its name from the device list. When in details view, you can see the following information about your device:

- **Health status** Shows the overall health of the Teams Rooms or Surface Hub device. Health status can be either **Healthy**, **Non-urgent**, **Critical**, or **Offline**.
- **Offline since** Shows the last time Microsoft 365 was able to communicate with the device.
- **Usage status** Shows the current state of the device: **Idle**, **Busy**, or **Unavailable**. Only for Teams Rooms on Windows.
- **Peripherals** Shows the peripherals connected to your Teams Rooms device and their health status. Health status can be either **Connected** or **Disconnected**. Only for Teams Rooms on Windows.
- **Health** Shows detailed information about the peripherals connected to your Teams Rooms device, network connectivity, sign in status to required services, and software version information.
- **Details** Shows manufacturer information, network IP address, and Teams Rooms device serial/MAC address.
- **Activity** Shows past meeting details including date and time of the meeting, number of participants, duration, and audio quality. For more information about meeting details, see the [Meeting activity details](#meeting-activity-details) section later in this article.
- **History** Shows a history of management activity on the Teams Rooms or Surface Hub device, including configuration updates, device restarts, and device log download links.

#### Meeting activity details

The **Activity** tab in device details shows high-level and detailed information about all of the meetings the device has participated in over time. In the **Activity** tab, you can see when a meeting was held, how many participants attended the meeting, and the quality of audio during the meeting.

:::image type="content" source="../media/teams-rooms-meeting-activity-summary.png" alt-text="Teams Rooms device activity summary list.":::

To see the detail information about a specific meeting, select the date and time of the meeting you want more information about. If a meeting has only two participants, you'll see the participant details page, otherwise you'll see a participant summary page.

##### Participant summary

The participant summary page shows all of the participants that attended the meeting. You can see when each participant joined the meeting, their name, audio quality, and what features were used during their session. To view the details of a participant's session, select the session start time for that participant.

:::image type="content" source="../media/teams-rooms-meeting-activity-participant-summary.png" alt-text="Teams Rooms device conference details.":::

##### Participant details

The participant details page shows end-to-end diagnostic information for that participant's session. As shown in the following graphic, **Device**, **System**, and **Connectivity** information is provided for the participant and for the Teams Rooms device. **Network** diagnostic information between the participant and the Teams Rooms device is also provided. Select the icon for the context you want more information about. For additional diagnostic information, select the **Advanced** tab.

:::image type="content" source="../media/teams-rooms-meeting-activity-participant-details.png" alt-text="Teams Rooms device call details.":::

[https://learn.microsoft.com/en-us/microsoftteams/rooms/rooms-pro-rbac]: https://learn.microsoft.com/en-us/microsoftteams/rooms/rooms-pro-rbac
