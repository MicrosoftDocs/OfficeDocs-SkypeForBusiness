---
title: Manage Cloud Voicemail settings
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jenstr
ms.topic: article
ms.assetid: 9c590873-b014-4df3-9e27-1bb97322a79d
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Phone System
description: Manage Voicemail settings for your users.
---

# Manage Cloud Voicemail settings for users

Voicemail settings allow you to configure voicemail settings for individual users.

Before configuring voicemail settings for your users, you should read [Set up Cloud Voicemail](set-up-phone-system-voicemail.md). For information about setting policies for groups of users, see [Manage Voicemail policies](manage-voicemail-policies.md).

The default settings for Cloud Voicemail are:

- Voicemail is enabled.
- The prompt language is set to the user’s preferred language.
- The out-of-office greeting is disabled.
- The out-of-office greeting, when automatic replies are set in Outlook, is disabled.
- The out-of-office greeting, when the calendar in Outlook shows out-of-office, is disabled.
- Sharing of voicemail and transcription data with the service for training and improving accuracy purposes is disabled.
- The call answering rule is set to Regular Voicemail.
- The default greeting prompt overwrite isn't set.
- The default out-of-office greeting prompt overwrite isn't set.
- The transfer target isn't set.


To manage Cloud Voicemail features for your users, you can use the Teams admin center or PowerShell. Your end users can also configure these settings in the Teams client by going to **Settings -> Calls -> Configure Voicemail.**

## Use Teams admin center

In the Teams admin center:

1.	In the left navigation, go to **Users > Manage users** and select the user.

2.	On the user details page, go to the **Voicemail** tab.

3.	Change the settings.

4.	Select **Save**.


## Use PowerShell

You can also use PowerShell to manage voicemail settings as follows:

- To manage Cloud Voicemail settings for individual users, use the  [Set-CsOnlineVoicemailUserSettings](/powershell/module/skype/set-csonlinevoicemailusersettings) cmdlet. 

- To view settings, use the [Get-CsOnlineVoicemailUserSettings](/powershell/module/skype/get-csonlinevoicemailusersettings) cmdlet.

- You can disable Cloud Voicemail for a user by using the [Set-CsOnlineVoicemailUserSettings](/powershell/module/skype/set-csonlinevoicemailusersettings) cmdlet and setting the VoicemailEnabled parameter to $false. 

## Voicemail settings

- **Voicemail enabled** - This setting controls whether Cloud Voicemail is enabled for the user. If the setting is false, Cloud Voicemail service won't be available for the user, and won't record a voicemail for the user.

- **Prompt language** - This setting specifies the language used for the prompts in the Cloud Voicemail. For more information, see [Change the default language for greetings and emails](change-the-default-language-for-greetings-and-emails.md).

- **Greeting settings** - Cloud Voicemail is able to play a specific greeting for when the user is in the office and for when the user is out-of-office. Both greetings can be recorded by the user or a text-to-speech greeting can be used.

  - **Default Greeting Prompt Overwrite** -  specifies the text-to-speech greeting that will be played in case the user hasn't recorded a greeting.

  - **Oof Greeting Enabled** - specifies whether the out-of-office greeting is played in voicemail deposit scenario, no matter Outlook settings.

  - **Oof Greeting Follow Automatic Replies Enabled** -  specifies whether to play out-of-office greeting in voicemail deposit scenario when user set automatic replies in Outlook.

  - **Oof Greeting Follow Calendar Enabled** - specifies whether to play out-of-office greeting in voicemail deposit scenario when user set out-of-office in calendar.

  - **Default Oof Greeting Prompt Overwrite** -  specifies the text-to-speech greeting that will be played in case the user is out-of-office and hasn't recorded an out-of-office  greeting.

- **Call answering rule** - This setting specifies the call answering rule. The rule can be:
  - The service declines the call with no message.
  - Only the relevant greeting (normal or out-of-office) is played.
  - The relevant greeting (normal or out-of-office) is played and the caller is transferred to the specified user or phone number.
  -  The relevant greeting (normal or out-of-office) is played and the caller can leave a voicemail.
  - The relevant greeting (normal or out-of-office) is played, the caller can leave a voicemail and is allowed to press 0 to be transferred to the specified user or phone number.

- **Share data for service improvements** - Specifies whether voicemail and transcription data is shared with the service for training and improving accuracy. If set to false, voicemail data will not be shared, regardless of user choice.

- **Call transfer** - Specifies the user or phone number that the caller is transferred to.


