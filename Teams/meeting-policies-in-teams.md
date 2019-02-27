---
title: Manage meeting policies
author: tonysmit
ms.author: tonysmit
manager: serdars
ms.date: 06/07/2018
ms.topic: article
ms.service: msteams
ms.reviewer: sonua 
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
f1keywords: 
- ms.teamsadmincenter.meetingpolicies.overview
description: Learn to manage meeting policy settings in Teams.
---
# Manage meeting policies in Teams
::: zone target="docs"
Meeting policies are used to control the features that are available to meeting participants for meeting that are scheduled by users in your organization. After you create a policy and make your changes, you can then assign uses to the policy. 
::: zone-end 

## Here are the settings you can change to fit your organization
<a name="bkgeneral"> </a>

::: zone target="chromeless"
## General
   - **Name** This is the name of the policy that will appear on the Meeting policies page. It can't contain special chararcters or be long than 64 characters.
   - **Description** You can put in a friendly description for your policy you create. This will be helpful if you want to assign a policy to a group of users.
   - **Allow Meet Now** Turning this on will allow the Meet Now feature to be available to users that join meetings.
   - **Allow the Outlook add-in** Turning this on will let users assigned to the policy have the Outlook add-in available when they schedule meetings.
   - **Allow Channel meeting scheduling** Turning this on will allow Channel Meeting scheduling.
   - **Allow scheduling private meetings** Turning this on will allow users that join a meeting to schedule private meetings.

<a name="bkaudioandvideo"> </a>

## Audio & video
   - **Allow transcription** If you turn this on, transcription of the meeting will be available to users.
   - **Allow cloud recording** Turning this on will allow recordings to be saved to the cloud.
   - **Allow IP video** Turning this on will allow IP videos during meetings.
   - **Media bit rate (KBs)** You can set the bit rate for meetings. The default is 50 MB.

<a name="bkcontentsharing"> </a>

## Content sharing
   - **Screen sharing mode** You can select the screen sharing mode. This will be the size of the screen that will be used during a meeting that a user assigned with the policy can use.
   - **Allow a participant to give or request control** This allows all participants in a meeting to give and request control of screen sharing.
   - **Allow an external participant to give or request control** This allows an external (someone not part of your organziation) participant to give and request control of a meeting when the screen is being shared.
   - **Allow PowerPoint sharing** If you turn this on, users that schedule meetings can share PowerPoint slide decks during a meeting.
   - **Allow whiteboard** If you turn this on, the whiteboard will be available to meeting participants during a meeting.
   - **Allow shared notes** If you turn this on, shared notes will be available to meeting participants during a meeting.

<a name="bkparticipantsandguests"> </a>

## Participants & guests
   - **Allow anonymous users to dial-out** If you want meeting participants to dial-out to add someone else, you can turn this on. If you turn it off, none of the meeting participants can dial out from the meeting.
   - **Allow anonymous users to start meetings** If this setting is off, then only someone that has been authenticated to the meeting with a Teams app can start the meeting. If it's on, then anyone can start the meeting.
   - **Automatically admit users** If you turn this off, then meeting participants will be left in the lobby until someone starts the meeting. If it's on, meeting participants will be allowed to automatically join the meeting.

[Full article](meeting-policies-in-teams.md)
::: zone-end

### Related topics
[Messaging policies in Teams](messaging-policies-in-teams.md)