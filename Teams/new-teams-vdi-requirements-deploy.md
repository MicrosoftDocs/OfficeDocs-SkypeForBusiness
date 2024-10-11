---
title:  New Microsoft Teams for Virtualized Desktop Infrastructure (VDI)
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 05/09/2024
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: fklurfan
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about upgrading to the new Teams for Virtualized Desktop Infrastructure (VDI)
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Upgrade to new Teams for Virtualized Desktop Infrastructure (VDI)

This article describes the requirements and limitations of using the new Microsoft Teams client in a virtualized environment.

## Important announcement for classic Teams for VDI

The **classic Teams for VDI** will reach end of support on **October 1, 2024**, and end of availability on **July 1, 2025**. For more information, see: [**End of availability for classic Teams client**](/MicrosoftTeams/teams-classic-client-end-of-availability)

After that date, users won't be able to use classic Teams but instead be prompted to switch to new Teams. We recommend you update to new Teams today.

>[!Note]
>New Teams for VDI is now generally available for customers in public clouds, GCC, GCC High and DoD government cloud.

## Requirements

For new Teams to be successfully installed, you need version 23306.3314.2555.9628 or higher.
In addition, virtual machines must meet the minimum requirements listed here:

|Requirement |Version|
|:-----|:-----|
|Windows|- Windows 10.0.19041 or higher (excluding Windows 10 LTSC for Teams desktop app) </br>- Windows Server 2019 (10.0.17763) </br>- Windows Server 2022 (20348.2402) or higher</br>- Windows Server 2016 is NOT supported. Plan upgrades.</br>- WebView2 framework required in Windows Server and Windows 10/11 Multi-User environments|
|Webview2|Update to the most current version. Learn more: [Enterprise management of WebView2 Runtimes](/microsoft-edge/webview2/concepts/enterprise)|
|Classic Teams app |Version 1.6.00.4472 or later to see the Try the new Teams toggle. Important: Classic Teams is only a requirement if you want users to be able to switch between classic Teams and new Teams. This prerequisite is optional if you only want your users to see the new Teams client. |
|Settings |Turn on the **Show Notification Banners** setting in System > Notifications > Microsoft Teams to receive Teams Notifications. |
|Exclude antivirus and DLP|Add new Teams to antivirus and DLP applications so Teams can start correctly. </br>Learn more: [Exclude antivirus and DLP applications from blocking Teams](/microsoftteams/troubleshoot/teams-administration/include-exclude-teams-from-antivirus-dlp)|

## Virtualization provider requirements

Currently, new Teams on VDI with audio/video (AV) optimization is certified with Azure Virtual Desktops, Windows 365, Citrix, and VMware.

Review the information in this section to ensure that you meet all requirements for proper functionality.

## Azure Virtual Desktop

Azure Virtual Desktop provides AV optimization for Teams on VDI. To learn more on requirements and installation, see [Use Teams on Azure Virtual Desktop](/azure/virtual-desktop/teams-on-avd).

The following minimum versions are necessary to support the new Teams client:

- Remote Desktop Client for Windows 1.2.2606
- Remote Desktop Client for Mac 10.7.7
- WebRTC Redirector Service 1.1.2110.16001

Microsoft recommends using the latest available versions.

In addition, you must deploy the following registry key on the virtual desktop for the new Teams client to be optimized:

HKLM\SOFTWARE\Microsoft\Teams:

- Name: IsWVDEnvironment
- Type: DWORD
- Value: 1

### RemoteApp

You can publish new Teams using the Windows `shell:appsFolder` location in the format: `shell:appsFolder\MSTeams_8wekyb3d8bbwe!MSTeams`.
 
See [this article](/azure/virtual-desktop/publish-applications?tabs=portal) for more details on RemoteApp.

## Windows 365

Windows 365 uses AV optimization provided by Azure Virtual Desktop to ensure optimal Teams experiences from Cloud PCs. To learn more on requirements and installation, see [Use Teams on Cloud PC](/windows-365/enterprise/teams-on-cloud-pc).

The Windows 10/11 images in the gallery are preconfigured with required optimization components. When you install and use Microsoft Teams in your Cloud PC, you get an optimized experience. A new image with the new Teams client will be added to the gallery in a few weeks.

If you want to create custom images that include optimizations for Microsoft Teams, you need to perform the steps described in [Create a custom Cloud PC image to support Microsoft Teams](/windows-365/enterprise/create-custom-image-support-teams).

The following minimum versions are necessary to support the new Teams client:

- Remote Desktop Client for Windows 1.2.2606
- Remote Desktop Client for Mac 10.7.7
- Windows 365 app for Windows via the Microsoft Store

In addition, you must deploy the following registry key on the virtual desktop for the new Teams client to be optimized:

HKLM\SOFTWARE\Microsoft\Teams:

- Name: IsWVDEnvironment
- Type: DWORD
- Value: 1

## Citrix Virtual Apps and Desktops and Citrix DaaS requirements

The following minimum versions are necessary to support the new Teams client:

Citrix Workspace app:

- Windows 2203 LTSR (and any CU)
- Windows 2302 CR
- Linux 2207
- Mac 2302
- Chrome/HTML5 2301

Citrix Virtual Delivery Agent (VDA):

- 2203 LTSR (and any CU)
- 2212 CR
- 1912 CU6 (but latest CU recommended - please note App Sharing is not supported on 1912)

In addition, you must deploy the following registry key on the VDA for the new Teams client to be optimized:

- Location:  HKLM\SOFTWARE\WOW6432Node\Citrix\WebSocketService
- Key (REG_Multi_SZ): ProcessWhitelist
- Value: msedgewebview2.exe

If this registry key is missing, the new Teams client operates in nonoptimized mode (server-side rendering). This regkey is not needed anymore if you are using VDA 2402 ([check here](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams) for more details).

>[!Note]
>Citrix Virtual Apps (also known as published apps) is currently supported with VDA 2402 LTSR.

For additional information, learn more at [Optimization for Microsoft Teams](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html).

## VMware Horizon and Workspace ONE requirements

The following minimum versions are necessary to support the new Teams client:

- Horizon 8 2111 ESB (8.4)

To learn more on the latest requirements and instructions, including how to configure media optimization for Teams, see [Configuring Media Optimization for Microsoft Teams](https://docs.vmware.com/en/VMware-Horizon/2006/horizon-remote-desktop-features/GUID-F68FA7BB-B08F-4EFF-9BB1-1F9FC71F8214.html).

## Deploy the new Microsoft Teams client

To deploy the new Microsoft Teams client to your organization, select one of the following options.

>[!IMPORTANT]
>You must use the latest version of the bootstrapper.exe. If you have downloaded the .exe previously, verify you have the latest version by viewing **Properties > Details > Product version** on your version and compare it to the properties on the latest download.

> [!NOTE]
> Make sure you have these KBs in your system, as they address many [policy settings restricting download and installation](/microsoftteams/troubleshoot/teams-administration/fix-new-teams-installation-issues#policy-settings-restricting-download--install) of new Teams.
>
> 1. If using Windows 10 or 11, make sure you're installing the appropriate KB patch [Windows 10: October 26, 2023 - KB5031445 (OS Build 19045.3636)](https://support.microsoft.com/topic/october-26-2023-kb5031445-os-build-19045-3636-preview-03f350cb-57f9-45e6-bfd7-438895d3c7fa) or [Windows 11: October 26, 2023 - KB5031445 (OS Build 22621.2506)](https://support.microsoft.com/topic/october-31-2023-kb5031455-os-builds-22621-2506-and-22631-2506-preview-6513c5ec-c5a2-4aaf-97f5-44c13d29e0d4). Otherwise, when GPO **AllowAllTrustedApps** is set to false and the issue mentioned in the [Features currently not available and known issues in VDI with the new Teams](#features-currently-not-available-and-known-issues-in-vdi-with-the-new-teams) section of this article can occur (New Teams fails to launch for users logging into non-persistent virtual desktops, or the app is **not** visible in the Start Menu.).
> 2. If GPO **BlockNonAdminUserInstall** is set to true, users might face the issue mentioned in the [Features currently not available and known issues  in VDI with the new Teams](#features-currently-not-available-and-known-issues-in-vdi-with-the-new-teams) section can occur (New Teams fails to launch for users logging into non-persistent virtual desktops, or the app is NOT visible in the Start Menu).
> Make sure you have the respective KB for your OS:
>
> - KB5035942 (Windows 11 version 22H2 and 23H2, all editions)
> - KB5035941 (Windows 10 any version, all editions)
> - [KB5036909](https://support.microsoft.com/topic/april-9-2024-kb5036909-os-build-20348-2402-36062ce9-f426-40c6-9fb9-ee5ab428da8c) (Windows Server 2022)

### Option 1: Uninstall the classic Teams client and install the new one

**Recommended way to deploy new Teams in VDI.** The direct or 'bulk deployment' method is used for this option. Learn more at [**Bulk deploy the new Microsoft Teams desktop client**](new-teams-bulk-install-client.md).

Using the teamsbootstrapper.exe -p command always guarantees the latest new Teams client is installed.

A phased and controlled rollout can then be achieved by selectively expanding the new computer catalogue/delivery group assignments to more users.

Admins can also use a local teams MSIX to provision new Teams. This option minimizes the amount of bandwidth used for the initial installation. The MSIX can exist in a local path or UNC.

1. [Download the .exe installer.](https://go.microsoft.com/fwlink/?linkid=2243204&clcid=0x409).
2. Download the MSIX:</br>- [MSIX x86](https://go.microsoft.com/fwlink/?linkid=2196060&clcid=0x409)</br>- [MSIX x64](https://go.microsoft.com/fwlink/?linkid=2196106)</br>- [ARM64](https://go.microsoft.com/fwlink/?linkid=2196207&clcid=0x409).
3. Open the Command Prompt as an Admin.
4. Depending on where your MSIX is located, do the following steps:
</br>

  **For local path, enter:** *.\teamsbootstrapper.exe -p -o "c:\path\to\teams.msix"*

   *Example:*

   :::image type="content" source="media/new-teams-bulk-offline-localpath.png" alt-text="local path location for offline installer":::

   **For UNC, enter:** *.\teamsbootstrapper.exe -p -o "\\unc\path\to\teams.msix"*

   *Example:*

   :::image type="content" source="media/new-teams-bulk-offline-unc.png" alt-text="offline location using unc":::

### Option 2: Install both apps 'side by side'

Let the user switch between them by using the toggle on the top left of the Teams UI.
You can control who sees the toggle by configuring the Teams Admin Center policy **Teams update policy**.

If the toggle is being used for the new Teams client rollout, admins must make sure that the VDI environments meet the minimum requirements described here: [Troubleshooting installation issues in the new Teams client](/microsoftteams/troubleshoot/teams-administration/fix-new-teams-installation-issues).

If IT administrators set restrictions for MSIX or deploy GPOs, it could prevent users from downloading and installing the app. If restrictions are in place, the user could see errors like this:

  :::image type="content" source="media/new-teams-troubleshooting-error-isntallation-org-policies.png" alt-text="error with org policies.":::

> [!IMPORTANT]
> The 'side by side' method is only supported in persistent environments. Classic Teams 1.7.00.7956 or higher will suppress the app switcher toggle irrespective of the Teams Admin Center policy value when classic Teams is running in a non-persistent environment, where non-persistent is detected based on the installation folder of classic Teams MSI, C:\Program Files (x86).

## Classic Teams versus new Teams installers in VDI environments

The classic Teams client and the new Teams client have different install locations and profile management requirements. It's important to understand the differences and plan accordingly.

|Installer format|Install location|Auto update|
|:-----|:-----|:-----|
|Classic Teams MSI with the ALLUSERS=1 flag|C:\Program Files (x86)\Microsoft\Teams|Disabled|
|Classic Teams .EXE|%localappdata%\Microsoft\Teams |Enabled |
|New Teams .EXE bootstrapper|**Teamsbootstrapper.exe** is a lightweight wrapper online installer with a headless command-line interface. It allows admins to 'provision' (install) the app for all users on a given target computer/. </br> It installs the Teams MSIX package on a target computer, making sure that Teams can interoperate correctly with Office and other Microsoft software.</br>C:\Program Files\WindowsApps\PublisherName.AppName_AppVersion_architecture_PublisherID</br></br>**Example**</br>C:\Program Files\WindowsApps\MSTeams.23306.3314.2555.9628_x64_8wekyb3d8bbwe|Enabled.  It can be disabled via regkey. Learn more: [Disable new Teams autoupdate](#disable-new-teams-autoupdate)|

## Troubleshooting new Teams deployment errors

Administrators can rely on the teamsbootstrapper.exe [error code](/windows/win32/seccrypto/common-hresult-values) that describes the problem. If the error code doesn't provide enough information, more diagnostic information can be found in the detailed event logs.

1. Go the Event Viewer (Local) **> Applications and Services Logs > Microsoft > Windows**.
2. Check for available logs under these categories:

- AppxPackagingOM > Microsoft-Windows-AppxPackaging/Operational
- AppXDeployment-Server > Microsoft-Windows-AppXDeploymentServer/Operational

3. Review logs under **AppXDeployment-Server**

Learn more here: [Common error codes](/windows/win32/appxpkg/troubleshooting#common-error-codes)

|Teamsbootstrapper.exe common error codes |Further information |
|-----------------------------------------|--------------------|
|0x80070057                               |The bootstrapper command doesn't have the full path (avoid URIs using .\). Try the full path instead (for example, c:\temp\MSTeams-x64.msix). |
|0x80070032                               |A probable error on the UNC path. Try copying the MSIX to a local folder instead. |
|0x80004004                               |There might be a regkey 'maglevInstallationSource' left behind in regkey HKLM\Software\WoW6432Node\Microsoft\Office\Teams. Try deleting it and reattempting the install. |

## Installation instructions for Windows Server 2019

For Windows Server 2019, the only supported installation method is:  

```Command Line
Dism /Online /Add-ProvisionedAppxPackage /PackagePath:<MSIX package path> /SkipLicense
```

Make sure sideloading is enabled, and that WebView2 is installed. See 'Requirements' section above.

The /SkipLicense command is needed because the MSIX package isn't considered a "Store Package" (since it wasn't downloaded from the store). Therefore, for the Dism installation command to succeed, you need to enable this policy as well during installation time:
Computer Configuration > Administrative Templates > Windows Components > App Package Deployment > **Allow all trusted apps to install**.

> [!IMPORTANT]
> `AllowAllTrustedApps` must be enabled after the new Teams package is successfully staged in the golden image. Otherwise, the registration of the package to each user (which happens only on login) will fail and users wont be able to launch the app.

Known limitations:

- Classic Teams on Windows Server 2019 isn't displaying the app switcher toggle if Classic Teams version is lower than 1.6.00.33567
- New Teams on Windows Server 2019 needs [FSLogix 2210 HotFix 4](/fslogix/overview-release-notes#fslogix-2210-hotfix-4-29888427471).

### Outlook presence integration with New Teams in Windows Server 2019

For Outlook to properly display presence status, the following steps are required on the golden image:

1. Install machine-wide (ALLUSERS=1) the '[Windows 10 1809 and Windows Server 2019 KB5035849 240209_02051 Feature Preview.msi](https://statics.teams.cdn.office.net/evergreen-assets/DesktopClient/Windows%2010%201809%20and%20Windows%20Server%202019%20KB5035849%20240209_02051%20Feature%20Preview.msi)'.
1. Open your Group Policy Editor. Navigate to Computer Configuration\Administrative Templates\KB5035849 240209_02051 Feature Preview\Windows 10, version 1809 and Windows Server 2019. Change the value of that Setting to **Enabled**.
1. Install [KB5035849](https://support.microsoft.com/topic/march-12-2024-kb5035849-os-build-17763-5576-719f5f8d-51c6-43f0-a612-1c15802fed06) March 2024 cumulative update from the [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/Search.aspx?q=2024-03%20Cumulative%20Update%20for%20Windows%20Server%202019%20for%20x64-based%20Systems%20(KB5035849)) or WSUS for Enterprises.
1. Install machine-wide (ALLUSERS=1) the '[MSTeamsNativeUtility.msi](https://statics.teams.cdn.office.net/evergreen-assets/DesktopClient/MSTeamsNativeUtility.msi)'.
1. Reboot the virtual machine.
1. Install new Teams 24033.811.2738.2546 or higher, using Dism as described in the section above.

> [!NOTE]
> Steps 1, 2, 3, 4, and 5 are only required once. Subsequent golden image maintenances will not need these steps repeated.

> [!IMPORTANT]
> Outlook must be started **after** new Teams is launched for presence to be shown correctly.

## Remove new Teams for all users

To uninstall and deprovision the new Teams for all users, use the following command:

```powershell
./teamsbootstrapper -x
```

This command unregisters and deprovisions the new Teams for all users. Teams user profile/cache is deleted.

## Disable new Teams autoupdate

To prevent new Teams from autoupdating, use the following registry key on the virtual machine.
Only new Teams builds higher than 23306.3314.2555.9628 in VDI can process this registry key.

```Registry editor
Location: Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Teams
Name: disableAutoUpdate
Type: DWORD
Value: 1
```

## New Teams auto-start

The auto-start behavior of Teams is controlled by three components:

1. By default, MSIX-based applications will not auto-start until there is a first launch, because the Windows OS doesn't auto-start packages in a provisioned state. An AppX registration is needed with user consent. After the first launch, users can go to **Settings** > **General** and fill the **Auto-start Teams** checkbox, or enable auto-start from the Windows Setting menu.

2. If the "Auto-start Teams" checkbox is greyed out, it means a system-wide GPO is disabling this option for UWP apps:

```Registry editor
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System] 
"EnableFullTrustStartupTasks"=dword:00000000
"EnableUwpStartupTasks"=dword:00000000
"SupportFullTrustStartupTasks"=dword:00000000
"SupportUwpStartupTasks"=dword:00000000
```

This registry setting causes the option to be unavailable in the operation systems under **Settings** > **Apps** > **Installed Apps**. In order to change this, create the regkeys with the values as shown below:

```Registry editor
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System]
"EnableFullTrustStartupTasks"=dword:00000002
"EnableUwpStartupTasks"=dword:00000002
"SupportFullTrustStartupTasks"=dword:00000001
"SupportUwpStartupTasks"=dword:00000001
```

Restart the virtual machine to see the startup options active in the operative system’s settings menu.

3. This registry key controls the Teams auto-start behavior, so you can enable or disable it programmatically.

```Registry editor
[HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\Windows\CurrentVersion\AppModel\SystemAppData\MSTeams_8wekyb3d8bbwe\TeamsTfwStartupTask]
"State"=dword:00000002
"UserEnabledStartupOnce"=dword:00000001
```

|State            |Number |Information                                                              |
|-----------------|-------|-------------------------------------------------------------------------|
|Disabled         |0      |The task is disabled.                                                    |
|DisabledByUser   |1      |The task was disabled by the user. It can only be re-enabled by the user.|
|EnabledByUser    |2      |The task is enabled.                                                     |
|DisabledByPolicy |3      |The task is disabled by the administrator or group policy. Platforms that don't support startup taks also report DisabledByPolicy. |
|EnabledByPolicy  |4      |The task is enabled by the administrator or group policy.                |

You can learn more at [this link](/uwp/api/windows.applicationmodel.startuptaskstate#fields).

> [!IMPORTANT]
> If you're using non-persistent VDI, you must make sure the TeamsTfwStartupTask registry key is roamed. FSLogix ODFC containers won't roam this, so you must rely on your other profile management tools (VMWare DEM, AppSense, Citrix UPM) to persist this key.

## Profile and cache location for new Teams Client

All the user settings and configurations are now stored in:

- C:\Users\\<username\>\AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\
- C:\Users\\<username\>\AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\Settings\settings.dat
- C:\Users\\<username\>\AppData\Local\Publishers\8wekyb3d8bbwe\TeamsSharedConfig\app_switcher_settings.json
- C:\Users\\<username\>\AppData\Local\Publishers\8wekyb3d8bbwe\TeamsSharedConfig\tma_settings.json

Make sure these folders and files are persisted for proper Teams functioning.

> [!NOTE]
> It's critical that **all** the necessary directories and top folder structure under AppData\Local\Packages\MSTeams_8wekyb3d8bbwe are correctly set up as directories, not as files or reparse points, and roam with the user's profile:
>
> AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\AC
> AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\AppData
> AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache
> AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalState
> AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\RoamingState
> AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\Settings
> AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\SystemAppData
> AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\TempState

**TeamsSharedConfig** stores user configurations for the Teams app switcher toggle (and what should be the default app, the Classic or New Teams), and the Teams Meeting Add In for Outlook.

The folder "meeting-addin" under TeamsSharedConfig shouldn't be persisted, as this could cause issues with the default meeting coordinates in the meeting templates inserted into Outlook.

>[!Important]
>Microsoft recommends FSLogix 2210 HotFix 4 ([2.9.8884.27471](/fslogix/overview-release-notes#fslogix-2210-hotfix-4-29888427471)) in order to guarantee proper integration with the new Teams client in VDI. The following issues have been addressed on that release:
>
>- Windows Server 2019 would sometimes fail to query the provisioned AppX applications for the user during sign-out.
>- [MSIX folders that should not be backed](/fslogix/troubleshooting-appx-issues#non-roamable-folders-not-backed-up) up would be removed during sign-out instead of only removing the contents of those folders.
>- New Microsoft Teams crashes or fails to start in Windows Server 2019.
>- New Microsoft Teams would display an error during launch with **The parameter is incorrect**.
>- New Microsoft Teams would display an error during launch with **Invalid function**.
>- New Microsoft Teams wouldn't on-demand register during sign-in when using the ODFC container.
>- New Microsoft Teams wouldn't on-demand register during profile creation and wouldn't register during future sign-ins, despite being installed.
>- User-based Group Policy settings would persist in the user's profile after the policy setting was removed or set to disabled.
>
>*Note:* Customers using Profile and ODFC or just ODFC containers, will still need to add the setting ‘IncludeTeams’ for the new Teams user data/cache to be preserved.

>[!Note]
>[Folder Redirection or Roaming User Profiles](/windows-server/storage/folder-redirection/folder-redirection-rup-overview) aren't supported with the new Teams client in VDI environments since they can't roam folders in AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams. Customers can continue to use Folder Redirection or Roaming User Profiles with a complementary product, such as FSLogix, Citrix Profile Manager, and VMware DEM, that can roam the Appdata\Local folders above.

> [!IMPORTANT]
> Citrix recommends Citrix Profile Manager version 2402 or 2203 CU5, as those address new Teams registrations errors and "the parameter is incorrect" error when trying to launch the application.
>
> If customers still experience Teams related issues, reach out to Citrix for a private build for 2402 CU1 or 2203 CU6.

### Folder exclusions

#### Disk storage usage

The new Teams app takes up about 50% less disk space than the classic version. To make it easier to distribute our client to Windows devices, we have added support for MSIX, which improves the dependability of installations and app updates, as well as reduces network bandwidth and disk space consumption. This packaging technology also shows the accurate disk space usage. Users may see larger disk usage than classic Teams in Windows settings, but the difference is mainly because the disk space related to Electron-based classic Teams is not fully and correctly shown.

#### Disk Footprint - Key folders and location

- **App installer**: C:\Program Files\WindowsApps\MSTeams_[version]_[arch]__8wekyb3d8bbwe
  Includes the installation package, supports the ability to reset the app, and allows single instancing.
- **User and app data**: C:\Users\\<alias\>\AppData\Local\Packages\MSTeams_8wekyb3d8bbwe
  This includes code (Javascript bundles), code cache, browser caches, databases for user data (like conversations which scales based on usage), and web storage (from domains hosted within Teams, such as Sharepoint, Viva learning, Apps, and so on).

The underlying folder structure is logically similar to Electron-based classic Teams. For non-persistent setups where storage footprint is a consideration, the following guidance applies:

##### Recommended for exclusion

|Folder                      |Folder path |Role |Exclusion impact |
|----------------------------|------------|---------|-----------------|
|**Logs**                    |LocalCache\Microsoft\MSTeams\Logs </br>LocalCache\Microsoft\MSTeams\PerfLog |Diagnostics, perf logs, and so on. |No impact. |
|**WebStorage**              |LocalCache\Microsoft\MSTeams\EBWebView\WV2Profile_tfw\WebStorage |Storage used and managed by the browser when accessing other web apps inside a web app using iframes. For example, loading Sharepoint, OneDrive and office apps within Teams. |Loading these apps again could be slower after clearing this cache. |
|**GPU Cache**               |LocalCache\Microsoft\MSTeams\EBWebView\WV2Profile_tfw\GPUCache |GPU cache. |No impact. |
|**StartMenuExperienceHost** |AppData\Local\Packages\Microsoft.Windows.StartMenuExperienceHost_cw5n1h2txyewy\TempState |Responsible for the **Start Menu** button and the tiles within it. |No impact. The exclusion is recommended to solve a missing Teams icon in the Start menu issue. |
|**ShellExperienceHost (For Windows Server 2019 only)** |AppData\Local\Packages\Microsoft.Windows.ShellExperienceHost_cw5n1h2txyewy\TempState |Responsible for the **Start Menu** button and the tiles within it. |No impact. The exclusion is recommended to solve a missing Teams icon in the Start menu issue. |

##### Review tradeoff considerations, requiring evaluation and testing for these environments

|Folder             |Folder path |Role |Exclusion impact |
|-------------------|---------|---------|---------|
|**Service worker** |LocalCache\Microsoft\MSTeams\EBWebView\WV2Profile_tfw\ Service Worker\CacheStorage </br>LocalCache\Microsoft\MSTeams\EBWebView\WV2Profile_tfw\Code Cache |Code and caching of Web/JS Scripts for the app to run. |- Reduced performance to download and load scripts on every app launch </br>- No offline access to app |
|**IndexedDB**      |LocalCache\Microsoft\MSTeams\EBWebView\WV2Profile_tfw\IndexedDB |Holds app and user data and is the recommended way to cache data at scale in a web app to improve responsiveness. |- Significantly higher app launch times as data (such as chat or channel conversations) must be pulled down, along with network usage as data needing to be downloaded and cached every time. </br>- The size of the data varies based on the user profile. </br>- Users might see **We’re setting things up for you** in the launch splash-screen. |
|**Cache**          |LocalCache\Microsoft\MSTeams\EBWebView\WV2Profile_tfw\Cache |Cache used and managed by the browser for the contents of all network calls that leave the app. Also known as Disk Cache. |For example, profile pictures in Teams are mostly cached in this storage by the browser. These will need to be downloaded again. |

Other than the folders in this section, we don't recommend excluding additional directories.

## New Teams and Outlook integration

When the "Register the new Teams as the chat app for Microsoft 365" checkbox is selected under Settings > General > System, this lets the new Teams client integrate with all the Microsoft 365 apps that have instant message capabilities (presence, chat, VOIP, etc.).

For example, Outlook goes through the discovery process outlined here to integrate with the default IM client application:  [Integrating IM applications with Office](/office/client-developer/shared/integrating-im-applications-with-office#discovering-the-im-application)

>[!Note]
>If the new Teams is installed on a virtual machine where the classic Teams is **not** installed, you must make sure you are using new Teams version 23320.3021.2567.4799 or higher in order to guarantee proper integration with Outlook and presence.

### Teams Meeting add-in

Additionally, the new Teams MSIX package bundles the Teams Meeting add-in (or TMA) MSI ("MicrosoftTeamsMeetingAddinInstaller.msi"). TMA lets you schedule a Teams meeting from Outlook.

For Security articles related to TMA integration with the Outlook client, learn more at [**Teams meeting add-in security when using your Outlook client**](/microsoftteams/teams-meeting-addin-security-with-outlook).

All new Teams files that are installed on the computer are signed, so IT admins can use  [AppLocker](/microsoftteams/applocker-in-teams) / Code Integrity  / Windows Defender Application Guard policies configured to enforce that.

- For New Teams per-user installations of TMA, the install folder is in AppData\Local\Microsoft\TeamsMeetingAddin
- Starting from new Teams version 24060.2623.2790.8046, the TMA per-user install folder is changed to  AppData\Local\Microsoft\TeamsMeetingAdd-in (an additional '-')
- Installation logs for TMA MSI are stored here: *AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams\Logs \tma_addin_msi.txt*

>[!Note]
>In Windows Server or Windows 10/11 Multiuser environments, installation of MicrosoftTeamsMeetingAddinInstaller.msi can fail with the error *"Installation success or error status: 1625."*.

This error is caused by GPOs affecting Windows Installer. This includes [**DisableUserInstalls**](/windows/win32/msi/disableuserinstalls), [**DisableMSI**](/windows/win32/msi/disablemsi), or AppLocker policies based on Publisher rule conditions, or a RuleCollection for MSI installs. In this case you must create an exception such as:

- FilePathCondition Path="%PROGRAMFILES%\WINDOWSAPPS\\*\MICROSOFTTEAMSMEETINGADDININSTALLER.MSI"

**Workaround:**  You can install the MSI that is located in the new Teams installation directory from an Admin Command prompt using:  

```powershell

msiexec.exe /i "C:\Program Files\WindowsApps\MSTeams_X.X.X.X_x64__8wekyb3d8bbwe\MicrosoftTeamsMeetingAddinInstaller.msi" ALLUSERS=1 /qn /norestart TARGETDIR="C:\Program Files (x86)\Microsoft\TeamsMeetingAdd-in\<version>\"

```

- TARGETDIR must be kept consistent across installs so that the Teams Meeting Add-in MSI can easily detect and clean up older versions. If multiple directories are used, then the installation may not behave as expected.
- **X.X.X.X** needs to be replaced by the New Teams version. Make sure there's a double underscore between the CPU architecture (x64) and the PublisherID (8wekyb3d8bbwe). The exact version number can be extracted by running this command in PowerShell:
  
  ```powershell

  Get-AppXPackage -Name "*msteams*" | Select-Object -ExpandProperty Version

  ```
  
- **version** must be replaced with the MSI file version, for example, 1.24.2203.0. The exact version number can be extracted by running this command in PowerShell:

```powershell

PS C:\WINDOWS\system32> Get-AppLockerFileInformation -Path "C:\PROGRAM FILES\WINDOWSAPPS\MSTEAMS_24026.1000.2656.1710_X64__8WEKYB3D8BBWE\MICROSOFTTEAMSMEETINGADDININSTALLER.MSI" | Select -ExpandProperty Publisher | select BinaryVersion

BinaryVersion

1.24.2203.0

```

**Example:** The following are examples of the final command:

```command prompt

msiexec.exe /i "C:\Program Files\WindowsApps\MSTeams_23320.3021.2567.4799_x64__8wekyb3d8bbwe\MicrosoftTeamsMeetingAddinInstaller.msi" ALLUSERS=1 /qn /norestart TARGETDIR="C:\Program Files (x86)\Microsoft\TeamsMeetingAdd-in\1.24.2203.0\"
```

```powershell
If (-not ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole] 'Administrator') ){
    Write-Error "Need to run as administrator. Exiting.."
    exit 1
}

# Get Version of currently installed new Teams Package
if (-not ($NewTeamsPackageVersion = (Get-AppxPackage -Name MSTeams).Version)) {
    Write-Host "New Teams Package not found. Please install new Teams from https://aka.ms/GetTeams ."
    exit 1
}
Write-Host "Found new Teams Version: $NewTeamsPackageVersion"

# Get Teams Meeting Addin Version
$TMAPath = "{0}\WINDOWSAPPS\MSTEAMS_{1}_X64__8WEKYB3D8BBWE\MICROSOFTTEAMSMEETINGADDININSTALLER.MSI" -f $env:programfiles,$NewTeamsPackageVersion
if (-not ($TMAVersion = (Get-AppLockerFileInformation -Path $TMAPath | Select-Object -ExpandProperty Publisher).BinaryVersion))
{
    Write-Host "Teams Meeting Addin not found in $TMAPath."
    exit 1
}
Write-Host "Found Teams Meeting Addin Version: $TMAVersion"

# Install parameters
$TargetDir = "{0}\Microsoft\TeamsMeetingAddin\{1}\" -f ${env:ProgramFiles(x86)},$TMAVersion
$params = '/i "{0}" TARGETDIR="{1}" /qn ALLUSERS=1' -f $TMAPath, $TargetDir

# Start the install process
write-host "executing msiexec.exe $params"
Start-Process msiexec.exe -ArgumentList $params
write-host "Please confirm install result in Windows Eventlog"
```

After installation, restart Outlook and verify TMA is loading. Logs are located on %localappdata%\Temp\Microsoft\Teams\meeting-addin.

For Teams Meeting add-in troubleshooting articles, learn more at: [**Resolve issues with Teams Meeting add-in for Outlook**](/microsoftteams/troubleshoot/meetings/resolve-teams-meeting-add-in-issues).

If classic Teams is removed and only new Teams is being installed, the Teams Meeting Add-in MSI could fail to create three registry keys under HKCU that prevent the Meeting Add In from loading properly.

These keys should be then deployed via additional sign in scripts or similar methods:

:::image type="content" source="media/new-teams-vdi-meeting-addin.png" alt-text="new Teams meeting add in":::

> [!NOTE]
> These HKCU regkeys aren't needed anymore if you're installing TeamsMeetingAddIn.msi version 1.0.24054.1 (which is bundled with new Teams 24060.2623.2790.8046 or higher) using the msiexec command previously mentioned in this article, with the ALLUSERS=1 parameter. Version 1.0.24054.1 has a fix for equivalent regkeys creation, but under HKLM\SOFTWARE\Microsoft\Office\Outlook\Addins\TeamsAddin.FastConnect.

### Troubleshooting new Teams and Outlook integration

#### Symptoms

You see any of the following issues when you check the presence status for a user in Outlook:

- The presence indicator isn't visible.
- The displayed presence is incorrect.
- The presence status is **Status unknown**.

#### Troubleshooting steps

1. Make sure new Teams is running. Then launch Outlook.
2. Check the registry settings on your computer to verify that new Teams is registered as the default instant messaging (IM) app.

  a. Start Registry Editor.
  b. Locate the following subkey:

```
- HKEY_CURRENT_USER\Software\IM Providers
```

  c. Verify the following values:

```
- **Name:** DefaultIMApp
- **Type:** REG_SZ
- **Data:** MsTeams (If you see Teams, it means classic Teams is still the default IM app)
```

4. Locate the following subkey:

- HKEY_CURRENT_USER\Software\IM Providers\MsTeams   (Outlook monitors this registry key for value changes)

5. Verify the following values:

  -Name: UpAndRunning
  -Type: REG_DWORD
  -Data: 2   (0—Not running, 1—Starting, 2—Running)

6. If the issues persist, contact Microsoft Support.

## Control fallback mode in Teams

When users connect from an unsupported endpoint, the users are in fallback mode, in which Audio/Video isn't optimized. You can disable or enable fallback mode by setting one of the following registry DWORD values:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Teams\DisableFallback`
`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\Teams\DisableFallback`

- To disable fallback mode, set the value to 1.
- To enable audio only, set the value to 2.
- If the value isn't present or is set to 0 (zero), fallback mode is enabled.
- On Fallback, screen sharing functionality is supported with a different screen picker UI (similar to the experience a user would see on Teams for Web).

## Multitenant and Multi-account in VDI

The new version of Teams in VDI allows you to sign in quickly and easily, and allowing you to switch between multiple accounts and organizations **from the same** Microsoft 365 cloud environment.

> [!NOTE]
> Cross cloud guests and Cross cloud meetings are not supported on VDI.
> See [Collaborate with guests from other Microsoft 365 cloud environments](/microsoft-365/solutions/collaborate-guests-cross-cloud) and [Manage accounts and organizations in Microsoft Teams](https://support.microsoft.com/office/manage-accounts-and-organizations-in-microsoft-teams-7b221128-6643-465c-a317-679e48cd2ce9) for more information.

If any of your accounts have guest access to other organizations, you don’t need to add them--they appear automatically.
A guest is someone from outside an organization that a team owner invites to join the team, such as a partner or consultant. Guests have fewer capabilities than team members or team owners.

Learn more: [Manage accounts and organizations in Microsoft Teams](https://support.microsoft.com/office/manage-accounts-and-organizations-in-microsoft-teams-7b221128-6643-465c-a317-679e48cd2ce9)

## Features currently not available and known issues in VDI with the new Teams

- New Microsoft Teams doesn't on-demand register during FSLogix profile creation (even with HotFix 4), and doesn't register during future signins, despite being installed. The issue is caused by a race condition between Process Lifetime Manager (PLM) service and AppxSvc causing a transient failure when updating the package with error 0x80004001 (E_NOTIMPL). If the PLM service is not running, the new Teams registration fails.
  - (In MSIX, Registration occurs on a per-user basis and begins when a user logs on. The OS will then load the preinstalled packaged app, creating user-specific app data, FTAs, and app tiles in the Start menu. This is done by the AppReadiness Service, which is aware of all preinstalled apps and requests the Appx Deployment Service (AppxSvc) deploy those packages.)
  - Customers hitting this error, even with FSLogix Hotfix 4, must deploy these KBs:
    - Windows 11 21H2 [KB5043067](https://support.microsoft.com/topic/september-10-2024-kb5043067-os-build-22000-3197-62287850-4f0d-4e4a-9fe8-b026bb1be994)
    - Windows Server 2022 [KB5042881](https://support.microsoft.com/topic/september-10-2024-kb5042881-os-build-20348-2700-5b548143-9613-4e5a-9454-8ed9be8b2bd2)
    - Windows Server 2019 [KB5043050](https://support.microsoft.com/topic/september-10-2024-kb5043050-os-build-17763-6293-66e9809a-1838-4474-a6a7-90d64f042f00)
  - This bug has addressed with [KB5037849](https://support.microsoft.com/help/5037849) for Windows 10 (May 2024). The issue isn't present on Windows 11 22H2 or higher.
- New Teams fails to launch for users logging into single-user non-persistent Windows 10 virtual desktops, or the app isn't visible in the Start Menu, but the app might become visible and launches successfully fifteen minutes after logging in.
  - This issue is addressed in [KB5041582](https://support.microsoft.com/topic/august-29-2024-kb5041582-os-build-19045-4842-preview-f4c4d191-5457-475c-80ac-e1d43cf9c941)/[KB5041587](https://support.microsoft.com/topic/august-27-2024-kb5041587-os-builds-22621-4112-and-22631-4112-preview-9706ea0e-6f72-430e-b08a-878963dafe08) for Windows 10/11, and Teams 24215.1007.3082.1590 (or higher) - both components are needed.
  - You might also need to exclude the following location from your roaming profile solution ( for FSLogix customers, as an example, via redirections.xml): `AppData\Local\Packages\Microsoft.Windows.StartMenuExperienceHost_cw5n1h2txyewy\TempState`
  - **NOTE** - The issue isn't seen in **multi-user** Windows 10 or 11. For Windows 2019, the StartMenuExperienceHost exclusion (`AppData\Local\Packages\Microsoft.Windows.ShellExperienceHost_cw5n1h2txyewy\TempState`) should be a workaround until a KB for that OS is published on Microsoft's October patch Tuesday (KB 5044277).
- Customers installing new Teams on a golden image which later undergoes a sysprep to generalize it are failing to launch the app. This includes templates from Azure Image Gallery.
  - Users logging in to the provisioned virtual machines see the Teams icon greyed out in the start menu and clicking on it has no effect.
  - The AppX log in the Event Viewer has the error 0x80073CF1.
  - Running `Get-AppxPackage -name MsTeams -allusers` from an elevated PowerShell window shows that PackageUserInformation is in a **Paused state** for SID S-1-15-18 (LocalSystem). This error is not seen on W11 22H2 or higher. Install [KB5039299](https://support.microsoft.com/topic/june-25-2024-kb5039299-os-build-19045-4598-preview-d4e3e815-fdd8-465e-8144-42afa165efed) for Windows 10 [KB5040437](https://support.microsoft.com/topic/july-9-2024-kb5040437-os-build-20348-2582-5b28d9b8-fcba-43bb-91e6-062f43c7ec7c) for WS2022, and [KB5040431](https://support.microsoft.com/topic/july-9-2024-kb5040431-os-build-22000-3079-346db750-842d-41b8-a55a-103cc04d175a) for W11 21H2.
- Screen sharing from chat for Azure Virtual Desktops/Windows 365 (This issue is now fixed on RD Client 1.2.5105 and Redirector Service
[1.50.2402.29001](/azure/virtual-desktop/whats-new-webrtc#updates-for-version-150240229001)).
- Screen sharing from chat for Citrix when using Workspace app 2311 only.
- msteams_autostart.exe "The parameter is incorrect": In non-persistent environments that use FSLogix (any version prior to 2210 HotFix 4) or Citrix Profile Manager profile containers, when new Teams attempts to autostart or a user tries to launch Teams from the Start menu, it throws the error: "The parameter is incorrect." The frequency and reproducibility of the error varies depending on the environment and especially the antivirus software being used (SentinelOne, Palo Alto, Trend Micro, Bitdefender, CrowdStrike, and so on.) and exclusions in place. This issue is now fixed on FSLogix 2210 HotFix 4. Customers facing this issue with Citrix Profile Manager are must upgrade to CPM 2402 or 2203 CU5.
  - "The parameter is incorrect" error can be caused by other file system drivers. Running fltmc from an elevated command window will list the drivers. Two Citrix drivers (UPMAction and upmjit) can cause the error, even if you're only using FSLogix HotFix 4 and don't have Citrix Profile Manager. This is because Citrix VDA installers typically install profilemgt_x64.msi by default for Citrix Director monitoring of logon time counters. Removing that MSI can fix "the parameter is incorrect" error.
- New Teams fails to launch for users logging into non-persistent virtual desktops, or the app is **not** visible in the Start Menu.
  - Admins don't experience this issue - after installing new Teams on the golden image they can launch it successfully.
  - After sealing the golden image and deploying it at scale (with provisioning tools like Citrix MCS/PVS or VMware Instant-Clones), users log into the virtual machines and click on the new Teams icon, but aren't able to launch the app. The issue is caused by a failed registration of the MSIX package at the user level with different profile management software (FSLogix prior to 2210 HotFix 4, Citrix CPM 2308 or 2311 **but not on 2402**, Ivanti UEM, and so on), even though the staging of the package was successful (the OS stored the package’s contents on the disk in the %ProgramFiles%\WindowsApps directory). This issue can be confirmed by running Get-AppxPackage -name MsTeams for the affected users. Running this code will return an empty output.
  - If Get-AppxPackage -name MsTeams -allusers is now run from an elevated powershell command window, the output shows that Teams is registered (see line PackageFullName) and the Status is **OK**.
  - This issue has been fixed in FSLogix 2210 HotFix 4.
- Teams meetings can't be launched when selecting a link from Outlook. There's an authentication prompt (Access to '{tenant}' tenant is denied) when users attempt to join an **external** meeting. This has been fixed on New Teams 24091.214.2846.1452.
- The PowerShell window shows after New Teams is provisioned. If the virtual machine's OS has the right KB fixes (see [Deploy the new Microsoft Teams client](#deploy-the-new-microsoft-teams-client), the second bullet in the Notes section), then Admins can delete this registry key and the Powershell window won't show anymore:

 ```powershell
 Location: "HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run"
 Name: TeamsProvisionRunKey
 ```

 The regkey was added by the teamsbootstrapper.exe version 1.0.2407104 as a workaround for environments lacking those KB fixes.

>[!Note]
>Microsoft is working on a solution and plan to remove these limitations soon.

## Enhancements in new Teams

Issues from classic Teams are now fixed in new Teams:

- Multitenant Multi-Account.
- Performance improvements in hardware resource consumptions.
- Channels 2.0.
- Multi-window is enabled by default, without prompting for a Restart.
- Sharing toolbar improvements (including pinning/unpinning).

## VDI Feature comparison between classic Teams and new Teams

All the multimedia features that work on the classic Teams client are expected to work in the new Teams client. For specific feature matrix, check your VDI Provider website.

|Provider|Details|
|:-----|:-----|
|Azure Virtual Desktops and Windows 365|[Supported features for Microsoft Teams on Azure Virtual Desktop](/azure/virtual-desktop/teams-supported-features)|
|Citrix|[Optimization for Microsoft Teams](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html)|
|VMware|[MS Teams Optimization Feature Compatibility Matrix for Horizon 7 and Horizon 8 Recent Releases. (86475) (vmware.com)](https://kb.vmware.com/s/article/86475)|

## New Teams for web in VDI

New Teams for Web isn't supported in VDI environments, so performance and reliability may be negatively impacted if used in VDI.

## Features not supported in VDI

The following features aren't supported in either classic Teams or new Teams when using the WebRTC-based optimization. Most of these limitations have been addressed with the new SlimCore-based optimization. Check out the [Feature list with the new optimization](vdi-2.md#feature-list-with-the-new-optimization) section of our VDI 2.0 article for more information.

- QoS.
- 1080p.
- Custom Backgrounds uploaded by users.
- Teams Premium features (End to End Encryption, Watermark, Premium Events aren't optimized, Custom meeting backgrounds for organizations).
- Avatars.
- Gallery View 3x3 and 7x7.
- Noise Suppression (except for Azure Virtual Desktop/W365, where noise suppression is on by default, but confirmation isn't shown in Teams client UI. This is by design).
- Zoom In / Out.
- Location Based Routing.
- Media Bypass.
- HID (Citrix only).
- Share System Audio (VMware only).
- Broadcast and live event producer and presenter roles.
- Cross cloud anonymous join in Government Clouds (GCC, GCC High and DoD).
- **Record video clip** doesn't capture screen share.
- The call monitor (the small floating window after you minimize the main Teams window) doesn't display video or screen share.
- Teams calls drop on a local machine that has an HID peripheral connected if a user launches a virtual desktop from that local machine and logs into Teams (Azure Virtual Desktop/W365 and VMware only).
