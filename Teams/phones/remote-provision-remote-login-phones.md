---
title: Remote provisioning and sign in for Teams phones
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: vapati
ms.date: 10/17/2024
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to remotely provision and sign in to Teams phones that are deployed in your organization.
---

# Remote provisioning and sign in for Teams phones

IT admins can remotely provision and sign in to a Teams Android device includiong Teams phones. To provision a Teams pohone remotely, the admin needs to upload the MAC IDs of the devices being provisioned and create a verification code. The entire process can be completed remotely from the Teams admin center.

> [!NOTE]
> Once you've signed in to a Teams phone, this feature isn't available. To use it again, the device must be reset to factory default settings.

## Supported devices

All Android and SIP devices certified by Microsoft can be provisioned remotely from Teams admin center.

Refer to the following for the list of certified hardware:

Teams phones - [Certified Teams phones](../devices/teams-phones-certified-hardware.md)
Teams panels - [Certified Teams panels](../devices/teams-panels-certified-hardware.md)
Microsoft Teams Rooms on Android - [Teams Rooms on Android certified devices](../devices/certified-hardware-android.md?tabs=Android)
SIP devices - [Teams compatible devices](./sip-gateway-plan.md#compatible-devices)

## Add a device MAC address

Complete the following steps to provision a new device.

1. Sign in to the Teams admin center.
2. Expand **Teams Devices**.
3. Select **Provision new device** from the **Actions** tab.

In the **Provision new devices** window, you can either add the MAC address manually or upload a file.

### Manually add a device MAC address

1. From the **Waiting on activation** tab, select **Add MAC ID**.

   :::image type="content" alt-text="Screenshot of 'Add MAC address' for manually adding a the MAC address for a device." source="../media/remote-provision-6-new.png" lightbox="../media/remote-provision-6-new.png":::

1. Enter the MAC ID.
1. Enter a location, which helps technicians identify where to install the devices.
1. Select **Apply** when finished.

### Upload a file to add a device MAC address

1. From the **Waiting on activation** tab, select **Upload MAC IDs**.
2. Download the file template.
3. Enter the MAC ID and location, and then save the file.
4. **Select file**, and then select **Upload**.

## Generate a verification code

You need a verification code for the devices. The verification code is generated in bulk or at the device level and is valid for 24 hours.

1. From the **Waiting on activation** tab, select an existing MAC ID.
   A password is created for the MAC address and is shown in the **Verification Code** column.

2. Provide the list of MAC IDs and verification codes to the field technicians. You can export the detail directly in a file and share the file with the technician who is doing the actual installation work.

## Provision the device

When the device is powered on and connected to the network, the technician provisions the device. These steps are completed on the Teams device.

1. The technician selects **Provision device** from the **Settings**.  

   ![Provision new device option from the Actions tab.](../media/provision-device1.png)
  
2. The technician enters the device-specific verification code in the provided input field.

   ![Provision new device verification.](../media/provision-device-verification1.png)

   Once the device is provisioned successfully, the tenant name appears on the sign-in page.

   ![Tenant name on sign-in page.](../media/provision-code.png)

## First time remote sign in

The provisioned device appears in the **Waiting for sign in** tab. Start the remote sign-in process by selecting the individual device.

1. Select a device from the **Waiting for sign in** tab.

   ![The window with a list of devices ready for sign in.](../media/remote-device1.png)

2. Follow the instructions in **Sign in a user**, and then select **Close**.

   ![The Sign in a user window for individual device.](../media/sign-in-user.png)

   This video shows how admins can remotely provision Android-based and SIP devices.

   > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE5fRYe?autoplay=false]

## Related articles

- [Manage your devices in Teams](../rooms/device-management.md)
- [Remote sign in and sign out](../devices/remote-sign-in-and-sign-out.md)
- [Update Teams devices remotely](../devices/remote-update.md)

