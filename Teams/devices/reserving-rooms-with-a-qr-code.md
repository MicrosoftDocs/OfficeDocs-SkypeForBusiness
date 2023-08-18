---
title: Reserve a room from a Teams Panel
ms.author: tonysmit
author: tonysmit
ms.reviewer: weizxue
ms.date: 08/18/2023
manager: serdars
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

# Reserving a room using a QR code from a Teams Panel

Teams Panels with a Teams Shared Device or Teams Rooms Pro license will allow users to reserve the room by scanning a QR code on the home screen. Users can either schedule a new meeting with the room pre-populated for them or easily see the room’s availability for their meetings and book the room with one touch.

  :::image type="content" source="../media/mtr-devices/qr-code-reserved.png" alt-text="Reserving a room with a QR code.":::

This feature is turned on by default for each organization. However, you can turn it off by going to **Settings** > **Device settings** > **Teams Admin Settings** > **Meetings**. With this feature, users will be able to book the room for meetings now, in the future, or as part of a scheduled meeting more conveniently by scanning the QR code.

### So how does it work?

Users will need to be in the same organization as the room to be able to reserve a room using a QR code. They can use their phone's camera to scan the QR code and once they scan it, it will open the Teams app.

> [!IMPORTANT]
> If users are using an Android based mobile device that has Android work profiles enabled, both the Teams app and the camera app must both be listed under the same profile. When they are in separate profiles, the camera app is not able to properly scan and transfer the data over to Teams app. 

> If you don't have the ability to remove profiles or add the camera app or Teams app to the same profile, they will need to contact your organization's admin. Below are the steps required to add the camera app to the work profile. See <How to fix it if your Android device has profiles set>.

When a user scans the QR code, they will be given two actions; they can **Schedule a new meeting** or **Reserve for Existing Meeting**. If they choose to schedule a new meeting, the room will be populated for them in the meeting invite so they don't have to spend time finding the room. If they choose to reserve the room for an existing meeting, they will be shown a list of their meetings that are already scheduled (up until the day after tomorrow) along with whether the room is booked or free at those times and the ability to easily reserve the room if it is.

  > [!NOTE]
  > Although users can only use the **Reserve** button on the Teams Panel when the room is available, they can scan the QR code at any point to reserve the room regardless of the room's status.

### What are the requirements for devices?

1. Make sure users have updated the Teams app on their mobile device to the latest version.
2. Make sure that the mobile device is running:
  - Android devices: 1416/1.0.0.20231228041.0.76.2023152002 or later.
  - iOS devices: 5.125.15.0 or later.

To reserve the room:
Here are the steps to book the room using the QR code on the Teams Panel:
1. Using their phone's camera app, they should hold it over the QR code found in the upper left hand side of the screen by the date and time and wait for a message to pop up. Tap on the message to open the Teams app.

  :::image type="content" source="../media/mtr-devices/qr-code-app-reserved-2.png" alt-text="Reserving a room for an existing meeting.":::

2. Choose if they want to book the room for a new meeting or for an existing meeting. In the Teams app on their mobile phone, they should select Schedule a new meeting or Reserve for existing meeting.

  > [!NOTE]
  > Although you can use third-party code scanner apps, its not recommended.

  - If they want to book the room for a new meeting , select **Schedule a new meeting**. The room will be automatically added as a participant of the meeting. They can then enter the other details of the meeting, such as the title, the date, the time, and the people they want to invite.
  - If they want to book the room for an existing meeting , select **Reserve for existing meeting**. They will then be presented with a list of their meetings that are ongoing and starting before midnight the next day after tomorrow. Next to each meeting option, they will be able to see if the room is free or busy at that time and tap to book the room.

3. After they book the room, they will need to click check in on the Teams Panel or join the meeting on the Microsoft Teams Rooms console found in the room if check in is enabled for the room.

:::image type="content" source="../media/mtr-devices/qr-code-app-reserved-1.png" alt-text="Reserving a room for an existing meeting.":::

### Add the Teams app and camera app to a work profile

Although there are lots many QR code scanner apps available, we recommend using the built in Camera apps that are available on all Android and iOS devices. 

However, if users are using an Android device to scan the QR code, it may not work if the device has both work and personal profiles set upenabled. If this is the case, and the Teams app is in the work profile, you will need to add the camera app to the work profile.

To do this:
1. In the Intune Admin Center, go to **Apps** > **Android** and select **Add**.
2. Select **Android enterprise system app**.
3. Put in the type of Android device and then paste OS camera package name.
4. Assign to users or groups.

If check-in is enabled for this room, after you book it, be sure to check into your reservation by selecting the check on Teams Panels or join the meeting on the Microsoft Teams Rooms device.