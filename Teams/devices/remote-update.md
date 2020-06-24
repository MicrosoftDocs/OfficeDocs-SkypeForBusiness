---
title: "Update Microsoft Teams devices remotely"
ms.author: dstrome
author: dstrome
ms.reviewer: rahulmi
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
localization_priority: Normal
description: "Update Microsoft Teams phones and collaboration bars remotely using the Teams admin center"
---

# Update Microsoft Teams devices remotely

Using the Microsoft Teams admin center, you can update your Teams devices, such as phones and collaboration bars, remotely, and you can choose device firmware automatic-update behavior. You can update the following on your devices using the Teams admin center:

- Teams app and teams admin agent
- Company portal app
- OEM agent app
- Device firmware

Device firmware updates are applied automatically. However, you can choose whether to apply those updates to your devices as soon as they become available, or defer them for up to 90 days. Only device firmware updates can be updated automatically.

Other available device updates can be installed either immediately or at a date and time of your choosing.

> [!NOTE]
> Device firmware updates can be also be scheduled. However, you can't schedule device updates beyond 90 days from the current date. 

## Choose automatic device firmware update behavior

Device firmware updates are applied automatically. However, you can decide whether to apply these updates as soon as they're released, or 30 or 90 days after they've been released.

To choose the automatic update behavior for your devices, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com
2. Navigate  **Devices** > **Phones** or **Collaboration bars**
1. Select one or more devices and then select **Update**
1. Under **Firmware auto-update**, select one of the following:
    - **As soon as available** Device firmware updates will be applied as soon as possible after they are is released.
    - **Defer 30 days** Device firmware updates will be applied 30 days after the they are released.
    - **Defer 90 days** Device firmware updates will be applied 90 days after the they are released.
1. Select **Update**

If, for whatever reason, you need to revert a device firmware update, you need to reset your device to its factory settings. Reset your device using the instructions from the device's manufacturer.  

## Manually update remote devices

When you update one or more devices using the admin center, you can decide whether to update the devices immediately or schedule an update for a future date and time. 

To manually update remote devices, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com
2. Navigate  **Devices** > **Phones** or **Collaboration bars**
1. Select one or more devices and then select **Update**
1. Under **Manual updates**, select **Schedule** if you want to schedule the update for a future date and time. The updates will be applied at the date and time in the timezone selected in **Timezone**.

What you'll see depends on whether you have one, or multiple, devices selected. The left image below shows multiple devices selected while the image on the right shows a single device selected.

:::image type="content" source="../media/device-update-status.png" alt-text="Single and multiple device views in device update status pane":::

When you select multiple devices, you can choose which update types to apply to each selected device. Select the update types you want to apply and select **Update**.

When you select a single device, updates that are available for the device are shown. If multiple update types are available for the device, select each update type to install. You can view the **Current version** installed on the device and the **New version** that will be installed. Select the update(s) you want to apply and select **Update**.

After you select **Update**, updates will be applied to your devices at the date and time you selected if you scheduled an update. If you didn't select a future date and time, updates will be applied to your devices within a few minutes.
