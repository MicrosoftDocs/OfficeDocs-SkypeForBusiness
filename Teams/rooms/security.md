---
title: "Microsoft Teams Rooms Security"
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
description: Learn how to secure your Microsoft Teams Rooms devices.
---

# Microsoft Teams Rooms Security

Microsoft works with our partners to deliver a solution that is secure and doesn't require additional actions to secure Microsoft Teams Rooms. This article discusses many of the security features found in Teams Rooms.

> [!NOTE]
> Microsoft Teams Rooms should not be treated like a typical end-user workstation. Not only are the use cases vastly different, but the default security profiles are also much different.
> This article applies to Microsoft Teams Rooms devices running on Windows.

Limited end-user data is stored on Teams Rooms. End-user data may be stored in the log files for troubleshooting and support only. At no point can an attendee of a meeting using Teams Rooms copy files to the hard drive or sign in as themselves. No end-user data is transferred to, or accessible by, the Microsoft Teams Rooms device.

Even though end users can't put files on a Teams Rooms hard drive, Microsoft Defender is still enabled. Teams Rooms performance is tested with Microsoft Defender. Disabling this or adding endpoint security software can lead to unpredictable results and potential system degradation.

## Hardware security

In a Teams Rooms environment, there's a central compute module that runs Windows 10 IoT Enterprise edition. Every certified compute module must have a secure mounting solution, a security lock slot (for example, Kensington lock), and I/O port access security measures to prevent the connection of unauthorized devices. You can also disable specific ports via Unified Extensible Firmware Interface (UEFI) configuration.

Every certified compute module must ship with Trusted Platform Module (TPM) 2.0 compliant technology enabled by default. TPM is used to encrypt the login information for the Teams Rooms resource account.

Secure boot is enabled by default. Secure boot is a security standard developed by members of the PC industry to help make sure that a device boots using only software that is trusted by the Original Equipment Manufacturer (OEM). When the PC starts, the firmware checks the signature of each piece of boot software, including UEFI firmware drivers (also known as Option ROMs), EFI applications, and the operating system. If the signatures are valid, the PC boots, and the firmware gives control to the operating system. For more information, see [Secure boot](/windows-hardware/design/device-experiences/oem-secure-boot).

Access to UEFI settings is only possible by attaching a physical keyboard and mouse. This prevents being able to access UEFI via the Teams Rooms touch-enabled console as well as any other touch-enabled displays attached to Teams Rooms.

Kernel Direct Memory Access (DMA) Protection is a Windows 10 setting that is enabled on Teams Rooms. With this feature, the OS and the system firmware protect the system against malicious and unintended DMA attacks for all DMA-capable devices:

- During the boot process.

- Against malicious DMA by devices connected to easily accessible internal/external DMA-capable ports, such as M.2 PCIe slots and Thunderbolt 3, during OS runtime.

Teams Rooms also enables Hypervisor-protected code integrity (HVCI). One of the features provided by HVCI is Credential Guard. Credential Guard provides the following benefits:

- **Hardware security** NTLM, Kerberos, and Credential Manager take advantage of platform security features, including Secure Boot and virtualization, to protect credentials.

- **Virtualization-based security** Windows NTLM and Kerberos derived credentials and other secrets run in a protected environment that is isolated from the running operating system.

- **Better protection against advanced persistent threats** When Credential Manager domain credentials, NTLM, and Kerberos derived credentials are protected using virtualization-based security, the credential theft attack techniques and tools used in many targeted attacks are blocked. Malware running in the operating system with administrative privileges can't extract secrets that are protected by virtualization-based security.

## Software Security

After Microsoft Windows boots, Teams Rooms automatically signs into a local Windows user account named Skype. The Skype account has no password. To make the Skype account session secure, the following steps are taken.

> [!IMPORTANT]
> Don't change the password or edit the local Skype user account. Doing so can prevent Teams Rooms from automatically signing in.

The Microsoft Teams Rooms app runs using the Assigned Access feature found in Windows 10 1903 and later. Assigned Access is a feature in Windows 10 that limits the application entry points exposed to the user. This is what enables single-app kiosk mode. Using Shell Launcher, Teams Rooms is configured as a kiosk device that runs a Windows desktop application as the user interface. The Microsoft Teams Rooms app replaces the default shell (explorer.exe) that usually runs when a user logs on. In other words, the traditional Explorer shell does not get launched at all. This greatly reduces the Microsoft Teams Rooms vulnerability surface within Windows. For more information, see [Configure kiosks and digital signs on Windows desktop editions](/windows/configuration/kiosk-methods).

If you decide to run a security scan or a Center for Internet Security (CIS) benchmark on Teams Rooms, the scan can only run under the context of a local administrator account as the Skype user account doesn't support running applications other than the Teams Rooms app. Many of the security features applied to the Skype user context don't apply to other local users and, as a result, these security scans won't surface the full security lockdown applied to the Skype account. Therefore, it is not recommended to run a local scan on Teams Rooms. However, you can run external penetration tests if so desired. Because of this, we recommend that you run external penetration tests against Teams Rooms devices instead of running local scans.

Additionally, lock down policies are applied to limit non-administrative features from being used. A keyboard filter is enabled to intercept and block potentially insecure keyboard combinations that aren't covered by Assigned Access policies. Only users with local or domain administrative rights are permitted to sign into Windows to manage Teams Rooms. These and other policies applied to Windows on Microsoft Teams Rooms devices are continually assessed and tested during the product lifecycle.

## Account Security

Teams Rooms devices include an administrative account named "Admin" with a default password. We strongly recommend that you change the default password as soon as possible after you complete setup.

The Admin account isn't required for proper operation of Teams Rooms devices and can be renamed or even deleted. However, before you delete the Admin account, make sure that you set up an alternate local administrator account configured before removing the one that ships with Teams Rooms devices. For more information on how to change a password for a local Windows account using built-in Windows tools or PowerShell, see the following:

- [Change or reset your Windows password](https://support.microsoft.com/windows/change-or-reset-your-windows-password-8271d17c-9f9e-443f-835a-8318c8f68b9c)
- [Set-LocalUser](/powershell/module/microsoft.powershell.localaccounts/set-localuser?view=powershell-5.1#example-2--change-the-password-on-an-account)

You can also import domain accounts into the local Windows Administrator group. You can do this for Azure AD accounts by using Intune. For more information, see [Policy CSP – RestrictedGroups.](/windows/client-management/mdm/policy-csp-restrictedgroups).

> [!NOTE]
> If you are using Crestron consoles, be sure to also update the Admin password on the console as well as on the compute module. For more information, contact Crestron.

> [!CAUTION]
> If you delete or disable the Admin account before granting local Administrator permissions to another local or domain account, you may lose the ability to administer the Teams Rooms device. If this happens, you'll need to reset the device back to its original settings and complete the setup process again.

Don't grant local Administrator permissions to the Skype user account.

Windows Configuration Designer can be used to create Windows 10 provisioning packages. Along with changing the local Admin password, you can also do things like changing the machine name and enrolling into Azure Active Directory. For more information on creating a Windows Configuration Designer provisioning package, see [Provisioning packages for Windows 10](/windows/configuration/provisioning-packages/provisioning-packages).

You need to create a resource account for each Teams Rooms device so that it can sign into Teams. You can't use two-factor or multi-factor authentication with this account. Requiring a second factor would prevent the account from being able to automatically sign into the Teams Rooms app after a reboot. However, you can enable Modern Authentication for additional security for this account. In addition, Azure Active Directory Conditional Access policies and Intune Compliance Policies can be deployed to secure the resource account. For more information, see [Supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms](supported-ca-and-compliance-policies.md) and [Conditional Access and Intune compliance for Microsoft Teams Rooms](conditional-access-and-compliance-for-devices.md)

We recommend that you create the resource account in Azure AD, if possible. While a synced account can work with Teams Rooms in hybrid deployments, these synced accounts often have difficulty signing into Teams Rooms and can be difficult to troubleshoot. If you choose to use a third-party federation service to authenticate the credentials for the resource account, ensure the third-party IDP responds with the `wsTrustResponse` attribute set to `urn:oasis:names:tc:SAML:1.0:assertion`.

## Network Security

Generally, Teams Rooms has the same network requirements as any Microsoft Teams client. Access through firewalls and other security devices is the same for Teams Rooms as for any other Microsoft Teams client. Specific to Teams Rooms, the categories listed as "required" for Teams must be open on your firewall. Teams Rooms also needs access to Windows Update, Microsoft Store, and Microsoft Intune (if you use Microsoft Intune to manage your devices). For the full list of IPs and URLs required for Microsoft Teams Rooms, see:

- **Microsoft Teams** [Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide#skype-for-business-online-and-microsoft-teams)
- **Windows Update** [Configure WSUS](/windows-server/administration/windows-server-update-services/deploy/2-configure-wsus#211-connection-from-the-wsus-server-to-the-internet)
- **Microsoft Store** [Prerequisites for Microsoft Store for Business and Education](/microsoft-store/prerequisites-microsoft-store-for-business#proxy-configuration)
- **Microsoft Intune** [Network Endpoints for Microsoft Intune](/mem/intune/fundamentals/intune-endpoints)

If you're using the Microsoft Teams Rooms managed services component of Microsoft Teams Rooms Premium, you also need to make sure that Teams Rooms can access the following URLs:

- agent.rooms.microsoft.com
- global.azure-devices-provisioning.net
- gj3ftstorage.blob.core.windows.net
- iothubsgagwt5wgvwg6.azure-devices.net
- blobssgagwt5wgvwg6.blob.core.windows.net
- mmrstgnoamiot.azure-devices.net
- mmrstgnoamstor.blob.core.windows.net
- mmrprodapaciot.azure-devices.net
- mmrprodapacstor.blob.core.windows.net
- mmrprodemeaiot.azure-devices.net
- mmrprodemeastor.blob.core.windows.net
- mmrprodnoamiot.azure-devices.net
- mmrprodnoamstor.blob.core.windows.net

Teams Rooms is configured to automatically keep itself patched with the latest Windows updates, including security updates. Teams Rooms installs any pending updates every day beginning at 2:00am using a pre-set local policy. There is no need to use additional tools to deploy and apply Windows Updates. Using additional tools to deploy and apply updates can delay the installation of Windows patches and thus lead to a less secure deployment. The Teams Rooms app is deployed using the Microsoft Store. If your devices are licensed with Microsoft Teams Rooms Standard, any new versions of the app are automatically installed during the nightly patching process. If your devices are licensed with Microsoft Teams Rooms Premium and enrolled in the Microsoft Managed Service, new versions of the Teams Rooms app are installed per your defined rollout plan.

Teams Rooms devices work with most 802.1X or other network-based security protocols. However, we're not able to test Teams Rooms against all possible network security configurations. Therefore, if performance issues arise that can be traced to network performance issues, you may need to disable these protocols if they're configured in your organization.

For optimum performance of real time media, we strongly recommend that you configure Teams media traffic to bypass proxy servers and other network security devices. Real time media is very latency sensitive and proxy servers and network security devices can significantly degrade users' video and audio quality. Also, because Teams media is already encrypted, there's no tangible benefit from passing the traffic through a proxy server. For more information, see [Networking up (to the cloud) — One architect’s viewpoint](/microsoft-365/solutions/networking-design-principles?view=o365-worldwide) which discusses network recommendations to improve the performance of media with Microsoft Teams and Microsoft Teams Rooms.

> [!IMPORTANT]
> Teams Rooms doesn't support authenticated proxy servers.

Teams Rooms devices don't need to connect to an internal LAN. Consider placing Teams Rooms in a secure network segment with direct Internet access. If your internal LAN becomes compromised, the attack vector opportunities towards Teams Rooms will be reduced.

We strongly recommend that you connect your Teams Rooms devices to a wired network. The use of wireless networks on Teams Rooms devices isn't recommended or certified. Some connectivity features, such as Wi-Fi Sense, are disabled by default.

Proximity Join and other Teams Rooms features rely on Bluetooth. However, the Bluetooth implementation on Teams Rooms devices doesn't allow for an external device connection to a Teams Rooms device. Bluetooth technology use on Teams Rooms devices is currently limited to advertising beacons and prompted proximal connections. The `ADV_NONCONN_INT` protocol data unit (PDU) type is used in the advertising beacon. This PDU type is for non-connectable devices advertising information to the listening device. There is no Bluetooth device pairing as part of these features. Additional details on Bluetooth protocols can be found on the [Bluetooth SIG website](https://www.bluetooth.com/blog/bluetooth-low-energy-it-starts-with-advertising/).
