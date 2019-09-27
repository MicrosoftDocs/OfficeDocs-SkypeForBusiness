---
title: Teams for Virtualized Desktop Infrastructure
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: rafarhi, jmorrow
audience: admin
description: Learn how to run Microsoft Teams in a Virtualized Desktop Infrastructure (VDI) environment.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# Teams for Virtualized Desktop Infrastructure

This article describes the requirements and limitations for using Microsoft Teams in a virtualized environment.

## What is VDI?

Virtual Desktop Infrastructure (VDI) is virtualization technology that hosts a desktop operating system and applications on a centralized server in a data center. This enables a fully personalized desktop experience to users with a fully secured and compliant centralized source.

Microsoft Teams in a virtualized environment is available with support for chat and collaboration as well as with calling and meeting on Citrix setups.
 
Teams in a virtualized environment supports multiple configurations. These include VDI, RDHS, dedicated, shared, persistent and non-persistent modes. Features are in continuous development and are added on a regular basis, so the functionality will expand in the coming months and years.
 
Using Teams in a virtualized environment may be somewhat different from using Teams non-virtualized. For example, some advanced features may not be available in a virtualized environment and video resolution may differ. To ensure an optimal user experience, follow the guidance in this article.

## Teams on VDI components

Using Teams in a virtualized environment requires the following components.

1. Virtualization broker: The resource and connection manager to the virtualization provider
2. Virtual desktop: Virtual machine (VM) stack, Microsoft Teams
3. Client: Endpoint that the user physically interfaces with

## Teams on VDI requirements

### Virtualization provider requirements

The Teams app is being validated with leading virtualization solution providers. With multiple market providers, we recommend that you consult your virtualization solution provider to ensure minimum requirements are met.
  
Teams on VDI with AV optimization is certified with Citrix. See the following details to ensure both Citrix and Teams requirements are met for proper functionality.

#### Citrix virtual Apps and Desktops requirements

Citrix provides a new solution to deliver Microsoft Teams optimization through Citrix Virtual Apps and Desktops (formerly known as XenApp and XenDesktop).

The necessary components are bundled into the Citrix Workspace app (CWA) and Virtual Delivery Agent (VDA) by default. There's no additional components or plugins that you need to install on CWA or the VDA (in contrast to RealTime Optimization Pack for Skype for Business, RTC and RTME respectively).

**Server requirements**

|Component  |Requirement  |
|---------|---------|
|Operating system   |Windows 10 1607 or later<br>Windows Server 2012 R2 or later        |
|VDA     |Version 1906      |
|Microsoft .NET Framework    |Version 4.7.1 or later (installed automatically)        |
|Microsoft Visual C++   |2013 and 2015 runtimes, 32-bit and 64-bit       |
|BCR_x64.msi    |MSI that contains the Microsoft Teams optimization code and starts automatically from the GUI. If a command-line interface for the VDA installation is used, don't exclude it.      |

**Client requirements**

|Component  |Requirement  |
|---------|---------|
|Workspace app  |Version 1906 or later      |
|Operating system     |Windows 7, Windows 10 1607 or later<br>32-bit and 64-bit including Embedded editions|
|CPU   |1.8 to 2.0 GHz quad core CPU that can support 360p nHD resolution during a peer-to-peer video conference call<br> 2.8 GHz quad core CPU that can support 720p HD resolution during a peer-to-peer video conference call|
|Memory |1 GB RAM    |
|Storage    |Minimum 600 MB free disk space|

For the latest requirements for Citrix components, see [this website](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html).

#### Get the latest Citrix software

You can download the latest version of Citrix Virtual Apps and Desktops [here](https://www.citrix.com/downloads/citrix-virtual-apps-and-desktops/betas-and-tech-previews.html). You'll need to sign in first. 

#### Citrix-approved thin clients

Citrix supports many clients and the clients aren't vendor-specific. Clients must meet the minimum requirements as outlined in the earlier table.

### Virtual Machine minimum requirements

#### Dedicated persistent setup

With the diverse workloads and user needs in a virtualized environment, the following is the recommended minimum VM configuration.

|Parameter  |Workstation operating system  |Server operation system  |
|---------|---------|---------|
|vCPU   |    2 cores     |  *4,6, or 8       |
|RAM     |   4 GB      | 512 to 1024 MB per user        |
|Storage    | 8 GB        | 40 to 60 GB        |

It's important to understand the underlying non-uniform memory access (NUMA) configuration and configure your VMs accordingly.

#### Non-persistent setup

We recommend that you configure a caching manager to ensure efficient Teams runtime data sync.

#### Teams cached content exclusion list

We recommend that you exclude the following from the Teams caching folder, %appdata%/Microsoft/Teams.

- .txt files
- Media-stack folder

### Teams performance on VDI

There are variety of virtualized setups, each with a different focus for optimization. For example, user density. Use these guidelines to help optimize your setup based on the workload needs of your organization:

- Minimum requirement: Some workloads may require a setup using resources that are above the minimum requirements.
- Dependencies: These include dependencies on infrastructure, workload, and other environmental considerations outside the Teams desktop app.
- Disabled features on VDI: Teams disables  GPU-intensive features for VDI, which can help improve transient CPU utilization. The following features are disabled:

- Teams CSS Animation
- Giphy auto-start

## Install the Teams desktop app on VDI

The Teams desktop app for VDI can be installed per-machine and per-user.  With per-machine installation,automatic updates is disabled for the Teams app. With the per-user installation, automatic updates is enabled.

For most VDI deployments, we recommend to deploy Teams using a per-machine configuration.

Note: You can also configure Teams by using the Microsoft Teams admin center.

### Deploy the Teams desktop app

1. Download the Teams MSI package that matches your VDI VM operating system using one of the following links.

    - [32-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true)
    - [64-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true&arch=x64)

2. Install the MSI to the VDI VM by running one of the following commands:

    - Per-user installation
    - Per-machine installation

        ```
        msiexec /i <path_to_msi> /l*v <install_logfile_name> ALLUSER=1
        ```

    This installs Teams to the Program Files (x86) folder on a 64-bit operating system and to the Program Files folder on a 32-bit operating system. At this point, the golden image setup is complete.
 
    The next interactive logon session starts Teams and asks for credentials.

3. Uninstall the MSI from the VDI VM by running the following command:

         ```
        msiexec /passive /x <path_to_msi> /l*v <uninstall_logfile_name>
         ```

    This uninstalls Teams from the Program Files (x86) folder or Program Files folder, depending on the operating system environment.

#### Teams desktop app updates

Updates for the Teams desktop app depends on whether deployment was per-machine or per-user. For per-machine deployments, automatic updates is disabled. This means that to update the Teams app, Teams must be uninstalled, and then reinstalled.

To learn more, see [Teams update process](teams-client-update.md).

#### Teams on VDI and Office 365 ProPlus support

Teams clients on VDI aren't automatically updated the way that non-VDI Teams clients are. You have to update the VM image by installing a new MSI as described in the [Install the Teams desktop app on VDI](#install-the-teams-desktop-app-on-vdi) section. You must uninstall the current version to update to a newer version. To learn more, see [Teams update process](teams-client-update.md).

## Teams on VDI - Calling and Meeting with the Citrix platform

Teams on VDI with Calling and Meeting feature support is available with Citrix-based platforms. Supported features are based on the WebRTC media stack and Citrix-specific implementation.

This diagram provides an overview of the architecture.

Supported Calling and Meeting features

## Known issues and limitations

### Client deployment, installation, and setup

- Teams on VDI isn't automatically updated in the way that non-VDI Teams clients are.  You have to update the VM image at least once a month by installing a new MSI as described in the [Install the Teams desktop app on VDI](#install-the-teams-desktop-app-on-vdi) section.  
- MacOs and Linux-based clients are not supported at this time. Support for the Citrix-based platform will be announced by Citrix at a future time.
- Dual installation


## Chat and collaboration

## Known issues and limitations

## Appendix A

## Appendix B

### Set policies to turn off calling and meeting functionality in Teams

The Teams calling and meeting experience isn't optimized for a VDI environment (coming soon). We recommend you set user-level policies to turn off calling and meeting functionality in Teams.

You can still choose to run Teams fully in VDI using either the Teams desktop app or web app. However, we recommend that you set the policies to avoid compromising the user experience.  

It can take some time (a few hours) for the policy changes to propagate. If you don’t see changes for a given account immediately, try again in a few hours.

> [!NOTE]
> When Teams calling and meetings are optimized for use in virtual desktop environments, you can revert these policies and allow users to use Teams as they normally would. 

#### Calling

Use the **CSTeamsCallingPolicy** cmdlets to control whether users are allowed to use calling and calling options in private and group chats. Here's the list of policy settings and recommended values.

|Policy name  |Description |Recommended value  |
|---------|---------|---------|
|AllowCalling    |Controls interop calling capabilities. Turning this on allows Skype for Business users to have one-on-one calls with Teams users and vice versa.         |Set to False to prevent calls from Skype for Business users landing in Teams.          |
|AllowPrivateCalling     | Controls whether the Calling app is available in the app bar on the left side of the Teams client and whether users see Calling and Video call options in private chat         |Set to False to remove the Calling app from the app bar on the left side of Teams and to remove the Calling and Video call options in private chat.          |

#### Create and assign a calling policy

1. Start a Windows PowerShell session as an administrator.
2. Connect to the Skype Online Connector.

        # Set Office 365 User Name and Password
        $username = “admin email address”
        password = ConvertTo-SecureString "password" -AsPlainText -Force
        $LiveCred = new-object -typename System.Management.Automation.PSCredential -argumentlist $username, $password
        # Connect to Skype Online
        Import-Module SkypeOnlineConnector
        $sfboSession = New-CsOnlineSession -Credential $LiveCred
        Import-PSSession $sfboSession```

3. View a list of calling policy options.

       Get-CsTeamsCallingPolicy
 
4. Look for the built-in policy option where all calling policies are disabled. It looks like this.
   
        Identity                        : Tag:DisallowCalling
        AllowCalling                    : False
        AllowPrivateCalling             : False
        AllowVoicemail                  : False
        AllowCallGroups                 : False
        AllowDelegation                 : False
        AllowUserControl                : False
        AllowCallForwardingToUser       : False
        AllowCallForwardingToPhone      : False
        PreventTollBypass               : False

5. Apply the DisallowCalling built-in policy option to all users who will be using Teams in a virtualized environment.

        Grant-CsTeamsCallingPolicy -PolicyName DisallowCalling -Identity “user email id”

For more information about Teams calling policies, see [Set-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallingpolicy).

#### Meetings

Use the **CsTeamsMeetingPolicy** cmdlets to control the type of meetings that users can create, the features that they can access while in a meeting, and the meeting features that are available to anonymous and external users. Here's the list of policy settings and recommended values.

|Policy Name |Description|Recommended Value                   |
|-------------------|-----------------|-----------------------|
|AllowPrivateMeetingScheduling  | Determines whether a user is allowed to schedule private meetings.| Set to False to prohibit the user from being able to schedule private meetings.  |
|AllowChannelMeetingScheduling  | Determines whether a user is allowed to schedule channel meetings. | Set to False to prohibit the user from being able to schedule channel meetings.                       |
|AllowMeetNow |Determines whether a user is allowed to create or start ad-hoc meetings.              |  Set this to False to prohibit the user from being able to start ad-hoc meetings.                     |
|ScreenSharingMode | Determines the mode in which a user is allowed to share their screen in calls or meetings. | Set to Disabled to prohibit the user from sharing their screens                          |
|AllowIPVideo |Determines whether video is enabled in a user's meetings or calls.                  |    Set to False to prohibit the user from sharing their video                                         |
| AllowAnonymousUsersToDialOut | Determines whether anonymous users are allowed to dial out to a PSTN number. | Set to False to prohibit anonymous users from dialing out                                  |
| AllowAnonymousUsersToStartMeeting | Determines whether anonymous users can start a meeting.     |  Set to False to prohibit users from starting a meeting                                            |
| AllowOutlookAddIn |Determines whether a user can schedule Teams meetings in the Outlook desktop client.| Set to False to prohibit a user from  scheduling Teams meetings in the Outlook desktop client|
| AllowParticipantGiveRequestControl|Determines whether participants can request or give control of screen sharing.| Set to False to prohibit the user from giving and requesting control in a meeting    |
| AllowExternalParticipantGiveRequestControl | Determines whether external participants can request or give control of screen sharing.| Set to False to prohibit an external user from giving, requesting control in a meeting|
|AllowPowerPointSharing|Determines whether PowerPoint sharing is allowed in a user’s meetings. |Set to False to prohibit a user from sharing PowerPoint files in a meeting  |
|AllowWhiteboard | Determines whether whiteboard is allowed in a user’s meetings. |   Set to False to prohibit whiteboard in a meeting |
| AllowTranscription |Determines whether real-time and/or post-meeting captions and transcriptions are allowed in a user's meetings.|    Set to False to prohibit transcription  and captions in a meeting  |  
| AllowSharedNotes | Determines whether users are allowed to take shared notes. | Set to False to prohibit users from taking shared notes |
|MediaBitRateKB |Determines the media bit rate for audio/video/app sharing transmissions in meetings  | Suggested value is 5000 (5 MB). You can change it based on your organization’s needs.| 

#### Create and assign a meeting policy

1. Start a Windows PowerShell session as an administrator.
2. Connect to the Skype Online Connector.

        # Set Office 365 User Name and Password
        $username = “admin email address”
        password = ConvertTo-SecureString "password" -AsPlainText -Force
        $LiveCred = new-object -typename System.Management.Automation.PSCredential -argumentlist $username, $password
        # Connect to Skype Online
        Import-Module SkypeOnlineConnector
        $sfboSession = New-CsOnlineSession -Credential $LiveCred
        Import-PSSession $sfboSession```

3. View a list of meeting policy options.

       Get-CsTeamsMeetingPolicy
 
4. Look for the built-in policy option where all meeting policies are disabled. It looks like this.
   
        Identity                                    : Tag:AllOff
        Description                                 :
        AllowChannelMeetingScheduling               : False
        AllowMeetNow                                : False
        AllowIPVideo                                : False
        AllowAnonymousUsersToDialOut                : False
        AllowAnonymousUsersToStartMeeting           : False
        AllowPrivateMeetingScheduling               : False
        AutoAdmittedUsers                           : False
        AllowCloudRecording                         : False
        AllowOutlookAddIn                           : False
        AllowPowerPointSharing                      : False
        AllowParticipantGiveRequestControl          : False
        AllowExternalParticipantGiveRequestControl  : False
        AllowSharedNotes                            : False
        AllowWhiteboard                             : False
        AllowTranscription                          : False
        MediaBitRateKb                              : False
        ScreenSharingMode                           : False

5. Apply the AllOff built-in policy option to all users who will be using Teams in a virtualized environment. 

        Grant-CsTeamsMeetingPolicy -PolicyName AllOff -Identity “user email id”

 For more information about Teams meeting policies, see [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy).

### Virtualization provider requirements

The Teams app has been validated on leading virtualization solution providers. With multiple market providers, consult your virtualization solution provider to ensure minimum requirements are met.

### Virtual Machine requirements

With the diverse workloads and user needs in a virtualized environment, the following is the minimum recommended VM configuration.

|Parameter  |Measure  |
|---------|---------|
|vCPU    |  2 cores       |
|RAM     |  4 GB      |
|Storage     | 8 GB       |

### Virtual Machine operating system requirements

The supported operating systems for VM are:

- Windows 10 and later
- Windows Server 2012 R2 and later

## Install Teams on VDI

Here's the process and tools to deploy the Teams desktop app. 

1. Download the Teams MSI package using one of the following links depending on the environment. We recommend the 64-bit version for a VDI VM with a 64-bit operating system.

    - [32-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true)
    - [64-bit version](https://teams.microsoft.com/downloads/desktopurl?env=production&plat=windows&download=true&managedInstaller=true&arch=x64)

2. Run the following command to install the MSI to the VDI VM (or complete updating it).

        msiexec /i <path_to_msi> /l*v <install_logfile_name> ALLUSER=1

    This installs Teams to Program Files. At this point, the golden image setup is complete.
 
    The next interactive logon session starts Teams and asks for credentials. Note that it's not possible to disable auto-launch of Teams when installing Teams on VDI using the ALLUSER property. 

3. Run the following command to uninstall the MSI from the VDI VM (or prepare for updating it).

        msiexec /passive /x <path_to_msi> /l*v <uninstall_logfile_name>

    This uninstalls Teams from Program Files.

## Known issues and limitations

The following are known issues and limitations for Teams on VDI.

- **Shared session host type deployments**: Shared session host type deployments (for example, shared non-persistent VM configuration) aren't in scope.
- **Calling and meetings**:

    - Calling and meeting scenarios aren't optimized for VDI. These scenarios will perform poorly. We recommend using user-level policies as described in the [Set policies to turn off calling and meeting functionality in Teams](#set-policies-to-turn-off-calling-and-meeting-functionality-in-teams) section.  
    - Applying the policies described in this article impacts the ability to use calling and meeting functionality, which depending on other policies, may affect other users in your organization. If users in your organization use non-VDI clients, you can choose to not apply the policies.  

- **Joining calls and meetings created by other users**: Although the policies restrict users from creating meetings, they can still join meetings if another user dials out to them from the meeting. In these meetings, the user's ability to share video, use whiteboard and other features depend on whether you disabled those features using TeamsMeetingPolicy.  
- **Cached content**: If the virtual environment in which Teams is running isn't persistent (and data is cleaned up at the end of each user session), users may notice performance degradation due to content refresh, regardless of whether the user accessed the same content in a previous session.
- **Client updates**: Teams on VDI isn't automatically updated with per-machine MSI installation. You have to update the VM image by installing a new MSI as described in the [Install Teams on VDI](#install-teams-on-vdi) section. You must uninstall the current version to update to a newer version.
- **User experience**: The Teams user experience in a VDI environment may be different from a non-VDI environment. The differences may be because of policy settings and/or feature support in the environment.

For Teams known issues that aren't related to VDI, see [Known issues for Microsoft Teams](Known-issues.md).

## Related topics

- [Install Microsoft Teams using MSI](msi-deployment.md)
