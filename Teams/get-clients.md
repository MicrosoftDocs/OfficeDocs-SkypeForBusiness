---
title: Get clients for Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
audience: Admin
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
ms.reviewer: rafarhi
ms.date: 10/13/2023
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to install the various clients available for classic Microsoft Teams on PCs, Macs, and mobile devices.
f1.keywords:
- CSH
appliesto: 
  - Microsoft Teams
---

# Get clients for classic Microsoft Teams

> [!TIP]
> **Want to install Teams on your PC, Mac, or mobile device?** Check out [Install the Teams client](https://go.microsoft.com/fwlink/?linkid=855754).

> [!TIP]
> **Want to get highly reliable push notifications on your Xiaomi phones?** Check out [How to make Teams push notifications work in your Xiaomi phone?](devices/xiaomi-push-notifications.md#how-to-make-teams-push-notifications-work-in-your-xiaomi-phone).

Microsoft Teams can be installed on PCs, Macs, and mobile devices, and can also be accessed via a web browser. Most end users can start using Teams just by [installing the client](https://go.microsoft.com/fwlink/?linkid=855754) themselves. After they install the Teams client, all they need to do is sign in with their username and password.

If you're an IT Pro and want to know more about the Teams installation experience and its requirements, select a client operating system in this article for more information.

For information about each client's capabilities on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

## Desktop clients

>[!Important]
>The new Microsoft Teams desktop client is now available. The system requirements are different. For more information, see [The new Microsoft Teams desktop client](new-teams-desktop-admin.md).

The classic Teams desktop client is available as a standalone application and as part of [Microsoft 365 Apps for enterprise](/deployoffice/teams-install) for the following operating systems:

- 32-bit and 64-bit versions of Windows (8.1 or later, excluding Windows 10 LTSC)
- ARM64 for Windows 10 on ARM
- Windows Server (2012 R2 or later)
- macOS
- Chrome OS (For more information, see [How to use Microsoft Office on a Chromebook](https://support.office.com/article/how-to-install-and-run-microsoft-office-on-a-chromebook-32f14a23-2c1a-4579-b973-d4b1d78561ad))

Desktop clients can be downloaded and installed by end users directly from [https://teams.microsoft.com/downloads](https://go.microsoft.com/fwlink/?linkid=855754) if they have the appropriate local permissions. Administrator permissions aren't required to install the Teams client on Windows PCs but are required on Macs.

IT Pros can choose their preferred method to distribute the installation files to computers in their organization. Some examples include Microsoft Endpoint Configuration Manager (Windows) or Jamf Pro (macOS). For more information about distributing Teams, see:

- **Windows** [Install Teams using Endpoint Configuration Manager](msi-deployment.md)
- **MacOS** [Jamf Pro](https://www.jamf.com/products/jamf-pro/)

> [!NOTE]
> Distribution of the client via these mechanisms is only for the initial installation of Teams clients and not for future updates. For information about the Teams update process, see [Teams update process](teams-client-update.md).

### [Windows](#tab/Windows)

> [!TIP]
> Watch the following session to learn about the benefits of the Windows Desktop Client, how to plan for it, and how to deploy it: [Teams Windows Desktop Client](https://aka.ms/teams-clients)

Teams on Windows provides downloadable MSI installers in [32-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true), [64-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true), and [ARM64](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=arm64&managedInstaller=true&download=true) architectures. The x86 architecture (32 bit vs. 64 bit) of Teams is agnostic to the architecture of Windows and Office that is installed. We recommend the 64-bit version of Teams on 64-bit systems.

Teams requires .NET Framework 4.5 or later. If .NET Framework 4.5 or later isn't installed, the Teams installer will offer to install for you.

> [!NOTE]
> Teams isn't supported in [Assigned Access](/windows/configuration/assigned-access/overview) mode (formerly known as Windows Kiosk mode).

The Windows client is deployed to the AppData folder located in the user’s profile. Deploying to the user’s local profile allows the client to be installed without requiring elevated permissions. The Windows client uses the following locations:

- %LocalAppData%\\Microsoft\\Teams

- %LocalAppData%\\Microsoft\\TeamsMeetingAddin

- %AppData%\\Microsoft\\Teams

- %LocalAppData%\\SquirrelTemp

When users initiate a call using the Teams client for the first time, they might notice a warning with the Windows firewall settings that ask for users to allow communication. Users might be instructed to ignore this message because the call will work even when the warning is dismissed.

:::image type="content" alt-text="Screenshot of a Windows Security Alert dialog." source="media/Get_clients_for_Microsoft_Teams_image3.png":::

> [!NOTE]
> Windows Firewall configuration will be altered. Two inbound rules for teams.exe for both TCP and UDP protocols will be created with:

> - Allow action, in case the user is a local administrator and selects **Allow access** only.
> - Block action, if the user isn't a local administrator and, in any case, when the prompt is dismissed by selecting **Cancel**.

If you want to prevent Teams from prompting users to create firewall rules when the users make their first call from Teams, use the PowerShell script in [Sample script - Microsoft Teams firewall PowerShell script](client-firewall-script.md).

### [Mac](#tab/Mac)

Mac users can install Teams by using a PKG installation file for macOS computers. Administrative access is required to install the Mac client. The macOS client is installed to the **/Applications** folder.

1. From the [Teams download page](https://teams.microsoft.com/downloads), under **Mac**, select **Download**.
2. Double-click the PKG file.
3. Follow the installation wizard to complete the installation.
   Teams will be installed to the **/Applications** folder. It's a machine-wide installation.

> [!NOTE]
> During the installation, the PKG will prompt for administrator credentials. The user needs to enter the administrator credentials, regardless of whether or not the user is an administrator.

If a user currently has a DMG installation of Teams and wants to replace it with the PKG installation, the user should:

1. Exit Teams.
2. Uninstall Teams.
3. Install the PKG file.

IT Pros can use a managed deployment solution, such as Jamf Pro, to distribute the Teams installation files to all Macs in their organization.

---

## Mobile clients

The Teams mobile apps are available for Android and iOS; are geared for on-the-go users participating in chat-based conversations; and allow peer-to-peer audio calls. For mobile apps, go to the relevant mobile stores **Google Play** and the **Apple App Store**.

Supported mobile platforms for Teams mobile apps are:

- **Android**: Support is limited to the last four major versions of Android. When a new major version of Android is released, the new version and the previous three versions are officially supported.

- **iOS**: Support is limited to the two most recent major versions of iOS. When a new major version of iOS is released, the new version of iOS and the previous version are officially supported.

> [!NOTE]
> The mobile version must be available to the public for Teams to work as expected.

Mobile apps are distributed and updated through the respective mobile platform’s app store only. Distribution of the mobile apps via MDM or side-loading isn't supported by Microsoft. Once the mobile app has been installed on a supported mobile platform, the Teams Mobile App itself will be supported, provided the version is within three months of the current release.

If you're in China, you can install Teams from the following app stores:

- **Xiaomi** <https://aka.ms/TeamsXiaomi>
- **Huawei** <https://aka.ms/TeamsHuawei>
- **Vivo** <https://aka.ms/Teamsvivo>
- **Oppo** Search for "Teams" in the Oppo store
- **Baidu** <https://aka.ms/TeamsBaidu>

> [!NOTE]
> When users install Teams from one of the China-based Android app stores and enable push notifications for Teams, Microsoft will provide Teams push notifications through a China-based push notification service.
>Currently, Microsoft supports push notifications in Xiaomi phones and OPPO phones. As a result, you must enable the push notifications in Xiaomi phones and OPPO phones. For detailed information on how to configure Xiaomi phones, see [How to make Teams push notifications work in your Xiaomi phone?](devices/xiaomi-push-notifications.md#how-to-make-teams-push-notifications-work-in-your-xiaomi-phone).

## Browser client

The browser client ([https://teams.microsoft.com](https://go.microsoft.com/fwlink/?linkid=855753)) is a full, functional client that can be used from various browsers. The browser client supports Calling and Meetings by using webRTC; so there's no plug-in or download required to run Teams in a browser. The browser must be configured to allow third-party cookies.

[!INCLUDE [browser-support](includes/browser-support.md)]

The browser client performs browser version detection upon connecting to [https://teams.microsoft.com](https://go.microsoft.com/fwlink/?linkid=855753). If an unsupported browser version is detected, it will block access to the browser interface and recommend that the user downloads the desktop client or mobile app.
