---
title: Plan for Teams webinars
ms.reviewer: justle
ms.date: 07/01/2023
ms.topic: article
ms.author: wlibebe
author: wlibebe
manager: serdars
ms.service: msteams
ms.subservice: meetings
ms.custom: intro-overview
audience: admin
f1.keywords:
- NOCSH
ms.collection: 
- M365-collaboration
- remotework
- m365initiative-meetings
- m365initiative-meetings-enabler
- enabler-strategic
- highpri
ms.localizationpriority: medium
search.appverid: MET150
appliesto: 
  - Microsoft Teams
description: Learn how to plan for webinars in Microsoft Teams.
---

# Plan for Teams webinars

**APPLIES TO:** ✖️Meetings ✔️Webinars ✖️Town halls

## Recordings

Webinar recordings are uploaded to OneDrive;
attendees can view the recording from the chat. However, guests can only view the recording if it's explicitly shared with them.
Microsoft Purview compliance features apply to the webinar recording files, the same as with other files.

## Registration

Registration is required for attendees to attend webinars.

As an admin, you can:

- Manage whether organizers can only create private webinars or public and private webinars
- Manage whether organizers can edit email communication templates (with a Teams Premium subscription)
- Manage the types of questions an organizer can require attendees to answer when registering for webinars

## External participants

Private (use name: In Org) webinars:

- don't include guests
- only accessible to members of the scheduling organization

Public webinars:

- no authentication, like a public website
- anonymous users can input anything on registration page
- join links are unique to registration with unique registration ID. loophole: you could forward registration links for someone else to join as you
- limited number of joins with registration ID to number 3 - not available yet
- after clicking join link, due to privacy, you have to re-enter your information
- Attendance report: each join records e.g. register as bob and join as "cool guy" on registration, they append from registration id from link and populate the registration id name

Anonymous participants:

- not internal, not guest, not federated
- can only register and join when webinar is public
- if you want anybody outside of your org, the webinar must be public

How to make the decision between a private vs public?

- Do you want to allow external attendees to join webinars?
- If registrant is logged into a tenant, it knows who they are and if not they can type a name
- How does the lobby work?
- How do join links work? These are not unique
- Dial in -- anonymous??
- Attendees with a registration link can bypass the lobby??
- People dialing in can bypass the lobby??
- Who can bypass the lobby: People who were invited(turn off allow forwarding)??QUESTION: How do you invite people to a webinar??
- Reject anyone who can't bypass the lobby??

Invited people are presenters and co-organizers. 
PSTN isn't available for webinar attendees but organizers and co-organizers can do this.

## Attendee interaction

Registered attendees join the webinar with their cameras and mics off; webinar organizers choose when to let attendees turn on their cameras or un-mute.

As an admin, you can manage the following features attendees use for interaction during webinars:

- **Chat:** Attendees can participate in a text-based chat messages during the webinar. Through chat, attendees can ask questions, share thoughts, and engage in discussions with other participants.

- **Q&A**: For a structured question and response format, webinar organizers can enable a dedicated Q&A feature where attendees can submit questions. Organizers or selected presenters can review and answer these questions during the webinar.

- **Reactions and hand raise**: During webinars, attendees can use reactions to show how they feel or give feedback. These reaction emojis include applause, like, laughter, heart, and surprise. Attendees can click on the reaction icons to display their reactions in real-time.

## Streaming

Find out more + ask Justin about this.

## Premium webinars

A Teams Premium subscription includes the following features for webinars:

- Create a webinar wait list
- Limit the day and time when people can register
- Manage attendees’ view
- Manually approve registrants
- Send reminder emails to registrants
- Set up a green room for webinar presenters
- Use RTMP-In for webinars

## Webinar control comparison

|Feature|Admins|Organizers|
|:------|:-----|:---------|
|[Attendance reports](teams-analytics-and-reports/meeting-attendance-report.md) |Can enforce on or off or allow organizer to choose|Can turn on or off if allowed by admin|
|[Audio and video](meeting-policies-audio-and-video.md)|Can set audio and video modes and network settings|Can allow or prevent attendee mic and cameras|
|[Chat](manage-meeting-chat.md) and [Q&A](manage-qna-for-teams.md)|Can choose if chat and Q&A are available|Can use chat and Q&A if allowed by admin|
|[Collaboration features](meeting-policies-content-sharing.md)|Can control the availability of PowerPoint Live, whiteboard, and shared notes|No control|
|[Content sharing](meeting-who-present-request-control.md)|Can control sharing mode and who can request control and can set a default for who can present|Can control who can present|
|[End-to-end encryption (Teams Premium)](end-to-end-encrypted-meetings.md)|Can allow or prevent end-to-end encryption|Can enforce end-to-end encryption if allowed by the admin|
|Email communications (Teams Premium)|Can control if event organizers and co-organizers can edit email templates for their webinars|Can edit email templates  before they're sent out|
|[Green room (Teams Premium)](https://support.microsoft.com/office/green-room-for-teams-meetings-5b744652-789f-42da-ad56-78a68e8460d5)|No control|Can choose if green room is used for a meeting|
|[Meeting join and lobby](who-can-bypass-meeting-lobby.md)|Can set the defaults for new meetings|Can choose meeting join and lobby settings for each meeting|
|[Recording](meeting-recording.md)|Can allow or prevent meeting recording and set recording expiration time|If recording is enabled by admin, can set who can record and automatic recording|
|Registration|Can allow or prevent meeting registration|Can require meeting registration if allowed by admin|
|Scheduling|Can define who can schedule private and channel meetings|Can schedule meetings if allowed by admin|
|Streaming|Can allow or prevent streaming|Can enforce streaming for a meeting if allowed by admin|
|Theme (Teams Premium)|Can define meeting themes, including colors, images, and logo|Can turn on or off the admin-defined theme|
|Transcription and captions|Can allow or prevent transcription and closed captions for attendees|Can enable CART captions|
|Translation (Teams Premium)|No control|Can enable live translated captions|
|Watermarks (Teams Premium)|Can allow or prevent watermarks for attendee video and shared content|Can enforce watermarks if allowed by the admin|
|Webinar usage report|View the activity overview for webinars created in your organization|No control|
