---
title: Manage meeting policies for recording and transcription
author: KarliStites
ms.author: kastites
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

This article describes the meeting policy settings specific to recording and transcription. These include the following:

- [Allow transcription](#allow-transcription)
- [Allow cloud recording](#allow-cloud-recording)
- [Store recordings outside of your country or region](#store-recordings-outside-of-your-country-or-region)

## Allow transcription

This is a combination of a per-organizer and per-user policy. This setting controls whether captions and transcription features are available during playback of meeting recordings. If you turn this off, the **Search** and **CC** options won't be available during playback of a meeting recording. The person who started the recording needs this setting turned on so that the recording also includes transcription.

Note that transcription for recorded meetings is currently only supported for users who have the language in Teams set to English and when English is spoken in the meeting.

## Allow cloud recording

This is a combination of a per-organizer and per-user policy. This setting controls whether this user's meetings can be recorded. The recording can be started by the meeting organizer or by another meeting participant if the policy setting is turned on for the participant and if they're an authenticated user from the same organization.

People outside your organization, such as federated and anonymous users, can't start the recording. Guest users can't start or stop the recording.

![Screenshot showing recording options](media/meeting-policies-recording.png)

Let's look at the following example.

|User |Meeting policy  |Allow cloud recording |
|---------|---------|---------|
|Daniela | Global   | Off |
|Amanda | Location1MeetingPolicy | On|
|John (external user) | Not applicable | Not applicable|

Meetings organized by Daniela can't be recorded and Amanda, who has the policy setting enabled, can't record meetings organized by Daniela. Meetings organized by Amanda can be recorded, however,  Daniela, who has the policy setting disabled and John who is an external user, can't record meetings organized by Amanda.

To learn more about cloud meeting recording, see [Teams cloud meeting recording](cloud-recording.md).

## Store recordings outside of your country or region

This policy controls whether meeting records can be permanently stored in another country or region. If it's enabled, the recordings can't be migrated. For more information on cloud meetings and where recordings are stored, see [Teams cloud meeting recording](cloud-recording.md).

## Related topics

- [Assign policies to users in Teams](policy-assignment-overview.md)
- [Cloud meeting recording](cloud-recording.md)