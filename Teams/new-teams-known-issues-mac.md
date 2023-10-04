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
# New Teams for the Mac: Known issues 

>[!Note]
> The features described in this article are available to [**Teams Public preview**](/microsoftteams/public-preview-doc-updates) and [**Microsoft 365 Targeted release**](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide#targeted-release) customers only. Features and content are subject to change. Check back for updates.


### General

**Issue**: Presence and Chat/Call from a user's live persona card (LPC) in Outlook doesn't work when non-admin users install the new Teams client. These experiences are also broken while switching between new Teams and classic Teams.</br>
**Fix**: Confirm that the minimum prerequisites have been met, including installing the Office and Windows security updates as it applies to your organization.


### Apps

- **Issue**: Pin/Unpin and Apps "Drag and Drop" are missing in new Teams.

### Calendar

- **Issue:** There's no option to add a Channel calendar to a channel.</br>
  **Workaround**: Use classic Teams to use this feature.</br>

- **Issue**: Unable to add an app in scheduling form.</br>
  **Workaround**: Use classic Teams to use this feature.</br>

### Calls

- **Issue**: Increased power usage during calls may cause CPU throttling and negatively impact performance.</br>
**Workaround/details**: We're working to resolve this.

- **Issue**: Call toast stacking isn't supported by default in Windows 10.</br>
  **Workaround**: Open the action center to view secondary incoming call toasts.

### Chats

- **Issue:** Chat Notifications have a "send" button instead than a "reply" button.</br>
  **Workaround:**  Select the send button if you want to reply.

- **Issue:** You may still receive notifications on the muted meeting chats.

- **Issue:** You can't search for external users even if you enter full email address.

- **Issue:** If you receive a message where @mention *Everyone* is used, it shows in your feed as a personal mention.</br>
  Details: The @mention Everyone feature is still pending for this release.

### Global readiness

- **Issue:** The UI lanauge and regional parameters are local.  They do not follow the OS, browser, or account. When a user changes the operation system UI language, the new choice is not pushed to the the new Teams app.
  **Workaround:**  Set the lanugate or regional settings manually, or restart the new Teams app.

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

- **Issue:** In Restricted Meetings, attendee Microphone/Camera UBAR buttons appear enabled, however Attendees Audio/Video doesn't flow into the meeting.

- **Issue:** When a user raises their hand in Gallery view, two hands are displayed raised on their gallery (bottom left and upper right).

- **Issue:** Selecting Room Audio has a blank UI, and it's unable to detect rooms or search on the Join screen.

- **Issue:** In Settings->Devices, users can't preview their video. 

- **Issue:** Users won't be able to start a "Screen sharing call". Users on Windows 11 can’t share the app using the taskbar. </br>
  **Workaround**: Share the app or window using the share tray within Teams meeting. 

- **Issue:** Users can’t use the advanced presenter modes (Standout, Side-by-side, Reporter, Cameo).

- **Issue:** Users won't see the presenter toolbar when a screen sharing session is active.

-- **Issue**: Users aren't muted despite the tooltip message that says they are.  In large meetings of over 600+ attendees the microphone was still active. </br>
   **Workaround:**  Manually mute the call.

- **Issue:**  During call transfer, if the call ends prematurely then the banner is not updated correctly.</br>
  **Workaround:**  Being investigated. No current workaround.

- **Issue:**  Previously ended meeting shows as still running; Timer is still counting.

- **Issue:**  The hover state is missing in the video icon in the channels header.

- **Issue:**  Meeting branding not working on Mac.

- **Issue:**  Cannot navigate to "join meeting" using keyboard actions.

- **Issue:**  At the top of the meeting window, the meeting title is not shown when joining for the first time. It only shows "Meeting now". </br>
  **Workaround:**  Rejoin the meeting; the meeting title shows as expected.

- **Issue:**  Presenter Modes are not available.

- **Issue:** Call Monitor Jumps.  If you switch between virtual desktop, the call monitor will pull users back to the original desktop that the meeting is on.

- **Issue:**  Presenter bar can't be unpinned.

- **Issue:**   Unable to give or take control in a meeting.

## Messaging

- **Issues:** Large gap in messages in a chat, gap is not resolved by closing and relaunching the app.  During call transfer, if the call ends prematurely, the banner is not updated correctly.

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


## Other areas:

- **Issue:** If a user has more than one tenant to their account, if they sign out of their accounts and then join a meeting, it will not sign in with their primary tenant account, but any one of their accounts (including guest accounts).</br>
**Workaround**: Before joining a meeting, sign in with primary tenant account.
