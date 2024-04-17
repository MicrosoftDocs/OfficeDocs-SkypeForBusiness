---
title: Teams meeting recording
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
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

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

In Microsoft Teams, users can record their Teams meetings, webinars, and town halls to capture audio, video, and screen sharing activity. The recording happens in Microsoft 365 and is saved to OneDrive or SharePoint, which must be enabled for the user.

> [!NOTE]
> This setting also affects webinars. Recording for live events is a different setting, which is covered in [Live event recording policies in Teams](teams-live-events/live-events-recording-policies.md).

When a meeting is recorded:

- It gets uploaded to OneDrive (private meetings) or SharePoint (channel meetings)
- People invited to the meeting have permissions to the recording (guests and external attendees can view the recording only if the recording is explicitly shared with them)
- Microsoft Purview compliance features apply to the meeting recording files the same as with other files.
- It's linked in the chat for the meeting
- It's displayed in the Recordings and Transcripts tab for the meeting in Teams calendar
- It's added to various file lists across Microsoft 365: Shared with me, office.com, Recommended, Recent, etc.
- Microsoft 365 Search indexes it

Town halls and webinars follow the same process for recording. However, there are a few key differences:

- In town halls, attendees can't access the recording through the chat.
- Webinars and town halls use video on demand (VOD) to publish recordings.

To learn more about VOD, see [Manage VOD publishing for webinars and town halls](manage-vod-publishing.md).

There's also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and review important discussion items in the transcript. For more information about transcription and captions, read [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md).

External participants can't record meetings except when it's a [Teams policy-based compliance recording](teams-recording-policy.md). If an external Teams user that's enabled for compliance recording joins a meeting or call hosted by your organization, the other organization records that meeting or call for compliance purposes, regardless of the **Meeting recording** setting in your organization. Presenters in that meeting can remove the external participant from the meeting if they don't want the recordings captured by the other organization.

## Allow or prevent users from recording meetings

You can use the Microsoft [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851) or PowerShell to set a Teams meeting policy to control whether users' meetings can be recorded. Both the meeting organizer and the recording initiator need to have recording permissions to record the meeting.

Many users use meetings and calls interchangeably depending on their needs. We recommend that you check your call recording policy settings as well. If the settings are different for meetings and calls, it might cause confusion for your users.

# [**Meeting policy**](#tab/meeting-policy)

To allow or prevent meeting recordings:

1. In the Microsoft [Teams admin center](https://admin.teams.microsoft.com/), expand **Meetings**.
1. Select **Meeting policies**.
1. Select the policy that you want to edit.
1. Turn **Meeting recording** On or Off.
1. Select **Save**.

With PowerShell, you configure the `-AllowCloudRecording` parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy).

# [**Calling policy**](#tab/calling-policy)

To allow or prevent call recordings:

1. In the Microsoft [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851), expand **Voice**.
1. Select **Calling policies**.
1. Select the policy that you want to edit.
1. Turn **Cloud recording for calling** On or Off.
1. Select **Save**.

With PowerShell, you configure the `-AllowCloudRecordingForCalls` parameter in [Set-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy).

For more information on call recording, see [Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md).

---

## Require participant agreement for recording

You can use the Teams admin center or PowerShell to manage whether meetings created by organizers with this assigned policy can require participants to provide explicit consent to be recorded.

When the explicit recording policy is enabled, once the meeting recording starts, all participants are muted, with their cameras and content-share off. When a participant decides to unmute, turn on their camera, or share content, they’re prompted to respond 'Yes' or 'No' to consent to be included in the meeting recording. If an attendee responds 'No' to the prompt, they have a view-only meeting experience. View only attendees can't start recordings for any meetings that require explicit consent.

The consent choice for each attendee is included in the attendance report. If the organizer disables the attendance report, the meeting can't be recorded. Attendees not in the attendance report—due to the admin policy or opting out—have a view-only meeting experience.

Before enabling this policy, make sure you check your chosen policy for the attendance report. To learn more about the attendance report, see [Attendance report for meetings and webinars in Microsoft Teams.](teams-analytics-and-reports/meeting-attendance-report.md)

> [!NOTE]
> The explicit recording consent policy doesn't apply to meetings started with transcription only and without recording.

### Supported and unsupported endpoints

The following user types are auto consented for recording without any participant interaction. They get a recording notification, and their consent data is logged as 'not applicable' or 'auto consent':

- Teams Rooms on Windows
- Teams Rooms on Android
- Third party video conferencing devices via Cloud Video Interop (CVI)
- Third party video conferencing devices connecting via Direct Guest Join (DGJ)
- Meeting participants dialing in using the Public Switched Telephone Network (PSTN) conferencing dial-in

#### Supported endpoints

Explicit recording consent is supported on the following endpoints:

- Teams native Windows
- Teams native Mac
- Teams Web
- Mobile Teams (Android and iOS)

#### Unsupported endpoints

In meetings requiring explicit consent, users joining from unsupported endpoints have the view only experience. Explicit recording consent isn’t supported on the following endpoints, along with any endpoints not listed under supported endpoints:

- Teams Phone devices (including audio conferencing phone devices)
- Teams Displays
- VDI
- CarPlay
- Old version native clients

### Manage explicit recording consent in the Teams admin center

Follow these steps in the Teams admin center to turn explicit recording consent on or off for users or groups in your organization:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Within your chosen policy, navigate to the **Recording & Transcription** section.
6. Toggle the **Require participant agreement for recording** setting **On** or **Off**.
7. Select Save.

### Manage explicit recording consent through PowerShell

Through PowerShell, you can manage explicit recording consent for users or groups in your organization:

The **`-ExplicitRecordingConsent`** parameter in the [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet controls whether meetings created by organizers with this assigned policy require participants to provide explicit consent for recordings.
The following table shows the behaviors of the settings for the **`-ExplicitRecordingConsent`** parameter:

|Setting value| Behavior|
|---------|---------------|
|Enabled| For organizers with this policy, all their meetings require participants to provide explicit consent to be recorded.|
|Disabled| **This setting is the default value.** For organizers with this policy, participants aren't asked for explicit consent to be recorded. All participants are included in recordings from these organizers' meetings. |

To enable **`-ExplicitRecordingConsent`** so that any meeting an organizer with this policy creates requires participants to give explicit consent to be recorded,  run the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -ExplicitRecordingConsent Enabled
```

## Block or allow download of channel meeting recordings

In PowerShell, the `-ChannelRecordingDownload` parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) controls if channel members can download meeting recordings. This is done by controlling which folder recordings are stored in.

The two values for this setting are:

- **Allow** - Saves channel meeting recordings to a 'Recordings' folder in the channel. The permissions on the recording files are based off the channel's SharePoint permissions. This is the same as any other file uploaded for the channel. This is the default setting.
- **Block** - Saves channel meeting recordings to a 'Recordingsonly' folder in the channel. Channel owners have full rights on the recordings in this folder, but channel members have read access without ability to download.

## Recordings automatically expire

This setting provides you with a simple tool that reduces the number of storage older recordings use. OneDrive and SharePoint monitor the expiration setting on all meeting recordings and automatically move recordings to the recycle bin on their expiration date.

You can turn off the **Meetings automatically expire** setting in the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851) under **Meetings** > **Meeting policies** > **Recording & transcription**.

### Default expiration time

This setting controls whether or not meeting recordings automatically expire. After turning on **Meetings automatically expire**, you'll get the option to set the **Default expiration time**, measured in days. Meeting recordings have a default expiration time of 120 days.

Any changes to this setting only affect newly created meeting recordings, not existing recordings. Admins can't change the expiration time on existing meeting recordings.

The expiration value is an integer for days that can be set as follows:

- Minimum value: 1
- Maximum value: 99999
- -1 (PowerShell only) so the recordings never expire

> [!NOTE]
> The maximum default expiration time for A1 users is 30 days.

To set the expiration time using PowerShell, run the following command:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -NewMeetingRecordingExpirationDays <days>
```

### Compliance

You shouldn't rely on meeting expiration settings for legal protection since end users can modify the expiration date of any recordings they control.

#### Recording expiration settings and Microsoft 365 retention policies in Microsoft Purview

File retention takes precedence over file deletion. A Teams meeting recording expiration policy can't delete a Teams meeting recording with a Purview retention policy until after the retention period is completed. For example, if you have a Purview retention policy that says a file will be kept for five years and a Teams meeting recording expiration policy set for 60 days, the Teams meeting recording expiration policy permanently deletes the recording after five years.

If you have a Teams meeting recording expiration policy and Purview deletion policy with different deletion dates, the file is deleted at the earliest of the two dates. For example, if you have a Purview deletion policy that says a file will be deleted after one year and a Teams meeting recording expiration set for 120 days, the Teams meeting recording expiration policy will delete the file after 120 days.

Users can manually delete their recordings before the expiration date unless there's a Purview retention policy that prevents it. If a user manually deletes a recording that's still in the retention period, the recording is held in the Preservation Hold library. However, the recording shows as deleted to the end user. To find out more, see [Learn about retention for SharePoint and OneDrive](/microsoft-365/compliance/retention-policies-sharepoint).

### Deletion of recordings

On the expiration date, the recording is moved into the recycle bin and the expiration date field is cleared. If a user recovers a recording from the recycle bin, the meeting expiration setting doesn't delete it again.

Usually, the recording is deleted within a day after the expiration date but in rare instances could take as long as five days. The file owner receives an email notification when the recording expires and is directed to the recycle bin if they want to recover the recording.

### Expiration of migrated recordings from Stream (Classic)

Migrated recordings from Stream (Classic) don't come with an expiration set on them. Instead, we encourage admins to only migrate recordings that they want to retain.

## Set a custom privacy policy URL

To update the Teams recording and transcription privacy policy URL with a custom link for users in and outside your org, you must use one of the following options:

- The **`-LegalURL`** parameter within the [CsTeamsMeetingConfiguration](/powershell/module/skype/set-csteamsmeetingconfiguration) PowerShell cmdlet.
- The Teams admin center through **Meeting settings** > **LegalURL**. For more information, see [Teams settings and policies reference](settings-policies-reference.md#email-invitation).

If you don't enter a legal URL in Teams meeting settings or PowerShell, we display the Microsoft Entra ID's privacy policy. For more information on Microsoft Entra ID's privacy policy, see [Add your organization's privacy info using Microsoft Entra ID](/entra/fundamentals/properties-area). If there's no Microsoft Entra ID, we display the Microsoft Privacy policy.

After you add your privacy policy URL, your URL replaces the default Teams meeting recording and transcription privacy statement.

## Permissions and storage

Teams meeting recordings are stored in OneDrive and SharePoint storage. The location and permissions depend on the type of meeting and the role of the user in the meeting. Users that have full edit rights on the video recording file can change the permissions and share it later with others as needed.

### Planning for storage

The size of a one-hour recording is 400 MB. Make sure you understand the capacity required for recorded files and have sufficient storage available in OneDrive and SharePoint. Read [Set the default storage space for OneDrive](/sharepoint/set-default-storage-space) and [Manage SharePoint site storage limits](/sharepoint/manage-site-collection-storage-limits) to understand the base storage included in the subscription and how to purchase more storage.

### Temporary storage when unable to upload to OneDrive and SharePoint

If a meeting recording can't be uploaded to OneDrive and SharePoint, it's temporarily available for download from the meeting chat for 21 days before it gets deleted. This might happen if the upload destination exceeds its quota or has file uploads restricted. If the chat is deleted, then the recording is also deleted.

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

- [Teams policy reference - Meetings](settings-policies-reference.md#meetings)

- [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)

- [Roles in a Teams meeting](https://support.microsoft.com/office/c16fa7d0-1666-4dde-8686-0a0bfe16e019)
