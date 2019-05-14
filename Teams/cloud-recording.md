---
title: Teams cloud meeting recording
author: tonysmit
ms.author: tonysmit
manager: serdars
ms.topic: article
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: sonua
search.appverid: MET150
description: Practical guidance for deploying cloud voice features in Microsoft Teams.
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Teams cloud meeting recording

In Microsoft Teams, users can record their Teams meetings and group calls to capture audio, video, and screen sharing activity. There is also an option for recordings to have automatic transcription, so that users can play back meeting recordings with closed captions and search for important discussion items in the transcript. The recording happens in the cloud and is saved to [Microsoft Stream](https://docs.microsoft.com/stream/), so users can share it securely across their organization.

Related: [Teams meeting recording end user documentation](https://aka.ms/recordmeeting)

## Prerequisites for Teams cloud meeting recording

For a Teams user’s meetings to be recorded, Microsoft Stream must be enabled for the tenant. In addition, the following prerequisites are required for both the meeting organizer and the person who is initiating the recording:

- User has an Office 365 E1, E3, E5, A1, A3, A5, M365 Business, Business Premium or Business Essentials
- User needs to be licensed for Microsoft Stream
- User has Microsoft Stream upload video permissions
- User has consented to the company guidelines, if set up by the admin
- User has sufficient storage in Microsoft Stream for recordings to be saved
- User has TeamsMeetingPolicy-AllowCloudRecording setting set to true
- User is not an anonymous, Guest, or federated user in the meeting

> [!NOTE]
> Additionally, to allow the person initiating the recording to choose whether to automatically transcribe the recording, the user's TeamsMeetingPolicy -AllowTranscription setting must be set to true

## Set up Teams cloud meeting recording for users in your organization

This section explains how you can set up and plan for recording Teams meetings.

### Enable Microsoft Stream for users in the organization

Microsoft Stream is available as part of eligible Office 365 subscriptions or as a standalone service.  See the [Stream licensing overview](https://docs.microsoft.com/stream/license-overview) for more details.  Microsoft Stream is now included in Microsoft 365 Business, Office 365 Business Premium, and Office 365 Business Essentials.

Learn more about how you can [assign licenses to users in Office 365](https://support.office.com/article/Assign-licenses-to-users-in-Office-365-for-business-997596B5-4173-4627-B915-36ABAC6786DC) so that users can access Microsoft Stream. Ensure that Microsoft Stream is not blocked for the users, as defined in [this article](https://docs.microsoft.com/stream/disable-user-organization).

### Ensure that users have upload video permissions in Microsoft Stream

By default, everyone in the company can create content in Stream, once Stream is enabled and the license is assigned to the user. A Microsoft Stream administrator can [restrict employees for creating content](https://docs.microsoft.com/stream/restrict-uploaders) in Stream. The users who are in this restricted list will not be able to record meetings.

### Notify employees to consent to company guidelines in Microsoft Stream

If a Microsoft Stream administrator has [set up company guideline policy](https://docs.microsoft.com/stream/company-policy-and-consent) and requires employees to accept this policy before saving content, users must do so before recording in Microsoft Teams. Before you roll out the recording feature in the organization, make sure users have consented to the policy.

### Turn on or turn off cloud recording

Use the setting AllowCloudRecording in TeamsMeetingPolicy in Teams PowerShell to control whether a user’s meetings are allowed to be recorded or not. You can learn more about managing TeamsMeetingPolicy with Office 365 PowerShell [here](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

Note that both the meeting organizer and the recording initiator need to have the recording permissions to record the meeting. Unless you have assigned a custom policy to the users, the users get Global policy, which has AllowTranscription disabled by default.

For a user to fall back to Global policy, use the following cmdlet to remove a specific policy assignment for a user:

`Grant-CsTeamsMeetingPolicy -Identity {user} -PolicyName $null -Verbose`

To change value of AllowCloudRecording in Global policy, use the following cmdlet:

`Set-CsTeamsMeetingPolicy -Identity Global -AllowCloudRecording $false`
</br>
</br>


|                                                                 Scenario                                                                 |                                                                                                                                                                         Steps                                                                                                                                                                          |
|------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                    I want all users in my company to be able to record their meetings                                    |                                                                     <ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = True<li>All users have the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True </ol>                                                                     |
| I want the majority of my users to be able to record their meetings but selectively disable specific users who are not allowed to record |        <ol><li>Confirm GlobalCsTeamsMeetingPolicy has AllowCloudRecording = True<li>Majority of the users have the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True<li>All other users have been granted one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False</ol>         |
|                                                   I want recording to be 100% disabled                                                   |                                                                <ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = False<li>All users have been granted the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False                                                                 |
|      I want recording to be disabled for the majority of the users but selectively enable specific users who are allowed to record       | <ol><li>Confirm Global CsTeamsMeetingPolicy has AllowCloudRecording = False<li>Majority of the users have been granted the Global CsTeamsMeetingPolicy OR one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = False<li>All other users have been granted one of the CsTeamsMeetingPolicy policies with AllowCloudRecording = True <ol> |
|                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                        |

### Turn on or turn off recording transcription

When users record their Teams meetings, they can confirm whether a transcript should automatically be generated after the meeting is recorded. If admins have disabled transcription capability for the meeting organizer and the recording initiator, the recording initiator will not get a choice to transcribe the meeting recordings.

Use the setting AllowTranscription in TeamsMeetingPolicy in Teams PowerShell to control whether a recording initiator gets a choice to transcribe the meeting recording. You can learn more about managing TeamsMeetingPolicy with Office 365 PowerShell [here](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

Unless you have assigned a custom policy to the users, they get Global policy, which has AllowTranscription disabled by default.

For a user to fall back to Global policy, use the following cmdlet to remove a specific policy assignment for a user:

`Grant-CsTeamsMeetingPolicy -Identity {user} -PolicyName $null -Verbose`

To change value of AllowCloudRecording in Global policy, use the following cmdlet:

`Set-CsTeamsMeetingPolicy -Identity Global -AllowTranscription $false`
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

The size of a 1-hour recording is 400 MB. Make sure you understand the capacity required for recorded files and have sufficient storage available in Microsoft Stream.  Read [this article](https://docs.microsoft.com/stream/license-overview) to understand the base storage included in the subscription and how to purchase additional storage.

## Manage meeting recordings
The meeting recordings are considered tenant-owned content. If the owner of the recording leaves the company, the admin can open the recording video URL in Microsoft Stream in admin mode. The admin can delete the recording, update any recording metadata, or change permissions for the recording video. Learn more about [admin capabilities in Stream](https://docs.microsoft.com/stream/manage-content-permissions).

## Compliance and eDiscovery for meeting recordings
The meeting recordings are stored in Microsoft Stream, which is Office 365 Tier-C compliant. To support e-Discovery requests for compliance admins who are interested in meeting or call recordings for Microsoft Streams, the recording completed message is available in the compliance content search functionality for Microsoft Teams. Compliance admins can look for the keyword "recording" in the subject line of the item in compliance content search preview and discover meeting and call recordings in the organization. A prerequisite for them to view all recordings is that they will need to be set up in Microsoft Stream with admin access. Learn more about [assigning admin permissions in Stream](https://docs.microsoft.com/stream/assign-administrator-user-role).

## Want to know more about Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center, such as when you are making setting changes for many users at one time. To get started with Windows PowerShell, see these topics:

- [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
- [Set up your computer for Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525038)

