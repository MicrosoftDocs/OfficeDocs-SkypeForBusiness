---
title: Update Microsoft Teams devices remotely
ms.author: tonysmit
author: tonysmit
ms.reviewer: rahulmi
ms.date: 10/04/2023
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Devices
  - Tier1
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

#### Software versions on Teams admin center

All new software versions for Teams devices are made available on Teams admin center once they are published by Microsoft. New releases may have minimum software version requirements. In such cases, the new version is only made available if the device fulfills the requirements. Ensure that the device is meeting the criteria, especially, that the firmware is updated.

Only software versions that have been tested by Microsoft are available for automatic or manual updates via the Teams admin center. Software versions tested by Microsoft are labeled **Verified by Microsoft**.

Additionally, early versions of the software may also be made available and will be labeled as **Microsoft Preview**. Devices can be manually updated to Microsoft Preview firmware, and devices running on these versions will also be eligible for receiving automatic updates in future.

Firmware versions that haven't been tested by Microsoft are labeled **Unknown version**. Devices running an unknown firmware version can't be automatically updated; these devices can only be manually updated.  
  
Refer to the following for more details on new releases and their requirements:

Phone - [Phone - Devices for Teams | Product release information](/microsoftteams/devices/teams-ip-phones#product-release-information-for-teams-phones)

Displays - [Displays - Devices for Teams | Product release information](/microsoftteams/devices/teams-ip-phones#product-release-information-for-teams-displays)

Panels - [Panels - Devices for Teams | Product release information](/microsoftteams/devices/teams-ip-phones#product-release-information-for-teams-panels)

MTRA - [MTRA - Product release information](/microsoftteams/rooms/android-app-firmware)

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

If you want to check which firmware versions are currently rolling out for your devices, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams devices** and then select **Phones**, **Displays**, **Panels**, or **Teams Rooms on Android**.
3. Refer to the widget titled **Software auto-updates** to determine the number of active update paths.
4. On this widget, select **View details**. A dialogue box opens showing the list of active update paths with the following details - 
    - Device model and manufacturer
    - Current version and new version
    - Number of eligible devices
    - Active phase
        - Devices assigned to this update phase are being currently updated. Any device from a previous phase that is not updated yet will also be included.

> [!NOTE]
> The new version may not always be the latest available version. Devices on older versions are updated in a step-wise approach, until they reach the latest version.

### Pause automatic updates

You can temporarily pause automatic updates for your tenant. When paused, Android based devices will not be automatically updated for the next 15 days. To pause the updates, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate to **Teams devices** and then select **Phones**, **Displays**, **Panels**, or **Teams Rooms on Android**.
3. Under the **Actions** menu, select **Pause auto-updates**.
4. Updates will automatically resume after 15 days. If you want to resume the updates before that, select **Resume auto-updates** from under the **Actions** menu.


## Manually update remote devices

If you want to manually update devices using the Teams admin center, you can decide whether to update the devices immediately or schedule an update for a future date and time.

To manually update remote devices, do the following:

1. Sign in to Microsoft Teams admin center by visiting https://admin.teams.microsoft.com.
2. Navigate  **Teams Devices** and then select **Phones**, **Displays**, **Panels**, or **Teams Rooms on Android**.
3. Select one or more devices and then select **Update**.
4. Under **Manual updates**, select **Schedule** if you want to schedule the update for a future date and time. The updates are applied at the date and time in the timezone selected in **Timezone**.

What you'll see depends on whether you have one, or multiple, devices selected. The left image below shows a single device selected while the image on the right shows multiple devices selected.

![Device status update panel with single and multiple devices selected.](../media/mtr-devices/update-manual-together.png)

When you select multiple devices, you can choose which update types to apply to each selected device. Select the update types you want to apply and select **Update**.

When you select a single device, updates that are available for the device are shown. If multiple update types are available for the device, select each update type to apply. You can view the **Current version** applied on the device and the **New version** that will be applied. Select the update(s) you want to apply and select **Update**.

After you select **Update**, updates are applied to your devices at the date and time you selected if you scheduled an update. If you didn't select a future date and time, updates are applied to your devices within a few minutes.


> [!NOTE]
> To manage devices, you need to be a Global admin, Teams Service admin, or Teams Device admin. For more information about admin roles, see [Use Microsoft Teams administrator roles to manage Teams](../using-admin-roles.md).


This video shows how to update Teams devices.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE5fxbK?autoplay=false]

## Frequently asked questions about automatic updates

1. **Which software components are automatically updated?**
Currently, only Firmware is automatically updated for eligible devices. Teams app needs to be updated through the [manual](#manually-update-remote-devices) approach by the administrators.

2. **What makes a device eligible to receive automatic updates?**
The following conditions should be satisfied for the device to be eligible for automatic updates:
    - Device model should be certified. Refer to [Devices for Teams](../devices/teams-ip-phones.md) and [Teams Rooms certified systems and peripherals](../rooms/certified-hardware.md?tabs=Android) for details.
    - Current version should be supported by Microsoft. Refer to [Software versions](#software-versions-on-teams-admin-center) for more details.
    - Devices on versions released before 2022 will generally not have auto-update support.

3. **How fast does the rollout happen?**
Eligible devices receive updates in weekly cycles based on the update phase they are in. For example, devices in General phase start receiving Firmware updates only after 30 days have elapsed since the new version was published. To ensure a stable rollout, the devices are updated gradually for a tenant and not all at once. Overall, the rollout of each new version takes a few weeks after the start of each update phase.

   Also, if the device is on an older version, like N-3. It will be updated step-wise to intermediate versions, like N-2 and N-1, before it is updated to the latest version (N). Therefore, this device may take longer to reach the latest version than usual, but no intervention is required.

5. **How do I check if a device has received an update?**
Whenever a device receives an update (or has one scheduled), the History tab on the device page will show corresponding details for a software update operation.

6. **I see that the updates are happening but they are failing. What do I do?**
Sometimes the updates can fail due to transient conditions. In such cases, no intervention is required. Updates will be automatically retried on the devices.
If updates are consistently failing across your inventory, you can check a few things:
    - Devices are online at the time when updates are scheduled.
    - Network configuration is done appropriately to allow download of updates. Refer to [URLs and IP address ranges for Microsoft Teams](/microsoft-365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams) for the URLs and IP address ranges that need to be allowed for Teams.
    - If this does not help, reach out to Microsoft support with the logs. Device logs can be found in the History tab of the device page as part of the Device diagnostics operation run with the software update operation.

7. **The eligible count of devices doesn't seem to match the available devices.**
The device count in **Automatic software updates** section shows the number of eligible devices that are ready to be updated. Those that have already been updated to the **New version** are not counted. It can also include devices from the previous phase that could not get updated.

8. **When do automatic updates happen?**
The updates are scheduled to happen over weekends outside of typical business hours to minimize impact. If the device is offline at that time, the updates will get executed when the device comes back online the next time.


