---
title: "Manage Voicemail Policies"
author: dstrome
ms.author: dstrome
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.assetid: 9c590873-b014-4df3-9e27-1bb97322a79d
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Phone System
description: "Manage Voicemail Policies for your users."
---

# Setting voicemail policies in your organization

> [!WARNING]
> For Skype for Business customers, disabling voicemail through a Microsoft Teams calling policy might also disable the voicemail service for your Skype for Business users.

## Voicemail organization defaults for all users
- Voicemail transcription is enabled.
- Voicemail transcription profanity masking is disabled.
- The maximum recording duration is set to five minutes.
- Editing call answering rules is enabled.

You can control these defaults by editing the Global voicemail policy using the Teams admin center 

or the [Set-CsOnlineVoicemailPolicy](/powershell/module/skype/Set-CsOnlineVoicemailPolicy) and [Grant-CsOnlineVoicemailPolicy](/powershell/module/skype/Get-CsOnlineVoicemailPolicy) cmdlets. You can also create your own voicemail policy instances using Teams admin center or the [New-CsOnlineVoicemailPolicy](/powershell/module/skype/New-CsOnlineVoicemailPolicy) cmdlet.

Voicemail messages received by users in your organization are transcribed in the region where your Microsoft 365 or Office 365 organization is hosted. The region where your tenant is hosted might not be the same region where the user receiving the voicemail message is located. To view the region where your tenant is hosted, go to the [Organization profile](https://go.microsoft.com/fwlink/p/?linkid=2067339) page and then click **View details** next to **Data location**.

> [!IMPORTANT]
> You can't edit or remove the pre-configured policy instances called TranscriptionDisabled and TranscriptionProfanityMaskingEnabled.

You can manage the transcription settings for your users using voicemail policies. To see all available voicemail policy instances, you can use the [Get-CsOnlineVoicemailPolicy](/powershell/module/skype/Get-CsOnlineVoicemailPolicy) cmdlet.

```PowerShell
PS C:\> Get-CsOnlineVoicemailPolicy


Identity                            : Global
EnableTranscription                 : True
ShareData                           : Defer
EnableTranscriptionProfanityMasking : False
EnableEditingCallAnswerRulesSetting : True
MaximumRecordingLength              : 00:05:00
EnableTranscriptionTranslation      : True
PrimarySystemPromptLanguage         :
SecondarySystemPromptLanguage       :

Identity                            : Tag:Default
EnableTranscription                 : True
ShareData                           : Defer
EnableTranscriptionProfanityMasking : False
EnableEditingCallAnswerRulesSetting : True
MaximumRecordingLength              : 00:05:00
EnableTranscriptionTranslation      : True
PrimarySystemPromptLanguage         :
SecondarySystemPromptLanguage       :

Identity                            : Tag:TranscriptionProfanityMaskingEnabled
EnableTranscription                 : True
ShareData                           : Defer
EnableTranscriptionProfanityMasking : True
EnableEditingCallAnswerRulesSetting : True
MaximumRecordingLength              : 00:05:00
EnableTranscriptionTranslation      : True
PrimarySystemPromptLanguage         :
SecondarySystemPromptLanguage       :

Identity                            : Tag:TranscriptionDisabled
EnableTranscription                 : False
ShareData                           : Defer
EnableTranscriptionProfanityMasking : False
EnableEditingCallAnswerRulesSetting : True
MaximumRecordingLength              : 00:05:00
EnableTranscriptionTranslation      : True
PrimarySystemPromptLanguage         :
SecondarySystemPromptLanguage       :
```
  
## Turning off transcription for your organization

Because the default setting for transcription is on for your organization, you may want to disable it by using [Set-CsOnlineVoicemailPolicy](/powershell/module/skype/Set-CsOnlineVoicemailPolicy). To do this, run:

```PowerShell
Set-CsOnlineVoicemailPolicy -EnableTranscription $false
```

## Turning on transcription profanity masking for your organization

Transcription profanity masking is disabled by default for your organization. If there is a business requirement to enable it, you can enable transcription profanity masking by using [Set-CsOnlineVoicemailPolicy](/powershell/module/skype/Set-CsOnlineVoicemailPolicy). To do this, run:

```PowerShell
Set-CsOnlineVoicemailPolicy -EnableTranscriptionProfanityMasking $true
```

## Changing the recording duration for your organization

The maximum recording length is set to five minutes by default for your organization. If there is a business requirement to increase or decrease the maximum recording length, this can be done by using [Set-CsOnlineVoicemailPolicy](/powershell/module/skype/Set-CsOnlineVoicemailPolicy). For example, to set the maximum recording time to 60 seconds,  run:

```PowerShell
Set-CsOnlineVoicemailPolicy -MaximumRecordingLength ([TimeSpan]::FromSeconds(60))
```

## Dual language system prompts for your organization

By default, the voicemail system prompts are presented to callers in the language selected by the user when setting up their voicemail. If there is a business requirement to have the voicemail system prompts presented in two languages, this can be done by using [Set-CsOnlineVoicemailPolicy](/powershell/module/skype/Set-CsOnlineVoicemailPolicy). A primary and secondary language must be set and may not be the same. To do this, run:

```PowerShell
Set-CsOnlineVoicemailPolicy -PrimarySystemPromptLanguage en-US -SecondarySystemPromptLanguage es-ES
```

## Turning off transcription for a user

User policies are evaluated before the organizational default settings. For example, if voicemail transcription is enabled for all of your users, you can assign a policy to disable transcription for a specific user by using the [Grant-CsOnlineVoicemailPolicy](/powershell/module/skype/Grant-CsOnlineVoicemailPolicy) cmdlet.

To disable transcription for a single user, run:

```PowerShell
Grant-CsOnlineVoicemailPolicy -PolicyName TranscriptionDisabled -Identity sip:amosmar@contoso.com
```

## Turning on transcription profanity masking for a user

To enable transcription profanity masking for a specific user, you can assign a policy to enable transcription profanity masking for a specific user by using the [Grant-CsOnlineVoicemailPolicy](/powershell/module/skype/Grant-CsOnlineVoicemailPolicy) cmdlet.

To enable transcription profanity masking for a single user, run:

```PowerShell
Grant-CsOnlineVoicemailPolicy -PolicyName TranscriptionProfanityMaskingEnabled -Identity sip:amosmar@contoso.com
```

## Changing the recording duration for a user

You must first create a custom voicemail policy using the [New-CsOnlineVoicemailPolicy](/powershell/module/skype/New-CsOnlineVoicemailPolicy) cmdlet. The command shown below creates a per-user online voicemail policy OneMinuteVoicemailPolicy with MaximumRecordingLength set to 60 seconds and other fields set to tenant level global value.

```PowerShell
New-CsOnlineVoicemailPolicy -Identity "OneMinuteVoicemailPolicy" -MaximumRecordingLength ([TimeSpan]::FromSeconds(60))
```

To assign this custom policy to a user, run: 

```PowerShell
Grant-CsOnlineVoicemailPolicy -PolicyName OneMinuteVoicemailPolicy -Identity sip:amosmar@contoso.com
```

## Dual language system prompts for a user

You must first create a custom voicemail policy using the [New-CsOnlineVoicemailPolicy](/powershell/module/skype/New-CsOnlineVoicemailPolicy) cmdlet. The command shown below creates a per-user online voicemail policy enUS-esSP-VoicemailPolicy with the PrimarySystemPromptLanguage set to en-US (English - United States) and the SecondarySystemPromptLanguage set to es-SP (Spanish - Spain).

```PowerShell
New-CsOnlineVoicemailPolicy -Identity "enUS-esES-VoicemailPolicy" -PrimarySystemPromptLanguage en-US -SecondarySystemPromptLanguage es-ES
```

To assign this custom policy to a user, run: 

```PowerShell
Grant-CsOnlineVoicemailPolicy -PolicyName "enUS-esES-VoicemailPolicy" -Identity sip:amosmar@contoso.com
```

> [!IMPORTANT]
> The voicemail service in Microsoft 365 and Office 365 caches voicemail policies and updates the cache every 6 hours. So, policy changes that you make can take up to 6 hours to be applied.
