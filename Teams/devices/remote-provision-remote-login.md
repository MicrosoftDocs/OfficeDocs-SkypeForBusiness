---
title: Remote provisioning and sign in for Teams Android devices
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Devices
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

## Review the supported devices

The following list shows the Android device firmware requirements.

|Device category|Device model|Firmware version|
|---|---|---|
|Teams phones|Yealink T55/T56/T58|58.15.0.124|
|Teams phones|Yealink VP59|91.15.0.58|
|Teams phones|Yealink CP960|73.15.0.117|
|Teams phones|Yealink MP56/MP54/MP58|122.15.0.36|
|Teams phones|Crestron UC-2|1.0.3.52|
|Teams phones|Poly Trio C60|7.0.2.1071|
|Teams phones|CCX400/CCX500/CCX600 |7.0.2.1072|
|Teams phones|Audio Codes C448HD/C450HD/C470HD|1.10.120|
|Teams panels|Crestron 770/1070|1.004.0115|
|Teams Rooms on Android|Logitech Rally Bar Mini|1.2.982|
|Teams Rooms on Android|Logitech Rally Bar|1.2.982|
|Teams Rooms on Android|AudioCodes RXV80|1.13.361|
|Teams Rooms on Android|EPOS EXPAND Vision 3T|1.2.2.21182.10|
|Teams Rooms on Android|Yealink MeetingBar A30|133.15.0.60|
|Teams Rooms on Android|Yealink MeetingBar A20|133.15.0.60|
|Teams Rooms on Android|Yealink CTP18 touch console|137.15.0.37|
|Teams Rooms on Android|Poly Studio X30|3.5.0.344025|
|Teams Rooms on Android|Poly Studio X50|3.5.0.344025|
|Teams Rooms on Android|Poly TC8 touch console |3.5.0.210489|
|Teams Rooms on Android|Yealink VC210|118.15.0.54|

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

   ![the Sign in a user window for individual device.](../media/sign-in-user.png)

## Related articles

- [Manage your devices in Teams](device-management.md)
- [Remote sign in and sign out](remote-sign-in-and-sign-out.md)
- [Update Teams devices remotely](remote-update.md)
