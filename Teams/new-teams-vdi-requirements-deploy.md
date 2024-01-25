---
title:  New Microsoft Teams for Virtualized Desktop Infrastructure (VDI)
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 01/22/2024
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


### Important announcement for classic Teams for VDI

The **classic Teams for VDI** will reach end of availability on **June 30th, 2024**. For more details, see: [**End of availability for classic Teams client**](/MicrosoftTeams/teams-classic-client-end-of-availability)

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
|Classic Teams app |Version 1.6.00.4472 or later to see the Try the new Teams toggle.  Important: Classic Teams is only a requirement if you want users to be able to switch between classic Teams and new Teams. This prerequisite is optional if you only want your users to see the new Teams client. |
|Settings |Turn on the "Show Notification Banners" setting in System > Notifications > Microsoft Teams to receive Teams Notifications. |
|App sideloading enabled |Ensure that sideloading is enabled on every computer you install on. Learn more: Sideload line of business (LOB) apps in Windows client devices |
|Exclude antivirus and DLP|Add new Teams to antivirus and DLP applications so Teams can start correctly. </br>Learn more: [Exclude antivirus and DLP applications from blocking Teams](/microsoftteams/troubleshoot/teams-administration/include-exclude-teams-from-antivirus-dlp)

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

The Windows 10/11 images in the gallery are preconfigured with required optimization components. When you install and use Microsoft Teams in your cloud PC, you get an optimized experience. A new image with the new Teams client will be added to the gallery in a few weeks.

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


For additional information, learn more at [Optimization for Microsoft Teams](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html),

## VMware Horizon and Workspace ONE requirements 

The following minimum versions are necessary to support the new Teams client: 

- Horizon 8 2111 ESB (8.4)
    

To learn more on the latest requirements and instructions, including how to configure media optimization for Teams, see [Configuring Media Optimization for Microsoft Teams](https://docs.vmware.com/en/VMware-Horizon/2006/horizon-remote-desktop-features/GUID-F68FA7BB-B08F-4EFF-9BB1-1F9FC71F8214.html).

 
## Deploy the new Microsoft Teams client 

To deploy the new Microsoft Teams client to your organization, select one of the following options.

>[!Important]
>You must use the latest version of the bootstrapper.exe. If you have downloaded the .exe previously, verify you have the latest version by viewing **Properties > Details > Product version** on your version and compare it to the properties on the latest download.

#### Option 1: Uninstall the classic Teams client and install the new one

**Recommended way to deploy new Teams in VDI.** The direct or “bulk deployment” method is used for this option. Learn more at [**Bulk deploy the new Microsoft Teams desktop client**](new-teams-bulk-install-client.md).

Using the teamsbootstrapper.exe -p command always guarantees the latest new Teams client is installed.

A phased and controlled rollout can then be achieved by selectively expanding the new computer catalogue/delivery group assignments to more users.

Admins can also use a local teams MSIX to provision new Teams. This option minimizes the amount of bandwidth used for the initial installation. The MSIX can exist in a local path or UNC.

1. [Download the .exe installer.](https://go.microsoft.com/fwlink/?linkid=2243204&clcid=0x409)
2. Download the MSIX:</br>- [MSIX x86](https://go.microsoft.com/fwlink/?linkid=2196060&clcid=0x409)</br>- [MSIX x64](https://go.microsoft.com/fwlink/?linkid=2196106)</br>- [ARM64](https://go.microsoft.com/fwlink/?linkid=2196207&clcid=0x409)
3. Open the Command Prompt as an Admin.
4. Depending on where your MSIX is located, do the following steps:
</br>

 **For local path, enter:** *.\teamsbootstrapper.exe -p -o "c:\path\to\teams.msix"*

   *Example:*

   :::image type="content" source="media/new-teams-bulk-offline-localpath.png" alt-text="local path location for offline installer"::: 
 
   **For UNC, enter:** *.\teamsbootstrapper.exe -p -o "\\unc\path\to\teams.msix"*

   *Example:*

   :::image type="content" source="media/new-teams-bulk-offline-unc.png" alt-text="offline location using unc":::


#### Option 2: Install both apps 'side by side' 
Let the user switch between them by using the toggle on the top left of the Teams UI.  
You can control who sees the toggle by configuring the Teams Admin Center policy "Teams update policy".
  
If the toggle is being used for the new Teams client rollout, admins must make sure that the VDI environments meet the minimum requirements described here: 
Troubleshooting the new Teams installation - Microsoft Teams | Microsoft Learn 

If IT administrators set restrictions for MSIX or deploy GPOs, it could prevent users from downloading and installing the app. If restrictions are in place, the user could see errors like this: 

  :::image type="content" source="media/new-teams-troubleshooting-error-isntallation-org-policies.png" alt-text="error with org policies":::

This error might be seen in non-persistent or multi-user OS deployments if the admin didn't sideload the new Teams client on the golden/master Image.


 ## Classic Teams versus new Teams installers in VDI environments 

The classic Teams client and the new Teams client have different install locations and profile management requirements. It's important to understand the differences and plan accordingly.

|Installer format|Install location|Auto update|
|:-----|:-----|:-----|
|Classic Teams MSI with the ALLUSERS=1 flag|C:\Program Files (x86)\Microsoft\Teams|Disabled|
|Classic Teams .EXE|%localappdata%/Microsoft/Teams |Enabled |
|New Teams .EXE bootstrapper|**Teamsbootstrapper.exe** is a lightweight wrapper online installer with a headless command-line interface. It allows admins to ‘provision’ (install) the app for all users on a given target computer/. </br> It installs the Teams MSIX package on a target computer, making sure that Teams can interoperate correctly with Office and other Microsoft software.</br>C:\Program Files\WindowsApps\PublisherName.AppName_AppVersion_architecture_PublisherID</br></br>**Example**</br>C:\Program Files\WindowsApps\MSTeams.23306.3314.2555.9628_x64_8wekyb3d8bbwe|Enabled.  It can be disabled via regkey. Learn more: [Disable new Teams autoupdate](#disable-new-teams-autoupdate)|


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

Known limitations:
- Classic Teams on Windows Server 2019 isn't displaying the app switcher toggle if Classic Teams version is lower than 1.6.00.33567
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

- C:\Users\<username>\AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams
- C:\Users\<username>\AppData\Local\Publishers\8wekyb3d8bbwe\TeamsSharedConfig\app_switcher_settings.json
- C:\Users\<username>\AppData\Local\Publishers\8wekyb3d8bbwe\TeamsSharedConfig\tma_settings.json

Make sure these folders and files are persisted for proper Teams functioning.

**TeamsSharedConfig** stores user configurations for the Teams app switcher toggle (and what should be the default app, the Classic or New Teams), and the Teams Meeting Add In for Outlook.

The folder "meeting-addin" under TeamsSharedConfig shouldn't be persisted, as this could cause issues with the default meeting coordinates in the meeting templates inserted into Outlook.

Excluding these items helps reduce the user caching size to further optimize a non-persistent setup:
 
- AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams\Logs
- AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams\PerfLogs
- AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams\EBWebView\WV2Profile_tfw\WebStorage

When you exclude the WebStorage folder (used for domains hosted within Teams like SharePoint, Viva Learning, etc.), you can significantly reduce storage. It can also have an impact on performance as users would lose caching benefits.

 
>[!Important]
>Customers using FSLogix need to install hotfix [2.9.8716.30241](/fslogix/overview-release-notes#fslogix-2210-hotfix-3-preview-29871630241) in order to guarantee proper integration with the new Teams client in VDI. The hotfix addressess the following issues:
>- In non-persistent multiuser environments, the new Teams can become unregistered for some users after a new Teams update
>- During user sign out, new Teams client user data/cache located in %LocalAppData%\Packages\MSTeams_8wekyb3d8bbwe\LocalCache **was not saved** in the FSLogix Profile or ODFC containers
>
>*Note:* Customers using Profile and ODFC or just ODFC containers, will still need to add the setting ‘IncludeTeams’ for the new Teams user data/cache to be preserved.

## New Teams and Outlook integration
 
When the "Register the new Teams as the chat app for Microsoft 365" checkbox is selected under Settings > General > System, this lets the new Teams client integrate with all the Microsoft 365 apps that have instant message capabilities (presence, chat, VOIP, etc.).

For example, Outlook goes through the discovery process outlined here to integrate with the default IM client application:  [Integrating IM applications with Office](/office/client-developer/shared/integrating-im-applications-with-office#discovering-the-im-application)
 
>[!Note]
>If the new Teams is installed on a virtual machine where the classic Teams is **not** installed, you must make sure you are using new Teams version 23320.3021.2567.4799 or higher in order to guarantee proper integration with Outlook and presence.

Additionally, the new Teams MSIX package bundles the Teams Meeting add-in MSI ("MicrosoftTeamsMeetingAddinInstaller.msi"). 

Installation logs for this MSI are stored here:
- AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams\Logs \tma_addin_msi.txt

>[!Note]
>In Windows Server or Windows 10/11 Multiuser environments, installation of MicrosoftTeamsMeetingAddinInstaller.msi can fail with the error "Installation success or error status: 1625". Microsoft is working on a solution for this issue.

 
### Troubleshooting new Teams and Outlook integration

#### Symptoms:

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
- On Fallback, screen sharing functionality is supported with a different screen picker UI (similar to the experience a user would see on Teams for Web)

## Multitenant and Multi-account in VDI

The new version of Teams in VDI allows you to sign in quickly and easily, and allowing you to switch between multiple accounts and organizations from the same Microsoft 365 cloud environment. 

If any of your accounts have guest access to other organizations, you don’t need to add them--they appear automatically.
A guest is someone from outside an organization that a team owner invites to join the team, such as a partner or consultant. Guests have fewer capabilities than team members or team owners.

Learn more: [Manage accounts and organizations in Microsoft Teams](https://support.microsoft.com/en-us/office/manage-accounts-and-organizations-in-microsoft-teams-7b221128-6643-465c-a317-679e48cd2ce9) 

### Cross Cloud Meetings

Users trying to join meetings between your organization and an organization in a different Microsoft 365 cloud environment (such as commercial/GCC and GCCH or DOD) must use the “Continue on this browser” option when prompted by the Join launcher:

:::image type="content" source="media/new-teams-vdi-mtma.png" alt-text="new teams for vdi using mtma"::: 


You can’t use the native Teams app to join meetings. Clicking “Join on the Teams app” will only bring new Teams chat UI to the foreground without switching to the lobby.


## Features currently not available in VDI with the new Teams

- Screen sharing from chat for Azure Virtual Desktops/Windows 365. **Note:** Note: This issue is fixed on new WebRTC Redirector Service 2.0.2311.15001 and RD Client 1.2.5105.
- Give/Take control for Citrix and AVD/Windows 365
- HID support in headsets
- The app switcher toggle isn't shown in new Teams if the virtual machine has the machine-wide classic Teams installed (MSI with ALLUSERS=1). **Note:** This issue is fixed on new Teams version 23320.3021.2567.4799 or higher.
  
>[!Note]
>Microsoft is working on a solution and plan to remove these limitations soon.

## Enhancements in new Teams 

Issues from classic Teams are now fixed in new Teams:

- Multitenant Multi-Account
- Performance improvements in hardware resource consumptions
- Channels 2.0 
- Multi-window is enabled by default, without prompting for a Restart.
- Sharing toolbar improvements (including pinning/unpinning).

## VDI Feature comparison between classic Teams and new Teams

All the multimedia features that work on the classic Teams client are expected to work in the new Teams client. For specific feature matrix, check your VDI Provider website.
 
|Provider|Details|
|:-----|:-----|
|Azure Virtual Desktops and Windows 365|[Supported features for Microsoft Teams on Azure Virtual Desktop](/azure/virtual-desktop/teams-supported-features)|
|Citrix|[Optimization for Microsoft Teams](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html)|
|VMware|[MS Teams Optimization Feature Compatibility Matrix for Horizon 7 and Horizon 8 Recent Releases. (86475) (vmware.com)](https://kb.vmware.com/s/article/86475)|

## Features not supported in VDI 

The following features aren't supported in either classic Teams or new Teams.

- QoS
- 1080p
- Custom Backgrounds uploaded by users
- Teams Premium features (End to End Encryption, Watermark, Premium Events aren't optimized, Custom meeting backgrounds for organizations) 
- Avatars
- Gallery View 3x3 and 7x7
- Noise Suppression
- Zoom In / Out
- Location Based Routing
- Media Bypass
- HID (Citrix only)
- Share System Audio (Citrix and VMware)
- Broadcast and live event producer and presenter roles
- Cross cloud anonymous join in Government Clouds (GCC, GCC High and DoD)
- “Record video clip” doesn't capture screen share 
- The call monitor (the small floating window after you minimize the main Teams window) doesn't display video or screen share 

