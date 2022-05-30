---
title: "Microsoft Teams Rooms app version support"
ms.author: dstrome
author: dstrome
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
ms.localizationpriority: medium
description: Learn about lifecycle support for Microsoft Teams Rooms, including the dynamic support structure and its phases.
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams Rooms app version support
 
The Microsoft Teams Rooms app gets updates through the Windows store. Microsoft Teams Room app uses an evergreen product lifecycle and only the current and the next most recent version of the app are supported at any given time. The Microsoft Teams Room app bundles a specific version of the Teams desktop app that is modified for room use. The Teams desktop app updates every two weeks. Learn more about the [Teams update process](../teams-client-update.md). This means Teams Rooms app current-1 version can be up to six Teams desktop app updates behind, so it's recommended to keep the Teams Room application updated to the latest version of the Teams Rooms app at all times. 

The support structure for Teams Rooms is dynamic and depends on the availability of the latest version. When you encounter a code defect in a version of the application that's not the latest, you must install the latest version to receive a fix.

All releases are listed in the [Microsoft Teams Rooms release notes](rooms-release-note.md).

> [!IMPORTANT]
> When installing a new device that came with an older version of the Teams room application, it is recommended to [manually update the application](manual-update.md) after setting the account, before downloading any Windows updates. This ensures correct OS version and Windows updates are installed on your device.  

## Windows 10 release support

Microsoft Teams Rooms requires the  Windows 10 IoT Enterprise or Windows 10 Enterprise SKUs under Semi-Annual Channel servicing options. These other Windows 10 editions aren't supported:

- Windows 10 Enterprise Long-term Servicing Branch (LTSB) / Long Term Servicing Channel (LTSC) editions
- Windows 10 Internet of Things (IoT) Enterprise LTSB / LTSC editions
- any other edition of Windows such as Windows 10 Pro or Home edition

New Windows 10 feature updates aren't offered on Microsoft Teams Rooms devices immediately. There's an intentional delay of up to six months or more after the general availability date published on the [Windows 10 release information](/windows/release-information/) page. This time is used to validate Windows 10 release compatibility for the Microsoft Teams Rooms app, device hardware, and certified audio video peripherals. Validation begins and continues during active development of each major release of Windows 10. Extra time is needed to validate that all device manufacturers have built updated images for their devices, and for Microsoft to certify and test those images. During the validation period, the Microsoft Teams Room app uses [Windows Update for Business group policies](/windows/deployment/update/waas-manage-updates-wufb) to delay Windows 10 feature updates. After any compatibility issues are found and resolved, the block is lifted via updating group policies through a new app release in Windows store. Devices that run the Microsoft Teams Rooms app automatically update to an appropriate Windows 10 release during the nightly maintenance reboot. An MSI version is made available for customers that need to manually manage updates.  

> [!IMPORTANT]
> During the validation period, Microsoft Teams Rooms devices should **not** be updated to the next release of Windows 10 by any means. This includes overriding the group policies in place, or using System Center or other third-party device management services. Any of these may cause issues for the Microsoft Teams Room app or may leave devices unusable.  

The following table shows recommended and supported versions of Windows 10 that are verified to support Microsoft Teams Rooms. All dates are listed in ISO 8601 format: YYYY-MM-DD.

| Version | Availability date | Microsoft Teams Rooms support status                    | Microsoft Teams Rooms Minimum application version | Recommended OS build |
|:--------|:------------------|:--------------------------------------------------------|:--------------------------------------------------|:---------------------|
| 21H2    | 2021-11-16        | Supported,<br>Recommended                               | 4.12.126.0                                        | 19044.1288           |
| 21H1    | 2021-05-18        | Not Supported                                           | &#x2014;                                          | &#x2014;             |
| 20H2    | 2020-10-20        | Supported                                               | 4.10.10.0                                         | 19042.631            |
| 2004    | 2020-05-27        | Skipped, <br/> Not recommended &#x2780;                 | &#x2014;                                          | &#x2014;             |
| 1909    | 2019-11-12        | Supported                                               | 4.5.33.0                                          | 18363.418            |
| 1903    | 2019-05-21        | Not Supported                                           | &#x2014;                                          | &#x2014;             |
| 1809    | 2019-03-28        | Not Supported, <br/>Known compatibility issues &#x2781; | &#x2014;                                          | &#x2014;             |
| 1803    | 2018-07-10        | Not Supported                                           | &#x2014;                                          | &#x2014;             |
| 1709    | 2018-01-18        | Not supported                                           | &#x2014;                                          | &#x2014;             |
| 1703    | 2017-07-11        | Not Supported                                           | &#x2014;                                          | &#x2014;             |

&#x2780; Windows 10 version 2004 is not recommended due to compatibility issues found with the Microsoft Teams Rooms application. This specific issue causes the Microsoft Teams Rooms application to fail to start after the nightly reboot. 

&#x2781; Windows 10 version 1809 is not recommended due to compatibility issues found with the Microsoft Teams Rooms application. This specific issue causes the Microsoft Teams Rooms application to fail to start after the nightly reboot. This issue was addressed in  Windows 10 version 1903.  

When you use a supported version of Windows 10, you will always get the latest application updates for the Microsoft Teams Rooms app.  


## Related topics

[Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Microsoft Teams Rooms release notes](rooms-release-note.md)

[Plan for Microsoft Teams Rooms](rooms-plan.md)
