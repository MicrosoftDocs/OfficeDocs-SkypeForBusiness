---
title: Microsoft Teams Rooms licenses
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: kspiess
ms.date: 08/08/2024
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
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords: 
  - NOCSH
ms.custom: 
  - Licensing
  - LIL_Placement
  - seo-marvel-apr2020
description: Learn about and compare the available licenses for different types of calling and meeting features in Microsoft Teams Rooms.
---

# Microsoft Teams Rooms licenses

Microsoft offers two licenses for Teams Rooms systems that participate in Teams meetings and calls:

- **Microsoft Teams Rooms Pro** delivers enhanced in-room meeting experiences like intelligent audio and video, front row and large galleries, and dual screen support. The Teams Rooms Pro license also provides advanced management features like remote device management, conditional access policies, and detailed device analytics.

    Teams Rooms Pro is a great fit for medium and enterprise organizations, as well as smaller organizations with larger room counts or more advanced needs. Teams Rooms Pro licenses can be used to license both certified Teams Rooms systems and Teams Panels.

- **Microsoft Teams Rooms Basic** provides core meeting experiences to organizations that purchase a certified Microsoft Teams Rooms system, at no additional cost. The Teams Rooms Basic license includes scheduling, joining meetings, content sharing, and collaborative white boarding, as well as basic security and management capabilities out-of-the-box.
- A Teams Rooms Basic license can be used to license a single certified Teams Rooms system in a room. If you want to log into more than one Teams Rooms system in a room using the same resource account, you need to use a Teams Rooms Pro license.

- You can assign up to 25 Microsoft Teams Rooms Basic licenses to Teams Rooms systems in your organization. If you need to license more than 25 Teams Rooms systems, those additional licenses need to be Teams Rooms Pro licenses. Teams Rooms Basic licenses can be used to license Teams Rooms systems only and not Teams Panels.

A Teams Room system can be one of the following:

- A Teams Rooms on Windows compute module and attached touch console
- A Teams Rooms on Android device and touch console connected via either an IP-based or USB connection
- A Surface Hub

The remote administration tasks you perform on a Teams Rooms system or device in the Teams admin center depend on the license that's assigned the system or device. For more information, see [Microsoft Teams Rooms license overview in Teams admin center](admin-center-license-overview.md).

> [!IMPORTANT]
> - Microsoft Teams Rooms devices need specific licenses like "Microsoft Teams Rooms Pro" or "Microsoft Teams Rooms Basic" to work. Other user licenses won't function with meeting devices. Meeting devices without a Teams Rooms license will be unable to sign in until they obtain one.
> - Microsoft Teams Shared Devices licenses are not supported with Teams Rooms devices. Only assign Teams Rooms Basic or Teams Rooms Pro licenses to these devices (Teams Rooms legacy licenses are also acceptable).


## Teams Rooms license service plan comparison

The following table shows the services included in each Teams Rooms license.

|                                           | Microsoft Teams Rooms Basic                                          | Microsoft Teams Rooms Pro                                              |
|:------------------------------------------|:--------------------------------------------------------------------:|:----------------------------------------------------------------------:|
| **Maximum number of licenses**            | 25                                                                   | Unlimited                                                              |
| **Microsoft Teams**                       | &#x2714;                                                             | &#x2714;                                                               |
|**Microsoft Teams Rooms Pro Management**||✔|
| **Audio Conferencing<sup>1</sup>**        | &#x2714;                                                             | &#x2714;                                                               |
| **Whiteboard**                            | &#x2714;                                                             | &#x2714;                                                               |
| **Teams Phone** **Standard**                          |                                                                      | &#x2714;                                                               |
| **Microsoft Intune<sup>2</sup>**          |                                                                      | &#x2714;                                                               |
| **Microsoft Entra ID P1** |                                                                      | &#x2714;                                                               |
|**Microsoft Defender for Endpoint Plan 2**||✔|
| **Skype for Business Plan 2<sup>3</sup>** |                                                                      | &#x2714;                                                               |
| **Geographic availability**               | Worldwide                                                            | Worldwide                                                              |
| **Segment availability**                  | Commercial, Worldwide Public Sector, Education, Charity, GCC         | Commercial, Worldwide Public Sector, Education, Charity, GCC, GCC-High |
| **Channel availability**                  | Web Direct, New commerce experience (NCE) - Customer led<sup>4</sup> | EA, EAS, EES, CSP, Web Direct, NCE - Customer led, NCE - Partner led   |

<sup>1</sup> To verify service availability, see [Country and region availability for Audio Conferencing and Calling Plans](../country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md). [Communication Credits](../what-are-communications-credits.md) may apply for additional services, such as toll-free, international minutes for domestic plans, and so on. You can disable these features to avoid additional billing. [Conference Phones with Meeting Interface](/microsoftteams/devices/teams-android-devices-user-interface) requires Microsoft Teams Rooms Pro License.

<sup>2</sup> Microsoft Intune Plan 1 and Plan 2.

<sup>3</sup> Included to enable certain legacy authentication methods. Effective October 1, 2023 Microsoft Teams Rooms will no longer support connections to Skype for Business server.

<sup>4</sup> You need to add and assign a free Teams Rooms Basic license for each device via the Microsoft 365 admin center. You need to provide payment details, although no charge will be made for Teams Rooms Basic licenses. see [subscriptions and billing documentation](/microsoft-365/commerce) for details. 

## Switching from Teams Rooms Standard and Teams Rooms Premium

If your organization has meeting devices that use the Teams Rooms Standard or Teams Rooms Premium legacy licenses, you can continue using those licenses until their expiration date. Upon the expiration date of your existing legacy licenses, we recommend that you transition to the Teams Rooms Pro license. The meeting and management features<sup>*</sup> available in both of the legacy licenses have been combined in the Teams Rooms Pro license.

> [!IMPORTANT]
> Legacy licenses won't automatically transition to the new licenses. Upon expiration of a legacy license, you'll need to purchase a new Teams Rooms Pro (recommended) or Teams Rooms Basic license. Teams Rooms Pro licenses can be purchased through the Microsoft 365 admin center or your preferred sales channel. Teams Rooms Basic licenses can only be purchased through the Microsoft 365 admin center.

If your organization has an Enterprise Agreement, you can continue using your existing legacy licenses until your next renewal period. You can also continue to reserve additional legacy licenses until your next renewal period. For more information, contact your Microsoft representative.

For information about legacy licenses, see [Microsoft Teams Rooms legacy licenses](rooms-legacy-licensing.md).

<sup>*</sup>Microsoft Service engineers will no longer serve as intermediaries to incident response starting October 1, 2022.

> [!TIP]
> As a companion to this article, we recommend using the [Microsoft Teams Rooms automated setup guide](https://go.microsoft.com/fwlink/?linkid=2224463) when signed in to the Microsoft 365 admin center. This guide will customize your experience based on your environment. To review best practices without signing in and activating automated setup features, go to the [Microsoft 365 setup portal](https://go.microsoft.com/fwlink/?linkid=2223356).

## Teams Rooms Basic and Teams Rooms Pro feature comparison

The following tables compare the Teams Rooms Basic and Teams Rooms Pro licenses and show what features are available with each. If a feature isn't available for a license, that feature can't be used on Teams Rooms devices that have been assigned that license. To use a feature on a Teams Rooms device, assign the license in which that feature is available to that device.

### Meeting join

|                                                                 | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:----------------------------------------------------------------|:---------------------------:|:-------------------------:|
| **Join Teams meetings with 1-touch, proximity, and meeting ID** | &#x2714;                    | &#x2714;                  |
| **Start ad hoc meetings from the room**                         | &#x2714;                    | &#x2714;                  |
| **Direct Guest Join for Zoom and Webex meetings**               | &#x2714;                    | &#x2714;                  |
| **Join meetings across Teams clouds**                           |                             | &#x2714;                  |
| **Room check-in with Teams Panel**                              |                             | &#x2714;                  |
| **Coordinated meeting**                                         |                             | &#x2714;                  |

### Share and collaborate

|                                                  | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:-------------------------------------------------|:---------------------------:|:-------------------------:|
| **Share and view all Teams content types**       | &#x2714;                    | &#x2714;                  |
| **Share whiteboard with Content Capture Camera** |                             | &#x2714;                  |

### Meeting engagement

|                                                      | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:-----------------------------------------------------|:---------------------------:|:-------------------------:|
| **Teams video gallery with multiple layout options** | &#x2714;                    | &#x2714;                  |
| **Front row**                                        |                             | &#x2714;                  |
| **Together mode**                                    |                             | &#x2714;                  |
| **Large gallery (up to 50 videos)**                  |                             | &#x2714;                  |
| **Dual screen support**                              |                             | &#x2714;                  |
| **Show meeting names**                               |                             | &#x2714;                  |

### Calling

|                                                   | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:--------------------------------------------------|:---------------------------:|:-------------------------:|
| **Make and receive peer to peer and group calls** | &#x2714;                    | &#x2714;                  |
| **Microsoft 365 Phone System**                    |                             | &#x2714;                  |
| **End-to-end call encryption**                    |                             | &#x2714;                  |

### Intelligent audio and video

|                                                                                 | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:--------------------------------------------------------------------------------|:---------------------------:|:-------------------------:|
| **Support for Intelligent Speaker live transcript with speaker identification** |                             | &#x2714;                  |
| **Multi-camera support**                                                        |                             | &#x2714;                  |
| **Panoramic room view**                                                         |                             | &#x2714;                  |
| **AI noise suppression**                                                        |                             | &#x2714;                  |
| **People counting**                                                             |                             | &#x2714;                  |

### Security and compliance

|                                                                     | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:--------------------------------------------------------------------|:---------------------------:|:-------------------------:|
| **Secure operating system**                                         | &#x2714;                    | &#x2714;                  |
| **System level security (Secure boot, Assigned Access mode, etc.)** | &#x2714;                    | &#x2714;                  |
| **Microsoft Entra Conditional Access policies**                              |                             | &#x2714;                  |

### Device management

|                                                   | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:--------------------------------------------------|:---------------------------:|:-------------------------:|
| **Teams Admin Center enrollment and inventory**   | &#x2714;                    | &#x2714;                  |
| **Automatic software updates**                    | &#x2714;                    | &#x2714;                  |
| **Detailed system and configuration information** |                             | &#x2714;                  |
| **Peripheral health management**                  |                             | &#x2714;                  |
| **Remote configuration**                          |                             | &#x2714;                  |
| **Custom backgrounds set up and management**      |                             | &#x2714;                  |
| **Device history and activity**                   |                             | &#x2714;                  |
| **ITSM integration**                              |                             | &#x2714;                  |
| **Custom health alerts**                          |                             | &#x2714;                  |
| **Device analytics**                              |                             | &#x2714;                  |


## Pro Management Portal Licensing 

### License Type Overview 
The Pro Management Portal's license type offer a clear and comprehensive summary of all devices licensing status. To access the licensing information: 
1. Use your credentials to log into the Pro Management Portal. 
2. Go to **Rooms** and **Inventory** views. 
3. In both views, locate the **License Type** column to see device licensing status. 

### Inventory View 
In the Inventory view, devices are categorized into: 
- **Pro**: Devices with pro licenses.
- **Premium**: Devices with premium licenses.
- **Basic**: Devices with basic licenses.
- **Standard**: Devices with standard licenses.
- **Syncing**: For new devices, the license information will appear 24 hours after room reboot due to syncing.
- **Unlicensed**: Devices lacking Pro, Premium, Basic, or Standard licenses.

### Rooms View
In the Rooms view, you'll find:
- **Pro**: Devices with Pro licenses.
- **Premium**: Devices with Premium licenses.
- **Basic**: Devices with basic licenses.
- **Standard**: Devices with standard licenses.
- **Syncing**: For new devices, the license information will appear 24 hours after room reboot due to syncing.
- **Unlicensed**: Devices lacking Pro, Premium, Basic, or Standard licenses.

> [!IMPORTANT]
> 
> - Please note that for Basic and Standard licenses, the presence of the red alert sign on the left side indicates that these licenses will not grant access to the Pro Management capabilities starting October 2. To continue enjoying the benefit with Pro Management capabilities, an upgrade to Pro license is required by the end of the grace period which is September 30, 2023.
> - Starting October 2, 2023 all devices without Pro or Premium licenses assigned to them will lose access to the pro management capabilities until valid licenses are assigned to them.
> - Once a license expires, access will be restricted; however, a 30 day grace period follows, preventing immediate disruptions. During this grace period, licenses can be renewed to reinstate access. Failure to renew within this period will result in loss of access.
> - When changing the account of the device, please ensure that the new account has the valid license to avoid any interruption with the device. The 30 day grace period will not be applying when using an expired account to enroll new devices or changing account on current devices.

### Troubleshooting licensing status:

If you encounter devices showing an incorrect “unlicensed” status even though they possess the proper licenses, this can result from account sign-out or improper sign-in of your devices. To resolve these issues, follow the steps outlined below: 
- For MTR-W devices, consult our documentation page on and follow the steps [here](/microsoftteams/troubleshoot/teams-rooms-and-devices/teams-rooms-resource-account-sign-in-issues) that outline how to sign in properly. 
- For MTR-A devices, kindly open an incident with the TAC team to ensure that the correct account information is sent to the service. 


## Assigning additional licenses:

Teams Rooms licenses include all necessary services for Teams Rooms functionality, and additional licenses are neither needed nor supported for these devices, with the exception of telephony. Customers requiring outbound calling features should purchase an appropriate calling plan for the device or configure direct routing for the room account. 

Teams Rooms devices managed by central IT should not be assigned any licenses beyond Microsoft Teams Rooms Pro, Microsoft Teams Rooms Basic and those required for calling. However, if a device is used by an executive to conduct meetings and access their personal calendar, it is permissible to set up the executive's user account on the device, provided the device also has a valid Microsoft Teams Rooms Pro license. The executive's account needs to satisfy the device's authentication requirements. Signing in with a user account doesn’t provide personal device experience on the device. An IT administrator should independently evaluate this scenario to determine if it aligns with company policies and permits such exceptions.


> [!IMPORTANT]
> - Microsoft Teams rooms are communal devices and should not be regarded or utilized as personal ones.
> - Avoid assigning Microsoft OneDrive for Business licenses to a Teams rooms account if the resource account is IT-managed. This can prevent user content, like recordings or transcripts, from being saved on the room's OneDrive, ensuring better content management.

