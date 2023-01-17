---
title: 'Zero-trust security guide for Microsoft Teams: Use Teams securely on shared computers'
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: pawa
description: Zero Trust guidance for using Microsoft Teams securely from a shared computer in the workplace.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - remotework
ms.custom: 
- Security
appliesto: 
  - Microsoft Teams
---

# Use Microsoft Teams securely on shared computers

When possible, it is *recommended* Enterprises make use of a Zero Trust approach to client devices making use of device management capabilities, device health checks and policy enforcement, device-level encryption, and other security features.

:::image type="content" source="media/tp_ZeroTrustPrinciples.PNG" alt-text="Zero trust picture showing verify explicitly, least privilege, and assume breach -- the core zero trust principles -- in blue circles.":::

Administrators can create secure conditions by *insisting* on verification, least privilege, and by assuming compromise--standards that lead to actions that minimize risk to both users and data.

> [!TIP]
> For a deeper examination of Zero Trust principles, see [these videos](/security/ciso-workshop/ciso-workshop-module-3#part-2-zero-trust-definition-and-models-1537).

## Tips for using Microsoft Teams securely from a shared computer

Recognizing that this may not be possible or practical in all scenarios, it is still important for security administrators to follow guidance for using Teams from a shared computer or unmanaged device as best they can.

Plans should be developed to adhere to guidelines as promptly as is possible.

1. Make use of Operating System platform security capabilities.
    1. Ensure that the operating system is configured to install automatic updates from the Operating System provider (for Microsoft systems, this can be accomplished via [**Windows Update**](https://support.microsoft.com/help/12373/windows-update-faq)). 
    1. Ensure that any device encryption capabilities such as [**bitlocker**](/windows/security/information-protection/bitlocker/bitlocker-overview) are enabled, and the key used to access the device is secured.  Note that most modern [**Windows 10 devices support bitlocker**](/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10). 
    1. Use anti-virus capabilities such as those offered by [**Windows Defender**](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) on your devices.
    1. Use of [separate user accounts](https://support.microsoft.com/help/4026923/windows-10-create-a-local-user-or-administrator-account) for each user of the system is highly recommended.
    1. *Do not* grant, or use, administrator privileges for non-administrative functions (such as browsing the web, running Teams, et cetera).

If the above guidance cannot be met, we recommend making use of other browser security best practices:

1. Apply browser security capabilities.
    1. Use private browsing sessions to minimize data and history that persists to disk. For example, use [inPrivate browsing in Microsoft Edge](https://support.microsoft.com/help/4533513/microsoft-edge-browse-inprivate), [Incognito browsing in Google Chrome](https://support.google.com/chrome/answer/95464?co=GENIE.Platform%3DDesktop&hl=en), or the capabilities your specific browser for browsing privately.
    1. Changing the system behavior to engage private browsing *by default* is recommended.

2. Browse to and use the [Teams web app](https://teams.microsoft.com) (sometimes called the *web* client) not the downloadable Teams client.

3. When you are done using the shared system, you must:
    1. [Sign out of Teams](https://support.microsoft.com/office/sign-out-of-teams-a6d76e69-e1dd-4bc4-8e5f-04ba48384487).
    1. Close all browser tabs and windows.
    1. Sign out of the device.

The items above are not a comprehensive list of best practices or security controls covering all cases, and there may be extra actions that can be taken in your environment, (for instance, security administrators may choose to use Safe Links and Safe Attachments for Teams if you have [Microsoft Defender for Office 365 Plan 1 or Plan 2](/microsoft-365/security/office-365-security/overview?view=o365-worldwide)). However, these steps are a starting point for building guidance for using Teams from shared devices.

## More Information

[BitLocker in Configuration Manager](/mem/configmgr/protect/deploy-use/bitlocker/deploy-management-agent)

[BitLocker for Windows 10 in Intune](/mem/intune/protect/encrypt-devices)

[Endpoint security in Intune](/mem/intune/protect/endpoint-security)

[Enable](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus#ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app) Microsoft Defender Antivirus in your Windows Security and [run scans](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus#run-a-scan-with-the-windows-security-app)

[Microsoft Defender security center article](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus)

[Teams web client/teams web app](./get-clients.md#browser-client)

[Security and Microsoft Teams](./teams-security-guide.md)
