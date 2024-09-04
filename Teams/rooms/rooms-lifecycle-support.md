---
title: Microsoft Teams Rooms app version support
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
ms.reviewer: raginis
ms.date: 08/21/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: Learn about lifecycle support for Microsoft Teams Rooms, including the dynamic support structure and its phases.
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams Rooms app version support
 
By default, the Microsoft Teams Rooms application receives updates through the Microsoft store. The app uses an evergreen product lifecycle and only the current and the next most recent major version of the app is supported at any given time. The app bundles a specific version of the Teams desktop app that is modified for room use. The Teams desktop app updates frequently while the Teams Rooms app updates less frequently. This means Teams Rooms app current-1 version can be several Teams desktop app updates behind, so it's recommended to keep the Teams Rooms app updated to the latest version at all times. Learn more about the [Teams update process](../teams-client-update.md).

While we support the most current release of Teams Rooms (N) and the previous major release (N-1) (5.1.xxx and 5.0.xxx for example), the support structure for Teams Rooms is dynamic and depends on the availability of the latest version. When you encounter a code defect in a version of the application that's not the latest, you must install the latest version to receive a fix.

All releases are listed in the [Microsoft Teams Rooms release notes](rooms-release-note.md).

> [!IMPORTANT]
> When installing a new device that came with an older version of the Teams Rooms application, it is recommended to [manually update the application](/microsoftteams/rooms/rooms-operations#software-updates) after setting the account this ensures correct OS version and Windows Updates are installed on your device.  

## Windows release support

Microsoft Teams Rooms requires the Windows IoT Enterprise or Windows Enterprise SKUs under the Global Availability Channel servicing option. These other Windows editions aren't supported:

- Windows Enterprise Long-term Servicing Branch (LTSB) / Long Term Servicing Channel (LTSC) editions
- Windows Internet of Things (IoT) Enterprise LTSB / LTSC editions
- any other edition of Windows such as Windows Pro or Home edition

New Windows feature updates aren't offered on Microsoft Teams Rooms devices immediately. There's an intentional delay of up to six months or more after the general availability date published on the [Windows release information](/windows/release-information/) page. This time is used to validate Windows release compatibility for the Microsoft Teams Rooms app, device hardware, and certified audio video peripherals. Validation begins and continues during active development of each major release of Windows. Extra time is needed to validate that all device manufacturers have built updated images for their devices, and for Microsoft to certify and test those images. During the validation period, the Microsoft Teams Rooms app uses [Windows Update for Business group policies](/windows/deployment/update/waas-manage-updates-wufb) to delay Windows feature updates. After any compatibility issues are found and resolved, the block is lifted via updating group policies through a new app release in Windows store. Devices that run the Microsoft Teams Rooms app automatically update to an appropriate Windows release during the nightly maintenance reboot. An MSI version is made available for customers that need to manually manage updates.  

> [!IMPORTANT]
> During the validation period, Microsoft Teams Rooms devices should **not** be updated to the next release of Windows by any means. This includes overriding the group policies in place, or using System Center or other third-party device management services. Any of these may cause issues for the Microsoft Teams Rooms app or may leave devices unusable.  

The following table shows recommended and supported versions of Windows that are verified to support Microsoft Teams Rooms. All dates are listed in ISO 8601 format: YYYY-MM-DD.

| Version | Availability date | Microsoft Teams Rooms support status                    | Microsoft Teams Rooms Minimum application version | Recommended OS build |
|:--------|:------------------|:--------------------------------------------------------|:--------------------------------------------------|:---------------------|
| 23H2    | 2023-10-31        | Supported,<br>Recommended                               |5.1.24.0                                           | 22631.2428   |
| 22H2    | 2022-10-18        | Supported                                               | 4.16.134.0                                        | 22621.525 &#x2780;   |
| 21H2    | 2021-11-16        | Not Supported                                           | &#x2014;                                          | &#x2014;             |
| 21H1    | 2021-05-18        | Not Supported                                           | &#x2014;                                          | &#x2014;             |
| 20H2    | 2020-10-20        | Not Supported                                           | &#x2014;                                          | &#x2014;             |
| 2004    | 2020-05-27        | Not Supported, <br/>Known compatibility issues  &#x2781;| &#x2014;                                          | &#x2014;             |
| 1909    | 2019-11-12        | Not Supported                                           | &#x2014;                                          | &#x2014;             |
| 1903    | 2019-05-21        | Not Supported                                           | &#x2014;                                          | &#x2014;             |
| 1809    | 2019-03-28        | Not Supported, <br/>Known compatibility issues &#x2782; | &#x2014;                                          | &#x2014;             |
| 1803    | 2018-07-10        | Not Supported                                           | &#x2014;                                          | &#x2014;             |
| 1709    | 2018-01-18        | Not supported                                           | &#x2014;                                          | &#x2014;             |
| 1703    | 2017-07-11        | Not Supported                                           | &#x2014;                                          | &#x2014;             |

&#x2780; In order to maximize service life, hardware that is not Windows 11 eligible will upgrade from Windows 10 21H2 to Windows 10 22H2. However, take note of the [Windows 10 IoT Enterprise end of support date](/lifecycle/products/windows-10-iot-enterprise), Teams Rooms on Windows devices running Windows 10 will not be supported after the Windows 10 IoT Enterprise end of support date.  

When you use a supported version of Windows, you will always get the latest application updates for the Microsoft Teams Rooms app.  

## Related topics

[Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Microsoft Teams Rooms release notes](rooms-release-note.md)

[Plan for Microsoft Teams Rooms](rooms-plan.md)
