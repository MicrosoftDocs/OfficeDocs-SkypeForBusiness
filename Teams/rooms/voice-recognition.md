---
title: Tenant Administration control for voice recognition (voice profile) in Teams Rooms
author: tonysmit
ms.author: tonysmit
ms.reviewer: parisataheri
ms.date: 03/29/2021
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
ms.subservice: itpro-rooms
search.appverid: MET150
description: Learn about Tenant Administration control for voice recognition (voice profile) in Teams meeting rooms.
ms.localizationpriority: medium
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
appliesto: 
  - Microsoft Teams
---

# Manage voice recognition technology controls for an Intelligent Speaker

An Intelligent Speaker uses voice profile information to recognize who said what in live transcription. When a Microsoft Teams Rooms on Windows meeting room is equipped with an Intelligent Speaker, live transcription can be used during the meeting. This article explains how you, a tenant admin, control the voice profiling that's used for voice recognition to generate live transcription. You can control to what degree the organization is using voice recognition and the following features:

- Edit the speaker's name in transcripts.
- Change the speaker of a single utterance in the transcript or change the speaker in all the utterances in the transcript (but not on future transcripts).
- Change the speaker identification for the people who are listed in the meeting.
- Remove the identification of one or more utterances identified as that speaker, on every transcript.

## Review Intelligent Speaker requirements

An Intelligent Speaker includes a special seven-microphone array. The system uses voice profile information to identify voices of up to 10 people in meeting rooms.

The following items are Intelligent Speaker requirements:

- The meeting room should have a maximum of 10 people present in person.
- The meeting room has an upload link of minimum 7 Mbps.

Epos, Jabra, Sennheiser, and Yealink Intelligent Speakers are supported.

> [!NOTE]
> Intelligent Speaker is available in all countries and regions. See [Supported locales](#supported-locales) for a list of the locales currently supported for biometric enrollment and in-meeting transcription.

## Set up an Intelligent Speaker

An Intelligent Speaker connects directly using USB to the Teams Rooms console or compute module.

> [!NOTE]
> We don't support an Intelligent Speaker connected to Logitech Surface Pro Microsoft Teams Rooms. There is a known issue that Teams Rooms can't recognize the Intelligent Speaker through the dock.

An Intelligent Speaker that is of a speakerphone design should be placed at least 8 inches (20 cm) away from walls and large objects, such as laptops. If the Intelligent Speaker USB cable isn't long enough for your setup, use cable extenders.

1. Sign in to the console as administrator.
2. Set the Teams device settings to match the Intelligent Speaker microphone and speaker.
   You can also do this through the Microsoft Teams admin center (TAC) portal instead of at the room console.

   The diagram shows how the Intelligent Speaker is connected to the device if the device includes a data box.

   ![The Intelligent Speaker setup with the speaker, the power and data box.One line goes to the USB port of the console, and the other line goes to power.](../media/intelligent-speakers1.png)

   The diagram shows how the Intelligent Speaker is connected to the device if the device doesn't include a data box.

   ![The Intelligent Speaker setup with the speaker connecting directly to the console.](../media/intelligent-speakers2.png)

> [!NOTE]
> EPOS and Yealink devices should have "EPOS" or "Yealink" prefix and contain "UAC2_RENDER" in the speaker name and "UAC2_TEAMS" in the microphone name. If you don't find these microphone and speaker names in the dropdown menu, restart the Intelligent Speaker device.
>
> The Jabra Panacast 50 connects directly to the Microsoft Teams Rooms compute module and not the center of table console. For the Jabra PanaCast 50, make sure you set the Playback Device Type to Microsoft Teams Rooms device. After restarting the Jabra PanaCast 50 you should see devices with "UAC2_RENDER" in the speaker name and "UAC2_TEAMS" in the microphone name.

## Enable an Intelligent Speaker user recognition

Voice profile data can be used in any meeting with an Intelligent Speaker. See [Teams meetings policies](../meetings-policies-recording-and-transcription.md#transcription) and the [PowerShell meeting cmdlets](/powershell/module/skype/set-csteamsmeetingpolicy) for information on the meeting settings.

> [!NOTE]
> If your voice profile isn't available under the *Recognition* tab in Settings and you aren't being attributed in transcriptions, re-enroll your Voice Profile.

The voice profile data of the user is created when the policy is set to distinguish or a non-meeting invitee walks in during the meeting. The voice profile data is dismissed at the end of the meeting.

The following are the required policies to set an Intelligent Speaker and user recognition.

|Policy|Description|Values and Behavior|
|-|-|-|
|enrollUserOverride|Use to set voice profile capture, or enrollment, in Teams settings for a tenant. |**Disabled**<br><ul><li> Users who have never enrolled can't view, enroll, or re-enroll.<li>The entry point to the enrollment flow will be hidden.<li>If users select a link to the enrollment page, they'll see a message that states this feature isn't enabled for their organization.  <li>Users who have enrolled can view and remove their voice profile in the Teams settings. Once they remove their voice profile, they won't be able to view, access, or complete the enrollment flow.</li></ul><br>**Enabled**<br><ul><li> Users can view, access, and complete the enrollment flow.<li>The entry point will show on Teams settings page under the **Recognition** tab.</li></ul>|
|roomAttributeUserOverride|Control the voice-based user identification in meeting rooms. This setting is required for Teams Rooms accounts.| **Off**<br><ul><li>The Teams Rooms device won't send audio stream-saving bandwidth from the room. <li>Meeting room users won't be attributed or distinguished, and their voice signatures won't be retrieved or used at all.<li>Meeting room users are unknown.</li></ul> <br>**Attribute**<br><ul><li>Rooms users will be attributed based on their enrollment status.<li>Users who are enrolled are shown with their name in the transcription.  <li>Users who aren't enrolled show as Speaker \<n>.<li>The Teams Rooms device will send seven audio streams from the room.</ul> <br>**Distinguish**<br> <ul><li>Rooms users will be distinguished and separated as speaker 1, speaker 2, ....speaker \<n> in the transcription.</li><li>Irrespective of enrollment status of the user, their name will not show in the transcription.</li><li>The Teams Rooms device will send seven audio streams from the room.</li></ul>
|AllowTranscription|Required for user and Teams rooms accounts.|**True** and **False**|
||||

In the Teams admin center, set the **Transcription** policy. Settings are **Off** by default.

![the admin center with meeting policies highlighted and Allow transcription selected.](../media/allow-transcription1.png)
  
> [!NOTE]
> After a policy is assigned, they can take up to 48 hours to take effect. To get the policy to take effect sooner, accounts must be signed out and signed back in.

## Frequently asked questions (FAQ)

**Where is the voice profile data stored?**

Voice profile data is stored in Office 365 cloud with user content.

**What is the retention timeline and policy?**

General retention policy is stated in the [Data retention overview](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview). In addition, a user's voice profile data will be deleted after 1 year if the user isn't invited to any meetings with an Intelligent Speaker within that 1-year period. Data isn't used in any meetings for existing employees. If an employee has left the company, voice profile data is considered user content and is treated as such per Office 365 data retention policy described in the [Data retention overview](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

**Is voice profile data used across Microsoft services?**

No, voice profile data is only used for the purpose for which the user has provided consent. Microsoft will not use the voice profile data except within Teams voice recognition scenarios.

**Is my voice profile data used when I join a meeting in another organization?**

No only in meetings organized by a user in your organization.

**How can I export my voice profile?**

Your IT admin can export your audio data at any time.

## Supported locales

The following enrollment and in-meeting transcription locales are supported in all countries and regions.

### Enrollment locales

End-users can enroll their voices for recognition in the following locales:

| Language | Country/Region | Culture ID |
|:-----|:-----|:-----|
|Arabic  |Saudi Arabia |ar-SA  |
|Chinese  |China |zh-CN  |
|Chinese  |Taiwan |zh-TW  |
|Danish  |Denmark |da-DK  |
|Dutch  |Netherlands |nl-NL  |
|English  |Australia |en-AU  |
|English  |Canada  |en-CA |
|English  |India  |en-IN  |
|English  |New Zealand  |en-NZ  |
|English  |United Kingdom  |en-GB  |
|English  |United States  |en-US  |
|Finnish  |Finland  |fi-FI  |
|French  |Canada |fr-CA  |
|French  |France |fr-FR  |
|Italian  |Italy |it-IT  |
|Japanese  |Japan |ja-JP  |
|Norwegian  |Norway |nb-NO  |
|Polish  |Poland |pl-PL  |
|Portuguese      |Brazil |pt-BR  |
|Russian  |Russia |ru-RU  |
|Swedish  |Sweden |sv-SE  |
|Spanish  |Mexico  |es-MX  |
|Spanish  |Spain  |es-ES  |

### In-meeting transcription locales

Once an end-user enrolls, their voice can be recognized during meetings and identified in the transcription when the meeting is set to one of the following locales:

| Language | Country/Region | Culture ID |
|:-----|:-----|:-----|
|Chinese (Simplified)  |China  |zh-CN  |
|English  |Australia |en-AU  |
|English  |Canada  |en-CA |
|English  |India  |en-IN  |
|English  |New Zealand  |en-NZ  |
|English  |United Kingdom  |en-GB  |
|English  |United States  |en-US  |
|French  |Canada  |fr-CA  |
|French  |France  |fr-FR  |
|German  |Germany  |de-DE  |
|Italian  |Italy  | it-IT |
|Japanese  |Japan  |ja-JP  |
|Korean  |Korea  |ko-KR  |
|Portuguese  |Brazil  |pt-BR  |
|Spanish  |Mexico  |es-MX  |
|Spanish  |Spain  |es-ES  |

## Related topics

[Support article: Use Intelligent Speakers to Identify in-room participants](https://support.microsoft.com/office/use-teams-intelligent-speakers-to-identify-in-room-participants-in-meeting-transcription-a075d6c0-30b3-44b9-b218-556a87fadc00)
