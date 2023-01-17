---
title: Manage meeting policies for recording and transcription
author: mkbond007
ms.author: mabond
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: jastark
audience: admin
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.recordingandtranscription
description: Learn to manage meeting policy settings in Teams for recording and transcription.
---

# Meeting policy settings for recording & transcription

This article describes the meeting policy settings specific to recording and transcription in a Teams meeting. These settings can be found in the Team admin center under **Meetings** > **Meeting policies**.

## Transcription

This is a combination of a per-organizer and per-user policy. This setting controls whether captions and transcription features are available during playback of meeting recordings. The person who started the recording needs this setting turned on for these features to work with their recording.

Turning this setting on creates a copy of the transcript that is stored with the meeting recording which enables **Search**, **CC**, and **transcripts** on the meeting recording.

## Cloud recording

This setting is a combination of a per-organizer and per-user policy and controls whether the meetings can be recorded. The recording can be started by the meeting organizer or by another meeting participant if the policy setting is turned on for the participant and if they're an authenticated user from the same organization.

People outside your organization, such as federated and anonymous users, can't start the recording. Guests can't start or stop the recording.

![Screenshot showing recording options](media/meeting-policies-recording.png)

Let's look at the following example.

| User                 | Meeting policy         | Allow cloud recording |
|----------------------|------------------------|-----------------------|
| Daniela              | Global                 | Off                   |
| Amanda               | Location1MeetingPolicy | On                    |
| John (external) | Not applicable         | Not applicable        |

- Meetings organized by Daniela can't be recorded.
- Amanda can't record meetings organized by Daniela.
- Meetings organized by Amanda can be recorded.
- Daniela can't record meetings organized by Amanda.
- John can't record meetings organized by Amanda.

To learn more about cloud meeting recording, see [Teams cloud meeting recording](cloud-recording.md).

## Meetings automatically expire

This setting controls whether or not meeting recordings automatically expire. After turning on this setting, you'll get the option to set a default expiration time, measured in days.

:::image type="content" source="media/meeting-expiration-policy.jpg" alt-text="Screenshot from Teams admin center of automatic meeting expiration setting.":::

This setting provides you with a simple tool that reduces the amount of storage older recordings use. The OneDrive and SharePoint system will monitor the expiration set on all meeting recordings and will automatically move recordings to the recycle bin on their expiration date.

### Default expiration time

All newly created meeting recordings will have a default expiration of 120 days; all recordings created after this feature was turned on will be deleted 120 days after their creation date.

> [!NOTE]
> The maximum default expiration time for A1 users is 30 days.

#### Changing default expiration time

Admins can edit the Default expiration time setting in PowerShell or the Teams admin center. Any changes will only affect newly created meeting recordings from that point forward; they won’t impact any recordings created before that date.

Admins can’t change the expiration time on existing meeting recordings. This is done to protect the decision of the user that owns the recording. Both meetings and calls can be controlled by this setting.

The expiration value is an integer for days.  This can be set as follows:

- Minimum value: **1**
- Maximum value: **99999**
- You can also set the expiration time to **-1** in PowerShell so the recordings never expire.

Example PowerShell command:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -NewMeetingRecordingExpirationDays 50
```

### Compliance

You shouldn’t rely on meeting expiration settings for legal protection since end users can modify the expiration date of any recordings they control.

#### Recording expiration settings and Microsoft 365 retention policies in Microsoft Purview

File retention takes precedence over file deletion. A Teams meeting recording with a Purview retention policy cannot be deleted by a Teams meeting recording expiration policy until after the retention period is completed. For example, if you have a Purview retention policy that says a file will be kept for five years and a Teams meeting recording expiration policy set for 60 days, the Teams meeting recording expiration policy will permanently delete the recording after five years.

If you have a Teams meeting recording expiration policy and Purview deletion policy with different deletion dates, the file will be deleted at the earliest of the two dates. For example, if you have a Purview deletion policy that says a file will be deleted after one year and a Teams meeting recording expiration set for 120 days, the Teams meeting recording expiration policy will delete the file after 120 days.

Users can manually delete their recordings prior to the expiration date unless there is a Purview retention policy that prevents it. If a recording that’s still in the retention period is manually deleted by a user, the recording will be held in the Preservation Hold library. However, the recording will show as deleted to the end user. To find out more, see [Learn about retention for SharePoint and OneDrive](/microsoft-365/compliance/retention-policies-sharepoint#how-retention-works-for-sharepoint-and-onedrive).

### Deletion of recordings

The recording is usually deleted within a day after the expiration date but in rare instances could take as long as five days. The file owner will receive an email notification when the recording expires and will be directed to the recycle bin to recover the recording.

> [!NOTE]
> On the expiration date, the recording is moved into the recycle bin and the expiration date field is cleared. If you recover the recording from the recycle bin, it won’t be deleted by this feature again because the expiration date has been cleared.

### Expiration of migrated recordings from Stream (Classic)

Migrated recordings from Stream (Classic) will not come with an expiration set on them. Instead, we encourage admins to only migrate recordings that they want to retain. More details can be found in [the Stream (Classic) migration documentation](/stream/streamnew/stream-classic-to-new-migration-overview).

## Store recordings outside of your country or region

This policy controls whether meeting records can be permanently stored in another country or region. If it's enabled, the recordings can't be migrated. For more information on cloud meetings and where recordings are stored, see [Teams cloud meeting recording](cloud-recording.md).

## Related topics

- [Manage meeting policies in Teams](meeting-policies-overview.md)
- [Assign policies to users in Teams](policy-assignment-overview.md)
- [Cloud meeting recording](cloud-recording.md)
- [Manage who can schedule meetings](manage-who-can-schedule-meetings.md)
