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
  - seo-marvel-apr2020
description: In this article, learn how to manage devices like conference or desk phones used with Teams in your organization.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
---

# Manage your devices in Microsoft Teams

As an admin, you can manage devices used with Teams in your organization from the Microsoft Teams admin center. You can view and manage the device inventory for your organization and do tasks such as update, restart, and monitor diagnostics for devices. You can also create and assign configuration profiles to a device or groups of devices. 

## What devices can you manage?
You can manage any device that's certified for, and enrolled in, Teams. A device is automatically enrolled the first time a user signs in to Teams on the device. For a list of certified devices that can be managed, see:

- [Conference phones](https://products.office.com/microsoft-teams/across-devices/devices/category?devicetype=16)
- [Desk phones](https://products.office.com/microsoft-teams/across-devices/devices/category?devicetype=34)
- Collaboration bars

Devices are managed in the [Microsoft Teams admin center](https://admin.teams.microsoft.com) under **Devices** in the left navigation.

> [!NOTE]
> If you have Microsoft Intune, devices are automatically enrolled in Intune. After a device is enrolled, device compliance is confirmed and conditional access policies are applied to the device.

## Manage phones and collaboration bars in Teams

Even though phones and collaboration bars are managed the same in the Microsoft Teams admin center, they have their own respective sections in the left navigation under **Devices**. This lets you manage each type of device separately.

From here, you can view and manage phones and collaboration bars enrolled in Teams in your organization. Information that you'll see for each device includes device name, manufacturer, model, user, status, action, last seen, and history. You can customize the view to show the information that fits your needs.

Here's some examples of how you can manage Teams devices in your organization.  
    
|To do this...  |Do this |
|---------|---------|
|Change device information   | Select a device > **Edit**. You can edit details such as device name, asset tag, and add notes.     |
|Manage software updates   |Select a device > **Update**. You can view the list of software and firmware updates available for the device and choose the updates to install.    |
|Restart a device   |Select a device > **Restart**.          |
|View device history  | Select a device > **History**. You can view the update history for the device.     |
|View diagnostics  | Select a device > **Diagnostics**.        |

## Use configuration profiles in Teams

Use configuration profiles to manage settings and features for Teams devices in your organization. You can create or upload configuration profiles to include settings and features you want to enable or disable and then assign a profile to a device or groups of devices. 

### Create a configuration profile

1. In the left navigation, go to **Devices** > **Configuration profiles**.
2. Click **Add**.
3. Enter a name for the profile and if you want, add a friendly description.
4. Specify the settings you want for the profile, and then click **Save**.

### Assign a configuration profile

1. In the left navigation, go to **Devices** > **Configuration profiles**.
2. Select the **Configuration profile** you want to assign, and then click **Assign to device**.  
3. In the **Assign devices to a configuration profile** pane, search for and select the devices you want to assign.
4. Click **Save**.
