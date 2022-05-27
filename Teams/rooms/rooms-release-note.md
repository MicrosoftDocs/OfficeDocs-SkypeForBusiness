---
title: Release notes for Microsoft Teams Rooms (Windows)
ms.author: czawideh
author: cazawideh
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
description: Admin can read the release notes for Microsoft Teams Rooms, which list cumulative improvements in Microsoft Teams Rooms.
ms.custom: seo-marvel-apr2020
---

# Release notes for Microsoft Teams Rooms

This article discusses cumulative improvements in Microsoft Teams Rooms.

There are two types of updates for Teams Rooms: Teams Rooms app updates and Teams Web-client. 

Teams Rooms app updates happen either via the Microsoft Store or via [manual update](manual-update.md). This updates the Universal Windows Platform (UWP) application that is installed locally on the device.

Teams Web-client updates happen via the Teams web app delivery services. This is a cloud-based service that does not require an update to the local UWP application installed on the device.

For more information on how Teams updates, see [Teams update process](../teams-client-update.md)

Teams Rooms is governed by the Modern Lifecycle Policy. See [Teams update process](../teams-client-update.md#servicing-agreement) for more information.

## Version history

|Release |Published to <br/> Microsoft Store |
|--- |--- |
|4.12.138.0 |5/26/2022 |
|4.12.126.0 |4/27/2022 |
|4.11.17.0 |3/3/2022 |
|4.11.12.0 |1/24/2022 |
|Teams Web-Client release | December 2021 |
|Teams Web-Client release | October 2021 |
|4.10.10.0 |10/1/2021 |
|4.9.12.0 |07/28/2021 |
|4.8.31.0 |05/12/2021 |
|4.8.25.0 |04/22/2021 |
|4.8.19.0 |04/06/2021 |
|4.7.19.0 |02/03/2021 |
|4.7.15.0 |12/11/2020 |
|4.6.23.0 |10/19/2020 |
|4.6.20.0 |09/30/2020 |
|4.5.37.0 |08/14/2020 |
|4.5.35.0 |07/23/2020 |
|4.4.63.0 |06/25/2020 |
|4.4.41.0 |05/06/2020 |
|4.4.25.0 |03/31/2020 |
|4.3.42.0 |03/02/2020 |
|4.3.33.0 |1/10/2020 |
|4.3.23.0 |12/13/2019 |
|4.2.4.0 |10/07/2019 |
|4.1.22.0 |08/15/2019 |
|4.0.105.0 |07/10/2019 |
|4.0.85.0 |04/08/2019 |
|4.0.78.0 |03/14/2019 |
|4.0.76.0 |03/04/2019 |
|4.0.64.0 |12/14/2018 |
|4.0.51.0 |11/17/2018 |
|4.0.31.0 |10/16/2018 |
|4.0.27.0 |10/1/2018 |
|4.0.19.0 |08/31/2018 |
|4.0.18.0 |08/27/2018 |
|4.0.8.0 |07/06/2018 |
|3.1.115.0|06/18/2018 |
|3.1.113.0|06/13/2018 |
|3.1.112.0|06/05/2018 |
|3.1.104.0|04/16/2018 |
|3.1.100.0|03/16/2018 |
|3.1.99.0 |3/14/2018 |
|3.1.98.0 |3/8/2018 |
|3.0.16.0 |11/27/2017 |
|3.0.15.0 |10/3/2017 |
|3.0.12.0 |9/1/2017 |
|3.0.8.0 |11/16/2017 |
|3.0.6.0 |11/16/2017 |
|2.0.2.0 |03/15/2017 |
|RTM (1.0.8) |12/7/2016 |

## Microsoft Teams Rooms feature introduction and issue resolution

### 4.12.138.0 (5/26/2022)

Introduced in this update:
- Bug fix for multiple simultaneous video streams from Jabra Panacast 50 (meeting video, content camera video)
- Cross-cloud meetings can now use default conferencing audio device
- Quality and reliability fixes

### 4.12.126.0 (4/27/2022)

Introduced in this update:
- IT admins can enroll a Teams rooms device to receive public preview features through XML setting. Once enrolled, the device will start to receive beta features. All features that go to beta testing are announced at [Microsoft Teams Public Preview - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-teams-public-preview/bd-p/MicrosoftTeamsPublicPreview)<sup>1,2</sup>  
- IT admin can set Front of Room display resolution and scaling remotely through XML settings<sup>2</sup>
- IT admin can disable Microsoft noise suppression through XML setting<sup>3</sup> 
- IT admin can override download folder clean up on the device through registry key setting<sup>4</sup>
- Enabling users to join Teams meeting hosted on another cloud (i.e., GCCH customer can join Teams meetings hosted on commercial cloud and vice versa) 
- Teams rooms now blocks launching edge browser from URLs in PowerPoint Live as an added security measure for Teams rooms with touch displays 
- Meet now experience is improved to add instructions for users to invite users to the room 
- Support for Windows 10 21H2 feature release for Teams rooms   
- New Cortana entry point on home screen, Share/ present button is back 

> <sup>1</sup> Instructions for enrolling public preview MTR Windows devices can be found [here](../public-preview-doc-updates.md#enable-public-preview)
> 
> <sup>2</sup> Front of Room display resolution and scaling remotely through XML can be found [here](../rooms/xml-config-file.md#set-front-of-room-scale-and-resolution)
>
> <sup>3</sup> At this time, only admin setting is being released. User control and enablement of the noise suppression will follow post 4.12 release in May 2022. 
>
> <sup>4</sup> Device clean up instructions can be found [here](../rooms/rooms-operations.md#collecting-logs-on-microsoft-teams-rooms)
> 
> 
> [!NOTE]
> Windows 10 21H2 feature update will be updated after 7 days of installing the application or Admins can use manual update instead to install faster. Microsoft Teams Rooms application version 4.12 with these changes, will start to roll out in April 2022 and complete rollout in 2-3 weeks. The application updates are delivered through Windows store and the application is automatically installed. This is rolling out on Microsoft Teams Rooms on Windows only. 
What you need to do to prepare: You might want to notify your users about this updated experience and update your training and documentation as appropriate.

### 4.11.17.0 (3/3/2022)

Introduced in this update:
- Bug fix for camera framing which will enhance all content in camera view.

### 4.11.12.0 (1/24/2022)

Introduced in this update:
- Front Row layout (Preview) for MTR on Windows<sup>1</sup> 
- Admin setting to set Front row layout as default  
- Meet Now and call app update for Teams only, Teams default client modes<sup>1,2</sup>
- Switch between multiple video cameras in Teams meetings<sup>1</sup> 
- Default video camera setting 
- Cortana push-to-talk icon update on MTR console 
- Azure AD Premium 1 license inclusion in Room Standard and Premium SKUs 
- AAD conditional access policies support<sup>3</sup> 
- Cortana voice activation enabled by default in OOBE
- Remote PTZ controls support<sup>4</sup>

> <sup>1</sup> These features are rolling out using Teams web client and will complete rollout in next couple of weeks. Read more about [Teams updates](../teams-client-update.md) for details.
> 
> <sup>2</sup> Teams rooms on Windows running in Microsoft Teams only or Skype for Business and Microsoft Teams (default) are updated with new Meet and Call experiences, however other modes are not impacted by this update.
> 
> <sup>3</sup> See addition details on setting up  [AAD conditional access](../rooms/rooms-authentication.md#azure-ad-conditional-access) policies for Teams Rooms.
> 
> <sup>4</sup> This feature requires that IT admins configure Teams desktop client Remote PTZ controls app.
> 

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
- Ability to lock a meeting for meetings where room is organizer, as well as awareness of meeting that is locked
- Presenter mode (weatherman) consumption support when a remote user shares content with presenter view option
- Reaction support in Teams meetings 

> [!NOTE]
> Web client updates are available to all Teams Rooms with application versions 4.10 and 4.9. Admins will be able to enroll in Teams Rooms public preview program to get sneak peak of the web client features soon.

### 4.10.10.0 (10/1/2021)

Introduced in this update:
- Room remote allows users to control basic functionality of the room using Teams on their mobile *
- Logitech scribe content camera support for BLE button for sharing into meeting
- Chat bubbles provide notifications for in meeting chat to bring attention to what's being said using meeting chat *
- Large gallery and Together mode support is now available in GCC High
- New Skills added to Cortana, Add person by name to the meeting and Call by name 
- Cortana Push to Talk is enabled by default on all devices. To learn more, see [Cortana voice assistance in Teams](../cortana-in-teams.md).

> [!NOTE]
> Deprecated 19H1 support. Min OS version supported by 4.10 is 19H2.

> [!NOTE]
> *These features are rolled out using Teams service and will work with all application versions greater than 4.9.

> [!NOTE]
> To join the scheduled meeting both from Teams Mobile app and MTR-W find the room account in roster on the Teams Mobile app and press "Control this room" menu and you can control Call controls from the app.

### 4.9.12.0 (7/28/2021)

Introduced in this update:
- Microsoft Teams only mode is now available in application settings, so you don't need to set up a Skype for Business account anymore. In this mode, devices signed in to Teams only mode join Skype for Business meetings as a guest user.
- Fix for HDMI audio causing lower call volume. HDMI audio feature is automatically enabled for all devices with application build 4.9.12.0.

> [!NOTE]
> With Skype for Business reaching end of life it is recommended to update to Teams only mode.

### 4.8.31.0 (05/12/2021)

Introduced in this update:
- Windows 10 20H2 support 

> [!NOTE]
> Crestron UC-Engine (BIOS version date containing "KYSKLi") Teams Rooms have compatibility issues and updated drivers will be provided by system OEMs in the near future. Windows 10 20H2 won't be offered to these devices. For more information about Windows version support, see [Windows 10 release support](./rooms-lifecycle-support.md#windows-10-release-support).

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
- Cortana voice skills (Preview)
- Prevent unmuting based on audio permissions when Teams Rooms joins as attendee. For more information, see [Manage attendee audio permissions in Teams Meetings](https://support.microsoft.com/office/manage-attendee-audio-permissions-in-teams-meetings-f9db15e1-f46f-46da-95c6-34f9f39e671a).
- Spotlight someone's video from Teams Room console and consume spotlighted video on room displays

> [!NOTE]
> Cortana voice skills are available for select audio peripherals for tenants located in the United States. Additional countries or regions will be added in the future. For more information, see [Cortana voice assistance in Teams](../cortana-in-teams.md)

### 4.6.23.0 (10/19/2020)

Introduced in this update:

- Fix for white half-screen when invoking On-screen keyboard in Teams meeting

### 4.6.20.0 (09/30/2020)

Introduced in this update:

- See more videos with 3x3 video gallery on front of room displays  
- Start local live closed captions from MTR
- Join Zoom meetings from Teams Rooms with direct guest join (Preview)

> [!NOTE]
> 3x3 video gallery and local live closed captions are delivered through the Microsoft Teams service. These features are available to all Teams Rooms devices with application version 4.5.37.0 and above.

### 4.5.37.0 (08/14/2020)

Introduced in this update:

- Coordinated Meetings between Microsoft Teams and Surface Hub 2S
- Fix for Skype For Business sign-in failure when [Windows 10 update KB4565351](https://support.microsoft.com/help/4565351/windows-10-update-kb4565351) or [Windows 10 update KB4571709](https://support.microsoft.com/help/4571709/windows-10-update-kb4571709) is installed

### 4.5.35.0 (07/23/2020)

Introduced in this update:

- Join Cisco WebEx meetings from Teams Rooms with direct guest join
- Teams Admin Center enablement and auto-enrollment
- Windows 10 1909 release support
- Switch to video gallery layout even when content is present
- Virtual raise hands support for attendee and controls for presenter
- Adjustable default volume setting for conferencing and default speaker
- Search and call federated users (tenant) from Teams Room

> [!IMPORTANT]
> Version 4.5 is last release to support Windows 10 version 1803; future releases will not be offered to systems on Windows 10 version 1803. For more information about Windows version support, see [Windows 10 release support](./rooms-lifecycle-support.md#windows-10-release-support).

### 4.4.63.0 (06/25/2020)

Introduced in this update:

- Quality and reliability fixes
- Fix for "application won't launch after update to 4.4.41.0" issue

> [!NOTE]
> If your device doesn't automatically update to version 4.4.63.0, follow the steps in [Microsoft Teams Rooms application does not start after updating to version 4.4.41.0](https://support.microsoft.com/help/4565998/teams-rooms-application-does-not-start-after-update) to resolve the issue.

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

- A fix for a Window resizing/flickering issue that's seen in certain configurations
- Calendar processing for third-party meetings removed
- Cortana status setting removed

### 4.3.23.0 (12/13/2019)

Introduced in this update:

- Auto-answer proximity-based calls and admin setting to control this
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
- Additional improvements to the Console UI to reduce clutter and moved Settings into a new side bar that is accessed via More on the console
- Disabled share tray button if local content cable is not connected or a content camera is not connected
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

<sup>1</sup> Microsoft Teams service rollout using Teams rings. This feature may be available earlier or later than 4.0.105.0 client update

<sup>2</sup> Requires IT admins to turn on Microsoft Whiteboard. Also, if you have a touch-enabled front of room display, you must calibrate multiple touch displays using Windows settings with device administrator login to start using Microsoft Whiteboard for collaboration from a room display shared into a Teams meeting

### 4.0.85.0 (04/8/2019)

Introduced in this update:

- Fixes an issue with the "give feedback" feature
- Optimizations in preparation for the forthcoming Microsoft Teams Rooms device upgrade to Windows 10 Version 1809

### 4.0.78.0 (03/14/2019)

Introduced in this update:

- Fix for "hang at app start-up" bug that affected devices on legacy Windows 10 RS2 build.

### 4.0.76.0 (03/04/2019)

Introduced in this update:

- DTMF keypad for Microsoft Teams P2P meetings and PSTN calls. To make Microsoft Teams your default calling client, admins must set IsTeamsDefaultClient to true
- Pin a remote participant's incoming video to full screen on front of room display. Use "Pin" command from participant roster on the console
- Improvements to Lobby notifications with addition of Front of Room notification
- Front of Room display casting icon removed when Bluetooth beacon is not enabled on Microsoft Teams Rooms device
- Fix for volume control issue in Teams meetings

### 4.0.64.0 (12/14/2018)

Introduced in this update:

- Display content on both Front of Room (FoR) displays on dual screen room systems
- Theming and Front of Room user interface improvements
- TLS 1.2 client-side support. For on-premise customers, enabling communication over TLS 1.2 for Microsoft Teams Rooms requires Skype for Business Server 2015 Cumulative Update 9 (CU9) or Skype for Business Server 2019 Cumulative Update 1 (CU1).

### 4.0.51.0 (11/17/2018)

Introduced in this update:

- Dual display (Front of Room) support for Teams Meetings

### 4.0.31.0 (10/16/2018)

Introduced in this update:

- Quality and reliability fixes

### 4.0.27.0 (10/1/2018)

Introduced in this update:

- Code changes necessary to prepare the Microsoft Teams Rooms app for later Windows 10 Version 1803 upgrade
- Fix formatting issue with localized EULAs (specifically Norwegian) which prevents advancing beyond EULA OOBE setup window
- Code changes required to make Microsoft Teams Rooms application run on legacy Lync Room Systems. See more [here](./lrs-migration.md).

### 4.0.19.0 (8/31/2018)

Introduced in this update:

- Hotfix for Crestron application not launching which would normally be accessible when the app button on a Crestron SR device is pressed. Microsoft Teams Rooms app restart required after installation of 4.0.19.0.

### 4.0.18.0 (08/27/2018)

Introduced in this update:

- "Report a Problem" feature improvements in Teams mode (equivalent of "Give Feedback" in Skype for Business mode)
- Enable ability to fall back from Teams to Skype for Business mode for SIP calls
- Accessibility improvements (Narrator, Magnifier)
- Automatically restart app when required after XML provisioning changes have been applied
- Miscellaneous fixes

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
- Resolves an issue where displays (console and front-of-room) fail to enter sleep mode when there is no activity in the room

### 3.0.12.0 (9/1/2017)

Introduced in this update:

- Runs on a Surface Pro (2017) tablet
- Supports Windows 10 Enterprise Creator's Update (English language, build 1703)
- Support for [Crestron SR](https://www.crestron.com/products/line/sr-for-skype-for-business-room-system) dock hardware
- OEM Support for Environment Controls (Crestron)

The 64-bit version of Windows 10 Enterprise Anniversary edition (English language, version 1607) is no longer supported as of Microsoft Teams Rooms release 3.0.12.0 (update 3).

### 3.0.8.0 (8/4/2017)

Introduced in this update:

- Resolves issues observed when searching for federated users through the Participants search field. Previous to this fix, search results for external federated users may not have resolved correctly and instead returned incorrect results.

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

<a name="See"> </a>
## See also

[Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Prepare your environment](rooms-prep.md)

[Support for Microsoft Teams Rooms Current Branch versions](rooms-lifecycle-support.md)

[Known issues](known-issues.md)

[Plan for Microsoft Teams Rooms](rooms-plan.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)
