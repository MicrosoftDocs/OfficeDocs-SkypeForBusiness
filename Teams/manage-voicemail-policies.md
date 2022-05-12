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

This setting controls whether the Cloud Voicemail service will generate a text transciption of the recorded voicemail and include it in the voicemail message. The transcription will be done based on the language detected in the recorded voicemail.

### Transcription translation

This setting controls whether the Cloud Voicemail service will translate the transcription of the recorded voicemail. The translation will be attempted into the
preferred language of the voicemail receiver.

### Transcription profanity masking

This setting controls whether the Cloud Voicemail service will mask profanity found in the transcription of the voicemail.

### Maximum recording duration

The maximum recording length controls the maximum time a voicemail can be recorded. The default is 5 minutes.

### Call answering rules

This setting controls whether the user is allowed to configure voicemail call answering rules in Microsoft Teams.

### Dual language system prompts

By default, the voicemail system prompts are presented to callers in the language selected by the user when setting up their voicemail. If there is a business 
requirement to have the voicemail system prompts presented in two languages, a primary and secondary language can be set and they may not be the same.

### Share data for service improvements

Specifies whether voicemail and transcription data is shared with the service for training and improving accuracy. If set to false, voicemail data will not be shared, regardless of user choice.


> [!IMPORTANT]
> The voicemail service in Microsoft 365 and Office 365 caches voicemail policies and updates the cache every 6 hours. So, policy changes that you make can take up to 6 hours to be applied.

## Related articles

[New-CsOnlineVoicemailPolicy](/powershell/module/skype/new-csonlinevoicemailpolicy)

[Set-CsOnlineVoicemailPolicy](/powershell/module/skype/set-csonlinevoicemailpolicy)

[Get-CsOnlineVoicemailPolicy](/powershell/module/skype/get-csonlinevoicemailpolicy)

[Grant-CsOnlineVoicemailPolicy](/powershell/module/skype/grant-csonlinevoicemailpolicy)

[Remove-CsOnlineVoicemailPolicy](/powershell/module/skype/remove-csonlinevoicemailpolicy)
