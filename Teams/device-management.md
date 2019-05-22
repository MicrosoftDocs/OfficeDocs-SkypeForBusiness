---
title: Manage your devices in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 11/12/2018
ms.topic: article
ms.service: msteams
ms.reviewer: kelsawi
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
f1keywords: 
- ms.teamsadmincenter.devicemanagement.overview
- ms.teamsadmincenter.managedevices.overview
description: Learn how to manage devices used with Teams in your organization. 
localization_priority: Normal
appliesto: 
- Microsoft Teams
---

# Manage your devices in Microsoft Teams

::: zone target="docs"
As an admin, you manage all devices used with Teams in your organization from the Microsoft Teams & Skype for Business admin center. You can view and manage the device inventory for your organization and do tasks such as update, restart, and monitor diagnostics for devices. You can also create and assign configuration profiles to a device or groups of devices. 

## What devices can you manage?
Devices must be certified for Teams and enrolled in Teams. A device is automatically enrolled the first time a user signs in to Teams on the device. For a list of certified devices that can be managed, see [Conference phones](https://products.office.com/en-us/microsoft-teams/across-devices/devices/category?devicetype=16) and [Desk phones](https://products.office.com/en-us/microsoft-teams/across-devices/devices/category?devicetype=34).

> [!NOTE]
> If you have Microsoft Intune, devices are automatically enrolled in Intune. After a device is enrolled, device compliance is confirmed and conditional access policies are applied to the device. 

## Manage devices in Teams

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. In the left navigation, go to **Devices** > **Manage Devices**.
2. Select **All devices**.  

::: zone-end

 From here, you can view and manage all devices enrolled in Teams in your organization. Information that you'll see for each device includes device name, manufacturer, model, user, status, action, last seen, and history. You can customize the view to show the information that fits your needs.

 Here's some examples of how you can manage Teams devices in your organization.  
    
|To do this...  |Do this |
|---------|---------|
|Change device information   | Select a device > **Edit**. You can edit details such as device name, user information, asset tag, and add notes.     |
|Manage software updates   |Select a device > **Update**. You can view the list of software and firmware updates available for the device and choose the updates to install.    |
|Restart a device   |Select a device > **Restart**.          |
|View device history  | Select a device > **History**. You can view the update history for the device.     |
|View diagnostics  | Select a device > **Diagnostics**.        |

## Use configuration profiles in Teams

Use configuration profiles to manage settings and features for Teams devices in your organization. You can create or upload configuration profiles to include settings and features you want to enable or disable and then assign a profile to a device or groups of devices. 

### Create a configuration profile

::: zone target="docs"

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) Using the Microsoft Teams & Skype for Business admin center

1. In the left navigation, go to **Devices** > **Manage Devices**.

::: zone-end

2. Select **Configuration profiles**, and then select **New configuration profile**.
3. Enter a name for the profile and if you want, add a friendly description.
4. Specify the settings you want for the profile, and then click **Save**.

### Assign a configuration profile

::: zone target="docs"

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) Using the Microsoft Teams & Skype for Business admin center

1. In the left navigation, go to **Devices** > **Manage Devices**.

::: zone-end

2. Select **Configuration profile**, and then under **Assigned to** in the profile you want to assign, click the link.  
3. In the **Assign devices to a configuration profile** pane, search for and select the devices you want to assign.
4. Click **Save**.
