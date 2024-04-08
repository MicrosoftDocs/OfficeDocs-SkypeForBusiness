---
title: Join meetings using a QR code
ms.author: tonysmit
author: tonysmit
manager: pamgreen
ms.reviewer: henrikalim
ms.date: 04/05/2024
ms.topic: article
audience: admin
appliesto:
- Microsoft Teams
ms.service: msteams
ms.subservice: itpro-rooms
ms.collection: 
- M365-collaboration
- teams-rooms-consoles
- Tier1
f1.keywords:
- NOCSH
search.appverid: MET150
ms.localizationpriority: medium
description: Learn how to use QR codes on Microsoft Teams Rooms to join meetings.
---
# Overview of QR codes on Microsoft Teams Rooms 

Teams Rooms on Windows and Teams Rooms on Android support a convenient way to join meetings from a Teams Rooms by simply scanning a QR code on the home screen, making it easier for people to use meeting rooms ad-hoc. This serves as an alternative to proximity-based technologies like Bluetooth and streamlines the user experience by reducing the steps for users to join a meeting with the room system. This feature is available in Teams Rooms on Windows 5.0 app and later as well as Teams Rooms on Android 2.2 app and later. 

A QR code is displayed by default on the Teams Room home screen. To ensure security, the QR code is refreshed every minute. You can enable or disable this feature through settings. When this feature is disabled, the QR code will not be shown on the home screen.![Teams Rooms home screen showing QR code.](media/teams-rooms-qr-codes/0011-min-(1).png)

Once users scan the QR code with their mobile camera, users can select an action on their mobile device that they would like to perform with the room system. Users can choose from joining any meeting on their mobile calendar that is ongoing or beginning within the next 10 minutes, starting an ad-hoc meeting, or casting content from their mobile device to the front of room display. Cross-tenant meetings are also supported when the External access organization settings and user policies in the Teams admin center allow it. If users do not have the Teams mobile app, they will be directed to download it after scanning the QR code. 

> [!NOTE]
> Only calendar events with an ongoing or upcoming online Teams meeting (scheduled to start within 10 minutes) will appear under **Join with room**. 
![Actions on the Teams mobile app that a user can take after scanning the QR code on a Teams Room device.](media/teams-rooms-qr-codes/444.png)

After users pick an action on their mobile device, the room system automatically accepts the meeting nudge and joins the meeting without additional user action by default. Users will then enter the full meeting experience on Teams Rooms and the room companion mode experience on Teams mobile. You can also disable the room auto-accept functionality for any QR code join in general through settings. 

> [!NOTE]
> For security reasons, if the user takes more than two minutes to select an action on mobile after scanning the QR code, the room auto-accept functionality will be disabled regardless of the setting value, and the user will have to manually accept the call on the touch console or touch display. 
IT admins can control the QR code feature using XML settings for Teams Rooms on Windows, device settings for Teams Rooms on Android, and the Teams admin center for both Teams Rooms platforms. 

QR code join will be enabled by default. For Teams Rooms on Android, IT admins can enable or disable the functionality through device settings or the Teams admin center. For Teams Rooms on Windows, IT admins can disable the QR code feature using an XML setting or the Teams admin center. When the feature is disabled, the QR code will not be visible on the home screen. To disable the QR code feature in an XML setting, use the following code:


```
<
```

IT admins can also disable the room auto-accept functionality for any QR code join in general using an XML setting or the Teams admin center. When auto-accept is disabled, users will have to manually tap "Accept" on the room system's touch console or touch board for the room to enter the meeting. To disable room auto-accept in an XML setting, use the following code:


```
<

```

> [!IMPORTANT]
> If users are using an Android mobile device and have Android work profiles enabled, both the Teams app and the camera must be listed under the same profile. When they are in separate profiles, the camera app isn't able to correctly scan and transfer the information over to the Teams app.
If you don't have the ability to remove profiles or add the camera app or Teams app to the same profile, you will need to contact your organization's admin. You can see how to **[Add the Teams app and camera app to a work profile](/editor/MicrosoftDocs/OfficeDocs-SkypeForBusiness-pr/Teams%2Fdevices%2Freserving-rooms-with-a-qr-code.md/main/5c19d6b0-bd86-c908-4bbb-5c6bd187bff0/?branch=main)**.

[Add the Teams app and camera app to a work profile]()

Although there are many QR code scanner apps available, we recommend using the built-in camera apps that are available on all Android and iOS devices. However, if users are using an Android device, it may not work if the device has both work and personal profiles enabled. If this is the case, and the Teams app is in the work profile, you need to add the camera app to the work profile as well.

To add the camera app to the work profile:
1. In the **Intune Admin Center**, go to **Apps** > **Android** and select **Add**.
1. Select **Android enterprise system app**.
1. Put in the type of Android device and then paste the OS camera package name.
1. Assign that package to the users or groups.
