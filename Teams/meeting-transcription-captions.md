---
title: Configure transcription, translation, and captions for Teams meetings
ms.author: mabond
author: mkbond007
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
ms.reviewer: nakulm
ms.date: 03/13/23
search.appverid: MET150
ms.localizationpriority: high
f1.keywords:
- NOCSH
description: Learn how to configure transcription and caption policies for Teams meetings.
appliesto: 
  - Microsoft Teams
---

# Configure transcription, translation, and captions for Teams meetings

In Microsoft Teams, there's an option for meeting recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and review important discussion items in the transcript.

## Transcription

This setting is a combination of a per-organizer and per-user policy. This setting controls whether captions and transcription features are available during playback of Teams meeting recordings. The person who started the recording needs this setting turned on for these features to work with their recording.

When transcription is turned on, users will have a written copy of the spoken text that is captured in near real time. The live transcription will show the speaker's name, if shared, with a timestamp. After the meeting, users can find the searchable transcription stored with the meeting recording.

> [!NOTE] Transcription for recorded meetings is currently only supported for English (US), English (Canada), English (India), English (UK), English (Australia), English (New Zealand), Arabic (United Arab Emirates), Arabic (Saudi Arabia), Chinese (Simplified, China), Chinese (Traditional, Hong Kong SAR), Chinese (Traditional, Taiwan), Czech (Czechia), Danish (Denmark), Dutch (Belgium), Dutch (Netherlands), French (Canada), French (France), Finnish (Finland), German (Germany), Greek (Greece), Hebrew (Israel), Hindi (India), Hungarian (Hungary), Italian (Italy), Japanese (Japan), Korean (Korea), Norwegian (Norway), Polish (Poland), Portuguese (Brazil), Portuguese (Portugal), Romanian (Romania), Russian (Russia), Slovak (Slovakia), Spanish (Mexico), Spanish (Spain), Swedish (Sweden), Thai (Thailand), Turkish (Turkey), Ukrainian (Ukraine), Vietnamese (Vietnam). The transcription is stored together with the meeting recordings in OneDrive and SharePoint storage.

> [!NOTE] Meeting transcription is not yet available in GCC.

### Use the Teams admin center to turn on or turn off transcription

In the Microsoft Teams admin center, turn on or turn off the **Transcription** setting in the meeting policy. This setting is off by default.

### Use PowerShell to turn on or turn off transcription

Using PowerShell, you can configure the `-AllowTranscription` setting in TeamsMeetingPolicy. To learn more, see [Set-CsTeamsMeetingPolicy](\powershell\module\skype\set-csteamsmeetingpolicy).

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowTranscription $True
```

For information on how your end users can use transcription, read [View live transcription in a Teams meeting](https://support.microsoft.com/office/dc1a8f23-2e20-4684-885e-2152e06a4a8b).

## Live captions

This setting is a per-user policy and applies during a meeting. This setting controls whether the **Turn on live captions** option is available for the user to turn on or turn off live captions in meetings that the user attends.  

|Setting value |Behavior  |
|---------|---------|
|**Off, but organizers and co-organizers can turn them on**     | Live captions aren't automatically turned on for the user during a meeting. The user sees the **Turn on live captions** option in the overflow (**...**) menu to turn them on. This is the default setting. |
|**Off**     | Live captions are disabled for the user during a meeting. The user doesn't have the option to turn them on.          |

Closed captions for Teams meeting recordings will be available during playback only if the user had transcription turned on at the time of recording. Admins must turn on recording transcription via policy to ensure their users have the option to record meetings with transcription.

Captions help create inclusive content for viewers of all abilities. As an owner, you can hide captions on the meeting recording, although the meeting transcript will still be available on Teams unless you delete it there.

Closed captions for the recording video file are linked to the Teams meeting transcript. This link will remain for the lifetime of the file in most cases, but can be broken if the video file is copied within the same OneDrive or SharePoint site, which would result in captions not being available on the copied video file.

For information on how your end users can turn on **Live captions**, read [Use live captions in a teams meeting](https://support.microsoft.com/office/4be2d304-f675-4b57-8347-cbd000a21260). For information on how your end users can do this in live events, read [Use live captions in a live event](https://support.microsoft.com/office/1d6778d4-6c65-4189-ab13-e2d77beb9e2a).

### Live translated captions

> [!NOTE]
> This feature is temporarily available in public preview. After the preview, the meeting organizer must have a Teams Premium license for attendees to use live translated captions.

By default, **Live captions** are displayed in the language that’s spoken during a meeting. **Live translated captions** allow your users to see captions translated into the language they’re most comfortable with.

To enable **Live translated captions**, **Live captions** must be set to **Off, but organizers and co-organizers can turn them on** in the Teams admin center. To turn off **Live translated captions**, set this to **Off**.
