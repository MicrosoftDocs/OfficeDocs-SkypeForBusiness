---
title: Install Microsoft Teams using MSI via SCCM
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: rowille
audience: admin
description: Admins can use the Teams MSI to bulk deploy Microsoft Teams to select users or computers.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Install Microsoft Teams using MSI

> [!Tip]
> Watch the following session to learn about the benefits of the Windows Desktop Client, how to plan for it and how to deploy it: [Teams Windows Desktop Client](https://aka.ms/teams-clients)

To use System Center Configuration Manager, or Group Policy, or any third-party distribution mechanisms for broad deployment, Microsoft has provided MSI files (both 32-bit and 64-bit) that admins can use for bulk deployment of Teams to select users or computers. Admins can use these files to remotely deploy Teams so that users do not have to manually download the Teams app. When deployed, Teams will auto launch for all users who sign in on that machine. (You can disable auto launch after installing the app. [See below](#disable-auto-launch-for-the-msi-installer).)
We recommend that you deploy the package to the computer, so all new users of the machine will also benefit from this deployment.

These are the links to the MSI files:


|Entity  |32 bit      |64 bit      |
|---------|---------|---------|
|Commercial     | [32 bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true)        | [64 bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true)       |
|Federal Government - GCC     | [32 bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&ring=general_gcc&download=true)       | [64 bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&ring=general_gcc&download=true)        |
|Federal Government - GCC High    | [32 bit](https://gov.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true)         | [64 bit](https://gov.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true)        |
|Federal Government - DoD     | [32 bit](https://dod.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true)        | [64 bit](https://dod.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true)        |

Teams can also be included with a deployment of Office 365 ProPlus. For more information, see [Deploy Microsoft Teams with Office 365 ProPlus](https://docs.microsoft.com/deployoffice/teams-install).

> [!Note]
> To learn more about SCCM, see [Introduction to System Center Configuration Manager](https://docs.microsoft.com/sccm/core/understand/introduction).

## Deployment procedure (recommended)

1. Retrieve the latest package.
2. Use the defaults prepopulated by the MSI.
3. Deploy to computers when possible.

## How the Microsoft Teams MSI package works

### PC installation

The Teams MSI will place an installer in Program Files. Whenever a user signs into a new Windows User Profile, the installer will be launched and a copy of the Teams app will be installed in that user's appdata folder. If a user already has the Teams app installed in the appdata folder, the MSI installer will skip the process for that user.

Do not use the MSI to deploy updates, because the client will auto update when it detects a new version is available from the service. To re-deploy the latest installer use the process of redeploying MSI described below. If you deploy an older version of the MSI package, the client will auto-update (except in VDI environments) when possible for the user. If a very old version gets deployed, the MSI will trigger an app update before the user is able to use Teams.

> [!Important]
> We don't recommended that you change the default install locations, as this could break the update flow. Having too old a version will eventually block users from accessing the service.

#### Target computer requirements

- .NET framework 4.5 or later
- Windows 7 or later
- 3 GB of disk space for each user profile (recommended)

### VDI installation

For complete guidance on how to deploy the Teams desktop app on VDI, see [Teams for Virtualized Desktop Infrastructure](teams-for-vdi.md).

## Clean up and redeployment procedure

If a user uninstalls Teams from their User Profile, the MSI installer will track that the user has uninstalled the Teams app and no longer install Teams for that User Profile. To redeploy Teams for this user on a particular computer where it was uninstalled, do the following:

1. Uninstall Teams App installed for every user profile.
2. After uninstall, delete directory recursively under %localappdata%\Microsoft\Teams\.
3. Redeploy the MSI package to that particular computer.

> [!TIP]
> You can use our [Microsoft Teams deployment clean up](scripts/Powershell-script-teams-deployment-clean-up.md) script to accomplish steps 1 and 2 via SCCM.

## Prevent Teams from starting automatically after installation

The default behavior of the MSI is to install the Teams app as soon as a user signs in and then automatically start Teams. If you don't want Teams to start automatically for users after it's installed, you can do so by using either Group Policy or by disabling auto launch for the MSI installer.

#### Use Group Policy (recommended)

Use Group Policy and enable the **Prevent Microsoft Teams from starting automatically after installation** policy setting. You can find this policy setting under User Configuration\Policies\Administrative Templates\Microsoft Teams. This is the recommended method because you can easily turn off and turn on the policy setting according to your organization's needs.

When you enable this policy setting before Teams is installed, Teams won't start automatically when the user logs in to Windows. When a user signs in to Teams for the first time, Teams is configured to start automatically the next time the user logs in.

Note that a shortcut to start Teams is added to the user's desktop when you enable this policy setting.

If you have Office 365 Business or can't use Group Policy for some other reason, you can add the PreventFirstLaunchAfterInstall REG_DWORD value to the HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Office\16.0\Teams key in the registry. Set the value to 1 if you don't want Teams to automatically start after installation.

### Disable auto launch for the MSI installer

You can disable auto launch for the MSI installer by using the **OPTIONS="noAutoStart=true"** parameter, as follows.  

For the 32-bit version
```
msiexec /i Teams_windows.msi OPTIONS="noAutoStart=true"
```
For the 64-bit version
```
msiexec /i Teams_windows_x64.msi OPTIONS="noAutoStart=true"
```

When a user logs in into Windows, Teams is installed with the MSI and a shortcut to start Teams is added to the user's desktop. Teams won't start until the user manually starts Teams. After the users manually starts Teams, Teams automatically starts whenever the user logs in to Windows.

> [!Note]
> If you run the MSI manually, be sure to run it with elevated permissions. Even if you run it as an administrator, without running it with elevated permissions, the installer won't be able to configure the option to disable auto start.
