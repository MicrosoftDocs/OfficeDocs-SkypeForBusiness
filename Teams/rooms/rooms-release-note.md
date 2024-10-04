---
title: Release notes for Microsoft Teams Rooms
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: henrikalim
ms.date: 09/30/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
description: Admin can read the release notes for Microsoft Teams Rooms, which list cumulative improvements in Microsoft Teams Rooms.
ms.custom: seo-marvel-apr2020
---

# Release notes for Microsoft Teams Rooms

This article discusses cumulative improvements in Microsoft Teams Rooms on Windows and Android devices.

There are two types of updates for Teams Rooms: Teams Rooms app updates and Teams Web client.

For information about Teams Rooms app updates, select the **Teams Rooms on Windows** or **Teams Rooms on Android** tabs.

Teams Web client updates happen via the Teams web app delivery services. The Teams web client is a cloud-based service that doesn't require an update to the local UWP application installed on the device.

For more information on how Teams updates, see [Teams update process](../teams-client-update.md).

Teams Rooms is governed by the Modern Lifecycle Policy. For more information, see [Teams update process](../teams-client-update.md#servicing-agreement).

## [Teams Rooms on Windows](#tab/Windows)

## Teams Rooms on Windows version history

|Release |Published to <br/> Microsoft Store |
|--- |--- |
|[5.2.115.0](#521150-9262024)| 9/26/2024 |
|[5.1.28.0](#51280-882024) | 8/8/2024 |
|[5.1.24.0](#51240-7302024) | 7/30/2024 |
|[5.0.305.0](#503050-632024) | 6/3/2024 |
|[5.0.230.0](#502300-5232024) | 5/23/2024 |
|[5.0.111.0](#501110-4242024) | 4/24/2024 |
|[4.19.82.0](#419820-1312024) | 1/31/2024 |
|[4.19.57.0](#419570-11162023) | 11/16/2023 |
|[4.18.44.0](#418440-9202023) | 9/20/2023 |
|[4.18.35.0](#418350-8212023) | 8/21/2023 |
|[4.17.51.0](#417510-6282023) | 6/28/2023 |
|[4.16.40.0](#416400-3242023) | 3/24/2023 |
|[4.15.58.0](#415580-1102023) | 1/10/2023 |
|[4.14.24.0](#414240-922022) |9/2/2022 |
|[4.13.132.0](#4131320-822022) |8/2/2022 |
|[4.12.139.0](#4121390-7142022) |7/14/2022 |
|[4.12.138.0](#4121380-5262022) |5/26/2022 |
|[4.12.126.0](#4121260-4272022) |4/27/2022 |

## Teams Rooms on Windows feature introduction and issue resolution

Teams Rooms app updates happen either using the Microsoft Store or using [manual update](manual-update.md). Updates are applied to the Universal Windows Platform (UWP) application that is installed locally on the device.

Features with the :::image type="icon" source="../media/mtr-pro-icon.png"::: icon are available only with Teams Rooms Pro license.

### 5.2.115.0 (9/26/2024)
Introduced in this update:
- **Proximity based join experience improvements**: Proximity based join experience is updated to disable auto accepting all nudges from external or federated tenants. In addition, Teams Rooms on Windows with compatible consoles will support proximity join using ultrasound, providing an alternative to Bluetooth. [Learn more](/microsoftteams/rooms/proximity-join?tabs=portal).
- **Dynamic video tile resizing based on people count** :::image type="icon" source="../media/mtr-pro-icon.png"::: **:**  The room video tile on Teams desktop client dynamically adjusts size based on the number of people in the room. When one person is in the room, the tile matches the remote participant's size. With two or more people, the room tile expands to be four times larger. Room admins can enable or disable the people count. [Learn more](/microsoftteams/rooms/xml-config-file).
- **Microsoft Teams Rooms on Windows room preview shows Cloud IntelliFrame** :::image type="icon" source="../media/mtr-pro-icon.png"::: **:** The Preview video of room will show IntelliFrame when Cloud IntelliFrame is enabled for the room, to let in room participants be aware of how they appear to those online. [Learn more](/microsoftteams/devices/cloud-intelliframe).
- **Roster grouping for in-room participants through proximity join** :::image type="icon" source="../media/mtr-pro-icon.png"::: **:**  When joining a meeting in a Microsoft Teams Room on Windows with a companion device, in-room participants will be grouped under the room node. Participants must join through Proximity Join with Microsoft Teams Rooms. [Learn more](https://support.microsoft.com/en-us/office/microsoft-teams-rooms-windows-e667f40e-5aab-40c1-bd68-611fe0002ba2).
- **Native controls for Group Framing, Active Speaker and Edge-composed IntelliFrame:**  Allow users to natively toggle certain camera features provided by OEMs, including group framing, active speaker framing, and edge-composed IntelliFrame. [Learn more](https://support.microsoft.com/en-us/office/enhance-hybrid-meetings-with-microsoft-intelliframe-for-teams-rooms-97161377-b746-49dc-992f-97bbf0d590f7).
- **Breakout rooms support:** With breakout room support, Teams Rooms on Windows can be added to a breakout room as an attendee and moved in and out of the main room making it easy for breakout session coordination. [Learn more](https://support.microsoft.com/en-us/office/use-breakout-rooms-in-microsoft-teams-meetings-7de1f48a-da07-466c-a5ab-4ebace28e461).

Resolved issues: 
- Fixed a known issue where content and gallery were swapped, after reconnecting a screen on dual display setups.
- Fixed a known issue where the chat panel is empty after a reboot.
- Fixed an issue where sometimes, the on-screen keyboard failed to appear on the console.
- Fixed an issue where the app would restart after the device wakes up or while using meet now.

### 5.1.28.0 (8/8/2024)
- Bug fixes for GCC-High: authentication & Teams Admin Center connectivity

### 5.1.24.0 (7/30/2024) 

Introduced in this update:

- **Support for Windows 23H2** - Eligible devices will now be updated to Windows 11 23H2.
- **Text and UI resizing** - IT admins can adjust the size of the text and all other UI elements on the front-of-room display by changing the display scaling settings. Text and UI elements are resized and adjusted for all supported display resolution and scaling combinations (1080p resolution at 100-150% scaling, 4K resolution at 100-300% scaling). This capability is extended to support touch boards.
- Fixes for certain Windowing issues.
- Other bug fixes.
  
### 5.0.305.0 (6/3/2024) 

**This is a manual update only.** This update brings the new features released in updates 5.0.111.0 and 5.0.230.0 to GCC-High customers. 

### 5.0.230.0 (5/23/2024)

**This release is available for all Teams environments, however, GCC-High customers with this version installed won't see new features released from the previous update 5.0.111.0.**

This update contains essential bug fixes and performance improvements:
- Fixed an issue where Webview 2 runtime was failing to install after updating to app 5.0.111.0, thereby not getting the new features released in that update. 
- Fixed an issue where Teams Rooms app might not fill the display when the display was reconnected and the scaling settings with Console was not synced.
- Fixed an issue where a blank screen was displayed upon applying a custom theme.
- Fixed an issue where Screen sharing from a video teleconferencing device to a Teams Rooms for Windows device doesn't work.
- Fixed an issue where some devices failed to setup after a reset by using Zero touch Deployment with Windows Autopilot.
- The ability to change language is now enabled by default. Admins can turn off this feature by setting the Room language setting to 'False'.  [Please visit](/microsoftteams/rooms/xml-config-file) to learn more.

  
### 5.0.111.0 (4/24/2024)

**This release is available for all Teams environments, however, GCC-High customers with this version installed won't see any of the below mentioned new features.**

Introduced in this update:

- **New Teams on Teams Rooms** - This update brings the New Teams available on Teams Desktop to Microsoft Teams Rooms on  Windows. With the new Teams app now a part of Teams Rooms on Windows, all Teams Rooms devices can now utilize available resources to optimize room experience and rendering intelligent audio and video more reliably. The New Teams app has parity of experiences, and in addition all new Teams rooms experiences are built on new Teams app.
- **Zero Touch Deployment with Windows Autopilot and Pro Management Portal** :::image type="icon" source="../media/mtr-pro-icon.png":::. This update includes app support to enable the end-to-end deployment experience. 
- **Ability to change language on Microsoft Teams Rooms on Windows**. With this new feature, end users can change the language of the Microsoft Teams Rooms on the Microsoft Windows app. The language choices offered are the same as those that are offered in the Microsoft Teams desktop app. The language is reverted to the default language when it restarts. To enable this, you will need to set the Room language setting to 'True'. [Please visit](/microsoftteams/rooms/xml-config-file) to learn more.
- **Skype for business deprecation**. Back with the release of app 4.19.57.0, we had announced the end of support for Skype for Business (Server and Online) on Microsoft Teams Rooms. With this update, we have retired the XML settings for SfB as well as ability to sign in or support to Skype for Business meetings. 
- **Meeting Chat shown by default in Gallery View for Teams Rooms on Windows**. Meeting Chat is now shown by default when joining a Teams meeting with Teams Rooms on Windows in Gallery View, making it easier to see incoming chat messages on the front of room display. Admins can configure the default chat experience for a room, and users can make in-meeting changes to show or hide the chat using the touch console. 
- **Join meetings with a QR code**. Users can quickly join upcoming meetings by scanning a QR code on the Teams Room home screen using a mobile camera. Users will then enter the room companion mode experience on Teams mobile and the full meeting experience on Teams Rooms. Users can also scan the QR code to start an ad-hoc meeting or cast content from mobile to the front-of-room display. If the user does not have the Teams mobile app, they will be directed to download it after scanning the QR code. Cross-tenant meetings are supported when the organization setting and user policies allow it. IT admins can control the feature from the XML settings or the Teams admin center. [Learn more](/microsoftteams/rooms/teams-rooms-qr-codes).
- **4K display UI scaling for Teams Rooms on Windows**. 4K-enabled displays, including front of room displays and touch boards, are natively supported on the Teams Rooms experience. Note: 4K video isn't supported.
- **Improvements to Join with an ID**. Teams meetings continues to be the default option while the option to select joining Zoom meetings with an ID, and others to come, is visually clearer.
- **Meeting ID and passcode to join on Teams Rooms on Windows**. Admins can configure and require a meeting ID and passcode to join a meeting on Teams Rooms on Windows to ensure one more level of security and privacy. This feature is available with Teams Rooms Pro license.
- **End users can switch IntelliFrame on or off using Stage roster**.

- **Intelligent Speakers for All Rooms and Devices:** With this update, users can now enjoy enhanced productivity in any meeting space, regardless of the type of mic connected to Teams Room. Support to identify who said what during meetings, providing live attributed transcriptions. This helps Microsoft Copilot and AI notes to keep track of important information. This feature is now in public preview on Microsoft Teams Rooms on Windows.

- **Integration between Report a Problem and Pro Portal Management:** Admins can configure for easier tracking, via SendFeedbackToPMP XML setting, that when a user sends feedback through Report a Problem from a room with a Microsoft Teams Pro license, each feedback creates an event in the Teams Rooms Pro Management portal. 

> [!IMPORTANT]
> Please note that some systems maybe missing the minimum version of the Edge WebView2 runtime. Until Edge Webview2 runtimeversion 110.0.1587.63 or higher is installed, these devices will be missing some features.

### 4.19.82.0 (1/31/2024)

Introduced in this update:

- **Windows Autopilot and Auto-login preview** :::image type="icon" source="../media/mtr-pro-icon.png":::. This feature is now available for Pro Management Portal customers that were nominated for the preview. To sign up, reach out to your Microsoft Account team. This feature provides a seamless end to end setup experience for Microsoft Teams Rooms on Windows.
- App version information is now shown on the setup screens including One Time Passcode screen.
- Fixed a bug that causes video to freeze temporarily when using Yealink SmartVision 60.
- Other bug fixes and improvements.

### 4.19.57.0 (11/16/2023)

Introduced in this update:

- **End of support for Skype for Business server and legacy home screen UI**. Support for Skype for Business and Skype for Business + Microsoft Teams as meeting modes are no longer available, and settings that were required for this set up are removed. The legacy home screen experience is also no longer officially supported. Learn more at [End of support for connecting to Skype for Business server in Microsoft Teams Rooms on Windows](https://techcommunity.microsoft.com/t5/skype-for-business-blog/end-of-support-for-connecting-to-skype-for-business-server-in/ba-p/3915956).
- **Touch board form factor support**. Teams Rooms on Windows now support certified Touch board form factors like Surface Hub 3. Touch boards run Teams rooms touch experience on single screen.  Portrait mode/Rotation on Surface Hub 3 is in preview with more optimizations to follow. 
- **One time passcode (OTP) based setup**:::image type="icon" source="../media/mtr-pro-icon.png":::. One-time passcode (OTP) provides a new and simplified way to set up Teams Room on Windows. During the first-time setup experience, the installer is presented with an option to enter a One-time passcode instead of resource account credentials, eliminating the need to share room account passwords. OTP is then used to automatically fetch the resource account credentials and sign into Teams Rooms. Teams room admins can provision the OTP from the Teams Rooms Pro Management Portal.
- **Front Row Enhancement - Active video speaker promotion**. Front Row now promotes pinned or spotlighted participants to the center stage when there's no shared content in the single and dual display mode to make the most of empty space. For single display mode, when no one is pinned, spotlighted, or sharing content, the most recent active speaker video will be promoted to the center. In dual display mode, when no one is pinned, spotlighted, or sharing content, the two most recent active speaker videos will be promoted to the center on each screen. If someone is sharing content, the most recent active video speaker will be promoted on the right screen.
- **Support Joining a Teams Live Event as an Attendee**. To join a live event as an attendee and watch the streaming experience, follow the instructions on [Attend a live event in Microsoft Teams](https://support.microsoft.com/office/attend-a-live-event-in-microsoft-teams-a1c7b989-ebb1-4479-b750-c86c9bc98d84).
- **Teams Room on Windows content camera enhancements**. Teams rooms on Windows support content cameras that are [certified by Microsoft](content-camera.md?tabs=Windows#supported-cameras-and-settings) to share analog Whiteboard in rooms. Customers now have the additional choice to connect any Teams certified or any other camera as a content camera on Teams Rooms on Windows to allow ease of use.
- **Responsive calendar sizing**. The calendar size changes dynamically based on screen width and height to adapt to various front-of-room display sizes. Learn more at [Set up and manage Teams Rooms on Windows custom backgrounds](/microsoftteams/rooms/custom-backgrounds).

> [!NOTE]
> Microsoft cannot guarantee that cloud enhancement filters work consistently on content camera not certified by Microsoft, so customers must validate the experience before rolling it out.

### 4.18.44.0 (9/20/2023)

- This update resolves a problem that prevents the room display resolution and scaling setting (configured using XML) from working on version 4.18.35.0 when sometimes Windows resets it to the default display settings.

### 4.18.35.0 (8/21/2023)

Introduced in this update:

- **Cloud IntelliFrame**:::image type="icon" source="../media/mtr-pro-icon.png":::. Cloud IntelliFrame makes non-AI cameras smarter. With Cloud IntelliFrame, participants in the room appear similar to remote attendees, creating an immersive and engaging experience for everyone. Whether working from home or in the office, participants are able to see every facial expression and cue, as if they were there in person. 
- **Intelligent camera support**:::image type="icon" source="../media/mtr-pro-icon.png":::. IntelliFrame enables multi-stream video, face recognition of in-room participants, active speaker recognition, attributed voice-based transcription, and panoramic video on front-of-room (180-degree view) and center-of-room (360-degree view) cameras, taking Teams Rooms on Windows cameras to the next level of intelligence.
- **Front Row gallery improvement – video segmentation with a unified background**<sup>1</sup>:::image type="icon" source="../media/mtr-pro-icon.png":::. It removes individual backgrounds, adjusts video participant’s size, and applies a unified background for remote participants to make them appear as if they are in the same room. This reduces distractions and provides in-room meeting participants with better connection to remote participants in Teams meetings.
- **Spatial audio in the Front Row experience**<sup>2</sup>:::image type="icon" source="../media/mtr-pro-icon.png":::. Spatial Audio brings next-generation audio to the Front Row experience when connected to stereo speakers. This intelligent audio technology delivers a more natural and inclusive experience for in-room participants by playing audio from channel closer to physical location of remote participants on Front row layout, making it feel like remote people are in the room with them and reducing meeting fatigue.

<sup>1</sup> The feature is turned on by default. To disable the feature, use the following XML. Learn more at [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md). ```<IsFrontRowUnifiedBackgroundEnabled>false</IsFrontRowUnifiedBackgroundEnabled>```

<sup>2</sup> You can achieve the best spatial audio experience with [Teams-certified stereo speakers](certified-hardware.md?tabs=Peripherals) and by following guidance on designing a [Signature Teams Room](room-planning-guidance.md?tabs=emtr#signature-teams-room-1). The feature is turned off by default. To enable the feature, use the following XML. Learn more at [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md). ```<IsSpatialAudioEnabled>true</IsSpatialAudioEnabled>```

### 4.17.51.0 (6/28/2023)

Introduced in this update:

- Teams Rooms user interface refresh is applied by default.
- Enhanced custom backgrounds on home screen. For more information, see [Set up and manage Teams Rooms on Windows custom backgrounds](custom-backgrounds.md?tabs=Enhanced). :::image type="icon" source="../media/mtr-pro-icon.png":::
- Support for SIP/H323 dialing <sup>1</sup>  :::image type="icon" source="../media/mtr-pro-icon.png":::
- Update to Windows 11 22H2 for eligible devices, and Windows 10 22H2 for all others
- Choose your Together mode scene and select it for everyone :::image type="icon" source="../media/mtr-pro-icon.png":::
- Net Promoter Score survey at the end of some meetings
- Simplified Device Registration Process for Microsoft Teams Rooms Pro Management Portal. To learn more, visit [Enrolling a device into Pro Management](./enroll-a-device.md). :::image type="icon" source="../media/mtr-pro-icon.png":::

<sup>1</sup> Functionality is available through a CVI provider. Learn more at [Teams Rooms on Windows with SIP and H.323 devices](./meetings-with-sip-h323-devices.md).

### 4.16.40.0 (3/24/2023)

Introduced in this update:

- A revitalized Teams Rooms user interface. For more information, see [Microsoft Teams Rooms home screen design refresh](mtr-home-refresh.md).
- Enhanced View Switcher <sup>1</sup>.
- Support for Teams premium meetings protection policies (watermark, end-to-end encryption for meetings, and sensitivity labels) <sup>2</sup>.
- Increased default font size for the meeting interface.
- Support for joining Blue Jeans meetings. To learn more, visit [Enable Teams Rooms devices to join third-party meetings](third-party-join.md).

 <sup>1</sup> Functionality in the layout switcher is contingent upon the type of Teams Rooms license. For more information, see [A new look for Microsoft Teams Rooms on Windows](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/a-new-look-for-microsoft-teams-rooms-on-windows/ba-p/3726040).

 <sup>2</sup> Meeting organizers should have a valid license to use these policies. Learn more at [Microsoft Teams Premium licensing](../teams-add-on-licensing/licensing-enhance-teams.md).

### 4.15.58.0 (1/10/2023)

Introduced in this update:

- In-meeting notification improvement
- Meeting chat in Gallery, Large gallery, and Together mode <sup>1</sup> :::image type="icon" source="../media/mtr-pro-icon.png":::
- Start whiteboard in Teams meetings
- Fit-to-frame room video roster control
- Overflow meeting support
- Join Zoom meetings by ID via Direct Guest Join. Support for joining Zoom meetings by ID has been added in this release and will be enabled in the coming weeks.
- Quality fixes for third-party meetings (Direct Guest Join)
- Fix for license information in settings showing no license when Teams isn't signed in
- A new default wallpaper (Vivid Flag) and four other new wallpapers

<sup>1</sup> Administrator configuration for hiding meeting chat from all meeting layouts through XML can be found in [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

### 4.14.24.0 (9/2/2022)

Introduced in this update:

- Front row layout experience update
- Pin and hide room video
- Administrator configuration for turning off split gallery in dual-display Teams Rooms <sup>1</sup>
- Dual-display Teams Rooms can now display up to 18 participant video streams
- Support for Microsoft Teams Rooms Pro and Microsoft Teams Rooms Basic room licenses

<sup>1</sup> Administrator configuration for turning off split gallery through XML can be found in [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](../rooms/xml-config-file.md).

### 4.13.132.0 (8/2/2022)

Introduced in this update:

- Join Teams meeting using meeting ID
- End-to-end encryption for one-to-one Teams calls<sup>1</sup>
- Noise suppression in Teams meetings<sup>2</sup>
- Share tray experience update
- Mute and unmute status on your room video
- Admin setting for content only layout default  
- Modern authentication is on by default

 <sup>1</sup> Before you can turn on end-to-end encryption for calls from a Teams Rooms device, you need to configure the policy for the device's user account. You can update the user's policy from the Teams admin center or by using Teams PowerShell. For more information, see [Configure the policy for the Teams Rooms user account.](../teams-end-to-end-encryption.md)

 <sup>2</sup> Teams Rooms added support for noise suppression in release 4.12 with admin override.

> [!IMPORTANT]
> With this update, new Teams Rooms devices now default to using modern authentication when connecting to Microsoft Teams and Exchange Online.
>
> We strongly recommend that you test your Teams Rooms devices prior to end of August by turning on Modern authentication for their room accounts.
>
> This change helps prepare for the upcoming update in Exchange Online to turn off basic authentication starting October 1, 2022. For more information, see [Basic Authentication Deprecation in Exchange Online - May 2022 Update](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-authentication-deprecation-in-exchange-online-may-2022/ba-p/3301866).  

### 4.12.139.0 (7/14/2022)

Introduced in this update:

- Changes the version number to allow systems impacted by Windows [KB5013942](https://support.microsoft.com/topic/may-10-2022-kb5013942-os-builds-19042-1706-19043-1706-and-19044-1706-60b51119-85be-4a34-9e21-8954f6749504) to re-register the app so it can launch. There are no functional changes in this app version from 4.1.2.138.0.

> [!NOTE]
> For more information, see "Teams Rooms app fails to start after update" in [Known issues in Teams Rooms and devices](/microsoftteams/troubleshoot/teams-rooms-and-devices/rooms-known-issues).

### 4.12.138.0 (5/26/2022)

Introduced in this update:
- Bug fix for multiple simultaneous video streams from Jabra Panacast 50 (meeting video, content camera video)
- Cross-cloud meetings can now use default conferencing audio device
- Quality and reliability fixes

### 4.12.126.0 (4/27/2022)

Introduced in this update:

- IT admins can enroll a Teams rooms device to receive public preview features through XML setting. Once enrolled, the device starts to receive preview features. All features that go to preview are announced at [Microsoft Teams Public Preview - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-teams-public-preview/bd-p/MicrosoftTeamsPublicPreview)<sup>1,2</sup>  
- IT admin can set Front of Room display resolution and scaling remotely through XML settings<sup>2</sup>
- IT admin can disable Microsoft noise suppression through XML setting<sup>3</sup> 
- IT admin can override download folder cleanup on the device through registry key setting<sup>4</sup>
- Enabling users to join Teams meeting hosted on another cloud (that is, GCCH customer can join Teams meetings hosted on commercial cloud and vice versa) 
- Teams Rooms now blocks launching Microsoft Edge from URLs in PowerPoint Live as an added security measure for Teams rooms with touch displays 
- Meet now experience is improved to add instructions for users to invite users to the room 
- Support for Windows 10 21H2 feature release for Teams rooms

<sup>1</sup> Instructions for enrolling public preview MTR Windows devices can be found [here](../public-preview-doc-updates.md#enable-public-preview).

<sup>2</sup> For information about setting Front of Room display resolution and scaling remotely through XML, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](manage-front-room-scale-res.md).

<sup>3</sup> At this time, only admin setting is being released. User control and enablement of the noise suppression will follow post 4.12 release in May 2022.

<sup>4</sup> Device clean up instructions can be found [here](../rooms/rooms-operations.md#collecting-logs-on-microsoft-teams-rooms).

> [!NOTE]
> Windows 10 21H2 feature update will be updated after 7 days of installing the application or Admins can use manual update instead to install faster. Microsoft Teams Rooms application version 4.12 with these changes, will start to roll out in April 2022 and complete rollout in 2-3 weeks. The application updates are delivered through Windows store and the application is automatically installed. This is rolling out on Microsoft Teams Rooms on Windows only. 

What you need to do to prepare: You might want to notify your users about this updated experience and update your training and documentation as appropriate.

### 4.11.17.0 (3/3/2022)

Introduced in this update:

- Bug fix for camera framing, which will enhance all content in camera view.

### 4.11.12.0 (1/24/2022)

Introduced in this update:

- Front Row layout (Preview) for MTR on Windows<sup>1</sup>
- Admin setting to set Front row layout as default
- Meet Now and call app update for Teams only, Teams default client modes<sup>1,2</sup>
- Switch between multiple video cameras in Teams meetings<sup>1</sup>
- Default video camera setting
- Azure AD Premium 1 license inclusion in Room Standard and Premium SKUs
- Azure AD conditional access policies support<sup>3</sup>
- Remote PTZ controls support<sup>4</sup>

<sup>1</sup> These features are rolling out using Teams web client and will complete rollout in next couple of weeks. Read more about [Teams updates](../teams-client-update.md) for details.

<sup>2</sup> Teams rooms on Windows running in Microsoft Teams only or Skype for Business and Microsoft Teams (default) are updated with new Meet and Call experiences, however other modes aren't impacted by this update.

<sup>3</sup> This feature requires that IT admins configure Teams desktop client Remote PTZ controls app.

### Teams Rooms Web client update (December 2021)

Introduced in this update:

- Split video layout across dual Front of Room displays when content isn't being shared

### Teams Rooms Web client update (October 2021)

Introduced in this update:

- Unified roster control with Teams desktop client with structured meetings grouping, meeting options and controls for presenters/ attendees, raise hand sort order and ability to invite users from Chat or meeting invite directly from roster
- Universal bar call controls alignment with desktop client in meeting call controls, Layout button and meeting status information
- Dynamic gallery support for single and dual front of room displays
- Unified layout picker for front of room layout option consolidated
- Spotlight or Pin multiple participants in Teams meetings
- Large meetings support with presenter/ attendees controls accessible by tapping participant from roster
- Ability to lock a meeting for meetings where room is organizer, and awareness of meeting that is locked
- Presenter mode consumption support when a remote user shares content with presenter view option
- Reaction support in Teams meetings

> [!NOTE]
> Web client updates are available to all Teams Rooms with application versions 4.10 and 4.9. Admins will be able to enroll in Teams Rooms public preview program to get sneak peek of the web client features soon.

### 4.10.10.0 (10/1/2021)

Introduced in this update:

- Room remote allows users to control basic functionality of the room using Teams on their mobile \*
- Logitech scribe content camera support for BLE button for sharing into meeting
- Chat bubbles provide notifications for in meeting chat to bring attention to what's being said using meeting chat \*
- Large gallery and Together mode support is now available in GCC High

> [!NOTE]
> Deprecated 19H1 support. Min OS version supported by 4.10 is 19H2.
>
> \*These features are rolled out using Teams service and will work with all application versions greater than 4.9.
>
> To join the scheduled meeting both from Teams Mobile app and MTR-W find the room account in roster on the Teams Mobile app and press "Control this room" menu and you can control Call controls from the app.

### 4.9.12.0 (7/28/2021)

Introduced in this update:

- Microsoft Teams only mode is now available in application settings, so you don't need to set up a Skype for Business account anymore. In this mode, devices signed in to Teams only mode join Skype for Business meetings as a guest.
- Fix for HDMI audio causing lower call volume. HDMI audio feature is automatically enabled for all devices with application build 4.9.12.0.

> [!NOTE]
> With Skype for Business reaching end of life it is recommended to update to Teams only mode.

### 4.8.31.0 (05/12/2021)

Introduced in this update:

- Windows 10 20H2 support

> [!NOTE]
> Crestron UC-Engine (BIOS version date containing "KYSKLi") Teams Rooms have compatibility issues and updated drivers will be provided by system OEMs in the near future. Windows 10 20H2 won't be offered to these devices. For more information about Windows version support, see [Windows release support](./rooms-lifecycle-support.md#windows-release-support).

### 4.8.25.0 (04/22/2021)

Introduced in this update:

- Fix for an issue where room information on Teams Rooms consoles doesn't show up for room accounts that are hidden from the global address list (GAL)

> [!NOTE]
> GCCH customers can download the upgrade package from [Manually update a Microsoft Teams Rooms device](manual-update.md)

### 4.8.19.0 (04/06/2021)

Introduced in this update:

- Government Community Cloud High (GCCH) support for Teams Rooms. GCCH customers with existing Teams Rooms devices can download version 4.8.19.0 from [Manually update a Microsoft Teams Rooms device](manual-update.md)
- Join Zoom meetings with better video quality (720p support) and receive the video gallery of participants
- Skype for Business sign-in failure banner removed for Teams default mode. This change supports organizations removing Skype for Business infrastructure
- Teams meetings join link parsing now handles Microsoft Defender Advanced Threat Protection Safe Links to allow joining external Teams seamlessly
- Fix for shared content scaling issue in Skype for Business meetings when the sharer's PC has a custom DPI set in Windows
- Quality and reliability fixes

### 4.7.19.0 (02/03/2021)

Introduced in this update:

- Quality and reliability fixes

### 4.7.15.0 (12/11/2020)

Introduced in this update:

- Share HDMI audio to meeting participants in Teams meeting
- Prevent unmuting based on audio permissions when Teams Rooms joins as attendee. For more information, see [Manage attendee audio permissions in Teams Meetings](https://support.microsoft.com/office/manage-attendee-audio-permissions-in-teams-meetings-f9db15e1-f46f-46da-95c6-34f9f39e671a).
- Spotlight someone's video from Teams Rooms console and consume spotlighted video on room displays

### 4.6.23.0 (10/19/2020)

Introduced in this update:

- Fix for white half-screen when invoking On-screen keyboard in Teams meeting

### 4.6.20.0 (09/30/2020)

Introduced in this update:

- See more videos with 3x3 video gallery on front of room displays  
- Start local live closed captions from MTR
- Join Zoom meetings from Teams Rooms with Direct Guest Join (Preview)

> [!NOTE]
> 3x3 video gallery and local live closed captions are delivered through the Microsoft Teams service. These features are available to all Teams Rooms devices with application version 4.5.37.0 and above.

### 4.5.37.0 (08/14/2020)

Introduced in this update:

- Coordinated Meetings between Microsoft Teams and Surface Hub 2S
- Fix for Skype For Business sign-in failure when [Windows 10 update KB4565351](https://support.microsoft.com/help/4565351/windows-10-update-kb4565351) or [Windows 10 update KB4571709](https://support.microsoft.com/help/4571709/windows-10-update-kb4571709) is installed

### 4.5.35.0 (07/23/2020)

Introduced in this update:

- Join Cisco Webex meetings from Teams Rooms with Direct Guest Join
- Teams Admin Center enablement and auto-enrollment
- Windows 10 1909 release support
- Switch to video gallery layout even when content is present
- Virtual raise hands support for attendee and controls for presenter
- Adjustable default volume setting for conferencing and default speaker
- Search and call federated users (tenant) from Teams Room

> [!IMPORTANT]
> Version 4.5 is last release to support Windows 10 version 1803; future releases will not be offered to systems on Windows 10 version 1803. For more information about Windows version support, see [Windows release support](./rooms-lifecycle-support.md#windows-release-support).

### 4.4.63.0 (06/25/2020)

Introduced in this update:

- Quality and reliability fixes
- Fix for "application won't launch after update to 4.4.41.0" issue

### 4.4.41.0 (05/06/2020)

Introduced in this update:

- Reliability fixes for application start in Windows 10 Kiosk

### 4.4.25.0 (03/31/2020)

Introduced in this update:

- Modern authentication support for Exchange and Skype for Business
- Support for dynamic emergency calling for Teams (Service components required and released using Teams client rings)
- Ability to disable duplicate content out of meeting for dual displays rooms using XML
- Application splash screen
- Open Source Software (OSS) notices in device settings

### 4.3.42.0 (03/02/2020)

Introduced in this update:

- Policy updates for "Windows Updates for Business"
- Fix for device events reporting showing error in Azure Monitor

### 4.3.33.0 (1/10/2020)

Introduced in this update:

- A fix for a Window resizing/flickering issue seen in certain configurations
- Calendar processing for third-party meetings removed

### 4.3.23.0 (12/13/2019)

Introduced in this update:

- Auto-answer proximity-based calls and admin setting to control the feature
- Device Admin Settings UI refresh with addition of device configuration under About tab
- Room control back to main screen
- Meeting Room SKU available in GCC
- Content camera support for Surface Pro-based system (Minimum required app build: 4.2.4.0)

### 4.2.4.0 (10/07/2019)

Introduced in this update:

- Windows 10 1903 support. Windows 10 1903 update is offered in a few days after app update
- Fixes for On-screen keyboard not showing up reliably

### 4.1.22.0 (08/15/2019)

Introduced in this update:

- A new content camera feature that enables users to intelligently include a traditional whiteboard into their Teams meeting
- Additional improvements to the Console UI to reduce clutter and moved **Settings** into a new side bar that is accessed via More on the console
- Disabled share tray button if local content cable isn't connected or a content camera isn't connected
- Fixed an issue with the touch keyboard where it failed to appear the first time only after an MTR system restart
- Quality and reliability fixes

### 4.0.105.0 (07/10/2019)

Introduced in this update:

- Skype Room System store app rebrand to "Microsoft Teams Rooms"
- Microsoft Teams Rooms console user interface realigned to Microsoft Teams
- Theme update: only keep custom background image on front of room displays, while making console background a neutral color to ensure console UI controls meet color contrast—accessibility requirements
- Universal bar for in-meeting call controls for Teams calls/ meetings to provide consistent experience with Microsoft Teams PC/ Web/ Mobile clients<sup>1</sup>
- Call quality feedback rating after Teams calls/ meetings<sup>1</sup>
- Receive/render Microsoft Whiteboard on Microsoft Teams Rooms front of room display when shared from PC/ Web/ Mobile Teams client<sup>1</sup> <sup>2</sup>
- Removed support for Windows 10 Version 1809 upgrades due to compatibility issues with Microsoft Teams Rooms client. Windows 10 Version 19H1 support will be added in future releases

<sup>1</sup> Microsoft Teams service rollout using Teams rings. This feature might be available earlier or later than 4.0.105.0 client update.

<sup>2</sup> Requires IT admins to turn on Microsoft Whiteboard. Also, if you have a touch-enabled front of room display, you must calibrate multiple touch displays using Windows settings with device administrator sign-in to start using Microsoft Whiteboard for collaboration from a room display shared into a Teams meeting.

### 4.0.85.0 (04/8/2019)

Introduced in this update:

- Fixes an issue with the "give feedback" feature.
- Optimizations in preparation for the forthcoming Microsoft Teams Rooms device upgrade to Windows 10 Version 1809.

### 4.0.78.0 (03/14/2019)

Introduced in this update:

- Fix for "hang at app start-up" bug that affected devices on legacy Windows 10 RS2 build.

### 4.0.76.0 (03/04/2019)

Introduced in this update:

- DTMF keypad for Microsoft Teams P2P meetings and PSTN calls. To make Microsoft Teams your default calling client, admins must set IsTeamsDefaultClient to true.
- Pin a remote participant's incoming video to full screen on front of room display. Use "Pin" command from participant roster on the console.
- Improvements to Lobby notifications with addition of Front of Room notification.
- Front of Room display casting icon removed when Bluetooth beacon isn't enabled on Microsoft Teams Rooms device.
- Fix for volume control issue in Teams meetings.

### 4.0.64.0 (12/14/2018)

Introduced in this update:

- Display content on both Front of Room (FoR) displays on dual screen room systems.
- Theming and Front of Room user interface improvements.
- TLS 1.2 client-side support. For on-premises customers, enabling communication over TLS 1.2 for Microsoft Teams Rooms requires Skype for Business Server 2015 Cumulative Update 9 (CU9) or Skype for Business Server 2019 Cumulative Update 1 (CU1).

### 4.0.51.0 (11/17/2018)

Introduced in this update:

- Dual display (Front of Room) support for Teams Meetings.

### 4.0.31.0 (10/16/2018)

Introduced in this update:

- Quality and reliability fixes.

### 4.0.27.0 (10/1/2018)

Introduced in this update:

- Code changes necessary to prepare the Microsoft Teams Rooms app for later Windows 10 Version 1803 upgrade.
- Fix formatting issue with localized EULAs (specifically Norwegian) which prevents advancing beyond EULA OOBE setup window.
- Code changes required to make Microsoft Teams Rooms application run on legacy Lync Room Systems. See more [here](./lrs-migration.md).

### 4.0.19.0 (8/31/2018)

Introduced in this update:

- Hotfix for Crestron application not launching which would normally be accessible when the app button on a Crestron SR device is pressed. Microsoft Teams Rooms app restart required after installation of 4.0.19.0.

### 4.0.18.0 (08/27/2018)

Introduced in this update:

- "Report a Problem" feature improvements in Teams mode (equivalent of "Give Feedback" in Skype for Business mode).
- Enable ability to fall back from Teams to Skype for Business mode for SIP calls.
- Accessibility improvements (Narrator, Magnifier).
- Automatically restart app when required after XML provisioning changes are applied.
- Miscellaneous fixes.

### 4.0.8.0 (07/06/2018)

Introduced in this update:

- This update enables both Skype for Business *and* Teams meetings support on Room Systems devices. Teams is turned off by default once the update is applied. Admins can enable Teams locally in device settings or via a remote xml push.

### 3.1.115.0 (06/18/2018)

Introduced in this update:

- Fix to address error observed on some systems during app launch.

### 3.1.113.0 (06/13/2018)

Introduced in this update:

- Changes enabling Microsoft to more flexibly manage Windows Updates.
- No change to end-user experience.

### 3.1.112.0 (06/05/2018)

Introduced in this update:

- Fix to address console responsiveness issues observed on Surface Pro 2017-based devices connected to two front-of-room displays and video ingest
- Automated check to ensure that system is running latest provisioning script

### 3.1.104.0 (04/16/2018)

Introduced in this update:

- Fix to improve OSK (on-screen keyboard) behavior in Window 10 Version 1709-based systems
- Improvements to prepare for future operating system updates

### 3.1.100.0 (03/16/2018)

Introduced in this update:

- Application updated to improve telemetry

### 3.1.99.0 (03/14/2018)

Introduced in this update:

- Fixes an issue where intermittent meeting join issues may occur
- Fixes an issue known to result in a device "hang" experience

### 3.1.98.0 (3/8/2018)

Introduced in this update:

- Bug/Crash fixes to improve stability
- Support for variable-sized console
- Peripheral audio processing offloading (additional media allowlist)
- Optimizations that enable IT Pros to build do-it-yourself images with Windows 10 Version 1709 January Update and later.

### 3.0.16.0 (11/27/2017)

Introduced in this update:

- Fixes an issue with the "Give Feedback" feature.

### 3.0.15.0 (10/3/2017)

Introduced in this update:

- Support for [Polycom MSR Series](https://www.polycom.com/hd-video-conferencing/microsoft-video/msr-series.mdl) dock hardware
- Support for the [Logitech Brio](https://www.logitech.com/product/brio)
- Resolves an issue where displays (console and front-of-room) fail to enter sleep mode when there's no activity in the room

### 3.0.12.0 (9/1/2017)

Introduced in this update:

- Runs on a Surface Pro (2017) tablet
- Supports Windows 10 Enterprise Creator's Update (English language, build 1703)
- Support for Crestron SR dock hardware.
- OEM Support for Environment Controls (Crestron)

The 64-bit version of Windows 10 Enterprise Anniversary edition (English language, version 1607) is no longer supported as of Microsoft Teams Rooms release 3.0.12.0 (update 3).

### 3.0.8.0 (8/4/2017)

Introduced in this update:

- Resolves issues observed when searching for federated users through the Participants search field. Previous to this fix, search results for external federated users might not have resolved correctly and instead have returned incorrect results.

### 3.0.6.0 (7/7/2017)

Introduced in this update:

- Dual-Screen support (for legacy system parity)
- Themes (built-in themes and the ability to set custom theme)
- Ability to Give Feedback for public builds
- Improved Telemetry around meeting join reliability
- Improved OMS reporting
- Ability for IT Admin to configure devices remotely

### 2.0.2.0 (03/15/2017)

Introduced in this update:

- In-app user selection of meeting room audio and video USB devices
- Integrated room console status reporting for customers using Microsoft Operations Management Suite, now Azure Monitor

### Release to Market (12/7/2016)

**Feature(s):**

**Built for Skype for Business**

- One-touch join of Skype Meetings
- Skype Meeting experience optimized for rooms with screen-filling HD video and HD wide-band audio
- All participants can connect to the Skype Meeting using their device of choice from wherever they may be located
- Invite people from your directory where you can instantly see their availability or via a phone call
- Supports Skype for Business PSTN Conferencing and PSTN Calling to replace the stand-alone conference phone in your room

**Transform Any Meeting Room**

- Dedicated Skype Meeting app optimized for center of table touch controller and large front of room display
- Reuse existing investments in your front of room display or projectors
- Works in all types of meeting spaces from huddle spaces to large conference rooms
- Certified Skype for Business audio and video devices are available for various room sizes
- Built-in wired ingest to project desktop sharing to the room and to the Skype Meeting

**Easy to Deploy, Simple to Manage**

- Always-on appliance that automatically wakes up the displays when it detects people in the room
- Simple deployment and updating of the UWP (Universal Windows Platform) Skype Meeting App
- Windows AppLocker locks down the device to the Skype Meeting app
- Monitored and managed as a Windows 10 Enterprise device via Intune and Configuration Manager (MDM)
- Enterprise-grade reliability
- Low training effort of end-users due to familiar Skype user interface
- Runs on Surface Pro 4 tablet

## [Teams Rooms on Android](#tab/Android)

## Teams Rooms on Android version history

|Release  |Release date  |
|---------|---------|
|[1449/1.0.96.2024091202](#144910962024091202-september-2024) | September 2024 |
|[1449/1.0.96.2024080804](#144910962024080804-august-2024) | August 2024 |
|[1449/1.0.96.2024061103](#144910962024061103-june-2024) | June 2024 |
|[1449/1.0.96.2024042606](#144910962024042606-april-2024) | April 2024 |
|[1449/1.0.96.2024032804](#144910962024032804-april-2024) | April 2024 |
|[1449/1.0.96.2024030101](#144910962024030101-march-2024) | March 2024 |
|[1449/1.0.96.2024020802](#144910962024020802-february-2024) | February 2024 |
|[1449/1.0.96.2023120901](#144910962023120901-february-2024) | February 2024 |
|[1449/1.0.96.2023120801](#144910962023120801-december-2023) | December 2023 |
|[1449/1.0.96.2023111001](#144910962023111001-december-2023) | December 2023 |
|[1449/1.0.96.2023090601](#144910962023090601-october-2023) | October 2023 |
|[1449/1.0.96.2023062301](#144910962023062301-june-2023)     | June 2023        |
|[1449/1.0.96.2023060802](#144910962023060802-june-2023)     | June 2023        |
|[1449/1.0.96.2023050203](#144910962023050203-may-2023)     | May 2023        |
|[1449/1.0.96.2023041207](#144910962023041207-april-2023)     | April 2023        |
|[1449/1.0.96.2023031201](#144910962023031201-march-2023)     | March 2023        |
|[1449/1.0.96.2022120503](#144910962022120503-december-2022)     | December 2022        |
|[1449/1.0.96.2022090606](#144910962022090606-september-2022)     | September 2022        |
|[1449/1.0.96.2022072103](#144910962022072103-august-2022)     | August 2022        |
|[1449/1.0.96.2022051102](#144910962022051102-may-2022)     | May 2022        |
|[1449/1.0.96.2022011305](#144910962022011305-february-2022)     | February 2022        |
|[1449/1.0.96.2021070803](#144910962021070803-july-2021)     | July 2021        |
|[1449/1.0.96.2021051904](#144910962021051904-june-2021)     | June 2021        |

## Teams Rooms on Android feature introduction and issue resolution

> [!NOTE]
> There can be a delay between when features are released by Microsoft and when they become available on a device make and model. If an update isn't available on your device, check with your device manufacturer for information on when it might become available.

Features with :::image type="icon" source="../media/mtr-pro-icon.png"::: are only available with Teams Rooms Pro license.

### 1449/1.0.96.2024091202 (September 2024)

Resolved issues:

- When a secondary external camera is attached, users are unable to switch the room camera in meetings.
- Local HDMI content that is projected outside of a meeting gets automatically shared into a meeting.
- Incorrect Korean translation of calendar time slots.
- The Join button is not showing up correctly on the calendar for Direct Guest Join meetings.
- Various issues causing meetings to crash.
- Minor improvements and bug fixes. 
  
### 1449/1.0.96.2024080804 (August 2024)

Introduced in this update:

- **Custom backgrounds<sup>1</sup>**:::image type="icon" source="../media/mtr-pro-icon.png":::. IT admins can upload custom background images on the Teams admin center to reinforce their company brand on their Teams Rooms on Android devices. The main room display, extended room display, and touch console can each have their own specific background image. PNG, JPG, and JPEG formats are supported. This feature is only available with the Teams Rooms Pro license. [Learn more](/microsoftteams/rooms/custom-backgrounds-android).
- **Join Zoom meetings with an ID and passcode**. Users can now join Zoom meetings with an ID and a passcode on Teams Rooms on Android. Rooms must be configured to enable Direct Guest Join meetings. [Learn more](/microsoftteams/rooms/third-party-join).

Resolved issues:

- Joining meetings on Cisco devices results in meeting drops and returning to the home screen.
- Built-in Teams backgrounds are not downloading successfully.
- Tapping Meet now on Logitech TAP devices shows a notification that the app does not support launching on secondary displays.
- When joining Direct Guest Join meetings while the HDMI ingest cable is connected, the HDMI ingest feed is shown as the room video instead of the local room camera feed.
- Volume is increased and decreased by increments of 30 instead of 10 on Logitech devices.
- Participant video gets re-framed from fit-to-frame to fill-frame intermittently on Cisco devices.
- Various meeting and call reliability issues.

<sup>1</sup>Neat devices are excluded from this rollout of custom backgrounds due to an issue that is unique to Neat devices. Once the issue is resolved, custom backgrounds will be enabled for Neat devices in a later release. 

### 1449/1.0.96.2024061103 (June 2024)

Introduced in this update:

- Bug fixes and other improvements. 

### 1449/1.0.96.2024042606 (April 2024)

Introduced in this update:

- **Home screen refresh**. The Teams Rooms on Android home screen matches the look and feel of Teams Rooms on Windows, enabling users to engage with a consistent Teams Rooms interface. The touch console features six action buttons and shows the room calendar on the right side of the home screen. If the Bluetooth beaconing setting is enabled, a room tip appears at the bottom left corner of the front-of-room display and touch console for user education.
- **Join meetings with a QR code**. Users can quickly join upcoming meetings by scanning a QR code on the Teams Room home screen using a mobile camera. Users will then enter the room companion mode experience on Teams mobile and the full meeting experience on Teams Rooms. Users can also scan the QR code to start an ad-hoc meeting or cast content from mobile to the front-of-room display. If the user does not have the Teams mobile app, they will be directed to download it after scanning the QR code. Cross-tenant meetings are supported when the organization setting and user policies allow it. IT admins can control the feature from the device settings or the Teams admin center. [Learn more](/microsoftteams/rooms/teams-rooms-qr-codes).
- **4K local HDMI content sharing**. Users can consume HDMI content in 4K quality on Teams Rooms on Android devices that support 4K HDMI input when users project content to the front-of-room display without joining an online Teams meeting.
- **Give feedback support**. The Help button includes a Give feedback option that lets users share their opinions and ideas about Teams Rooms on Android with Microsoft, just like users can do so on Teams desktop, web, mobile, and Teams Rooms on Window clients. This feedback is used to improve the Teams experience. IT admins can enable or disable this feature for users and manage other feedback policies using PowerShell. [Learn more](/microsoftteams/manage-feedback-policies-in-teams).
- Performance improvements in meetings including when users share HDMI content. 

### 1449/1.0.96.2024032804 (April 2024)

Introduced in this update:

- Bug fixes for issues with launching whiteboard and meeting join failures. 

### 1449/1.0.96.2024030101 (March 2024)

Introduced in this update:

- Bug fixes for app crashes and an issue with the device restart banner that does not auto dismiss.  

### 1449/1.0.96.2024020802 (February 2024)

Introduced in this update:

- **Meeting ID and passcode**<sup>1</sup> :::image type="icon" source="../media/mtr-pro-icon.png":::. IT admins can configure and require users to enter a meeting ID and passcode for joining meetings to ensure a level of security and privacy. 
- **New calendar views**. A new look with expanded functionalities. Users can view the calendar for the current day and the next day. Any available time slots for 11 minutes or more are shown. A visual indicator (green/purple vertical bar) is added to each time slot for users to easily see whether a room is booked or available.
- **Improved view switcher for Front of Room display controls**. The updated interface for the view switcher menu provides users with more control of the front of room display(s) during a meeting. Users can customize the views to show or hide the meeting chat. For Front Row, users can select which meeting component is displayed on the left and right panel. IT admins can configure the default number of panels and the default component showing on the panel(s) using the local device setting.
- Support for Teams Premium security features including end-to-end encryption for meetings and sensitivity labels.
- Fix for an experience regression in the Call app including support for P2P call and group call.
- Reliability and other improvements.
- Removal of Calling settings from the Teams admin settings on the device, including auto dial and auto answer. The latest device configuration prior to the setting removal still applies. Once a device is reset, the functionality is no longer available, just as it is for new devices. 

<sup>1</sup> The Meeting ID and passcode feature fully rolls out in March 2024.  
  
### 1449/1.0.96.2023120901 (February 2024)

Introduced in this update:

- **Daily maintenance restart window**. By default, the device restarts anytime between 2:00 AM and 3:00 AM based on its local time zone. If the device is in use during this window and the window period ends, the restart is rescheduled the following day. IT admins can turn off this functionality or change the restart window from the device settings. Support for these admin controls is coming soon on the Teams admin center.
- Bug fixes and other improvements.

> [!NOTE]
> This release only applies to Logitech and DTEN devices. Support for additional device manufacturers will be added later.

### 1449/1.0.96.2023120801 (December 2023)

Introduced in this update:

- Bug fixes for app crashes and issues with daily maintenance restart window.

### 1449/1.0.96.2023111001 (December 2023)

Introduced in this update:

- **Daily maintenance restart window**. By default, the device restarts anytime between 2:00 AM and 3:00 AM based on its local time zone. If the device is in use during this window and the window period ends, the restart is rescheduled the following day. IT admins can turn off this functionality or change the restart window from the device settings. Support for these admin controls is coming soon on the Teams admin center.
- Bug fixes for app crashes and devices not showing up on Intune.
- Significant reduction in sign out errors and pairing issues due to Workplace Join failures, timeout issues, and memory leaks.

### 1449/1.0.96.2023090601 (October 2023)

Introduced in this update:

- Improvements to the pairing resiliency of the room system and the touch console.
- Other reliability improvements and bug fixes on authentication, smart camera controls, and proximity join.

### 1449/1.0.96.2023062301 (June 2023)

Introduced in this update:

- GCC-H support :::image type="icon" source="../media/mtr-pro-icon.png":::
- Smart camera controls :::image type="icon" source="../media/mtr-pro-icon.png":::
- Content camera :::image type="icon" source="../media/mtr-pro-icon.png":::
- Primary camera switching 
- Default meeting layout controls

### 1449/1.0.96.2023060802 (June 2023)

Introduced in this update:

- Fixes for console pairing issues

### 1449/1.0.96.2023050203 (May 2023)

Introduced in this update:

- Quality and reliability fixes

### 1449/1.0.96.2023041207 (April 2023)

Introduced in this update:

- Performance improvements and fixes for volume controls, meeting join latency, chat loading, and layout switching issues

### 1449/1.0.96.2023031201 (March 2023)

Introduced in this update:

- Join Teams meeting with ID
- Single tap ad hoc meetings
- Room reservation extension :::image type="icon" source="../media/mtr-pro-icon.png":::
- Front row layout :::image type="icon" source="../media/mtr-pro-icon.png":::
- Meeting chat in Gallery, Large gallery, and Together mode :::image type="icon" source="../media/mtr-pro-icon.png":::
- HDMI connect auto share controls
- HDMI audio share
- Collaborative annotations support
- Teams Premium watermark-enabled meetings support

### 1449/1.0.96.2022120503 (December 2022)

Introduced in this update:

- Whenever you want to brainstorm in the office, simply walk up and start whiteboarding using the new whiteboard button on the home screen. With just one touch, you can quickly launch Microsoft Whiteboard and start collaborating outside of a Teams meeting. Admins can enable and control this feature with the **Allow initiate Whiteboard** setting on the device.
- Seamlessly switch from local to online collaboration by selecting Start meeting on the local whiteboarding screen. This action kicks off an ad-hoc meeting and automatically presents the existing whiteboard. From there, you can add participants into the meeting and contribute across the same whiteboard in real-time.
- Microsoft Whiteboard can now be viewed side by side with remote meeting participants using the Content + Gallery layout. Whenever content sharing starts, Content + Gallery will now be the default layout regardless of the content type.
- Content sharing in a meeting is more accessible with the redesigned share menu. When you select **Share** in the meeting control bar, you can find all content options that can be shared in one place, including Microsoft Whiteboard. Sharing Microsoft Whiteboard in a meeting is also now supported on resource accounts. [Admins, see instructions on how to manage Microsoft Whiteboard sharing in Teams](/microsoft-365/whiteboard/manage-sharing-organizations)
- We're also introducing a new touch screen support that allows you to control the room system from both the touch display at the front of the room and the touch console, whichever is more convenient. Admins can enable this feature with the **Enable touch screen controls** setting on the device. To further enhance the meeting experience on large screen devices, 4K display is also now supported.
- Aside from optimizing touch experiences for local meetings, we're also enriching hybrid meetings through remote camera pan, tilt, and zoom controls support. Remote meeting participants can now control the zoom and orientation of a Teams Rooms camera directly from their desktop during a meeting. [Admins, follow these instructions for enabling this setting](/microsoftteams/meeting-policies-audio-and-video)
- Joining a meeting on a room device has also become more inclusive. With chat notifications, you can see incoming chat messages on the front-of-room display and participate in the meeting on equal grounds. Admins can enable this setting in the device settings, and you can temporarily disable this setting using the meeting control bar.

### 1449/1.0.96.2022090606 (September 2022)

Introduced in this update:

- Teams crops videos to make them fit your screen better. (Microsoft Teams Rooms are excluded from this cropping by default to give you an uncropped view of meeting rooms.) Learn more at [Adjust your view in a Teams meeting](https://support.microsoft.com/office/adjust-your-view-in-a-teams-meeting-9825091c-0e7d-4c2b-95f5-eba644f19175).
- Fit to frame automatically enabled for incoming videos from other Microsoft Teams Room devices.
- Improvements and bug fixes for video-related issues.
- Support for Microsoft Teams Rooms Pro and Microsoft Teams Room Basic licenses.
- For known issues and troubleshooting, see [Known issues in Teams Rooms and devices](/microsoftteams/troubleshoot/teams-rooms-and-devices/rooms-known-issues).
- Get more details about the latest update at [Microsoft 365 blog](https://www.microsoft.com/microsoft-365/blog/2022/09/06/meet-microsoft-teams-rooms-pro/).

### 1449/1.0.96.2022072103 (August 2022)

In partnership with Cisco, you'll be able to join Cisco WebEx meetings through Microsoft Teams. After you enable **Direct guest** **join** through settings, schedule a new Cisco WebEx meeting or forward an existing meeting to the Teams Room on Android. The meeting will appear on the calendar and will be available to join.

> [!NOTE]
> Direct guest join Cisco WebEx will be initially available on Poly. Other manufacturers will receive it shortly after.

For IT admins who want to learn more about known issues and troubleshooting Teams Rooms on Android, see [Known issues in Teams Rooms and devices](/microsoftteams/troubleshoot/teams-rooms-and-devices/rooms-known-issues).

### 1449/1.0.96.2022051102 (May 2022)

In partnership with Zoom, we're releasing an ability to join Zoom meetings through Microsoft Teams. After you enable **Direct guest** **join** through settings, schedule a new Zoom meeting or forward to an existing Zoom meeting to the Teams Room on Android. The meeting will appear on the calendar and will be available to join.

> [!NOTE]
> Direct guest join will be initially available on Logitech, Poly, and some Yealink devices. Other manufacturers will receive it shortly after.

To increase the flexibility of how you view people and content in a meeting, we're providing a way for participants to change the orientation of the videos when content is shared, or participants are spotlighted. If you see a strip of participants on the screen, you can change its location by selecting **Layout**.

For known issues and troubleshooting, read [Known issues in Teams Rooms and devices](/microsoftteams/troubleshoot/teams-rooms-and-devices/rooms-known-issues)

### 1449/1.0.96.2022011305 (February 2022)

Introduced in this update:

- Meetings now display more attendee videos and provide additional flexibility of what is shown on the Teams Room front-of-room displays. Here are a few significant improvements:
- Split gallery views in a dual screen meeting.
- Spotlight multiple attendees at once.
- Docked meeting controls.
- New reactions.
- You can view content in the room or share it into the meeting by plugging in an HDMI cable. Available for all certified devices with HDMI capability.
- Presenters and organizers are able to control camera and microphone access for all attendees.
- Five new wallpapers to choose from to customize your Teams Rooms on Android devices. These wallpapers will apply to the front-of-room displays in a single and dual screen configuration.
- Webinar presenters can now join and participate from the Teams Room on Android devices.
- To provide a more cohesive experience, all IT admin settings are combined into one group under device settings for easier room configuration.
- These settings are available only on shared room accounts and require a password to access.
- This functionality will be available on a select set of devices.
- A warning message will appear on the front-of-room display when the room is over capacity.
- This will initially be available only on these select devices: EPOS EXPAND Vision 3T, Yealink MeetingBar A20, Yealink MeetingBar A30.
- When someone checks in on a Teams panel devices and the previous meeting is running over, a notification will appear on the front-of-room display to inform those people in the room that their meeting is over, and that people are waiting for the room. (Must have a Teams panel device paired with the Teams Room device).

### 1449/1.0.96.2021070803 (July 2021)

Introduced in this update:

- Calling and meeting video optimizations
- Connectivity improvements between touch console, meeting room bar, and mobile room remote
- Access to the dial pad from a remote controller during calls and meetings
- Ability to send feedback and report a problem from the touch console

### 1449/1.0.96.2021051904 (June 2021)

Introduced in this update:

- Simplified sign-in screen
- IT Admins can do remote provisioning and sign-in of Teams Rooms from the Teams Admin Center
- Use your phone or a secondary Teams device as a remote for the Teams Room. Control mic, camera, volume, live captions, and layout settings via the secondary device
- Select Teams Rooms devices now support projecting your screen via HDMI cable
- Live captions now available for one-on-one calls
- Presenters and organizers can select to lock a meeting to prevent anyone else from joining the meeting. Go to **More** > **Lock** **meeting**
- Hide meeting titles in the calendar on certain Teams Rooms devices
- IT admins can now enable auto-answer for Teams Rooms when someone starts an instant meeting via **Meet** **now**
- 1080p resolution now supported in outgoing video on Logitech, Poly, and Yealink A-series devices

### 1449/1.0.96.2021032002 (April 2021)

Most Teams Rooms on Android devices are compatible with a touch console (for example Poly TC8). When paired with a Teams Rooms system, the console allows you to see the room calendar, join meetings, and place calls directly from the console. During meetings or calls, you'll be able to see current meeting participants, add new ones, switch content layouts, raise hands, and more

A full-day calendar view will show all scheduled meetings on the system and permit you to join meetings directly from the device. All existing calling and meeting functionality will move to the console and will be arranged along side the calendar.

> [!NOTE]
> If the touch console is connected, all actionable functionality will move to the console, but the calendar will remain visible on the connected display for quick reference.

The following features will be available to you when you sign in with your account (e.g. E5 licenses) into the Teams Rooms on Android systems:

- Start Microsoft Whiteboard and share the whiteboard in the meeting from the Teams Rooms device.
- Start recording during meeting or call.
- Enable background effects (blur background or use an image). This functionality is only available when a touch console isn't paired.

### 1449/1.0.94.2020102101 (December 2020)

Introduced in this update:

- Dual screen support. Some select hardware (e.g., Poly Studio X50) that supports dual display configuration can now have a dual display experience with Teams. It's particularly useful in meetings, where meeting participants will be presented on one display and content on the other
- Meeting gallery supports 9 participants. Now Teams Rooms on Android will show up to 9 participants on the meeting stage
- New layouts. Together mode and Large gallery layouts are now available under the existing Layout button during meetings. These additional layouts are made to highlight video participants better
- Spotlight. Teams Rooms on Android will present spotlighted participants as large tiles on the meeting stage similar to content. Only desktop Teams clients are capable of selecting spotlighted participants at this time
- Request to speak. Muted participants can now request to be unmuted by raising their hand during meetings
- Auto-answer. Teams Rooms on Android can answer calls or meeting invites automatically. This setting is available to shared configurations only and is located in Admin settings

---

<a name="See"> </a>
## See also

[Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Prepare your environment](rooms-prep.md)

[Support for Microsoft Teams Rooms Current Branch versions](rooms-lifecycle-support.md)

[Known issues](known-issues.md)

[Plan for Microsoft Teams Rooms](rooms-plan.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)
