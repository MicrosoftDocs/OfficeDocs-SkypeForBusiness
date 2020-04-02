---
title: Install Microsoft Teams using MSI via Microsoft Endpoint Configuration Manager
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
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Install Microsoft Teams using Microsoft Endpoint Configuration Manager

> [!Tip]
> Watch the following session to learn about the benefits of the Windows Desktop Client, how to plan for it and how to deploy it: [Teams Windows Desktop Client](https://aka.ms/teams-clients).

To use Microsoft Endpoint Configuration Manager, or Group Policy, or any third-party distribution mechanisms for broad deployment, Microsoft has provided MSI files (both 32-bit and 64-bit) that admins can use for bulk deployment of Teams to select users or computers. Admins can use these files to remotely deploy Teams so that users do not have to manually download the Teams app. When deployed, Teams will auto launch for all users who sign in on that machine. (You can disable auto launch after installing the app. [See below](#disable-auto-launch-for-the-msi-installer).)
We recommend that you deploy the package to the computer, so all new users of the machine will also benefit from this deployment.

These are the links to the MSI files:


|Entity  |32-bit      |64-bit      |
|---------|---------|---------|
|Commercial     | [32-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true)        | [64-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true)       |
|Federal Government - GCC     | [32-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&ring=general_gcc&download=true)       | [64-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&ring=general_gcc&download=true)        |
|Federal Government - GCC High    | [32-bit](https://gov.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true)         | [64-bit](https://gov.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true)        |
|Federal Government - DoD     | [32-bit](https://dod.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true)        | [64-bit](https://dod.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true)        |

> [!NOTE]
> Install the 64-bit version of Teams on 64-bit operating systems. If you try to install the 64-bit version of Teams on a 32-bit operating system, the installation won't be successful and  currently you won't receive an error message.

Teams can also be included with a deployment of Office 365 ProPlus. For more information, see [Deploy Microsoft Teams with Office 365 ProPlus](https://docs.microsoft.com/deployoffice/teams-install).

> [!Note]
> To learn more about Microsoft Endpoint Configuration Manager, see [What is Configuration Manager?](https://docs.microsoft.com/configmgr/core/understand/introduction)

## Deployment procedure (recommended)

1. Retrieve the latest package.
2. Use the defaults prepopulated by the MSI.
3. Deploy to computers when possible.

## How the Microsoft Teams MSI package works

### PC installation

The Teams MSI will place an installer in Program Files. Whenever a user signs into a new Windows User Profile, the installer will be launched and a copy of the Teams app will be installed in that user's `AppData` folder. If a user already has the Teams app installed in the `AppData` folder, the MSI installer will skip the process for that user.

Do not use the MSI to deploy updates, because the client will auto update when it detects a new version is available from the service. To re-deploy the latest installer use the process of redeploying MSI described below. If you deploy an older version of the MSI package, the client will auto-update (except in VDI environments) when possible for the user. If a very old version gets deployed, the MSI will trigger an app update before the user is able to use Teams.

> [!Important]
> We don't recommended that you change the default install locations, as this could break the update flow. Having too old a version will eventually block users from accessing the service.

#### Target computer requirements

- .NET framework 4.5 or later
- Windows 8.1 or later
- Windows Server 2012 R2 or later
- 3 GB of disk space for each user profile (recommended)

### VDI installation

For complete guidance on how to deploy the Teams desktop app on VDI, see [Teams for Virtualized Desktop Infrastructure](teams-for-vdi.md).

## Clean up and redeployment procedure

If a user uninstalls Teams from their user profile, the MSI installer will track that the user has uninstalled the Teams app and no longer install Teams for that user profile. To redeploy Teams for this user on a particular computer where it was uninstalled, do the following:

> [!IMPORTANT]
> The next steps contain information about how to modify the registry. Make sure that you back up the registry before you modify it and that you know how to restore the registry if a problem occurs. For more information about how to back up, restore, and modify the registry, see [Windows registry information for advanced users](https://support.microsoft.com/help/256986).

1. Uninstall the Teams app installed for every user profile. For more information, see [Uninstall Microsoft Teams](https://support.office.com/article/uninstall-microsoft-teams-3b159754-3c26-4952-abe7-57d27f5f4c81#ID0EAABAAA=Desktop).
2. Delete the directory recursively under `%localappdata%\Microsoft\Teams\`.
3. Delete the `HKEY_CURRENT_USER\Software\Microsoft\Office\Teams\PreventInstallationFromMsi` registry value.
4. Redeploy the MSI package to that particular computer.

## Prevent Teams from starting automatically after installation

The default behavior of the MSI is to install the Teams app as soon as a user signs in and then automatically start Teams. If you don't want Teams to start automatically for users after it's installed, you can use Group Policy to set a policy setting or disable auto launch for the MSI installer.

### Use Group Policy (recommended)

Enable the **Prevent Microsoft Teams from starting automatically after installation** Group Policy setting. You can find this policy setting in User Configuration\Policies\Administrative Templates\Microsoft Teams. This is the recommended method because you can turn off or turn on the policy setting according to your organization's needs.

When you enable this policy setting before Teams is installed, Teams doesn't start automatically when users log in to Windows. After a user signs in to Teams for the first time, Teams starts automatically the next time the user logs in.

To learn more, see [Use Group Policy to prevent Teams from starting automatically after installation](https://docs.microsoft.com/deployoffice/teams-install#use-group-policy-to-prevent-microsoft-teams-from-starting-automatically-after-installation).

> [!CAUTION]
> If you've already deployed Teams and want to set this policy to disable Teams autostart, first set the Group Policy setting to the value you want, and then run the [Teams autostart reset script](scripts/powershell-script-teams-reset-autostart.md) on a per-user basis.

### Disable auto launch for the MSI installer

You can disable auto launch for the MSI installer by using the **OPTIONS="noAutoStart=true"** parameter as follows.  

For the 32-bit version:

```console
msiexec /i Teams_windows.msi OPTIONS="noAutoStart=true" ALLUSERS=1
```

For the 64-bit version:

```console
msiexec /i Teams_windows_x64.msi OPTIONS="noAutoStart=true" ALLUSERS=1
```

When a user logs in to Windows, Teams is installed with the MSI and a shortcut to start Teams is added to the user's desktop. Teams won't start until the user manually starts Teams. After the user manually starts Teams, Teams automatically starts whenever the user logs in.

Note that these examples also use the **ALLUSERS=1** parameter. When you set this parameter, Teams Machine-Wide Installer appears in Programs and Features in Control Panel and in Apps & features in Windows Settings for all users of the computer. All users can then uninstall Teams if they have admin credentials on the computer.

> [!Note]
> If you run the MSI manually, be sure to run it with elevated permissions. Even if you run it as an administrator, without running it with elevated permissions, the installer won't be able to configure the option to disable auto start.
