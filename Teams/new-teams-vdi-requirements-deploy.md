---
title:  New Microsoft Teams for Virtualized Desktop Infrastructure (VDI)
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 01/30/2024
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

The **classic Teams for VDI** will reach end of availability on **June 30th, 2024**. For more information, see: [**End of availability for classic Teams client**](/MicrosoftTeams/teams-classic-client-end-of-availability)

After that date, users won't be able to use classic Teams but instead be prompted to switch to new Teams. We recommend you update to new Teams today.

>[!Note]
>New Teams for VDI is now generally available for customers in public clouds and for the GCC government cloud. Other government clouds (GCC High, DOD) are currently not supported. Check back for updates.

## Requirements

For new Teams to be successfully installed, you need version 23306.3314.2555.9628 or higher.
In addition, virtual machines must meet the minimum requirements listed here:

|Requirement |Version|
|:-----|:-----|
|Windows|- Windows 10.0.19041 or higher </br>- Windows Server 2019 (10.0.17763) in public preview </br>- Windows Server 2022 (10.0.20348) or higher</br>- Windows Server 2016 is NOT supported. Plan upgrades.</br>- WebView2 framework required in Windows Server and Windows 10/11 Multi-User environments|
|Webview2|Minimum version: 90.0.818.66. Learn more: [Enterprise management of WebView2 Runtimes](/microsoft-edge/webview2/concepts/enterprise)|
|Classic Teams app |Version 1.6.00.4472 or later to see the Try the new Teams toggle. Important: Classic Teams is only a requirement if you want users to be able to switch between classic Teams and new Teams. This prerequisite is optional if you only want your users to see the new Teams client. |
|Settings |Turn on the **Show Notification Banners** setting in System > Notifications > Microsoft Teams to receive Teams Notifications. |
|App sideloading enabled |Ensure that sideloading is enabled on every computer you install on. Learn more: Sideload line of business (LOB) apps in Windows client devices |
|Exclude antivirus and DLP|Add new Teams to antivirus and DLP applications so Teams can start correctly. </br>Learn more: [Exclude antivirus and DLP applications from blocking Teams](/microsoftteams/troubleshoot/teams-administration/include-exclude-teams-from-antivirus-dlp)|

## Virtualization provider requirements

Currently, new Teams on VDI with audio/video (AV) optimization is certified with Azure Virtual Desktops, Windows 365, Citrix, and VMware.  

Review the information in this section to ensure that you meet all requirements for proper functionality.

## Azure Virtual Desktop

Azure Virtual Desktop provides AV optimization for Teams on VDI. To learn more on requirements and installation, see [Use Teams on Azure Virtual Desktop](/azure/virtual-desktop/teams-on-avd).

The following minimum versions are necessary to support the new Teams client:

- Remote Desktop Client for Windows 1.2.1755
- Remote Desktop Client for Mac 10.7.7
- WebRTC Redirector Service 1.1.2110.16001

Microsoft recommends using the latest available versions.

In addition, you must deploy the following registry key on the virtual desktop for the new Teams client to be optimized:

HKLM\SOFTWARE\Microsoft\Teams:
- Name: IsWVDEnvironment
- Type: DWORD
- Value: 1

## Windows 365

Windows 365 uses AV optimization provided by Azure Virtual Desktop to ensure optimal Teams experiences from Cloud PCs. To learn more on requirements and installation, see [Use Teams on Cloud PC](/windows-365/enterprise/teams-on-cloud-pc).

The Windows 10/11 images in the gallery are preconfigured with required optimization components. When you install and use Microsoft Teams in your Cloud PC, you get an optimized experience. A new image with the new Teams client will be added to the gallery in a few weeks.

If you want to create custom images that include optimizations for Microsoft Teams, you need to perform the steps described in [Create a custom Cloud PC image to support Microsoft Teams](/windows-365/enterprise/create-custom-image-support-teams).

The following minimum versions are necessary to support the new Teams client:

- Remote Desktop Client for Windows 1.2.1755
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

- 1912 CU6
- 2203 LTSR (and any CU)
- 2212 CR

In addition, you must deploy the following registry key on the VDA for the new Teams client to be optimized:

- Location:  HKLM\SOFTWARE\WOW6432Node\Citrix\WebSocketService
- Key (REG_Multi_SZ): ProcessWhitelist
- Value: msedgewebview2.exe

If this registry key is missing, the new Teams client operates in nonoptimized mode (server-side rendering).

>[!Note]
>Citrix Virtual Apps (also known as published apps) is currently not supported.

For additional information, learn more at [Optimization for Microsoft Teams](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html).

## VMware Horizon and Workspace ONE requirements

The following minimum versions are necessary to support the new Teams client:

- Horizon 8 2111 ESB (8.4)

To learn more on the latest requirements and instructions, including how to configure media optimization for Teams, see [Configuring Media Optimization for Microsoft Teams](https://docs.vmware.com/en/VMware-Horizon/2006/horizon-remote-desktop-features/GUID-F68FA7BB-B08F-4EFF-9BB1-1F9FC71F8214.html).

## Deploy the new Microsoft Teams client

To deploy the new Microsoft Teams client to your organization, select one of the following options.

>[!Important]
>You must use the latest version of the bootstrapper.exe. If you have downloaded the .exe previously, verify you have the latest version by viewing **Properties > Details > Product version** on your version and compare it to the properties on the latest download.

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

If the toggle is being used for the new Teams client rollout, admins must make sure that the VDI environments meet the minimum requirements described here: [Troubleshooting installation issues in the new Teams client](new-teams-troubleshooting-installation.md).

If IT administrators set restrictions for MSIX or deploy GPOs, it could prevent users from downloading and installing the app. If restrictions are in place, the user could see errors like this:

  :::image type="content" source="media/new-teams-troubleshooting-error-isntallation-org-policies.png" alt-text="error with org policies":::

> [!IMPORTANT]
> The 'side by side' method is only supported in persistent environments.

## Classic Teams versus new Teams installers in VDI environments

The classic Teams client and the new Teams client have different install locations and profile management requirements. It's important to understand the differences and plan accordingly.

|Installer format|Install location|Auto update|
|:-----|:-----|:-----|
|Classic Teams MSI with the ALLUSERS=1 flag|C:\Program Files (x86)\Microsoft\Teams|Disabled|
|Classic Teams .EXE|%localappdata%/Microsoft/Teams |Enabled |
|New Teams .EXE bootstrapper|**Teamsbootstrapper.exe** is a lightweight wrapper online installer with a headless command-line interface. It allows admins to 'provision' (install) the app for all users on a given target computer/. </br> It installs the Teams MSIX package on a target computer, making sure that Teams can interoperate correctly with Office and other Microsoft software.</br>C:\Program Files\WindowsApps\PublisherName.AppName_AppVersion_architecture_PublisherID</br></br>**Example**</br>C:\Program Files\WindowsApps\MSTeams.23306.3314.2555.9628_x64_8wekyb3d8bbwe|Enabled.  It can be disabled via regkey. Learn more: [Disable new Teams autoupdate](#disable-new-teams-autoupdate)|

## Troubleshooting new Teams deployment errors

Administrators can rely on the teamsbootstrapper.exe [error code](/windows/win32/seccrypto/common-hresult-values) that describes the problem. If the error code doesn't provide enough information, more diagnostic information can be found in the detailed event logs.

1. Go the Event Viewer (Local) **> Applications and Services Logs > Microsoft > Windows**.
2. Check for available logs under these categories:

- AppxPackagingOM > Microsoft-Windows-AppxPackaging/Operational
- AppXDeployment-Server > Microsoft-Windows-AppXDeploymentServer/Operational

3. Review logs under **AppXDeployment-Server**

Learn more here: [Common error codes](/windows/win32/appxpkg/troubleshooting#common-error-codes)

## Installation instructions for Windows Server 2019

For Windows Server 2019, the only supported installation method is:  

```Command Line
Dism /Online /Add-ProvisionedAppxPackage /PackagePath:<MSIX package path> /SkipLicense
```

Make sure sideloading is enabled, and that WebView2 is installed. See 'Requirements' section above.

The /SkipLicense command is needed because the MSIX package isn't considered a "Store Package" (since it wasn't downloaded from the store). Therefore, for the Dism installation command to succeed, you need to enable this policy as well during installation time:
Computer Configuration > Administrative Templates > Windows Components > App Package Deployment > **Allow all trusted apps to install**.

Known limitations:

- Classic Teams on Windows Server 2019 isn't displaying the app switcher toggle if Classic Teams version is lower than 1.6.00.33567
- New Teams on Windows Server 2019 currently isn't compatible with FSLogix and fails to launch. See [FSLogix known issues](/fslogix/troubleshooting-known-issues) for more details.
- New Teams MSIX installer isn't registering UC Typelib, causing Outlook presence bubbles to show as grey/unknown even if the virtual machine does have the Classic Teams client installed as well.

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

## Profile and cache location for new Teams Client

All the user settings and configurations are now stored in:

- C:\Users\<username>\AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\
- C:\Users\<username>\AppData\Local\Publishers\8wekyb3d8bbwe\TeamsSharedConfig\app_switcher_settings.json
- C:\Users\<username>\AppData\Local\Publishers\8wekyb3d8bbwe\TeamsSharedConfig\tma_settings.json

Make sure these folders and files are persisted for proper Teams functioning.

**TeamsSharedConfig** stores user configurations for the Teams app switcher toggle (and what should be the default app, the Classic or New Teams), and the Teams Meeting Add In for Outlook.

The folder "meeting-addin" under TeamsSharedConfig shouldn't be persisted, as this could cause issues with the default meeting coordinates in the meeting templates inserted into Outlook.

>[!Important]
>Customers using FSLogix need to install hotfix [2.9.8784.63912](/fslogix/overview-release-notes#fslogix-2210-hotfix-3-29878463912) in order to guarantee proper integration with the new Teams client in VDI. The hotfix addresses the following issues:
>- In non-persistent multiuser environments, the new Teams can become unregistered for some users after a new Teams update
>- During user sign out, new Teams client user data/cache located in %LocalAppData%\Packages\MSTeams_8wekyb3d8bbwe\LocalCache **was not saved** in the FSLogix Profile or ODFC containers.
>
>*Note:* Customers using Profile and ODFC or just ODFC containers, will still need to add the setting ‘IncludeTeams’ for the new Teams user data/cache to be preserved.

>[!Note]
>[Folder Redirection or Roaming User Profiles](/windows-server/storage/folder-redirection/folder-redirection-rup-overview) aren't supported with the new Teams client in VDI environments since they can't roam folders in AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams. Customers can continue to use Folder Redirection or Roaming User Profiles with a complementary product, such as FSLogix, Citrix Profile Manager, VMware, and DEM, that can roam the Appdata\Local folders above.

### Folder exclusions

#### Disk storage usage

The new Teams app takes up about 50% less disk space than the classic version. To make it easier to distribute our client to Windows devices, we have added support for MSIX, which improves the dependability of installations and app updates, as well as reduces network bandwidth and disk space consumption. This packaging technology also shows the accurate disk space usage. Users may see larger disk usage than classic Teams in Windows settings, but the difference is mainly because the disk space related to Electron-based classic Teams is not fully and correctly shown.

#### Disk Footprint - Key folders and location

- **App installer**: C:\Program Files\WindowsApps\MSTeams_[version]_[arch]__8wekyb3d8bbwe
  Includes the installation package, supports the ability to reset the app, and allows single instancing.
- **User and app data**: C:\Users\<alias>\AppData\Local\Packages\MSTeams_8wekyb3d8bbwe
  This includes code (Javascript bundles), code cache, browser caches, databases for user data (like conversations which scales based on usage), and web storage (from domains hosted within Teams, such as Sharepoint, Viva learning, Apps, and so on).

The underlying folder structure is logically similar to Electron-based classic Teams. For non-persistent setups where storage footprint is a consideration, the following guidance applies:

##### Recommended for exclusion

|Folder             |Folder path |Role |Exclusion impact |
|-------------------|------------|---------|-----------------|
|**Logs**           |LocalCache\Microsoft\MSTeams\Logs </br>LocalCache\Microsoft\MSTeams\PerfLog |Diagnostics, perf logs, and so on. |No impact. |
|**WebStorage**     |LocalCache\Microsoft\MSTeams\EBWebView\WV2Profile_tfw\ WebStorage |Storage used and managed by the browser when accessing other web apps inside a web app using iframes. For example, loading Sharepoint, OneDrive and office apps within Teams. |Loading these apps again could be slower after clearing this cache. |
|**GPU Cache**      |LocalCache\Microsoft\MSTeams\EBWebView\WV2Profile_tfw\ GPUCache |GPU cache. |No impact. |

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
- Installation logs for TMA MSI are stored here: *AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams\Logs \tma_addin_msi.txt*

>[!Note]
>In Windows Server or Windows 10/11 Multiuser environments, installation of MicrosoftTeamsMeetingAddinInstaller.msi can fail with the error *"Installation success or error status: 1625."*.

This error is caused by GPOs affecting Windows Installer. This includes [**DisableUserInstalls**](/windows/win32/msi/disableuserinstalls), [**DisableMSI**](/windows/win32/msi/disablemsi), or AppLocker policies based on Publisher rule conditions, or a RuleCollection for MSI installs. In this case you must create an exception such as:

- FilePathCondition Path="%PROGRAMFILES%\WINDOWSAPPS\*\MICROSOFTTEAMSMEETINGADDININSTALLER.MSI"

**Workaround:**  You can install the MSI that is located in the new Teams installation directory from an Admin Command prompt using:  

```powershell

msiexec.exe /i "C:\Program Files\WindowsApps\MSTeams_X.X.X.X_x64__8wekyb3d8bbwe\MicrosoftTeamsMeetingAddinInstaller.msi" ALLUSERS=1 /qn /norestart TARGETDIR="C:\Program Files (x86)\Microsoft\TeamsMeetingAddin\<version>\"

```

- TARGETDIR must be kept consistent across installs so that the Teams Meeting Add-in MSI can easily detect and clean up older versions. If multiple directories are used, then the installation may not behave as expected.
- **X.X.X.X** needs to be replaced by the New Teams version. Make sure there's a double underscore between the CPU architecture (x64) and the PublisherID (8wekyb3d8bbwe).
- **version** must be replaced with the MSI file version, for example, 1.24.2203.0. The exact version number can be extracted by running this command in PowerShell:

```powershell

PS C:\WINDOWS\system32> Get-AppLockerFileInformation -Path "C:\PROGRAM FILES\WINDOWSAPPS\MSTEAMS_24026.1000.2656.1710_X64__8WEKYB3D8BBWE\MICROSOFTTEAMSMEETINGADDININSTALLER.MSI" | Select -ExpandProperty Publisher | select BinaryVersion

BinaryVersion

1.24.2203.0

```

**Example:**  The following is an example of the final command:

```powershell

msiexec.exe /i "C:\Program Files\WindowsApps\MSTeams_23320.3021.2567.4799_x64__8wekyb3d8bbwe\MicrosoftTeamsMeetingAddinInstaller.msi" ALLUSERS=1 /qn /norestart TARGETDIR="C:\Program Files (x86)\Microsoft\TeamsMeetingAddin\1.24.2203.0\"
```

After installation, restart Outlook and verify TMA is loading. Logs are located on %localappdata%\Temp\Microsoft\Teams\meeting-addin.

For Teams Meeting add-in troubleshooting articles, learn more at: [**Resolve issues with Teams Meeting add-in for Outlook**](/microsoftteams/troubleshoot/meetings/resolve-teams-meeting-add-in-issues).

If classic Teams is removed and only new Teams is being installed, the Teams Meeting Add-in MSI could fail to create three registry keys under HKCU that prevent the Meeting Add In from loading properly.

These keys should be then deployed via additional sign in scripts or similar methods:

:::image type="content" source="media/new-teams-vdi-meeting-addin.png" alt-text="new Teams meeting add in":::

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

The new version of Teams in VDI allows you to sign in quickly and easily, and allowing you to switch between multiple accounts and organizations from the same Microsoft 365 cloud environment.

If any of your accounts have guest access to other organizations, you don’t need to add them--they appear automatically.
A guest is someone from outside an organization that a team owner invites to join the team, such as a partner or consultant. Guests have fewer capabilities than team members or team owners.

Learn more: [Manage accounts and organizations in Microsoft Teams](https://support.microsoft.com/office/manage-accounts-and-organizations-in-microsoft-teams-7b221128-6643-465c-a317-679e48cd2ce9)

## Features currently not available in VDI with the new Teams

- Screen sharing from chat for Azure Virtual Desktops/Windows 365.
- Screen sharing from chat for Citrix.
- The app switcher toggle isn't shown in new Teams if the virtual machine has the machine-wide classic Teams installed (MSI with ALLUSERS=1). **Note:** This issue is fixed on new Teams version 23320.3021.2567.4799 or higher.

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

The following features aren't supported in either classic Teams or new Teams.

- QoS.
- 1080p.
- Custom Backgrounds uploaded by users.
- Teams Premium features (End to End Encryption, Watermark, Premium Events aren't optimized, Custom meeting backgrounds for organizations).
- Avatars.
- Gallery View 3x3 and 7x7.
- Noise Suppression.
- Zoom In / Out.
- Location Based Routing.
- Media Bypass.
- HID (Citrix only).
- Share System Audio (Citrix and VMware).
- Broadcast and live event producer and presenter roles.
- Cross cloud anonymous join in Government Clouds (GCC, GCC High and DoD).
- **Record video clip** doesn't capture screen share.
- The call monitor (the small floating window after you minimize the main Teams window) doesn't display video or screen share.
- Running new Teams simultaneously on a physical device and on a virtual desktop (connected from the same physical device).
