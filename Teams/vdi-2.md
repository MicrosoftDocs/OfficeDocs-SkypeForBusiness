---
title:  New VDI solution for Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 07/09/2024
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

# New VDI solution for Teams

New VDI solution for Teams is a new architecture for optimizing the delivery of multimedia workloads in virtual desktops.

> [!IMPORTANT]
> The rollout to General Availability started on August 27th 2024, and will reach 100% coverage in the next few days for Azure Virtual Desktops and Windows 365. 
>
> For Citrix customers, in order to participate on the public preview, administrators must move users to the public preview channel as described [in this article](public-preview-doc-updates.md).

## Components

|Component |Role |Update |Size |Notes |
|----------|-----|-------|-----|------|
|New Teams **vdiBridge**     |Server-side virtual channel module. |New version with every new Teams version. |Bundled with new Teams. | |
|Custom virtual channel (VC) |Custom VC owned by Microsoft Teams. |Stable API - no updates foreseen. | |Check the Citrix Studio policy **Virtual channel allow list**. |
|Plugin                      |Client-side VC dll. Responsible also for SlimCore download and clean-up. |Not frequent (ideally no updates). |Approximately 200 KB. |Bundled with [RD Client 1.2.5405.0](/azure/virtual-desktop/whats-new-client-windows) or Windows App 1.3.252 or higher. Citrix CWA 2402 or higher can fetch and install the plugin. |
|SlimCore                    |Media engine (operating system specific, not VDI vendor specific). |Auto-updated to a new version with each new Teams version. |Approximately 50 MB. |MSIX package hosted on Microsoft's public CDN|

## System requirements

|Requirement                       |Minimum version |
|----------------------------------|----------------|
|New Teams                         |24193.1805.3040.8975 (for Azure Virtual Desktop/Windows 365) </br>24165.1410.2974.6689 (for Citrix)                                                                                     |
|Azure Virtual Desktop/Windows 365 |Windows App: 1.3.252</br>Remote Desktop Client: 1.2.5405.0                                                |
|Citrix                            |VDA: 2203 LTSR CU3 or 2305 CR</br>Citrix Workspace app: 2203 LTSR (any CU), 2402 LTSR, or 2302 CR          |
|Endpoint                          |Windows 10 1809 (SlimCore minimum requirement)</br>GPOs must not block MSIX installations (see [Step 3: SlimCore MSIX staging and registration on the endpoint](#step-3-slimcore-msix-staging-and-registration-on-the-endpoint))</br>Minimum CPU: Intel Celeron (or equivalent) @ 1.10 GHz, 4 Cores, Minimum RAM: 4 GB |

## Optimizing with new VDI solution for Teams

### Step 1: Confirm prerequisites

1. Make sure you have the new Microsoft Teams version 24193.1805.3040.8975 or higher (for Azure Virtual Desktop/Windows 365), and 24165.1410.2974.6689 or higher for Citrix.
1. [Enable the new Teams policy](#microsoft-teams-powershell-policy-for-optimization) **if necessary** for a specific user group (it's enabled by default at a Global org-wide level).
1. For Citrix, you must configure the **Virtual channel allow list** as described in the [Citrix Virtual channel allow list](#citrix-virtual-channel-allow-list) section of this article.

### Step 2: Plugin installation on the endpoint

1. For Azure Virtual Desktop and Windows 365, MsTeamsPluginAvd.dll is bundled with the RD Client for Windows 1.2.5405.0, or with the Windows App Store app 1.3.252 or higher.
  - The plugin is found in the same folder location where the RD Client is installed. It's either located at AppData\Local\Apps\Remote Desktop or C:\Program Files (x86), depending on the mode in which it was installed.
  - The [Windows App Store](/windows-app/overview) app, since it's MSIX-based, is found in C:\Program Files\WindowsApps. Access to this folder is restricted.
1. For Citrix CWA 2402 or higher, MsTeamsPluginCitrix.dll can be installed either:
  - Using the user interface when installing CWA:
     On the **Add-on(s)** page, select the **Install Microsoft Teams VDI plug-in** checkbox, and then select **Install**.
     Agree to the user agreement that pops up and proceed with the installation of the Citrix Workspace app.

> [!NOTE]
> Citrix Workspace app 2402 only presents the plugin installation UI on a fresh install.
> For in-place upgrades to also present this option, Citrix Workspace app 2405 or higher is required.

  - Via command line or scripts for managed devices using:
    `C:\>CitrixWorkspaceApp.exe installMSTeamsPlugin`
  - Admins can also install the plugin manually on top of any existing supported CWA (see [System Requirements](#system-requirements)) using tools like SCCM (use the Windows app package deployment type) or Intune (use the Line-of-Business app).
  Admins can use **msiexec** with appropriate flags, as discussed in [this documentation](/windows-server/administration/windows-commands/msiexec).

> [!IMPORTANT]
> You can find the plugin MSI download link for Citrix customers [here](https://download.microsoft.com/download/3/0/e/30e54a38-eb74-44dc-9755-36dcac09656d/MsTeamsPluginCitrix.msi).

The plugin MSI automatically detects the CWA installation folder and places MsTeamsPluginCitrix.dll in that location:

|User type     |Installation folder                                                                             |Installation type |
|--------------|------------------------------------------------------------------------------------------------|------------------|
|Administrator |64-bit: C:\Program Files (x86)\Citrix\ICA Client</br>32-bit: C:\Program Files\Citrix\ICA Client |Per-system installation |

- Plugins can't be downgraded, only upgraded or reinstalled (repaired).
- Per-user installation of CWA isn't supported.
- If no CWA is found on the endpoint, installation is stopped.

### Step 3: SlimCore MSIX staging and registration on the endpoint

The plugin silently executes this step, without user or admin intervention. The staging and registration relies on the App Readiness Service (ARS) on the endpoint. It's possible that the MSIX package installation is blocked by registry keys set by a Group Policy or a third-party tool. For a complete list of applicable registry keys, see [How Group Policy works with packaged apps - MSIX](/windows/msix/group-policy-msix).

The following registry keys could block new media engine MSIX package installation:

- [BlockNonAdminUserInstall](/windows/client-management/mdm/policy-csp-applicationmanagement#blocknonadminuserinstall)
- [AllowAllTrustedApps](/windows/client-management/mdm/policy-csp-applicationmanagement#allowalltrustedapps)
- AllowDevelopmentWithoutDevLicense

> [!IMPORTANT]
> If AllowAllTrustedApps is disabled, the new media engine (MSIX) installation fails. This issue has been fixed in the Windows October cumulative update KB5031455:
>
> - [Windows 10: October 26, 2023—KB5031445 (OS Build 19045.3636)](https://support.microsoft.com/topic/october-26-2023-kb5031445-os-build-19045-3636-preview-03f350cb-57f9-45e6-bfd7-438895d3c7fa)
> - [Windows 11: October 26, 2023—KB5031455 (OS Build 22621.2506)](https://support.microsoft.com/topic/october-26-2023-kb5031455-os-build-22621-2506-preview-6513c5ec-c5a2-4aaf-97f5-44c13d29e0d4)
>
> If this optional October update isn't available for your OS build, the November security update also includes the fix.

These three registry keys can be found at either of the following locations on the user's device:

- HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\AppModelUnlock
- HKLM\SOFTWARE\Policies\Microsoft\Windows\Appx

Some policies might change these registry keys and block app installation in your organization because the admins set a restrictive policy. Some of the known GPO policies that could prevent installation include:

- Prevent nonadmin users from installing packaged Windows apps.
- Allow all trusted apps to install (disabled).

> [!NOTE]
> [AppLocker](/windows/security/application-security/application-control/windows-defender-application-control/applocker/applocker-overview) or [Windows Defender Application Control](/windows/security/application-security/application-control/windows-defender-application-control/wdac-and-applocker-overview) can also prevent MSIX package installation.
>
> AppLocker is a defense-in-depth security feature and not considered a defensible [Windows security feature](https://www.microsoft.com/msrc/windows-security-servicing-criteria). [Windows Defender Application Control](/windows/security/threat-protection/windows-defender-application-control/wdac-and-applocker-overview) should be used when the goal is to provide robust protection against a threat and there are expected to be no by-design limitations that would prevent the security feature from achieving this goal.

> [!IMPORTANT]
> Make sure there's no blocking configuration or policy, or add an exception for SlimCore MSIX packages in Local Security Policy -> Application Control Policies -> AppLocker.
>
> AppLocker can't process trailing wildcards, unlike Windows Defender Application Control. Since SlimCoreVdi Packages contain a version-specific PackageFamilyName (for example, Microsoft.Teams.SlimCoreVdi.win-x64.2024.36_8wekyb3d8bbwe), customers can add AppX or MSIX exclusions by relying on the PublisherID 8wekyb3d8bbwe instead.

## Verifying that the end point is optimized

Once you meet all the minimum requirements, launching new Teams for the first time will still be in WebRTC optimized mode by default.

> [!IMPORTANT]
> For first run experiences, two app restarts are required to get the new optimization.

You can check in the Teams client that you optimized with the new architecture by going to the ellipsis (three dots ...) on the top bar, then selecting Settings > About. The Teams and client versions are listed there.

- AVD SlimCore Media Optimized = New optimization based on SlimCore.
- AVD Media Optimized = Legacy optimization based on WebRTC.

The plugin (MsTeamsPluginAvd.dll or MsTeamsPluginCitrix.dll) is responsible for eventually downloading the media engine, and SlimCore, which is an MSIX package. It installs silently without admin privileges or reboots in (example, exact path varies):

`C:\Program Files\WindowsApps\Microsoft.Teams.SlimCoreVdi.win-x64.2024.15_2024.15.1.5_x64__8wekyb3d8bbwe`

The remote desktop client downloads the x64 or x86 SlimCore package, and the Citrix CWA downloads an x86 package. This folder is locked down, so users don't have access to it. Admins can take ownership by modifying ACLs, though this action isn't recommended. Instead, use PowerShell to list the MSIX apps in the endpoint:

```powershell
PowerShellCopy

Get-AppxPackage Microsoft.Teams.SlimCore*
```

A sample of the results that can be returned from running this Powershell is:

```powershell
Name              : Microsoft.Teams.SlimCoreVdi.win-x64.2024.32
Publisher         : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Architecture      : X64
ResourceId        :
Version           : 2024.32.1.7
PackageFullName   : Microsoft.Teams.SlimCoreVdi.win-x64.2024.32_2024.32.1.7_x64__8wekyb3d8bbwe
InstallLocation   : C:\Program
                    Files\WindowsApps\Microsoft.Teams.SlimCoreVdi.win-x64.2024.32_2024.32.1.7_x64__8wekyb3d8bbwe
IsFramework       : False
PackageFamilyName : Microsoft.Teams.SlimCoreVdi.win-x64.2024.32_8wekyb3d8bbwe
PublisherId       : 8wekyb3d8bbwe
IsResourcePackage : False
IsBundle          : False
IsDevelopmentMode : False
NonRemovable      : False
IsPartiallyStaged : False
SignatureKind     : Developer
Status            : Ok
```

> [!IMPORTANT]
> Microsoft stores up to 12 versions of SlimCoreVdi for compatibility purposes, and in case the user accesses different VDI environments (such as persistent, where new Teams auto-updates itself, and non-persistent, where new Teams auto-updates are disabled).

If you're optimized, you can see MsTeamsVdi.exe running on your endpoint for Azure Virtual Desktop/W365 (as a child process of msrdc.exe) or Citrix (as a child process of wfica32.exe). When using Process Explorer, If you select msrdc.exe (or wfica32.exe), select **Show the lower pane** under **View** and switch to the DLL tab, you can also see the Plugin (MsTeamsPluginAvd.dll or MsTeamsPluginCitrix.dll) being loaded. This action is a useful troubleshooting step in case you're not getting the new optimization.

If you enable the bottom pane and switch to the DLL tab, you can also see the Plugin being loaded. This action is a useful troubleshooting step in case you're not getting the new optimization.

## Session roaming and reconnections

New Teams loads WebRTC or SlimCore at launch time. If virtual desktop sessions are disconnected (not logged off, Teams is left running on the VM), new Teams can't switch optimization stacks unless it's restarted. As a result, users might be in fallback mode (not optimized) if they roam between different devices that don't support the new optimization architecture (for example, a MAC device that is used in BYOD while working from home, and a corporate-managed thin client in the office).

|Reconnecting options                                        |If current optimization is WebRTC |If current optimization is SlimCore  |
|------------------------------------------------------------|----------------------------------|-------------------------------------|
|Reconnecting from an endpoint **without** the MsTeamsPlugin |Then WebRTC classic optimization  |Then fallback (local SlimCore)       |
|Reconnecting from an endpoint **with** the MsTeamsPlugin    |THen WebRTC classic optimization  |Then new SlimCore-based optimization |

## Networking considerations

> [!NOTE]
> MsTeamsVdi.exe is the process that makes all the TCP/UDP network connections to the Teams relays/conference servers or other peers.
>
> SlimCore MSIX manifest will add the following rules to the Firewall:
> `<Rule  Direction="in" IPProtocol="TCP"  Profile="all" />`
> `<Rule Direction="in" IPProtocol="UDP" Profile="all" />`

Make sure the user's device has network connectivity (UDP and TCP) to endpoint ID 11, 12, 47 and 127 described in [Microsoft 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams).

|ID  |Category          |ER  |Addresses    |Ports                       |Notes |
|----|------------------|----|-------------|----------------------------|------|
|11  |Optimize required |Yes |13.107.64.0/18, 52.112.0.0/14, 52.122.0.0/15, 2603:1063::/38 |UDP: 3478, 3479, 3480, 3481 |Media Processors and Transport Relay 3478 (STUN), 3479 (Audio), 3480 (Video), 3481 (Screenshare) |
|12  |Allow required    |Yes |`*.lync.com`, `*.teams.microsoft.com`, `teams.microsoft.com` 13.107.64.0/18, 52.112.0.0/14, 52.122.0.0/15, 52.238.119.141/32, 52.244.160.207/32, 2603:1027::/48, 2603:1037::/48, 2603:1047::/48, 2603:1057::/48, 2603:1063::/38, 2620:1ec:6::/48, 2620:1ec:40::/42 |TCP: 443, 80                |      |
|47  |Default required  |No  |*.office.net |TCP: 443, 80                |Used for SlimCore downloads and background effects |
|127 |Default required  |No  |*.skype.com  |TCP: 443, 80                |      |

### Network architecture

:::image type="content" source="media/teams-vdi-2-network-architecture.png" alt-text="The network architecture of Teams VDI 2.":::

A walkthrough of the architecture in the diagram:

1. Start new Teams.​
2. Teams client authenticates to Teams services. Tenant policies are pushed down to the Teams client, and relevant configurations are relayed to the app.​
3. Teams detects that it's running in a virtual desktop environment and instantiates the internal vdibridge service​.
4. Teams opens a secure virtual channel on the server​.
5. The RDP or HDX protocol carries the request to the RD Client or Citrix Workspace app that previously loaded MsTeamsPlugin (client-side virtual channel component)​.
6. The RD Client or Citrix Workspace app spawns a new process called MsTeamsVdi.exe, which is the new media engine (SlimCore) used for the new optimization​.
7. SlimCore media engine (on the client) and msteams.exe (on the virtual desktop) now have a bidirectional channel and can start processing multimedia requests.​

User calls

8. Peer A selects the call button. MsTeamsVdi.exe communicates with the Microsoft Teams services in Azure, establishing an end-to-end signaling path with Peer B. MsTeamsVdi.exe collects a series of supported call parameters (codecs, resolutions, and so forth, which is known as a Session Description Protocol (SDP) offer). These call parameters are then relayed using the signaling path to the Microsoft Teams services in Azure and from there to the other peer.​
9. The SDP offer/answer (single-pass negotiation) takes place through the signaling channel, and the ICE connectivity checks (NAT and Firewall traversal using STUN bind requests) complete. Then, Secure Real-time Transport Protocol (SRTP) media flows directly between MsTeamsVdi.exe and the other peer (or Teams Transport Relays or Conference servers).

IP blocks for signaling, media, background effects, and other options are described in [this article](/microsoft-365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams).

### Types of traffic handled by SlimCore on the endpoint

1. Teams media flows connectivity is implemented using standard IETF Interactive Connectivity Establishment (ICE) for STUN and TURN procedures.
1. Real-time media. Data encapsulated within Real-time Transport Protocol (RTP) that supports audio, video, and screen sharing workloads. In general, media traffic is highly latency sensitive. This traffic must take the most direct path possible and use UDP versus TCP as the transport layer protocol, which is the best transport for interactive real-time media from a quality perspective.
  - As a last resort, media can use TCP/IP and also be tunneled within the HTTP protocol, but it's not recommended due to bad quality implications.
  - RTP flow is secured using SRTP, in which only the payload is encrypted.
1. Signaling. The communication link between the endpoint and Teams servers, or other clients, used to control activities (for example, when a call is initiated). Most signaling traffic uses UDP 3478 with fallback to HTTPS, though in some scenarios (for example, the connection between Microsoft 365 and a Session Border Controller) it uses SIP protocol. It's important to understand that this traffic is much less sensitive to latency but may cause service outages or call timeouts if latency between the endpoints exceeds several seconds.

### Bandwidth consumption

Teams is designed to give the best audio, video, and content sharing experience regardless of your network conditions. When bandwidth is insufficient, Teams prioritizes audio quality over video quality. Where bandwidth isn't limited, Teams optimizes media quality, including high-fidelity audio, up to 1080p video resolution, and up to 30 fps (frames per second) for video and content. To learn more, read [Bandwidth requirements](prepare-network.md#bandwidth-requirements)

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
  > Any endpoint-based marking must be applied to MsTeamsVdi.exe, the process that handles all multimedia offloading on the user's device. Refer to the [Playbook document](https://aka.ms/teams-vdi-2.0-playbook) for more info on QoS.
- For information on implementing QoS for routers, see your manufacturer's documentation.
- Setting QoS on network devices might include some or all of:
  - using port-based Access Control Lists (ACLs)
  - defining the QoS queues
  - defining DSCP markings

> [!IMPORTANT]
> We recommend implementing these QoS policies using the endpoint source ports and a source and destination IP address of "any". This will catch both incoming and outgoing media traffic on the internal network.

### Technologies that aren't recommended with Microsoft Teams in VDI

1. **VPN network**. It's not recommended for media traffic.
1. Packet shapers. Any kind of packet sniffer, packet inspection, proxies, or packet shaper devices aren't recommended for Teams media traffic and may degrade quality significantly.

### Microsoft Teams PowerShell policy for optimization

The CsTeamsVdiPolicy cmdlets enabled administrators to control the type of meetings that users can create or the features that they can access while in a meeting specifically on an VDI environment, where WebRTC optimization was disabled using the VDI Partner's policy engine ([Citrix Studio](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html#enable-optimization-of-microsoft-teams), [VMware HTML5 ADMX template](https://docs.vmware.com/en/VMware-Horizon/2203/horizon-remote-desktop-features/GUID-8557C3D7-4B08-4C98-B474-97B795300A6E.html#GUID-8557C3D7-4B08-4C98-B474-97B795300A6E), or [this registry key](/azure/virtual-desktop/teams-on-avd) for AVD and Windows 365).

The default policy configurations are:

- DisableCallsAndMeetings: False
- DisableAudioVideoInCallsAndMeetings: False

This policy is now expanded with an additional argument as the only configuration point to control whether a user can get the new optimization mode that's based on SlimCore or not (in other words, the VDI Partner's policy engines don't control the new optimization mode):

- VDI2Optimization: Enabled  (default value)

|Name                    |Definition |Example |Notes |
|------------------------|-----------|--------|------|
|New-CsTeamsVdiPolicy    |Allows administrators to define new VDI policies that can be assigned to users for controlling Teams features related to meetings on a VDI environment. |`PS C:\> New-CsTeamsVdiPolicy -Identity RestrictedUserPolicy -VDI2Optimization "Disabled"` |The command shown here uses the New-CsTeamsVdiPolicy cmdlet to create a new VDI policy with the identity RestrictedUserPolicy. This policy uses all the default values for a VDI policy except one: VDI2Optimization. In this example, users with this policy can't be optimized with SlimCore. |
|Grant-CsTeamsVdiPolicy  |Allows administrators to assign a Teams VDI policy at a per-user scope to control the type of meetings that a user can create, the features they can access on an unoptimized VDI environment, and whether a user can be optimized with the new optimization mode that's based on SlimCore. |`PS C:\> Grant-CsTeamsVdiPolicy -identity "Ken Myer" -PolicyName RestrictedUserPolicy` |In this example, a user with identity "Ken Myer" is assigned the RestrictedUserPolicy. |
|Set-CsTeamsVdiPolicy    |Allows administrators to update existing VDI policies. |`PS C:\> Set-CsTeamsVdiPolicy -Identity RestrictedUserPolicy -VDI2Optimization "Disabled"` |The command shown here uses the Set-CsTeamsVdiPolicy cmdlet to update an existing VDI policy with the Identity RestrictedUserPolicy. This policy uses all the existing values except one: VDI2Optimization; in this example, users with this policy can't be optimized with SlimCore. |
|Remove-CsTeamsVdiPolicy |Allows administrators to delete a previously created Teams VDI policy. Users with no explicitly assigned policy will fall back to the default policy in the organization. |`PS C:\> Remove-CsTeamsMeetingPolicy -Identity RestrictedUserPolicy` |In the example shown above, the command deletes the restricted user policy from the organization's list of policies and removes all assignments of this policy from users who have the policy assigned. |
|Get-CsTeamsVdiPolicy    |Allows administrators to retrieve information about all the VDI policies that have been configured in the organization. |`PS C:\> Get-CsTeamsVdiPolicy -Identity SalesPolicy` |In this example, Get-CsTeamsVdiPolicy is used to return the per-user meeting policy that has an Identity SalesPolicy. Because identities are unique, this command doesn't return more than one item. |

### Feature list with the new optimization

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

## SlimCore user profile on the endpoint

The new solution for VDI stores user-specific data on the endpoint in the following locations, depending on your vendor:

- `C:\users\<user>\AppData\Local\Microsoft\TeamsVDI\avd-default-<cloudname>\`
- `C:\users\<user>\AppData\Local\Microsoft\TeamsVDI\citrix-default-<cloudname>\`

> [!IMPORTANT]
> Locked-down thin clients must allow these locations to be read/write, otherwise the new optimization might fail. For older Windows 10 1809 Thin Clients (such as Dell Wyse 5070 and similar models), the folder location for SlimCore profile is
`C:\Users\<user>\AppData\Local\Packages\Microsoft.Teams.SlimCoreVdi.win-<architecture>.<version>_8wekyb3d8bbwe\LocalCache\`.

Logs, configurations, and AI or ML models (used in noise suppression, bandwidth estimation, etc.) are saved in this location. If these folders are purged after a user signs out (for example, locked-down thin clients without roaming profiles), MsTeamsVdi.exe will recreate them and download the user-specific configuration (about 6 MB of data).

### SlimCore installation and upgrade process in locked down Thin Client environments (optional)

By default, the MsTeamsPlugin automatically downloads and installs the right SlimCore media engine version without user or Admin intervention. But customers on restricted network environments in the branch office can opt for an alternative SlimCore distribution process, without requiring the endpoint be able to fetch SlimCore packages using https from Microsoft's public CDN.

> [!IMPORTANT]
> If you must chose this method, you must guarantee that:
>
> 1. [Teams auto-update is disabled](new-teams-vdi-requirements-deploy.md#disable-new-teams-autoupdate) in the virtual desktop.
> 2. The SlimCore packages are pre-provisioned to the endpoint's local storage or network share before you upgrade new Teams in the virtual desktop. Any newer Teams version will request a matching new version of SlimCore and if the plugin can't find it, the user will be in fallback mode (server-side rendering).
>
> This is because new Teams and SlimCore versions must match.

#### Configuration steps

1. On the user's endpoint (thin client/fat client), you must create the following regkey:
  - Location for Citrix: HKLM\SOFTWARE\WOW6432Node\Microsoft\Teams\MsTeamsPlugin
  - Location for Azure Virtual Desktop/W365: HKLM\SOFTWARE\Microsoft\Teams\MsTeamsPlugin
  - Name: MsixUrlBase
  - Type: REG_SZ
  - Data: Either local storage or network storage UNC path, such as file://C:/Temp or file://ComputerName/SharedFolder.
  The regkey defines the Base URL.
2. Additionally, admins must download the exact SlimCore MSIX Package version from Microsoft's CDN that matches the new Teams version you're planning to deploy in the future.

  > [!IMPORTANT]
  > The MSIX package needs to match the architecture or bitness of the Citrix Workspace app (x86 only) or Remote Desktop or Windows App clients: `Microsoft.Teams.SlimCoreVdi.<platform>-<architecture>.msix`.

3. Place the MSIX in a specific folder with the version within the location specified in the registry key to preserve the structure. For example, C:\Temp\2024.4.1.9\Microsoft.Teams.SlimCoreVdi.win-x86.msix or //ComputerName/SharedFolder/2024.4.1.9/.
  
  > [!NOTE]
  > If the Plugin can't find a SlimCore MSIX package in the local or network storage, it automatically attempts to download it from the Microsoft public CDN as a fallback.

#### Known issues

- AVD RemoteApps and Citrix Published Apps aren't supported at this time.
- Screen Capture Protection (SCP) causes the presenter's screen to show as a black screen with only the mouse cursor on top it (as seen by the receiving side).
- Calls drop on Teams running on the local machine that has an HID peripheral connected if a user launches a virtual desktop from that same local machine and logs into Teams.
- Camera self preview isn't supported at this time (either under Settings/Devices, or while on a call when selecting the down arrow on the camera icon).

#### Citrix virtual channel allow list

The [Virtual channel allow list](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/secure/virtual-channel-security#adding-virtual-channels-to-the-allow-list) policy setting in CVAD enables the use of an allow list that specifies which virtual channels can be opened in an ICA session. When enabled, all processes except the Citrix built-in virtual channels must be stated. As a result, more entries are required for the new Teams client to be able to connect to the client-side plugin (MsTeamsPluginCitrix.dll).

With Citrix Virtual Apps and Desktops 2203 or later, the virtual channel allow list is **enabled by default**. These default settings deny access to the new Teams custom virtual channels as the allow list **doesn't** include the new Teams main process name.

The new Teams client requires three custom virtual channels to function: MSTEAMS, MSTEAM1 and MSTEAM2. These channels are accessed by ms-teams.exe. You can use wildcards to allow the ms-teams.exe executable and custom virtual channel:

- MSTEAMS,C:\Program Files\WindowsApps\MSTeams*8wekyb3d8bbwe\ms-teams.exe
- MSTEAM1,C:\Program Files\WindowsApps\MSTeams*8wekyb3d8bbwe\ms-teams.exe
- MSTEAM2,C:\Program Files\WindowsApps\MSTeams*8wekyb3d8bbwe\ms-teams.exe

1. Wildcard support is available in:
  - VDA 2206 CR.
  - VDA 2203 LTSR from CU2 onwards.
2. The VDA machines must be rebooted for the policy to take effect.

#### Citrix App Protection and Microsoft Teams compatibility

Users who have App Protection enabled can still share their screen and apps while using the new optimization. Sharing requires VDA version 2402 or higher, and CWA for Windows 2309.1 or higher. Users on lower versions will end up sharing a black screen instead when the App Protection module is installed and enabled.

#### AVD Screen Capture Protection and Microsoft Teams compatibility

Users who have [Screen Capture Protection](/azure/virtual-desktop/screen-capture-protection?tabs=intune) (SCP) enabled can't share their screens or apps. Other people on the call can only see a black screen. If you want to allow users to share their screen even with SCP enabled, you need to disable SlimCore optimization in the Teams Admin Center policy (so the user will be optimized with WebRTC), and set the SCP policy to **Block screen capture on client**.

#### Troubleshooting

- Not optimized with SlimCore and instead you see:</br>"Azure Virtual Desktop Media Optimized"</br>"Citrix HDX Optimized"
  - Error Codes 2000 ("No Plugin") and 2001 ("Virtual Channel not available") are the most likely causes.
  
  1. Make sure your 'Virtual Channel Allow list' is properly configured to allow MSTEAMS, MSTEAM1, MSTEAM2.
  2. Make sure the endpoint has the plugin, and is loaded by the VDI Client with Process Explorer:
    - Run [process explorer](/sysinternals/downloads/process-explorer).
    - Enable the bottom pane and switch to the DLL tab.
    - On Azure Virtual Desktop, look for the msrdc.exe process and ensure the MsTeamsPluginAvd.dll is loaded.
    - On Citrix, look for the wfica32.exe process and ensure the MsTeamsPluginCitrix.dll is loaded.
  3. Restart the new Teams app. It requires two restarts to transition from WebRTC to SlimCore, when the plugin is detected for the first time.
  4. If the problem persists, check Event Viewer in the VM for **Microsoft Teams VDI**-related errors (new Teams 24123.X.X.X or higher).

- Not optimized with SlimCore and instead you see: "Azure Virtual Desktop SlimCore Media Not Connected" or "Citrix SlimCore Media Not Connected".
  - Check the [Troubleshooting SlimCoreVdi MSIX deployment errors](#troubleshooting-slimcorevdi-msix-deployment-errors) section. MSIX or AppX-related errors are the most likely reasons for this error.

## New Teams logs for VDI

Teams logs can be collected by selecting Ctrl+Alt+Shift+1 while running Teams on a VM. This action produces a ZIP folder in the Downloads folder. Inside the PROD-WebLogs-*.zip file, look for the Core folder.

### Vdi_debug.txt is the main file for VDI related information

|Azure Virtual Desktop/W365 |Citrix   |
|---------------------------|---------|
|"vdiConnectedState": {"connectedStack": "remote"}, "vdiVersionInfo": {"bridgeVersion": "2024.18.1.11", "remoteSlimcoreVersion": "2024.18.01.11", "nodeId": "1051a908af6b160e", "clientOsVersion": "10.0.22631", "rdClientVersion": "1.2.5405.0", "rdClientProductName": "Microsoft® Remote Desktop", "pluginVersion": "2024.14.01.1", "screenShareFallback": true} |"vdiConnectedState": {"connectedStack": "remote"}, "vdiVersionInfo": {"bridgeVersion": "2024.18.1.14", "remoteSlimcoreVersion": "2024.18.01.14", "nodeId": "ffffffff93eaee6a", "clientOsVersion": "10.0.22631", "rdClientVersion": "24.3.0.64", "rdClientProductName": "Citrix Workspace", "pluginVersion": "2024.15.01.3", "screenShareFallback": true} |

- **vdiConnectedState** shows the current active calling stack.
  - **connectedStack**: **remote** indicates Teams has successfully connected to the remote endpoint through the virtual channel. It doesn't necessarily mean the calling stack is successfully initialized, so the user can still encounter calling-related failures, such as being unable to start a call.
  - **connectedStack**: **local** indicates the virtual channel connection has failed. The user is now on fallback mode.
- **vdiVersionInfo** provides useful information for the Teams client and the endpoint.
  - **bridgeVersion** is tied to the version of the Teams desktop client running on the VM.
  - **remoteSlimcroreVersion** is the version of the SlimCore VDI that's available on the endpoint.
  - **nodeId** is a unique id tied to the endpoint.
  - **clientOsVersion** is the OS version for the endpoint.
  - **rdClientVersion** is the version of the remote desktop client running on the endpoint, which is used to connect to the VM.
  - **rdClientProductName** is the name of the remote desktop client running on the endpoint.
  - **pluginVersion** is the version of the plugin that is integrated into the remote desktop client.

### Diagnostics-logs.txt could be on weblogs\user(..)

For further investigating VDI connection-related issues, using keyword **vdiBRidgeEventsHandler** provides the logs from the vdiBridge connection and disconnection event handlings, as shown (onConnected event handling) in the following example of a successful connection with the new optimization stack:

`7432 2024-03-01T17:51:22.032Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - onConnected: end, currentStack=remote
7435 2024-03-01T17:51:22.032Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - new calling stack type set: currentStack=remote
7436 2024-03-01T17:51:22.032Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - deviceManagerService reloaded
7445 2024-03-01T17:51:22.031Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - calling stack reinit complete with nextStack=remote
7464 2024-03-01T17:51:21.785Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - starting calling stack reinit with nextStack=remote
7465 2024-03-01T17:51:21.785Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - SlimCore replacement complete, remote is now available
7467 2024-03-01T17:51:21.783Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - setVDIOptimizationModeOverride: from SlimCore to SlimCore
7468 2024-03-01T17:51:21.782Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - onConnected: isVersionMismatch=false, forceVersion=undefined, bridgeVersion=2024.5.1.11
7469 2024-03-01T17:51:21.782Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - cached local SlimCore for future (fallback), currentStack=local
7470 2024-03-01T17:51:21.782Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - onConnected: start, vendorType=1, remoteSlimcoreVersion=2024.05.01.11, platform=win-x86, loadErrc=1, deployErrc=24002, nodeId=ffffffffbd7d5e77
7471 2024-03-01T17:51:21.782Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - enqueueBridgeCallback: adding onConnected to queue, 0 bridge callbacks in queue, isBridgeCallbacksQueueProcessing=false`

### Connection error

If there's a connection error, the error code can be found from the log line containing "loadErrc" and "deployErrc". A deploy error (also known as install_error) is an error that happens when the plugin was trying to download the SlimCore MSIX package from Microsoft's CDN and stage or provision it to the endpoint using the App Readiness Service for AppX. A load error is an error that happens when the plugin tried to start MsTeamsVdi.exe and establish a Remote Procedure Call (RPC) to it.

The code logged here needs to be mapped using this table:

|loadErrc   |deployErrc |Definition                         |Notes |
|-----------|-----------|-----------------------------------|------|
|0          |0          |OK                                 |Special code for 'ConnectedNoPlugin' Telemetry Messages. |
|5          |43         |ERROR_ACCESS_DENIED                |MsTeamsVdi.exe process failed at startup. Could be caused by BlockNonAdminUserInstall being enabled. Or the endpoint could be busy registering multiple MSIX packages after a user logon and it didn't finish registering SlimCoreVdi. |
|404        |3235       |HTTP_STATUS_NOT_FOUND              |Publishing issue: SlimCore MSIX package isn't found on CDN. |
|1260       |10083      |ERROR_ACCESS_DISABLED_BY_POLICY    |This error usually means that Windows Package Manager can't install the SlimCore MSIX package. Event Viewer can show the hex error code 0x800704EC. AppLocker Policies can cause this error code. You can either disable AppLocker, or add an exception for SlimCoreVdi packages in Local Security Policy -> Application Control Policies -> AppLocker. Check [Step 3](#step-3-slimcore-msix-staging-and-registration-on-the-endpoint) under "Optimizing with new VDI solution for Teams". |
|1460       |11683      |ERROR_TIMEOUT                      |MsTeamsVdi.exe process failed at startup (60-second timeout). |
|1722       |           |RPC_S_SERVER_UNAVAILABLE           |'The RPC server is unavailable' MsTeamsVdi.exe related error. |
|2000       |16002      |No Plugin                          |Endpoint doesn't have the MsTeamsPlugin, or if it has it, it didn't load (check with Process Explorer). |
|2001       |           |Virtual Channel Not Available      |Error on Citrix VDA WFAPI. |
|3000       |24002      |SlimCore Deployment not needed     |This code isn't really an error. It's a good indicator that the user is on the new optimization architecture with SlimCore. |
|3001       |24010      |SlimCore already loaded            |This code isn't really an error. It's a good indicator that the user is on the new optimization architecture with SlimCore. |
|3004       |24035      |Plugin irresponsive                |Try restarting RDP or ICA session. |
|3005       |24043      |Plugin timeout while downloading   |Failure to download the MSIX within 2 minutes. |
|3007       |24058      |Load timeout                       |SlimCore download or installation timed out (slow internet or App Readiness Service is busy). |
|4000       |           |ERROR_WINS_INTERNAL                |WINS encountered an error while processing the command. |
|15615      |1951       |ERROR_INSTALL_POLICY_FAILURE       |SlimCore MSIX related error. To install this app, you need either a Windows developer license, or a sideloading-enabled system. AllowAllTrustedApps regkey might be set to 0? |
|15616      |           |ERROR_PACKAGE_UPDATING             |SlimCore MSIX related error 'The application cannot be started because it is currently updating'. |
|15700      |           |APPMODEL_ERROR_NO_PACKAGE          |The process has no package identity. There's no alias for MsTeamsVdi in %LOCALAPPDATA%\Microsoft\WindowsApps. [Feedback Hub](https://support.microsoft.com/windows/send-feedback-to-microsoft-with-the-feedback-hub-app-f59187f8-8739-22d6-ba93-f66612949332) logs are needed while reproducing the error (make sure you select **Developer Platform** as the category and **App deployment** as the subcategory) |
|16389      |           |E_FAIL reported by Package Manager |Usually the same as Load error code 5 (ERROR_ACCESS_DENIED). Most likely caused by the BlockNonAdminUserInstall policy when the user is not an Admin. Check [this link](/windows/client-management/mdm/policy-csp-applicationmanagement#blocknonadminuserinstall) for more details. |

## Using Event Viewer on the VM for troubleshooting

Every connect/disconnect event gets logged in the Event Viewer running on the Virtual Machine. The Event Viewer can also display client-side related errors. Filter by Source (Microsoft Teams VDI) and Event ID (0). Error codes can be found in the [New Teams logs for VDI](#new-teams-logs-for-vdi) section.

> [!NOTE]
> In order to be able to filter by Source, you need to run this command from an elevated powershell window:
>
> PS C:\Windows\system32> New-EventLog -LogName Application -Source "Microsoft Teams VDI"

## Troubleshooting Plugin deployment errors

Diagnostic information can be found in the detailed event logs on the user's device. After install, MsTeamsPluginCitrix.dll is written into the CWA folder. Only for the Citrix platform, the following keys on the Endpoint (not VM) are created:

|Key |Key type |Key name |Key value |
|---------|---------|---------|---------|
|HKLM\SOFTWARE\WOW6432Node\Citrix\ICA Client\Engine\Configuration\Advanced\Modules\ICA 3.0 |String |VirtualDriverEx |MicrosoftTeamsVDI |
|HKLM\SOFTWARE\WOW6432Node\Citrix\ICAClient\Engine\Configuration\Advanced\Modules\MicrosoftTeamsVDI |String |DriverNameWin32 |MsTeamsPluginCitrix.dll |

To debug installations, you can enable installer logging, but then you must use msiexec manually, and pass correct flags. For example, if the plugin isn't currently installed, it can be installed with logs like this: msiexec.exe /i MsTeamsPluginCitrix.msi /l*vx installer.log.txt.

## Troubleshooting SlimCoreVdi MSIX deployment errors

Make sure you review the [SlimCore MSIX staging and registration on the endpoint](#step-3-slimcore-msix-staging-and-registration-on-the-endpoint) section, as certain GPOs can prevent MSIX installations.

Diagnostic information can be found in the detailed event logs on the user's device.

1. Go the Event Viewer (Local) > Applications and Services Logs > Microsoft > Windows.
1. Check for available logs under these categories:
  - AppxPackagingOM > Microsoft-Windows-AppxPackaging/Operational
  - AppXDeployment-Server > Microsoft-Windows-AppXDeploymentServer/Operational
1. Review the logs under AppXDeployment-Server.

### Error 15615

Error 15615 usually means that the Windows Package Manager can't install the MSIX package with SlimCoreVdi.

- Make sure the digital signature of that MSIX is trusted by the Endpoint (Go to MSIX > Properties > Digital signatures > Details). It's a valid store-friendly Microsoft signature, but customers may have something special configured.
- Try enabling the [AllowAllTrustedApps policy](/windows/client-management/mdm/policy-csp-applicationmanagement).
- Try to allow sideloading apps from trusted nonstore sources.
  - On Windows 10, this setting is enabled by default, so modify it here in case it's disabled: Settings > Update and Security > For developers > Sideload apps.
  - On Windows 11, this setting is enabled by default: Settings > Apps > Advanced app settings > Choose where to get apps > Anywhere.

## Log collection

Logging can be found in the following locations:

- On the client:
  - `AppData\Local\Microsoft\TeamsVDI\<vdi_vendor>-default-<cloudname>\skylib`
  - `AppData\Local\Microsoft\TeamsVDI\<vdi_vendor>-default-<cloudname>\media-stack`
- On the Server:
  - `AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams\Logs\skylib`
