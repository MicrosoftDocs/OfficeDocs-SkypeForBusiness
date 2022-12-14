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

Only firmware versions that have been tested by Microsoft are available for automatic or manual update via the Teams admin center. Firmware versions tested by Microsoft are labeled **Verified by Microsoft**. Firmware versions that haven't been tested by Microsoft are labeled **Unknown version**. Devices running an unknown firmware version can't be automatically updated; these devices can only be manually updated.

To manage devices, you need to be a Global admin, Teams Service admin, or Teams Device admin. For more information about admin roles, see [Use Microsoft Teams administrator roles to manage Teams](../using-admin-roles.md).

## Assign devices to an automatic update phase

Assigning devices to an automatic update phase is a Teams Rooms Pro feature for Teams Rooms on Android devices. Devices with a Teams Rooms Basic license will be assigned to the General phase. Any pre-configured phase will be maintained, and no further change will be allowed. For more information, see [Microsoft Teams Rooms licenses](../rooms/rooms-licensing.md).  

Automatic updates of Teams devices using the Teams admin center isn't available in GCC High. Organizations in GCC High can, however, [manually update Teams devices](#manually-update-remote-devices) using the Teams admin center.

> [!IMPORTANT]
> The automatic update feature is currently in early release. Updates might be deployed more slowly than the phase you selected. Over the next few months, the speed at which updates are automatically deployed will increase until they reach the phase you've selected.

> [!NOTE]
> Some devices don't support automatic firmware updates yet. Applying automatic firmware update settings on devices that don't support automatic updates won't have any affect on those devices. For questions about whether your device will support automatic firmware updates, contact your device manufacturer.
>
> Updates are applied on weekends and outside typical business hours to avoid disruptions. Devices within a phase will be updated gradually over a few weeks rather than all at once.

To choose the automatic update phase for your devices, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams devices** and then select **Phones**, **Displays**, **Panels**, or **Teams Rooms on Android**.  
3. Select one or more devices and then select **Update**.
4. Under **Firmware auto-update**, select one of the following:
    - **Test** This option is best for lab or test devices on which you can carry out any validation you need to perform. Updates start deployment as soon as the latest firmware version is released. Previously called **As soon as possible**.
    - **General** This is the default option and is best for most of your general-purpose devices. Updates start deployment only after 30 days have elapsed from the release of the new firmware version. Previously called **Defer by 30 days**.
    - **Final** This option is best for devices used by VIPs and in large settings after large-scale validation has been completed. Updates start deployment only after 90 days have elapsed from the release of the new firmware version. Previously called **Defer by 90 days**.
5. Select **Update**.

To see which phase devices are in, see the **Firmware auto-update** column in the Teams admin center. To see which devices are part of a specific phase, use the **Filter** option with the **Auto-update phase** parameter.

To revert a device firmware update, you need to reset your device to its factory settings. Reset your device using the instructions from its manufacturer.  

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
