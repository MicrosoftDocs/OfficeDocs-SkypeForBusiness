---
title: Teams meeting recording storage and permissions in OneDrive and SharePoint
ms.author: wlibebe
author: wlibebe
ms.reviewer: yudma, yujin1, lisma, ritikag
ms.date: 7/19/2024
manager: pamgreen
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn about how meeting recordings are stored in OneDrive and SharePoint, and permissions.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
appliesto: 
  - Microsoft Teams
---

# Teams meeting recording storage and permissions in OneDrive and SharePoint

When users in your org record Teams meetings, the recording is stored in either OneDrive and SharePoint. Depending on where your users access the file, the recording plays on the video player in OneDrive or SharePoint. This article helps you, as an admin, understand recording storage and permissions for OneDrive and Sharepoint.

To learn about your recording policies, see [Teams meeting recording](meeting-recording.md). To learn how to block the download of Teams meeting recording files from SharePoint or OneDrive, see [Block the download of Teams meeting recording files from SharePoint or OneDrive](block-download-meeting-recording.md).

## Recording storage

### Meetings and events

For **meetings, webinars, and town halls**, by default, all recording files are saved to the organizer's OneDrive **Recordings** folder. The **`-MeetingRecordingOwnership`** parameter within the PowerShell [**CsTeamsRecordingRolloutPolicy**](/powershell/module/teams/set-csteamsrecordingrolloutpolicy) cmdlet controls whether the recording is saved to the organizer's or recording initiator's OneDrive, overriding the default storage settings. This policy applies to the following meeting and event types:

- Automatically recorded meetings
- Delegate-created meetings
- Manually recorded meetings
- Meet now meetings
- Meetings scheduled in Outlook
- Meetings scheduled in the Teams client
- Recurring meetings
- Town halls
- Webinars

If **`-MeetingRecordingOwnership`** is set to `RecordingInitiator`, when organizers with this policy create meetings and events, the recording saves to the OneDrive of the user who starts the recording. If the recording initiator doesn't have a OneDrive, the recording is temporarily saved to async media storage.

If **`-MeetingRecordingOwnership`** is set to `MeetingOrganizer`, when organizers with this policy create meetings and events, the recording saves to organizer's OneDrive, even if the organizer didn't attend the meeting or event. Co-organizers have the same editing permissions as organizers for recording files. To understand what happens if an organizer doesn't have a OneDrive account, see the **Recording storage for organizers without OneDrive accounts** section in this article.

#### Delegate-created meetings

For meetings in which an organizer appoints a **delegate** who has permission to act on the organizer's behalf, all recording files are automatically saved to the organizer's **Recordings** folder in OneDrive. When delegates are added as co-organizers, they have the same editing permissions as organizers for recording files.

### 1:1 and group calls

For 1-1 call and group calls, recording files go to the OneDrive account of the user who selected **Record**.

### Channel meetings

For **Channel meetings**, the recording is stored in the SharePoint Teams site documentation library in a folder named **Recordings**. For example: *Teams name - Channel name*/**Documents**/**Recordings**.

### Shared accounts

For **shared accounts**, if the shared account has OneDrive, the recording is uploaded there. However, since shared accounts typically don’t have OneDrive, the recordings are uploaded to the organizer’s OneDrive in those cases. To understand what happens if an organizer doesn't have a OneDrive account, see the **Recording storage for organizers without OneDrive accounts** section in this article.

For details on shared accounts, see [About shared mailboxes - Microsoft 365 admin](/microsoft-365/admin/email/about-shared-mailboxes).

### Microsoft Teams Rooms meetings

WHICH VERSION IS CORRECT?

**VERSION 1:** For **Microsoft Teams Rooms meetings(MTR)**, when an organizer creates a meeting using the meet-now button in MTR, the room itself becomes the meeting organizer, and the recording is stored in the MTR’s OneDrive account. However, none of the meeting participants have full permissions to the file. If you want meeting participants to have full permissions to the recording file, avoid assigning OneDrive storage to an MTR.

When an an MTR attends a meeting that another user organizes, the MTR can't initiate the recording, but other meeting participants can.

When the MTR doesn't have a OneDrive account, the recording gets saved to the organizer's OneDrive. For details on what happens if an organizer doesn't have a OneDrive account, see the **Recording storage for organizers without OneDrive accounts** section in this article.

**VERSION 2:** In Microsoft Teams Rooms, recording and transcription initiation isn't yet available.

To learn more about Microsoft Teams Rooms meetings, see [Microsoft Teams Rooms (Windows)](https://support.microsoft.com/office/microsoft-teams-rooms-windows-e667f40e-5aab-40c1-bd68-611fe0002ba2).

### Recording storage for organizers without OneDrive accounts

When the organizer doesn’t have a OneDrive account, here's what happens, in order, to the meeting recording:
  
1. The recording is saved to the co-organizer's OneDrive, while the meeting or event organizer retains permissions to edit and share the recording. When there are multiple co-organizers, the recording saves to the co-organizers' OneDrive, ordered by the first number of each co-organizer's Entra object ID. To find the object IDs for users in your org, see [Locate important IDs for a user](/partner-center/account-settings/find-ids-and-domain-names#find-the-user-object-id).

   Let's take a look at the following example with three co-organizers:

   :::image type="content" source="media/objectid-co-organizer-recording-small.png" alt-text="Screenshot of the object IDs for three organizers. The first organizer's object ID starts with the letter one, the second character in the second organizer's object ID is the number 5, and the second character in the third organizer's object ID is the number 3." lightbox="media/objectid-co-organizer-recording-expand.png":::

   In this example, the recording is saved to co-organizer 1’s OneDrive account. If co-organizer 1 doesn’t have a OneDrive account, the recording is saved to co-organizer 3’s OneDrive. If co-organizer 3 also doesn’t have a OneDrive account, the recording is then saved to co-organizer 2’s OneDrive.

1. If none of the co-organizers have OneDrive accounts, the recording is saved to the OneDrive account of the user who initiated the recording.
1. If the user who initiated the recording doesn’t have a OneDrive, the recording gets temporarily stored to async media storage.

### Async media storage

If a Teams meeting recording fails to successfully upload to OneDrive because the organizer, co-organizers and recording initiator don’t have OneDrive accounts, or the storage quota is full, an error message appears. The recording is instead temporarily saved to async media storage. Once the recording is in async media storage, no retry attempts are made to automatically upload the recording to OneDrive or SharePoint. During that time, the organizer must download the recording. The organizer can try to upload the recording again if they get a OneDrive or SharePoint license, or clear some space in their storage quota. If not downloaded within 21 days, the recording is deleted.

### Videos

Videos are just like any other file in OneDrive and SharePoint. Handling ownership and retention after an employee leaves follows the standard [OneDrive and SharePoint process](/onedrive/retention-and-deletion).

### Retention labels

To learn how to apply retention labels to Teams meeting recordings, see [How to autoapply a retention label](/microsoft-365/compliance/apply-retention-labels-automatically).

### Planning for storage

The size of a one-hour recording is 400 MB. Make sure you understand the capacity required for recorded files and have sufficient storage available in OneDrive and SharePoint. Read [Set the default storage space for OneDrive](/sharepoint/set-default-storage-space) and [Manage SharePoint site storage limits](/sharepoint/manage-site-collection-storage-limits) to understand the base storage included in the subscription and how to purchase more storage.

## Viewing permissions

For **non-Channel meetings**, all meeting invitees, except for external participants, automatically get a personally shared link. The meeting organizer must explicitly add external participants to the shared list.

For **Channel meetings**, permissions are inherited from the owners and members list in the channel.

## Recording quotas

Teams meeting recording files live in OneDrive and SharePoint and are included in your quota for those services. To learn more, see
[SharePoint quota](/sharepoint/sites/plan-site-maintenance-and-management#quotas), [Sharepoint limits](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits), and [OneDrive quota](/onedrive/set-default-storage-space).

## Managing captions

Captions help create inclusive content for viewers of all abilities. Closed captions for Teams meeting recordings are available during playback only if the user had transcription turned on at the time of recording. You must enable transcription to allow your users to record meetings with transcription. To learn more about enabling transcription for your users, see [Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md).

As an owner, you can hide captions on the meeting recording, although the meeting transcript is available on Teams unless you delete it there.

Closed captions are supported for Teams meeting recordings for 60 days from when the meeting is recorded. Closed captions aren't fully supported if the Teams Meeting Recording is moved or copied from its original location on OneDrive or SharePoint.

## Permissions or role-based access

> [!NOTE]
> We recommend that the recipient is required to be a logged-in user when sharing Teams meeting recordings. Select the **People in (Your Organization)** option when you share the file as documented in [Share SharePoint files or folders](https://support.microsoft.com/office/1fe37332-0f9a-4719-970e-d2578da4941c). External sharing isn't designed for the distribution of large files or a large number of files.

|Meeting type                               | Who selected Record?| Where does the recording land?                               |Who has access? R/W, R, or sharing                                                                                                                                                                                                                                                     |
|-------------------------------------------|-----------------------|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|1:1 call with internal parties             |Caller                 |Caller’s OneDrive account                        |Caller is owner and has full permissions. <br /><br />Callee has read-only access, but no sharing or download permissions. <br /><br />|
|1:1 call with internal parties             |Callee                 |Callee’s OneDrive account                        |Callee is owner and has full permissions. <br /><br />Caller has read-only access, but no sharing or download permissions. <br /><br />|
|1:1 call with an external call             |Caller                 |Caller’s OneDrive account                        |Caller is owner and has full permissions.<br /> <br />Callee has no access. Caller must share it to the Callee.|
|1:1 call with an external call             |Callee                 |Callee’s OneDrive account                        |Callee is owner and has full permissions.<br /><br />Caller has no access. Callee must share it to the Caller.|
|Group call                                 |Any member of the call |Group member who selected Record’s OneDrive account  |Member who selected Record has full permissions. <br /><br /> Other group members from the same tenant have Read rights. <br /><br /> Other group members from different tenant have no permissions to it.|
|Adhoc/Scheduled meeting                    |Organizer              |Organizer’s OneDrive account                     |Organizer has full permissions to the recording. Co-organizers and organizer have edit permissions and can share. <br /> <br />  All other members of the meeting from the same tenant as the organizer have read access, but no sharing and download permissions.|
|Adhoc/Scheduled meeting                    |Other meeting member   |Organizer’s OneDrive account                                  |Organizer has full permissions to the recording. Co-organizers and organizer have edit permissions and can share. <br /> <br />  All other members of the meeting from the same tenant as the organizer have read access.|
|Adhoc/Scheduled meeting with external participants|Organizer              |Organizer’s OneDrive account                     |Organizer has full permissions to the recording. Co-organizers and organizer have edit permissions and can share. <br /> <br />  All other members of the meeting from the same tenant as the organizer have read access. <br /><br /> All other external participants have no access, and the Organizer must share it to them.|
|Adhoc/Scheduled meeting with external participants|Other meeting member   |Organizer’s OneDrive account                                  |Organizer has full permissions to the recording. Co-organizers and organizer have edit permissions and can share. <br /><br /> All other members of the meeting from the same tenant as the organizer have read access. <br /><br />All other external participants have no access, and the Organizer must share it to them.|
|Channel meeting                            |Channel Member         |Teams SharePoint location for that channel. **Note**: Channel meeting recording upload to SharePoint isn't supported for IP-based restrictions. We recommend using [Azure conditional access](/azure/active-directory/conditional-access/overview). |Member who selected on Record has edit permissions to the recording. <br /> <br />Every other member’s permissions are based on the Channel SharePoint permissions.|

## Related topics

- [Which policy takes precedence?](./policy-assignment-overview.md#which-policy-takes-precedence)
- [Teams meeting recording](meeting-recording.md)
- [Block the download of Teams meeting recording files from SharePoint or OneDrive](block-download-meeting-recording.md)
- [Policy recommendations for securing SharePoint sites and files](/security/zero-trust/zero-trust-identity-device-access-policies-sharepoint)
