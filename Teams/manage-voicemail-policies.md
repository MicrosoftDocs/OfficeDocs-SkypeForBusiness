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

You can use voicemail policies to control different features related to Cloud Voicemail.

## Voicemail organization defaults for all users
- Voicemail transcription is enabled.
- Voicemail transcription translation is enabled.
- Voicemail transcription profanity masking is disabled.
- The maximum recording duration is set to five minutes.
- Editing call answering rules is enabled.
- Primary and secondary system prompt languages are set to null and the user's voicemail language setting is used.

You can use the global (Org-wide default) policy that's created automatically or create and assign custom policies.

## Create a custom voicemail policy

Follow these steps to create a custom voicemail policy.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Voicemail policies**.
2. Select **Add**.
3. Turn on or turn off the features that you want to use in your voicemail policy.
4. Select **Save**.

## Edit a voicemail policy

Follow these steps to edit an existing voicemail policy.

1. In the left navigation of the Microsoft Teams admin center, select **Voice** > **Voicemail policies**.
2. Click next to the policy that you want to modify, and then select **Edit**.
3. Make the changes that you want, and then click **Save**.

## Assign a custom voicemail policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]


Voicemail messages received by users in your organization are transcribed in the region where your Microsoft 365 or Office 365 organization is hosted. The region where your tenant is hosted might not be the same region where the user receiving the voicemail message is located. To view the region where your tenant is hosted, go to the [Organization profile](https://go.microsoft.com/fwlink/p/?linkid=2067339) page and then click **View details** next to **Data location**.

> [!IMPORTANT]
> You can't edit or remove the pre-configured policy instances called TranscriptionDisabled and TranscriptionProfanityMaskingEnabled.

## Voicemail policy settings
  
### Enable transcription

This setting controls whether the Cloud Voicemail service will generate a text transciption of the recorded voicemail and include it in the voicemail message.

### Transcription translation

This setting controls whether the Cloud Voicemail service will translate the transcription of the recorded voicemail. The translation will be

### Transcription profanity masking

This setting controls whether the Cloud Voicemail service will mask profanity found in the transcription of the voicemail.

### Maximum recording duration

The maximum recording length controls the maximum time a voicemail can be recorded. The default is 5 minutes.

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

## Related articles

[New-CsOnlineVoicemailPolicy](/powershell/module/skype/new-csonlinevoicemailpolicy)

[Set-CsOnlineVoicemailPolicy](/powershell/module/skype/set-csonlinevoicemailpolicy)

[Get-CsOnlineVoicemailPolicy](/powershell/module/skype/get-csonlinevoicemailpolicy)

[Grant-CsOnlineVoicemailPolicy](/powershell/module/skype/grant-csonlinevoicemailpolicy)

[Remove-CsOnlineVoicemailPolicy](/powershell/module/skype/remove-csonlinevoicemailpolicy)
