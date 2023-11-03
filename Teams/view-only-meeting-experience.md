---
title: View-only meeting experience
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: christi.balaki
ms.date: 10/15/2020
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn about the Teams view-only meeting experience for admins, presenters, and attendees
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

# Teams view-only meeting experience

**APPLIES TO:** ✔️Meetings ✔️Webinars

Microsoft Teams allows up to 10,000 attendees to join a Teams meeting. After the capacity of the main meeting has been reached (which is when 1000 users enter a meeting), additional attendees will join with a view-only experience. Meeting organizers will begin seeing notifications for view-only experience around the 500 user mark.

Attendees who join the meeting first, up to the capacity of the main meeting, will get the full Teams meeting experience. They can share audio and video, see shared videos, and participate in meeting chat.

Attendees who join after the main meeting capacity has been reached will have a view-only experience.

Attendees will be able to join the view-only experience through desktop, web, and Teams mobile (Android and iOS).

> [!Note]
> Teams meetings don't use Microsoft eCDN. For more information, see [Microsoft eCDN onboarding checklist](/ecdn/integration/onboarding-checklist-for-tle-customers).

## Teams view-only experience controls

You enable the view-only experience using the [`Set-CsTeamsMeetingPolicy`](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet from the [SkypeForBusiness PowerShell module](/powershell/module/skype/) or at least version 2.0.0 of the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams).

> [!NOTE]
> This setting also affects webinars.

To enable the view-only experience, you can use the following PowerShell snippet:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -StreamingAttendeeMode Enabled
```

To disable the view-only experience, you can also use PowerShell.

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -StreamingAttendeeMode Disabled
```

## Impact to users

A user's experience will vary depending on several factors.

When the capacity of the main meeting has been reached, an attendee will be unable to join the meeting if any of the following are true:

- An administrator hasn't enabled the Teams view-only experience for either the organizer or for the entire tenant.
- The view-only attendee can't bypass the lobby. As an example, if an organizer of a meeting chooses to have only **People in my organization** bypass the lobby, and an attendee who is outside of the organization attempts to join as a view-only attendee, they won't be able to join.

When the capacity of the main meeting has been reached, the meeting organizer and presenters will see a banner informing them that new attendees might join as view-only attendees.

  ![the Teams client and banner message for organizers and presenters.](media/chat-and-banner-message.png)

When the capacity of the main meeting has been reached, meeting attendees will be informed on the pre-join screen that they're joining in view-only mode.

  ![the Teams pre-join screen and the message for participants telling them that they will join in view-only mode.](media/view-only-pre-join-screen.png)

If there's space, a user will always join the main meeting. If the main meeting reaches capacity, and one or more attendees leave the main meeting, the main meeting has available capacity. Attendees who join (or rejoin) the meeting will join the main meeting until it reaches capacity again. Attendees who are in the view-only experience won't automatically be promoted to the main meeting and can't be manually promoted to the main meeting.

If presenter and attendee roles have been set, and a presenter attempts to join a meeting after the main meeting has reached capacity, they'll join as a view-only attendee and have the same limitations as other view-only attendees. Support to ensure all presenters join the main meeting will roll out at a later date. The organizer, presenter, and co-organizer will always be guaranteed space in the main meeting.

## Impact to meeting presenters and organizers

Limitations for meeting presenters and organizers include:

- You'll have no information about the view-only attendee. We don't support E-discovery for view-only attendees.
- Users in the main meeting can't see the view-only attendees.
- You can't remove a view-only attendee from the meeting.

> [!Note]
> Attendee count will only reflect the people in the main meeting and not the people in the view-only room. Therefore, presenters can't get an exact count of who is in the view-only experience.

## Experience for view-only attendees

The Teams view-only experience allows attendees to:

- Listen to the participants in the main Teams meeting.
- See the video feed for the active speaker (if the active speaker is sharing video).
- See content being shared using the share desktop or screen functionality.

The view-only attendee won't be able to experience the following options in meetings:

- Join the meeting if the attendee doesn't have permission to bypass the lobby based on set lobby policies or options.
- Join the view-only room using Audio Conferencing.
- Join the view-only room using Microsoft Teams Rooms system or using Cloud Video Interop (CVI) services.
- Share their audio or video.
- See or participate in the meeting chat.
- See the video feed of meeting participants unless the participant is the active speaker.
- See PowerPoint files that are shared using the PowerPoint Live functionality or individual application shares (other than desktop or screen sharing).
- Raise their hand in the meeting.
- Send or see reactions.
- Interact with any 3P App integrating into the Teams Meeting, including Polls.
- Access to meeting recording.

## View-only feature limitations

- View-only attendees will only be able to see Live Captions on Desktop and Web. Only English Captions are supported at this time.
- View-only attendees can't register for Webinars.
- View-only attendees won't have Information Barrier support. If you need Information Barrier support in your organization, you should disable this feature. 
- View-only attendees will be supported by streaming technology.
- View-only attendees won't be included in the attendance report.
- View-only attendees will have a single video experience. They can see either the active speaker or the content being shared, but not both.
- We don't currently support **Gallery**, **Large gallery**, or **Together mode** layouts for view-only attendees.
- View-only attendees are only supported by the following lobby policies: 'People in my organization,' 'People in my organization and guests,' 'People in my organization, trusted organizations, and guests,' and 'Everyone.' If you use a lobby policy that does not support View-only attendees, View-only attendees will be rejected from the meeting. 
- View-only attendees won't have the same latency as a regular attendee. <sup>1</sup>

  <sup>1</sup> View-only attendees will be at a 30-second video and audio delay in the meeting.
  
## Networking Considerations

Teams View-Only meetings utilize the same platform as Teams live events. View-only attendees receive meeting content, audio, and video as TCP HTTPS streams. We strongly recommend that you bypass proxy infrastructure for Teams live events URLs and IP addresses. For more information, see [Azure CDN Coverage by Metro](/azure/cdn/cdn-pop-locations).
