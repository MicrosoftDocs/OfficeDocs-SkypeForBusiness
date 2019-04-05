---
title: Install Microsoft Teams using MSI via SCCM
author: Lester-Hewett
ms.author: lehewe
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
description: Admins can use the Teams MSI to bulk deploy Microsoft Teams to select users or computers.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Install Microsoft Teams using MSI
=================================

> [!Tip]
> Watch the following session to learn about the benefits of the Windows Desktop Client, how to plan for it and how to deploy it: [Teams Windows Desktop Client](https://aka.ms/teams-clients)

To use System Center Configuration Manager, or Group Policy, or any third-party distribution mechanisms for broad deployment, Microsoft has provided MSI files (both [32-bit](https://aka.ms/teams32bitmsi) and [64-bit](https://aka.ms/teams64bitmsi)) that admins can use for bulk deployment of Teams to select users or computers. Admins can use these files to remotely deploy Teams so that users do not have to manually download the Teams app. When deployed, Teams will auto launch for all users who sign in on that machine. (You can disable auto launch after installing the app. [See below](#disable-auto-lanuch-for-the-msi-installer).)
We recommend that you deploy the package to the computer, so all new users of the machine will also benefit from this deployment. 
 
> [!Note] 
> To learn more about SCCM, see [Introduction to System Center Configuration Manager](https://docs.microsoft.com/sccm/core/understand/introduction).

## Deployment procedure (recommended)
1. Retrieve the latest package.
2. Use the defaults prepopulated by the MSI.
3. Deploy to computers when possible.

## How the Microsoft Teams MSI package works

### PC installation

> [!Note] 
> See [VDI installation](#vdi-installation) for guidance on how to deploy Teams to a Virtual DesktopInfrastructure (VDI) environment.

The Teams MSI will place an installer in Program Files. Whenever a user signs into a new Windows User Profile, the installer will be launched and a copy of the Teams app will be installed in that user's appdata folder. If a user already has the Teams app installed in the appdata folder, the MSI installer will skip the process for that user.

Do not use the MSI to deploy updates, because the client will auto update when it detects a new version is available from the service. To re-deploy the latest installer use the process of redeploying MSI described below. If you deploy an older version of the MSI package, the client will auto-update when possible for the user. If a very old version gets deployed, the MSI will trigger an app update before the user is able to use Teams. 

> [!Important] 
> We don't recommended that you change the default install locations, as this could break the update flow. Having too old a version will eventually block users from accessing the service. 

#### Target computer requirements

- .NET framework 4.5 or later
- Windows 7 or later
- 3 GB of disk space for each user profile (recommended)

### VDI installation

Here's the process to deploy the Teams desktop app. For complete guidance, see [Teams for Virtualized Desktop Infrastructure](teams-for-vdi.md).

1. Download the Teams MSI package using one of the following links depending on the environment. We recommend the 64-bit version for a VDI VM with a 64-bit operating system.

    - [32-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true)
    - [64-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true&arch=x64)

2. Run the following command to install the MSI to the VDI VM (or complete updating it).

        msiexec /i <path_to_msi> /l*v <install_logfile_name> ALLUSER=1

    This installs Teams to Program Files. At this point, the golden image setup is complete.

    The next interactive logon session starts Teams and asks for credentials. Note that it's not possible to disable auto-launch of Teams when installing Teams on VDI using the ALLUSER property.

3. Run the following command to uninstall the MSI from the VDI VM (or prepare for updating it).

        msiexec /passive /x <path_to_msi> /l*v <uninstall_logfile_name>

    This uninstalls Teams from Program Files.

## Clean up and redeployment procedure

If a user uninstalls Teams from their User Profile, the MSI installer will track that the user has uninstalled the Teams app and no longer install Teams for that User Profile. To redeploy Teams for this user on a particular computer where it was uninstalled, do the following:

1. Uninstall Teams App installed for every user profile. 
2. After uninstall, delete directory recursively under %localappdata%\Microsoft\Teams\.
3. Redeploy the MSI package to that particular computer.

> [!TIP] 
> You can use our [Microsoft Teams deployment clean up](scripts/Powershell-script-teams-deployment-clean-up.md) script to accomplish steps 1 and 2 via SCCM.

## Disable auto launch for the MSI installer

Default behavior of the MSI is to install the Teams client as soon as a user signs in and then automatically start Teams. You can modify this behavior with the parameters below as follows:

- When a user logs in into Windows, Teams will be installed with the MSI
- However, the Teams client will not start until the user has started Teams manually
- A shortcut to start Teams will be added on the desktop of the user
- Once manually started, Teams will auto-start whenever the user logs in

For the 32-bit version
```
msiexec /i Teams_windows.msi OPTIONS="noAutoStart=true"
```
For the 64-bit version
```
msiexec /i Teams_windows_x64.msi OPTIONS="noAutoStart=true"
```

> [!Note]
>  If you run the MSI manually, be sure to run it with elevated permissions. Even if you run it as an administrator, without running it with elevated permissions, the installer will not be able to configure the option to disable auto start.
