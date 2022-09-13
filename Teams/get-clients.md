---
title: Get clients for Microsoft Teams
author: dstrome
ms.author: dstrome
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
ms.reviewer: harij, rafarhi
ms.localizationpriority: high
search.appverid: MET150
description: Learn how to install the various clients available for Microsoft Teams on PCs, Macs, and mobile devices.
f1.keywords:
- CSH
appliesto: 
  - Microsoft Teams
---

# Get clients for Microsoft Teams

> [!TIP]
> **Want to install Teams on your PC, Mac, or mobile device?** Check out [Install the Teams client](https://go.microsoft.com/fwlink/?linkid=855754).

Microsoft Teams can be installed on PCs, Macs, and mobile devices, and can also be accessed via a web browser. Most end users can start using Teams just by [installing the client](https://go.microsoft.com/fwlink/?linkid=855754) themselves. After they install the Teams client, all they need to do is log in with their username and password.

If you're an IT Pro and want to know more about the Teams installation experience and its requirements, select a client operating system in this article for more information.

For details about each client's capabilities on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

## Desktop clients

The Teams desktop client is available as a standalone application and as part of [Microsoft 365 Apps for enterprise](/deployoffice/teams-install) for the following operating systems:

- 32-bit and 64-bit versions of Windows (8.1 or later, excluding Windows 10 LTSC) 
- ARM64 for Windows 10 on ARM 
- Windows Server (2012 R2 or later)
- macOS
- Linux (in `.deb` and `.rpm` formats)
- Chrome OS (For more information, see [How to use Microsoft Office on a Chromebook](https://support.office.com/article/how-to-install-and-run-microsoft-office-on-a-chromebook-32f14a23-2c1a-4579-b973-d4b1d78561ad))

Desktop clients can be downloaded and installed by end users directly from [https://teams.microsoft.com/downloads](https://go.microsoft.com/fwlink/?linkid=855754) if they have the appropriate local permissions. Admin permissions aren't required to install the Teams client on Windows PCs but are required on Macs.

IT Pros can choose their preferred method to distribute the installation files to computers in their organization. Some examples include Microsoft Endpoint Configuration Manager (Windows) or Jamf Pro (macOS). For more information about distributing Teams, see the following.

- **Windows** [Install Teams using Endpoint Configuration Manager](msi-deployment.md)
- **MacOS** [Jamf Pro](https://www.jamf.com/products/jamf-pro/)

> [!NOTE]
> Distribution of the client via these mechanisms is only for the initial installation of Teams clients and not for future updates. For information about the Teams update process, see [Teams update process](teams-client-update.md).

### [Windows](#tab/Windows)

> [!TIP]
> Watch the following session to learn about the benefits of the Windows Desktop Client, how to plan for it, and how to deploy it: [Teams Windows Desktop Client](https://aka.ms/teams-clients)

Teams on Windows provides downloadable MSI installers in [32-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true), [64-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true), and [ARM64](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=arm64&managedInstaller=true&download=true) architectures. The x86 architecture (32-bit vs. 64-bit) of Teams is agnostic to the architecture of Windows and Office that is installed. We recommend the 64-bit version of Teams on 64-bit systems.

Teams requires .NET Framework 4.5 or later. If .NET Framework or later isn't installed the Teams installer will offer to install for you.

The Windows client is deployed to the AppData folder located in the user’s profile. Deploying to the user’s local profile allows the client to be installed without requiring elevated permissions. The Windows client leverages the following locations:

- %LocalAppData%\\Microsoft\\Teams

- %LocalAppData%\\Microsoft\\TeamsMeetingAddin

- %AppData%\\Microsoft\\Teams

- %LocalAppData%\\SquirrelTemp

When users initiate a call using the Teams client for the first time, they might notice a warning with the Windows firewall settings that asks for users to allow communication. Users might be instructed to ignore this message because the call will work, even when the warning is dismissed.

![Screenshot of a Windows Security Alert dialog.](media/Get_clients_for_Microsoft_Teams_image3.png)

> [!NOTE]
> Windows Firewall configuration will be altered even when the prompt is dismissed by selecting “Cancel”. Two inbound rules for teams.exe will be created with Allow action for both TCP and UDP protocols.

If you want to prevent Teams from prompting users to create firewall rules when the users make their first call from Teams, use the PowerShell script in [Sample script - Microsoft Teams firewall PowerShell script](client-firewall-script.md).

### [Mac](#tab/Mac)

Mac users can install Teams by using a PKG installation file for macOS computers. Administrative access is required to install the Mac client. The macOS client is installed to the /Applications folder.

1. From the [Teams download page](https://teams.microsoft.com/downloads), under **Mac**, click **Download**.
2. Double click the PKG file.
3. Follow the installation wizard to complete the installation.
4. Teams will be installed to /Applications folder. It is a machine-wide installation.

> [!NOTE]
> During the installation, the PKG will prompt for admin credentials. The user needs to enter the admin credentials, regardless of whether or not the user is an admin.

If a user currently has a DMG installation of Teams and wants to replace it with the PKG installation, the user should:

1. Exit the Teams app.
2. Uninstall the Teams app.
3. Install the PKG file.

IT Pros can use a managed deployment solution, such as Jamf Pro, to distribute the Teams installation files to all Macs in their organization.

### [Linux](#tab/Linux)

On Linux, package managers such as `apt` and `yum` will try to install any requirements for you. However, if they don't then you will need to install any reported requirements before installing Teams on Linux.

Users will be able to install native Linux packages in `.deb` and `.rpm` formats. Installing the DEB or RPM package will automatically install the package repository.

- DEB `https://packages.microsoft.com/repos/ms-teams stable main`
- RPM `https://packages.microsoft.com/yumrepos/ms-teams`

The signing key to enable auto-updating using the system's package manager is installed automatically. However, it can also be found at: <https://packages.microsoft.com/keys/microsoft.asc>. Teams ships monthly and if the repository was installed correctly, then your system package manager should handle auto-updating in the same way as other packages on the system.

#### Install Teams using DEB package

1. Download the package from <https://aka.ms/getteams>.
2. Install using one of the following:
    - Open the relevant package management tool and go through the self-guided Linux app installation process.
    - Or if you love Terminal, type: `sudo dpkg -i **teams download file**`

You can launch Teams via Activities or via Terminal by typing `teams`.

#### Install Teams using RPM package

1. Download the package from <https://aka.ms/getteams>.
2. Install using one of the following:
    - Open the relevant package management tool and go through the self-guided Linux app installation process.
    - Or if you love Terminal, type: `sudo yum install **teams download file**`

You can launch Teams via Activities or via Terminal by typing `teams`.

#### Install manually from the command line

Install manually on Debian and Ubuntu distributions:

```bash
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/ms-teams stable main" > /etc/apt/sources.list.d/teams.list'

sudo apt update
sudo apt install teams
```

Install manually on RHEL, Fedora and CentOS based distributions:

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

sudo sh -c 'echo -e "[teams]\nname=teams\nbaseurl=https://packages.microsoft.com/yumrepos/ms-teams\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/teams.repo'

sudo dnf check-update
sudo dnf install teams
```

Alternatively, to use yum instead of dnf:

```bash
yum check-update
sudo yum install teams
```

Install manually on openSUSE based distributions:

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

sudo sh -c 'echo -e "[teams]\nname=teams\nbaseurl=https://packages.microsoft.com/yumrepos/ms-teams\nenabled=1\nautorefresh=1\nkeeppackages=0\ntype=rpm-md\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/teams.repo'

sudo zypper refresh
sudo zypper install teams
```

---

## Mobile clients

The Teams mobile apps are available for Android and iOS, and are geared for on-the-go users participating in chat-based conversations and allow peer-to-peer audio calls. For mobile apps, go to the relevant mobile stores Google Play and the Apple App Store.

Supported mobile platforms for Teams mobile apps are the following:

- **Android**: Support is limited to the last four major versions of Android. When a new major version of Android is released, the new version and the previous three versions are officially supported.

- **iOS**: Support is limited to the two most recent major versions of iOS. When a new major version of iOS is released, the new version of iOS and the previous version are officially supported.

> [!NOTE]
> The mobile version must be available to the public in order for Teams to work as expected.

Mobile apps are distributed and updated through the respective mobile platform’s app store only. Distribution of the mobile apps via MDM or side-loading is not supported by Microsoft. Once the mobile app has been installed on a supported mobile platform, the Teams Mobile App itself will be supported provided the version is within three months of the current release.

If you're in China, you can install Teams from the following app stores:

- **Xiaomi** <https://aka.ms/TeamsXiaomi>
- **Huawei** <https://aka.ms/TeamsHuawei>
- **Oppo** Search for "Teams" in the Oppo store
- **Baidu** <https://aka.ms/teams_baidu_direct_dl>

>[!NOTE]
>When users install Teams from one of the China-based app stores and enable push notifications for Teams, Microsoft will provide Teams push notifications through a China-based push notification service.

## Browser client

The browser client ([https://teams.microsoft.com](https://go.microsoft.com/fwlink/?linkid=855753)) is a full, functional client that can be used from a variety of browsers. The browser client supports Calling and Meetings by using webRTC, so there is no plug-in or download required to run Teams in a browser. The browser must be configured to allow third-party cookies.

[!INCLUDE [browser-support](includes/browser-support.md)]

The browser client performs browser version detection upon connecting to [https://teams.microsoft.com](https://go.microsoft.com/fwlink/?linkid=855753). If an unsupported browser version is detected, it will block access to the browser interface and recommend that the user download the desktop client or mobile app.
