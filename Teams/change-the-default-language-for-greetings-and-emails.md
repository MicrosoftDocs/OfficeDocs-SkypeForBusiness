---
title: "Change the default language for greetings and emails"
author: dstrome
ms.author: dstrome
manager: serdars
ms.reviewer: jenstr
ms.topic: article
ms.assetid: 820c3892-1b7e-47d3-ae8d-6e27e7cbcf38
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - M365-collaboration
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Phone System
  - seo-marvel-mar2020
description: Learn how to set up Microsoft Teams and Skype for Business to use another language for your organization's default voicemail greeting.
---

# Change the default language for greetings and emails

Cloud Voicemail uses various language settings to play greetings, generate transcription translations and generate voicemail messages. The language settings can be
specified by default on the tenant level, by policy or individually on a given user.

## Greetings
Greetings are played to the caller leaving voicemail and can be the following types:

- System greetings
- Custom greetings recorded by the user being called
- Custom text-to-speech greeting specified on the user being called

The language used to play the system greetings is, in priority order, either the primary and secondary prompt language specified in the online voicemail policy assigned
to the user, the preferred language specified for the user or the default tenant language.

The custom and out of office greeting are recorded by the user in the language chosen by the user.

If custom text-to-speech greetings are specified for the user either by the user or the tenant administrator, the language used to generate the speech is the
PromptLanguage specified together with the text-to-speech greetings.

The custom text-to-speech greetings are only used, if there are no custom greetings recorded for the user.

## Transcription
If enabled by online voicemail policy for the user being called, Cloud Voicemail will try to transcribe the voicemail left by the caller. It will use speech detection
to understand the language used in the audio content and, if possible, transcribe the content using the detected language.

## Transcription translation
If enabled by online voicemail policy for the user being called, Cloud Voicemail will translate the transcribed voicemail. It will translate from the language detected
during speech detection into, in priority order, either the preferred language specified for the user or the default tenant language.

## Voicemail message template
Cloud Voicemail will generate the voicemail message using a language template based on, in priority order, either the preferred language specified for the user or the
default tenant language.

## Setting the preferred language for a user
You can set the preferred language for a user using PowerShell either in Azure Active Directory or in the on-premises Active Directory. For more information, see [How to set language and region settings for Microsoft 365 or Office 365](/office365/troubleshoot/access-management/set-language-and-region).

Users can change their own preferred language through their settings after they sign in. For more information, see [Change your display language and time zone in Microsoft 365 for Business](https://support.office.com/article/change-your-display-language-and-time-zone-in-microsoft-365-for-business-6f238bff-5252-441e-b32b-655d5d85d15b?ui=en-US&rs=en-US&ad=US)

## Change the system language for everyone in your organization

1. Sign in with your [global administrator](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d) account at [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home).

2. In the Microsoft 365 admin center, choose **Settings** > **Org settings** > **Organization profile**.
3. Choose **Organization information**.
4. Select a language from the **Preferred language** list for everyone in your organization.
5. Choose **Save**.

**The languages that are available to you are determined by the location of your organization**. For example, if your organization is located in the United States, you can set the default language to English or Spanish. If your organization is located in Canada, you can choose between English and French.

## Supported languages in Cloud Voicemail
For a list of supported languages in Cloud Voicemail for Microsoft Teams and Skype for Business, see [Cloud Voicemail supported languages](languages-for-voicemail-greetings-and-messages.md).
  

## Custom greeting recorded by a user
Users can record their own custom and out of office custom greeting. See  [Teams desktop client settings](https://support.office.com/article/manage-your-call-settings-in-teams-456cb611-3477-496f-b31a-6ab752a7595f) and [Check Skype for Business voicemail and options](https://support.office.com/article/2deea7f8-831f-4e85-a0d4-b34da55945a8).

## Custom text-to-speech greeting specified for a user
The tenant administrator can specify the custom text-to-speech greeting and prompt language for a user by using the [Set-CsOnlineVoicemailUserSettings](/powershell/module/skype/set-csonlinevoicemailusersettings) cmdlet.

## Custom text-to-speech greeting specified by a user
Users can specify their own custom text-to-speech greetings and the language used for the greetings. For Microsoft Teams - Users can change their voicemail greeting from the [Teams desktop client settings](https://support.office.com/article/manage-your-call-settings-in-teams-456cb611-3477-496f-b31a-6ab752a7595f). For Skype for Business - [https://mysettings.lync.com/voicemail](https://mysettings.lync.com/voicemail) and choose a new language under **Prompt Language**. 


## Related articles

[Set-CsOnlineVoicemailUserSettings](/powershell/module/skype/set-csonlinevoicemailusersettings)

[Get-CsOnlineVoicemailUserSettings](/powershell/module/skype/get-csonlinevoicemailusersettings)

[Set-CsOnlineVoicemailPolicy](/powershell/module/skype/set-csonlinevoicemailpolicy)

[Get-CsOnlineVoicemailPolicy](/powershell/module/skype/get-csonlinevoicemailpolicy)
