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


If you're optimized, you'll see MsTeamsVdi.exe running on your endpoint in process explorer for AVD/W365, and in XXX for Citrix.

If you enable the bottom pane and switch to the DLL tab, you can also see the Plugin being loaded. This is a useful troubleshooting step in case you're not getting optimized with VDI 2.0.

XXX WHAT DoeS OPTIMIZED EVEN MEAN? EVEN WITH SCREENS, WHAA


## Networking considerations

> [!NOTE]
> MsTeamsVdi.exe is the process that makes all the TCP/UDP network connections to the Teams relays/conference servers or other peers.
>
> SlimCore MSIX manifest will add the following rules to the Firewall:
> `<Rule  Direction="in" IPProtocol="TCP"  Profile="all" />`
> `<Rule Direction="in" IPProtocol="UDP" Profile="all" />`

Make sure the user’s device has network connectivity (UDP and TCP) to endpoint ID 11, 12, 47 and 127 described in [Microsoft 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams).

|ID  |Category          |ER  |Addresses    |Ports                       |Notes |
|----|------------------|----|-------------|----------------------------|------|
|11  |Optimize required |Yes |13.107.64.0/18, 52.112.0.0/14, 52.122.0.0/15, 2603:1063::/38 |UDP: 3478, 3479, 3480, 3481 |Media Processors and Transport Relay 3478 (STUN), 347 (Audio), 3480 (Video), 3481 (Screenshare) |
|12  |Allow required    |Yes |`*.lync.com`, `*.teams.microsoft.com`, `teams.microsoft.com` 13.107.64.0/18, 52.112.0.0/14, 52.122.0.0/15, 52.238.119.141/32, 52.244.160.207/32, 2603:1027::/48, 2603:1037::/48, 2603:1047::/48, 2603:1057::/48, 2603:1063::/38, 2620:1ec:6::/48, 2620:1ec:40::/42 |TCP: 443, 80                |      |
|47  |Default required  |No  |*.office.net |TCP: 443, 80                |Used for SlimCore downloads and background effects |
|127 |Default required  |No  |*.skype.com  |TCP: 443, 80                |      |


XXXX ARCHITECTURE/TOPOLOGY SCREEN THAT NEEDS TO BE WRITTEN OUT FOR ACCESSIBILITY AND SEO
There are numbers on the diagram in the word doc, so I know there's a narrative somewhere for this. We also can't use the diagram, the colors don't work.

### Types of traffic handled by SlimCore on the endpoint

1. Teams media flows connectivity is implemented using standard IETF Interactive Connectivity Establishment (ICE) for STUN and TURN procedures.
1. Real-time media. Data encapsulated within Real-time Transport Protocol (RTP) that supports audio, video, and screen sharing workloads. In general, media traffic is highly latency sensitive. This traffic must take the most direct path possible and use UDP versus TCP as the transport layer protocol, which is the best transport for interactive real-time media from a quality perspective.
  a. Note that as a last resort, media can use TCP/IP and also be tunneled within the HTTP protocol, but it isn't recommended due to bad quality implications.
  b. RTP flow is secured using SRTP, in which only the payload is encrypted.
1. Signaling. The communication link between the endpoint and Teams servers, or other clients, that's used to control activities (for example, when a call is initiated). Most signaling traffic uses the HTTPS-based REST interfaces, though in some scenarios (for example, the connection between Microsoft 365 and a Session Border Controller) it uses SIP protocol. It's important to understand that this traffic is much less sensitive to latency but may cause service outages or call timeouts if latency between the endpoints exceeds several seconds.

### Bandwidth consumption

Teams is designed to give the best audio, video, and content sharing experience regardless of your network conditions. When bandwidth is insufficient, Teams prioritizes audio quality over video quality. Where bandwidth isn't limited, Teams optimizes media quality, including high-fidelity audio, up to 1080p video resolution, and up to 30fps (frames per second) for video and content. To learn more, read [Bandwidth requirements](prepare-network.md#bandwidth-requirements)

### Quality of services (QoS)

Implement QoS settings for endpoints and network devices and determine how you want to handle media traffic for calling and meetings.

- As a prerequisite, enable QoS globally in the Teams Admin Center. See [Configure QoS in the Teams admin center](meetings-real-time-media-traffic.md) for details on enabling the **Insert Quality of Service (QoS) markers for real-time media traffic** settings.

  Recommended initial port ranges:

  |Media traffic type    |Client source port range |Protocol |DSCP value |DSCP class                |
  |----------------------|-------------------------|---------|-----------|--------------------------|
  |Audio                 |50,000 - 50,019          |TCP/UDP  |46         |Expedited Forwarding (EF) |
  |Video                 |50,020 - 50,039          |TCP/UDP  |34         |Assured Forwarding (AF41) |
  |App or screen sharing |50,040 = 50,059          |TCP/UDP  |18         |Assured Forwarding (AF41) |
- For information on configuring DSCP markings for Windows endpoints, see [Implement QoS in Teams clients](QoS-in-Teams-clients.md).
  > [!NOTE]
  > Any endpoint-based marking must be applied to MsTeamsVdi.exe, the process that handles all multimedia offloading on the user’s device.
- For information on implementing QoS for routers, see your manufacturer's documentation.
- Setting QoS on network devices might include some or all of:
  - using port-based Access Control Lists (ACLs)
  - defining the QoS queues
  - defining DSCP markings

> [!IMPORTANT]
> We recommend implementing these QoS policies using the endpoint source ports and a source and destination IP address of "any". This will catch both incoming and outgoing media traffic on the internal network.

### Technologies that aren't recommended with Microsoft Teams in VDI

1. **VPN network**. It isn't recommended for media traffic.
1. Packet shapers. Any kind of packet sniffer, packet inspection, proxies, or packet shaper devices aren't recommended for Teams media traffic and may degrade quality significantly.

|Feature                           |Available                                                       |
|----------------------------------|----------------------------------------------------------------|
|1080p                             |Yes                                                             |
|Hardware acceleration on endpoint |Yes                                                             |
|Gallery View 3x3 and 7x7          |Yes                                                             |
|Quality of Service                |Yes                                                             |
|Noise suppression                 |Yes                                                             |
|HID                               |Yes                                                             |
|Presenter mode                    |Yes                                                             |
|Teams Premium                     |Yes</br>(Pending: Watermark, Townhalls, Decorate my Background) |
|User-uploaded background effect   |Coming soon                                                     |
|Zoom +/-                          |Coming soon                                                     |

> [!NOTE]
> Check the VDI Vendor-specific versions required for any VDI 1.0 feature listed in this table.
>
> - [AVD/W365](/azure/virtual-desktop/teams-supported-features#version-requirements)
> - [Citrix](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html#feature-matrix-and-version-support)
> - [VMware](https://kb.omnissa.com/s/article/86475)

## Slimcore user profile on the endpoint

The new solution for VDI stores user-specific data on the endpoint in the following locations, depending on your vendor:

- `C:\users\<user>\AppData\Roaming\Microsoft\TeamsVDI\avd-default-<cloudname>\`
- `C:\users\<user>\AppData\Roaming\Microsoft\TeamsVDI\citrix-default-<cloudname>\`

Logs, configurations and AI/ML-models (used in noise suppression, bandwidth estimation, etc.) are saved in this location. If these folders are purged after a user logoff (for example, locked-down thin clients without roaming profiles), MsTeamsVdi.exe will recreate them and download the user-specific configuration (about 6MB of data).

### SlimCore installation and upgrade process in locked down Thin Client environments (optional)

By default, the MsTeamsPlugin will automatically download and install the right SlimCore media engine version without user or Admin intervention. But customers on restricted network environments in the branch office can opt for an alternative SlimCore distribution process, without requiring the endpoint be able to fetch slimcore packages using https from Microsoft’s public CDN.

> [!IMPORTANT]
> If you must chose this method, you must guarantee that:
>
> 1. Teams auto-update is disabled in the virtual desktop.
> 2. The SlimCore packages are pre-provisioned to the endpoint’s local storage or network share before you upgrade new Teams in the virtual desktop. Any newer Teams version will request a matching new version of SlimCore and if the plugin can't find it, the user will be in fallback mode (server-side rendering).
>
> This is because new Teams and SlimCore versions must match.

#### Configuration steps

1. On the user’s endpoint (thin client/fat client), you must create the following regkey:
  a. Location for Citrix: HKLM\SOFTWARE\WOW6432Node\Microsoft\Teams\MsTeamsPlugin
  b. Location for AVD/W365: HKLM\SOFTWARE\Microsoft\Teams\MsTeamsPlugin
  c. Name: MsixUrlBase
  d. Type: REG_SZ
  e. Data: Either local storage or network storage UNC path, such as file://C:/Temp or file://ComputerName/SharedFolder.
  The regkey will define the Base URL.
2. Additionally, admins must download the exact SlimCore MSIX Package version from Microsoft’s CDN that matches the new Teams version you are planning to deploy in the future: [https://res.cdn.office.net/ic3-1/slimcorevdi/2024.4.1.9/Microsoft.Teams.SlimCoreVdi.win-x64.msix](https://res.cdn.office.net/ic3-1/slimcorevdi/2024.4.1.9/Microsoft.Teams.SlimCoreVdi.win-x64.msix).
  
  > [!IMPORTANT]
  > The MSIX package needs to match the architecture or bitness of the Citrix Workspace app (x86 only) or Remote Desktop or Windows App clients: `Microsoft.Teams.SlimCoreVdi.<platform>-<architecture>.msix`.

3. Place the MSIX in a specific folder with the version within the location specified in the registry key, in order to preserve the structure. For example, C:\Temp\2024.4.1.9\Microsoft.Teams.SlimCoreVdi.win-x86.msix or //ComputerName/SharedFolder/2024.4.1.9/.
  
  > [!NOTE]
  > If the Plugin can't find a SlimCore MSIX package in the local or network storage, it automatically attempts to download it from the Microsoft public CDN as a fallback.

#### Known issues XXX IS THIS SUPPOSED TO BE IN THE KNOWN ISSUES DOC? IS THERE RESOLUTION

If trying to join a meeting right after launching new Teams (for example, clicking on a Teams deep link in Outlook without having new Teams running), the call might drop.

#### Citrix virtual channel allow list

The [Virtual channel allow list](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/secure/virtual-channel-security#adding-virtual-channels-to-the-allow-list) policy setting in CVAD enables the use of an allow list that specifies which virtual channels are allowed to be opened in an ICA session. When enabled, all processes except the Citrix built-in virtual channels must be stated. As a result, additional entries are required for the new Teams client to be able to connect to the client-side plugin (MsTeamsPluginCitrix.dll).

With Citrix Virtual Apps and Desktops 2203 or later, the Virtual channel allow list is **enabled by default**. These default settings will deny access to the new Teams custom virtual channels as the allow list **doesn't** include the new Teams main process name.

The new Teams client requires three custom virtual channels to function: MSTEAMS, MSTEAM1 and MSTEAM2. These are accessed by ms-teams.exe. You can use wildcards to whitelist the ms-teams.exe executable and custom virtual channel:

- MSTEAMS,C:\Program Files\WindowsApps\MSTeams*8wekyb3d8bbwe\ms-teams.exe
- MSTEAM1,C:\Program Files\WindowsApps\MSTeams*8wekyb3d8bbwe\ms-teams.exe
- MSTEAM2,C:\Program Files\WindowsApps\MSTeams*8wekyb3d8bbwe\ms-teams.exe

1. Wildcard support is available in:
  a. VDA 2206 CR
  b. VDA 2203 LTSR from CU2 onwards
2. The VDA machines must be rebooted for the policy to take effect

#### Citrix App Protection and Microsoft Teams compatibility

Users who have App Protection enabled can still share their screen and apps while optimized with VDI 2.0. This requires VDA version 2402 or higher, and CWA for Windows 2309.1 or higher. Users on versions lower than those will end up sharing a black screen instead when the App Protection module is installed and enabled.

#### Troubleshooting
