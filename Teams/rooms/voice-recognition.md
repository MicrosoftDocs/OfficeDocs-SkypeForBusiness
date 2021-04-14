---
title: Tenant Administration control for voice recognition (voice profile) in Teams Rooms 
author: cichur
ms.author: v-cichur
ms.reviewer: parisataheri
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn about Tenant Administration control for voice recognition (voice profile) in Teams meeting rooms.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Manage voice recognition technology controls for an Intelligent Speaker

Intelligent Speakers use voice profile information to recognize who said what in live transcription. When a Microsoft Teams Rooms for Windows meeting room is equipped with an Intelligent Speaker, live transcription can be used during the meeting. This article explains how you, a tenant admin, control the voice profiling that's used for voice recognition to generate live transcription. You can control to what degree the organization is using voice recognition and the following features:

- Edit the speaker's name in transcripts.
- Change the speaker of a single utterance in the transcript or change the speaker in all the utterances in the transcript (but not on future transcripts).
- Change the speaker identification for the people who are listed in the meeting.
- Remove the identification of a single utterance or all utterances identified as that speaker on every transcript.

## Use an Intelligent Speaker in Teams Rooms

Intelligent Speakers are intelligent peripherals for Microsoft Teams Rooms. They'll bring speaker attributed transcription for participants in the meeting room. Intelligent Speakers include a special seven-microphone array. The speakers use voice profile information to identify voices of up to 10 people in meeting rooms. The speakers help you see who said what during and after the meeting.

### Review Intelligent Speaker requirements

The following items are Intelligent Speaker requirements:

- The customer tenant must be located in the U.S.(North America).<sup>1</sup> 
- Rooms has a maximum of 10 people present in person.
- Rooms has an upload link of minimum 7 Mbps.

 <sup>1</sup> Rockfall and associated biometric storage and usage will only be available in EN-US language and for US (NA-US region) tenants. Both conditions must be true for a tenant user to be able to enroll and use Rockfall for attributed transcription.

## Set up an Intelligent Speaker

Yealink Rockfall connects directly using USB to the Teams Rooms console. For best results, we recommend that you use Yealink Rockfall with the Yealink console.

> [!NOTE]
> We don't support Rockfall connected to Logitech Surface Pro Microsoft Teams Rooms. There is a known issue that Teams Rooms can't recognize the Rockfall device through the dock.

Rockfall should be placed at least 8 inches (20 cm) away from walls and large objects, such as laptops. If the Rockfall USB cable isn't long enough for your setup, use cable extenders.

1. Sign in to the console as administrator.
2. Set the Teams device settings to match the Rockfall microphone and speaker. (**They can also do this through the TAC portal instead of at the room console.)What is TAC?**
3. Ensure you have the correct microphone and speaker settings.

The diagram shows how the Intelligent Speaker is connected to the device.

   ![The Intelligent Speaker setup with the speaker, the power and data box. One line goes to the USB port of the console, and the other line goes to power. ](../media/intelligent-speakers.png)

> [!Note]
> EPOS and Yealink devices should have "EPOS" or "Yealink" prefix and contain "UAC2_RENDER" in the speaker name and "UAC2_TEAMS" in the microphone name. If you don't find these microphone and speaker names in the dropdown menu, restart the Rockfall device.

### Enable an Intelligent Speaker and user attribution

Use the following required policies to set speaker and user attribution.

- `enrollUserOverride`: Use `enrollUserOverride` to control user voice enrollment. Allowed values are `Enabled` and `Disabled`.
- `roomAttributeUserOverride`: To control the voice-based user identification in meeting rooms. This setting is required for Teams Rooms accounts. Allowed values are `Off`, `attribute`, which means room participants will be distinguished and identified based on enrolled voices (if enrolled). *This setting will be available at a later date.*
- `enabletranscription`: This setting is required for user and Teams rooms accounts. Allowed values are `true` and `false`.

## Use voice profile policies

There are two major policies used with a voice profile:

- Capture, which controls the capture of the voice profile data through the enrollment flow.
- Usage, which controls how the voice profile data will be used in meeting rooms.

Voice profile data can be used in any meeting with an Intelligent Speaker. See [Teams meetings policies](../meeting-policies-in-teams.md) and the [PowerShell meeting cmdlets](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy?view=skype-ps) for information on the meeting settings.

### Voice profile settings

Turn on or off voice profile capture, or enrollment, in Teams settings through the admin policy `EnrollUserOverride`. An admin can enable or disable the enrollment feature for a tenant. One policy will cover voice enrollment. This policy works independently from the usage policy to give admins flexibility to roll out this feature. The flexibility includes:

- Turn on voice profile capture.
- Enroll users.
- Turn on usage.

When the settings are enabled:

- Users can view, access, and complete the enrollment flow.
- The entry point will show on Teams settings page under the **Recognition** tab.  

Settings are disabled by default. When the Capture policy is disabled:

- Users who have never enrolled can't view, enroll, or re-enroll.
- The entry point to the enrollment flow will be hidden.
- If users select a link to the enrollment page, they'll see a message that this feature isn't enabled for their organization.  
- Users who have already enrolled will be able to view and remove their voice profile in the Teams settings. Once they remove their voice profile, they won't be able to view, access, or complete the enrollment flow.  

### Set voice profile usage

Turn on or off voice profile usage for attribution and diarization. (Speaker diarization is the process of partitioning an input audio stream into homogeneous segments according to the speaker identity.) Use `RoomAttributeUserOverride` in Rooms to set voice profile usage. An admin can control if users in a conference room will be attributed, diarized (distinguished), or neither. This policy controls use of both voice and face for transcription attribution purposes. This setting is **off** by default, so it won't use a user's attribute or distinguish features.

- Rooms won't send audio stream-saving bandwidths from the room.  
- Rooms users won't be attributed or distinguished, and their voice signatures won't be retrieved or used at all.
- Rooms users are unknown.  

The attribute feature captures the following details:

- Rooms users will be attributed based on their enrollment status.
- Users who are enrolled, are shown with their name in the transcription.  
- Users who aren't enrolled show as Speaker n.
- Rooms will send 7 audio streams from the room.

(**coming in the future** do we want to say this?) The distinguish feature captures the following details only for people who are invited:

- Rooms users will be distinguished but not named (Speaker n). No user identity is shown for in-room attendees.
- Rooms will send seven audio streams from the room.

The voice profile of the user is created when the policy is set to distinguish or a non-meeting invitee walks in during the meeting. The voice profile is dismissed at the end of the meeting.

## Frequently asked questions (FAQ)

**Where is the voice profile data stored?**

Voice profile data is stored in Office 365 cloud with user content.

**How long is voice profile information stored after an employee has left the company?**

Voice profile data is considered user content and is treated as such per Office 365 data retention policy described in the [Data retention overview](https://docs.microsoft.com/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

**Is voice profile data used across Microsoft services?**

Scenario 1: User enrolls in company tenant and then uses Microsoft consumer service (Xbox, Teams for Life, Office 365 Personal. Their voice is recognized by the consumer service.
Scenario 2: Users enroll in their company tenant and their voice is recognized and attributed in the meeting hosted by another company.

No, voice profile data is only used for the purpose for which the user has provided consent. Therefore, Microsoft isn't intending to use the voice profile data across different non-Teams services at this point.

However,  Microsoft may decide in the future to use the same voice and face enrollment data for other Microsoft Office 365 scenarios. Such a decision will be duly notified, with required consent and policies in place, empowering tenant admins to decide and control.

**Is Rockfall General Data Protection Regulation (GDPR) compliant?**

Yes, audio data collected from user can be exported by the tenant admin using Teams admin center.

**What is the retention timeline and policy?**

General retention policy is stated in the [Data retention overview](https://docs.microsoft.com/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview). In addition, the voice profile data will be deleted after three years if the data isn't used in any meetings for existing employees.

> [!NOTE]
> In the future, if we can give a bar of how good the audio data is, then you can evaluate the quality of the transcript.(**reviewer comment**)
