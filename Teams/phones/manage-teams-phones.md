---
title: Manage Teams phones
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: srpall
ms.date: 10/16/2024
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
description: Manage Teams phones you deployed in your organization.
ms.localizationpriority: medium
search.appverid: MET150
---

# Manage Teams phones

You can manage Teams phones used with Microsoft Teams in your organization from Microsoft Teams admin center. You can view and manage the device inventory for your organization and do tasks such as update, restart, and monitor diagnostics for devices. You can also create and assign configuration profiles to a device or groups of devices.

To manage your phones, such as change device configuration, restart devices, manage updates, or view device and peripheral health, you need to be assigned one of the following Microsoft 365 admin roles:

- Teams Service admin
- Teams Device admin

For more information about admin roles in Teams, see [Use Teams administrator roles to manage Teams](../using-admin-roles.md).

## What Teams phones can you manage?

You can manage any Teams phone certified for, and enrolled in, Teams. Each Teams phone is automatically enrolled the first time it's signed into Teams on the device. For a list of certified devices that can be managed, see: [Certified Teams phones](/microsoftteams/devices/teams-phones-certified-hardware)

To manage Teams phones, in the left navigation of the [Microsoft Teams admin center](https://admin.teams.microsoft.com), go to **Teams Devices**, and then select **Phones**.

## Manage Teams phones

In the Teams admin center, you can view and manage phones enrolled in Teams in your organization. Information that you'll see for each device includes device name, manufacturer, model, user, status, action, last seen, and history. You can customize the view to show the information that fits your needs. Teams Phones are automatically enrolled in Microsoft Intune if you've signed up for it. After a device is enrolled, device compliance is confirmed and conditional access policies are applied to the device.

Here are some examples of how you can manage phones in your organization.  

| **Task**                           | **Action**                                                                                                                                                                                                                                                                                                     |
|-----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Change device information               | Select a device > **Edit**. You can edit details such as device name, asset tag, and add notes.                                                                                                                                                                                                              |
| Manage software updates                 | Select a device > **Update**. You can view the list of software and firmware updates available for the device and choose the updates to install. For more information about updating devices, see [Update Teams devices remotely](../devices/remote-update.md)                                                          |
| Assign or change configuration policies | Select one or more devices > **Assign configuration**.                                                                                                                                                                                                                                                       |
| Add or remove device tags               | Select one or more devices > **Manage tags**. For more information about device tags, see [Manage Teams device tags](../devices/manage-device-tags.md).                                                                                                                                                                 |
| Restart devices                         | Select one or more devices > **Restart**.                                                                                                                                                                                                                                                                    |
| Filter devices using device tags        | Select the filter icon, select the **Tag** field, specify a device tag to filter on, and select **Apply**. For more information about filtering devices using device tags, see [Use filters to return devices with a specific tag](../devices/manage-device-tags.md#use-filters-to-return-devices-with-a-specific-tag). |
|Schedule device actions|Actions like **Restart** and **Software update** can be scheduled for the preferred date and time.|
| View device history and diagnostics     | Under the **History** column, select the **View** link for a device to view its update history and diagnostic details.                                                                                                                                                                                         |
|View device action details|In the **History** tab on the device page, select the action status to view the details of the action.|
|Cancel device actions|From the **History** section, you can cancel any action that is in a Queued or Scheduled state (not in progress or completed) to prevent execution. This option is accessible from the **History** tab in the device page and the **History** column in the list page. You can select multiple actions to cancel at once. Paired actions are canceled together if execution didn't start.|
|Actions on multiple devices|You can select multiple devices from the list page and perform an action on them at once. This is applicable for **Restart**, **Software update**, **Assign configuration**, **Manage tags**, **Remove device**, and **Sign-out**.|

This video shows how to search for Teams devices.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE5fHGQ?autoplay=false]

### View issues with Teams phones

You can view issues with Teams phones in the health status column of the device list.

In addition to the health status of the device, the following issues are also surfaced in the health status column:

1. **Sign-in errors exist** - There was an issue signing in to the device. Select the health status of the device to view the time the sign-in failure occurred, the account that attempted to sign into the device, the reason for the failure, and a history of previous sign-in failures.
2. **No connection** - The connection between Teams admin center and the device was lost. Restart or update the device through Teams admin center to resolve this error.
3. **Multiple issues** - One or more errors exist. Select the health status of the device to view the list of issues.

> [!NOTE]
> If you don't see any issues for a device you're having trouble with, make sure the device's firmware is on the latest version.

### Use configuration profiles in Teams

Use configuration profiles to manage settings and features for different Teams phones in your organization. You can create or upload configuration profiles to include settings and features you want to enable or disable, and then assign a profile to a device or set of devices.

#### Create a configuration profile

To create a configuration profile for a Teams device type:

1. In the left navigation, go to **Teams Devices** > **Phone** > **Configuration profiles** to create a new configuration profile for Teams phone.
2. Select **Add**.
3. Enter a name for the profile and optionally add a friendly description.
4. Specify the settings you want for the profile, and then Select **Save**.
   The newly created configuration profile is displayed in the list of profiles.

#### Assign a configuration profile

After creating a configuration profile for a Teams device type, assign it to one or more devices.

1. In the left navigation, go to **Teams Devices** > **Phones**.
2. Select one or more devices, and then Select **Assign configuration**.  
3. In the **Assign a configuration** pane, search for configuration profile to assign to the selected devices.
4. Select **Apply**.
   For the devices to which you applied the configuration policy, the **Action** column displays **Config Update** and the **Configuration profile** column displays the configuration profile name.
