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
description: Practical guidance for deploying features in Teams to record Teams meetings to capture audio, video, and screen sharing activity.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Teams meeting recording

In Microsoft Teams, users can record their Teams meetings and group calls to capture audio, video, and screen sharing activity. There is also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and review important discussion items in the transcript. The recording happens in Microsoft 365 and is saved to OneDrive and SharePoint, so users can share it securely across their organization.

When a meeting is recorded, it’s automatically:

- Uploaded to OneDrive or SharePoint
- Permissioned to the people invited to the meeting
- Linked in the chat for the meeting
- Displayed in the Recordings and Transcripts tab for the meeting in Teams calendar
- Added to various file lists across Microsoft 365: Shared with me, office.com, Recommended, Recent, etc.
- Indexed for Microsoft 365 Search

For detailed information on the change in storing meeting recordings from Microsoft Stream (Classic) to OneDrive and SharePoint, see [Use OneDrive and SharePoint for meeting recordings]().

For live events recording options, see [Live event recording policies in Teams]().

For 1:1 calling recording options, see []().

## Prerequisites for Teams meeting recording

For a Teams user’s meetings to be recorded, OneDrive and SharePoint must be enabled. Users and Team channels must have sufficient storage in OneDrive and SharePoint for meeting recordings to be saved, as the size of a 1-hour recording is 400 MB. In addition, the following prerequisites are required for both the meeting organizer and the person who is initiating the recording:

- User has the **Meeting recording** setting enabled under **Meetings** \> **Meeting policies** \> **Recording & transcription** to record meetings and group calls.
- User is not an anonymous, guest, or federated user in the meeting.
- To enable transcription for a user’s meeting, the Teams meeting policy they are assigned to must have the **Transcription** setting set to true under **Meetings** \> **Meeting policies** \> **Recording & transcription**.
- To enable channel meeting recordings to be saved so channel members can’t edit or download the recordings, the `CSTeamsMeetingPolicy -ChannelRecordingDownload` setting must be set to Block.

> [!IMPORTANT]
> Users won’t need OneDrive or SharePoint enabled if you want users to only record and download the recordings. This will mean that the recordings aren’t stored in OneDrive or SharePoint, but are instead stored in temporary Teams storage with a 21-day limit before it’s deleted. It’s not something that an admin can control, manage, or delete at this time.
>  
> For more [information on how temporary meeting recording storage works](#temp-storage), see below.

## Configure Teams meeting recording policies

This section explains how you can set up and plan for recording Teams meetings via Teams meeting policies.

### Meeting recording

You can use the Microsoft Teams admin center or PowerShell to set a Teams meeting policy to control whether user’s meetings can be recorded. Both the meeting organizer and the recording initiator need to have the recording permissions to record the meeting.

In the Microsoft Teams admin center, turn on or turn off the **Meeting recording** setting under **Meetings** > **Meeting policies**. This setting is turned on by default.

With PowerShell, you configure the `-AllowCloudRecording` setting in TeamsMeetingPolicy. To learn more, see Set-CsTeamsMeetingPolicy.

> [!NOTE] For more information about using Teams roles to configure who has permission to record a meeting, see [Roles in a Teams meeting](https://support.microsoft.com/office/c16fa7d0-1666-4dde-8686-0a0bfe16e019).

> [!NOTE] If an external Teams user that is enabled for Teams policy-based compliance recording joins a meeting or call on your tenant, that meeting/call will be recorded by the other tenant for compliance purposes regardless of **Meeting recording** turned on or off on your tenant. Presenters that are part of the meeting in your tenant are advised to remove the user from the meeting if recordings should not be captured by users from another tenant. For more information about policy based compliance recording on Teams, see Introduction to Teams policy-based recording for calling & meetings.

#### Block or allow download of channel meeting recordings

Using PowerShell, The ChannelRecordingDownload setting in TeamsMeetingPolicy controls if channel meetings are saved to a “Recordings” folder or a “Recordingsonly” folder in the channel. The setting applies to the policy of the user who selects record for the channel meeting. To learn more, see Set-CsTeamsMeetingPolicy.

The two values for this setting are:

- **Allow** — Saves channel meeting recordings to a “Recordings” folder in the channel. The permissions on the recording files will be based off the Channel SharePoint permissions. This is the same as any other file uploaded for the channel. This is the default setting.
- **Block** — Saves channel meeting recordings to a “Recordingsonly” folder in the channel. Channel owners will have full rights on the recordings in this folder, but channel members will have read access without ability to download.

> [!NOTE] The ChannelRecordingDownload setting is only available in the Teams PowerShell module version 2
> 4.1-preview or higher. To download the latest preview version of the module use this command:
> Install-Module -Name MicrosoftTeams -Force -AllowClobber -AllowPrerelease

### Transcription

This setting is a combination of a per-organizer and per-user policy. This setting controls whether captions and transcription features are available during playback of meeting recordings. The person who started the recording needs this setting turned on for these features to work with their recording. Turning this setting on creates a copy of the transcript that is stored with the meeting recording which enables **Search**, **Closed Captions**, and **Transcripts** on the meeting recording.

In the Microsoft Teams admin center, turn on or turn off the **Transcription** setting in the meeting policy. This setting is off by default.

Using PowerShell, you configure the `-AllowTranscription` setting in TeamsMeetingPolicy. To learn more, see Set-CsTeamsMeetingPolicy.

> [!NOTE] Transcription for recorded meetings is currently only supported for English (US), English (Canada), English (India), English (UK), English (Australia), English (New Zealand), Arabic (United Arab Emirates), Arabic (Saudi Arabia), Chinese (Simplified, China), Chinese (Traditional, Hong Kong SAR), Chinese (Traditional, Taiwan), Czech (Czechia), Danish (Denmark), Dutch (Belgium), Dutch (Netherlands), French (Canada), French (France), Finnish (Finland), German (Germany), Greek (Greece), Hebrew (Israel), Hindi (India), Hungarian (Hungary), Italian (Italy), Japanese (Japan), Korean (Korea), Norwegian (Norway), Polish (Poland), Portuguese (Brazil), Portuguese (Portugal), Romanian (Romania), Russian (Russia), Slovak (Slovakia), Spanish (Mexico), Spanish (Spain), Swedish (Sweden), Thai (Thailand), Turkish (Turkey), Ukrainian (Ukraine), Vietnamese (Vietnam). The transcription is stored together with the meeting recordings in OneDrive and SharePoint storage.

#### Closed captions for recordings

Closed captions for Teams meeting recordings will be available during playback only if the user had transcription turned on at the time of recording. Admins must turn on recording transcription via policy to ensure their users have the option to record meetings with transcription.

Captions help create inclusive content for viewers of all abilities. As an owner, you can hide captions on the meeting recording, although the meeting transcript will still be available on Teams unless you delete it there.

Closed captions for the recording video file are linked to the Teams meeting transcript. This link will remain for the lifetime of the file in most cases, but can be broken if the video file is copied within the same OneDrive or SharePoint site, which would result in captions not being available on the copied video file.

Any future changes to the link between the transcript in Teams and the recording will be clarified here and in message center notifications. If we make any changes in the future, we will ensure recording files less than 60-days old display the transcript from the meeting as captions.

> [!NOTE] Meeting transcription is not yet available in GCC.

### Meetings automatically expire

This setting is a combination of a per-organizer and per-user policy and controls whether the meetings can be recorded. The recording can be started by the meeting organizer or by another meeting participant if the policy setting is turned on for the participant and if they're an authenticated user from the same organization.

People outside your organization, such as federated and anonymous users, can't start the recording. Guests can't start or stop the recording.

This setting provides you with a simple tool that reduces the amount of storage older recordings use. The OneDrive and SharePoint system will monitor the expiration set on all meeting recordings and will automatically move recordings to the recycle bin on their expiration date.

You can turn off the **Meetings automatically expire** setting in the Teams admin center, under **Meetings** > **Meeting policies** > **Recording & transcription**.

#### Default expiration time

This setting controls whether or not meeting recordings automatically expire. After turning on **Meetings automatically expire**, you'll get the option to set the **Default expiration time**, measured in days. Meeting recordings have a default expiration time of 120 days.

Any changes to this setting will only affect newly created meeting recordings from that point forward; they won’t impact any recordings created before that date.

Admins can’t change the expiration time on existing meeting recordings. This is done to protect the decision of the user that owns the recording. Both meetings and calls can be controlled by this setting.

The expiration value is an integer for days. This can be set as follows:

- Minimum value: 1
- Maximum value: 99999
- You can also set the expiration time to -1 in PowerShell so the recordings never expire.

To change the expiration time to 50 days, run this script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -NewMeetingRecordingExpirationDays 50
```

> [!NOTE] The maximum default expiration time for A1 users is 30 days.

#### Compliance

You shouldn’t rely on meeting expiration settings for legal protection since end users can modify the expiration date of any recordings they control.

##### Recording expiration settings and Microsoft 365 retention policies in Microsoft Purview

File retention takes precedence over file deletion. A Teams meeting recording with a Purview retention policy cannot be deleted by a Teams meeting recording expiration policy until after the retention period is completed. For example, if you have a Purview retention policy that says a file will be kept for five years and a Teams meeting recording expiration policy set for 60 days, the Teams meeting recording expiration policy will permanently delete the recording after five years.

If you have a Teams meeting recording expiration policy and Purview deletion policy with different deletion dates, the file will be deleted at the earliest of the two dates. For example, if you have a Purview deletion policy that says a file will be deleted after one year and a Teams meeting recording expiration set for 120 days, the Teams meeting recording expiration policy will delete the file after 120 days.

Users can manually delete their recordings prior to the expiration date unless there is a Purview retention policy that prevents it. If a recording that’s still in the retention period is manually deleted by a user, the recording will be held in the Preservation Hold library. However, the recording will show as deleted to the end user. To find out more, see Learn about retention for SharePoint and OneDrive.

#### Deletion of recordings

The recording is usually deleted within a day after the expiration date but in rare instances could take as long as five days. The file owner will receive an email notification when the recording expires and will be directed to the recycle bin to recover the recording.

> [!NOTE] On the expiration date, the recording is moved into the recycle bin and the expiration date field is cleared. If you recover the recording from the recycle bin, it won’t be deleted by this feature again because the expiration date has been cleared.

#### Expiration of migrated recordings from Stream (Classic)

Migrated recordings from Stream (Classic) will not come with an expiration set on them. Instead, we encourage admins to only migrate recordings that they want to retain. More details can be found in the [Use OneDrive for Business and SharePoint or Stream for meeting recordings](tmr-meeting-recording-change.md).

## Permissions and storage

Meeting recordings are stored in OneDrive and SharePoint storage. The location and permissions depend on the type of meeting and the role of the user in the meeting. Users that have full edit rights on the video recording file can change the permissions and share it later with others as needed. The default permissions applied to the recording are listed below.

### Non-Channel meetings

- The recording is stored in a folder named **Recordings** in the OneDrive of the user who clicked record.
    Example: *recorder’s OneDrive*/**Recordings**
- People invited to the meeting, except external participants, will automatically be granted permission to the recording file with view access without ability to download.
- The meeting owner and the person who clicked record will get full edit access with ability to change permissions and share with other people.

### Channel meetings

If the download of channel meeting recordings is allowed:

- The recording is stored in the Teams site documentation library in a folder named **Recordings**.
    Example: *Teams name - Channel name*/**Documents**/**Recordings**
- The user who clicked record has edit rights to the recording.
- Every other member’s permissions are based on the Channel SharePoint permissions.

If the download of channel meeting recordings is blocked:

- The recording is stored in the Teams site documentation library in a folder named **Recordings/View only**.
    Example: *Teams name - Channel name*/**Documents/Recordings/View only**
- Channel owners will have full edit and download rights on the recordings in this folder.
- Channel members will have view-only access without ability to download.

### Temporary storage when unable to upload to OneDrive and SharePoint

If a meeting recording isn’t able to be uploaded to OneDrive and SharePoint, it will temporarily be available for download from Teams for 21 days before it is deleted. This is not something at this point that an admin can control or manage to include the ability to delete it.

Meeting recordings may end up in this temporary storage for the following reasons:

- For non-channel meetings if the user who is recording doesn’t have OneDrive or their OneDrive has reached its storage quota
- For a channel meeting if the SharePoint site has reached its storage quota or the site wasn’t provisioned yet
- If specific OneDrive and SharePoint policies are enabled restricting users from uploading files when not on specific IP ranges, etc.

The recording retention for this is temporary storage is affected by the chat message itself. As such, any deletion of the original chat message for the recording will prevent users from being able to access the recording. There are two scenarios that can affect this:

- **User manually deletes the chat message**—In this scenario, as the original message is gone, users will no longer be able to access the recording and no further downloads will be possible. However, the recording itself may still be retained within Microsoft’s internal systems for a time (not exceeding the original 21-day period).

- **Recording chat message is deleted by chat retention policy**—Temporary storage recordings are directly tied to the chat retention policy. As such, although recordings on Teams temporary storage will by default be retained for 21 days before being deleted, if the chat message is deleted before the 21-day time period, due to chat message retention policies, the recording will also be deleted. There is no way to recover the recording after this.

### Planning for storage

The size of a 1-hour recording is 400 MB. Make sure you understand the capacity required for recorded files and have sufficient storage available in OneDrive and SharePoint. Read Set the default storage space for OneDrive and Manage SharePoint site storage limits to understand the base storage included in the subscription and how to purchase additional storage.

## Manage meeting recordings

Meeting recordings are stored as video files in OneDrive and SharePoint and follow management and governance options available in those platforms. Read SharePoint governance overview for more information.

For non-channel meetings, the recordings are stored in the recorder’s OneDrive, thus handling ownership and retention after an employee leaves will follow the normal OneDrive and SharePoint process.

## Meeting Recording Diagnostic Tools

### User cannot record meetings

If you’re an administrator, you can use the following diagnostic tool to validate that the user is properly configured to record a meeting in Teams:

1. Select **Run Tests** below, which will populate the diagnostic in the Microsoft 365 Admin Center.
    - > [!div class=“nextstepaction”] [Run Tests: Meeting Recording](https://aka.ms/MeetingRecordingDiag)
1. In the Run diagnostic pane, enter the email of the user who cannot record meetings in the **Username or Email** field, and then select **Run Tests**.
1. The tests will return the best next steps to address any tenant or policy configurations to validate that the user is properly configured to record a meeting in Teams.

### Meeting recording is missing

If you’re an administrator, you can use the following diagnostic tool to validate that the meeting recording completed successfully and it was uploaded to OneDrive or Stream, based on the meeting ID and recording start time:

1. Select **Run Tests** below, which will populate the diagnostic in the Microsoft 365 Admin Center.
    - > [!div class=“nextstepaction”] [Run Tests: Missing Meeting Recording](https://aka.ms/MissingRecordingDiag)
1. In the Run diagnostic pane, enter the URL of the meeting in the **URL of the meeting that was recorded** field (usually found in the meeting invitation) as well as the date of the meeting in the **When was the meeting recorded?** field and then select **Run Tests**.
1. The tests will validate that the meeting recording completed successfully and it was uploaded to Stream or OneDrive.

## Related topics
- [Teams PowerShell overview]()
- [Teams policy reference - Meeting]()
