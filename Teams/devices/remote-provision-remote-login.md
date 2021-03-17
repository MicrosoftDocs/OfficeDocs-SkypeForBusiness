---
title: Remote provisioning and sign in for Teams Android devices
author: cichur
ms.author: v-cichur
manager: serdars
ms.reviewer: prgholve
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
f1.keywords:
- NOCSH
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to remote provision and sign in for Teams Android devices
---

# Remote provisioning and sign in for Teams Android devices

IT admins can remotely provision and sign in to a Teams device. To provision a device remotely, the admin needs to upload the MAC IDs of the devices being provisioned and create a verification code. The entire process can be completed remotely from the Teams admin center.

## Review the supported devices

The following list shows the device firmware requirements.

|Device category|Manufacturer|Minimum firmware|
|-|-|-|
||||

## Add a device MAC address

Complete the following steps to provision a new device.

1. Sign in to the Teams admin center.
2. Expand **Devices**.
3. Select **Provision new device** from the **Actions** tab.

In the **Provision new devices** window, you can either add the MAC address manually or upload a file.

### Manually add a device MAC address

1. From the **Awaiting Activation** tab, select **Add MAC ID**.
2. Enter the MAC ID.
3. Enter a location, which helps technicians identify where to install the devices.
4. Select **Apply** when finished.

### Upload a file to add a device MAC address

1. From the **Awaiting Activation** tab, select **Upload MAC IDs**.
2. Download the file template.
3. Enter the MAC ID and location, and then save the file.
4. **Select file**, and then select **Upload**.

## Generate a verification code

You need a verification code for the devices. The verification code is generated in bulk or at the device level and is valid for 24 hours.

1. From the **Awaiting Activation** tab, select an existing MAC ID.
   A password is created for the MAC address and is shown in the **Verification Code** column.

2. Provide the list of MAC IDs and verification codes to the field technicians. You can export the detail directly in a file and share the file with the technician who is doing the actual installation work.

## Provision the device

When the device is powered on and connected to the network, the technician provisions the device. These steps are completed on the Teams device.

![Provision new device overview](../media/remote-provision-7.png)

1. The technician selects **Provision device** from the **Settings**.  

   ![Provision new device option from the Actions tab](../media/provision-device1.png)
  
2. The technician enters the device-specific verification code in the provided input field.

   ![Provision new device verification](../media/provision-device-verification1.png)

   Once the device is provisioned successfully, the tenant name appears on the sign-in page.

## Sign in remotely

The provisioned device appears in the **Awaiting sign in** tab. Start the remote sign-in process by selecting the individual device.

![The window to choose a device for sign in.](../media/remote-provision-7.png)

1. Select a device from the **Awaiting sign in** tab.

   ![The window with a list of devices ready for sign in.](../media/remote-device1.png)

2. Follow the instructions in **Sign in a user**, and then select **Close**.

   ![the Sign in a user window for individual device](../media/sign-in-user.png)

## Related article

- [Manage your devices in Teams](device-management.md)
- [Update Teams devices remotely](remote-update.md)
