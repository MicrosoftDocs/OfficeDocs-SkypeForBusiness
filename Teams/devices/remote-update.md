---
title: "Update Microsoft Teams devices remotely"
ms.author: czawideh
author: cazawideh
ms.reviewer: rahulmi
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
ms.localizationpriority: medium
description: "Update Microsoft Teams phones, Teams panels, and collaboration bars remotely using the Teams admin center"
---

# Update Microsoft Teams devices remotely

Using the Microsoft Teams admin center, you can update your Teams devices, such as Teams phones, Teams panels, and collaboration bars, remotely, and you can choose device firmware automatic-update behavior. You can update the following on your devices using the Teams admin center:

- Teams app and teams admin agent
- Company portal app
- OEM agent app
- Device firmware

Device firmware updates can either be applied automatically or scheduled for a future date and time. Other available device updates aren't applied automatically, but can be applied manually or scheduled for a future date and time.

> [!NOTE]
> While device firmware updates can be scheduled, if the scheduled date and time falls after the configured maximum 30 or 90 day delay, the firmware update is applied when the maximum delay is reached. The scheduled date and time are ignored. Additionally, updating Microsoft Teams devices remotely is a feature not yet available on US Government Cloud tenants (GCC-High).

To manage devices, you need to be a Global admin, Teams Service admin, or Teams Device admin. For more information about admin roles, see [Use Microsoft Teams administrator roles to manage Teams](../using-admin-roles.md).

## Choose automatic device firmware update behavior

Device firmware updates are applied automatically. You can decide whether to apply updates as soon as one is released (if you choose this option, updates are applied on the first weekend after an update is released), or 30 or 90 days after an update is released. By default, device firmware updates are applied 30 days one released.

> [!IMPORTANT]
> The latest firmware update release isn't applied on your Teams device. Instead, the update that's automatically applied on your device is delayed by one version. For example, assume your device has version "10" applied, and version "11" is released. Version "11" won't be applied yet. Instead your device will only be updated to version "11" after version "12" is released.

> [!NOTE]
> Some devices don't support automatic firmware update yet. Applying automatic firmware update settings on devices that don't support automatic updates won't have any affect on those devices. For questions about whether your device will support automatic firmware updates, contact your device manufacturer.

To choose the automatic update behavior for your devices, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate **Teams Devices** > **IP phones** or **Collaboration bars** or **Teams panels**.
3. Select one or more devices and then select **Update**.
4. Under **Firmware auto-update**, select one of the following:
    - **As soon as available** Second-newest device firmware update is applied on the first weekend after the latest update is released.
    - **Defer 30 days** Second-newest device firmware update is applied 30 days after the latest update is released.
    - **Defer 90 days** Second-newest device firmware update is applied 90 days after the latest update is released.
5. Select **Update**.

If, for whatever reason, you need to revert a device firmware update, you need to reset your device to its factory settings. Reset your device using the instructions from its manufacturer.  

## Manually update remote devices

When you update one or more devices using the admin center, you can decide whether to update the devices immediately or schedule an update for a future date and time.

To manually update remote devices, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate  **Teams Devices** > **IP phones** or **Collaboration bars** or **Teams panels**.
3. Select one or more devices and then select **Update**.
4. Under **Manual updates**, select **Schedule** if you want to schedule the update for a future date and time. The updates are applied at the date and time in the timezone selected in **Timezone**.

What you'll see depends on whether you have one, or multiple, devices selected. The left image below shows multiple devices selected while the image on the right shows a single device selected.

:::image type="content" source="../media/device-update-status.png" alt-text="Single and multiple device views in device update status pane.":::

When you select multiple devices, you can choose which update types to apply to each selected device. Select the update types you want to apply and select **Update**.

When you select a single device, updates that are available for the device are shown. If multiple update types are available for the device, select each update type to apply. You can view the **Current version** applied on the device and the **New version** that will be applied. Select the update(s) you want to apply and select **Update**.

After you select **Update**, updates are applied to your devices at the date and time you selected if you scheduled an update. If you didn't select a future date and time, updates are applied to your devices within a few minutes.
