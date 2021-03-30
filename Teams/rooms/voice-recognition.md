---
title: Tenant Administration control for voice recognition (biometric data) in meeting rooms 
author: cichur
ms.author: v-cichur
ms.reviewer: parisataheri
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn about Tenant Administration control for voice recognition (biometric data) in meeting rooms.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Tenant Administration control for voice recognition (biometric data) in meeting rooms

A Teams tenant admin can control to what degree the organization is using voice recognition (biometric data). This feature allows people to edit the speakers of transcripts. You can change the speaker of a single utterance on all transcripts. The people you can change the speaker label for are the ones who are listed in the meeting. You can remove the identification of a single utterance or all utterances identified as that speaker on every transcript.

There are two major policies used with biometric data:

- Capture, which controls the capture of the biometric data through the enrollment flow.
- Usage, which controls how the biometric data will be used in meeting rooms.

Biometric data can be used in any meeting with or without external audio devices.

## Use biometric data settings

Turn on or off biometric capture, or enrollment, in Teams settings through the admin policy EnrollUserOverride. An admin can enable or disable the enrollment feature for a tenant. One policy will cover both voice and face enrollment. This policy works independently from the usage policy to give admins flexibility to roll out this feature. The flexibility includes:

- Turn on biometric capture.
- Enroll users.
- Turn on usage.

When the settings are enabled:

- Users can view, access, and complete the enrollment flow.
- The entry point will show on Teams settings page.  

Settings are disabled by default. When the settings are disabled:

- Users who have never enrolled can't view, enroll, or re-enroll.
- The entry point to enrollment flow will be hidden.
- If users select a link to enrollment page, they'll see a message that this feature isn't enabled for their organization.  
- Users who have already enrolled will be able to view and remove their biometric data in the Teams settings. Once they remove their biometric data, they won't be able to view, access, or complete the enrollment flow.  

## Set Biometric usage

Turn on or off biometric usage for attribution and diarization. Speaker diarization is the process of partitioning an input audio stream into homogeneous segments according to the speaker identity. Use RoomAttributeUserOverride in Rooms to set biometric usage. An admin can control if users in a conference room will be attributed, diarized (distinguished), or neither. This policy controls use of both voice and face for transcription attribution purposes. This setting is **off** by default, so it won't use a user's attribute or distinguish features.

- Rooms won't send audio stream-saving bandwidths from the room.  
- Rooms users won't be attributed or diarized.
- Rooms users are unknown.  

Distinguish participants but don't identify

- Rooms users will be diarized but not specifically named (attendee n). No user identity is shown for in-room attendees.
- Rooms will send seven audio streams from the room.

Biometric information of the user is created during the meeting and dismissed at the end of the meeting.

Attribute  

- Room users will be attributed based on their enrollment status 
- Users who are enrolled, are shown with their name in the transcription  
- Users who aren't enrolled show as attendee n
- Room will send seven audio streams from the room
