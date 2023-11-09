---
title: Remote provisioning and sign in for Teams Android devices
author: tonysmit
ms.author: tonysmit
manager: serdars
ms.reviewer: kimmatlock
ms.date: 11/02/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to remote provision and sign in for Teams Android devices
---

# Remote provisioning and sign in for Teams Android devices

IT admins can remotely provision and sign in to a Teams Android device. To provision a device remotely, the admin needs to upload the MAC IDs of the devices being provisioned and create a verification code. The entire process can be completed remotely from the Teams admin center.

> [!NOTE]
> Once you've signed in to a Teams Android device, this feature isn't available. To use it again, the device must be reset to factory default settings.

## Supported devices

All Android and SIP devices certified by Microsoft can be provisioned remotely from Teams admin center. 

Refer to the following for the list of certified hardware:

Phones, Displays, Panels - [Devices for Teams | Microsoft certified hardware](./teams-ip-phones.md)
Microsoft Teams Rooms on Android - [Teams Rooms certified systems and peripherals](../rooms/certified-hardware.md?tabs=Android)
SIP devices - [Teams compatible devices](../sip-gateway-plan.md#compatible-devices)


## Add a device MAC address

Complete the following steps to provision a new device.

1. Sign in to the Teams admin center.
2. Expand **Teams Devices**.
3. Select **Provision new device** from the **Actions** tab.

In the **Provision new devices** window, you can either add the MAC address manually or upload a file.

### Manually add a device MAC address

1. From the **Waiting on activation** tab, select **Add MAC ID**.

   ![manually add a device mac address.](../media/remote-provision-6-new.png)

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

- [Manage your devices in Teams](device-management.md)
- [Remote sign in and sign out](remote-sign-in-and-sign-out.md)
- [Update Teams devices remotely](remote-update.md)

