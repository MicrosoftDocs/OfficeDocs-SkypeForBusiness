---
title: Teams meeting recording
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
ms.reviewer: nakulm
ms.date: 05/19/2023
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
description: Learn how to deploy features in Teams meetings to record audio, video, and screen sharing activity.
---

# Teams meeting recording

**APPLIES TO:** ✔️Meetings ✔️Webinars

In Microsoft Teams, users can record their Teams meetings to capture audio, video, and screen sharing activity. The recording happens in Microsoft 365 and is saved to OneDrive or SharePoint, which must be enabled for the user.

> [!NOTE]
> This setting also affects webinars. Recording for live events is a different setting, which is covered in [Live event recording policies in Teams](teams-live-events/live-events-recording-policies.md).

When a meeting is recorded:

- It's uploaded to OneDrive (private meetings) or SharePoint (channel meetings)
- People invited to the meeting have permissions to the recording (guests and external attendees can view the recording only if it's explicitly shared with them)
- Microsoft Purview compliance features apply to the meeting recording files the same as with other files.
- It's linked in the chat for the meeting
- It's displayed in the Recordings and Transcripts tab for the meeting in Teams calendar
- It's added to various file lists across Microsoft 365: Shared with me, office.com, Recommended, Recent, etc.
- Microsoft 365 Search indexes it

There's also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and review important discussion items in the transcript. For more information about transcription and captions, read [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md).

External participants can't record meetings except in the case of [Teams policy-based compliance recording](teams-recording-policy.md). If an external Teams user that is enabled for compliance recording joins a meeting or call hosted by your organization, that meeting or call will be recorded by the other organization for compliance purposes regardless of the **Meeting recording** setting in your organization. Presenters in that meeting can remove the external participant from the meeting if they don't want the recordings captured by the other organization.

## Allow or prevent users from recording meetings

You can use the Microsoft [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851) or PowerShell to set a Teams meeting policy to control whether users' meetings can be recorded. Both the meeting organizer and the recording initiator need to have recording permissions to record the meeting.

Many users use meetings and calls interchangeably depending on their needs. We recommend you check your call recording policy settings as well. If the settings are different for meetings and calls, it may cause confusion for your users.

# [**Meeting policy**](#tab/meeting-policy)

To allow or prevent meeting recordings
1. In the Microsoft [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851), expand **Meetings**.
1. Select **Meeting policies**.
1. Select the policy that you want to edit.
1. Turn **Meeting recording** On or Off.
1. Select **Save**.

With PowerShell, you configure the `-AllowCloudRecording` parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

# [**Calling policy**](#tab/calling-policy)

To allow or prevent call recordings
1. In the Microsoft [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851), expand **Voice**.
1. Select **Calling policies**.
1. Select the policy that you want to edit.
1. Turn **Cloud recording for calling** On or Off.
1. Select **Save**.

With PowerShell, you configure the `-AllowCloudRecordingForCalls` parameter in [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy).

---

## Block or allow download of channel meeting recordings

Using PowerShell, the `-ChannelRecordingDownload` parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) controls if channel members can download meeting recordings. This is done by controlling which folder recordings are stored in.

The two values for this setting are:

- **Allow** - Saves channel meeting recordings to a “Recordings” folder in the channel. The permissions on the recording files are based off the channel's SharePoint permissions. This is the same as any other file uploaded for the channel. This is the default setting.
- **Block** - Saves channel meeting recordings to a “Recordingsonly” folder in the channel. Channel owners have full rights on the recordings in this folder, but channel members have read access without ability to download.

## Recordings automatically expire

This setting provides you with a simple tool that reduces the amount of storage older recordings use. OneDrive and SharePoint monitor the expiration setting on all meeting recordings and automatically move recordings to the recycle bin on their expiration date.

You can turn off the **Meetings automatically expire** setting in the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851) under **Meetings** > **Meeting policies** > **Recording & transcription**.

### Default expiration time

This setting controls whether or not meeting recordings automatically expire. After turning on **Meetings automatically expire**, you'll get the option to set the **Default expiration time**, measured in days. Meeting recordings have a default expiration time of 120 days.

Any changes to this setting only affect newly created meeting recordings, not existing recordings. Admins can't change the expiration time on existing meeting recordings.

The expiration value is an integer for days that can be set as follows:

- Minimum value: 1
- Maximum value: 99999
- -1 (PowerShell only) so the recordings never expire.

> [!NOTE]
> The maximum default expiration time for A1 users is 30 days.

To set the expiration time using PowerShell, run the following command:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -NewMeetingRecordingExpirationDays <days>
```

### Compliance

You shouldn't rely on meeting expiration settings for legal protection since end users can modify the expiration date of any recordings they control.

#### Recording expiration settings and Microsoft 365 retention policies in Microsoft Purview

File retention takes precedence over file deletion. A Teams meeting recording with a Purview retention policy can't be deleted by a Teams meeting recording expiration policy until after the retention period is completed. For example, if you have a Purview retention policy that says a file will be kept for five years and a Teams meeting recording expiration policy set for 60 days, the Teams meeting recording expiration policy will permanently delete the recording after five years.

If you have a Teams meeting recording expiration policy and Purview deletion policy with different deletion dates, the file is deleted at the earliest of the two dates. For example, if you have a Purview deletion policy that says a file will be deleted after one year and a Teams meeting recording expiration set for 120 days, the Teams meeting recording expiration policy will delete the file after 120 days.

Users can manually delete their recordings prior to the expiration date unless there's a Purview retention policy that prevents it. If a user manually deletes a recording that's still in the retention period, the recording is held in the Preservation Hold library. However, the recording shows as deleted to the end user. To find out more, see [Learn about retention for SharePoint and OneDrive](/microsoft-365/compliance/retention-policies-sharepoint).

### Deletion of recordings

On the expiration date, the recording is moved into the recycle bin and the expiration date field is cleared. If a user recovers a recording from the recycle bin, the meeting expiration setting won't delete it again.

The recording is usually deleted within a day after the expiration date but in rare instances could take as long as five days. The file owner receives an email notification when the recording expires and is directed to the recycle bin if they want to recover the recording.

### Expiration of migrated recordings from Stream (Classic)

Migrated recordings from Stream (Classic) won't come with an expiration set on them. Instead, we encourage admins to only migrate recordings that they want to retain.

## Set a custom privacy policy URL

You can update the Teams recording and transcription privacy policy URL with a custom link for people in your organization in Azure Active Directory. For details, see [Add your organization's privacy info using Azure Active Directory](/azure/active-directory/fundamentals/active-directory-properties-area).

After adding your privacy policy URL, the default Teams meeting recording and transcription privacy statement will be replaced with the URL you provided. (People from outside your organization who join Teams meetings hosted by your organization will still have the default Teams meeting recording and transcription privacy policy.)

## Permissions and storage

Teams meeting recordings are stored in OneDrive and SharePoint storage. The location and permissions depend on the type of meeting and the role of the user in the meeting. Users that have full edit rights on the video recording file can change the permissions and share it later with others as needed.

### Planning for storage

The size of a one-hour recording is 400 MB. Make sure you understand the capacity required for recorded files and have sufficient storage available in OneDrive and SharePoint. Read [Set the default storage space for OneDrive](/sharepoint/set-default-storage-space) and [Manage SharePoint site storage limits](/sharepoint/manage-site-collection-storage-limits) to understand the base storage included in the subscription and how to purchase additional storage.

### Temporary storage when unable to upload to OneDrive and SharePoint

If a meeting recording can't be uploaded to OneDrive and SharePoint, it's temporarily available for download from the meeting chat for 21 days before it's deleted. This may happen if the upload destination has exceeded its quota or has file uploads restricted. If the chat is deleted, then the recording is also deleted.

## Meeting Recording Diagnostic Tools

### User can't record meetings

You can use the following diagnostic tool to validate that the user is properly configured to record a meeting in Teams:

1. Select **Run Tests** to populate the diagnostic in the Microsoft 365 admin center.

   > [!div class="nextstepaction"]
   > [Run Tests: Meeting Recording](https://aka.ms/MeetingRecordingDiag)

1. In the Run diagnostic pane, enter the email of the user who can't record meetings in the **Username or Email** field, and then select **Run Tests**.
1. The tests will return the best next steps to address any tenant or policy configurations to validate that the user is properly configured to record a meeting in Teams.

### Meeting recording is missing

You can use the following diagnostic tool to validate that the meeting recording completed successfully and it was uploaded to OneDrive or SharePoint:

1. Select **Run Tests** to populate the diagnostic in the Microsoft 365 admin center.

   > [!div class="nextstepaction"]
   > [Run Tests: Missing Meeting Recording](https://aka.ms/MissingRecordingDiag)

1. In the Run diagnostic pane, enter the URL of the meeting in the **URL of the meeting that was recorded** field (usually found in the meeting invitation) and the date of the meeting in the **When was the meeting recorded?** field and then select **Run Tests**.
1. The tests validate that the meeting recording completed successfully and it was uploaded to SharePoint or OneDrive.

## Related topics

[Teams policy reference - Meetings](settings-policies-reference.md#meetings)

[Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)

[Roles in a Teams meeting](https://support.microsoft.com/office/c16fa7d0-1666-4dde-8686-0a0bfe16e019)
