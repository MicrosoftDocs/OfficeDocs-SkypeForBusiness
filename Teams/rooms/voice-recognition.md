---
title: Tenant Administration control for voice recognition (voice profile) in Teams Rooms
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: parisataheri
ms.date: 05/15/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
search.appverid: MET150
ms.localizationpriority: medium
description: Learn about how admins can control for voice recognition (voice profile) in Teams meeting rooms.
---
# Manage voice recognition technology controls for an Intelligent Speaker

This article provides guidance on how admins can enable Teams Rooms for voice recognition and live transcription. As an admin, you have the ability to adjust the extent to which your organization lets users utilize voice recognition and Intelligent Speakers capabilities.

> [!NOTE]
> Intelligent Speaker is available in all countries and regions. See [Supported locales](#in-meeting-transcription-locales) for a list of the locales currently supported for biometric enrollment and in-meeting transcription.

> [!NOTE]
> - Intelligent Speakers are available to customers with Teams Room Pro licenses.​​​​​​​
> - Selected devices under legacy Microsoft Teams Rooms Premium licenses will continue to be supported.
## Optimizing Transcription Precision with Intelligent Speakers

When you have activated Intelligent Speaker for your Microsoft Teams Rooms, the meeting transcript is able to not only distinguish between different speakers in the room, but also identify them and attribute them to the correct person. Intelligent Speaker enables critical use cases for Copilot and intelligent recap.

Speaker recognition is enabled by intelligent speakers certified for Teams. Certified intelligent speakers are designed with multiple microphones to provide high-quality audio, maximize accuracy in recognition and transcription, and boast an industry-leading reduction of what is referred to as 'word error rate'.

That said, we get it – [intelligent speaker certified Hardware](/microsoftteams/rooms/certified-hardware?tabs=Devices) aren't available yet in every Teams Room. That is why we're extending this feature to existing hardware. While we're delighted to extend the capability of speaker recognition to more rooms, it's important to note the quality may not match that of an intelligent speaker certified device. So, it's essential to evaluate the advantages of incorporating an intelligent speaker, especially in crucial spaces where attaining the highest quality transcription and attribution is vital.

## Maintain your identity in meetings optimized for Copilot and meeting recap

The most essential input for Copilot in Teams is the identity of each speaker. Copilot needs a meeting transcript, with attribution for every speaker, to deliver meeting summaries, insights, and action items. In a hybrid meeting, without speaker recognition, the video, and audio feed for people in the room would be attributed to the space (for example, Conference Room 1), not the individuals speaking, making it difficult to query individuals’ contributions, summarize everyone’s perspectives, and tackle those to-do items.

Teams Rooms devices use advanced technology called speaker recognition to analyze the distinct vocal characteristics of each speaker, such as pitch, tone, and speaking style, to create a voiceprint for each participant, akin to a fingerprint for their voice.

With speaker recognition, [Teams Rooms](/microsoftteams/rooms) can identify speakers during live transcription in shared meeting rooms, ensuring clear and precise voice capture for every participant. This allows you to effortlessly track who said what during the meeting through intelligent meeting recap and Copilot.

To enable speaker recognition for your employees, you can set up a voice profile in minutes using the Teams Desktop app. Each person gets a unique voice signature, stored securely in your organization's tenant in the Microsoft Cloud to assure that every contribution is accurately captured in every meeting, enabling Copilot and intelligent meeting recap – and helping you drive your work forward.

:::image type="content" source="../rooms/media/voice-recognition/image.png" alt-text="Screenshot showing a meeting in progress." lightbox="../rooms/media/voice-recognition/image.png":::

## Requirements and recommendations

- Teams Rooms on Windows
- To ensure best precision for the transcript, we suggest limiting the number of in person attendees to a maximum of 10 people.
- People to be identified in the room, need to be enrolled with their voice profile and be invited to the scheduled meeting.
- The current limitation for people invited with voice profile is currently 20.
- To support high-quality audio and video during meetings, we recommend that the meeting room has an upload speed of at least 7 Mbps.

> [!NOTE]
> We are extending intelligent speaker to work with all certified microphones. You can try this out as part of our Public Preview program for Teams Rooms with version 5.0.111.0 or later.

## Enable an Intelligent Speaker user recognition

Voice profile data can be used in any meeting with an Intelligent Speaker. See [Teams meetings policies](/microsoftteams/rooms/voice-and-face-recognition) and the [PowerShell meeting cmdlets](/microsoftteams/teams-powershell-overview) for information on the meeting settings.

```powershell
Set-CsTeamsMeetingPolicy -Identity PolicyName -roomAttributeUserOverride Attribute -AllowTranscription $true
```

> [!NOTE]
> If your voice profile isn't available under the *Recognition* tab in Settings and you aren't being attributed in transcriptions, re-enroll your Voice Profile.

The following are the required policies to set an Intelligent Speaker and user recognition.

|Policy|Description|Values and Behavior|
|-|-|-|
|roomAttributeUserOverride|Control the voice-based user identification in meeting rooms. This setting is required for Teams Rooms accounts.| **Off**<br><ul><li>The Teams Rooms device won't send audio stream-saving bandwidth from the room. <li>Meeting room users won't be attributed or distinguished, and their voice signatures won't be retrieved or used at all.<li>Meeting room users are unknown.</li></ul> <br>**Attribute**<br><ul><li>Rooms users will be attributed based on their enrollment status.<li>Users who are enrolled are shown with their name in the transcription.  <li>Users who aren't enrolled show as Speaker \<n\>.<li>The Teams Rooms device will send seven audio streams from the room.</ul> <br>**Distinguish**<br> <ul><li>Teams Rooms users will be distinguished and separated as speaker 1, speaker 2, ....speaker \<n\> in the transcription.</li><li>Irrespective of enrollment status of the user, their name won't show in the transcription.</li><li>The Teams Rooms device will send seven audio streams from the room.</li></ul>|
|AllowTranscription|Required for user and Teams rooms accounts.|**True** and **False**|

In the Teams admin center, set the **Transcription** policy. Settings are **Off** by default.

> [!NOTE]
> After a policy is assigned, they can take up to 48 hours to take effect. To get the policy to take effect sooner, accounts must be signed out and signed back in.

The following in-meeting transcription locales are supported in all countries and regions.

### In-meeting transcription locales

Once an end-user enrolls, their voice can be recognized during meetings and identified in the transcription when the meeting is set to one of the following languages:  
  
English (US), English (Canada), English (India), English (UK), English (Australia), English (New Zealand), Arabic (Arab Emirates), Arabic (Saudi Arabia), Chinese (Simplified China), Chinese (Traditional, Hong Kong SAR), Chinese (Traditional, Taiwan), Czech (Czechia), Danish (Denmark), Dutch (Belgium), Dutch (Netherlands), French (Canada), French (France), Finnish (Finland), German (Germany), Greek (Greece), Hebrew (Israel), Hindi (India), Hungarian (Hungary), Italian (Italy), Japanese (Japan), Korean (Korea), Norwegian (Norway), Polish (Poland), Portuguese (Brazil), Portuguese (Portugal), Romanian (Romania), Russian (Russia), Slovak (Slovakia), Spanish (Mexico), Spanish (Spain), Swedish (Sweden), Thai (Thailand), Turkish (Turkey), Ukrainian (Ukraine), Vietnamese (Vietnam), Welsh (United Kingdom)

## Frequently asked questions (FAQ)

Please review the [face and voice enrollment](/microsoftteams/rooms/voice-and-face-recognition) document if you have more questions regarding voice profile data usage and storage

## Related topics

[Support article: Use Intelligent Speakers to Identify in-room participants](https://support.microsoft.com/office/use-teams-intelligent-speakers-to-identify-in-room-participants-in-meeting-transcription-a075d6c0-30b3-44b9-b218-556a87fadc00)
