---
title: Manage devices in Microsoft Teams
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: kimmatlock
ms.date: 07/08/2024
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
ms.collection: 
  - teams-rooms-devices
  - M365-collaboration
  - m365initiative-deployteams
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.managedevices.overview
  - ms.teamsadmincenter.devicemanagement.overview
description: Manage devices used with Microsoft Teams in your organization.
ms.localizationpriority: medium
search.appverid: MET150
---

# Manage devices in Teams 

You can manage devices used with Microsoft Teams in your organization from the Microsoft Teams admin center or in Teams Rooms Pro Management. You can view and manage the device inventory for your organization and do tasks such as update, restart, and monitor diagnostics for devices. You can also create and assign configuration profiles to a device or groups of devices.

To manage devices, such as change device configuration, restart devices, manage updates, or view device and peripheral health, you need to be assigned one of the following Microsoft 365 admin roles:

- Teams Service admin
- Teams Device admin

For more information about admin roles in Teams, see [Use Teams administrator roles to manage Teams](../using-admin-roles.md).

For more information about Teams Rooms Pro management role based access control, see [Role-based access control in the Microsoft Teams Rooms Pro Management Portal](../rooms/rooms-pro-rbac.md)

## What devices can you manage?

You can manage any device that's certified for, and enrolled in, Teams. A device is automatically enrolled the first time a user signs in to Teams on the device. For a list of certified devices that can be managed, see:

- [Microsoft Teams Rooms](https://www.microsoft.com/microsoft-365/microsoft-teams/across-devices/devices/category?devicetype=20)
- [Conference phones](https://products.office.com/microsoft-teams/across-devices/devices/category?devicetype=73)
- [Desk phones](https://products.office.com/microsoft-teams/across-devices/devices/category?devicetype=34)
- [Teams displays](https://www.microsoft.com/microsoft-365/microsoft-teams/across-devices/devices/category?devicetype=34)
- [Teams panels](teams-panels.md)

To manage devices, in the left navigation of the [Microsoft Teams admin center](https://admin.teams.microsoft.com), go to **Teams Devices**, and then select the device type. Each type of device has its own respective section, which lets you manage them separately.

## Manage Teams Rooms in Teams Rooms Pro Management

To manage devices in Teams Rooms Pro Management, see [Microsoft Teams Rooms Pro Management Portal](../rooms/managed-meeting-rooms-portal.md)

## Manage Teams Rooms on Windows devices in Teams Admin Center

You can use the Teams admin center to view and remotely manage your Teams Rooms on Windows devices across your organization. The Teams admin center makes it easy to see, at a glance, which devices are healthy and which need attention, and lets you focus on specific devices to see detailed information about device health, meeting performance, call quality, and peripherals.

Here are some things you can do to manage your Teams Rooms devices. Teams Rooms devices can be found in the [Microsoft Teams admin center](https://admin.teams.microsoft.com) under **Teams Devices** > **Teams Rooms on Windows**.

For details about how to manage your Teams Rooms devices, see [Manage Microsoft Teams Rooms](../rooms/rooms-manage.md).

| To do this...                          | Do this                                                                                                                                                                                                                                                                                                                                                                          |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Change settings on one or more devices | Select one or more devices > **Edit settings**. If you select multiple devices, the values you change will replace the values on all the selected devices.                                                                                                                                                                                                                       |
| Restart devices                        | Select one or more devices > **Restart**. When you restart a device, you can choose whether to restart the device immediately or select **Schedule restart** to restart the device at a specific date and time. The date and time you select are local to the device being restarted.                                                                                            |
| View meeting activity                  | Select a device name to open device details > **Activity**. When you open the **Activity** tab, you can see all the meetings that the device has participated in. This summary view shows the meeting start time, the number of participants, its duration, and the overall call quality.                                                                                        |
| View meeting details                   | Select a device name to open device details > **Activity** > select a meeting. When you open a meeting's details, you can see all of the participants in the meeting, how long they were in the call, the Teams session types, and their individual call quality. If you want to see technical information about a participant's call, select the participant's call start time. |

## Manage phones, Teams Rooms on Android, Teams displays, and Teams panels

In the Teams admin center, you can view and manage phones, Teams Rooms on Android, Teams displays, and Teams panels enrolled in Teams in your organization. Information that you'll see for each device includes device name, manufacturer, model, user, status, action, last seen, and history. You can customize the view to show the information that fits your needs.

Phones, Teams Rooms on Android, Teams displays, and Teams panels are automatically enrolled in Microsoft Intune if you've signed up for it. After a device is enrolled, device compliance is confirmed and conditional access policies are applied to the device.

Here are some examples of how you can manage phones, Teams Rooms on Android, Teams displays, and Teams panels in your organization.  

| To do this...                           | Do this                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Change device information               | Select a device > **Edit**. You can edit details such as device name, asset tag, and add notes.                                                                                                                                                                                                              |
| Manage software updates                 | Select a device > **Update**. You can view the list of software and firmware updates available for the device and choose the updates to install. For more information about updating devices, see [Update Teams devices remotely](remote-update.md)                                                          |
| Assign or change configuration policies | Select one or more devices > **Assign configuration**.                                                                                                                                                                                                                                                       |
| Add or remove device tags               | Select one or more devices > **Manage tags**. For more information about device tags, see [Manage Teams device tags](manage-device-tags.md).                                                                                                                                                                 |
| Restart devices                         | Select one or more devices > **Restart**.                                                                                                                                                                                                                                                                    |
| Filter devices using device tags        | Select the filter icon, select the **Tag** field, specify a device tag to filter on, and select **Apply**. For more information about filtering devices using device tags, see [Use filters to return devices with a specific tag](manage-device-tags.md#use-filters-to-return-devices-with-a-specific-tag). |
|Schedule device actions|Actions like **Restart** and **Software update** can be scheduled for the preferred date and time.|
| View device history and diagnostics     | Under the **History** column, click the **View** link for a device to view its update history and diagnostic details.                                                                                                                                                                                         |
|View device action details|In the **History** tab on the device page, select the action status to view the details of the action.|
|Cancel device actions|From the **History** section, you can cancel any action that is in a Queued or Scheduled state (not in progress or completed) to prevent execution. This option is accessible from the **History** tab in the device page and the **History** column in the list page. You can select multiple actions to cancel at once. Paired actions will be canceled together if execution hasn't started.|
|Actions on multiple devices|You can select multiple devices from the list page and perform an action on them at once. This is applicable for **Restart**, **Software update**, **Assign configuration**, **Manage tags**, **Remove device**, and **Sign-out**.|

This video shows how to search for Teams devices.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE5fHGQ?autoplay=false]

### View issues with Android-based Teams devices

You can view issues with Android-based Teams devices in the health status column of the device list.

In addition to the health status of the device, the following issues are also surfaced in the health status column:

1. **Sign-in errors exist** - There was an issue signing-in to the device. Select the health status of the device to view the time the sign-in failure occurred, the account that attempted to sign into the device, the reason for the failure, and a history of previous sign-in failures.
2. **No connection** - The connection between Teams admin center and the device has been lost. Restart or update the device through Teams admin center to resolve this error.
3. **Multiple issues** - One or more errors exist. Select the health status of the device to view the list of issues.

> [!NOTE]
> If you don't see any issues for a device you're having trouble with, make sure the device's firmware is on the latest version.

### Use configuration profiles in Teams

Use configuration profiles to manage settings and features for different Teams devices in your organization, including Teams Rooms on Android, Teams displays, Teams phone, and Teams panels. You can create or upload configuration profiles to include settings and features you want to enable or disable, and then assign a profile to a device or set of devices.

#### Create a configuration profile

To create a configuration profile for a Teams device type:

1. In the left navigation, go to **Teams Devices** > select the Teams device type > **Configuration profiles**. For example, select **Teams Devices** > **Teams panels** > **Configuration profiles** to create a new configuration profile for Teams panels.
2. Click **Add**.
3. Enter a name for the profile and optionally add a friendly description.
4. Specify the settings you want for the profile, and then click **Save**.
   The newly created configuration profile is displayed in the list of profiles.

#### Assign a configuration profile

After creating a configuration profile for a Teams device type, assign it to one or more devices.

1. In the left navigation, go to **Teams Devices** > select the Teams device type. For example, to assign a configuration profile to a Teams panels device, select **Teams Devices** > **Teams panels**.
2. Select one or more devices, and then click **Assign configuration**.  
3. In the **Assign a configuration** pane, search for configuration profile to assign to the selected devices.
4. Click **Apply**.
   For the devices to which you applied the configuration policy, the **Action** column displays **Config Update** and the **Configuration profile** column displays the configuration profile name.
