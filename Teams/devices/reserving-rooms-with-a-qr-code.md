---
title: Reserve a room from a Teams Panel
author: mstonysmith
ms.author: tonysmit
ms.reviewer: eviegrimshaw
ms.date: 08/21/2024
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Devices
  - Tier1
search.appverid: MET150
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: This article provides information for admins about using QR codes on Teams Panels to reserve rooms in an organization.
---

# Reserving a room using a QR code on a Teams Panel

Teams Panels supports the ability for users to reserve the room by scanning a QR code on the home screen. This feature lets users book the room for meetings now, in the future, or as part of a scheduled meeting with a few steps. After scanning the QR code, they can either schedule a new meeting with the room pre-populated or view the room’s availability for their meetings and easily select to book the room.

:::image type="content" source="../media/mtr-devices/qr-code-reserved.png" alt-text="Teams Panels home screen with a QR code and scan to reserve label in the top left.":::

This feature is turned on by default in each organization. However, you can turn it off on the device by going to **Settings** > **Device settings** > **Teams Admin Settings** > **Meetings** and turning off **Allow room reservations by QR code**. To turn it off remotely, log into **Teams Admin Center** > go to **Teams devices** > **Panels** > select **Configuration profiles** > **Add** or **Edit** > **Meeting settings** > turn off **People can scan a QR code to reserve a room**. 

> [!IMPORTANT]
> Teams Panels must have a Teams Shared Device or Teams Rooms Pro license assigned.

### So how does it work?

Users need to be in the same organization as the room to be able to reserve the room using the QR code. They can use their phone's camera app to scan the QR code, and once they scan it, it opens the Teams mobile app.

> [!IMPORTANT]
> If users are using an Android based mobile device and have Android work profiles enabled, both the Teams app and the camera must be listed under the same profile. When they are in separate profiles, the camera app isn't able to correctly scan and transfer the information over to the Teams app. 
> 
> If you don't have the ability to remove profiles or add the camera app or Teams app to the same profile, you will need to contact your organization's admin. You can see how to [Add the Teams app and camera app to a work profile](#add-the-teams-app-and-camera-app-to-a-work-profile).
When a user scans the QR code, they can choose to **Schedule a new meeting** or **Reserve for existing meeting**. If they choose to schedule a new meeting, the room is added for them in the meeting invite, so they don't have to spend time finding the room. If they choose to reserve the room for an existing meeting, they are shown a list of their meetings that are already scheduled and starting before the day after tomorrow. Next to each meeting, they can see if the room is booked or free and can easily reserve the room.

> [!NOTE]
> Although users can only use the **Reserve** button on the Teams Panel when the room is available, they can scan the QR code at any point to reserve the room regardless of the room's status.

### What are the requirements for devices?

1. Make sure that the Teams Panels is running on Teams app version 1449/1.0.97.2023080401 or later and has a Teams Shared Device or Teams Rooms Pro license assigned.
2. Make sure users have updated the Teams app on their mobile device to the latest version.
3. Make sure that the mobile device is running:
    - Android devices: 1416/1.0.0.2023153001 or later.
    - iOS devices: 5.15.0 or later.

To reserve the room:
1. Using the phone's camera app, users should hold it over the QR code found in the upper left hand side of the screen (located by the date and time) and wait for a message to pop up. They can then select the message on their phone to open the Teams app.

      :::image type="content" source="../media/mtr-devices/qr-code-app-reserved-1.png" alt-text="Teams mobile app with two actions being shown.":::

2. They will be able to choose if they want to book the room for a new meeting or for an existing meeting. In the Teams app on their mobile phone, they should select **Schedule a new meeting** or **Reserve for existing meeting** respectively.

    - **Schedule a new meeting**: The room is automatically added as a participant of the meeting. They can then enter the other details of the meeting, such as the title, the date, the time, and the people they want to invite.
    
        OR
    
    - **Reserve for existing meeting**: They will be given a list of their meetings that are ongoing and starting before midnight the day after tomorrow. Next to each meeting option, they can see if the room is free or busy at that time and can tap 'Reserve' to book the room.

        :::image type="content" source="../media/mtr-devices/qr-code-app-reserved-2.png" alt-text="Teams mobile app with user's meetings being shown and buttons to reserve the room if free.":::

3. After they book the room, they'll need to remember to check-in if check-in has been enabled for the room.

### Add the Teams app and camera app to a work profile

Although there are many QR code scanner apps available, we recommend using the built-in camera apps that are available on all Android and iOS devices. However, if users are using an Android device, it may not work if the device has both work and personal profiles enabled. If this is the case, and the Teams app is in the work profile, you need to add the camera app to the work profile as well.

To add the camera app to the work profile:
1. In the **Intune Admin Center**, go to **Apps** > **Android** and select **Add**.
2. Select **Android enterprise system app**.
3. Put in the type of Android device and then paste the OS camera package name.
4. Assign that package to the users or groups.
