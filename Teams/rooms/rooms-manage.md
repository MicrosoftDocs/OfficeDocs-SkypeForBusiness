---
title: "Manage Microsoft Teams Rooms"
ms.author: dstrome
author: dstrome
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
f1.keywords:
- NOCSH
localization_priority: Normal
ms.assetid: 39d7dc65-22c3-400f-91f1-87ed2fd792b6
ms.collection: 
  - M365-collaboration
description: Learn about how to develop and execute ongoing maintenance and operations to ensure that your Microsoft Teams Rooms systems are available for your users.
ms.custom: seo-marvel-apr2020
---

# Manage Microsoft Teams Rooms

If you have Microsoft Teams Rooms-certified devices in your organization, you have flexible management options.  You can manage the devices yourself in the same central location where you manage all you Teams solutions, Microsoft Teams Admin Center or you can transfer management responsibility to dedicated experts using [Microsoft Teams Rooms Managed Services](https://portal.rooms.microsoft.com).  You can also delegate management access to a partner of your choice for either of the options.

With Microsoft Teams Admin Center, you can:

- Perform device management like restarting or blocking devices, and downloading device logs
- Apply Teams-specific settings
- Check the health status of Microsoft Teams Room devices and their peripherals, including cameras, displays, microphones, and so on
- Review current and past meeting activity (such as details about call quality, network health and connectivity, and number of participants)
- See peripherals (such as cameras and projectors) connected to a Microsoft Teams Room device

To manage Teams Rooms devices, open the [Microsoft Teams admin center](https://admin.teams.microsoft.com) and go to **Devices** > **Teams Rooms**.

:::image type="content" source="../media/teams-rooms-summary.png" alt-text="Teams Rooms summary pages in Teams admin center":::

> [!IMPORTANT]
> To manage devices using the Teams admin center, you need to be assigned the Global Administrator, Teams Service Administrator or Teams Device Administrator roles.

## Make changes to Teams Rooms devices

If you have more than one Teams Rooms device, you can do most actions on multiple devices at the same time. For example, you can set Teams app settings on all of your devices at the same time.

### Device settings

You can change settings on one or more devices in your organization. To change settings, select the device or devices you want to manage and then select **Edit Settings**. A new pane will open with all of the settings you can change on your devices. The following table lists the settings you can change using the Teams admin center. Some settings are only available when you select a single device.

If you select more than one device, settings that support bulk editing show the two following options.

- **Keep existing value** If you choose this option, no changes will be made to the setting on the devices you selected.
- **Replace existing value with** If you choose this option, you can update the setting on the devices you selected with the value you provide.
    > [!CAUTION]
    > Existing values on the settings you choose to update will be replaced with the value you provide. If you want to add to a list of existing values, you need to include the existing values with the value you want to add. For example, if a setting has an existing domain list of `contoso.com, fabrikam.com`, and you want to add `northwindtraders.com`, the value you need to provide would be `contoso.com, fabrikam.com, northwindtraders.com`.
    >
    > If you select multiple devices, the setting on all of the devices you select will be changed to the value you provide. If devices have different values for a setting, they'll all be updated to the same value.

| Setting                                                      | Accepted values                                        | Supports bulk edit |
|--------------------------------------------------------------|--------------------------------------------------------|--------------------|
| *Account*                                                    |                                                        |                    |
| **Email**                                                    | Email address                                          | No                 |
| **Supported meeting mode**                                   | Skype for Business (default) and Microsoft Teams<br>Skype for Business and Microsoft Teams (default)<br>Skype for Business Only|Yes|
| **Modern authentication**                                    | On<br>Off                                              | Yes                |
| **Exchange address**                                         | Email address                                          | No                 |
| **Domain\username (optional)**                               | Account domain and user name                           | No                 |
| **Configure domain**                                         | Comma-separated list                                   | Yes                |
| *Meetings*                                                   |                                                        |                    |
| **Automatic screen sharing**                                 | On<br>Off                                              | Yes                |
| **Show meeting names**                                       | On<br>Off                                              | Yes                |
| **Auto-leave if everyone else left meeting**                 | On<br>Off                                              | Yes                |
| *Device*                                                     |                                                        |                    |
| **Dual monitor mode**                                        | On<br>Off                                              | Yes                |
| **Bluetooth beaconing**                                      | On<br>Off                                              | Yes                |
| **Automatically accept proximity-based meeting invitations** | Selected<br>Unselected                                 | Yes                |
| **Send logs with feedback**                                  | On<br>Off                                              | Yes                |
| **Email address for logs and feedback**                      | Email address                                          | Yes                |
| *Peripherals*                                                |                                                        |                    |
| **Conferencing microphone**                                  | List of available microphones                          | No                 |
| **Conferencing speaker**                                     | List of available speakers                             | No                 |
| **Default volume**                                           | 0-100                                                  | No                 |
| **Default speaker**                                          | List of available speakers                             | No                 |
| **Default volume**                                           | 0-100                                                  | No                 |
| **Content camera**                                           | List of available cameras                              | No                 |
| **Content Camera Enhancements**                              | On<br>Off                                              | No                 |
| **Rotate Content Camera 180 degrees**                        | On<br>Off                                              | No                 |
| *Theming*                                                    |                                                        |                    |
|                                                              | Default<br>No theme<br>Custom<br>List of built-in themes   | Yes                |

### Device restart options

Changes to device settings will only take effect after the devices have been restarted. When you make changes that need a restart, you can choose whether to restart the devices immediately or schedule a restart. Here are the available restart options:

- **Immediate restart** If you choose this option, all of the devices you're making changes to will restart as soon as you select this option.
- **Scheduled restart** If you choose this option, you can restart the devices you're making changes to at a time that's less disruptive to your organization.
  - **Select date and time** - Choose the specific date and time to restart the device. The date and time you choose is local to the device being restarted. 
  - **Leave update for nightly reboot** Devices are restarted nightly to perform maintenance. Changes you make to devices will be applied during this restart.

> [!CAUTION]
> Devices in use at the time of a restart will become unavailable for the duration of the restart process. They'll be disconnected from in-progress meetings and won't be available to join new meetings.

### Remove or block a device

When you **remove** a device, the device is removed from your organization and no longer appears in your list of Teams Rooms devices in the Teams admin center. 

When you **block** a device, Teams no longer communicates with the device. Blocked devices won't be sent commands even if they're included in a group of devices that are being bulk-edited. It's still listed in your list of Teams Rooms devices with a status of **Blocked**.

Regardless of whether a device is blocked or removed, if it's still configured with a valid username and password, it will be automatically re-added to your Teams Rooms devices list if it connects to Microsoft 365.

To remove one or more devices, do the following:

1. Go to **Devices** > **Teams Rooms** and select the devices you want to remove.
1. Select **Remove**.

To block a device, do the following:

1. Go to **Devices** > **Teams Rooms** and select the name of the device you want to block.
1. On the device details page, select **Actions** in the top-right corner of the page.
1. Select **Block**.

To unblock a device, do the following:

1. Go to **Devices** > **Teams Rooms** and select the name of the device you want to block.
1. On the device details page, select **Actions** in the top-right corner of the page.
1. Select **Unblock**.

## Download device logs

You can download a copy of a device's diagnostic log files if requested to do so by Microsoft support. Log files are compressed into a zip file that can be downloaded from the Teams admin center.

To download logs from a Teams Rooms device to your computer, do the following:

1. Go to **Devices** > **Teams Rooms** and select the name of the device you want to download logs from.
1. Select **Download device logs**. It can take several minutes for device logs to become available.
1. Select the **History** tab and then select log file link under **Diagnostics file**. A zip file containing your device's diagnostic log files will be downloaded to your browser's default Downloads folder.

## View device information

From the Teams admin center, you an view the overall status of all devices in your organization and view details of each device individually.

### Teams Rooms system dashboard

The Teams Rooms system dashboard shows you the status and health of all of your devices at a glance.

### Device details view

To view detailed information about a device, select its name from the device list. When in details view, you can see the following information about your device:

- **Health status** Shows the overall health of the Teams Room device. Health status can be either **Healthy** or **Unhealthy**.
- **Offline since** Shows the last time Microsoft 365 was able to communicate with the device.
- **Device status** Shows the current state of the device: **Idle**, **Teams meeting**, **Skype meeting**, or **Ingest**.
- **Peripherals** Shows the peripherals connected to your Teams Room device and their health status. Health status can be either **Connected** or **Disconnected**.
- **Health** Shows detailed information about the peripherals connected to your Teams Room device, network connectivity, sign in status to required services, and software version information.
- **Details** Shows manufacturer information, network IP address, and Teams Room device serial/MAC address.
- **Activity** Shows past meeting details including date and time of the meeting, number of participants, duration, and audio quality. For more information about meeting details, see the [Meeting activity details](#meeting-activity-details) section later in this article.
- **History** Shows a history of management activity on the Teams Room device, including configuration updates, device restarts, and device log download links.

#### Meeting activity details

The **Activity** tab in Teams Room device details shows high-level and detailed information about all of the meetings the device has participated in over time. In the **Activity** tab, you can see when a meeting was held, how many participants attended the meeting, and the quality of audio during the meeting.

:::image type="content" source="../media/teams-rooms-meeting-activity-summary.png" alt-text="Teams Room device activity summary list":::

To see the detail information about a specific meeting, select the date and time of the meeting you want more information about. If a meeting has only two participants, you'll see the participant details page, otherwise you'll see a participant summary page.

##### Participant summary

The participant summary page shows all of the participants that attended the meeting. You can see when each participant joined the meeting, their name, audio quality, and what features were used during their session. To view the details of a participant's session, select the session start time for that participant.

:::image type="content" source="../media/teams-rooms-meeting-activity-participant-summary.png" alt-text="Teams Room device conference details":::

##### Participant details

The participant details page shows end-to-end diagnostic information for that participant's session. As shown in the following graphic, **Device**, **System**, and **Connectivity** information is provided for the participant and for the Teams Rooms device. **Network** diagnostic information between the participant and the Teams Rooms device is also provided. Select the icon for the context you want more information about. For additional diagnostic information, select the **Advanced** tab.

:::image type="content" source="../media/teams-rooms-meeting-activity-participant-details.png" alt-text="Teams Room device call details":::
