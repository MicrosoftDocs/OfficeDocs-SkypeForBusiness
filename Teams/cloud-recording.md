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
ms.localizationpriority: high
f1.keywords:
- NOCSH
description: Practical guidance for deploying cloud voice features in Teams to record Teams meetings and group calls to capture audio, video, and screen sharing activity.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Teams cloud meeting recording

In Microsoft Teams, users can record their Teams meetings and group calls to capture audio, video, and screen sharing activity. There is also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and review important discussion items in the transcript. The recording happens in the cloud and is saved to Microsoft OneDrive for Business and Microsoft SharePoint Online, so users can share it securely across their organization.

When a meeting is recorded, it's automatically:

- Uploaded to OneDrive for Business or SharePoint Online
- Permissioned to the people invited to the meeting
- Linked in the chat for the meeting
- Displayed in the Recordings and Transcripts tab for the meeting in Teams calendar
- Added to various file lists across Microsoft 365: Shared with me, office.com, Recommended, Recent, etc.
- Indexed for Microsoft 365 Search

Related: [Teams meeting recording end user documentation](https://support.microsoft.com/en-us/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24)

>[!Note]
> The change from using Microsoft Stream (classic) to OneDrive for Business and SharePoint Online for meeting recordings would have happened automatically in August 2021. For detailed information, see [Use OneDrive for Business and SharePoint Online or Stream for meeting recordings](tmr-meeting-recording-change.md).

> [!NOTE]
> For information about using roles in Teams meetings, and how to change users' roles, see [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019). For live events recording options, see [Live event recording policies in Teams](teams-live-events/live-events-recording-policies.md).

## Prerequisites for Teams cloud meeting recording

For a Teams user's meetings to be recorded, OneDrive for Business and SharePoint Online must be enabled for the tenant. In addition, the following prerequisites are required for both the meeting organizer and the person who is initiating the recording:

- User has sufficient storage in OneDrive for Business for non-channel meeting recordings to be saved.

- The Teams' channel has sufficient storage in SharePoint Online for channel meeting recordings to be saved.

- User has `CsTeamsMeetingPolicy -AllowCloudRecording` setting set to true in order to record meetings and group calls.

- User has `CsTeamsCallingPolicy -AllowCloudRecordingForCalls` setting set to true in order to record 1:1 calls.

- User is not an anonymous, Guest, or federated user in the meeting.

- To enable transcription for a user's meeting, the Teams meeting policy they are assigned to must have the `-AllowTranscription` setting set to true.

- To enable channel meeting recordings to be saved so channel members can't edit or download the recordings the `CSTeamsMeetingPolicy -ChannelRecordingDownload` setting must be set to Block.

> [!IMPORTANT]
>
> Users won't need OneDrive for Business or SharePoint Online enabled if you want users to only record and download the recordings. This will mean that the recordings aren't stored in OneDrive for Business or SharePoint Online, but are instead stored in temporary Teams storage with a 21-day limit before it's deleted. It's not something that an admin can control, manage, or delete at this time.
>
> For more [information on how temporary meeting recording storage works](#temp-storage), see below.  

## Set up Teams cloud meeting recording for users in your organization

This section explains how you can set up and plan for recording Teams meetings via [Teams meeting policies](policy-assignment-overview.md).

### Turn on or turn off cloud recording

You can use the Microsoft Teams admin center or PowerShell to set a Teams meeting policy to control whether user's meetings can be recorded.

In the Microsoft Teams admin center, turn on or turn off the **Cloud recording** setting in the meeting policy. To learn more, see [Meeting policy settings for audio and video](meetings-policies-recording-and-transcription.md#allow-cloud-recording).

Using PowerShell, you configure the AllowCloudRecording setting in TeamsMeetingPolicy. To learn more, see [New-CsTeamsMeetingPolicy](/powershell/module/skype/new-csteamsmeetingpolicy) and [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

Both the meeting organizer and the recording initiator need to have the recording permissions to record the meeting. Unless you have assigned a custom policy to the users, users get the Global policy, which has AllowCloudRecording enabled by default.

> [!NOTE]
> For more information about using Teams roles to configure who has permission to record a meeting, see [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

For a user to fall back to the Global policy, use the following cmdlet to remove a specific policy assignment for a user:

```powershell
Grant-CsTeamsMeetingPolicy -Identity {user} -PolicyName $null -Verbose
```

To change value of AllowCloudRecording in the Global policy, use the following cmdlet:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowCloudRecording $true
```

|Scenario|Steps|
|--|--|
| I want all users in my company to be able to record their meetings. | <ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = True.<li>All users have the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True.</ol> |
| I want most of my users to be able to record their meetings but selectively disable specific users who are not allowed to record. | <ol><li>Confirm GlobalCsTeamsMeetingPolicy has AllowCloudRecording = True.<li>Most of the users have the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True.<li>All other users have been granted one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False.</ol> |
| I want recording to be 100% disabled. | <ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = False.<li>All users have been granted the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False. |
| I want recording to be turned off for the majority of the users but selectively enable specific users who are allowed to record. | <ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = False.<li>Most of the users have been granted the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False.<li>All other users have been granted one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True. <ol> |


<a name="bd-channel"></a>
### Block or allow download of channel meeting recordings

This setting controls if channel meetings are saved to a "Recordings" folder or a "Recordings\View only" folder in the channel. The setting applies to the policy of the user who selects record for the channel meeting.

The two values for this setting are:

- **Allow** (default)—Saves channel meeting recordings to a "Recordings" folder in the channel. The permissions on the recording files will be based off the Channel SharePoint Online permissions. This is the same as any other file uploaded for the channel.

- **Block**—Saves channel meeting recordings to a "Recordings\View only" folder in the channel. Channel owners will have full rights on the recordings in this folder, but channel members will have read access without ability to download.

Using PowerShell, you configure the ChannelRecordingDownload setting in TeamsMeetingPolicy. To learn more, see [New-CsTeamsMeetingPolicy](/powershell/module/skype/new-csteamsmeetingpolicy) and [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

Unless you have assigned a custom policy to the users, users get the Global policy, which has ChannelRecordingDownload set to Allow by default.

For a user to fall back to Global policy, use the following cmdlet to remove a specific policy assignment for a user:

```powershell
Grant-CsTeamsMeetingPolicy -Identity {user} -PolicyName $null -Verbose
```

To change value of ChannelRecordingDownload in the Global policy, use the following cmdlet:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -ChannelRecordingDownload Block
```

> [!NOTE]
> The ChannelRecordingDownload setting is only available in the Teams PowerShell module version 2.4.1-preview or higher. To download the latest preview version of the module use this command:
>
>```powershell
>Install-Module -Name MicrosoftTeams -Force -AllowClobber -AllowPrerelease
>```

### Turn on or turn off recording transcription
This setting controls whether captions and transcription features are available during playback of meeting recordings. The person who started the recording needs this setting turned on for these features to work with their recording.
  
Turning this setting on creates a copy of the transcript that is stored with the meeting recording which enables **Search**, **CC**, and **transcripts** on the meeting recording.


> [!NOTE]
> That transcription for recorded meetings is currently only supported for English (US), English (Canada), English (India), English (UK), English (Australia), English (New Zealand), Arabic (Arab Emirates) , Arabic (Saudi Arabia) , Chinese (Cantonese), Chinese (Mandarin), Czech (Czechia) , Danish (Denmark), Dutch (Belgium) , Dutch (Netherlands), French (Canada), French (France), Finnish (Finland) , German (Germany), Hebrew (Israel) , Hindi (India), Italian (Italy), Japanese (Japan), Korean (Korea) , Norwegian (Norway), Polish (Poland) , Portuguese (Brazil), Portuguese (Portugal) , Russian (Russia) , Spanish (Mexico), Spanish (Spain), Swedish (Sweden), Thai (Thailand) , Turkish (Turkey), Vietnamese (Vietnam). They are stored together with the meeting recordings in OneDrive for Business and SharePoint Online cloud storage.

You can use the Microsoft Teams admin center or PowerShell to set a Teams meeting policy to control whether the recording initiator gets a choice to transcribe the meeting recording.

In the Microsoft Teams admin center, turn on or turn off the **Allow transcription** setting in the meeting policy. To learn more, see [Meeting policy settings for audio and video](meetings-policies-recording-and-transcription.md#allow-transcription).

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
|I want all users in my company to be able to transcribe when initiating recording of a meeting. |<ol><li>Confirm Global CsTeamsMeetingPolicy has AllowTranscription = True. <li>All users have the Global csTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowTranscription = True. </ol>|
|I want most of my users to be able to transcribe the meeting recordings, but selectively disable specific users who are not allowed to transcribe. |<ol><li>Confirm Global CsTeamsMeetingPolicy has AllowTranscription = True. <li>Majority of the users have the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowTranscription = True. <li>All other users have been granted one of the CsTeamsMeetingPolicy policies with AllowTranscription = False. </ol>|
|I want transcription of the recording to be 100% disabled. |<ol><li>Confirm Global CsTeamsMeetingPolicy has AllowTranscription = False. <li>All users have been granted the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowTranscription = False. </ol>|
|I want transcription to be disabled for the majority of the users but selectively enable specific users who are allowed to transcribe. |<ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = False. <li>Majority of the users have been granted the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False. <li>All other users have been granted one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True. </ol>|

### Terms of use acceptance
If your organization has a meeting recording policy that you would like your users to accept before recording a meeting, use the [Azure Active Directory terms of use](/azure/active-directory/conditional-access/terms-of-use) feature. This feature allows your users to accept your organization's terms of user policy before getting access to Microsoft Teams. This feature is not specific to clicking the record button, but is related to using Teams or other Microsoft 365 apps overall. Our suggestion is to add your meeting recording information to your overall terms of use for using Teams or Microsoft 365.

### Set a custom privacy policy URL

As an admin, you can update the Teams recording and transcription privacy policy URL with a custom link for your organization. You can do this in the [Azure AD admin center](https://aad.portal.azure.com) using the following steps:

1. Sign in to the Azure AD admin center.
1. Go to **Azure Active Directory** > **Properties**.
1. Update the **Privacy statement URL** field with the link to your privacy policy.

> [!NOTE]
> If you already updated this field for your organization, you don't need to make any changes.

After adding your privacy policy URL, the default Teams meeting recording and transcription privacy statement will be replaced with the new URL provided by your organization.

> [!NOTE]
> Anonymous, guest, and federated users who join Teams meetings hosted by your organization will still have the default Teams meeting recording and transcription privacy policy.

## Permissions and storage

Meeting recordings are stored in OneDrive for Business and SharePoint Online cloud storage. The location and permissions depend on the type of meeting and the role of the user in the meeting. The default permissions applied to the recording are listed below, users that have full edit rights on the video recording file can change the permissions and share it later with others as needed.

### Non-Channel meetings

- The recording is stored in a folder named **Recordings** in the OneDrive for Business of the user who clicked record. 

  Example:  <i>recorder's OneDrive for Business</i>/**Recordings**

- People invited to the meeting, except external users, will automatically be granted permission to the recording file with view access without ability to download.

- The meeting owner and the person who clicked record will get full edit access with ability to change permissions and share with other people.

### Channel meetings

If `Set-CsTeamsMeetingPolicy -ChannelRecordingDownload` is set to Allow (default):

- The recording is stored in the Teams site documentation library in a folder named **Recordings**.

  Example:  <i>Teams name - Channel name</i>/**Documents**/**Recordings**

- The member who clicked record has edit rights to the recording.

- Every other member’s permissions are based on the Channel SharePoint Online permissions.

If `Set-CsTeamsMeetingPolicy -ChannelRecordingDownload` is set to Block:

- The recording is stored in the Teams site documentation library in a folder named **Recordings/View only**. 

  Example:  <i>Teams name - Channel name</i>/**Documents/Recordings/View only**

- Channel owners will have full edit and download rights on the recordings in this folder.

- Channel members will have view only access without ability to download.

For more info on specific meeting types, see the following table:

| Meeting type  | Who clicked on Record?| Where does the recording land? | Who has access? R/W, R, or sharing  |
|-------------|-----------------------|------------------------|------------------------|
|1:1 call with internal parties             |Caller                 |Caller’s OneDrive for Business account                        |Caller is owner and has full rights. <br /><br />Callee (if in the same tenant) has read-only access. No sharing access. <br /><br /> Callee (if in different tenant) has no access. Caller must share it to the Callee.|
|1:1 call with internal parties             |Callee                 |Callee’s OneDrive for Business account                        |Callee is owner and has full rights. <br /><br />Caller (if in the same tenant has read-only access. No sharing access. <br /><br />Caller (if in different tenant) has no access. Callee must share it to the Caller.|
|1:1 call with an external call             |Caller                 |Caller’s OneDrive for Business account                        |Caller is owner and has full rights.<br /> <br />Callee has no access. Caller must share it to the Callee.|
|1:1 call with an external call             |Callee                 |Callee’s OneDrive for Business account                        |Callee is owner and has full rights.<br /><br />Caller has no access. Callee must share it to the Caller.|
|Group call                                 |Any member of the call |Group member who clicked on Record’s OneDrive for Business account  |Member who clicked on Record has full rights. <br /><br /> Other members from the same tenant have Read rights. <br /><br /> Other group members from different tenants have no rights to it.|
|Adhoc/Scheduled meeting                    |Organizer              |Organizer’s OneDrive for Business account                     |Organizer has full rights to the recording. <br /><br /> All other members of the meeting have read access without ability to download.|
|Adhoc/Scheduled meeting                    |Other meeting member   |Meeting member who clicked on Record                                  |Member who clicked on Record has full rights to the recording. <br /><br />Organizer has edit rights and can share.<br /><br /> All other meeting members have read access without ability to download.|
|Adhoc/Scheduled meeting with external users|Organizer              |Organizer’s OneDrive for Business account                     |Organizer has full rights to the recording.<br /> <br /> All other members of the meeting from the same tenant as the organizer have read access without ability to download. <br /><br /> All other external members have no access, and the Organizer must share it to them.|
|Adhoc/Scheduled meeting with external users|Other meeting member   |Member who clicked on Record                                  |Member who clicked on Record has full rights to the recording. Organizer has edit rights and can share. <br /><br /> All other members of the meeting from the same tenant as the organizer have read access without ability to download. <br /><br />All other external members have no access, and the Organizer must share it to them.|
|Channel meeting                            |Channel Member         |Teams' SharePoint Online location for that channel                   |If Set-CsTeamsMeetingPolicy -ChannelRecordingDownload is set to Allow (default) the member who clicked on Record has edit rights to the recording. Every other member’s permissions are based on the Channel SharePoint Online permissions.<Br><Br>If Set-CsTeamsMeetingPolicy -ChannelRecordingDownload is set to Block channel owners will have full rights on the recording, but channel members will have read access without ability to download.|

<a name="temp-storage"></a>
### Temporary storage when unable to upload to OneDrive for Business and SharePoint Online

If a meeting recording isn't able to be uploaded to OneDrive for Business and SharePoint Online, it will temporarily be available for download from Teams for 21 days before it is deleted. This is not something at this point that an admin can control or manage to include the ability to delete it.

Meeting recordings may end up in this temporary storage for the following reasons:

- For non-channel meetings if the user recording doesn't have a OneDrive for Business set up or the OneDrive for Business has reached its storage quota
- For a channel meeting if the SharePoint Online site has reached its storage quota or the site wasn't provisioned yet
- If specific OneDrive for Business and SharePoint Online policies are enabled restricting users from uploading files when not on specific IP ranges, etc.

The recording retention for this is temporary storage is affected by the chat message itself. As such, any deletion of the original chat message for the recording will prevent users from being able to access the recording. There are two scenarios that can affect this:

- **User manually deletes the chat message**—In this scenario, as the original message is gone, users will no longer be able to access the recording and no further downloads will be possible. However, the recording itself may still be retained within Microsoft's internal systems for a time (not exceeding the original 21-day period).

- **Recording chat message is deleted by chat retention policy**—Temporary storage recordings are directly tied to the chat retention policy. As such, although recordings on Teams temporary storage will by default be retained for 21 days before being deleted, if the chat message is deleted before the 21-day time period, due to chat message retention policies, the recording will also be deleted. There is no way to recover the recording after this.

### Planning for storage

The size of a 1-hour recording is 400 MB. Make sure you understand the capacity required for recorded files and have sufficient storage available in OneDrive for Business and SharePoint Online.  Read [Set the default storage space for OneDrive for Business](/onedrive/set-default-storage-space) and [Manage SharePoint Online site storage limits](/sharepoint/manage-site-collection-storage-limits) to understand the base storage included in the subscription and how to purchase additional storage.

 <a name="auto-expiration"></a>
### Auto-expiration of Teams meeting recordings

See the frequently asked questions for admins and end users to gather insights into how auto-expiration of Teams meeting recordings will work, what actions you can take now, and what actions you can take after the feature launches.
  
Learn more about the admin-specific changes [here](meeting-expiration.md#changes-to-meeting-expiration).

Learn more about how end users can manage meeting expiration [here](https://support.microsoft.com/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24#bkmk_view_change_expiration_date).
  
## Manage meeting recordings

Meeting recordings are stored as video files in OneDrive for Business and SharePoint Online and follow management and governance options available in those platforms. Read [SharePoint Online governance overview](/sharepoint/governance-overview), [OneDrive for Business guide for enterprises](/onedrive/plan-onedrive-enterprise), or [OneDrive for Business guide for small businesses](/onedrive/one-drive-quickstart-small-business) for more information.

For non-channel meetings, the recordings are stored in the recorder's OneDrive for Business, thus handling ownership and retention after an employee leaves will follow the normal [OneDrive for Business and SharePoint Online process](/onedrive/retention-and-deletion#the-onedrive-deletion-process).

## Closed captions for recordings

Closed captions for Teams meeting recordings will be available during playback only if the user had transcription turned on at the time of recording. Admins must [turn on recording transcription via policy](#turn-on-or-turn-off-recording-transcription) to ensure their users have the option to record meetings with transcription.

Captions help create inclusive content for viewers of all abilities. As an owner, you can hide captions on the meeting recording, although the meeting transcript will still be available on Teams unless you delete it there.

Today closed captions for the recording video file are linked to the Teams meeting transcript. This link will remain for the lifetime of the file in most cases, but can be broken if the video file is copied within the same OneDrive for Business or SharePoint Online site, which would result in captions not being available on the copied video file.

Any future changes to the link between the transcript in Teams and the recording will be clarified here and in message center notifications. If we make any changes in the future, we will ensure recording files less than 60-days old display the transcript from the meeting as captions.

> [!NOTE]
> Meeting transcription is not yet available in GCC.

## eDiscovery and Compliance for meeting recordings

### eDiscovery

The meeting recordings are stored in OneDrive for Business and SharePoint Online, which is Microsoft 365 and Office 365 Tier-D compliant. To support e-Discovery requests for compliance admins who are interested in meeting or call recordings, the recording completed message is available in the compliance content search functionality for Microsoft Teams. Compliance admins can look for the keyword "recording" in the subject line of the item in compliance content search preview and discover meeting and call recordings in the organization.

In addition, the meeting recording video file can be found via eDiscovery searches for files on SharePoint Online and OneDrive for Business.

To learn more about eDiscovery see the article [eDiscovery solutions for Microsoft 365](/microsoft-365/compliance/ediscovery)

### Retention policies

You can apply automatic retention labels to target just Teams meeting recording video files via the ProgID property. For more information, see [How to auto-apply a retention label for Teams meeting recordings](/microsoft-365/compliance/apply-retention-labels-automatically#microsoft-teams-meeting-recordings).

### Microsoft Purview Data Loss Prevention (DLP) policies

You can apply DLP policies to meeting recording files also by the ProgID property. In the DLP rule for files in SharePoint Online and OneDrive for Business set the conditions to be:

- Document property = *ProgID*
- Value = *Media.Meeting*

To learn more about DLP see the article [Learn about data loss prevention](/microsoft-365/compliance/dlp-learn-about-dlp)

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

2. In the Run diagnostic pane, enter the URL of the meeting in the **URL of the meeting that was recorded** field (usually found in the meeting invitation) as well as the date of the meeting in the **When was the meeting recorded? ** field and then select **Run Tests**.

3. The tests will validate that the meeting recording completed successfully and it was uploaded to Stream or OneDrive.

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
