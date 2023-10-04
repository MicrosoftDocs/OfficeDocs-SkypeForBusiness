---
title:  Known issues in the new Microsoft Teams desktop client
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
|[**Known issues**](#known-issues)|Known issues we're working on.|
[**What features are changing in new Teams**](#what-features-are-changing)|Find out the changes you see in your improved customer experience.|
|[**Features that are coming soon**](#Features-that-are-coming-soon)|There are a few features that we're still working on.|

## Known issues

### General

- **Issue:** Presence and Chat/Call from a user's live persona card (LPC) in Outlook doesn't work when non-admin users install the new Teams client. These experiences are also broken while switching between new Teams and classic Teams.</br>
  **Workaround:** Confirm that the minimum prerequisites have been met, including installing the Office and Windows security updates as it applies to your organization.

### Apps

- **Issue**: Pin/Unpin and Apps "Drag and Drop" are missing in new Teams.

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
  Details you won't see include forwards, "show as," and assigned meeting categories. 

- **Issue:** For channel meetings, you won’t see a banner at the top of a channel when a meeting hosted there's active.</br>
  **Workaround**: Select Join in the channel conversation to join the meeting.

- **Issue:** In Restricted Meetings, attendee Microphone/Camera UBAR buttons appear enabled, however Attendees Audio/Video doesn't flow into the meeting.

- **Issue:** Network Device Interface (NDI) streaming is still pending and will be available later this year.  Live events present and attendee presenter and attendee are supported, however TLE Producer isn't. Users need to use classic Teams for TLE producer.

- **Issue:** Give and Take control not available.

- **Issue:** Currently there's no support of Cameo rendering, Sandaout/Weatherson layout in PowerPoint Live.


### MTMA

- **Issues:** New tenant invitations or status may not appear or get updated in the Me control for 24 hours.
  **Workaround:** Switch to classic Teams if you need to access that new tenant in less than 24 hours.

### Notifications

- **Issue**: If a user receives a message where @mention *Everyone* is used, it shows in their feed as a personal mention.</br>
   Details: The @mention Everyone feature is still pending for this release.

### Offline

- **Issue:** Some offline experiences are impacted if user has poor network 
- 
### Peripherals

- **Issue:**  BetterTogether calling and meeting support isn't available yet in new Teams.

- **Issue:**  If an audio device is connected to a PC over native bluetooth (without a dongle), call control buttons won't sync with new Teams.

- **Issue:** Teams button functionality (Raise Hands, Join Meeting, bring Teams app to foreground) not available. 

-  **Issue:**  Using running a side-by-side scenario may experience mute sync issues, call drops, and other syncing issues between their Peripheral and new Teams.

- **Issue:** While casting, the include audio radio button currently doesn't transfer audio.

- **Issue:**  Certified collaboration controller type device (that is, Presenter+) functionality unavailable.

### Presence

- **Issue:** Occasionally when a user is in a meeting, their Presence Status shows as Available.

- **Issue:**  Sometimes users aren't able to reset presence status.

- **Issue:** The preview thumbnail for Teams appears but there are no presence buttons.

- **Issue:**  When users switch from new Teams to classic, classic Teams crashes.

### Teams and Channels

- **Issue:** You won't see a banner at the top of a channel for channel meetings when a meeting hosted is active. You can still join the meeting from the channel.

- **Issue:**  Users of GCC High and DoD government clouds may see the option to create a shared channel, but it isn't yet available.  If you try to create a shared channel, an error will occur and the channel won't be created. 

- **Issue:** Toast notifications won't appear when Creating a team. The team is created.

- **Issue:** Can't create Team from the grid layout. </br>
  **Workaround:**  User the list view layout to create teams.

### Other areas:

- **Issue:** If a user has more than one tenant in their account, and if they sign out of their accounts and then join a meeting, it will not sign in with their primary tenant account. It signs in with any one of their accounts (including guest accounts).</br>
  **Workaround**: Before joining a meeting, sign in with primary tenant account.

- **Issue:** If a tenant has deployed proxy server, proxy server isn't supported yet and therefore the video background images download through proxy server will fail, user sees gray video background in this scenario.</br>
  **Workaround:** Use Background Blur as an alternative.

- **Issue:** Proxy authentication is currently in beta release. Contact support if you experience issues or switch to classic Teams.

- **Issue:** Signing out from Admin Disabled page doesn't go back to the sign in page - Admin Disabled page continues to show.

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
</br>

|Area|Description|
|:-----|:-----|
|Presence|-Manual hybrid presence in MeControl</br>- Duration for presence status</br>- Custom duratino for status message|
|People|Ability to @mention users in status note|
|LPC|Support opening of LPC from an @mention in status message in new Teams Me control|
|Teams Native Shell|- Set presence on taskbar and system tray</br>|
|Native Shell Auth|Show Account name and tenant name while displaying Presence information|
|Toasts|Show presence in system tray|
|Meeting|- Meeting start notification Support for Channel Meeting for anyone other than the original invite list </br>- Meetings Extensibility: Add annotations entry point in Presenter toolbar V2 in new Teams (Mac)|
|Rooms & Devices|- Enable pairing between Desktop App and companion devices (IPPhones, Displays)</br>- Native Bluetooth call control functions (aka HFP) - Integration/testing only</br>- Native Bluetooth Teams button (aka ASP over GATT)|
