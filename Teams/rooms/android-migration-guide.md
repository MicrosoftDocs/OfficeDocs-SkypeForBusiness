---
title: Migration guide Android AOSP management for Microsoft Teams Android devices
ms.author: tonysmit
author: mstonysmith
ms.reviewer: mattslomka
ms.date: 05/02/2024
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: msteams
ms.subservice: itpro-rooms
ms.collection:
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords:
  - NOCSH
ms.localizationpriority: medium
description: Learn about how to migrate Android devices to AOSP
---

# Overview of migrating Android devices

## Customer Intent for this Article: The customer is seeking guidance on how to successfully migrate Microsoft Teams Android devices from Device Administrator to Android AOSP management.
Article:

## Successful AOSP Migration for Microsoft Teams Android Devices

This document will guide both Teams and Intune admins through the necessary steps to handle the upcoming mandatory AOSP migration for Microsoft Teams Android devices. The migration process includes setting up enrollment profiles, creating AOSP policies, and applying firmware upgrades.

### 1. Prerequisites

To migrate from Device Administrator to Android AOSP management, ensure you have the following:

- An active Microsoft Intune tenant.
- A Teams Android device that supports Intune AOSP.

If your organization does not use Intune for Teams Android devices, you only need to take the firmware upgrade through Teams Admin Center. In this case, Teams Android devices will not leverage AOSP management.

### 2. Set up enrollment profiles

Follow the instructions in [Set up Android (AOSP) device management in Intune for corporate-owned user-associated devices](https://docs.microsoft.com/en-us/mem/intune/enrollment/android-aosp-enroll) to enroll the device in Intune. The enrollment process includes:

1. Creating a Corporate-owned, User-associated enrollment profile.
2.  Marking "For Microsoft Teams devices" as "Enabled".
3.  Saving the profile.

Note: The enrollment to Intune will happen automatically when the device updates to AOSP. Ensure there are no existing enrollment profiles when creating a new one.

### 3. Create AOSP policies

Automatic policy migration is not available due to differences between Device Administrator and AOSP policies. IT administrators will need to create new AOSP policies for their Microsoft Teams Android devices that are migrating. AOSP policy creation should be done before taking the firmware update to ensure that devices work as intended after migration.

There are two types of AOSP policies for Teams Android devices:

- Compliance settings: [Android (AOSP) compliance settings in Microsoft Intune](https://docs.microsoft.com/en-us/mem/intune/protect/compliance-policy-create-android-aosp)
- Device restriction settings: [Device restriction settings for Android (AOSP) in Microsoft Intune](https://docs.microsoft.com/en-us/mem/intune/configuration/device-restrictions-android-aosp)

#### 3.1 Supported AOSP policies

Teams Android devices migrating to AOSP will initially support the following AOSP policies:

- Compliance settings:

- - Device Health: Rooted devices
  - Device Properties: Minimum OS version
  - Device Properties: Maximum OS version
  - System Security: Encryption - require encryption of data storage on the device

- Device restriction settings:

- - Block screen capture

Other AOSP policies will not apply to Teams Android devices initially on migration. In future updates, additional AOSP policies will be supported and can be leveraged for Teams Android devices.

#### 3.2 Teams' settings

Teams' settings configured on a device through Teams Admin Center will not be affected by the migration to AOSP and will persist after migration.

### 4. Firmware update

After setting up your enrollment profiles and creating your AOSP policies, your devices are ready to go through migration to AOSP. The firmware update will be available in Teams Admin Center as a manual update to be applied to devices. Follow these steps to update a device:

1.  Select a device and select "Update".
2.  Under the "Manual updates" section, you should see a new firmware available.
3.  Select the firmware and choose to update it immediately, or schedule a preferred time and then update.
4.  Check the "History" of the device to confirm the update is complete.
5.  After a successful update, "Microsoft Intune" and "Authenticator" will be listed under the "Software health" section in device details. "Company portal" will no longer be listed.
6.  Ensure the device is online during the entire process. If the update fails, check the network state and configuration and try again. If the update is failing repeatedly, contact Microsoft Support.

On completion of the firmware update, the device should remain signed in (if it was already signed in) and should properly enroll into Intune. Once this process is complete, the device is ready to be used!
