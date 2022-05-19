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
The greetings are played to the caller leaving voicemail and can be the following types:

- System greetings
- Custom greetings recorded by the user being called
- Custom text-to-speech greeting specified on the user being called

The langauge used to play the system greetings is in priority order either the primary and secondary prompt language specified in the online voicemail policy assigned
to the user, the preferred language specified for the user or the default tenant language.

The custom greeting is recorded by the user in the language chosen by the user.

If custom text-to-speech greetings are specified on the user in the online voicemail user settings, the language is the PromptLanguage specified together with the
text-to-speech greetings.

## Transcription
If enabled by online voicemail policy, Cloud Voicemail will try to transcripe the voicemail left by the caller. It will use speech detection to understand the language
used in the audio content and transcribe the content if possible.

## Transcription translation
If enabled by online voicemail policy, Cloud Voicemail will translate the transcriped voicemail. It will translate from the language detected during speech detetction 
and into in priority order either the preferred language specified for the user or the default tenant language.

## Voicemail message
Cloud Voicemail will generate the voicemail message text using a template based on in priority order either the preferred language specified for the user or the
default tenant language.

 **First, read this important info:**
  
- **The languages that are available to you are determined by the location of your organization**. For example, if your organization is located in the United States, you can set the default language to English or Spanish. If your organization is located in Canada, you can choose between English and French. For a list of supported languages in Teams and Skype for Business, see the following:
  - [Microsoft Teams supported languages](languages-for-voicemail-greetings-and-messages.md)
  - [Skype for Business supported languages](/skypeforbusiness/what-is-phone-system-in-office-365/phone-system-voicemail/languages-for-voicemail-greetings-and-messages)

- **Changing languages for individual user's voicemail greeting and voicemail messages.** You can change the preferred language for users, which will change the language of their voicemail greeting and voicemail messages sent to their Outlook mailbox. For more information, see [How to set language and region settings for Microsoft 365 or Office 365](/office365/troubleshoot/access-management/set-language-and-region).

  > [!NOTE]
  > Users can change their own greeting language through their settings after they sign in. For more information, see [Change your display language and time zone in Microsoft 365 for Business](https://support.office.com/article/change-your-display-language-and-time-zone-in-microsoft-365-for-business-6f238bff-5252-441e-b32b-655d5d85d15b?ui=en-US&rs=en-US&ad=US)
  
- **Do you want to record your outgoing voicemail message?** See [Check Skype for Business voicemail and options](https://support.office.com/article/2deea7f8-831f-4e85-a0d4-b34da55945a8). For Microsoft Teams - Users can change their voicemail settings from the [Teams desktop client settings](https://support.office.com/article/manage-your-call-settings-in-teams-456cb611-3477-496f-b31a-6ab752a7595f)

- **Do you want to change the voicemail prompt language?** For Skype for Business - [https://mysettings.lync.com/voicemail](https://mysettings.lync.com/voicemail) and choose a new language under **Prompt Language**. For Microsoft Teams - Users can change their voicemail greeting from the [Teams desktop client settings](https://support.office.com/article/manage-your-call-settings-in-teams-456cb611-3477-496f-b31a-6ab752a7595f)

## Change the system language for everyone in your organization

1. Sign in with your [global administrator](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d) account at [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home).

2. In the Microsoft 365 admin center, choose **Settings** > **Org settings** > **Organization profile**.
3. Choose **Organization information**.
4. Select a language from the **Preferred language** list for everyone in your organization.

5. Choose **Save**.

## Related articles for the admin

- [Phone System and Calling Plans](calling-plan-landing-page.md)

- [Set up Calling Plans](set-up-calling-plans.md)

- [Plan Phone System in Microsoft 365 or Office 365 with on-premises PSTN connectivity in Skype for Business Server](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-phone-system-with-on-premises-pstn-connectivity)

## Related topics

- [Change your display language and time zone in Microsoft 365 or Office 365 for Business](https://support.office.com/article/Change-your-display-language-and-time-zone-in-Office-365-for-Business-6f238bff-5252-441e-b32b-655d5d85d15b)

- [Add a language or set language preferences in Office 2010 and later](https://support.office.com/article/Add-a-language-or-set-language-preferences-in-Office-663d9d94-ca99-4a0d-973e-7c4a6b8a827d))

- [Enable or change a keyboard layout language](https://support.office.com/article/Enable-or-change-a-keyboard-layout-language-1c2242c0-fe15-4bc3-99bc-535de6f4f258)
