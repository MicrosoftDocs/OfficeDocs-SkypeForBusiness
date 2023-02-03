---
title: Teams meeting recording
ms.author: mabond
author: mkbond007
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - M365-collaboration
  - m365initiative-meetings
  - highpri
ms.reviewer: nakulm
search.appverid: MET150
ms.localizationpriority: high
f1.keywords:
- NOCSH
description: Practical guidance for deploying features in Teams to record Teams meetings and group calls to capture audio, video, and screen sharing activity.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Teams meeting recording

In Microsoft Teams, users can record their Teams meetings and group calls to capture audio, video, and screen sharing activity. There is also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and review important discussion items in the transcript. The recording happens in Microsoft 365 and is saved to OneDrive and SharePoint, so users can share it securely across their organization.

When a meeting is recorded, it's automatically:

- Uploaded to OneDrive or SharePoint
- Permissioned to the people invited to the meeting
- Linked in the chat for the meeting
- Displayed in the Recordings and Transcripts tab for the meeting in Teams calendar
- Added to various file lists across Microsoft 365: Shared with me, office.com, Recommended, Recent, etc.
- Indexed for Microsoft 365 Search

Related: [Teams meeting recording end user documentation](https://support.microsoft.com/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24)

>[!Note]
> The change from using Microsoft Stream (classic) to OneDrive and SharePoint for meeting recordings will automatically happen in August 2021. For detailed information, see [Use OneDrive and SharePoint or Stream for meeting recordings](tmr-meeting-recording-change.md).

> [!NOTE]
> For live events recording options, see [Live event recording policies in Teams](teams-live-events/live-events-recording-policies.md).

## Prerequisites for Teams meeting recording

For a Teams user's meetings to be recorded, OneDrive and SharePoint must be enabled for the tenant. In addition, the following prerequisites are required for both the meeting organizer and the person who is initiating the recording:

- User has sufficient storage in OneDrive for non-channel meeting recordings to be saved.

- The Teams' channel has sufficient storage in SharePoint for channel meeting recordings to be saved.

- User has the **Meeting recording** setting enabled under **Meetings** > **Meeting policies** > **Recording & transcription** to record meetings and group calls.

- User has **Cloud recording for calling** setting enabled under **Voice** > **Calling policies** to record 1:1 calls.

- User is not an anonymous, guest, or federated user in the meeting.

- To enable transcription for a user's meeting, the Teams meeting policy they are assigned to must have the **Transcription** setting set to true under **Meetings** > **Meeting policies** > **Recording & transcription**.

- To enable channel meeting recordings to be saved so channel members can't edit or download the recordings the `CSTeamsMeetingPolicy -ChannelRecordingDownload` setting must be set to Block.

> [!IMPORTANT]
>
> Users won't need OneDrive or SharePoint enabled if you want users to only record and download the recordings. This will mean that the recordings aren't stored in OneDrive or SharePoint, but are instead stored in temporary Teams storage with a 21-day limit before it's deleted. It's not something that an admin can control, manage, or delete at this time.
>
> For more [information on how temporary meeting recording storage works](#temp-storage), see below.  

## Set up Teams meeting recording for users in your organization

This section explains how you can set up and plan for recording Teams meetings via [Teams meeting policies](policy-assignment-overview.md).

### Turn on or turn off meeting recording

You can use the Microsoft Teams admin center or PowerShell to set a Teams meeting policy to control whether user's meetings can be recorded. Both the meeting organizer and the recording initiator need to have the recording permissions to record the meeting. **Meeting recording** is enabled by default.

In the Microsoft Teams admin center, turn on or turn off the **Meeting recording** setting under **Meetings** > **Meeting policies**.

With PowerShell, you configure the AllowCloudRecording setting in TeamsMeetingPolicy. The following PowerShell example turns on Teams meeting recording. To learn more, see [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <PolicyName> -AllowCloudRecording $True
   ```

<a name="bd-channel"></a>

> [!NOTE]
> If a Teams user from an external tenant that is enabled for Teams policy-based compliance recording joins a meeting or call on your tenant, that meeting/call will be recorded by the other tenant for compliance purposes regardless of **Meeting recording** turned on or off on your tenant. Presenters that are part of the meeting in your tenant are advised to remove the user from the meeting if recordings should not be captured by users from another tenant. For more information about policy based compliance recording on Teams, see [Introduction to Teams policy-based recording for calling & meetings](teams-recording-policy.md).

### Block or allow download of channel meeting recordings

Using PowerShell, The ChannelRecordingDownload setting in TeamsMeetingPolicy controls if channel meetings are saved to a "Recordings" folder or a "Recordings\View only" folder in the channel. The setting applies to the policy of the user who selects record for the channel meeting. To learn more, see [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

The two values for this setting are:

- **Allow** — Saves channel meeting recordings to a "Recordings" folder in the channel. The permissions on the recording files will be based off the Channel SharePoint permissions. This is the same as any other file uploaded for the channel. This is the default setting.

- **Block** — Saves channel meeting recordings to a "Recordings\View only" folder in the channel. Channel owners will have full rights on the recordings in this folder, but channel members will have read access without ability to download.

> [!NOTE]
> The ChannelRecordingDownload setting is only available in the Teams PowerShell module version 2.4.1-preview or higher. To download the latest preview version of the module use this command:
>
>```powershell
>Install-Module -Name MicrosoftTeams -Force -AllowClobber -AllowPrerelease
>```

### Transcription

This setting is a combination of a per-organizer and per-user policy. This setting controls whether transcription and caption features are available during playback of meeting recordings. The person who started the recording needs this setting turned on for these features to work with their recording. Turning this setting on creates a copy of the transcript that is stored with the meeting recording which enables Search, Closed Captions, and Transcripts on the meeting recording.

In the Microsoft Teams admin center, turn on or turn off the **Transcription** setting in the meeting policy. This setting is off by default.

Using PowerShell, you configure the AllowTranscription setting in TeamsMeetingPolicy. The following PowerShell example turns on transcription. To learn more, see [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

  ```powershell
  Set-CsTeamsMeetingPolicy -Identity <PolicyName> -AllowTranscription $True
   ```

> [!NOTE]
> That transcription for recorded meetings is currently only supported for English (US), English (Canada), English (India), English (UK), English (Australia), English (New Zealand), Arabic (United Arab Emirates) , Arabic (Saudi Arabia) , Chinese (Simplified, China), Chinese (Traditional, Hong Kong SAR), Chinese (Traditional, Taiwan), Czech (Czechia) , Danish (Denmark), Dutch (Belgium) , Dutch (Netherlands), French (Canada), French (France), Finnish (Finland) , German (Germany), Greek (Greece), Hebrew (Israel) , Hindi (India), Hungarian (Hungary), Italian (Italy), Japanese (Japan), Korean (Korea) , Norwegian (Norway), Polish (Poland) , Portuguese (Brazil), Portuguese (Portugal), Romanian (Romania), Russian (Russia), Slovak (Slovakia), Spanish (Mexico), Spanish (Spain), Swedish (Sweden), Thai (Thailand) , Turkish (Turkey), Ukrainian (Ukraine), Vietnamese (Vietnam). They are stored together with the meeting recordings in OneDrive and SharePoint storage.

#### Closed captions

Closed captions for Teams meeting recordings will be available during playback only if the user had transcription turned on at the time of recording. Admins must turn on recording transcription via policy to ensure their users have the option to record meetings with transcription.

Captions help create inclusive content for viewers of all abilities. As an owner, you can hide captions on the meeting recording, although the meeting transcript will still be available on Teams unless you delete it there.

Closed captions for the recording video file are linked to the Teams meeting transcript. This link will remain for the lifetime of the file in most cases, but can be broken if the video file is copied within the same OneDrive or SharePoint site, which would result in captions not being available on the copied video file.

### Meetings automatically expire



## Permissions and storage

Meeting recordings are stored in OneDrive and SharePoint storage. The location and permissions depend on the type of meeting and the role of the user in the meeting. The default permissions applied to the recording are listed below, users that have full edit rights on the video recording file can change the permissions and share it later with others as needed.

### Non-Channel meetings

- The recording is stored in a folder named **Recordings** in the OneDrive of the user who clicked record.

  Example: *recorder's OneDrive*/**Recordings**

- People invited to the meeting, except external participants, will automatically be granted permission to the recording file with view access without ability to download.

- The meeting owner and the person who clicked record will get full edit access with ability to change permissions and share with other people.

### Channel meetings

If `Set-CsTeamsMeetingPolicy -ChannelRecordingDownload` is set to Allow (default):

- The recording is stored in the Teams site documentation library in a folder named **Recordings**.

  Example: *Teams name - Channel name*/**Documents**/**Recordings**

- The member who clicked record has edit rights to the recording.

- Every other member’s permissions are based on the Channel SharePoint permissions.

If `Set-CsTeamsMeetingPolicy -ChannelRecordingDownload` is set to Block:

- The recording is stored in the Teams site documentation library in a folder named **Recordings/View only**.

  Example: *Teams name - Channel name*/**Documents/Recordings/View only**

- Channel owners will have full edit and download rights on the recordings in this folder.

- Channel members will have view-only access without ability to download.

<a name="temp-storage"></a>

### Temporary storage when unable to upload to OneDrive and SharePoint

If a meeting recording isn't able to be uploaded to OneDrive and SharePoint, it will temporarily be available for download from Teams for 21 days before it is deleted. This is not something at this point that an admin can control or manage to include the ability to delete it.

Meeting recordings may end up in this temporary storage for the following reasons:

- For non-channel meetings if the user who is recording doesn't have OneDrive or their OneDrive has reached its storage quota
- For a channel meeting if the SharePoint site has reached its storage quota or the site wasn't provisioned yet
- If specific OneDrive and SharePoint policies are enabled restricting users from uploading files when not on specific IP ranges, etc.

The recording retention for this is temporary storage is affected by the chat message itself. As such, any deletion of the original chat message for the recording will prevent users from being able to access the recording. There are two scenarios that can affect this:

- **User manually deletes the chat message**—In this scenario, as the original message is gone, users will no longer be able to access the recording and no further downloads will be possible. However, the recording itself may still be retained within Microsoft's internal systems for a time (not exceeding the original 21-day period).

- **Recording chat message is deleted by chat retention policy**—Temporary storage recordings are directly tied to the chat retention policy. As such, although recordings on Teams temporary storage will by default be retained for 21 days before being deleted, if the chat message is deleted before the 21-day time period, due to chat message retention policies, the recording will also be deleted. There is no way to recover the recording after this.

### Planning for storage

The size of a 1-hour recording is 400 MB. Make sure you understand the capacity required for recorded files and have sufficient storage available in OneDrive and SharePoint.  Read [Set the default storage space for OneDrive](/onedrive/set-default-storage-space) and [Manage SharePoint site storage limits](/sharepoint/manage-site-collection-storage-limits) to understand the base storage included in the subscription and how to purchase additional storage.
  
## Manage meeting recordings

Meeting recordings are stored as video files in OneDrive and SharePoint and follow management and governance options available in those platforms. Read [SharePoint governance overview](/sharepoint/governance-overview) for more information.

For non-channel meetings, the recordings are stored in the recorder's OneDrive, thus handling ownership and retention after an employee leaves will follow the normal [OneDrive and SharePoint process](/onedrive/retention-and-deletion#the-onedrive-deletion-process).

Meeting recordings have a Default expiration time of 120 days. You can turn off the Meetings automatically expire setting or change the Default expiration time. Learn more about [meeting recordings automatically expiring](meetings-policies-recording-and-transcription.md#meetings-automatically-expire).

## Closed captions for recordings

Closed captions for Teams meeting recordings will be available during playback only if the user had transcription turned on at the time of recording. Admins must [turn on recording transcription via policy](#meeting-recordings-transcription) to ensure their users have the option to record meetings with transcription.

Captions help create inclusive content for viewers of all abilities. As an owner, you can hide captions on the meeting recording, although the meeting transcript will still be available on Teams unless you delete it there.

Today closed captions for the recording video file are linked to the Teams meeting transcript. This link will remain for the lifetime of the file in most cases, but can be broken if the video file is copied within the same OneDrive or SharePoint site, which would result in captions not being available on the copied video file.

Any future changes to the link between the transcript in Teams and the recording will be clarified here and in message center notifications. If we make any changes in the future, we will ensure recording files less than 60-days old display the transcript from the meeting as captions.

> [!NOTE]
> Meeting transcription is not yet available in GCC.

## Meeting Recording Diagnostic Tools

### User cannot record meetings

If you're an administrator, you can use the following diagnostic tool to validate that the user is properly configured to record a meeting in Teams:

1. Select **Run Tests** below, which will populate the diagnostic in the Microsoft 365 Admin Center.

   > [!div class="nextstepaction"]
   > [Run Tests: Meeting Recording](https://aka.ms/MeetingRecordingDiag)

2. In the Run diagnostic pane, enter the email of the user who cannot record meetings in the **Username or Email** field, and then select **Run Tests**.

3. The tests will return the best next steps to address any tenant or policy configurations to validate that the user is properly configured to record a meeting in Teams.
  
### Meeting record is missing

If you're an administrator, you can use the following diagnostic tool to validate that the meeting recording completed successfully and it was uploaded to Stream or OneDrive, based on the meeting ID and recording start time:

1. Select **Run Tests** below, which will populate the diagnostic in the Microsoft 365 Admin Center.

   > [!div class="nextstepaction"]
   > [Run Tests: Missing Meeting Recording](https://aka.ms/MissingRecordingDiag)

2. In the Run diagnostic pane, enter the URL of the meeting in the **URL of the meeting that was recorded** field (usually found in the meeting invitation) as well as the date of the meeting in the **When was the meeting recorded?** field and then select **Run Tests**.

3. The tests will validate that the meeting recording completed successfully and it was uploaded to Stream or OneDrive.

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
