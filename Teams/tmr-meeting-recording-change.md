---
title: Use OneDrive and SharePoint for meeting recordings
ms.author: wlibebe
author: wlibebe
ms.reviewer: yudma, yujin1, ritikag
ms.date: 5/22/2024
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

# Use OneDrive and SharePoint for meeting recordings

When users in your org record Teams meetings, they're stored in OneDrive and SharePoint. The video plays on the video player of OneDrive or SharePoint depending on where your users access the file.
This article helps you, as an admin, understand recording storage and permissions for OneDrive and Sharepoint.

To learn about blocking the download of Teams meeting recording files from SharePoint or OneDrive, see [Block the download of Teams meeting recording files from SharePoint or OneDrive](block-download-meeting-recording.md).

## Recording storage

**As an admin, you can't change where recording are stored.**

For **webinars and meetings**, all recording files are automatically saved to the organizer's OneDrive **Recordings** folder, even if the organizer didn't attend the meeting. This applies to auto-recorded, recurring, meet now, and meetings that delegates create. Co-organizers can edit the recording files.

For **Channel meetings**, the recording is stored in the Teams site documentation library in a folder named **Recordings**. For example: *Teams name - Channel name*/**Documents**/**Recordings**.

For **shared accounts** and **Microsoft Teams Rooms meet now meetings**, the recording goes to the shared account's OneDrive, and if there's no OneDrive, it gets temporarily stored to async media storage. To learn more about Microsoft Teams Rooms meet now meetings, see [Microsoft Teams Rooms (Windows)](https://support.microsoft.com/office/microsoft-teams-rooms-windows-e667f40e-5aab-40c1-bd68-611fe0002ba2). For details on shared accounts, see [Sharing accounts with Microsoft Entra ID](/entra/identity/users/users-sharing-accounts).

Videos are just like any other file in OneDrive and SharePoint, so handling ownership and retention after an employee leaves follows the normal [OneDrive and SharePoint process](/onedrive/retention-and-deletion).

To learn how to apply retention labels to Teams meeting recordings, see [How to auto-apply a retention label](/microsoft-365/compliance/apply-retention-labels-automatically).

### Async media storage

If a Teams meeting recording fails to successfully upload to OneDrive because the user doesn't have OneDrive or SharePoint, or the storage quota is full, a "The recording ended unexpectedly" error message appears. The recording is instead temporarily saved to async media storage. Once the recording is in async media storage, no retry attempts are made to automatically upload the recording to OneDrive or SharePoint. During that time, the organizer must download the recording. If not downloaded within 21 days, the recording is deleted.

## Viewing permissions

For **non-Channel meetings**, all meeting invitees, except for external participants, automatically get a personally shared link. The meeting organizer or the person who started the meeting recording must explicitly add external participants to the shared list.

For **Channel meetings**, permissions are inherited from the owners and members list in the channel.

## Recording quotas

Teams meeting recording files live in OneDrive and SharePoint and are included in your quota for those services. To learn more, see
[SharePoint quota](/sharepoint/sites/plan-site-maintenance-and-management#quotas), [Sharepoint limits](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits), and [OneDrive quota](/onedrive/set-default-storage-space).

## Managing captions

Captions help create inclusive content for viewers of all abilities. Closed captions for Teams meeting recordings are available during playback only if the user had transcription turned on at the time of recording. Admins must turn on transcription to ensure their users can record meetings with transcription. To learn more about enabling transcription for your users, see [Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md).

As an owner, you can hide captions on the meeting recording, although the meeting transcript is available on Teams unless you delete it there.

Closed captions are supported for Teams meeting recordings for 60 days from when the meeting is recorded. Closed captions aren't fully supported if the Teams Meeting Recording is moved or copied from its original location on OneDrive or SharePoint.

## Permissions or role-based access

> [!NOTE]
> We recommend that the recipient is required to be a logged-in user when sharing Teams meeting recordings. Select the **People in (Your Organization)** option when you share the file as documented in [Share SharePoint files or folders](https://support.microsoft.com/office/1fe37332-0f9a-4719-970e-d2578da4941c). External sharing isn't designed for the distribution of large files or a large number of files.

|Meeting type                               | Who clicked on Record?| Where does the recording land?                               |Who has access? R/W, R, or sharing                                                                                                                                                                                                                                                     |
|-------------------------------------------|-----------------------|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|1:1 call with internal parties             |Caller                 |Caller’s OneDrive account                        |Caller is owner and has full rights. <br /><br />Callee (if in the same tenant) has read-only access. No sharing access. <br /><br /> Callee (if in different tenant) has no access. Caller must share it to the Callee.|
|1:1 call with internal parties             |Callee                 |Callee’s OneDrive account                        |Callee is owner and has full rights. <br /><br />Caller (if in the same tenant has read-only access. No sharing access. <br /><br />Caller (if in different tenant) has no access. Callee must share it to the Caller.|
|1:1 call with an external call             |Caller                 |Caller’s OneDrive account                        |Caller is owner and has full rights.<br /> <br />Callee has no access. Caller must share it to the Callee.|
|1:1 call with an external call             |Callee                 |Callee’s OneDrive account                        |Callee is owner and has full rights.<br /><br />Caller has no access. Callee must share it to the Caller.|
|Group call                                 |Any member of the call |Group member who clicked on Record’s OneDrive account  |Member who clicked on Record has full rights. <br /><br /> Other group members from the same tenant have Read rights. <br /><br /> Other group members from different tenant have no rights to it.|
|Adhoc/Scheduled meeting                    |Organizer              |Organizer’s OneDrive account                     |Organizer has full rights to the recording. <br /><br /> All other members of the meeting have read access.|
|Adhoc/Scheduled meeting                    |Other meeting member   |Meeting member who clicked on Record                                  |Member who clicked on Record has full rights to the recording. <br /><br />Organizer has edit rights and can share.<br /><br /> All other meeting members have read access.|
|Adhoc/Scheduled meeting with external participants|Organizer              |Organizer’s OneDrive account                     |Organizer has full rights to the recording.<br /> <br /> All other members of the meeting from the same tenant as the organizer have read access. <br /><br /> All other external participants have no access, and the Organizer must share it to them.|
|Adhoc/Scheduled meeting with external participants|Other meeting member   |Member who clicked on Record                                  |Member who clicked on Record has full rights to the recording. Organizer has edit rights and can share. <br /><br /> All other members of the meeting from the same tenant as the organizer have read access. <br /><br />All other external participants have no access, and the Organizer must share it to them.|
|Channel meeting                            |Channel Member         |Teams SharePoint location for that channel. **Note**: Channel meeting recording upload to SharePoint isn't supported for IP-based restrictions. We recommend using [Azure conditional access](/azure/active-directory/conditional-access/overview). |Member who clicked on Record has edit rights to the recording. <br /> <br />Every other member’s permissions are based on the Channel SharePoint permissions.|

## Related topics

- [Which policy takes precedence?](./policy-assignment-overview.md#which-policy-takes-precedence)
- [Teams meeting recording](meeting-recording.md)
- [Block the download of Teams meeting recording files from SharePoint or OneDrive](block-download-meeting-recording.md)
- [Policy recommendations for securing SharePoint sites and files](/security/zero-trust/zero-trust-identity-device-access-policies-sharepoint)