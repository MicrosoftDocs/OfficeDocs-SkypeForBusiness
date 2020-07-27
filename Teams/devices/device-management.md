---
title: Manage your devices in Microsoft Teams
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: kelsawi
ms.collection: 
  - M365-collaboration
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.managedevices.overview
  - ms.teamsadmincenter.devicemanagement.overview
description: Learn how to manage devices used with Teams in your organization.
localization_priority: Normal
search.appverid: MET150
appliesto: 
  - Microsoft Teams
---

# Manage your devices in Microsoft Teams

As an admin, you can manage devices used with Microsoft Teams in your organization from the Microsoft Teams admin center. You can view and manage the device inventory for your organization and do tasks such as update, restart, and monitor diagnostics for devices. You can also create and assign configuration profiles to a device or groups of devices.

## What devices can you manage?

You can manage any device that's certified for, and enrolled in, Teams. A device is automatically enrolled the first time a user signs into Teams on the device. For a list of certified devices that can be managed, see:

- [Microsoft Teams Rooms](https://www.microsoft.com/microsoft-365/microsoft-teams/across-devices/devices/category?devicetype=20)
- [Conference phones](https://products.office.com/microsoft-teams/across-devices/devices/category?devicetype=73)
- [Desk phones](https://products.office.com/microsoft-teams/across-devices/devices/category?devicetype=34)
- [Collaboration bars](https://www.microsoft.com/microsoft-365/microsoft-teams/across-devices/devices/category?devicetype=16)

These devices are managed in the [Microsoft Teams admin center](https://admin.teams.microsoft.com) and have their own respective sections in the left navigation under **Devices**. This lets you manage each type of device separately.

## Manage Teams Rooms devices

You can use the Teams admin center to view and remotely manage your Teams Rooms devices across your organization. The Teams admin center makes it easy to see, at a glance, which devices are healthy and which need attention, and lets you focus on specific devices to see detailed information about device health, meeting performance, call quality, and peripherals. 

Here are some things you can do to manage your Teams Rooms devices. Teams Rooms devices can be found in the [Microsoft Teams admin center](https://admin.teams.microsoft.com) under **Devices** > **Teams Rooms**.

For details about how to manage your Teams Rooms devices, see [Manage Microsoft Teams Rooms](../rooms/rooms-manage.md).

| To do this... | Do this|
|---------------|--------|
| Change settings on one or more devices | Select one or more devices > **Edit settings**. If you select multiple devices, the values you change will replace the values on all the selected devices. |
| Restart devices | Select one or more devices > **Restart**. When you restart a device, you can choose whether to restart the device immediately or select **Schedule restart** to restart the device at a specific date and time. The date and time you select are local to the device being restarted.|
| View meeting activity | Select a device name to open device details > **Activity**. When you open the **Activity** tab, you can see all the meetings that the device has participated in. This summary view shows the meeting start time, the number of participants, its duration, and the overall call quality.|
| View meeting details |  Select a device name to open device details > **Activity** > select a meeting. When you open a meeting's details, you can see all of the participants in the meeting, how long they were in the call, the Teams session types, and their individual call quality. If you want to see technical information about a participant's call, select the participant's call start time.|


## Manage phones and collaboration bars in Teams

In the Teams admin center, you can view and manage phones and collaboration bars enrolled in Teams in your organization. Information that you'll see for each device includes device name, manufacturer, model, user, status, action, last seen, and history. You can customize the view to show the information that fits your needs.

Phones and collaboration bars are automatically enrolled in Microsoft Intune, if you've signed up for it. After a device is enrolled, device compliance is confirmed and conditional access policies are applied to the device.

Here are some examples of how you can manage phones and collaboration bars in your organization.  
    
|To do this...  |Do this |
|---------|---------|
|Change device information   | Select a device > **Edit**. You can edit details such as device name, asset tag, and add notes.     |
|Manage software updates   |Select a device > **Update**. You can view the list of software and firmware updates available for the device and choose the updates to install. For more information about updating devices, see [Update Microsoft Teams devices remotely](remote-update.md)   |
|Restart a device   |Select a device > **Restart**.          |
|View device history  | Select a device > **History**. You can view the update history for the device.     |
|View diagnostics  | Select a device > **Diagnostics**.        |

### Use configuration profiles in Teams

Use configuration profiles to manage settings and features for Teams phones and collaboration bars in your organization. You can create or upload configuration profiles to include settings and features you want to enable or disable and then assign a profile to a device or groups of devices. 

#### Create a configuration profile

1. In the left navigation, go to **Devices** > **Configuration profiles**.
2. Click **Add**.
3. Enter a name for the profile and if you want, add a friendly description.
4. Specify the settings you want for the profile, and then click **Save**.

#### Assign a configuration profile

1. In the left navigation, go to **Devices** > **Configuration profiles**.
2. Select the **Configuration profile** you want to assign, and then click **Assign to device**.  
3. In the **Assign devices to a configuration profile** pane, search for and select the devices you want to assign.
4. Click **Save**.

