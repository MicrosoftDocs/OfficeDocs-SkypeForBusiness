---
title:  Known issues in the new Microsoft Teams for the Mac
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 10/04/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: smylavarapu
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about any known issues for the new Microsoft Teams desktop client for the Mac
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Known issues in new Teams for the Mac

>[!Note]
> The features described in this article are available to [**Teams Public preview**](/microsoftteams/public-preview-doc-updates) and [**Microsoft 365 Targeted release**](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide#targeted-release) customers only. Features and content are subject to change. Check back for updates.


## Known issues

### General

- **Issue:** Presence and Chat/Call from a user's live persona card (LPC) in Outlook doesn't work when non-admin users install the new Teams client. These experiences are also broken while switching between new Teams and classic Teams.</br>
  **Workaround:** Confirm that the minimum prerequisites have been met, including installing the Office and Windows security updates as it applies to your organization.

### Apps

- **Issue**: Pin/Unpin and Apps "Drag and Drop" are missing in new Teams.
 
- **Issues:**  Apps can't be pinned to the left rail.

###  Calls

- **Issue:**  Increased power usage during calls may impact battery life.

### Chats

- **Issue:** You may still receive notifications on muted meeting chats.

- **Issue:** If you receive a message where @mention *Everyone* is used, it shows in your feed as a personal mention.</br>
  Details: The @mention Everyone feature is still pending.

- **Issue:** Possible duplication of Group Chats where non-blocking Group Chat call fails.  User could potentially create a new GroupChat with the same membership as one that already exists.


### Global readiness

- **Issue:** The UI lanauge and regional parameters are local.  They don't follow the OS, browser, or account. When a user changes the operation system UI language, the new choice isn't pushed to the new Teams app.
  **Workaround:**  Set the language or regional settings manually, or restart the new Teams app.

### Messages

- **Issues:** Message extensions in Powerbar aren't yet available.

### Meetings

- **Issue:** Some meeting details won’t appear in new Teams.</br>
  Details including forwards, "show as," and assigned meeting categories won't be seen.

- **Issue:** For channel meetings, you won’t see a banner at the top of a channel when a meeting hosted there's active.</br>
  **Workaround**: Select Join in the channel conversation to join the meeting.

- **Issue:** In Restricted Meetings, attendee Microphone/Camera UBAR buttons appear enabled, however Attendees Audio/Video doesn't flow into the meeting.

- **Issue:** Live events present and attendee presenter and attendee are supported, however TLE Producer isn't. Users need to use classic Teams for TLE producer.

- **Issue:** Give and Take control not available.

- **Issue:** Currently there's no support of Cameo rendering, Sandaout/Weatherson layout in PowerPoint Live.

- **Issue:**  The hover state is missing in the video icon in the channels header.

- **Issue:**  Meeting branding not working on Mac.

- **Issue:**  Cannot navigate to "join meeting" using keyboard actions.

- **Issue:**  At the top of the meeting window, the meeting title is not shown when joining for the first time. It only shows "Meeting now". </br>
  **Workaround:**  Rejoin the meeting; the meeting title shows as expected.

- **Issue:**  Presenter Modes are not available.

- **Issue:** Call Monitor Jumps. If you switch between virtual desktop, the call monitor will pull users back to the original desktop that the meeting is on.

- **Issue:**  Presenter bar can't be unpinned.


### MTMA

- **Issues:** New tenant invitations or status may not appear or get updated in the Me control for 24 hours.
  **Workaround:** Switch to classic Teams if you need to access that new tenant in less than 24 hours.

### NDI

- **Issue:** Network Device Interface (NDI) streaming is still pending and will be available later this year.  

### Notifications

- **Issue**: If a user receives a message where @mention *Everyone* is used, it shows in their feed as a personal mention.</br>
   Details: The @mention Everyone feature is still pending for this release.

- **Issue:** Notifications have a Send button rather than Reply.
  **Workaround:**  Select the send button if you want to reply.

### Offline

- **Issue:** Some offline experiences are impacted if user has poor network 
- 
### Peripherals

- **Issue:**  BetterTogether calling and meeting support isn't available yet in new Teams.

- **Issue:**  If an audio device is connected to a PC over native bluetooth (without a dongle), call control buttons won't sync with new Teams.

- **Issue:** Teams button functionality (Raise Hands, Join Meeting, bring Teams app to foreground) not available. 

-  **Issue:**  Using running a side-by-side scenario may experience mute sync issues, call drops, and other syncing issues between their Peripheral and new Teams.

- **Issue:** While casting, the include audio radio button doesn't transfer audio.

- **Issue:**  Certified collaboration controller type device (for example, Presenter+) functionality is unavailable.

### Presence

- **Issue:** Occasionally when a user is in a meeting, their Presence Status shows as Available.

- **Issue:**  Sometimes users aren't able to reset presence status.

- **Issue:** The preview thumbnail for Teams appears but there are no presence buttons.

- **Issue:**  When users switch from new Teams to classic, classic Teams crashes.

### Teams and Channels

- **Issue:** You won't see a banner at the top of a channel for channel meetings when a meeting hosted is active. You can still join the meeting from the channel.

- **Issue:**  Users of GCC High and DoD government clouds may see the option to create a shared channel, but it isn't yet available. If you try to create a shared channel, you receive an error and the channel won't be created.

- **Issue:** Toast notifications don't appear when Creating a team. The team is created.

- **Issue:** Can't create Team from the grid layout. </br>
  **Workaround:**  User the list view layout to create teams.

### Other areas:

- **Issue:** If a user has more than one tenant to their account, if they sign out of their accounts and then join a meeting, it will not sign in with their primary tenant account, but any one of their accounts (including guest accounts).</br>
  **Workaround**: Before joining a meeting, sign in with primary tenant account.

- **Issue:** Proxy server isn't supported yet. If a tenant has deployed proxy server, video background images downloaded through proxy server fail. The user sees only a gray video background.</br>
  **Workaround:** User can used Background Blur as an alternative.

- **Issue:** Proxy authentication is currently in beta release. Contact support if you experience issues or switch to classic Teams.

- **Issue:** Signing out from Admin Disabled page doesn't go back to the sign in page - Admin Disabled page continues to show.