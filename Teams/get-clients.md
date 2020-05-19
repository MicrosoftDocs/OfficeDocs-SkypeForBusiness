---
title: Get clients for Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
ms.reviewer: harij, rafarhi
localization_priority: Normal
search.appverid: MET150
description: Learn how to use the various clients available for Microsoft Teams which include web, desktop (Windows and Mac), and mobile (Android and iOS).
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
appliesto: 
  - Microsoft Teams
---

# Get clients for Microsoft Teams 


Microsoft Teams has clients available for desktop (Windows, Mac, and Linux), web, and mobile (Android and iOS). These clients all require an active internet connection and do not support an offline mode.

> [!NOTE]
> Effective November 29, 2018, you'll no longer be able to use the Microsoft Teams for Windows 10 S (Preview) app, available from the Microsoft Store. Instead, you can now download and install the Teams desktop client on devices running Windows 10 S mode. To download the desktop client, go to [https://teams.microsoft.com/downloads](https://go.microsoft.com/fwlink/?linkid=855754). MSI builds of the Teams desktop client are not yet available for devices running Windows 10 S mode.
>
> For more information about Windows 10 S mode, see [Introducing Windows 10 in S mode](https://www.microsoft.com/windows/s-mode). 

## Desktop client

> [!TIP]
> Watch the following session to learn about the benefits of the Windows Desktop Client, how to plan for it, and how to deploy it: [Teams Windows Desktop Client](https://aka.ms/teams-clients)

The Microsoft Teams desktop client is a standalone application and is also [available in Microsoft 365 Apps for enterprise](https://docs.microsoft.com/deployoffice/teams-install). Teams is available for 32-bit and 64-bit versions of Windows (8.1 or later) and Windows Server (2012 R2 or later), as well as for macOS and Linux (in `.deb` and `.rpm` formats). On Windows, Teams requires .NET Framework 4.5 or later; the Teams installer will offer to install it for you if you don't have it. On Linux, package managers such as `apt` and `yum` will try to install any requirements for you. However, if they don't then you will need to install any reported requirements before installing Teams on Linux.

The desktop clients provide real-time communications support (audio, video, and content sharing) for team meetings, group calling, and private one-on-one calls.

Desktop clients can be downloaded and installed by end users directly from [https://teams.microsoft.com/downloads](https://go.microsoft.com/fwlink/?linkid=855754) if they have the appropriate local permissions (admin rights are not required to install the Teams client on a PC but are required on a Mac).

> [!NOTE]
> For more details about installing Teams on a Chromebook, please see [How to install and run Microsoft Office on a Chromebook](https://support.office.com/article/how-to-install-and-run-microsoft-office-on-a-chromebook-32f14a23-2c1a-4579-b973-d4b1d78561ad).

IT admins can choose their preferred method to distribute the installation files to computers in their organization. Some examples include Microsoft Endpoint Configuration Manager (Windows) or Jamf Pro (macOS). To get the MSI package for Windows distribution, see [Install Microsoft Teams using MSI](msi-deployment.md).  

> [!NOTE]
> Distribution of the client via these mechanisms is only for the initial installation of Microsoft Team clients and not for future updates.

### Windows

The Microsoft Teams installation for Windows provides downloadable installers in 32-bit and 64-bit architecture.

> [!NOTE]
> The architecture (32-bit vs. 64-bit) of Microsoft Teams is agnostic to the architecture of Windows and Office that is installed.

The Windows client is deployed to the AppData folder located in the user’s profile. Deploying to the user’s local profile allows the client to be installed without requiring elevated rights. The Windows client leverages the following locations:

- %LocalAppData%\\Microsoft\\Teams

- %LocalAppData%\\Microsoft\\TeamsMeetingAddin

- %AppData%\\Microsoft\\Teams

- %LocalAppData%\\SquirrelTemp

When users initiate a call using the Microsoft Teams client for the first time, they might notice a warning with the Windows firewall settings that asks for users to allow communication. Users might be instructed to ignore this message because the call will work, even when the warning is dismissed.

![Screenshot of a Windows Security Alert dialog.](media/Get_clients_for_Microsoft_Teams_image3.png)

> [!NOTE]
> Windows Firewall configuration will be altered even when the prompt is dismissed by selecting “Cancel”. Two inbound rules for teams.exe will be created with Block action for both TCP and UDP protocols.

If you want to prevent Teams from prompting users to create firewall rules when the users make their first call from Teams, use the [Sample PowerShell script - inbound firewall rule](#sample-powershell-script---inbound-firewall-rule) below. 

### Mac

Mac users can install Teams by using a PKG installation file for macOS computers. Administrative access is required to install the Mac client. The macOS client is installed to the /Applications folder.

#### Install Teams by using the PKG file

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

IT admins can use managed deployment of Teams to distribute the installation files to all Macs in their organization, such as Jamf Pro.

> [!NOTE]
> If you experience issues installing the PKG, let us know. In the **Feedback** section at the end of this article, click **Product feedback**.

### Linux

Users will be able to install native Linux packages in `.deb` and `.rpm` formats.
Installing the DEB or RPM package will automatically install the package repository.
- DEB `https://packages.microsoft.com/repos/ms-teams stable main`
- RPM `https://packages.microsoft.com/yumrepos/ms-teams` 

The signing key to enable auto-updating using the system's package manager is installed automatically. However, it can also be found at: (https://packages.microsoft.com/keys/microsoft.asc). Microsoft Teams ships monthly and if the repository was installed correctly, then your system package manager should handle auto-updating in the same way as other packages on the system.

> [!NOTE] 
> If you find a bug, submit it using `Report a Problem` from within the client. For known issues, see [Support Teams in your organization](Known-issues.md).
> For Teams for Linux support you can use the [Linux forum support channel on Microsoft Q&A](https://docs.microsoft.com/answers/topics/teams.html). Be sure to use the `teams-linux` tag when posting questions. 

#### Install Teams using DEB package

1. Download the package from https://aka.ms/getteams.
2. Install using one of the following:  
    - Open the relevant package management tool and go through the self-guided Linux app installation process.
    - Or if you love Terminal, type: `sudo apt install **teams download file**`

You can launch Teams via Activities or via Terminal by typing `Teams`. 

#### Install Teams using RPM package

1. Download the package from https://aka.ms/getteams.
2. Install using one of the following:
    - Open the relevant package management tool and go through the self-guided Linux app installation process.
    - Or if you love Terminal, type: `sudo yum install **teams download file**`

You can launch Teams via Activities or via Terminal by typing `Teams`.

#### Install manually from the command line

Install manually on Debian and Ubuntu distributions:
```
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
 
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/ms-teams stable main" > /etc/apt/sources.list.d/teams.list'
 
sudo apt update
sudo apt install teams
```

Install manually on RHEL, Fedora and CentOS based distributions:
```
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
 
sudo sh -c 'echo -e "[teams]\nname=teams\nbaseurl=https://packages.microsoft.com/yumrepos/ms-teams\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/teams.repo'
 
sudo dnf check-update
sudo dnf install teams
```

Alternatively, to use yum instead of dnf:
```
yum check-update
sudo yum install teams
```

Install manually on openSUSE based distributions:
```
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
 
sudo sh -c 'echo -e "[teams]\nname=teams\nbaseurl=https://packages.microsoft.com/yumrepos/ms-teams\nenabled=1\nautorefresh=1\nkeeppackages=0\ntype=rpm-md\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/teams.repo'
 
sudo zypper refresh
sudo zypper install teams
```

## Web client 

The web client ([https://teams.microsoft.com](https://go.microsoft.com/fwlink/?linkid=855753)) is a full, functional client that can be used from a variety of browsers. The web client supports Calling and Meetings by using webRTC, so there is no plug-in or download required to run Teams in a web browser. The browser must be configured to allow third-party cookies. 

[!INCLUDE [browser-support](includes/browser-support.md)]

The web client performs browser version detection upon connecting to [https://teams.microsoft.com](https://go.microsoft.com/fwlink/?linkid=855753). If an unsupported browser version is detected, it will block access to the web interface and recommend that the user download the desktop client or mobile app.

## Mobile clients

The Microsoft Teams mobile apps are available for Android and iOS, and are geared for on-the-go users participating in chat-based conversations and allow peer-to-peer audio calls. For mobile apps, go to the relevant mobile stores Google Play and the Apple App Store. The Windows Phone App was retired July 20, 2018 and may no longer work. 

In China, here's how to [get Teams for Android](get-teams-android-in-china.md). 

Supported mobile platforms for Microsoft Teams mobile apps are the following:

-   **Android**: Support is limited to the last four major versions of Android. When a new major version of Android is released, the new version and the previous three versions are officially supported.

-   **iOS**: Support is limited to the two most recent major versions of iOS. When a new major version of iOS is released, the new version of iOS and the previous version are officially supported.

> [!NOTE]
> The mobile version must be available to the public in order for Teams to work as expected.

Mobile apps are distributed and updated through the respective mobile platform’s app store only. Distribution of the mobile apps via MDM or side-loading is not supported by Microsoft. Once the mobile app has been installed on a supported mobile platform, the Teams Mobile App itself will be supported provided the version is within three months of the current release.


| | | |
|---------|---------|---------|
|![An icon depicting a decision point](media/Get_clients_for_Microsoft_Teams_image4.png)      |Decision Point         |Are there any restrictions preventing users from installing the appropriate Microsoft Teams client on their devices?         |
|![An icon depicting the next steps](media/Get_clients_for_Microsoft_Teams_image5.png)     |Next Steps         |If your organization restricts software installation, make sure that process is compatible with Microsoft Teams. Note: Admin rights are not required for PC client installation but are required for installation on a Mac.         |

## Client update management

Clients are currently updated automatically by the Microsoft Teams service with no IT administrator intervention required. If an update is available, the client will automatically download the update and when the app has idled for a period of time, the update process will begin.

## Client-side configurations

Currently, there are no supported options available to configure the client either through the tenant admin, PowerShell, Group Policy Objects or the registry.

## Notification settings

There are currently no options available for IT administrators to configure client-side notification settings. All notification options are set by the user. The figure below outlines the default client settings.

![Screenshot of Notifications settings.](media/Get_clients_for_Microsoft_Teams_image6.png)

## Sample PowerShell script - inbound firewall rule

This sample script, which needs to run on client computers in the context of an elevated administrator account, will create a new inbound firewall rule for each user folder found in c:\users. When Teams finds this rule, it will prevent the Teams application from prompting users to create firewall rules when the users make their first call from Teams. 

```powershell
<#
.SYNOPSIS
   Creates firewall rules for Teams.
.DESCRIPTION
   (c) Microsoft Corporation 2018. All rights reserved. Script provided as-is without any warranty of any kind. Use it freely at your own risks.
   Must be run with elevated permissions. Can be run as a GPO Computer Startup script, or as a Scheduled Task with elevated permissions. 
   The script will create a new inbound firewall rule for each user folder found in c:\users. 
   Requires PowerShell 3.0.
#>

#Requires -Version 3

$users = Get-ChildItem (Join-Path -Path $env:SystemDrive -ChildPath 'Users') -Exclude 'Public', 'ADMINI~*'
if ($null -ne $users) {
    foreach ($user in $users) {
        $progPath = Join-Path -Path $user.FullName -ChildPath "AppData\Local\Microsoft\Teams\Current\Teams.exe"
        if (Test-Path $progPath) {
            if (-not (Get-NetFirewallApplicationFilter -Program $progPath -ErrorAction SilentlyContinue)) {
                $ruleName = "Teams.exe for user $($user.Name)"
                "UDP", "TCP" | ForEach-Object { New-NetFirewallRule -DisplayName $ruleName -Direction Inbound -Profile Domain -Program $progPath -Action Allow -Protocol $_ }
                Clear-Variable ruleName
            }
        }
        Clear-Variable progPath
    }
}
```
