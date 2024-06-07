---
title:  Teams for Virtualized Desktop Infrastructure (VDI) 2.0
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 06/07/2024
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: fklurfan
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about Teams for Virtualized Desktop Infrastructure (VDI) 2.0.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Teams for VDI 2.0

VDI 2.0 is a new architecture for optimizing the delivery of multimedia workloads in virtual desktops.

## Components

|Component |Role |Update |Size |Notes |
|----------|-----|-------|-----|------|
|New Teams **vdiBridge**     |Server-side virtual channel module. |New version with every new Teams version. |Bundled with new Teams. | |
|Custom virtual channel (VC) |Custom VC owned by Microsoft Teams. |Stable API - no updates foreseen. | |Check the Citrix Studio policy **Virtual channel allow list**. |
|Plugin                      |Client-side VC dll. Responsible also for SlimCore download and clean-up. |Not frequent (ideally no updates). |Approximately 200 KB. |Bundled with [RD Client 1.2.5405.0](/azure/virtual-desktop/whats-new-client-windows) or Windows App 1.3.252 or higher. Citrix CWA 2402 or higher can fetch and install the plugin. |
|SlimCore                    |Media engine (operating system specific, not VDI vendor specific). |Auto-updated to a new version with each new Teams version. |Approximately 50 MB. |MSIX package hosted on Microsoft’s public CDN, [https://res.cdn.office.net/*](https://res.cdn.office.net/*) |

## System requirements

|Requirement |Minimum version |
|------------|----------------|
|New Teams   |24124.2315.2911.3357                                                                                      |
|AVD/W365    |Windows App: 1.3.252</br>Remote Desktop Client: 1.2.5405.0                                                |
|Citrix      |VDA: 2203 LTSR CU2 or 2212 CR</br>Citrix Workspace app: 2203 LTSR (any CU), 2402 LTSR or 2302 CR          |
|Endpoint    |Windows 10 1809 (SlimCore minimum requirement)</br>GPOs must not block MSIX installations (see Step 3 on the section below, Sideloading must be enabled)</br>Minimum CPU: Intel Celeron (or equivalent) @ 1.10GHz, 4 Cores, Minimum RAM: 4GB |

## Optimizing with new VDI solution for Teams

### Step 1: Confirm prerequisites

1. Make sure you have the new Microsoft Teams version 24124.2311.2896.3219 or higher.
1. Enable the new Teams policy **if necessary** for a specific user group (it's enabled by default at a Global org-wide level).
1. For Citrix, you must configure the **Virtual channel allow list** as described in **Citrix Virtual channel allow list** section of this article.

### Step 2: Plugin installation on the endpoint

1. For AVD and Windows 365, MsTeamsPluginAvd.dll is bundled with the RD Client for Windows 1.2.5405.0, or with the Windows App Store app 1.3.252 or higher.
  a. The plugin can be found in the same folder location where the RD Client is installed; either AppData\Local\Apps\Remote Desktop or C:\Program Files (x86), depending on the mode it was installed.
  b. For the [Windows App Store](/windows-app/overview) app, since it's MSIX-based, it's found in C:\Program Files\WindowsApps. Access to this folder is restricted.
1. For Citrix CWA 2402 or higher, MsTeamsPluginCitrix.dll can be installed either:
  a. Using the user interface when installing CWA:
     On the **Add-on(s)** page, select the **Install Microsoft Teams VDI plug-in** checkbox, and then select **Install**.
     Agree to the user agreement that pops up and proceed with the installation of the Citrix Workspace app.
  b. Via command line or scripts for managed devices using:
    `C:\>CitrixWorkspaceApp.exe installMSTeamsPlugin`
  c. Admins can also install the plugin manually on top of any existing supported CWA (see [System Requirements](#system-requirements)) using tools like SCCM (use the Windows app package deployment type) or Intune (use the Line-of-Business app).
  Admins can use **msiexec** with appropriate flags, as discussed in [this documentation](/windows-server/administration/windows-commands/msiexec).

> [!IMPORTANT]
> You can find the plugin MSI download link for Citrix customers [here](https://download.microsoft.com/download/3/0/e/30e54a38-eb74-44dc-9755-36dcac09656d/MsTeamsPluginCitrix.msi).

The plugin MSI automatically detects the CWA installation folder and places MsTeamsPluginCitrix.dll in that location:

|User type     |Installation folder                                                                             |Installation type |
|--------------|------------------------------------------------------------------------------------------------|------------------|
|Administrator |64-bit: C:\Program Files (x86)\Citrix\ICA Client</br>32-bit: C:\Program Files\Citrix\ICA Client |Per-system installation |
|User          |%USERPROFILE%\AppData\Local\Citrix\ICA Client                                                   |Per-user installation |

- Plugins can't be downgraded, only upgraded or reinstalled (repaired).
- If no CWA is found on the endpoint, installation is stopped.

### SlimCore MSIX staging and registration on the endpoint

This step is silently executed by the plugin, without user or admin intervention. The staging and registration relies on the App Readiness Service (ARS) on the endpoint. It's possible that the MSIX package installation is blocked by registry keys set by a Group Policy or a third-party tool. For a complete list of applicable registry keys, see [How Group Policy works with packaged apps - MSIX](/windows/msix/group-policy-msix).

The following registry keys could block new media engine MSIX package installation:

- BlockNonAdminUserInstall
- AllowAllTrustedApps
- AllowDevelopmentWithoutDevLicense

> [!IMPORTANT]
> If AllowAllTrustedApps is disabled, the new media engine (MSIX) installation fails. This issue has been fixed in the Windows October cumulative update KB5031455:
>
> - [Windows 10: October 26, 2023—KB5031445 (OS Build 19045.3636)](https://support.microsoft.com/topic/october-26-2023-kb5031445-os-build-19045-3636-preview-03f350cb-57f9-45e6-bfd7-438895d3c7fa)
> - [Windows 11: October 26, 2023—KB5031455 (OS Build 22621.2506)](https://support.microsoft.com/topic/october-26-2023-kb5031455-os-build-22621-2506-preview-6513c5ec-c5a2-4aaf-97f5-44c13d29e0d4)
>
> If this optional October update isn't available for your OS build, the November security update also includes the fix.

These three registry keys can be found at either of the following locations on the user’s device:

- HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\AppModelUnlock
- HKLM\SOFTWARE\Policies\Microsoft\Windows\Appx

Some policies might change these registry keys and block app installation in your organization because of a restrictive policy that was set by the admins. Some of the known GPO policies that could prevent installation include:

- Prevent non-admin users from installing packaged Windows apps.
- Allow all trusted apps to install (disabled).

## Verifying that the end point is optimized

Once you meet all the minimum requirements, launching new Teams for the first time will be in VDI 1.0 (WebRTC) optimized mode by default.

> [!IMPORTANT]
> For first run experiences, two app restarts are required to get into VDI 2.0 mode.

You can check in the Teams client that you have VDI 2.0 by going to the elipsis (three dots ...) on the top bar, then selecting Settings > About. The Teams and client versions are listed there.

The plugin (MsTeamsPluginAvd.dll or MsTeamsPluginCitrix.dll) is responsible for eventually downloading the media engine, and SlimCore, which is an MSIX package. It installs silently without admin privileges or reboots in (example, exact path varies):

`C:\Program Files\WindowsApps\Microsoft.Teams.SlimCoreVdi.win-x64.2024.15_2024.15.1.5_x64__8wekyb3d8bbwe`

The remote desktop client downloads the x64 or x86 SlimCore package, and the Citrix CWA will download an x86 package. This folder is locked down, so users don't have access to it. Admins can take ownership by modifying ACLs, though this isn't recommended. Instead, use PowerShell to list the MSIX apps in the endpoint:

```powershell
PowerShellCopy

Get-AppxPackage Microsoft.Teams.SlimCore*
```

> [!IMPORTANT]
> Microsoft stores up to ten versions of SlimCoreVdi for compatibility purposes, and in case the user accesses different VDI environments (such as persistent, where new Teams auto-updates itself, and non-persistent, where new Teams auto-updates are disabled).



