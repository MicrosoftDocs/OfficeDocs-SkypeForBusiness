---
title: Microsoft Teams Rooms security
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: kimmatlock
ms.date: 03/19/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devicesf
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: Learn how to secure your Microsoft Teams Rooms on Windows and Android devices.
---

# Microsoft Teams Rooms security

This article provides security guidance for Microsoft Teams Rooms devices on both Windows and Android devices. This guidance includes information on hardware, software, network, and account security. 

Select the **Teams Rooms on Windows** or **Teams Rooms for Android** tab for more information on Teams Room security on your device.

## [Teams Rooms on Windows](#tab/Windows)

Microsoft works with our partners to deliver a solution that is secure and doesn't require extra actions to secure Microsoft Teams Rooms on Windows. This section discusses many of the security features found in Teams Rooms on Windows.

For information about security on Teams Rooms on Android devices, select the **Teams Rooms on Android** tab.

> [!NOTE]
> Microsoft Teams Rooms should not be treated like a typical end-user workstation. Not only are the use cases vastly different, but the default security profiles are also much different, we recommend treating them as appliances. Installing additional software on your Teams Rooms devices is not supported by Microsoft.
> This article applies to Microsoft Teams Rooms devices running on Windows.

Limited end-user data is stored on Teams Rooms. End-user data may be stored in the log files for troubleshooting and support only. No attendees of a meeting using Teams Rooms can copy files to the hard drive or sign in as themselves. No end-user data is transferred to, or accessible by, the Microsoft Teams Rooms device.

Even though end users can't put files on a Teams Rooms hard drive, Microsoft Defender is still enabled out of the box. Teams Rooms performance is tested with Microsoft Defender, including enrolling into the Defender for Endpoint portal. Disabling this or adding endpoint security software can lead to unpredictable results and potential system degradation.

## Hardware security

In a Teams Rooms environment, there's a central compute module that runs Windows 10 or 11 IoT Enterprise edition. Every certified compute module must have a secure mounting solution, a security lock slot (for example, Kensington lock), and I/O port access security measures to prevent the connection of unauthorized devices. You can also disable specific ports via Unified Extensible Firmware Interface (UEFI) configuration.

Every certified compute module must ship with Trusted Platform Module (TPM) 2.0 compliant technology enabled by default. TPM is used to encrypt the login information for the Teams Rooms resource account.

Secure boot is enabled by default. Secure boot is a security standard developed by members of the PC industry to help make sure that a device boots using only software trusted by the Original Equipment Manufacturer (OEM). When the PC starts, the firmware checks the signature of each piece of boot software, including UEFI firmware drivers (also known as Option ROMs), EFI applications, and the operating system. If the signatures are valid, the PC boots, and the firmware gives control to the operating system. For more information, see [Secure boot](/windows-hardware/design/device-experiences/oem-secure-boot).

Access to UEFI settings is only possible by attaching a physical keyboard and mouse, which prevents being able to access UEFI via the Teams Rooms touch-enabled console or any other touch-enabled displays attached to Teams Rooms.

Kernel Direct Memory Access (DMA) Protection is a Windows setting that is enabled on Teams Rooms. With this feature, the OS and the system firmware protect the system against malicious and unintended DMA attacks for all DMA-capable devices:

- During the boot process.

- Against malicious DMA by devices connected to easily accessible internal/external DMA-capable ports, such as M.2 PCIe slots and Thunderbolt 3, during OS runtime.

Teams Rooms also enables Hypervisor-protected code integrity (HVCI). One of the features provided by HVCI is Credential Guard. Credential Guard provides the following benefits:

- **Hardware security** NTLM, Kerberos, and Credential Manager take advantage of platform security features, including Secure Boot and virtualization, to protect credentials.

- **Virtualization-based security** Windows NTLM and Kerberos derived credentials and other secrets run in a protected environment that is isolated from the running operating system.

- **Better protection against advanced persistent threats** When Credential Manager domain credentials, NTLM, and Kerberos derived credentials are protected using virtualization-based security, the credential theft attack techniques, and tools used in many targeted attacks are blocked. Malware running in the operating system with administrative privileges can't extract secrets that are protected by virtualization-based security.

## Software Security

After Microsoft Windows boots, Teams Rooms automatically signs into a local Windows user account named Skype. The Skype account has no password. To make the Skype account session secure, the following steps are taken.

> [!IMPORTANT]
> Don't change the password or edit the local Skype user account. Doing so can prevent Teams Rooms from automatically signing in.

The Microsoft Teams Rooms app runs using the Assigned Access feature found in Windows 10 1903 and later. Assigned Access is a feature in Windows that limits the application entry points exposed to the user and enables single-app kiosk mode. Using Shell Launcher, Teams Rooms is configured as a kiosk device that runs a Windows desktop application as the user interface. The Microsoft Teams Rooms app replaces the default shell (explorer.exe) that usually runs when a user logs on. In other words, the traditional Explorer shell doesn't get launched at all which greatly reduces the Microsoft Teams Rooms vulnerability surface within Windows. For more information, see [Configure kiosks and digital signs on Windows desktop editions](/windows/configuration/kiosk-methods).

If you decide to run a security scan or a Center for Internet Security (CIS) benchmark on Teams Rooms, the scan can only run under the context of a local administrator account as the Skype user account doesn't support running applications other than the Teams Rooms app. Many of the security features applied to the Skype user context don't apply to other local users and, as a result, these security scans don't surface the full security lockdown applied to the Skype account. Therefore, we don't recommend to running a local scan on Teams Rooms. However, you can run external penetration tests if so desired. Because of this, we recommend that you run external penetration tests against Teams Rooms devices instead of running local scans.

Additionally, lock down policies are applied to limit nonadministrative features from being used. A keyboard filter is enabled to intercept and block potentially insecure keyboard combinations that aren't covered by Assigned Access policies. Only users with local or domain administrative rights are permitted to sign into Windows to manage Teams Rooms. These and other policies applied to Windows on Microsoft Teams Rooms devices are continually assessed and tested during the product lifecycle.

Microsoft Defender is enabled out of the box, the Teams Rooms Pro license also includes Defender for Endpoint, which allows customers to enroll their Teams Rooms into Defender for Endpoint to provide security teams visibility into the security posture of Teams Room on Windows devices from the Defender portal. Teams Rooms on Windows can be enrolled following the steps for [Windows devices](/microsoft-365/security/defender-endpoint/onboarding-endpoint-manager). We don't recommend modifying Teams Rooms using protection rules (or other Defender policies that make configuration changes) as these policies can impact Teams Rooms functionality; however, reporting functionality into the portal is supported.

## Account Security

Teams Rooms devices include an administrative account named "Admin" with a default password. We strongly recommend that you change the default password as soon as possible after you complete setup.

The Admin account isn't required for proper operation of Teams Rooms devices and can be renamed or even deleted. However, before you delete the Admin account, make sure that you set up an alternate local administrator account configured before removing the one that ships with Teams Rooms devices. For more information on how to change a password for a local Windows account using built-in Windows tools or PowerShell, see the following:

- [Configuring LAPS on Teams Rooms on Windows](/microsoftteams/rooms/laps-authentication)
- [Change or reset your Windows password](https://support.microsoft.com/windows/change-or-reset-your-windows-password-8271d17c-9f9e-443f-835a-8318c8f68b9c)
- [Set-LocalUser](/powershell/module/microsoft.powershell.localaccounts/set-localuser#example-2--change-the-password-on-an-account)

You can also import domain accounts into the local Windows Administrator group by using Intune. For more information, see [Policy CSP – RestrictedGroups.](/windows/client-management/mdm/policy-csp-restrictedgroups).

> [!NOTE]
> If you are using a Crestron Teams Rooms with a network connected console, ensure you follow Crestron's guidance for how to configure the Windows account used for pairing.

> [!CAUTION]
> If you delete or disable the Admin account before granting local Administrator permissions to another local or domain account, you may lose the ability to administer the Teams Rooms device. If this happens, you'll need to reset the device back to its original settings and complete the setup process again.

Don't grant local Administrator permissions to the Skype user account.

Windows Configuration Designer can be used to create Windows provisioning packages. Along with changing the local Admin password, you can also do things like changing the machine name and enrolling into Microsoft Entra ID. For more information on creating a Windows Configuration Designer provisioning package, see [Provisioning packages for Windows 10](/windows/configuration/provisioning-packages/provisioning-packages).

You need to create a resource account for each Teams Rooms device so that it can sign into Teams. You can't use user interactive two-factor or multi-factor authentication with this account. Requiring a second factor would prevent the account from being able to automatically sign into the Teams Rooms app after a reboot. In addition, Microsoft Entra Conditional Access policies and Intune Compliance Policies can be deployed to secure the resource account. For more information, see [Supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms](supported-ca-and-compliance-policies.md) and [Conditional Access and Intune compliance for Microsoft Teams Rooms](conditional-access-and-compliance-for-devices.md).

We recommend that you create the resource account in Microsoft Entra ID, if possible as a cloud-only account. While a synced account can work with Teams Rooms in hybrid deployments, these synced accounts often have difficulty signing into Teams Rooms and can be difficult to troubleshoot. If you choose to use a third-party federation service to authenticate the credentials for the resource account, ensure the third-party IDP responds with the `wsTrustResponse` attribute set to `urn:oasis:names:tc:SAML:1.0:assertion`. If your organization doesn't want to use WS-Trust, use cloud-only accounts instead.

## Network Security

Generally, Teams Rooms has the same network requirements as any Microsoft Teams client. Access through firewalls and other security devices is the same for Teams Rooms as for any other Microsoft Teams client. Specific to Teams Rooms, the categories listed as "required" for Teams must be open on your firewall. Teams Rooms also needs access to Windows Update, Microsoft Store, and Microsoft Intune (if you use Microsoft Intune to manage your devices). For the full list of IPs and URLs required for Microsoft Teams Rooms, see:

- **Microsoft Teams, Exchange Online, SharePoint Online, Microsoft 365 Common, and Office Online** [Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams)
- **Windows Update** [Configure WSUS](/windows-server/administration/windows-server-update-services/deploy/2-configure-wsus#211-connection-from-the-wsus-server-to-the-internet)
- **Microsoft Store** [Prerequisites for Microsoft Store for Business and Education](/microsoft-store/prerequisites-microsoft-store-for-business#proxy-configuration)
- **Microsoft Intune** [Network Endpoints for Microsoft Intune](/mem/intune/fundamentals/intune-endpoints)

If you're using the Microsoft Teams Rooms managed services component of Microsoft Teams Rooms Pro, you also need to make sure that Teams Rooms can access the following URLs:

- agent.rooms.microsoft.com
- global.azure-devices-provisioning.net
- gj3ftstorage.blob.core.windows.net
- mmrstgnoamiot.azure-devices.net
- mmrstgnoamstor.blob.core.windows.net
- mmrprodapaciot.azure-devices.net
- mmrprodapacstor.blob.core.windows.net
- mmrprodemeaiot.azure-devices.net
- mmrprodemeastor.blob.core.windows.net
- mmrprodnoamiot.azure-devices.net
- mmrprodnoamstor.blob.core.windows.net

**GCC customers will also need to enable the following URLs:**

- mmrprodgcciot.azure-devices.net
- mmrprodgccstor.blob.core.windows.net

Teams Rooms is configured to automatically keep itself patched with the latest Windows updates, including security updates. Teams Rooms installs any pending updates every day beginning at 2:00am using a preset local policy. There's no need to use other tools to deploy and apply Windows Updates. Using other tools to deploy and apply updates can delay the installation of Windows patches and thus lead to a less secure deployment. The Teams Rooms app is deployed using the Microsoft Store.

Teams Rooms devices work with most 802.1X or other network-based security protocols. However, we're not able to test Teams Rooms against all possible network security configurations. Therefore, if performance issues arise that can be traced to network performance issues, you may need to disable these protocols.

For optimum performance of real time media, we strongly recommend that you configure Teams media traffic to bypass proxy servers and other network security devices. Real time media is very latency sensitive and proxy servers and network security devices can significantly degrade users' video and audio quality. Also, because Teams media is already encrypted, there's no tangible benefit from passing the traffic through a proxy server. For more information, see [Networking up (to the cloud)—One architect’s viewpoint](/microsoft-365/solutions/networking-design-principles), which discusses network recommendations to improve the performance of media with Microsoft Teams and Microsoft Teams Rooms.

> [!IMPORTANT]
> Teams Rooms doesn't support authenticated proxy servers.

Teams Rooms devices don't need to connect to an internal LAN. Consider placing Teams Rooms in a secure isolated network segment with direct Internet access. If your internal LAN becomes compromised, the attack vector opportunities towards Teams Rooms is reduced.

We strongly recommend that you connect your Teams Rooms devices to a wired network. The use of wireless networks requires careful planning and assessment for the best experience. For more information, see [Wireless network considerations](rooms-plan.md#wireless-network-considerations).

Proximity Join and other Teams Rooms features rely on Bluetooth. However, the Bluetooth implementation on Teams Rooms devices doesn't allow for an external device connection to a Teams Rooms device. Bluetooth technology use on Teams Rooms devices is currently limited to advertising beacons and prompted proximal connections. The `ADV_NONCONN_INT` protocol data unit (PDU) type is used in the advertising beacon. This PDU type is for nonconnectable devices advertising information to the listening device. There's no Bluetooth device pairing as part of these features. Additional details on Bluetooth protocols can be found on the [Bluetooth SIG website](https://www.bluetooth.com/blog/bluetooth-low-energy-it-starts-with-advertising/).

## [Teams Rooms on Android](#tab/Android)

This article doesn't cover Android devices configured for dedicated device mode by Microsoft Endpoint Manager. Teams Android devices run in Kiosk mode by design. For information about Android Kiosk, see [Android Enterprise dedicated device enrollment](/mem/intune/enrollment/android-kiosk-enroll).

Microsoft works with our OEM partners to deliver a solution that is secure by design, and customizable to meet customer needs. This article discusses many of the security features found in Teams Android devices and our approach. It's split into four key sections for ease of navigation.

> [!NOTE]
> Microsoft Teams Android devices shouldn't be treated as a typical Android device. Teams Android devices are purpose-built appliances designed for use with Teams and their respective use cases. This article applies to certified and dedicated Microsoft Teams devices running the Android operating system only. Teams certified devices can only be purchased from certified OEM vendors. For information about Microsoft Teams certified Android devices, see [Teams Rooms certified systems and peripherals](certified-hardware.md).

For information about security on Teams Rooms on Windows devices, select the **Teams Rooms on Windows** tab.

## Software security

### Android kiosk mode

Teams Android devices are locked down to run only approved applications by running the device in Android Kiosk mode. Kiosk mode disables access to any launcher capabilities and helps to secure the device so authorized applications launch on the device.  

| Application Name            | Application Description                   |
|-----------------------------|-------------------------------------------|
| Microsoft Teams Android App | Microsoft Teams Device Application        |
| Microsoft Teams Admin Agent | Teams admin center Remote Management      |
| Intune Company Portal       | Device Enrollment, Registration & Sign-in |
| OEM Partner Agent           | OEM Partner Agent & Device Settings App   |

By design, the Microsoft Teams Android app launches on start-up in Android Kiosk mode and doesn't provide the user any access to the operating system or access to components outside of the designated Teams user experience.

### Application code signing

All Microsoft and OEM applications are code signed. Code signing helps validating that the software running on a device is genuine from Microsoft and our hardware partners. Code signing also attempts to validate the integrity of the software being run on the device, such that only genuine software can launch and run.  

### Third party applications

Teams certified devices don't have the Google Play Store, Amazon App Store, or Google Play Services, installed by design. This helps to ensure that no third-party applications can be installed from the store onto a device.  

### Android debug bridge

Android debug bridge (ADB) is disabled by design on all Teams Android devices running release software. ADB is a command line tool that enables administrators to perform functions on Android-based devices and enables installation of apps, access to the device shell, and other admin functions.  

### File system encryption

Teams Android devices must support Android-based encryption and can be enforced using Microsoft Endpoint Manager compliance policies. For information about Endpoint Manager compliance policies [Use Endpoint Manager compliance policies to set rules for devices you manage with Intune](/mem/intune/protect/device-compliance-get-started).

### Android OS version

Teams Android devices run supported versions of Android. The Android operating system is managed by OEM partners, merged into Teams certified firmware, and then pushed to devices from the Teams admin center. For information about which Android versions are running on Teams Android devices, see [[Microsoft Teams certified Android devices](/microsoftteams/devices/teams-ip-phones)](android-app-firmware.md).

### Android security updates

OEM vendors, as part of the firmware update process, incorporate the appropriate Android security update baselines to help ensure the base operating system is kept secure. Keeping your devices updated regularly is important to ensure the appropriate Android security updates are running on your devices. For more information, please refer to your device manufacturer.

### Account security

Teams Android devices are built around two types of accounts that enable successful functioning of a device.

- Local device administrator account

- User or resource account  

Teams Android devices are also compatible with some conditional access policies, which can be used as more layers of security for device sign-in. For best practices and supported conditional access policies, see [Supported conditional access compliance policies](/microsoftteams/rooms/supported-ca-and-compliance-policies).

### Local device administrator account

Teams Android devices include an administrative account to access device settings, the local web server if one's installed, and any OEM specific settings.

Initial device setup and configuration items such as the default username and password for this account can be obtained from the device manufacturer.

> [!CAUTION]
> Be sure to change the local device administrator password as soon as possible.  

> [!TIP]
> The Teams admin center can be used to change the local device administrator password of a signed-in Teams Android device by applying a configuration profile. We recommend this approach after initial device sign-in to protect elevated features of an Android device. Elevated features can include device settings and web admin portals if they're supported.

### User or resource account

Teams Android devices require the use of a user, or dedicated resource account, to sign into Microsoft 365. We attempt to secure these accounts in specific ways, depending on if it's a user account for a personal device or a resource account for a shared device. For more information, see [Create and configure resource accounts for rooms and shared devices](/microsoftteams/rooms/create-resource-account).

### Device updates

Teams Android devices are configured to download Microsoft-certified updates from the Teams admin center when they become available. These updates can be pushed automatically or manually invoked by an Administrator. Third-party tools from our OEM partners is also available to perform this function if necessary. Teams Android devices can install updates after hours to avoid impact to users. After hours schedules can be configured in the Teams admin center or using third-party tools from OEM partners.

> [!IMPORTANT]
> Microsoft recommends the management of firmware for all Teams Android devices is done via the Teams admin center.

## Network security

Teams Android devices have the same network requirements as any Microsoft Teams client, including access through firewalls and other security devices. Specifically, the categories listed as **required** for Teams must be open on your firewall along with other supporting services as listed below. For the full list of IPs and URLs required for Teams Android devices, see:

- Microsoft Teams, Exchange Online, SharePoint Online, Microsoft 365 Common, and Office Online [Office 365 URLs and IP address range](/microsoft-365/enterprise/urls-and-ip-address-ranges)

- Microsoft Intune [Network Endpoints for Microsoft Intune](/mem/intune/fundamentals/intune-endpoints)

Teams Android devices work with most 802.1X and other network-based security protocols. However, we can't test Teams Android devices against all network security configurations. Therefore, if performance issues arise that can be traced to network performance issues, you may need to disable these protocols if they're configured in your organization, or contact your OEM partner for assistance.

For optimum performance of real time media, we strongly recommend that you configure Teams media traffic to bypass proxy servers and other network security devices. Real time media is sensitive to network latency, which can be caused by proxy servers and other network security devices. Network latency can significantly degrade users' video and audio quality. For more information, see [Networking up (to the cloud)—One architect’s viewpoint](/microsoft-365/solutions/networking-design-principles), which discusses network recommendations to improve the performance of media with Microsoft Teams.

Teams Android devices use encrypted communications and endpoint authentication on the internet. Teams Android devices use TLS 1.2+.  

> [!IMPORTANT]
> Teams Android devices don't support authenticated proxy servers or tenant restrictions. Contact your OEM partner for proxy support information.

Teams Android devices don't need to connect to an internal LAN. Consider placing Teams Android devices in a secure network segment with direct Internet access. For example, Teams Phones could be deployed on a voice VLAN. If your internal LAN becomes compromised, the attack vector opportunities towards Teams Android devices is reduced by implementing this network segregation.

We strongly recommend that you connect your Teams Rooms devices to a wired network. The use of wireless networks requires careful planning and assessment for the best experience. For more information, see [Wireless network considerations](rooms-plan.md#wireless-network-considerations).

Proximity Join, Better Together, Teams Cast, and pairing of Teams panels rely on Bluetooth. Bluetooth technology use on Teams Rooms on Android devices is currently limited to advertising beacons and prompted proximal connections. The `ADV_NONCONN_INT` protocol data unit (PDU) type is used in the advertising beacon. This PDU type is for nonconnectable devices advertising information to the listening device. There's no Bluetooth device pairing as part of these features. More details on Bluetooth protocols can be found on the Bluetooth SIG website.

Teams Phones and Displays offers Bluetooth pairing capability to pair with headsets using the Bluetooth Hands-Free Profile.

For more information on security in Microsoft Teams, see [Security and Microsoft Teams](/microsoftteams/teams-security-guide).  
