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

Microsoft Teams in a virtualized environment is available with support for chat and collaboration as well as with calling and meeting on Citrix.
 
Teams in a virtualized environment supports multiple configurations. These include VDI, RDHS, dedicated, shared, persistent and non-persistent modes. Features are in continuous development and are added on a regular basis, so  functionality will expand in the coming months and years.
 
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

#### Citrix Virtual Apps and Desktops requirements

Citrix provides a new solution to deliver Microsoft Teams optimization through Citrix Virtual Apps and Desktops (formerly known as XenApp and XenDesktop). The necessary components are bundled into the Citrix Workspace app (CWA) and Virtual Delivery Agent (VDA) by default. There's no additional components or plugins that you need to install on CWA or the VDA (in contrast to RealTime Optimization Pack for Skype for Business, RTC and RTME respectively).

You can download the latest version of Citrix Virtual Apps and Desktops [here](https://www.citrix.com/downloads/citrix-virtual-apps-and-desktops/betas-and-tech-previews.html). (You'll need to sign in first.)

Here are the minimum server and client requirements for Citrix components. For the latest requirements, see [this website](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html).

**Server requirements**

|Component  |Requirement  |
|---------|---------|
|Operating system   |Windows 10 1607 or later<br>Windows Server 2012 R2 or later        |
|VDA     |Version 1906      |
|Microsoft .NET Framework    |Version 4.7.1 or later (installed automatically)        |
|Microsoft Visual C++   |2013 and 2015 runtimes, 32-bit and 64-bit       |
|BCR_x64.msi    |MSI that contains the Microsoft Teams optimization code and starts automatically from the GUI. If a command-line interface for the VDA installation is used, don't exclude it.      |

**Client requirements**

Citrix supports many clients and the clients aren't vendor-specific. Clients must meet these minimum requirements.

|Component  |Requirement  |
|---------|---------|
|Workspace app  |Version 1906 or later      |
|Operating system     |Windows 7, Windows 10 1607 or later<br>32-bit and 64-bit including Embedded editions|
|CPU   |1.8 to 2.0 GHz quad core CPU that can support 360p nHD resolution during a peer-to-peer video conference call<br> 2.8 GHz quad core CPU that can support 720p HD resolution during a peer-to-peer video conference call|
|Memory |1 GB RAM    |
|Storage    |Minimum 600 MB free disk space|

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

There are variety of virtualized setup configurations, each with a different focus for optimization. For example, user density. Use these guidelines to help optimize your setup based on the workload needs of your organization:

- Minimum requirement: Some workloads may require a setup using resources that are above the minimum requirements.
- Dependencies: These include dependencies on infrastructure, workload, and other environmental considerations outside the Teams desktop app.
- Disabled features on VDI: Teams disables GPU-intensive features for VDI, which can help improve transient CPU utilization. The following features are disabled:

- Teams CSS Animation
- Giphy auto-start

## Install the Teams desktop app on VDI

You can deploy the Teams desktop app for VDI using a per-machine installation or per-user installation. With per-machine installation, automatic updates is disabled. This means that to update the Teams app, Teams must be uninstalled, and then reinstalled. With per-user installation, automatic updates is enabled.

For most VDI deployments, we recommend to deploy Teams using a per-machine installation.

Note: You can also configure Teams in the Microsoft Teams admin center.???

For Teams on VDI and Office 365 ProPlus, you have to update the VM image by installing a new MSI. You must uninstall the current version to update to a newer version.???

To learn more about updates for Teams, see [Teams update process](teams-client-update.md).

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

## Teams on VDI with calling and meeting with the Citrix platform

Teams on VDI with calling and meeting support is available with Citrix-based platforms. Supported features are based on the WebRTC media stack and Citrix-specific implementation.

The following diagram provides an overview of the architecture.

### Supported calling and meeting features

Here's a list of supported calling and meeting features.

- 1:1 audio/video calls
- 1:1 group call escalation
    - Multi-call handling
    - Blind transfer
    - Consultative transfer
- Transfer to PSTN
    - Safe transfer
    - Simultaneous ring
    - Forward to group
    - Call forwarding
    - Group call pickup
- Call blocking
    - Boss and delegate support
    - Distinctive ring
    - Do not disturb
    - Out of office support
    - Voicemail
    - Speed dial
    - Suggested contacts
    - Shared line appearance
- Enterprise Voice (EV) Dial to PSTN numbers and receive calls to a user's EV PSTN number in Teams
    - Schedule in Outlook and Teams
    - Private and channel meetings
- Cloud recording
    - Participant management
    - Device selection
    - Mute other participants
- Desktop screen sharing
- PowerPoint load and share
- Whiteboard and meeting notes

The following calling and meeting features are not supported:

- Enhanced emergency services
- HID buttons and LED controls between the Teams app and devices
- Background blur and effects
- Broadcast/live events
- Location-Based Routing (LBR)
    - Call park
    - Call queue

We're working on adding calling and meeting features that are currently only available in non-VDI environments. These may include more admin control over quality, additional screen sharing scenarios, and advanced features recently added to Teams. Contact your Teams representative to learn more about upcoming features.

### Network requirements

Teams relies on Transport Relay servers in Azure for meetings, multiparty calls, and scenarios where two peers in a point-to-point call don't have direct connectivity. Therefore, the network health between the peer and the Office 365 cloud determines the performance of the call. This also implies that the client requires internet connectivity to use calling.

We recommend evaluating your environment to identify any risks and requirements that can influence your overall cloud voice and video deployment. Use the [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885) to test whether your network is ready for Teams.

To learn more about how to prepare your network for Teams, see [Prepare your organization's network for  Teams](prepare-network.md).

### Migrate from Skype for Business on VDI to Teams on VDI

If you're migrating from Skype for Business on VDI to Teams on VDI, besides the differences between the two applications, there are some differences when VDI is also implemented. Some capabilities that aren’t currently supported in Teams VDI that are in Skype for Business VDI are as follows:

- Control of VDI calling experiences with policies for limiting media bit rate
- Per-platform policy to disable some AV features in VDI
- Give and take control when app sharing
- Screen share from chat without audio
- Simultaneous video and screen sharing send and receive

### Teams on Chrome browser versus Teams desktop app for VDI

Teams on Chrome browser doesn't provide a replacement for the Teams desktop app for VDI with AV optimization. The chat and collaboration experience works as expected. When media is needed, there are some experiences that may not meet user expectations on the Chrome browser.

- The audio and video streaming experience may not be optimal. Users may experiences delays or reduced quality.
- Device settings aren't available in browser settings.
- Device management is handled through the browser and requires multiple settings in browser site settings.
- Device settings may also need to be set in Windows device management.

## Teams on VDI with chat and collaboration

If your organization wants to only use chat and collaboration features in Teams, you can set user-level policies to turn off calling and meeting functionality in Teams. For steps on how to do this, see [Appendix B: Turn off calling and meeting functionality in Teams](#appendix-b-turn-off-calling-and-meeting-functionality-in-teams).

### Migrate Teams on VDI with chat and collaboration to Citrix with AV optimization

If you have an existing implementation of Teams on VDI with chat and collaboration in which you set policies to turn off calling and meeting functionality for Teams users on VDI, and you're migrating to Citrix with AV optimization, use policies to turn on calling and meeting functionality for those Team users.

#### Calling

Teams includes the built-in AllowCalling calling policy, in which all calling features are turned on. Assign the AllowCalling policy to all users in your organization who use Teams in a virtualized environment.

To view the settings in the AllowCalling policy, in the left navigation of the Microsoft Teams admin center, go to **Voice** > **Calling policies**, and then in the list of policies, click **AllowCalling**.

#### Meeting

Teams includes the built-in AllOn meeting policy, in which all meeting features are turned on. Assign the AllOn policy to all users in your organization who use Teams in a virtualized environment.

To view the settings in the AllOn policy, in the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Meeting policies**, and then in the list of policies, click **AllOn**

#### Assign the policies to users

1. In the left navigation of the Microsoft Teams admin center, go to **Users**.
2. Select the user by clicking to the left of the user name, and then click **Edit settings**.
3. Do one of the following:
     - Under **Calling policy**, click **AllowCalling**.
     - Under **Meeting policy**, click **AllOn**. 
4. Click **Apply**.

To assign a policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md).

Or, you can also do the following:

1. In the left navigation of the Microsoft Teams admin center, do one of the following:
    - Go to **Voice** > **Calling policies**, and then click **AllowCalling**.
    - Go to **Meetings** > **Meeting policies**, and then click **AllOn**.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then click **Add**. Repeat this step for each user that you want to add.
5. When you're finished adding users, click **Save**.

It can take some time (a few hours) for policy changes to propagate. If you don’t see changes for a given account immediately, try again after a few hours.

## Known issues and limitations

### Client deployment, installation, and setup

- Teams on VDI isn't automatically updated in the way that non-VDI Teams clients are.  You have to update the VM image at least once a month by installing a new MSI as described in the [Install the Teams desktop app on VDI](#install-the-teams-desktop-app-on-vdi) section.  
- MacOs and Linux-based clients are not supported at this time. Support for the Citrix-based platform will be announced by Citrix at a future time.
- Dual installation

### Calling and meeting

- Interoperability with Skype for Business is limited to audio calls, no video modality.
- NoDual Tone Multi Frequency (DTMF) is currently not supported.
- Joining Teams meetings as an anonymous user isn't AV-optimized. The user can join the meeting and have a non-optimized experience. This applies only to TAP. 
- Only a single incoming video stream is supported in meetings or group calls. When multiple people send video, only the dominant speaker's video is shown at any given time.  
- Incoming and outgoing video stream resolution is limited to 720p resolution. This is a WebRTC limitation.
- Only one video stream from an incoming camera or screen share stream is supported. When there's an incoming screen share, that screen share is shown it instead of the video of the dominant speaker.
- Outgoing screen sharing:
    - Application sharing is not supported.
    - Potential privacy issue with multiple screen.
- Give control and take control:  
    - Not supported during a screen sharing or application sharing session.
    - Supported during a PowerPoint sharing session.  
- In some cases, zooming windows that contain video content may create situations where user interface elements are partially visible.  
- High DPI scaling on CWA is not supported.

For Teams known issues that aren’t related to VDI, see [Known issues for Teams](Known-issues.md).

## Appendix A: Troubleshoot Citrix components

### Virtual Desktop Agent

The following four services are installed by BCR_x64.msi.

|Service  |Path the .exe file  |Log on as  |Description  |
|---------|---------|---------|---------|
|Citrix HDX HTML5 Video Redirection Service     |Program Files (x86)\Citrix\System32\WebSocketService.exe /service         |Local system account         |Provides HTML5 video redirection, Browser content redirection, and Teams redirection with secure WebSocket services        |
|Citrix HDX Browser Redirection Service    |Program Files (x86)\Citrix\System32\CtxSvcHost.exe" -g BrowserRedirSvcs          |This account (local service)         |Provides browser content redirection between the endpoint device and the virtual desktop        |
|Citrix HDX Port Forwarding Service     |Program Files (x86)\Citrix\System32\CtxSvcHost.exe" -g PortFwdSvcs         |This account (local service)         |Provides port forwarding between the endpoint device and the virtual desktop.         |
|Citrx HDX Teams Redirection Service     |Program Files (x86)\Citrix\System32\CtxSvcHost.exe" -g TeamsSvcs         |This account (local service)         |         |

Of these, the Citrix HDX Teams Redirection Service and Citrix HDX HTML5 Video Redirection Service are responsible for Teams redirection in the VDA.

#### Citrix HDX Teams Redirection Service

This service establishes the virtual channel used in Teams.

#### Citrix HDX HTML5 Video Redirection Service

This service runs as WebSocketService.exe listening on 127.0.0.1:9002 TCP. WebSocketService.exe performs two main functions:

- TLS termination for secure WebSockets. The service receives a secure WebSocket connection from vdiCitrixPeerConnection.js which is a component inside the Teams app. You can track this using Process Monitor.
- User session mapping. WebSocketAgent.exe starts in the user’s session in the VDA by WebSocketService.exe (which runs in Session 0 as a LocalSystem account) when the Teams app starts.

WebSocketService.exe listens in two TCP sockets, 127.0.0.1:9001 and 127.0.0.1:9002. Port 9001 is used for browser content redirection and HTML5 video redirection features. Port 9002 is used for Teams redirection.

To check whether the service is in an active listening state in the VDA, you can do the following.

**Option 1**

In a browser, go to [https://127.0.0.1:9002](https://127.0.0.1:9002). Success means there was communication with the service.

**Option 2**

Open the DevTools console in Microsoft Edge, and then do the following:
1. Type the following:

    ```
    var exampleSocket = new WebSocket('wss://127.0.0.1:9002');  
    exampleSocket.onmessage = function(messageEvent) { console.log(JSON.stringify(messageEvent)); };
    ```

2. Wait a few seconds, and then type the following:

    ```
    exampleSocket.readyState
    ```

The expected output is **1**, which indicates that the WebSocket connection was successful. The following table lists the possible outputs.

|  |  |
|---------|---------|
|0 (CONNECTING) The connection is not yet open     | 1 (OPEN) The connection is open and ready to communicate      |
|2 (CLOSING) The connection is in the process of closing   | 3 (CLOSED) The connection is closed or couldn't be opened |

If the output is **3** or if you receive a "failed: Error in connection establishment: net::ERR_CONNECTION_REFUSED [HdxWebRTC.js] Unable to connect to websocket service!" error message, make sure that the Citrix HDX Team Redirection Service is running. Restart, if necessary.

### Citrix Workspace app

When Teams opens in the VDA, CWA for Windows instantiates a new service, HdxTeams.exe, on the user’s endpoint. If you don’t see the HdxTeams.exe  on the user's endpoint, do the following:

1. Check the following:
    - Make sure the correct version of the CWA is installed. You should install the version that's included in the TAP build.
    - Make sure that HdxTeams.exe and Webrpc.dll are in the CWA installation folders.
    - Use Wireshark or TCP View to monitor HdxTeams.exe and analyze the network traffic.
    - Check whether there are incoming and outgoing packets between the process and the Azure cloud (or another peer).

    If you still don't see the HdxTeams.exe service, go to step 2.

2. Make sure that HdxTeams.exe is running.
    1. Exit Teams on VDA.
    2. Start services.msc on VDA, and then stop Citrix HDX Teams Redirection Service.
    3. Disconnect the ICA session.
    4. Start Citrix HDX Teams Redirection Service, and then restart Citrix HDX HTML5 Redirection Service.
    5. Open Teams on VDA.

   If you still don't see the HdxTeams.exe service, go to step 3.

3. Restart the VDA, and then restart the client endpoint.

## Appendix B: Turn off calling and meeting functionality in Teams

This section describes how to set user-level policies to turn off calling and meeting functionality in Teams. You can set policies by using the Microsoft Teams admin center or PowerShell.  

It can take some time (a few hours) for the policy changes to propagate. If you don’t see changes for a given account immediately, try again in a few hours.

### Calling

Calling policies in Teams control which calling features are available to users. Teams includes the built-in DisallowCalling calling policy, in which all calling features are turned off. Assign the DisallowCalling policy to all users in your organization who use Teams in a virtualized environment.

#### Using the Microsoft Teams admin center

To view the settings in the DisallowCalling policy, in the left navigation of the Microsoft Teams admin center, go to **Voice** > **Calling policies**, and then in the list of policies, click **DisallowCalling**.

To assign the DisallowCalling policy to users:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**.
2. Select the user by clicking to the left of the user name, and then click **Edit settings**.
3. Under **Calling policy**, select **DisallowCalling**, and then click **Apply**.

To assign a policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md).

Or, you can also do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Calling policies**.
2. Select **DisallowCalling** by clicking to the left of it.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then click **Add**. Repeat this step for each user that you want to add.
5. When you're finished adding users, click **Save**.

To learn more, see [Calling policies in Teams](teams-calling-policy.md).

#### Using PowerShell

Use the **CSTeamsCallingPolicy** cmdlets to manage calling policies in Teams. Here's the list of policy settings and recommended values.

|Policy name  |Description |Recommended value  |
|---------|---------|---------|
|AllowCalling    |Controls interop calling capabilities. Turning this on allows Skype for Business users to have 1:1 calls with Teams users and vice versa.         |Set to False to prevent calls from Skype for Business users landing in Teams.          |
|AllowPrivateCalling     | Controls whether the Calling app is available in the app bar on the left side of the Teams client and whether users see calling and video call options in private chat         |Set to False to remove the Calling app from the app bar on the left side of Teams and to remove the calling and video call options in private chat.          |

**Assign the DisallowCalling calling policy**

1. Start a Windows PowerShell session as an administrator.
2. Connect to the Skype Online Connector.

    ```
    # Set Office 365 User Name and Password
    $username = “admin email address”
    password = ConvertTo-SecureString "password" -AsPlainText -Force
    $LiveCred = new-object -typename System.Management.Automation.PSCredential -argumentlist $username, $password
    # Connect to Skype Online
    Import-Module SkypeOnlineConnector
    $sfboSession = New-CsOnlineSession -Credential $LiveCred
    Import-PSSession $sfboSession
    ```

3. View a list of calling policy options.

    ```
    Get-CsTeamsCallingPolicy
    ```

4. Look for the built-in policy where all calling features are turned off. It looks like this.

    ```
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
    ```

5. Apply the DisallowCalling policy to all users who use Teams in a virtualized environment.

    ```
    Grant-CsTeamsCallingPolicy -PolicyName DisallowCalling -Identity “user email id”
    ```

To learn more, see [Set-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallingpolicy).

### Meetings

Meeting policies in Teams control the types of meetings that users can create and the features that are available to meeting participants that are scheduled by users in your organization. Teams includes the built-in AllOff meeting policy, in which all meeting features are turned off. Assign the AllOff policy to all users in your organization who use Teams in a virtualized environment.

#### Using the Microsoft Teams admin center

To view the settings in the DisallowCalling policy, in the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Meeting policies**, and then in the list of policies, click **AllOff**.

To assign the DisallowCalling policy to users, do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**.
2. Select the user by clicking to the left of the user name, and then click **Edit settings**.
3. Under **Meeting policy**, select **AllOff**, and then click **Apply**.

To assign a policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md).

Or, you can also do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Meetings** > **Meeting policies**.
2. Select **AllOff** by clicking to the left of it.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then click **Add**. Repeat this step for each user that you want to add.
5. When you're finished adding users, click **Save**.

To learn more, see [Manage meeting policies in Teams](meeting-policies-in-teams.md).

#### Using PowerShell

Use the **CsTeamsMeetingPolicy** cmdlets to manage meeting policies in Teams. Here's the list of policy settings and recommended values.

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

**Assign the AllOff meeting policy**

1. Start a Windows PowerShell session as an administrator.
2. Connect to the Skype Online Connector.

    ```
    # Set Office 365 User Name and Password
    $username = “admin email address”
    password = ConvertTo-SecureString "password" -AsPlainText -Force
    $LiveCred = new-object -typename System.Management.Automation.PSCredential -argumentlist $username, $password
    # Connect to Skype Online
    Import-Module SkypeOnlineConnector
    $sfboSession = New-CsOnlineSession -Credential $LiveCred
    Import-PSSession $sfboSession
    ```

3. View a list of meeting policy options.

    ```
    Get-CsTeamsMeetingPolicy
    ```

4. Look for the built-in policy where all meeting features are turned off. It looks like this.

    ```   
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
    ```

5. Apply the AllOff policy to all users who use Teams in a virtualized environment.

    ```
    Grant-CsTeamsMeetingPolicy -PolicyName AllOff -Identity “user email id”
    ```

 To learn more, see [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy).

+++++

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

For Teams known issues that aren't related to VDI, see [Known issues for Teams](Known-issues.md).

## Related topics

- [Install Microsoft Teams using MSI](msi-deployment.md)
- [Teams PowerShell Overview](teams-powershell-overview.md)
