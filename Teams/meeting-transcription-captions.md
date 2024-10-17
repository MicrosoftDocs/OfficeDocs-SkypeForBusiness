---
title: Admins- Manage transcription and captions for Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
ms.reviewer: richardzhang
ms.date: 4/29/2024
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Learn how to configure transcription and caption policies for Teams meetings.
appliesto: 
  - Microsoft Teams
---

# Admins- Manage transcription and captions for Teams meetings

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

> [!NOTE]
> When organizers turn off Microsoft 365 Copilot in Teams meetings and events, recording and transcription are also turned off. To learn more about Copilot, see [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md).

In Microsoft Teams meetings and events, there's an option for recordings to have automatic transcription. Transcription allows users to play back meeting recordings with closed captions and review important discussion items in the transcript. Transcription and captions help create inclusive content for viewers.

As an admin, you can manage transcription and captions for users in your org.

## Transcription

This setting is a combination of a per-organizer and per-user policy that controls whether captions and transcription features are available during playback of Teams meeting recordings. The person who started the recording needs this setting turned on for these features to work with their recording.

When transcription is turned on, users have a written copy of the spoken text that is captured in near real time. After the meeting, users can find the searchable transcription stored with the meeting recording. If transcription was turned on for the recording, Stream plays the video with the transcript next to the recording, and shows who is speaking and when as the video plays.

If recording is turned on, but transcription is turned off, the recording doesn't have a transcript file stored next to it. Also, when viewing the recording playback in Stream, captions can't be turned on.

The transcription link remains for the lifetime of the file in most cases, but can be broken if the video file is copied within the same OneDrive or SharePoint site. This would result in captions not displaying on the copied video file.

The transcription is [stored together with the meeting recordings in OneDrive and SharePoint storage](https://support.microsoft.com/office/3cb9acb6-05b2-4f59-a50d-7df61123aa20#bkmk_how-captions-and-transcripts-are-stored).

> [!NOTE]
> Transcription for recorded meetings is currently only supported for English (US), English (Canada), English (India), English (UK), English (Australia), English (New Zealand), Arabic (United Arab Emirates), Arabic (Saudi Arabia), Chinese (Simplified, China), Chinese (Traditional, Hong Kong SAR), Chinese (Traditional, Taiwan), Czech (Czechia), Danish (Denmark), Dutch (Belgium), Dutch (Netherlands), French (Canada), French (France), Finnish (Finland), German (Germany), Greek (Greece), Hebrew (Israel), Hindi (India), Hungarian (Hungary), Italian (Italy), Japanese (Japan), Korean (Korea), Norwegian (Norway), Polish (Poland), Portuguese (Brazil), Portuguese (Portugal), Romanian (Romania), Russian (Russia), Slovak (Slovakia), Spanish (Mexico), Spanish (Spain), Swedish (Sweden), Thai (Thailand), Turkish (Türkiye), Ukrainian (Ukraine), Vietnamese (Vietnam), Welsh(United Kingdom).

### Use the Teams admin center to enable or disable transcription

In the Teams admin center, you can enable or disable the **Transcription** setting for your users within a meeting policy located under **Meetings** > **Meeting policies**. This setting is off by default.

### Use PowerShell to enable or disable transcription

You can use the **`-AllowTranscription`** parameter in the[Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet to manage transcription.

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowTranscription $True
```

For information on how your end users can use transcription, read [View live transcription in a Teams meeting](https://support.microsoft.com/office/dc1a8f23-2e20-4684-885e-2152e06a4a8b).

### Live translated transcription

> [!NOTE]
> This feature is temporarily available in public preview. After the preview, the meeting organizer must have a Teams Premium license for attendees to use live translated captions.

By default, transcripts are shown in the language spoken during a meeting or event. Live translated transcription allows your users to translate the meeting or event transcript into the language they're most comfortable with.

To enable **Live translated transcription**, **Transcription** must be set to '**On**' in the corresponding meeting policy in the Teams admin center. To turn off **Live translated transcription**, set **Transcription** to **Off**.

For information on how your end users can turn on live translated captions, read [View live transcription in Microsoft Teams meetings](https://support.microsoft.com/office/view-live-transcription-in-microsoft-teams-meetings-dc1a8f23-2e20-4684-885e-2152e06a4a8b).

## Live captions

Teams can detect what was said in a meeting, webinar, or town hall and present real-time captions. If you turned on the new meeting experience, your users' captions include speaker attribution, so you see not only what's being said, but who's saying it and when.

This setting is a per-user policy and applies during a meeting. This setting controls whether the **Turn on live captions** option is available for the user to turn on or turn off automatically generated live captions in meetings that the user attends. These captions aren't saved alongside the video file.

:::image type="content" alt-text="This screenshot shows the menu initiated by selecting the ellipses icon. The option to Turn on live captions is highlighted." source="media/meeting-policies-live-captions.png" lightbox="media/meeting-policies-live-captions.png":::

|Teams admin center policy option|Parameter value in PowerShell| Behavior|
|---|---|---|
| Off, but organizers and co-organizers can turn them on | DisabledUserOverride| **This value is the default setting.** Live captions aren't automatically turned on for users with this assigned policy during meetings and events. The user sees the **Turn on live captions** option in the overflow (**...**) menu to turn them on. |
| Off | Disabled | Live captions are disabled for users with this assigned policy in meetings and events; this user can't turn them on.|

Users with this policy can turn on live captions during a meeting or event; live captions aren't automatically on.

### Use the Teams admin center to manage live captions

In the Teams admin center, you can turn on or turn off the **Live Captions** setting within a meeting policy located under **Meetings** > **Meeting policies**. This setting is off by default.

### Use PowerShell to manage live captions

You can use the **`-LiveCaptionsEnabledType`** parameter in the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet to manage live captions.

To disable live captions for users with this policy, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -LiveCaptionsEnabledType Disabled
```

To enable live captions for users with this policy, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -LiveCaptionsEnabledType DisabledUserOverride 
```

To learn how your end users can use live captions for meetings and webinars, see [Use live captions in a teams meeting](https://support.microsoft.com/office/4be2d304-f675-4b57-8347-cbd000a21260).

For details on how your organizers can create human-generated captions, see [Use CART captions in a Microsoft Teams meeting](https://support.microsoft.com/office/2dd889e8-32a8-4582-98b8-6c96cf14eb47).

### Live translated captions

Live translated captions allow your users to see captions translated into the language they’re most comfortable with. By default, live captions are displayed in the language spoken during a meeting, webinar, or town hall. For town halls, organizers can pre-select 6 languages and 10 languages with a Teams Premium license, for attendees to use during the event.

To enable **Live translated captions**, **Live captions** must be set to '**Off, but organizers and co-organizers can turn them on**' in the corresponding meeting policy in the Teams admin center. To turn off **Live translated captions**, set **Live captions** to **Off**.

For information on how your end users can use live translated captions, see [Use live translated captions in a teams meeting](https://support.microsoft.com/office/4be2d304-f675-4b57-8347-cbd000a21260).

## Related topics

- [Teams meeting recording](meeting-recording.md)
- [Block the download of Teams meeting recording and transcript files from SharePoint or OneDrive](block-download-meeting-recording.md)
- [Accessibility guide for Microsoft Teams Admins](accessibility-guide-admin.md)
- [Teams policies reference - Meetings](settings-policies-reference.md#meetings)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
- [Delete Exchange Online and OneDrive transcript files for Teams meetings](delete-exchange-online-transcripts.md)
