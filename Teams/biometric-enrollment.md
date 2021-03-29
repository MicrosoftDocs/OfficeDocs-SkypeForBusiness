---
title: Tenant Administration control for biometric data in meeting rooms 
author: cichur
ms.author: v-cichur
ms.reviewer: 
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn about Tenant Administration control for biometric data in meeting rooms.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Tenant Administration control for biometric data in meeting rooms 

A Teams tenant admin can control to what degree the organization is using biometric data. There are two major policies: capture and usage. The former controls the capture of the biometric data through the enrollment flow, the later controls how the biometric data will be used in meeting rooms.

- This feature allows people to edit the SPEAKERS of transcripts
- You can change the speaker of a single utterance (on all transcripts). The people you can change to are listed as who is in the meeting.
- You can remove the identification of a single utterance or all utterances identified as that speaker (on all transcripts)

Biometric data can be used with the Rockfall device and any meeting with or without external audio devices.

## Use biometric data settings

Turn on or off Biometric capture, or Enrollment, in Teams settings through the admin policy EnrollUserOverride. An admin can enable or disable the enrollment feature for a tenant. One policy will cover both voice and face enrollment. This policy works independently from the usage policy to give admins flexibility to roll out this feature. The flexibility includes:

- Turn on biometric capture.
- Enroll users.
- Turn on usage.

When the settings are enabled:

- Users can view, access, and complete the enrollment flow.
- The entry point will show on Teams settings page.  

Settings are disabled by default. When the settings are disabled:

- Users who have never enrolled won't be able to view, enroll, or re-enroll.
- The entry point to enrollment flow will be hidden.
- If users select a link to enrollment page, they'll see a message that this feature isn't enabled for their organization.  
- Users who have already enrolled still will be able to view and remove their biometric data in the Teams settings. Once they remove their biometric data, they won't be able to view, access, or complete the enrollment flow.  

## Set Biometric usage

Turn on or off Biometric usage for attribution and diarization. (Speaker diarization is the process of partitioning an input audio stream into homogeneous segments according to the speaker identity.) Use RoomAttributeUserOverride in Rooms to set Biometric usage. An admin can control if users in a conference room will be attributed, diarized (distinguished),or neither. This policy controls use of both voice and face for transcription attribution purposes. This setting is off by default, so it won't use a user's attribute or distinguish features.

- Rooms won't send audio stream-saving bandwidths from the room.  
- Rooms users won't be attributed or diarized.
- Rooms users are unknown.  

Distinguish (distinguish but do not identify) 

- Room users will be diarized (attendee n), no user identity is shown for in-room attendees 
- Room will send 7 audio streams from the room 

Biometric information of the user is created during the meeting and dismissed at the end of the meeting 

Attribute  

- Room users will be attributed based on their enrollment status 
- Users who are enrolled, are shown with their name in the transcription  
- Users who are not enrolled show as attendee n 
- Room will send 7 audio streams from the room 

[Plaza Only] 

Policy Name = RoomPeopleNameUserOverride 

Purpose = Turn on/off biometric “usage” of face data by showing/hiding user names in the roster and people video feeds in rooms  

Feature Description =  Plaza family of cameras are capable of recognizing people in a room using their face biometric data.  One a person in a conf room is recognized by the camera, the name of that person will be added to the meeting roster and also as a name label on the people video feed of that person viewed by remote users.  

Policy description =  A Teams tenant admin should be able to control if meeting room participants can be identified or not using their face biometric data . 

Values 

- Off (do not show the names) [Default] 
- Room will not send face stream from the Plaza device. 
- Room attendees names will not appear in the meeting roster nor on the people video feeds. 
- Room users are remain unknown. 

On (show the names in roster and people video feeds) 

- Room will send face stream from the Plaza device 
- Names of the room attendees who have enrolled their face will show in the meeting roster and on their people video feed. If a user is not face enrolled, they appear as speaker 1, speaker 2,…. in the meeting roster 
