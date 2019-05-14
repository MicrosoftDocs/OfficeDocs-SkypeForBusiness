---
title: "Create or delete an announcement in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: a6fd5922-fe46-41ba-94e3-c76b1101a31b
description: "Create or delete announcements for Announcement application in Skype for Business Server Enterprise Voice. This affects how calls to unassigned numbers are handled."
---

# Create or delete an announcement in Skype for Business Server

Create or delete announcements for Announcement application in Skype for Business Server Enterprise Voice. This affects how calls to unassigned numbers are handled.

When you configure announcements, you are really configuring how you want calls to unassigned numbers to be handled. You can play a prompt, which can be an audio file or a text-to-speech (TTS) file, or you can just transfer the call to a specified destination without playing a prompt.

You need to create announcements before you define the unassigned number table. You need to perform this step for all announcements that use an audio prompt, a TTS prompt, or no prompt.

This topic describes how to import and create announcements. For details about assigning announcements in the unassigned number table, see [Configure the Unassigned Number Table](https://technet.microsoft.com/library/eaa01986-e92f-4328-acf6-4e46c4306a04.aspx).

## Create a new announcement for unassigned numbers

To create a new announcement, you need to perform the following steps:

1. For audio prompts, record the audio file by using your favorite audio recording application.

2. For audio prompts, run the **Import-CsAnnouncementFile** cmdlet to import the contents of the audio file to File Store.

3. Run the **New-CsAnnouncement** cmdlet to create and name the announcement. Perform this step to create announcements with an audio prompt, a text-to-speech (TTS) prompt, or no prompt.

    > [!TIP]
    > You might want to create an announcement with no prompt (for example, if you want to transfer calls to a specific destination without playing a message).

4. Assign the new announcement to a number range in the unassigned number table.

### To create a new announcement

1. For audio prompts, create the audio file.

2. Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in **Delegate Setup Permissions**.

3. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

4. For audio prompts, run:

   ```
   Import-CsAnnouncementFile -Parent <service of the Application Server running the Announcement application> -FileName <name for file in File Store> -Content Byte [<contents of file in byte array>]
   ```

5. Run:

   ```
   New-CsAnnouncement -Parent <service of Application Server running the Announcement application, in the form: service:ApplicationServer:<fqdn>> -Name <unique name to be used as destination in unassigned number table> [-AudioFilePrompt <FileName specified in Import-CsAnnouncementFile>] [-TextToSpeechPrompt <text string to be converted to speech>] [-Language <Language for playing the TTS prompt (required for PromptTts)>] [-TargetUri sip:SIPAddress for transferring caller after announcement]
   ```

    For transferring calls to voice mail, type SIPAddress in the format sip:username@domainname;opaque=app:voicemail (for example, sip:bob@contoso.com;opaque=app:voicemail). For transferring calls to a phone number, type SIPAddress in the format sip:number@domainname;user=phone (for example, sip:+ 14255550121@contoso.com;user=phone).

    For example, to specify an audio prompt:

   ```
   $a = Get-Content ".\PromptFile.wav" -ReadCount 0 -Encoding Byte
   Import-CsAnnouncementFile -Parent service:ApplicationServer:pool0@contoso.com -FileName "ChangedNumberMessage.wav" -Content $a
   New-CsAnnouncement -Parent service:ApplicationServer:pool0.contoso.com -Name "Number Changed Announcement" -AudioFilePrompt "ChangedNumberMessage.wav"
   ```

    For example, to specify a TTS prompt:

   ```
   New-CsAnnouncement -Parent service:ApplicationServer:pool0.contoso.com -Name "Help Desk Announcement" -TextToSpeechPrompt "The Help Desk number has changed. Please dial 5550100." -Language "en-US"
   ```

   For more detail about these cmdlets, and to see a list of the language codes to use in the **TextToSpeechPrompt** parameter, see [New-CsAnnouncement](https://docs.microsoft.com/powershell/module/skype/new-csannouncement?view=skype-ps).

## Delete an announcement for unassigned numbers

### To delete an announcement

1. Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in **Delegate Setup Permissions**.

2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

3. List all the announcements in your organization. At the command line, run:

   ```
   Get-CsAnnouncement
   ```

4. In the resulting list, locate the announcement you want to delete, and copy the GUID. Then, at the command line, run:

   ```
   Remove-CsAnnouncement -Identity "<Service:service ID/guid>"
   ```

    For example:

   ```
   Remove-CsAnnouncement -Identity "ApplicationServer:Redmond.contoso.com/1951f734-c80f-4fb2-965d-51807c792b90"
   ```

    > [!NOTE]
    > For details about more options, see [Get-CsAnnouncement](https://docs.microsoft.com/powershell/module/skype/get-csannouncement?view=skype-ps) and [Remove-CsAnnouncement](https://docs.microsoft.com/powershell/module/skype/remove-csannouncement?view=skype-ps).

## See also

[Create or delete an announcement in Skype for Business Server](create-an-announcement.md)

[Import-CsAnnouncementFile](https://docs.microsoft.com/powershell/module/skype/import-csannouncementfile?view=skype-ps)

[New-CsAnnouncement](https://docs.microsoft.com/powershell/module/skype/new-csannouncement?view=skype-ps)

[Remove-CsAnnouncement](https://docs.microsoft.com/powershell/module/skype/remove-csannouncement?view=skype-ps)

[Get-CsAnnouncement](https://docs.microsoft.com/powershell/module/skype/get-csannouncement?view=skype-ps)

