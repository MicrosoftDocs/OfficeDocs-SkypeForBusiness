---
title: View-only meeting experience
author: cichur
ms.author: v-cichur
ms.reviewer: christi.balaki
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn about the Teams view-only meeting experience for admins, presenters, and attendees
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Teams view-only meeting experience

> [!Note]
> View-only broadcasts will be available in Microsoft 365 E3/E5 and Microsoft 365 A3/A5. This feature will be enabled March 1,2021 as default OFF. This feature in Microsoft 365 Government G3/G5 plans will be available at a later date. You must change the default policy after that date if you want to have the feature be default ON. Use PowerShell to enable the policy `Set-CsTeamsMeetingPolicy -Identity Global -StreamingAttendeeMode Enabled`.

> [!Note]
> If your meeting or webinar hits capacity, Teams will seamlessly scale to accommodate a 10,000-person view-only broadcast experience. Plus, during this time of increased remote work, take advantage of even larger 20,000-person broadcasts through the end of this year.

Microsoft Teams allows up to 10,000 attendees to join a Teams meeting. After the capacity of the main meeting has been reached, additional attendees will join with a view-only experience.

Attendees who join the meeting first, up to the capacity of the meeting, will get the full Teams meeting experience. They can share audio and video, see shared videos, and participate in meeting chat.

Attendees who join after the main meeting capacity has been reached will have a view-only experience.

We have full Android and iOS mobile support for an attendee to join.

> [!Note]
> The current limit for the number of people who can chat and call in to a meeting is 300 in WW and 250 in GCC, GCC High, and DoD.

The view-only experience is disabled by default for any organizer who has E3/E5/A3/A5 SKU. No further configuration or setup is required.

## Disable Teams view-only experience

Administrators can disable the view-only experience using PowerShell.

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -StreamingAttendeeMode Disabled
```

In the future, it will also be possible for administrators to disable the view-only experience in the Teams admin center.

## Impact to users

A user's experience will vary depending on several factors.

When the capacity of the main meeting has been reached, an attendee will be unable to join the meeting if any of the following are true:

- An administrator has disabled the Teams view-only experience.
- The attendee doesn't have permission to bypass the lobby.

When the capacity of the main meeting has been reached, the meeting organizer and presenters will see a banner informing them that the meeting capacity has been reached and that new attendees will join a view-only attendee.

  ![the Teams client and banner message for organizers and presenters](media/chat-and-banner-message.png)

When the capacity of the main meeting has been reached, meeting attendees will be informed on the pre-join screen that they're joining in view-only mode.

  ![the Teams pre-join screen and the message for participants telling them that they will join in view-only mode](media/view-only-pre-join-screen.png)

If there's space, a user will always join the main meeting. If the main meeting reaches capacity, and one or more attendees leave the main meeting, the main meeting has available capacity. Attendees who join (or rejoin) the meeting will join the main meeting until it reaches capacity again. Attendees who are in the view-only experience won't automatically be promoted to the main meeting and can't currently be manually promoted to the main meeting.

If presenter/attendee roles haven't been set, spaces in the main meeting are filled on a first-come, first-served basis. Once the meeting capacity has been reached, all other users will join with a view-only experience.

## Impact to meeting presenters

Limitations for meeting presenters include:

- You'll have no information about the view-only attendee. We don't support E-discovery for view-only attendees.
- Users can't see the view-only attendees.
- You can't remove a view-only attendee from the meeting.

> [!Note]
> Attendee count will only reflect the people in the meeting and not the people in the view-only room. Therefore, presenters can't get an exact count of who is in the view-only experience.

## Experience for view-only attendees

The Teams view-only experience allows attendees to:

- Listen to the participants in the main Teams meeting.
- See the video feed for the active speaker (if the active speaker is sharing video).
- See content being shared using the share desktop functionality.

The view-only attendee won't be able to experience the following options in meetings:

- Join the meeting if the attendee doesn't have permission to bypass the lobby based on set lobby policies or options.
- Join the view-only room using Audio Conferencing.
- Join the view-only room using Microsoft Teams Room system or using Cloud Video Interop (CVI) services.
- Share their audio or video.
- See or participate in the meeting chat.
- See the video feed of meeting participants unless the participant is the active speaker.
- See PowerPoint files that are shared using the native share PowerPoint functionality or individual application shares (other than desktop sharing).

## View-only feature limitations

- View-only attendees will always see live captions, regardless of the live-captions setting for that meeting. Only English Captions are supported at this time.
- View-only attendees will be supported by streaming technology.
- View-only attendees won't be included in the attendance report.
- View-only attendees will have a single video experience. They can see either the active speaker or the content being shared, but not both.
- We don't currently support **Gallery**, **Large gallery**, or **Together mode** layouts for view-only attendees.  
- View-only attendees won't have the same latency as a regular attendee. <sup>1</sup>

  <sup>1</sup> View-only attendees will be at a 30-second video and audio delay in the meeting.  
