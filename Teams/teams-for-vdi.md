---
title: Teams for Virtualized Desktop Infrastructure
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.date: 04/10/2019
ms.topic: article
ms.service: msteams
ms.reviewer: rafarhi
description: Learn how to run Microsoft Teams in a Virtualized Desktop Infrastructure (VDI) environment.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# Teams for Virtualized Desktop Infrastructure

This article describes the requirements and limitations for using Microsoft Teams in a virtualized environment.

## What is VDI?

Virtual Desktop Infrastructure (VDI) is virtualization technology that hosts a desktop operating system and applications on a centralized server in a data center. This enables a fully personalized desktop experience to users with a fully secured and compliant centralized source. 
 
Currently, Teams in a virtualized environment is available with support for collaboration and chat functionality with a dedicated persistent virtualized machine (VM). To ensure an optimal user experience, follow the guidance in this article. 

## Teams requirements

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
