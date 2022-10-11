---
title: Microsoft Teams for Android security
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
appliesto: 
  - Microsoft Teams
ms.reviewer: sohailta
ms.topic: article
ms.service: msteams
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
description: Learn how to secure your Microsoft Teams for Android devices.
---

# Microsoft Teams for Android security

This article doesn't cover Android devices configured for dedicated device mode by Microsoft Endpoint Manager. Teams Android devices run in Kiosk mode by design. For information about Android Kiosk, see [Android Enterprise dedicated device enrollment](/mem/intune/enrollment/android-kiosk-enroll).

Microsoft works with our OEM partners to deliver a solution that is secure by design, and customizable to meet customer needs. This article discusses many of the security features found in Teams Android devices and our approach. It is split into four key sections for ease of navigation.

> [!NOTE]
> Microsoft Teams Android devices shouldn't be treated as a typical Android device. Teams Android devices are purpose-built appliances designed for use with Teams and their respective use cases. This article applies to certified and dedicated Microsoft Teams devices running the Android operating system only. Teams certified devices can only be purchased from certified OEM vendors. For information about Microsoft Teams certified Android devices, see [Microsoft Teams certified Android devices](/microsoftteams/devices/teams-ip-phones).

For information about security on Teams Rooms for Windows devices, see [Microsoft Teams Rooms for Windows security](security-windows.md).

## Software security

### Android kiosk mode

Teams Android devices are locked down to run only approved applications by running the device in Android Kiosk mode. Kiosk mode disables access to any launcher capabilities and helps to secure the device so authorized applications launch on the device.  

| Application Name            | Application Description                   |
|-----------------------------|-------------------------------------------|
| Microsoft Teams Android App | Microsoft Teams Device Application        |
| Microsoft Teams Admin Agent | Teams admin center Remote Management      |
| Intune Company Portal       | Device Enrollment, Registration & Sign-in |
| OEM Partner Agent           | OEM Partner Agent & Device Settings App   |

By design, the Microsoft Teams Android app will launch on start-up in Android Kiosk mode and doesn't provide the user any access to the operating system or access to components outside of the designated Teams user experience.

### Application code signing

All Microsoft and OEM applications are code signed. Code signing assists in validating that the software running on a device is genuine from Microsoft and our hardware partners. Code signing also attempts to validate the integrity of the software being run on the device, such that only genuine software can launch and run.  

### Third party applications

Teams certified devices don't have the Google Play Store, Amazon App Store, or Google Play Services, installed by design. This helps to ensure that no third-party applications can be installed from the store onto a device.  

### Android debug bridge

Android debug bridge (ADB) is disabled by design on all Teams Android devices running release software. ADB is a command line tool that enables administrators to perform functions on Android-based devices and enables installation of apps, access to the device shell, and other admin functions.  

### File system encryption

Teams Android devices must support Android-based encryption and can be enforced using Microsoft Endpoint Manager compliance policies. For information about Endpoint Manager compliance policies [Use Endpoint Manager compliance policies to set rules for devices you manage with Intune](/mem/intune/protect/device-compliance-get-started).

### Android OS version

Teams Android devices run supported versions of Android. The Android operating system is managed by OEM partners, merged into Teams certified firmware, and then pushed to devices from the Teams admin center. For information about which Android versions are running on Teams Android devices, see [Microsoft Teams certified Android devices](/microsoftteams/devices/teams-ip-phones).

### Android security updates

OEM vendors, as part of the firmware update process, incorporate the appropriate Android security update baselines to help ensure the base operating system is kept secure. Keeping your devices updated regularly is important to ensure the appropriate Android security updates are running on your devices. For more information, please refer to your device manufacturer.

### Account security

Teams Android devices are built around two types of accounts that enable successful functioning of a device.

- Local device administrator account

- User or resource account  

Teams Android devices are also compatible with some conditional access policies, which can be used as additional layers of security for device sign-in. For best practices and supported conditional access policies, see [Supported conditional access compliance policies](/microsoftteams/rooms/supported-ca-and-compliance-policies).

### Local device administrator account

Teams Android devices include an administrative account to access device settings, the local web server if one's installed, and any OEM specific settings.

Initial device setup and configuration items such as the default username and password for this account can be obtained from the device manufacturer.

> [!CAUTION]
> Be sure to change the local device administrator password as soon as possible.  

> [!TIP]
> The Teams admin center can be used to change the local device administrator password of a signed-in Teams Android device by applying a configuration profile. We recommend this approach after initial device sign-in to protect elevated features of an Android device. Elevated features can include device settings and web admin portals if they're supported.

### User or resource account

Teams Android devices require the use of a user, or dedicated resource account, to sign into Microsoft 365. We attempt to secure these accounts in specific ways, depending on if it's a normal user account for a personal device or a resource account for a shared device. For more information, see [Create and configure resource accounts for rooms and shared devices](/microsoftteams/rooms/with-office-365).

### Device updates

Teams Android devices are configured to download Microsoft-certified updates from the Teams admin center when they become available. These can be pushed automatically or manually invoked by an Administrator. Third-party tools from our OEM partners is also available to perform this function if required. Teams Android devices can install updates after hours to avoid impact to users. After hours schedules can be configured in the Teams admin center or using third-party tools from OEM partners.

> [!IMPORTANT]
> Microsoft recommends the management of firmware for all Teams Android devices is done via the Teams admin center.

## Network security

Teams Android devices have the same network requirements as any Microsoft Teams client, including access through firewalls and other security devices. Specifically, the categories listed as **required** for Teams must be open on your firewall along with other supporting services as listed below. For the full list of IPs and URLs required for Teams Android devices, see:

- Microsoft Teams, Exchange Online, SharePoint Online, Microsoft 365 Common, and Office Online [Office 365 URLs and IP address range](/microsoft-365/enterprise/urls-and-ip-address-ranges)

- Microsoft Intune [Network Endpoints for Microsoft Intune](/mem/intune/fundamentals/intune-endpoints)

Teams Android devices work with most 802.1X and other network-based security protocols. However, we can't test Teams Android devices against all network security configurations. Therefore, if performance issues arise that can be traced to network performance issues, you may need to disable these protocols if they are configured in your organization, or contact your OEM partner for assistance.

For optimum performance of real time media, we strongly recommend that you configure Teams media traffic to bypass proxy servers and other network security devices. Real time media is sensitive to network latency, which can be caused by proxy servers and other network security devices. Network latency can significantly degrade users' video and audio quality. For more information, see [Networking up (to the cloud) — One architect’s viewpoint](/microsoft-365/solutions/networking-design-principles?view=o365-worldwide) which discusses network recommendations to improve the performance of media with Microsoft Teams.

Teams Android devices use encrypted communications and endpoint authentication on the internet. Teams Android devices use TLS 1.2+.  

> [!IMPORTANT]
> Teams Android devices don't support authenticated proxy servers or tenant restrictions. Contact your OEM partner for proxy support information.

Teams Android devices don't need to connect to an internal LAN. Consider placing Teams Android devices in a secure network segment with direct Internet access. For example, Teams Phones could be deployed on a voice VLAN. If your internal LAN becomes compromised, the attack vector opportunities towards Teams Android devices will be reduced by implementing this network segregation.

We strongly recommend that you connect your Teams Android devices to a wired network. The use of wireless networks requires careful planning and assessment for the best experience.

Proximity Join, Better Together, Teams Cast, and pairing of Teams panels rely on Bluetooth. Bluetooth technology use on Teams Rooms for Android devices is currently limited to advertising beacons and prompted proximal connections. The `ADV_NONCONN_INT` protocol data unit (PDU) type is used in the advertising beacon. This PDU type is for non-connectable devices advertising information to the listening device. There is no Bluetooth device pairing as part of these features. Additional details on Bluetooth protocols can be found on the Bluetooth SIG website.

Teams Phones and Displays offers Bluetooth pairing capability to pair with headsets using the Bluetooth Hands-Free Profile.

For more information on security in Microsoft Teams, see [Security and Microsoft Teams](/microsoftteams/teams-security-guide).  
