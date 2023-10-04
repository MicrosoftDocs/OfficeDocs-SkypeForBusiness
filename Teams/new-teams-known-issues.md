---
title:  Known issues in the new Microsoft Teams desktop client
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 10/05/2023
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
# Known issues for new Teams Windows desktop 

This article covers known issues:

|What|Description|
|:-----|:-----|
|[**Known issues**](#known-issues)|Known issues we are working on.|
[**What features are changing in new Teams**](#what-features-are-changing)|Find out the changes you see in your improved customer experience.|
|[**Features that are coming soon**](#Features-that-are-coming-soon)|There are a few features that we are still working on.|

## Known issues


### Apps

- **Issue**: Pin/Unpin and Apps "Drag and Drop" are missing in new Teams.


### Calendar

- **Issue:** There's no option to add a Channel calendar to a channel.</br>
  **Workaround**: Use classic Teams to use this feature.</br>

- **Issue**: Unable to add an app in scheduling form.</br>
  **Workaround**: Use classic Teams to use this feature.</br>


### Chats

- **Issue:** You may still receive notifications on the muted meeting chats.

- **Issue:** You can't search for external users even if you enter full email address.

- **Issue:** If you receive a message where @mention *Everyone* is used, it shows in your feed as a personal mention.</br>
  Details: The @mention Everyone feature is still pending.


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

- **Issue:** For channel meetings, you won’t see a banner at the top of a channel when a meeting hosted there's active.</br>
  **Workaround**: Select Join in the channel conversation to join the meeting.

- **Issue:** When using the "Share screen" option to share content, toast notifications will still pop up, even if you have notifications muted.</br>
  Details: Meeting attendees may see preview content in those notifications.</br>
  **Workaround**: Use "Share window" or "PowerPoint Live" instead of "Share desktop."

- **Issue:** In Restricted Meetings, attendee Microphone/Camera UBAR buttons appear enabled, however Attendees Audio/Video doesn't flow into the meeting.

- **Issue:** Selecting Room Audio has a blank UI, and it's unable to detect rooms or search on the Join screen.

- **Issue:** Users won't be able to start a "Screen sharing call".</br>
  Details: Users on Windows 11 can’t share the app using the taskbar. </br>
  **Workaround**: Share the app or window using the share tray within Teams meeting. 


### Notifications

- **Issue**: If a user receives a message where @mention *Everyone* is used, it shows in their feed as a personal mention.</br>
  Details: The @mention Everyone feature is still pending for this release.


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


## What features are changing?

As we improve the client, the experience has been improved to align with similar features. Here are some of the changes you see.

|Classic Teams|New Teams|
|:-----|:-----|
|Purple toast notifications|You'll no longer see the purple "toast" notifications, and the taskbar icon will behave a little different. Notifications are via Windows native notifications to provide a consistent experience.|
|Adding a Wiki to a channel tab|You'll no longer see a Wiki app. Instead, select the Notes app.|
|Adding third party cloud storage service from Files app and Files tab in channels|You'll no longer see the "Add cloud storage" in the Files app on Teams' left navigation bar and within the Files tab in Teams channels. Now you can add the third party storage app directly from the Teams App Store.|
|Look up an organizational chart while in a 1:1 chat |Select a user’s avatar or profile photo anywhere in Teams and navigate to the organizational chart within the profile card.|
|Look up LinkedIn while in a 1:1 chat | Select a user’s avatar or profile photo anywhere in Teams and navigate to the LinkedIn tab within the profile card.|
|Adding a document library (DocLib) app to a tab in channels|Use the Sharepoint app instead. Then add the document library from there as a tab to the channel. Existing document libraries will automatically convert to a SharePoint document library on first use.|
|Activity tab in chat| No longer available.|
|Ability to save messages and files in Teams|No longer available. Will be replaced later this year by a similar feature.|
|Allow users to follow another user's presence, then notify them of availability|Select a user’s avatar or profile photo anywhere in new Teams to quickly get an overview of their online status, next available calendar slot in Outlook, work hours, local time, and work location (remote or office).|
|Ability to sign out from the notification area at the far right of the taskbar (system tray). |No longer available.|
|Settings dialog|Settings is now an app accessed from the More options menu **(...)** in the title bar. |
|About links in the More options menu (...) |About links are now in the Settings app under the **About Teams** category.|
|Help in the app bar|The Help entrypoint, including Help links and Give Feedback is now located under the More options menu **(...)** in the title bar.|
|Ability to build Teams personal apps usings Adaptive cards|No longer available.|
|General appearance changes|Colors, tooltip styles, and general appearance have been updated.|
|Ability to use tags in the "Add member" dialog.|There's now an advanced flow for tags.|
|Organization chart is a tab in chat|The organization chart is now located in the live persona card (LPC).|

## Features that are coming soon

### 