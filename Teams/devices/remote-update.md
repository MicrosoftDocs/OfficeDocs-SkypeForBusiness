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
description: Update Microsoft Teams phones, Teams panels, and collaboration bars remotely using the Teams admin center
---

# Update Microsoft Teams devices remotely

Using the Microsoft Teams admin center, you can update your Teams devices, such as Teams phones, Teams panels, and Teams Room for Android, remotely. You can also choose the automatic update behavior for device firmware updates. The following software components on your device can be updated from the Teams admin center:

- Teams app
- Device firmware

Device firmware updates happen automatically. However, if you prefer, firmware and other software components can be updated manually. When applying updates manually, they can be applied immediately or scheduled for a future date and time.

Only firmware versions that have been tested by Microsoft are available for automatic or manual update via the Teams admin center. Firmware versions tested by Microsoft are labeled **Verified by Microsoft**.

Firmware versions that haven't been tested by Microsoft are labeled **Unknown version**. Devices running an unknown firmware version can't be auto-updated; these devices can only be manually updated.

> [!NOTE]
> While device firmware updates can be scheduled, if the scheduled date and time falls after the configured maximum 30 or 90 day delay, the firmware update is applied when the maximum delay is reached. The scheduled date and time are ignored. Additionally, updating Microsoft Teams devices remotely is a feature not yet available on US Government Cloud tenants (GCC-High).

To manage devices, you need to be a Global admin, Teams Service admin, or Teams Device admin. For more information about admin roles, see [Use Microsoft Teams administrator roles to manage Teams](../using-admin-roles.md).

## Assign an auto-update phase to a device

Assigning a phase for auto-updates is a Teams Rooms Pro feature for Teams Rooms on Android devices. All devices with Basic license will be assigned to the General phase. Any pre-configured phase will be maintained, and no further change will be allowed. For more information on new licenses, visit Microsoft Teams Rooms license overview in Teams admin center - Microsoft Teams | Microsoft Learn.  

> [!NOTE]
> Some devices don't support automatic firmware update yet. Applying automatic firmware update settings on devices that don't support automatic updates won't have any affect on those devices. For questions about whether your device will support automatic firmware updates, contact your device manufacturer.

To choose the automatic update behavior for your devices, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams devices** and then select **Phones**, **Displays**, **Panels**, or **Teams Rooms on Android**.  
3. Select one or more devices and then select **Update**.
4. Under **Firmware auto-update**, select one of the following:
    - **Test** This option is best for lab or test devices on which you can carry out any validation you prefer. Updates start rolling out as soon as the latest firmware version is released. Previously called **As soon as possible**.
    - **General** This is the default option and is best for most of your general-purpose devices. Updates start rolling out only after 30 days have elapsed from the release of the new firmware version. Previously called **Defer by 30 days**.
    - **Final** This option is best for devices used by VIPs and in large settings after large-scale validation has been completed. Updates start rolling out only after 90 days have elapsed from the release of the new firmware version. Previously called **Defer by 90 days**.
5. Select **Update**.

To see which phase devices are in, see the **Firmware auto-update** column in the Teams admin center. To see which devices are part of a specific phase, use the **Filter** option.

To revert a device firmware update, you need to reset your device to its factory settings. Reset your device using the instructions from its manufacturer.  

> [!IMPORTANT]
> The auto-update feature is currently in early release. Updates might be released more slowly than the phase you selected. Over the next few months, the speed at which updates are automatically released will increase until they reach the phase you've selected.
>
> Updates are applied on weekends and outside typical business hours to avoid disruptions. Devices within a phase will be updated gradually over a few weeks rather than all at once.

## Manually update remote devices

When you update one or more devices using the admin center, you can decide whether to update the devices immediately or schedule an update for a future date and time.

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
