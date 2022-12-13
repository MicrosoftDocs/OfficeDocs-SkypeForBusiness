---
title: Bulk install Teams using Windows Installer (MSI)
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: amitsri
audience: admin
description: Use Windows Installer (MSI) files to distribute the Teams client to multiple users and computers.
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
ms.custom: seo-marvel-apr2020
appliesto: 
  - Microsoft Teams
---

# Bulk install Teams using Windows Installer (MSI)

> [!Tip]
> Watch the following session to learn about the benefits of the Windows Desktop Client, how to plan for it and how to deploy it: [Teams Windows Desktop Client](https://aka.ms/teams-clients).

Microsoft provides 32-bit, 64-bit, and ARM64 MSI files that you can use to bulk deploy Microsoft Teams to select users and computers. MSI files can be used with [Microsoft Endpoint Configuration Manager](/configmgr/core/understand/introduction), [Group Policy](/troubleshoot/windows-server/group-policy/use-group-policy-to-install-software), or third-party distribution software, to deploy Teams to your organization. Bulk deployments are useful because users don't need to download and install the Teams client manually. Rather, Teams will be deployed to computers and then auto-launch the first time users sign into a computer.

We recommend that you deploy the package to computers rather than a specific user. By targeting computers, all new users of those computers will benefit from this deployment.

>[!NOTE]
> Teams can also be distributed to your organization as part of Microsoft 365 Apps for enterprise. For more information, see [Deploy Microsoft Teams with Microsoft 365 Apps for enterprise](/deployoffice/teams-install).

## MSI files

The table below provides links to 32-bit, 64-bit, and ARM64 MSI files for Teams. Download the MSI that you want to install on computers in your organization. The x86 architecture (32-bit or 64-bit) Teams supports is independent of other Office apps installed on a computer.

If you have 64-bit computers, we recommend installing the 64-bit Teams MSI even if the computer is running a 32-bit version of Office. The ARM64 MSI can only be installed on computers that use the ARM architecture, such as the Surface Pro X.

> [!IMPORTANT]
> Install the 64-bit version of Teams only on 64-bit operating systems. If you try to install the 64-bit version of Teams on a 32-bit operating system, the installation won't be successful and you won't receive an error message.

|Entity  |32-bit      |64-bit      | ARM64 |
|---------|---------|---------|-----------|
|Commercial     | [32-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true)        | [64-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true)       | [ARM64](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=arm64&managedInstaller=true&download=true)|
|U.S. Government - GCC     | [32-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&ring=general_gcc&download=true)       | [64-bit](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&ring=general_gcc&download=true)        |[ARM64](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=arm64&managedInstaller=true&download=true) |
|U.S. Government - GCC High    | [32-bit](https://gov.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true)         | [64-bit](https://gov.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true)        |[ARM64](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=arm64&managedInstaller=true&download=true) |
|U.S. Government - DoD     | [32-bit](https://dod.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&managedInstaller=true&download=true)        | [64-bit](https://dod.teams.microsoft.us/downloads/desktopurl?env=production&plat=windows&arch=x64&managedInstaller=true&download=true)        | [ARM64](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&arch=arm64&managedInstaller=true&download=true)|

## How the Microsoft Teams MSI file works

### PC installation

The Teams MSI places an installer in `%SystemDrive%\Program Files\Teams Installer` on 32-bit Windows and `%SystemDrive%\Program Files (x86)\Teams Installer` on 64-bit Windows. Whenever a user signs into a new Windows user profile, the installer is launched and a copy of the Teams app is installed in that user's `%LocalAppData%\Microsoft\Teams` folder. If a user already has the Teams app installed in the `%LocalAppData%\Microsoft\Teams` folder, the MSI installer skips the process for that user.

MSI files can't be used to deploy updates. The Teams client will auto-update when it detects a new version is available from the service. To re-deploy the latest installer, use the process of redeploying MSI described below. If you deploy an older version of the MSI file, the client will auto-update (except in VDI environments) when possible for the user. If a very old version gets deployed, the MSI will trigger an app update before the user is able to use Teams.

> [!IMPORTANT]
> We don't recommended that you change the default install locations as this could break the update flow. Having too old a version will eventually block users from
> accessing the service.

#### Target computer requirements

Make sure the computers you install Teams on meeting the requirements listed in [Hardware requirements for Microsoft Teams](hardware-requirements-for-the-teams-app.md).

### VDI installation

For complete guidance on how to deploy the Teams desktop app on VDI, see [Teams for Virtualized Desktop Infrastructure](teams-for-vdi.md).

## Clean up and redeployment procedure

If a user uninstalls Teams from their user profile, the MSI installer will track that the user has uninstalled the Teams app and no longer install Teams for that user profile. To redeploy Teams for this user on a particular computer where it was uninstalled, do the following:

> [!IMPORTANT]
> The next steps contain information about how to modify the registry. Make sure that you back up the registry before you modify it and that you know how to restore the registry if a problem occurs. For more information about how to back up, restore, and modify the registry, see [Windows registry information for advanced users](https://support.microsoft.com/help/256986).

1. Uninstall the Teams app installed for every user profile. For more information, see [Uninstall Microsoft Teams](https://support.office.com/article/uninstall-microsoft-teams-3b159754-3c26-4952-abe7-57d27f5f4c81#ID0EAABAAA=Desktop).
2. Delete the directory recursively under `%LocalAppData%\Microsoft\Teams\` for each user profile.
3. Delete the `HKEY_CURRENT_USER\Software\Microsoft\Office\Teams\PreventInstallationFromMsi` registry value for each user profile.
4. Redeploy the MSI file to that particular computer.

> [!TIP]
> You can also use our [Teams deployment clean up script](scripts/powershell-script-deployment-cleanup.md) to complete steps 1 and 2.  

## Prevent Teams from starting automatically after installation

The default behavior of the MSI is to install the Teams app as soon as a user signs in and then automatically start Teams. If you don't want Teams to start automatically for users after it's installed, you can use Group Policy to set a policy setting or disable auto launch for the MSI installer.

### Use Group Policy (recommended)

Enable the **Prevent Microsoft Teams from starting automatically after installation** [Group Policy](/troubleshoot/windows-server/group-policy/use-group-policy-to-install-software) setting. You can find this policy setting in **User Configuration**\\**Policies**\\**Administrative Templates**\\**Microsoft Teams**. This is the recommended method because you can turn off or turn on the policy setting according to your organization's needs.

When you enable this policy setting before Teams is installed, Teams doesn't start automatically when users log in to Windows. After a user signs in to Teams for the first time, Teams starts automatically the next time the user logs in.

To learn more, see [Use Group Policy to prevent Teams from starting automatically after installation](/deployoffice/teams-install#use-group-policy-to-prevent-microsoft-teams-from-starting-automatically-after-installation).

> [!CAUTION]
> If you've already deployed Teams and want to set this policy to disable Teams autostart, first set the Group Policy setting to the value you want, and then run the [Teams autostart reset script](scripts/powershell-script-teams-reset-autostart.md) on a per-user basis.

### Disable auto launch for the MSI installer

You can disable auto launch for the MSI installer by using the `OPTIONS="noAutoStart=true"` parameter as follows.  

For the 32-bit version:

```console
msiexec /i Teams_windows.msi OPTIONS="noAutoStart=true" ALLUSERS=1
```

For the 64-bit version:

```console
msiexec /i Teams_windows_x64.msi OPTIONS="noAutoStart=true" ALLUSERS=1
```

When a user logs in to Windows, Teams is installed with the MSI. Teams won't start until the user manually starts Teams. After the user manually starts Teams, Teams automatically starts whenever the user logs in.

Note that these examples also use the **ALLUSERS=1** parameter. When you set this parameter, Teams Machine-Wide Installer appears in Programs and Features in Control Panel and in Apps & features in Windows Settings for all users of the computer. All users can then uninstall Teams if they have admin credentials on the computer.

> [!Note]
> If you run the MSI manually, be sure to run it with elevated permissions. Even if you run it as an administrator, without running it with elevated permissions, the installer won't be able to configure the option to disable auto start.
