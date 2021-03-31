---
title: Tenant Administration control for voice recognition (biometric data) in meeting rooms 
author: cichur
ms.author: v-cichur
ms.reviewer: parisataheri
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn about Tenant Administration control for voice recognition (biometric data) in meeting rooms.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Tenant Administration control for voice recognition (biometric data) in Teams Meeting Rooms

Microsoft Teams Meetings Rooms now have voice recognition. A Teams tenant admin can control to what degree the organization is using voice recognition (biometric data). This feature allows people to edit the speakers of transcripts. You can change the speaker of a single utterance on all transcripts. The people you can change the speaker label for are the ones who are listed in the meeting. You can remove the identification of a single utterance or all utterances identified as that speaker on every transcript.

There are two major policies used with biometric data:

- Capture, which controls the capture of the biometric data through the enrollment flow.
- Usage, which controls how the biometric data will be used in meeting rooms.

Biometric data can be used in any meeting with or without external audio devices.

## Use biometric data settings

Turn on or off biometric capture, or enrollment, in Teams settings through the admin policy EnrollUserOverride. An admin can enable or disable the enrollment feature for a tenant. One policy will cover both voice and face enrollment. This policy works independently from the usage policy to give admins flexibility to roll out this feature. The flexibility includes:

- Turn on biometric capture.
- Enroll users.
- Turn on usage.

When the settings are enabled:

- Users can view, access, and complete the enrollment flow.
- The entry point will show on Teams settings page.  

Settings are disabled by default. When the settings are disabled:

- Users who have never enrolled can't view, enroll, or re-enroll.
- The entry point to enrollment flow will be hidden.
- If users select a link to enrollment page, they'll see a message that this feature isn't enabled for their organization.  
- Users who have already enrolled will be able to view and remove their biometric data in the Teams settings. Once they remove their biometric data, they won't be able to view, access, or complete the enrollment flow.  

## Set biometric usage

Turn on or off biometric usage for attribution and diarization. Speaker diarization is the process of partitioning an input audio stream into homogeneous segments according to the speaker identity. Use RoomAttributeUserOverride in Rooms to set biometric usage. An admin can control if users in a conference room will be attributed, diarized (distinguished), or neither. This policy controls use of both voice and face for transcription attribution purposes. This setting is **off** by default, so it won't use a user's attribute or distinguish features.

- Rooms won't send audio stream-saving bandwidths from the room.  
- Rooms users won't be attributed or diarized.
- Rooms users are unknown.  

Distinguish participants but don't identify the participants

- Rooms users will be diarized but not specifically named (attendee n). No user identity is shown for in-room attendees.
- Rooms will send seven audio streams from the room.

Biometric information of the user is created during the meeting and dismissed at the end of the meeting.

Attribute  

- Rooms users will be attributed based on their enrollment status. 
- Users who are enrolled, are shown with their name in the transcription.  
- Users who aren't enrolled show as attendee n.
- Rooms will send seven audio streams from the room.

## Use intelligent speakers in Teams Rooms

Intelligent speakers are intelligent peripherals for Microsoft Teams Rooms. They'll bring speaker attributed transcription for participants in the meeting room, enabling attendees to spend less time note taking and easily follow along who said what in the room. Intelligent speakers include a special seven microphone array and Microsoft Office graph and biometric information to identify voices of up to ten people in meeting rooms so whether you are working remotely or following the meeting in the conference room, you can effectively see who said what during and after the meeting.

## Review the requirements

- The customer tenant must be located in the U.S.(North America).
-	Rooms have regular meetings with multiple (2-10) people present in person.
- Rooms have upload link of minimum 7Mbps.
- All meetings will be recorded by Microsoft for testing and AI/speech training. Customers must be aware of the recordings. Signs need to be posted inside and outside of the conference room to this effect (provided by Microsoft).

## Set up the device

Yealink Rockfall connects directly using USB to the Teams Rooms console. For best results, we recommend that you use Yealink Rockfall with the Yealink console.

Rockfall should be placed at least eight inches (20 cm) away from walls and large objects, such as laptops. If the the Rockfall USB cable isn't long enough for your setup, use cable extenders.

1. Sign in to the console as administrator.
2. Set the Teams device settings to match the Rockfall microphone and speaker.
3. Make sure you have the right Microphone and Speaker settings. 
   
> [!Note]
> EPOS and Yealink devices should have "EPOS" or "Yealink" prefix and contain "UAC2_RENDER" in the speaker name and "UAC2_TEAMS" in the microphone name. If you don't find these microphone and speaker names in the dropdown menu, restart the Rockfall device. For best results, Rockfall should be placed at least eight inches away from walls and large objects, such as laptops.

## Enable intelligent speaker and user attribution

Use the following required policies to set speaker and user attribution.

- `enrollUserOverride`: To control user biometric (voice) enrollment using the Teams desktop client (Windows). This isn't required to be set for mobile accounts. Allowed values are `Enabled` and `Disabled`. 
- `roomAttributeUserOverride`: To control the voice-based user identification in meeting rooms. Required for MTR accounts. Allowed values are `Off`, `attribute`, which means room participants will be distinguished and identified based on enrolled voices (if enrolled). 
`enabletranscription`: Required for user and MTR accounts. Allowed values are `true` and `false`.

## To set the tenant policies, complete the following steps.

1. Open the PowerShell admin mode. 

    ```PowerShell
    Install-Module MicrosoftTeams $userCredential = Get-Credential
    ```

2. Enter tenant admin credentials.

    ```PowerShell
    $teamsSession= New-CsOnlineSession -Credential $userCredential 
    Import-PSSession $teamsSession 
    Get-CsTeamsMeetingPolicy => To check out the current configuration. 
    Set-CsTeamsMeetingPolicy -Identity <Value> -<PolicyName> <Value>  
    ```

    Examples:

    ```PowerShell
    Set-CsTeamsMeetingPolicy –Identity XYZ -AllowTranscription "True"
    Set-CsTeamsMeetingPolicy –Identity XYZ -EnrollUserOverride "Enabled"
    Set-CsTeamsMeetingPolicy –Identity XYZ -RoomAttributeUserOverride "Attribute"
    ```

3. If you’re trying to set up a new identity, run the following commands:

    ```PowerShell
    New-CsTeamsMeetingPolicy –Identity TestMeetingPolicy  -AllowTranscription $True -EnrollUserOverride "Enabled" -RoomAttributeUserOverride "Attribute"
    ```

   See [New-csteamsmeetingpolicy](https://docs.microsoft.com/powershell/module/skype/new-csteamsmeetingpolicy?view=skype-ps).

4. To grant the above created identity to certain user, instructions see [grant-csteamsmeetingpolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsmeetingpolicy?view=skype-ps)

   ```PowerShell
   Grant-CsTeamsMeetingPolicy -identity "Ken Myer" -PolicyName TestMeetingPolicy
   ```

## Related topics

- [Teams PowerShell install](https://docs.microsoft.com/MicrosoftTeams/teams-powershell-install)
- [set-csteamsmeetingpolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy?view=skype-ps)
