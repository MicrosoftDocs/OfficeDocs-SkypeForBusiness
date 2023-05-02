---
title: Update Microsoft Teams devices remotely
ms.author: dstrome
author: dstrome
ms.reviewer: rahulmi
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Devices
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: Update Microsoft Teams phones, Teams panels, and Teams Rooms on Android, devices remotely using the Teams admin center.
---

# Update Microsoft Teams devices remotely

Using the Microsoft Teams admin center, you can update your Teams devices, such as Teams phones, Teams panels, and Teams Rooms on Android, remotely. The following software components on your device can be updated from the Teams admin center:

- Teams app
- Device firmware

Device firmware updates happen automatically by default. You can, however, update firmware and other software components manually. When applying updates manually, they can be applied immediately or scheduled for a future date and time.

Only firmware versions that have been tested by Microsoft are available for automatic or manual update via the Teams admin center. Firmware versions tested by Microsoft are labeled **Verified by Microsoft**. Sometimes, an early version of the firmware may also be made available to customers which will be labeled as **Microsoft Preview**. Devices can be manually updated to these early versions and devices running on these versions will also be eligible for receiving automatic updates in future. Firmware versions that haven't been tested by Microsoft are labeled **Unknown version**. Devices running an unknown firmware version can't be automatically updated; these devices can only be manually updated.

To manage devices, you need to be a Global admin, Teams Service admin, or Teams Device admin. For more information about admin roles, see [Use Microsoft Teams administrator roles to manage Teams](../using-admin-roles.md).

## Automatic updates

### Assign devices to update phases

Assigning devices to an automatic update phase is a Teams Rooms Pro feature for Teams Rooms on Android devices. Devices with a Teams Rooms Basic license will be assigned to the General phase. Any pre-configured phase will be maintained, and no further change will be allowed. For more information, see [Microsoft Teams Rooms licenses](../rooms/rooms-licensing.md).  

Automatic updates of Teams devices using the Teams admin center isn't available in GCC High. Organizations in GCC High can, however, [manually update Teams devices](#manually-update-remote-devices) using the Teams admin center.

> [!NOTE]
> Some devices don't support automatic firmware updates yet. Applying automatic firmware update settings on devices that don't support automatic updates won't have any effect on those devices. For questions about whether your device will support automatic firmware updates, contact your device manufacturer.
>
> Updates are applied on weekends and outside typical business hours to avoid disruptions. Devices within a phase will be updated gradually over a few weeks rather than all at once.

To choose the automatic update phase for your devices, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams devices** and then select **Phones**, **Displays**, **Panels**, or **Teams Rooms on Android**.  
3. Select one or more devices and then select **Update**.
4. Under **Firmware auto-update**, select one of the following:
    - **Validation** This option is best for lab or test devices on which you can carry out any validation you need to perform. Updates start deployment as soon as the latest firmware version is released. Previously called **As soon as possible**.
    - **General** This is the default option and is best for most of your general-purpose devices. Updates start deployment only after 30 days have elapsed from the release of the new firmware version. Previously called **Defer by 30 days**.
    - **Final** This option is best for devices used by VIPs and in large settings after large-scale validation has been completed. Updates start deployment only after 90 days have elapsed from the release of the new firmware version. Previously called **Defer by 90 days**.
5. Select **Update**.

To see which phase devices are in, see the **Firmware auto-update** column in the Teams admin center. To see which devices are part of a specific phase, use the **Filter** option with the **Auto-update phase** parameter.

To revert a device firmware update, you need to reset your device to its factory settings. Reset your device using the instructions from its manufacturer.  

### Track automatic updates

If you want to check which firmware versions are currently being rolled out for your devices, you can do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams devices** and then select **Phones**, **Displays**, **Panels**, or **Teams Rooms on Android**.
3. A new widget is added called **Software auto-updates**. The number on this widget indicates the active update paths (combination of a current version and a new version).
4. On this widget, select **View details**. A new dialogue box opens showing the list of active update paths with the following details - 
    - Device model and manufacturer
    - Current version and the new version. Devices on the specified current version will be updated to the specified new version.
        - The new version may not always be the latest available version. To ensure safe updates, devices on older versions are updated in a step-wise approach, until they reach the latest version.
    - Number of eligible devices
    - Active phase
        - Devices in this update phase are being currently updated. Any device from a previous phase that is not updated yet will also be included.

### Pause automatic updates

If you want more time to check some thing and don't want to change the update phase of the device, you can temporarily pause the automatic updates for your tenant. This will ensure that automatic updates do not happen for any device (Android-based) during the next 15 days. After that, the automatic updates resume automatically and will start getting scheduled for eligible devices again. In case, you want to resume the updates before the 15 days elapse, you can resume the updates. Following are the steps for pausing the updates:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams devices** and then select **Phones**, **Displays**, **Panels**, or **Teams Rooms on Android**.
3. Under the **Actions** menu, select **Pause auto-updates**. A dialogue box will open for confirmation.
4. Updates will automatically resume after 15 days. If you want to resume the updates before that, select **Resume auto-updates** from under the **Actions** menu.


## Manually update remote devices

If you want to manually update devices using the Teams admin center, you can decide whether to update the devices immediately or schedule an update for a future date and time.

To manually update remote devices, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate  **Teams Devices** and then select **Phones**, **Displays**, **Panels**, or **Teams Rooms on Android**.
3. Select one or more devices and then select **Update**.
4. Under **Manual updates**, select **Schedule** if you want to schedule the update for a future date and time. The updates are applied at the date and time in the timezone selected in **Timezone**.

What you'll see depends on whether you have one, or multiple, devices selected. The left image below shows multiple devices selected while the image on the right shows a single device selected.

:::image type="content" source="../media/device-update-status.png" alt-text="Single and multiple device views in device update status pane.":::

When you select multiple devices, you can choose which update types to apply to each selected device. Select the update types you want to apply and select **Update**.

When you select a single device, updates that are available for the device are shown. If multiple update types are available for the device, select each update type to apply. You can view the **Current version** applied on the device and the **New version** that will be applied. Select the update(s) you want to apply and select **Update**.

After you select **Update**, updates are applied to your devices at the date and time you selected if you scheduled an update. If you didn't select a future date and time, updates are applied to your devices within a few minutes.
