---
title: Microsoft Teams Rooms for Android security
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
description: Learn how to secure your Microsoft Teams Rooms for Android devices.
---

# Microsoft Teams Rooms for Android security

This article does **not** cover Android devices configured for dedicated device mode by Microsoft Endpoint Manager. Teams Android devices run in Kiosk mode by design. More information about Android Kiosk mode can be found [here](/mem/intune/enrollment/android-kiosk-enroll).

Microsoft works with our OEM partners to deliver a solution that is secure by design, and customizable to meet customer needs. This article discusses many of the security features found in Teams Android devices and our approach. It is split into four key sections for ease of navigation.

> [!NOTE]
> Microsoft Teams Android devices should not be treated as a typical Android device. They are purpose-built appliances designed for use with Teams, and their respective use cases. This article applies to certified and dedicated Microsoft Teams Devices running the Android Operating System only. Teams certified devices can only be purchased from certified OEM vendors. More information on Microsoft Teams Certified Android Devices can be found [here](/microsoftteams/devices/teams-ip-phones).

## Software security

### Android kiosk mode

Teams Android devices are locked down to run only approved applications by running the device in Android Kiosk Mode. Kiosk Mode disables access to any launcher capabilities and secures the device, so it only allows authorized applications to launch on the device.  

| Application Name            | Application Description                   |
|-----------------------------|-------------------------------------------|
| Microsoft Teams Android App | Microsoft Teams Device Application        |
| Microsoft Teams Admin Agent | Teams admin center Remote Management      |
| Intune Company Portal       | Device Enrollment, Registration & Sign-in |
| OEM Partner Agent           | OEM Partner Agent & Device Settings App   |

By design, the Microsoft Teams Android App will launch on start-up in Android Kiosk Mode and does not provide the user any access to the operating system or access to components outside of the designated Teams user experience.

### Application code signing

All Microsoft, and OEM applications are code signed. This validates and ensures that the software running on a device is genuine from Microsoft and our hardware partners. Application Code Signing validates the integrity of the software being run on the device, ensuring that only genuine software can launch and run.  

### Third party applications

Teams certified devices do not have the Google Play Store, Amazon App Store or Google Play Services installed by design. This ensures no third-party applications can be installed from the store onto a device.  

### Android debug bridge

Android debug bridge (ADB) is disabled by design on all Teams Android devices running release software. Android Debug Bridge is a command line tool that enables administrators to perform functions on an Android based device. ADB enables installation of apps, access to the device shell and other admin functions.  

### File system encryption

Teams Android devices must support Android-based encryption and can be enforced using Microsoft Endpoint Manager Compliance Policies. You can learn more [here](/mem/intune/protect/device-compliance-get-started).

### Android OS version

Teams Android devices run supported versions of Android. The Android Operating system is managed by OEM partners which is merged into Teams Certified Firmware and then pushed to the device from Teams admin center. You can learn more about the Android OS versions running on devices, [here](/microsoftteams/devices/teams-ip-phones).

### Android security updates

OEM vendors, as part of the firmware update process, incorporate the appropriate Android Security Update baselines to ensure the base OS is kept secure. Keeping your devices updated regularly is important to ensure the appropriate Android Security Updates are running on your device estate. For more information, please refer to your device manufacturer.

### Account security

Teams Android devices are built around two types of accounts that enable successful functioning of a device.

- Local device administrator account

- User or resource account  

Teams Android devices are also compatible with some Conditional Access policies, which can be used as additional layers of security for device sign-in. You can review our best practices, and supported policies [here](/microsoftteams/rooms/supported-ca-and-compliance-policies?tabs=mtr-w).

### Local device administrator account

Teams Android devices include an administrative account to access device settings, local web server if installed, and any OEM specific settings.

Initial device setup and configuration items such as the default username and password for this account can be obtained from the device manufacturer.

> [!CAUTION]
> Be sure to change the local device administrator password as soon as possible.  

> [!TIP]
> Teams admin center can be used to change the local device administrator password of a signed in Teams Android Device by applying a configuration profile. We recommend this approach after initial device sign in to protect elevated features of an Android device such as device settings, or web admin portals if supported.

### User or resource account

Teams Android devices require the use of a user, or dedicated resource account to sign into Microsoft 365. These accounts are secured in specific ways, depending on if it is a normal user account for a personal device, or resource account for a shared [device](/microsoftteams/rooms/with-office-365?tabs=m365-admin-center%2Cazure-active-directory2-password%2Cactive-directory2-license).

### Device updates

Teams Android devices are configured to download updates from Teams admin center when available and certified by Microsoft. These can be pushed automatically, or manually invoked by an Administrator. Third Party Tooling from our OEM Partners is also available to perform this function if required. Teams Android devices can have updates scheduled to be installed out of hours, configurable via Teams admin center or third-party tooling from OEM partners.

> [!IMPORTANT]
> Microsoft recommends the management of firmware for all Teams Android devices is done via Teams admin center.

## Network security

Teams Android devices have the same network requirements as any Microsoft Teams client. Access through firewalls and other security devices is the same for Teams Android devices as for any other Microsoft Teams client. Specifically, the categories listed as "required" for Teams must be open on your firewall, along with other supporting services as listed below. For the full list of IPs and URLs required for Teams Android devices, see:

- Microsoft Teams, Exchange Online, SharePoint Online, Microsoft 365 Common, and Office Online [Office 365 URLs and IP address range](/microsoft-365/enterprise/urls-and-ip-address-ranges)

- Microsoft Intune [Network Endpoints for Microsoft Intune](/mem/intune/fundamentals/intune-endpoints)

Teams Android devices work with most 802.1X or other network-based security protocols. However, we are not able to test Teams Android devices against all network security configurations. Therefore, if performance issues arise that can be traced to network performance issues, you may need to disable these protocols if they are configured in your organization, or contact your chosen OEM partner for assistance.

For optimum performance of real time media, we strongly recommend that you configure Teams media traffic to bypass proxy servers and other network security devices. Real time media is latency sensitive and proxy servers and network security devices can significantly degrade users' video and audio quality. Also, because Teams media is already encrypted, there is no tangible benefit from passing the traffic through a proxy server. For more information, see [Networking up (to the cloud) — One architect’s viewpoint](/microsoft-365/solutions/networking-design-principles) which discusses network recommendations to improve the performance of media with Microsoft Teams.

Teams Android devices use encrypted communications and endpoint authentication on the internet. By design, Teams Android devices use TLS 1.2+.  

> [!IMPORTANT]
> Teams Android devices do not support authenticated proxy servers or tenant restrictions. Contact your OEM partner for proxy support information.

Teams Android devices do not need to connect to an internal LAN. Consider placing Teams Android devices in a secure network segment with direct Internet access. For Teams Phone deployments this could be a Voice VLAN as example. If your internal LAN becomes compromised, the attack vector opportunities towards Teams Android devices will be reduced by implementing this network segregation.

We strongly recommend that you connect your Teams Android devices to a wired network. The use of wireless networks requires careful planning and assessment, for the best experience.

Proximity Join, Better Together, Teams Cast, and pairing of Teams panels rely on Bluetooth. Bluetooth technology use on Teams Rooms for Android devices is currently limited to advertising beacons and prompted proximal connections. The `ADV_NONCONN_INT` protocol data unit (PDU) type is used in the advertising beacon. This PDU type is for non-connectable devices advertising information to the listening device. There is no Bluetooth device pairing as part of these features. Additional details on Bluetooth protocols can be found on the Bluetooth SIG website.

Teams Phones and Displays offers Bluetooth pairing capability to pair with headsets using the HFP profile.

For further information on security in Microsoft Teams, check out this [page](/microsoftteams/teams-security-guide).  
