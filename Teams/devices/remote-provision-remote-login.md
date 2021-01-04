---
title: Remote provisioning and remote sign-in
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
description: Learn how to remote provision a device and create a one-time password in Microsoft Teams. 
---

# Remote provisioning and one-time password creation in Microsoft Teams

To provision a remote device, the admin needs to upload the MAC IDs of the devices being provisioned and create a one-time password (OTP). The entire process can be completed remotely from the Teams admin center.

## Add a device MAC address

Provision the device by generating a MAC address for it.

1. Sign in to the Teams admin center.
2. Select **Devices** > **IP Phones**.
3. Select **Provision new device** from the **Actions** tab.

![Provision new device option from the Actions tab](../media/provision-new-device.png)

In the **Provision new devices** window, you can either add the MAC address manually or upload a file.

**Manually add a device MAC address**

1. From the **Awaiting Activation** tab, select **Add MAC ID**.
2. Enter the MAC ID, and select **Apply** when finished.

**Upload a file to add a device MAC address**

1. From the **Awaiting Activation** tab, select **Upload MAC IDs**.
2. Download the file template.
3. Enter the MAC ID and location, and then save the file.
4. **Select file**, and then select **Upload**.

## Generate a one-time password

You need to generate an OTP for the devices. The OTP is generated in bulk or at the device level and is valid for 24 hours. The password can be unique for each device, or you can use the same password for all devices.

1. From the **Awaiting Activation** tab, select an existing MAC ID.
2. Select  **Unique OTP per device**.

   A password is created for the MAC address and is shown in the **Verification Code** column.

3. Optional: You can select **Same OTP per device** to generate the same password for every device. You need to select every MAC Address that you want to have the same password.

You'll need to provide the list of MAC IDs and OTP to the field technicians. Once the device is powered up and connected to network, the technician provisions the device by entering the tenant **Verification code** in the user interface.

## Sign in remotely

The provisioned device appears in the **Awaiting sign in** tab. Initiate the remote sign-in process by selecting the individual device.

1. Select a device from the **Awaiting sign in** tab.
2. Follow the instructions in **Sign in a user**, and then select **Close**.

![the Sign in a user window](../media/sign-in-user.png)

## Related article

- [Manage your devices in Teams](device-management.md)
- [Update Teams devices remotely](remote-update.md)
