---
title: What is Microsoft Multi-Stream IntelliFrame and Intelligent Camera?
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: vishnuna
ms.date: 09/12/2024
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
search.appverid: MET150
description: Learn how to set up and use the Microsoft Teams Multi-Stream IntelliFrame cameras for hybrid meetings.
---
# What is Microsoft Multi-Stream IntelliFrame and Intelligent Camera?

Microsoft Teams Multi-Stream IntelliFrame is a AI (Artificial Intelligence) platform, which allows users to inspire and share experiences for remote users.

IntelliFrame provides an immersive video experience for remote users through a better meeting understanding by identifying the active speaker and a view of the room.
## Getting started

Microsoft Teams Multi-Stream IntelliFrame certified devices, include a speaker, microphone, and a AI camera that can produce multiple video streams and AI-powered active speaker tracking by recognizing facial movements and gestures.

### Prerequisites

- Microsoft Teams Rooms Windows device
- Microsoft Teams Rooms Pro license
  - Microsoft Teams Rooms with Pro license is required to enable IntelliFrame, and people recognition features on Microsoft Teams Rooms.
  - Basic license doesn't support IntelliFrame or people recognition. If you have Teams Rooms Basic license, the camera shows only active speaker and panoramic views.
  - Check the [this link](/microsoftteams/rooms/rooms-licensing#rooms-view) to determine if you have the right license.
- Policy configured for [People Recognition and Enrollment](#enabling-enrollment-option-and-people-recognition).

## Device provisioning

### Supported cameras

These Microsoft Teams Rooms devices support Multi-Stream IntelliFrame and people recognition:

- Yealink SmartVision 60
- Jabra Panacast 50

### Setting up your certified Multi-Stream IntelliFrame camera to your Microsoft Teams Room

Connect the supplied USB cable to the USB port on your Microsoft Teams Room device.

> [!Note]
> Ensure the cable is not pulled tightly or pinched for ideal data transmission and connectivity.

Sign in to Microsoft Teams Rooms settings as an admin and ensure your camera is selected.  You may need to adjust OEM specific camera settings to ignore displays or set tracking zones if you have glass walls in your conference room. Refer to your camera documentation for these processes as they're device specific.


## Enabling enrollment option and people recognition

In order for people recognition to function, you need to prepare your organizations by enabling [Face enrollment](#enabling-face-enrollment) and [People recognition](#enabling-people-recognition).

### Enabling face enrollment

A multi-stream IntelliFrame camera uses face and voice profile information of an enrolled user to recognize who is speaking from the room to enable the following features:

- Name labels on room participant stage videos.
- Roster entry under call room participants.
- Live transcription with recognition (who said what).

`CsTeamsMeetingPolicy` **enrollUserOverride** tenant policy must be **Enabled**. When an Admin applies the policy, face enrollment option shows up under **Recognition** tab along with voice enrollment.

> [!IMPORTANT]
>
> - You are responsible for compliance with local laws and regulations when you install a AI intelligent camera and use Face Enrollment and People Recognition in a particular jurisdiction, including with respect to obligations around notice, consent, and data retention.
> - Please install appropriate signage outside any meeting room, where you install an AI intelligent camera, advising people about the people recognition, face enrollment, and voice recognition features.
> - You must first enroll for Voice recognition before you can enroll for Face recognition.

- `enrollUserOverride` = {Disabled | Enabled}

  - **Enabled**- Policy value allows Enrollment tab to be seen on individual Teams user accounts for registering voice and face profiles.  
  - **Disabled** – No enrollment tab option (Default).

  *This policy should already be enabled if tenant already allows voice enrollment.

  :::image type="content" source="../media/enroll-user-override.png" alt-text="Screenshot that shows the voice recognition."

### Enabling people recognition

In some locations, people recognition can't be used due to local laws or regulations.

Enabling people recognition requires the tenant  `CsTeamsMeetingPolicy` **roomPeopleNameUserOverride** to be "**On**" and **roomAttributeUserOverride** to be **Attribute** for allowing individual voice and face profiles to be used for recognition in meetings.

- `roomPeopleNameUserOverride` = {On | Off}

  - **On** - Policy value allows **People recognition** option on Microsoft Teams Rooms under call control bar.  
  - **Off** – No People Recognition option on Microsoft Teams Room (Default).

- `roomAttributeUserOverride` = {Attribute | Off}

  - **Attribute** - Policy value allows **Voice identification** option on Microsoft Teams Rooms if transcription is started for the meeting.  
  - **Off** – No Voice identification option on Microsoft Teams Rooms (Default).

For more on information on setting meeting policies, see [Tenant administration control](../rooms/voice-recognition.md) and [Microsoft Teams PowerShell](../teams-powershell-overview.md).

PowerShell cmdlet sample for changing CsTeamsMeetingPolicy

```powershell
Import-Module MicrosoftTeams
$credential = Get-Credential   // Enter your admin’s email and password 
Connect-MicrosoftTeams –Credential $credential

New-CsTeamsMeetingPolicy    // enter identity name and use it in next steps 
Set-CsTeamsMeetingPolicy -identity {identity_name} –RoomPeopleNameUserOverride On 
Get-CsTeamsMeetingPolicy -identity {identity_name} // to confirm the changed value.

New-CsTeamsMeetingPolicy // enter identity name and use it in next steps.
Set-CsTeamsMeetingPolicy -identity {identity_name} –RoomAttributeUserOverride Attribute
Get-CsTeamsMeetingPolicy -identity {identity_name} // to confirm the changed value. 
```


## Getting Identified during a meeting. 

When you schedule a meeting, the users who wish to be identified must be invited to meeting or meeting forwarded to them before the meeting transcription is started . 

Note: Identification only works for Face enrolled users, everyone else will be treated as a participant.

> [!Note]
> Adhoc meetings won't have face identifications, where there is no Outlook appointment with a list of participants.
> 1:1 meeting will not have IntelliFrame or identification.
> Always schedule a meeting to use features like IntelliFrame and People recongnition.

## Known issues

| # | Behavior | Mitigation |
|---|----------|------------|
| 1 | When the view from the room is an Active speaker view and not IntelliFrame view, the **Name** label is missing on the participant video. | N/A |
| 2 | Intermittently room participants fail to get added to the Roster. | Option 1: Stop and Start the camera. Option 2: Restart device |
| 3 | The purple bounding box around the room is always highlighted even when there's no voice or sound from the Room. | N/A |
| 4 | Time taken to switch from IntelliFrame to Active speaker, after IntelliFrame toggle, and for **Name** labels to appear/disappear after people recognition toggle is five to seven seconds. | N/A |
| 5 | For people Identification, the Outlook invite supports a total of 64 users, which includes both users attending online and up to 12 concurrent users in the room for **Name** labels. | N/A |
| 6 | Room participants get identified: <br><li> If they're part of the Outlook meeting invite <br><li> If the meeting invite was forwarded to a participant before 30 minutes of the meeting. | N/A |


