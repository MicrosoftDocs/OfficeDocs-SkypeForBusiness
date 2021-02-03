---
title: Use Teams with remote desktop services
author: cichur
ms.author: v-cichur
ms.reviewer: alivano
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to use Microsoft Teams with remote desktop services.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

# Teams in Remote Desktop Services

This article describes the requirements and limitations for using Microsoft Teams in a remote desktop services (RDS) environment.

## What is RDS?

Remote Desktop Services (RDS) is the platform of choice for building virtualization solutions for every end customer need, including delivering individual virtualized applications, providing secure mobile and remote desktop access, and providing end users the ability to run their applications and desktops from the cloud.

RDS offers deployment flexibility, cost efficiency, and extensibility—all delivered through a variety of deployment options, including Windows Server 2016 for on-premises deployments, Microsoft Azure for cloud deployments, and a robust array of partner solutions.
Depending on your environment and preferences, you can set up the RDS solution for session-based virtualization, as a virtual desktop infrastructure (VDI)

Currently, Teams in a remote desktop services environment is available with support for collaboration and chat functionality. To ensure an optimal user experience, follow the guidance in this article.

## Teams requirements

### Set policies to turn off calling and meeting functionality in Teams

The Teams calling and meeting experience isn't optimized for RDS. We recommend you set user-level policies to turn off calling and meeting functionality in Teams.

You can still choose to run Teams fully in RDS using either the Teams desktop app or web app. However, we recommend that you set the policies to avoid compromising the user experience.

It can take some time (a few hours) for the policy changes to propagate. If you don’t see changes for a given account immediately, try again in a few hours.

Use the **CSTeamsCallingPolicy** cmdlets to control whether users are allowed to use calling and calling options in private and group chats. Here's the list of policy settings and recommended values.

| **Policy name**     | **Description**                                                                                                                                                        | **Recommended value**                                                                                                                               |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| AllowCalling        | Controls interop calling capabilities. Turning this on allows Skype for Business users to have one-on-one calls with Teams users and vice versa.                       | Set to False to prevent calls from Skype for Business users landing in Teams.                                                                       |
| AllowPrivateCalling | Controls whether the Calling app is available in the app bar on the left side of the Teams client and whether users see Calling and Video call options in private chat. | Set to False to remove the Calling app from the app bar on the left side of Teams and to remove the Calling and Video call options in private chat. |

#### Create and assign a calling policy

1. Start a Windows PowerShell session as an administrator.

2. Connect to the Skype Online Connector.

```powershell
\# Set Office 365 User Name and Password
$username = “admin email address”
password = ConvertTo-SecureString "password" -AsPlainText -Force
$LiveCred = new-object -typename System.Management.Automation.PSCredential -argumentlist $username, $password
\# Connect to Skype Online
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $LiveCred
Import-PSSession $sfboSession\`\`\`
```

3. View a list of calling policy options by using Get-CsTeamsCallingPolicy.

4. Look for the built-in policy option where all calling policies are disabled. It looks like this:

   - Identity : Tag:DisallowCalling

   - AllowCalling : False

   - AllowPrivateCalling : False

   - AllowVoicemail : False

   - AllowCallGroups : False

   - AllowDelegation : False

   - AllowUserControl : False

   - AllowCallForwardingToUser : False

   - AllowCallForwardingToPhone : False

   - PreventTollBypass : False

5. Apply the DisallowCalling built-in policy option to all users who will be using Teams in a virtualized environment.

```powershell
Grant-CsTeamsCallingPolicy -PolicyName DisallowCalling -Identity “user email id”
```
  
For more information about Teams calling policies, see [Set-CsTeamsCallingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamscallingpolicy).

#### Meetings

Use the **CsTeamsMeetingPolicy** cmdlets to control the type of meetings that users can create, the features that they can access while in a meeting, and the meeting features that are available to anonymous and external users. Here's the list of policy settings and recommended values.

| **Policy Name**                            | **Description**                                                                                                | **Recommended Value**                                                                        |
|--------------------------------------------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| AllowPrivateMeetingScheduling              | Determines whether a user is allowed to schedule private meetings.                                             | Set to False to prohibit the user from being able to schedule private meetings.              |
| AllowChannelMeetingScheduling              | Determines whether a user is allowed to schedule channel meetings.                                             | Set to False to prohibit the user from being able to schedule channel meetings.              |
| AllowMeetNow                               | Determines whether a user is allowed to create or start ad-hoc meetings.                                       | Set this to False to prohibit the user from being able to start ad-hoc meetings.             |
| ScreenSharingMode                          | Determines the mode in which a user is allowed to share their screen in calls or meetings.                     | Set to Disabled to prohibit the user from sharing their screens                              |
| AllowIPVideo                               | Determines whether video is enabled in a user's meetings or calls.                                             | Set to False to prohibit the user from sharing their video                                   |
| AllowAnonymousUsersToDialOut               | Determines whether anonymous users are allowed to dial out to a PSTN number.                                   | Set to False to prohibit anonymous users from dialing out                                    |
| AllowAnonymousUsersToStartMeeting          | Determines whether anonymous users can start a meeting.                                                        | Set to False to prohibit users from starting a meeting                                       |
| AllowOutlookAddIn                          | Determines whether a user can schedule Teams meetings in the Outlook desktop client.                           | Set to False to prohibit a user from scheduling Teams meetings in the Outlook desktop client |
| AllowParticipantGiveRequestControl         | Determines whether participants can request or give control of screen sharing.                                 | Set to False to prohibit the user from giving and requesting control in a meeting            |
| AllowExternalParticipantGiveRequestControl | Determines whether external participants can request or give control of screen sharing.                        | Set to False to prohibit an external user from giving, requesting control in a meeting       |
| AllowPowerPointSharing                     | Determines whether PowerPoint sharing is allowed in a user’s meetings.                                         | Set to False to prohibit a user from sharing PowerPoint files in a meeting                   |
| AllowWhiteboard                            | Determines whether whiteboard is allowed in a user’s meetings.                                                 | Set to False to prohibit whiteboard in a meeting                                             |
| AllowTranscription                         | Determines whether real-time and/or post-meeting captions and transcriptions are allowed in a user's meetings. | Set to False to prohibit transcription and captions in a meeting                             |
| AllowSharedNotes                           | Determines whether users are allowed to take shared notes.                                                     | Set to False to prohibit users from taking shared notes                                      |
| MediaBitRateKB                             | Determines the media bit rate for audio/video/app sharing transmissions in meetings                            | Suggested value is 5000 (5 MB). You can change it based on your organization’s needs.        |

#### Create and assign a meeting policy

1. Start a Windows PowerShell session as an administrator.

2. Connect to the Skype Online Connector.

```powershell
\# Set Office 365 User Name and Password
$username = “admin email address”
password = ConvertTo-SecureString "password" -AsPlainText -Force
$LiveCred = new-object -typename System.Management.Automation.PSCredential -argumentlist $username, $password
\# Connect to Skype Online
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $LiveCred
Import-PSSession $sfboSession\`\`\`
```

3. View a list of meeting policy options using Get-CsTeamsMeetingPolicy.

4. Look for the built-in policy option where all meeting policies are disabled. It looks like the following items:

   - Identity : Tag:AllOff
   - Description :

   - AllowChannelMeetingScheduling : False

   - AllowMeetNow : False

   - AllowIPVideo : False

   - AllowAnonymousUsersToDialOut : False

   - AllowAnonymousUsersToStartMeeting : False

   - AllowPrivateMeetingScheduling : False

   - AutoAdmittedUsers : False

   - AllowCloudRecording : False

   - AllowOutlookAddIn : False

   - AllowPowerPointSharing : False

   - AllowParticipantGiveRequestControl : False

   - AllowExternalParticipantGiveRequestControl : False

   - AllowSharedNotes : False

   - AllowWhiteboard : False

   - AlowTranscription : False

   - MediaBitRateKb : False

   - ScreenSharingMode : False

5. Apply the AllOff built-in policy option to all users who will be using Teams in a virtualized environment:

```powershell
Grant-CsTeamsMeetingPolicy -PolicyName AllOff -Identity “user email id”
``` 

For more information about Teams meeting policies, see [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy).
