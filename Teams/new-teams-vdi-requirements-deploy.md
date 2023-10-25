---
title:  New Microsoft Teams for Virtualized Desktop Infrastructure (VDI)
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 10/13/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: smylavarapu
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about upgrading to the new Teams for Virtualized Desktop Infrastructure (VDI)
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Upgrade to new Teams for Virtualized Desktop Infrastructure (VDI)

>[!Note]
>VDI for new Teams is currently in public preview and subject to change. Check back for updates.

This article describes the requirements and limitations of using the new Microsoft Teams client in a virtualized environment. 

## Requirements

For new Teams to be successfully installed, virtual machines must meet the minimum requirements listed here: 

|Requirement |Version|
|:-----|:-----|
|Windows|- Windows 10.0.19041 or higher </br>- Windows Server 2019 (10.0.17763) coming soon </br>-Windows Server 2022 (10.0.20348) coming soon</br>- Windows Server 2016 is NOT supported. Plan upgrades.</br>- WebView2 framework required in Windows Server environment|
|Webview2|Update to the most current version. Learn more: [Enterprise management of WebView2 Runtimes](/microsoft-edge/webview2/concepts/enterprise)|
|Classic Teams app |Version 1.6.00.4472 or later to see the Try the new Teams toggle.  Important: Classic Teams is only a requirement if you want users to be able to switch between classic Teams and new Teams. This prerequisite is optional if you only want your users to see the new Teams client. |
|Settings |Turn on the "Show Notification Banners" setting in System > Notifications > Microsoft Teams to receive Teams Notifications. |
|App sideloading enabled |Ensure that sideloading is enabled on every computer you install on. Learn more: Sideload line of business (LOB) apps in Windows client devices |
|Exclude antivirus and DLP|Add new Teams to antivirus and DLP applications so Teams can start correctly.  Learn more: [Exclude antivirus and DLP applications from blocking Teams](/microsoftteams/troubleshoot/teams-administration/include-exclude-teams-from-antivirus-dlp)

## Virtualization provider requirements 

Currently, new Teams on VDI with audio/video (AV) optimization is certified with Azure Virtual Desktops, Windows 365, Citrix, and VMware.  

Review the information in this section to ensure that you meet all requirements for proper functionality. 

##  Azure Virtual Desktop 

Azure Virtual Desktop provides AV optimization for Teams on VDI. To learn more on requirements and installation, see Use Teams on Azure Virtual Desktop. 

The following minimum versions are necessary to support the new Teams client: 

- Remote Desktop Client for Windows 1.2.1755 (ideally the latest version) 
- Remote Desktop Client for Mac 10.7.7 (ideally the latest version) 
- WebRTC Redirector Service 1.1.2110.16001 (ideally the latest version) 

In addition, you must deploy the following registry key on the virtual desktop for the new Teams client to be optimized: 

HKLM\SOFTWARE\Microsoft\Teams: 
- Name: IsWVDEnvironment 
- Type: DWORD 
- Value: 1 

## Windows 365 

Windows 365 uses AV optimization provided by Azure Virtual Desktop to ensure optimal Teams experiences from Cloud PCs. To learn more on requirements and installation, see [Use Teams on Cloud PC](/windows-365/enterprise/teams-on-cloud-pc). 

The Windows 10/11 images in the gallery are preconfigured with required optimization components. When you install and use Microsoft Teams in your cloud PC, you get an optimized experience. 

If you want to create custom images that that include the optimizations for Microsoft Teams, you need you perform the steps described in [Create a custom Cloud PC image to support Microsoft Teams](/windows-365/enterprise/create-custom-image-support-teams). 

The following minimum versions are necessary to support the new Teams client: 

- Remote Desktop Client for Windows 1.2.1755 (ideally the latest version) 
- Remote Desktop Client for Mac 10.7.7 (ideally the latest version) 
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

- 1912 CU6 (and any subsequent CU) 
- 2203 LTSR (and any CU) 
- 2212 CR 

In addition, you must deploy the following registry key on the VDA for the new Teams client to be optimized: 

- Location:  HKLM\SOFTWARE\WOW6432Node\Citrix\WebSocketService 
- Key (REG_Multi_SZ): ProcessWhitelist 
- Value: msedgewebview2.exe  

If this registry key is missing, the new Teams client functions in nonoptimized mode (server-side rendering). 

>[!Note]
>Citrix Virtual Apps (also known as published apps) is currently not supported.


For additional information, learn more at [Optimization for Microsoft Teams](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html),

## VMware Horizon and Workspace ONE requirements 

The following minimum versions are necessary to support the new Teams client: 

- Horizon Agent 2103 

To learn more on the latest requirements and instructions, including how to configure media optimization for Teams, see [Configuring Media Optimization for Microsoft Teams](https://docs.vmware.com/en/VMware-Horizon/2006/horizon-remote-desktop-features/GUID-F68FA7BB-B08F-4EFF-9BB1-1F9FC71F8214.html).

 
## Deploy the new Microsoft Teams client 

To roll out the new Microsoft Teams client to your organization, you can either: 

**Option 1: Uninstall the classic Teams client and install the new one**. Recommended. 
 The direct or “bulk deployment” method is used for this option. Learn more at [**Bulk deploy the new Microsoft Teams desktop client**](new-teams-bulk-install-client.md)</br>A phased and controlled rollout can then be achieved by selectively expanding the new machine catalogue/delivery group assignments to more users. 
 
or

**Option 2: Install both apps 'side by side'**. 
Let the user switch between them by using the toggle on the top left of the Teams UI.  
You can control who sees the toggle by configuring the Teams Admin Center policy "Teams update policy".
  
If the toggle is being used for the new Teams client rollout, Admins must make sure that the VDI environments meet the minimum requirements described here: 
Troubleshooting the new Teams installation - Microsoft Teams | Microsoft Learn 

IT administrators could have set restrictions for MSIX or deploy GPOs that could prevent users from downloading and installing the app. If restrictions are in place, the user could see errors like this: 

  :::image type="content" source="media/new-teams-troubleshooting-error-isntallation-org-policies.png" alt-text="error with org policies":::

This error might be seen in non-persistent or multi-user OS deployments if the Admin didn't sideload the new Teams client on the Golden/Master Image.

## Classic Teams versus new Teams installers in VDI environments 

The classic Teams client and the new Teams client have different install locations and profile management requirements. It's important to understand the differences and plan accordingly.

|Installer format|Install location|Auto update|
|:-----|:-----|:-----|
|Classic Teams MSI with the ALLUSERS=1 flag|C:\Program Files (x86)\Microsoft\Teams|Disabled|
|Classic Teams .EXE|%localappdata%/Microsoft/Teams |Enabled |
|New Teams .EXE bootstrapper|**Teamsbootstrapper.exe** is a lightweight wrapper online installer with a headless command-line interface. It allows admins to ‘provision’ (install) the app for all users on a given target computer/. </br> It installs the Teams MSIX package on a target computer, making sure that Teams can interoperate correctly with Office and other Microsoft software.</br>C:\Program Files\WindowsApps\PublisherName.AppName_AppVersion_architecture_PublisherID</br></br>**Example**</br>C:\Program Files\WindowsApps\MSTeams.23125.600.2069.5679_x64_8wekyb3d8bbwe|Enabled (and can be disabled via regkey, coming soon)|


### Profile and Cache location for new Teams Client 

All the user settings and configurations are now stored in: 
 
- C:\Users\alland\AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams

Make sure this folder is persisted for proper Teams functioning. 


##  Features currently not available in VDI 

- All the features available in new Teams Windows client are supported on VDI except: 
- Multitenant Multi-Account (MTMA) 
- Teams Premium features (E2EE, Watermark, Premium Events aren't optimized, Custom meeting backgrounds for organizations) 
- Screen sharing from chat 
- Presenter toolbar during a screen sharing session isn't shown. 
- The self-preview in Settings / Devices isn't shown 
- “Record video clip” doesn't capture screen share 
- The call monitor (the small floating window after you minimize the main Teams window) doesn't display video or screen share 

## Enhancements in new Teams 

Issues from classic Teams are now fixed in new Teams:

- Channels 2.0 
- Multi-window is enabled by default, without prompting for a Restart.


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
- Custom Backgrounds
- Gallery View 3x3 and 7x7
- Noise Suppression
- Zoom In / Out
- Location Based Routing
- Media Bypass
- HID (Citrix only)
- Share System Audio (Citrix and VMware)
- Broadcast and live event producer and presenter roles
- Cross cloud anonymous join in Government Clouds (GCC, GCC High and DoD)
