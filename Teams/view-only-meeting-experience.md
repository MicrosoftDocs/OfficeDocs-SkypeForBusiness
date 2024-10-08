---
title: View-only meeting experience
ms.author: wlibebe
author: wlibebe
ms.reviewer: christi.balaki
ms.date: 9/26/2024
manager: pamgreen
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn about the Teams view-only meeting experience for admins, presenters, and attendees.
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

**APPLIES TO:** ✔️Meetings ✖️Webinars ✖️Town halls

Microsoft Teams supports up to 10,000 attendees in a meeting. Once the main meeting reaches capacity at around 900 users, additional attendees join with a view-only experience. Attendees in the view-only experience can view the meeting, but have limited access to meeting features. Meeting organizers see notifications for the view-only experience when around 500 users are in the meeting.

Initial attendees who join before the meeting capacity enjoy the full meeting experience. These attendees can share audio/video, see shared content, and participate in chat.

Attendees who join after the main meeting capacity is reached have a view-only experience. These attendees can join the view-only experience through desktop, web, and Teams mobile (Android and iOS).

As an admin, you can assign this policy to organizers, allowing the view-only experience for attendees who join their meetings after the 900-user capacity is reached. If you turn off the view-only experience, meeting attendance is limited to the first 1,000 attendees.

## Teams view-only experience controls

You enable the view-only experience using the [`Set-CsTeamsMeetingPolicy`](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet from the [SkypeForBusiness PowerShell module](/powershell/module/teams/) or at least version 2.0.0 of the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams).

To enable the view-only experience, use the following PowerShell script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -StreamingAttendeeMode Enabled
```

To disable the view-only experience, use the following PowerShell script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -StreamingAttendeeMode Disabled
```

## User experience

The user experience varies based on several factors.

When the capacity of the main meeting is reached, an attendee can't join the meeting if any of the following are true:

- You didn't enable the Teams view-only experience for either the organizer or for the entire tenant.
- The view-only attendee can't bypass the lobby. For example, if a meeting  organizer chooses to have only **People in my organization** bypass the lobby, an attendee outside of the org can't join the meeting as a view-only attendee.

When the capacity of the main meeting is reached, the meeting organizer and presenters see a banner informing them that new attendees might join as view-only attendees.

  ![the Teams client and banner message for organizers and presenters.](media/chat-and-banner-message.png)

When the capacity of the main meeting is reached, meeting attendees are informed on the pre-join screen that they're joining in view-only mode.

  ![the Teams pre-join screen and the message for participants telling them that they will join in view-only mode.](media/view-only-pre-join-screen.png)

Before the meeting reaches capacity, attendees always join the main meeting. Once the meeting reaches capacity, view-only attendees can't be promoted to the main meeting.

If presenter and attendee roles are set, presenters who join after capacity is reached in the main meeting become view-only attendees. These presenters have the same limitations as other view-only attendees. Organizers are always guaranteed space in the main meeting.

## Meeting presenter and organizer limitations

Limitations for meeting presenters and organizers include:

- They have no information about the view-only attendees. We don't support E-discovery for view-only attendees.
- Users in the main meeting can't see the view-only attendees.
- They can't remove a view-only attendee from the meeting.

> [!NOTE]
> Attendee count only reflects the attendees in the main meeting and not the view-only attendees. Presenters can't get an exact count of attendees in the view-only experience.

## Experience for view-only attendees

The Teams view-only experience allows attendees to:

- Listen to the participants in the main Teams meeting.
- See the video feed for the active speaker (if the active speaker is sharing video).
- See content being shared using the share desktop or screen functionality.

View-only attendees can't perform these actions in the meeting:

- Join the meeting if they don't have permission to bypass the lobby.
- Join the view-only meeting using Audio Conferencing.
- Join the view-only meeting using Microsoft Teams Rooms on Android system or using Cloud Video Interop (CVI) services.
- Share their audio or video.
- See or participate in the meeting chat.
- See the video feed of meeting participants unless the participant is the active speaker.
- See PowerPoint files that are shared using the PowerPoint Live functionality or individual application shares (other than desktop or screen sharing).
- Raise their hand in the meeting.
- Send or see reactions.
- Interact with any third-party App integrating into the Teams Meeting, including Polls.
- Access the meeting recording.

## View-only feature limitations

- View-only attendees can only see Live Captions on Desktop and Web. Only English captions are supported at this time.
- View-only attendees don't have Information Barrier support. If you need Information Barrier support in your organization, you should disable this feature.
- Streaming technology supports view-only attendees.
- View-only attendees have a single video experience. They can see either the active speaker or the content being shared, but not both.
- We don't currently support **Gallery**, **Large gallery**, or **Together mode** layouts for view-only attendees.
- The following lobby policies support view-only attendees: **'People in my org,'** **'People in my org and guests,'** **'People in my org, trusted orgs, and guests,'** and **'Everyone'**. If you use a lobby policy that doesn't support view-only attendees, they're rejected from the meeting.
- View-only attendees don't have the same latency as a regular attendee. <sup>1</sup>

  <sup>1</sup> View-only attendees have a 30-second video and audio delay in the meeting.
  
## Networking Considerations

Teams view-only meetings use the same platform as Teams live events. View-only attendees receive meeting content, audio, and video as TCP HTTPS streams. We strongly recommend that you bypass proxy infrastructure for Teams live events URLs and IP addresses. For more information, see [Azure CDN Coverage by Metro](/azure/cdn/cdn-pop-locations).

## Related topics

- [IT Admins - Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md)
- [Configure the Microsoft Teams meeting lobby for sensitive meetings](configure-lobby-sensitive-meetings.md)
