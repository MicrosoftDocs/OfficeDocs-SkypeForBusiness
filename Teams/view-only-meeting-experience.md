---
title: View-only meeting experience
author: cichur
ms.author: v-cichur
ms.reviewer: hao.moy
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

Microsoft Teams allows up to 20,000 attendees to join a Teams meeting. After the capacity of the main meeting has been reached, additional attendees will join with a view-only experience.

Attendees who join the meeting first, up to the capacity of the meeting, will get the full Teams meeting experience. They can share audio and video, see shared videos, and participate in meeting chat.

Attendees who join after the main meeting capacity has been reached will have a view-only experience.

> [!Note]
> The current limit for the number of people who can chat and call in to a meeting is 300 in WW and 250 in GCC, GCC High, and DoD.

## Impact to administrators

The view-only experience is enabled by default for any user with a license for the Advanced Communications add-on SKU. When a user with the Advanced Communications add-on creates a Teams meeting, that meeting will automatically support up to 20,000 attendees. No further configuration or setup is required.

> [!Note]
> Attendees who join the meeting don't need to have the Advanced Communications add-on. The add-on is only required by the meeting organizer.

Users without the Advanced Communications add-on will be limited according to the limits outlined in [Limits and specifications for Microsoft Teams](limits-specifications-teams.md).

### Disable Teams view-only experience

Administrators can disable the view-only experience using PowerShell. 

``powershell
Set-CsTeamsMeetingPolicy -Identity Global -StreamingAttendeeMode Disabled
Set-CsTeamsMeetingPolicy -Identity Global -StreamingAttendeeMode Enabled
```

In the future, it will also be possible for administrators to disable the view-only experience in the Teams admin center.

## Impact to users

A user's experience will vary depending on several factors.

When the capacity of the main meeting has been reached, an attendee will be unable to join the meeting if any of the following are true:

- An administrator has disabled the Teams view-only experience.
- The meeting organizer hasn't been assigned a license for the Advanced Communications add-on SKU.
- The attendee doesn't have permission to bypass the lobby.

When the capacity of the main meeting has been reached, the meeting organizer and presenters will see a banner informing them that the meeting capacity has been reached and that new attendees will join a view-only attendee.

  ![the Teams client and banner messsage for organizers and presenters](media/chat-and-banner-message.png)

When the capacity of the main meeting has been reached, meeting attendees will be informed on the pre-join screen that they're joining in view-only mode.

  ![the Teams pre-join screen and the message for participants telling them that they will join in view-only mode](media/view-only-pre-join-screen.png)

If there's space, a user will always join the main meeting. If the main meeting reaches capacity, and one or more attendees leave the main meeting, the main meeting has available capacity. Attendees who join (or rejoin) the meeting will join the main meeting until it reaches capacity again. Attendees who are in the view-only experience will not automatically be promoted to the main meeting and can't currently be manually promoted to the main meeting.

If presenter/attendee roles haven't been set, spaces in the main meeting are filled on a first-come, first-served basis. Once the meeting capacity has been reached, all other users will join with a view-only experience.

## Impact to meeting presenters

At launch, presenters will be treated in the same way as any other attendee. If a presenter joins after the main meeting has already reached capacity, they'll join in view-only mode and will, therefore, be unable to present.

Additionally, if a presenter leaves and then later rejoins the meeting, it's possible that they'll rejoin with the view-only experience if the main meeting capacity has been reached.

In the future, we plan to reserve space in the main meeting for the organizer and presenters.

Limitations for meeting presenters include the following:

- You'll have no information about the view-only attendee. We don't support E-discovery for view-only attendees.
- Users can't see the view-only attendees.
- You can't reserve room for presenters and special attendees in the inner meeting.
- You can't remove a view-only attendee from the meeting.

> [!Note]
> Attendee count will only reflect the people in the meeting and not the people in the overflow room. Therefore, presenters can't get an exact count of who is in the view-only experience.

## Experience for view-only attendees

The Teams view-only experience allows attendees to:

- Listen to the participants in the main Teams meeting.
- See the video feed for the active speaker (if the active speaker is sharing video).
- See content being shared using the share desktop functionality.

The view-only attendee won't be able to experience the following options in meetings:

- Join the meeting if the attendee doesn't have permission to bypass the lobby based on set lobby policies or options.
- Join the Overflow Room via Audio Conferencing.
- Join the Overflow Room via Microsoft Teams Room system or via Cloud Video Interop (CVI) services.
- Join the Overflow Room via the Teams Android mobile app.
- Share their audio or video.
- See or participate in the meeting chat.
- See the video feed of meeting participants unless the participant is the active speaker.
- See PowerPoint files that are shared using the native share PowerPoint functionality or individual application shares (other than desktop sharing).

## View-only feature limitations

- Supported platforms include desktop, web, and iOS. Android is coming soon.
- View-only attendees will always see live captions, regardless of the live-captions setting for that meeting.
- View-only attendees will be supported by streaming technology.
- View-only attendees won't be included in the attendance report.
- View-only attendees will have a single video experience. They can see either the active speaker or the content being shared, but not both.
- We don't currently support **Gallery**, **Large gallery**, or **Together mode** layouts for view-only attendees.  
- View-only attendees won't have the same latency as a regular attendee. <sup>1</sup>

  <sup>1</sup> View-only attendees will be at a 30-second video and audio delay in the meeting.  

## Related topics

- [Advanced communications add-on for Teams](teams-add-on-licensing/advanced-communications.md)
- [Limits and specifications for Teams](limits-specifications-teams.md)
