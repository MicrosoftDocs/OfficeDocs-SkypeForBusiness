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

Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, or Windows Server 2008 with Remote Desktop Services (RDS) (formerly known as Terminal Services) allow a server to host multiple, simultaneous client sessions. Remote Desktop uses Remote Desktop Services technology to allow a single session to run remotely. A user can connect to a Remote Desktop Session Host (RD Session Host) server (formerly known as a terminal server) by using Remote Desktop Connection (RDC) client software. The Remote Desktop Web Connection extends Remote Desktop Services technology to the web.

Currently, Teams in a remote desktop services environment is available with support for collaboration and chat functionality. To ensure an optimal user experience, follow the guidance in this article.

## Teams requirements

### Set policies to turn off calling and meeting functionality in Teams

The Teams calling and meeting experience isn't optimized for a Remote Desktop Services. We recommend you set user-level policies to turn off calling and meeting functionality in Teams.

You can still choose to run Teams fully in RDS using either the Teams desktop app or web app. However, we recommend that you set the policies to avoid compromising the user experience.

It can take some time (a few hours) for the policy changes to propagate. If you don’t see changes for a given account immediately, try again in a few hours.

Use the **CSTeamsCallingPolicy** cmdlets to control whether users are allowed to use calling and calling options in private and group chats. Here's the list of policy settings and recommended values.

| **Policy name**     | **Description**                                                                                                                                                        | **Recommended value**                                                                                                                               |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| AllowCalling        | Controls interop calling capabilities. Turning this on allows Skype for Business users to have one-on-one calls with Teams users and vice versa.                       | Set to False to prevent calls from Skype for Business users landing in Teams.                                                                       |
| AllowPrivateCalling | Controls whether the Calling app is available in the app bar on the left side of the Teams client and whether users see Calling and Video call options in private chat | Set to False to remove the Calling app from the app bar on the left side of Teams and to remove the Calling and Video call options in private chat. |

#### Create and assign a calling policy

1.  Start a Windows PowerShell session as an administrator.

2.  Connect to the Skype Online Connector.

3.  \# Set Office 365 User Name and Password

4.  $username = “admin email address”

5.  password = ConvertTo-SecureString "password" -AsPlainText -Force

6.  $LiveCred = new-object -typename System.Management.Automation.PSCredential -argumentlist $username, $password

7.  \# Connect to Skype Online

8.  Import-Module SkypeOnlineConnector

9.  $sfboSession = New-CsOnlineSession -Credential $LiveCred

10. Import-PSSession $sfboSession\`\`\`

11. View a list of calling policy options.

12. Get-CsTeamsCallingPolicy

13. Look for the built-in policy option where all calling policies are disabled. It looks like this.

14. Identity : Tag:DisallowCalling

15. AllowCalling : False

16. AllowPrivateCalling : False

17. AllowVoicemail : False

18. AllowCallGroups : False

19. AllowDelegation : False

20. AllowUserControl : False

21. AllowCallForwardingToUser : False

22. AllowCallForwardingToPhone : False

23. PreventTollBypass : False

24. Apply the DisallowCalling built-in policy option to all users who will be using Teams in a virtualized environment.

25. Grant-CsTeamsCallingPolicy -PolicyName DisallowCalling -Identity “user email id”

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

1.  Start a Windows PowerShell session as an administrator.

2.  Connect to the Skype Online Connector.

3.  \# Set Office 365 User Name and Password

4.  $username = “admin email address”

5.  password = ConvertTo-SecureString "password" -AsPlainText -Force

6.  $LiveCred = new-object -typename System.Management.Automation.PSCredential -argumentlist $username, $password

7.  \# Connect to Skype Online

8.  Import-Module SkypeOnlineConnector

9.  $sfboSession = New-CsOnlineSession -Credential $LiveCred

10. Import-PSSession $sfboSession\`\`\`

11. View a list of meeting policy options.

12. Get-CsTeamsMeetingPolicy

13. Look for the built-in policy option where all meeting policies are disabled. It looks like this.

14. Identity : Tag:AllOff

15. Description :

16. AllowChannelMeetingScheduling : False

17. AllowMeetNow : False

18. AllowIPVideo : False

19. AllowAnonymousUsersToDialOut : False

20. AllowAnonymousUsersToStartMeeting : False

21. AllowPrivateMeetingScheduling : False

22. AutoAdmittedUsers : False

23. AllowCloudRecording : False

24. AllowOutlookAddIn : False

25. AllowPowerPointSharing : False

26. AllowParticipantGiveRequestControl : False

27. AllowExternalParticipantGiveRequestControl : False

28. AllowSharedNotes : False

29. AllowWhiteboard : False

30. AlowTranscription : False

31. MediaBitRateKb : False

32. ScreenSharingMode : False

33. Apply the AllOff built-in policy option to all users who will be using Teams in a virtualized environment.

34. Grant-CsTeamsMeetingPolicy -PolicyName AllOff -Identity “user email id”

For more information about Teams meeting policies, see [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy).
