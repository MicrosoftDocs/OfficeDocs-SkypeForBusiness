---
title: Microsoft Teams Rooms license overview in Teams admin center
ms.author: dstrome
author: dstrome
manager: serdars
ms.reviewer: sohailta
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - NOCSH
ms.custom: 
  - Licensing
  - LIL_Placement
  - seo-marvel-apr2020
description: Learn about and compare Teams Rooms licensing and feature availability in Teams admin center.
---

# Microsoft Teams Rooms license overview in Teams admin center

The Teams admin center lets you view and manage Teams Rooms devices and their peripherals from a central location. This article shows you [what management capabilities](#comparison-of-teams-rooms-feature-availability-by-license) you have, depending on whether a Teams Rooms device is assigned a Microsoft Teams Rooms Basic or Microsoft Teams Rooms Pro license.

For more information about Microsoft Teams Rooms licenses, see [Microsoft Teams Rooms licenses](rooms-licensing.md).

> [!NOTE]
> If you have existing Teams Rooms Standard or Teams Rooms Premium legacy licenses, you'll need to switch to Teams Rooms Pro when your legacy licenses expire. If you have an Enterprise Agreement, you'll need to switch to Teams Rooms Pro licenses at your next renewal period. For more information, see [Switching from Teams Rooms Standard and Teams Rooms Premium](rooms-licensing.md#switching-from-teams-rooms-standard-and-teams-rooms-premium).

## See which licenses are assigned to Teams Rooms devices

You can see what license your devices have by going to Teams devices in the Teams admin center, and then selecting the device category (Teams Rooms on Windows, Teams Rooms on Android, and Surface Hubs) you want to see. For example, if you select **Teams devices** > **Teams Rooms on Windows**, you'll see something similar to the following image. The **License** column shows the Teams Rooms license assigned to each device.

:::image type="content" source="../media/mtr-device-inventory-license-focus.png" alt-text="Teams Rooms inventory list with focus on Standard, Pro, and Pro (Trial) licenses.":::

Devices that have the **Pro** license can access all the features of the Teams admin center. Devices with other licenses can access a subset of those features. You can see which features are available to each license in [Comparison of Teams Rooms feature availability by license](#comparison-of-teams-rooms-feature-availability-by-license).

> [!IMPORTANT]
> If you select multiple devices that include both Microsoft Teams Rooms Basic and Microsoft Teams Rooms Pro licenses, actions that require a Microsoft Teams Rooms Pro license will be performed only on devices that have been assigned that license. The action won't be performed on devices assigned the Microsoft Teams Rooms Basic license.

## See which features require a Microsoft Teams Rooms Pro license

Features that require a Microsoft Teams Rooms Pro license can be identified by looking for the :::image type="icon" source="../media/mtr-pro-icon.png" border="false"::: icon on a device's details page. If the device that's currently selected isn't assigned a Microsoft Teams Rooms Pro license, you won't be able to perform the action and will see a prompt to upgrade.

:::image type="content" source="../media/mtr-restart-device-dialog.png" alt-text="Teams Rooms device restart dialog showing Pro icon.":::

## Comparison of Teams Rooms feature availability by license

The following table shows the management capabilities available in the Teams admin center for each Microsoft Teams Rooms license.

|                                               | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:----------------------------------------------|:---------------------------:|:-------------------------:|
| **Automatic device updates**                  | &#x2714;                    | &#x2714;                  |
| **Basic device analytics**                    | &#x2714;                    | &#x2714;                  |
| **Basic device health**                       | &#x2714;                    | &#x2714;                  |
| **Call quality dashboard**                    | &#x2714;                    | &#x2714;                  |
| **Create and view workspaces**                | &#x2714;                    | &#x2714;                  |
| **Real-time telemetry**                       | &#x2714;                    | &#x2714;                  |
| **Regular feature updates**                   | &#x2714;                    | &#x2714;                  |
| **Remote sign-in and sign-out**               | &#x2714;                    | &#x2714;                  |
| **Android device configurations**             |                             | &#x2714;                  |
| **Device alerts**                             |                             | &#x2714;                  |
| **Device analytics - health and utilization** |                             | &#x2714;                  |
| **Device detail view**                        |                             | &#x2714;                  |
| **Device health details**                     |                             | &#x2714;                  |
| **Device tags**                               |                             | &#x2714;                  |
| **Graph APIs**                                |                             | &#x2714;                  |
| **Remote restart**                            |                             | &#x2714;                  |
| **Windows device peripherals management**     |                             | &#x2714;                  |
| **Windows device settings**                   |                             | &#x2714;                  |
