---
title: Teams cloud meeting recording
author: tonysmit
ms.author: tonysmit
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - M365-collaboration
  - m365initiative-meetings
ms.reviewer: nakulm
search.appverid: MET150
f1.keywords:
- NOCSH
description: Practical guidance for deploying cloud voice features in Teams to record Teams meetings and group calls to capture audio, video, and screen sharing activity.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Teams cloud meeting recording

In Microsoft Teams, users can record their Teams meetings and group calls to capture audio, video, and screen sharing activity. There is also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and search for important discussion items in the transcript. The recording happens in the cloud and is saved to [Microsoft Stream](/stream/), so users can share it securely across their organization.

Related: [Teams meeting recording end user documentation](https://aka.ms/recordmeeting)

>[!Note]
> The change from using Microsoft Stream to OneDrive for Business and SharePoint for meeting recordings will be a phased approach. For detailed information on each phase, see [Use OneDrive for Business and SharePoint or Stream for meeting recordings](tmr-meeting-recording-change.md).

> [!NOTE]
> For information about using roles in Teams meetings, and how to change users' roles, see [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019?ui=en-us&rs=en-us&ad=us). For live events recording options, see [Live event recording policies in Teams](teams-live-events/live-events-recording-policies.md).

## Prerequisites for Teams cloud meeting recording

For a Teams user's meetings to be recorded, Microsoft Stream must be enabled for the tenant. In addition, the following prerequisites are required for both the meeting organizer and the person who is initiating the recording:

- User has Office 365 E1, E3, E5, A1, A3, A5, Microsoft 365 Business Premium, Business Standard, or Business Basic<sup>1</sup>
- User has consented to the company guidelines, if set up by the admin
- User has sufficient storage in Microsoft Stream for recordings to be saved
- User has CsTeamsMeetingPolicy -AllowCloudRecording setting set to true in order to record meetings and group calls
- User has CsTeamsCallingPolicy -AllowCloudRecordingForCalls setting set to true in order to record 1:1 calls
- User is not an anonymous, Guest, or federated user in the meeting
- To enable transcription for a user's meeting, the Teams meeting policy they are assigned to must have the -AllowTranscription setting set to true.

<sup>1</sup> As of August 20, 2020, access to the meeting recording file will expire after 21 days for users with A1. For more information, see [Upload a Microsoft Teams meeting recording to Stream](/stream/portal-upload-teams-meeting-recording).

<sup>2</sup> User needs to be licensed to upload/download meetings to/from Microsoft Stream, however they do not need the license to record a meeting. If you wish to block a user from recording a Microsoft Teams Meeting, you must grant a TeamsMeetingPolicy that has AllowCloudRecording set to $False.

> [!IMPORTANT]
> Users won't need a Microsoft Stream license assigned if you want users to only record and download the recordings. This will mean that the recordings aren't stored in Microsoft Stream but are instead stored in Azure Media Services (AMS) with a 21-day limit before it's deleted. It's not something at this point that an admin can control or manage including the ability to delete it.

## Set up Teams cloud meeting recording for users in your organization

This section explains how you can set up and plan for recording Teams meetings.

### Turn on Microsoft Stream for users in the organization

Microsoft Stream is available as part of eligible Microsoft 365 and Office 365 subscriptions or as a standalone service.  See the [Stream licensing overview](/stream/license-overview) for more details.  Microsoft Stream is now included in Microsoft 365 Business, Microsoft 365 Business Standard, and Microsoft 365 Business Basic.

Learn more about how you can [assign licenses to users in Microsoft 365 or Office 365](https://support.office.com/article/Assign-licenses-to-users-in-Office-365-for-business-997596B5-4173-4627-B915-36ABAC6786DC) so that users can access Microsoft Stream. Ensure that Microsoft Stream is not blocked for the users, as defined in [Block sign-ups for Microsoft Stream](/stream/disable-user-organization).

### Make sure users have upload video permissions in Microsoft Stream

By default, everyone in the company can create content in Stream, once Stream is enabled and the license is assigned to the user. A Microsoft Stream administrator can [restrict employees for creating content](/stream/restrict-uploaders) in Stream. The users who are in this restricted list will not be able to record meetings.

### Notify employees to consent to company guidelines in Microsoft Stream

If a Microsoft Stream administrator has [set up company guideline policy](/stream/company-policy-and-consent) and requires employees to accept this policy before saving content, users must do so before recording in Microsoft Teams. Before you roll out the recording feature in the organization, make sure users have consented to the policy.

### Turn on or turn off cloud recording

You can use the Microsoft Teams admin center or PowerShell to set a Teams meeting policy to control whether user's meetings can be recorded.

In the Microsoft Teams admin center, turn on or turn off the **Allow cloud recording** setting in the meeting policy. To learn more, see [Manage meeting policies in Teams](meeting-policies-in-teams.md#allow-cloud-recording).

Using PowerShell, you configure the AllowCloudRecording setting in TeamsMeetingPolicy. To learn more, see [New-CsTeamsMeetingPolicy](/powershell/module/skype/new-csteamsmeetingpolicy) and [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

Note that both the meeting organizer and the recording initiator need to have the recording permissions to record the meeting. Unless you have assigned a custom policy to the users, users get the Global policy, which has AllowCloudRecording enabled by default.

> [!NOTE]
> For more information about using Teams roles to configure who has permission to record a meeting, see [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019?ui=en-us&rs=en-us&ad=us).

For a user to fall back to the Global policy, use the following cmdlet to remove a specific policy assignment for a user:

```powershell
Grant-CsTeamsMeetingPolicy -Identity {user} -PolicyName $null -Verbose
```

To change value of AllowCloudRecording in the Global policy, use the following cmdlet:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowCloudRecording $false
```

</br>
</br>


|                                                                 Scenario                                                                 |                                                                                                                                                                         Steps                                                                                                                                                                          |
|------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                    I want all users in my company to be able to record their meetings                                    |                                                                     <ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = True<li>All users have the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True </ol>                                                                     |
| I want the majority of my users to be able to record their meetings but selectively disable specific users who are not allowed to record |        <ol><li>Confirm GlobalCsTeamsMeetingPolicy has AllowCloudRecording = True<li>Majority of the users have the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True<li>All other users have been granted one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False</ol>         |
|                                                   I want recording to be 100% disabled                                                   |                                                                <ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = False<li>All users have been granted the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False                                                                 |
|      I want recording to be turned off for the majority of the users but selectively enable specific users who are allowed to record       | <ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = False<li>Majority of the users have been granted the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False<li>All other users have been granted one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True <ol> |
|                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                  |

#### Where your meeting recordings are stored

Meeting recordings are stored in Microsoft Stream cloud storage. Currently, the meeting recording feature is turned off for customers whose Teams data is stored in-country if Microsoft Stream isn't available in the in-country data residency region where the data is stored. The meeting recording feature can be turned on for customers whose data is supposed to be stored in-country even if Microsoft Stream isn't available in the in-country data residency region. This can be done by allowing recordings to be stored in the nearest geographic region for Microsoft Stream. 

If your Teams data is stored in-country and you prefer to store meeting recordings in-country, we recommend that you turn off the feature, and then turn it on after Microsoft Stream is deployed to your in-country data residency region. To turn off the feature for all users in your organization, turn off the **Allow cloud recording** setting in the Global Teams meeting policy, which is in the Microsoft Teams admin center. If, however, you still wish to enable recordings to be stored in the nearest geographic region for Microsoft Stream, you must turn on both **Allow cloud recording** and **Allow Recording Storage Outside Region** before this change takes place.

To enable recordings in-region in the Global policy, use the following cmdlet:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowCloudRecording $true -AllowRecordingStorageOutsideRegion $true
```

Here's a summary of what happens when you turn on meeting recording when this change takes effect:

|If you turn on meeting recordings...|Meeting recordings are stored... |
|---|---|
|Before Microsoft Stream is available in your in-country data residency region |In the nearest Microsoft Stream region|
|After Microsoft Stream is available in your in-country data residency region |In your in-country data residency region|

For new and existing tenants that haven't yet turned on meeting recording, new recordings are stored in-country after Microsoft Stream is available in the in-country data residency region. However, any tenant that enables meeting recording before Microsoft Stream is available in the in-country data residency region will continue to use the Microsoft Stream storage for existing and new recordings, even after Microsoft Stream is available in the in-country data residency region.

To find the region where your Microsoft Stream data is stored, in Microsoft Stream, click **?** in the upper-right corner, click **About Microsoft Stream**, and then click **Your data is stored in**.  To learn more about the regions where Microsoft Stream stores data, see [Microsoft Stream FAQ](/stream/faq#which-regions-does-microsoft-stream-host-my-data-in).

To learn more about where data is stored across services in Microsoft 365 or Office 365, see [Where is your data located?](https://products.office.com/where-is-your-data-located?rtc=1)

### Turn on or turn off recording transcription

This setting controls whether captions and transcription features are available during playback of meeting recordings. If you turn this off, the **Search** and **CC** options won't be available during playback of a meeting recording. The person who started the recording needs this setting turned on so that the recording also includes transcription.

> [!NOTE]
> That transcription for recorded meetings is currently only supported for users who have the language in Teams set to English and when English is spoken in the meeting. They are stored together with the meeting recordings in Microsoft Stream cloud storage.

You can use the Microsoft Teams admin center or PowerShell to set a Teams meeting policy to control whether the recording initiator gets a choice to transcribe the meeting recording.

In the Microsoft Teams admin center, turn on or turn off the **Allow transcription** setting in the meeting policy. To learn more, see [Manage meeting policies in Teams](meeting-policies-in-teams.md#allow-transcription).

Using PowerShell, you configure the AllowTranscription setting in TeamsMeetingPolicy. To learn more, see [New-CsTeamsMeetingPolicy](/powershell/module/skype/new-csteamsmeetingpolicy) and [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

Unless you have assigned a custom policy to the users, users get the Global policy, which has AllowTranscription disabled by default.

For a user to fall back to Global policy, use the following cmdlet to remove a specific policy assignment for a user:

```powershell
Grant-CsTeamsMeetingPolicy -Identity {user} -PolicyName $null -Verbose
```

To change value of AllowCloudRecording in the Global policy, use the following cmdlet:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowTranscription $false
```

</br>
</br>

|Scenario|Steps |
|---|---|
|I want all users in my company to be able to transcribe when initiating recording of a meeting |<ol><li>Confirm Global CsTeamsMeetingPolicy has AllowTranscription = True <li>All users have the Global csTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowTranscription = True. </ol>|
|I want the majority of my users to be able to transcribe the meeting recordings, but selectively disable specific users who are not allowed to transcribe |<ol><li>Confirm Global CsTeamsMeetingPolicy has AllowTranscription = True <li>Majority of the users have the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowTranscription = True <li>All other users have been granted one of the CsTeamsMeetingPolicy policies with AllowTranscription = False </ol>|
|I want transcription of the recording to be 100% disabled |<ol><li>Confirm Global CsTeamsMeetingPolicy has AllowTranscription = False <li>All users have been granted the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowTranscription = False </ol>|
|I want transcription to be disabled for the majority of the users but selectively enable specific users who are allowed to transcribe |<ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = False <li>Majority of the users have been granted the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False <li>All other users have been granted one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True </ol>|
|||

### Planning for storage

The size of a 1-hour recording is 400 MB. Make sure you understand the capacity required for recorded files and have sufficient storage available in Microsoft Stream.  Read [Microsoft Stream Licensing overview](/stream/license-overview) to understand the base storage included in the subscription and how to purchase additional storage.

## Manage meeting recordings

The meeting recordings are considered tenant-owned content. If the owner of the recording leaves the company, the admin can open the recording video URL in Microsoft Stream in admin mode. The admin can delete the recording, update any recording metadata, or change permissions for the recording video. Learn more about [admin capabilities in Stream](/stream/manage-content-permissions).

> [!NOTE]
> See [Manage user data in Microsoft Stream](/stream/managing-user-data) and [Permissions and privacy in Microsoft Stream](/stream/portal-permissions) for additional information on managing recordings and user access.

## Compliance and eDiscovery for meeting recordings

The meeting recordings are stored in Microsoft Stream, which is Microsoft 365 and Office 365 Tier-C compliant. To support e-Discovery requests for compliance admins who are interested in meeting or call recordings for Microsoft Streams, the recording completed message is available in the compliance content search functionality for Microsoft Teams. Compliance admins can look for the keyword "recording" in the subject line of the item in compliance content search preview and discover meeting and call recordings in the organization. A prerequisite for them to view all recordings is that they will need to be set up in Microsoft Stream with admin access. Learn more about [assigning admin permissions in Stream](/stream/assign-administrator-user-role).

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)