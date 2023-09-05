---
title:  Known issues in the new Microsoft Teams desktop client
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 08/29/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: dansteve
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about any known issues for the new Microsoft Teams desktop client. 
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# New Teams desktop client: Known issues 

There are a few known issues we're working on.

### General

**Issue**: Presence and Chat/Call from a user's live persona card (LPC) in Outlook doesn't work when non-admin users install the new Teams client. These experiences are also broken while switching between new Teams and classic Teams.</br>
**Fix**: Confirm that the minimum prerequisites have been met, including installing the Office and Windows security updates as it applies to your organization.</br>Learn more about prerequisites here: [**Prerequisites for new Teams**](new-teams-deploy-using-policies.md#prerequisites).

### Accessibility

**Issue**: There may be accessibility gaps between new and classic Teams.
If you discover any accessibility gaps, select **Give Feedback**.

### Apps

- **Issue**: If custom apps are used, their icons are broken on the left pane.

- **Issue**: You can't install or uninstall any app in new Teams yet. Only apps installed in classic Teams show up in new Teams. </br>Workaround: Add your app in classic Teams. It will then appear in new Teams. 

- **Issue**: While all the basic capabilities within the app bar and flyout are supported, other advanced capabilities such as pinning, reordering, uninstalling, store navigation are still pending.

### Calendar

- **Issue:* There's no option to add a Channel calendar to a channel.</br>
  **Workaround**: Switch back to classic Teams to use this feature.</br>

- **Issue**: Unable to add an app in scheduling form.</br>
  **Workaround**: Switch back to classic Teams to use this feature.</br>

### Calls

- **Issue**: Increased power usage during calls may cause CPU throttling and negatively impact performance.</br>
**Workaround/details**: We're working to resolve this.

- **Issue**: Full HID capabilities (for example, device mute/unmute, LED sync) aren't yet supported.

- **Issue**: When using the “share screen” option to share content or in DND mode, call toast notifications will still pop up.

- **Issue**: Call toast stacking isn't supported by default in Windows 10.</br>
  **Workaround**: Open the action center to view secondary incoming call toasts.

### Chats

- **Issue:** The Organization tab isn't available on chat.</br>
  Details: The organization tab has moved to a person's Microsoft 365 contact card. To view your organization tab, select a user's profile picture and then Organization on their card. This aligns with how you view org charts in other Microsoft 365 apps, creating a more consistent experience.

- **Issue:** When you pop out a chat, the window may appear blank for a few moments.

- **Issue:** You may still receive notifications on the muted meeting chats.

- **Issue:** You can't search for external users even if you enter full email address.

- **Issue:** If you receive a message where @mention *Everyone* is used, it shows in your feed as a personal mention.</br>
  Details: The @mention Everyone feature is still pending for this release.

### Meetings

- **Issue** Commercial cloud customers are unable to join a meeting hosted in a Government cloud (including GCC, GCC High, DoD) using Cross Cloud Anon (CCA).</br>
  Details: This feature is still pending in new Teams. Switch back to classic Teams for this meeting.

- **Issue:** When using the “Share screen” option to share content, notifications will still pop up, even if you have notifications muted.</br>
Details: The meeting attendees may see preview content in those notifications.</br>
  **Workaround**: Use "Share window" or "PowerPoint Live" instead of "Share desktop".

- **Issue:** Some meeting details won’t appear in new Teams.</br>
  Details you won't see include forwards, "show as," and assigned meeting categories. 

- **Issue:** When you close a meeting window by selecting "X" in the upper-right corner, you won’t receive a prompt saying, “Are you sure you want to leave?”</br>
  **Workaround**: If you leave a meeting by accident, rejoin.

- **Issue:** For channel meetings, you won’t see a banner at the top of a channel when a meeting hosted there's active.</br>
  **Workaround**: Select Join in the channel conversation to join the meeting.

- **Issue:** When you disable attendee mic/camera, it may not look like it's disabled to attendees.</br>
  Details: When you disable attendee mic/camera for a meeting, attendees will still be able to select the microphone and camera icons in the meeting toolbar. However nothing happens until they come off mute or turn on their video.

- **Issue:** Some people are experiencing poor resolution when screen-sharing during a meeting.</br>
  Details: The product group is investigating this issue.

- **Issue:** An error occurs when joining a meeting whose organizer is from an organization for which you either (1) don't have an account signed-in into the new Teams client or (2) none of your signed-in accounts are guests there.</br>
  Details: Before joining the meeting, turn off preview using the toggle button on the title bar.

- **Issue:** When using the "Share screen" option to share content, toast notifications will still pop up, even if you have notifications muted.</br>
  Details: Meeting attendees may see preview content in those notifications.</br>
  **Workaround**: Use "Share window" or "PowerPoint Live" instead of "Share desktop."

- **Issue:** Some meeting details won't show up in new Teams.</br>
  Details include forwards, "show as," and assigned meeting categories.

- **Issue:** If you're using new Teams, you can't join or be assigned to a Breakout room as a participant. Meeting organizers: If you set up the Breakout Room in classic Teams, you won't be able to manage and open Breakout Rooms from new Teams.</br>
  **Workaround**: As an organizer, if you plan to run Breakout sessions, switch back to classic Teams and inform all participants that the meeting includes Breakout Rooms, and they all must switch to classic Teams to participate.

- **Issue:** In Restricted Meetings, attendee Microphone/Camera UBAR buttons appear enabled, however Attendees Audio/Video doesn't flow into the meeting.

- **Issue:** When a user raises their hand in Gallery view, two hands are displayed raised on their gallery (bottom left and upper right).

- **Issue:** Selecting Room Audio has a blank UI, and it's unable to detect rooms or search on the Join screen.

- **Issue:** In Settings->Devices, users can't preview their video. 

- **Issue:** Users won't be able to start a "Screen sharing call".</br>
  Details: Users on Windows 11 can’t share the app using the taskbar. </br>
  **Workaround**: Share the app or window using the share tray within Teams meeting. 

- **Issue:** Users can’t use the advanced presenter modes (Standout, Side-by-side, Reporter, Cameo).

- **Issue:** Users won't see the presenter toolbar when a screen sharing session is active.

### Multi-Tenant Multi-Account (MTMA)

- **Issue:** If you enable the sign-in restrictions policy, the new Teams client applies the policy on guest tenants. For example, if the policy is set to only allow sign in to Contoso, then Contoso users won't be able to switch their Teams app to any other org where they have been invited as a Entra B2B guest (formerly known as Azure AD B2B guest).</br>
**Workaround**: Add all the tenants where your users can be guested to your sign in restrictions policy.

- **Issue:** After successfully seeing the toggle and installing the new Teams, a user switches to a different tenant that doesn't have new Teams enabled. The user can't sign back into their home tenant.</br>
**Workaround**: Uninstall the new Teams and reinstall.

- **Issue:** When you open an app, you may see a banner saying you're signed in to that app and Teams with different accounts. For example, if you go to the Approvals app, the banner reads: "There’s a small chance you’re signed in to Approvals and Teams with different accounts."</br>
  **Workaround**: If you sign out and back in, the banner shouldn't appear anymore. [Learn more about this issue](https://support.microsoft.com/en-us/office/troubleshooting-sign-in-to-apps-in-teams-943e9035-6225-4b23-b902-e0118cec7841).

- **Issue:** New tenant invitations may not appear or get updated for 24 hours.</br>
  **Workaround**: Switch back to classic Teams if the user needs access earlier than 24 hours.


### Notifications

- **Issue**: If a user receives a message where @mention *Everyone* is used, it shows in their feed as a personal mention.</br>
  Details: The @mention Everyone feature is still pending for this release.

- **Issue**: Some Teams users aren't receiving notifications of chat mentions, meetings or calls.</br>
  Details: Review your Windows Notification settings. From the upper-right corner of the Teams desktop app, select the ellipsis (...) > Settings & Notifications > Open Windows notification settings. Find Microsoft Teams (work preview) in the apps list and set your preferences.

### Presence

- **Issue**: Occasionally when a user is in a meeting, their Presence Status shows as Available.

- **Issue**: Sometimes users aren't able to reset presence status.

- **Issue**: The preview thumbnail for Teams appears but there are no presence buttons.

### Teams and Channels

- **Issue**: You won't see a banner at the top of a channel for channel meetings when a meeting hosted is active. You can still join the meeting from the channel.

- **Issue**: Member and guest counts are occasionally displayed incorrectly in the members' tab.

- **Issue**: Limited options on Team Channel properties Dialog, including:
  - Pin, Manage Channel and Get Email Address available
  - Limited team site properties dialog – Hide, Manage Team, and Manage Tags available
  - Adding a tab to a channel isn't currently available.
  - Webhooks not supported

- **Issue**: Attendance report doesn't show after a meeting.</br>
  **Workaround**: To download, go to **Edit Meeting Details** > **Attendance** > **Download**. It will always download the latest meeting's report. Currently, there's no option to download a report of an older channel meeting.

## Other areas:

- **Issue**: Right-clicking on the back button (next to Search) doesn't bring the old history for you to navigate.

- **Issue**: If Windows (Focus/Do not Disturb) mode is on you won’t receive Teams notifications.</br>
  **Workaround**: Turn on the "Show Notification Banners" setting in System > Notifications > Microsoft Teams to receive Teams Notifications and enable it with Focus/Do not Disturb mode.

- **Issue:** If a user has more than one tenant to their account, if they sign out of their accounts and then join a meeting, it will not sign in with their primary tenant account, but any one of their accounts (including guest accounts).</br>
**Workaround**: Before joining a meeting, sign in with primary tenant account.
