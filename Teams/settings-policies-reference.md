---
title: Teams policies reference
author: MikePlumleyMSFT
ms.author: mikeplum
manager: serdars
ms.reviewer: arundas
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-securecollab
f1.keywords: 
  - NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: This reference describes each of the policies available in Microsoft Teams
---

# Teams policies reference

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

This reference describes each of the policies available in Microsoft Teams. Each section is broken down by the corresponding policy area in the Teams admin center, along with any PowerShell-only policies that may also exist.

## Teams

### Teams policies

**Navigation:** Teams admin center > Teams > Teams policies

Teams policies are used to control what settings or features are available to users when they're using teams and channels.

:::image type="content" source="media/teams-policies-teams.png" alt-text="Screenshot of Teams team policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Create private channels|On|When **On**, team owners and members can create private channels that contain a subset of team members.|
|Create shared channels|On|When **On**, team owners can create shared channels for people within and outside the organization.|
|Invite external users to shared channels|On|When **On**, owners of a shared channel can invite external people in other Azure AD organizations to join the channel, if Azure AD cross-tenant access settings are configured.|
|Join external shared channels|On|When **On**, users and teams can be invited to external shared channels, if Azure AD cross-tenant access settings are configured.|

#### PowerShell-only Teams policies

|Parameter|Default|Description|
|:-----|:-----|:-----|
|AllowOrgWideTeamCreation|None|Determines whether a user is allowed to create an org-wide team. Set this value to **True** to allow or **False** to prohibit. Read more on [how organization-wide teams in Microsoft Teams help everyone collaborate](create-an-org-wide-team.md).|
|EnablePrivateTeamDiscovery|None|Determines whether a user is allowed to discover private teams in suggestions and search results. Set this value to **True** to allow or **False** to prohibit.|

#### Related topics to Teams policies

- [Manage channel policies in Microsoft Teams](teams-policies.md)
- [Set-CsTeamsChannelsPolicy](/powershell/module/skype/set-csteamschannelspolicy)

### Template policies

**Navigation:** Teams admin center > Teams > Template policies

Template policies control what team templates users see when they create a new team. The following templates are available to users by default:

- Manage a Project
- Manage an Event
- Onboard Employees
- Adopt Office 365
- Organize Help Desk
- Incident Response
- Crisis Communications
- Manage a Store
- Bank Branch
- Patient Care
- Hospital
- Quality and Safety
- Retail for Managers

#### Related topics to template policies

- [Manage team templates in the admin center](templates-policies.md)
- [Get started with team templates in the Teams admin center](get-started-with-teams-templates-in-the-admin-console.md)
- [Get-CsTeamTemplate](/powershell/module/teams/get-csteamtemplate)
- [Get-CsTeamTemplateList](/powershell/module/teams/get-csteamtemplatelist)

### Teams update policies

**Navigation:** Teams admin center > Teams > Template policies

Update policies are used to manage Teams and Office preview users that will see pre-release or preview features in the Teams app. Public preview isn't enabled by default.

:::image type="content" source="media/teams-update-policy.png" alt-text="Screenshot of Teams update policy.":::

You can also set the policy using the PowerShell `Set-CsTeamsUpdateManagementPolicy` cmdlet with the `-AllowPublicPreview` parameter.

#### Related topics to Teams update policies

- [Microsoft Teams Public Preview](public-preview-doc-updates.md)
- [Public Preview Features - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-teams-public-preview/bd-p/MicrosoftTeamsPublicPreview)

## Teams apps

### Permission policies

**Navigation:** Teams admin center > Teams apps > Permission policies

App permission policies control what apps you want to make available to Teams users in your organization.

:::image type="content" source="media/teams-apps-permission-policies.png" alt-text="Screenshot of Teams apps permission policies.":::

The types of apps to permission are divided into three categories - Microsoft apps, Third-party apps, and Custom apps. Each app category includes the following options for permissions:

- **Allow all apps** - Users can install and use any app published by your organization in the Teams app store.
- **Allow specific apps and block all others** - Allow specific apps you want to allow from the Teams app store and all other apps would be blocked.
- **Block specific apps and allow all others** - Add which apps you want to block from the Teams app store and all the other apps would be allowed.
- **Block all apps** - Users can't install apps that are published by your organization in the Teams app store.

#### Related topics to permission policies

- [Use app permission policies to control user access to apps](teams-app-permission-policies.md)
- [Overview of app management and governance in Teams admin center](manage-apps.md)
- [Information accessed and actions performed by apps and related admin considerations](app-permissions.md)
- [View app permissions and grant admin consent in Teams admin center](app-permissions-admin-center.md)
- [Resource-specific consent in Microsoft Teams](resource-specific-consent.md)
- [Set-CsTeamsAppPermissionPolicy](/powershell/module/skype/set-csteamsapppermissionpolicy)

### Setup policies

**Navigation:** Teams admin center > Teams apps > Setup policies

App setup policies control how apps are made available to a user with the Teams app.

:::image type="content" source="media/teams-apps-setup-policies-small.png" alt-text="Screenshot of Teams apps setup policy." lightbox="media/teams-apps-setup-policies.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Upload custom apps|Off|This setting determines if a user can upload a custom app package in the Teams app. Turning it on lets you create or develop a custom app to be used personally or across your organization without having to submit it to the Teams app store. Uploading a custom app also lets you test an app before you distribute it more widely by only assigning it to a single user or group of users. Read more about how to [Manage custom and sideloaded apps in Teams admin center](teams-custom-app-policies-and-settings.md).|
|User pinning|On|If you turn this setting on, the user’s existing app pins will be added to the list of pinned apps set in this policy. Users can rearrange, add, and remove pins as they choose. If you turn this setting off, the user’s existing app pins will be removed and replaced with the apps defined in this policy.|
|Installed apps|(none)|Choose which apps and messaging extensions you want installed in your users' personal Teams environment and in meetings they create. Users can install other available apps from the Teams app store.|
|Pinned apps|Activity, Chat, Teams, Calendar, Calling, Files|Choose the order apps are pinned in messaging extensions and the Teams app bar.|

#### Related topics to setup policies

- [Use app setup policies to pin and auto-install apps in Teams](teams-app-setup-policies.md)
- [Use of Teams apps for external attendees or guest from outside an organization](non-standard-users.md)
- [Understand Microsoft Teams apps and their capabilities](deploy-apps-microsoft-teams-landing-page.md)

## Meetings

### Meeting policies

Meeting policies are used to control what features are available to users when they join Microsoft Teams meetings.

#### Meeting scheduling

**Navigation:** Teams admin center > Meetings > Meeting policies

| Setting | Default | Description |
|:-----|:-----|:-----|
|Private meeting scheduling|On|When **On**, meeting organizers allow users to schedule private meetings.|
|Meet now in private meetings|On|Controls whether a user can start an instant private meeting.|
|Channel meeting scheduling|On|When **On**, meeting organizers allow users to schedule channel meetings within channels that the users belong to.|
|Meet now in channels|On|When **On**, meeting organizers allow users to start instant meetings within channels that the users belong to.|
|Outlook add-in|On|When **On**, meeting organizers allow users to schedule private meetings from Outlook. Read more about [the Teams Meeting add-in in Outlook](Teams-add-in-for-Outlook.md).|
|Meeting registration|On|When **On**, meeting organizers can require registration to join a meeting.|
|Who can register|Everyone|Determines who can register for meetings (if **Meeting registration** is **On**) - **Everyone** or **Everyone in the organization**.|
|Attendance report|Everyone, unless organizers opt-out|This setting allows meeting organizers the ability to see the toggle that turns on or off Attendance Reports within Meeting options.|
|Who's in the report|Everyone, but users can opt-out|This setting controls whether users in the meeting can opt in or out of offering their attendance information in the Attendance Report.|
|Attendance information collection|All information|This setting controls whether to show attendance time information (such as join times, leave times and in-meeting duration) for each participant in the meeting.|

#### Related topics to meeting scheduling

- [Manage who can start instant meetings and schedule meetings](manage-who-can-schedule-meetings.md)
- [Meetings, webinars, and live events](quick-start-meetings-live-events.md)

#### Meeting join & lobby

**Navigation:** Teams admin center > Meetings > Meeting policies

| Setting | Default | Description |
|:-----|:-----|:-----|
|Anonymous users can join a meeting|On|This per-organizer setting allows anyone to join meetings as an anonymous user by selecting the link in the meeting invitation.|
|Anonymous and dial-in users can start a meeting|Off|This setting is a per-organizer policy that allows for leaderless dial-in conferencing meetings. This setting controls whether dial-in users can join the meeting without an authenticated user from the organization in attendance.|
|Who can bypass the lobby|Everyone in my organization and guests|Controls who can join a meeting directly and who has to wait in the lobby until they're admitted by an authenticated user. This setting doesn't apply to dial-in users.|
|People dialing in can bypass the lobby|Off|Controls whether people who dial in by phone join the meeting directly without waiting in the lobby.|

##### PowerShell-only meeting join & lobby policies

|Parameter|Default|Description|
|:-----|:-----|:-----|
|BlockedAnonymousJoinClientTypes|(empty list)|This setting allows users to join a Teams meeting anonymously using a Teams client or using a custom application built using Azure Communication Services. When anonymous meeting join is enabled, both types of clients may be used by default. This optional parameter can be used to block one of the client types that can be used. If both clients are specified, this will be equivalent to disabling anonymous join completely.|

##### Related topics to meeting join & lobby policies

- [Control who can bypass the meeting lobby and access meetings](who-can-bypass-meeting-lobby.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

#### Meeting engagement

**Navigation:** Teams admin center > Meetings > Meeting policies

| Setting | Default | Description |
|:-----|:-----|:-----|
|Meeting chat|Turn it on for everyone|Controls which meeting attendees can participate in the meeting chat. When turned off for anonymous participants, they can read the chat but not post messages. Read more about how to [Manage messaging policies in Teams](messaging-policies-in-teams.md).|
|Q&A|On|When **On**, organizers can enable a question and answer experience for their meetings. Read more on [Q&A in Teams Meetings](manage-qna-for-teams.md).|
|Reactions|On|This setting controls whether users can use live reactions such as Like, Love, Applause, Laugh, and Surprise in Teams meetings.|

##### PowerShell-only meeting engagement policies

|Parameter|Default|Description|
|:-----|:-----|:-----|
|StreamingAttendeeMode|Enabled|This setting enables view-only mode for meetings that exceed the capacity of the main meeting. Read more about [Teams view-only meeting experience](view-only-meeting-experience.md).|

##### Related topics to meeting engagement policies

- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

#### Content sharing

**Navigation:** Teams admin center > Meetings > Meeting policies

Content sharing settings let you control the different types of content that can be used during Teams meetings that are held in your organization.

| Setting | Default | Description |
|:-----|:-----|:-----|
|Who can present|Everyone, but user can override|Controls what the default value is for **Who can  present?** in **Meeting options** for the Teams client.|
|Screen sharing mode|Entire screen|Controls whether desktop and window sharing is allowed in the user's meeting. Read more on how to [Configure desktop sharing in Microsoft Teams](configure-desktop-sharing.md).|
|Participants can give or request control|On|Controls whether the user can give control of the shared desktop or window to other meeting participants. This setting isn't supported if either user is in Teams in a browser.|
|External participants can give or request control|Off|Controls whether external participants can be given or request control of the shared desktop or window. This setting must be turned on in both organizations for an external participant to take control in Teams meetings hosted by people in your organization.|
|PowerPoint Live|On|Controls whether a user can share PowerPoint slide decks in a meeting. External participants, including anonymous, guest, and external access users, inherit the policy of the meeting organizer.|
|Whiteboard|On|Controls whether a user can share the Whiteboard in a meeting. External participants, including anonymous, guest, and external access users, inherit the policy of the meeting organizer. Read more on [how to manage the Whiteboard in Microsoft Teams](manage-whiteboard.md).|
|Shared notes|On|When **On**, attendees can create shared meeting notes through the meeting details.|

##### Related topics to content sharing policies

- [Meeting policy settings - Content sharing](meeting-policies-content-sharing.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

#### Watermark

**Navigation:** Teams admin center > Meetings > Meeting policies

 Watermarks can be useful for protecting confidential information shared in meetings. They're most useful when sharing information with people who don't normally have access to the information. Watermarks can be displayed in Teams meetings both for content shared on screen and for attendee video. For watermarks to be available in templates and sensitivity labels, and to the meeting organizer, they must be enabled.

| Setting | Default | Description |
|:-----|:-----|:-----|
|Watermark videos|Off|This setting controls watermarks on attendee videos. This setting requires a Teams Premium license.|
|Watermark shared content|Off|This setting controls watermarks on content shared on screen in a meeting. This setting requires a Teams Premium license.|

##### Related topics to watermark policies

- [Require a watermark for sensitive Teams meetings](watermark-meeting-content-video.md)
- [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

#### Recording & transcription

**Navigation:** Teams admin center > Meetings > Meeting policies

| Setting | Default | Description |
|:-----|:-----|:-----|
|Meeting recording|On|When **On**, users can record their Teams meetings and group calls to capture audio, video, and screen sharing activity. The meeting organizer and recording initiator need to have recording permissions to record the meeting.|
|Recordings automatically expire|On|When **On**, meeting recordings will automatically expire in the number of days shown in the Default expiration time setting.|
|Default expiration time|120|The default expiration time for new meeting recordings. From 1 to 99999 days. **Meetings automatically expire** must also be turned **On**.|
|Transcription|On|Controls whether captions and transcription features are available during playback of meeting recordings. The person who started the recording needs this setting turned on for these features to work with their recording.|
|Live captions|Not enabled but the user can override|This setting is a per-user policy and applies during a meeting. This setting controls whether the **Turn on live captions** option is available for the user to turn on and turn off live captions in meetings that the user attends.|
|Store recordings outside your country or region|Off|Controls whether meeting records can be permanently stored in another country or region.|

##### PowerShell-only recording & transcription policies

|Parameter|Default|Description|
|:-----|:-----|:-----|
|AllowCartCaptionsScheduling|DisabledUserOverride|This setting determines whether a user can add a URL for captions from a Communications Access Real-Time Translation (CART) captioner to provide real-time captions in meetings.|
|ChannelRecordingDownload|Allow|This setting controls how channel meeting recordings are saved, permissioned, and who can download them.|
|EnrollUserOverride|Disabled|This setting sets voice profile capture, or enrollment, in Teams settings for a tenant.|
|LiveInterpretationEnabledType|DisabledUserOverride|This setting allows meeting organizers to configure a meeting for language interpretation and select attendees to become interpreters that other attendees can select and listen to the real-time translation they provide.|
|MeetingInviteLanguages|None|This setting controls how the join information in meeting invitations is displayed by enforcing a common language or enabling up to two languages to be displayed. All Teams supported languages can be specified using language codes.|
|SpeakerAttributionMode|EnabledUserOverride|Speakers are identified in transcription. If enabled, users can override this setting and choose not to be identified in their Teams profile settings.|
|RoomAttributeUserOverride|(none)|This setting controls the voice-based user identification in meeting rooms. This setting is required for Teams Rooms account. Read more about how to [Manage voice recognition technology controls for an Intelligent Speaker](rooms/voice-recognition.md).|

##### Related topics to recording & transcription policies

- [Teams meeting recording](cloud-recording.md)
- [Use OneDrive for Business and SharePoint or Stream for meeting recordings](tmr-meeting-recording-change.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

#### Audio & video

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-policies-meetings-audio-video.png" alt-text="Screenshot of Teams meetings audio and video policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Mode for IP audio|Outgoing and incoming audio enabled|This setting controls whether incoming and outgoing audio can be turned on in meetings and group calls.|
|Mode for IP video|Outgoing and incoming video enabled|This setting controls whether incoming and outgoing video can be turned on in meetings and group calls.|
|IP video|On|This setting controls whether video can be turned on in meetings hosted by a user and in 1:1 and group calls started by a user. On Teams mobile clients, this setting controls whether users can share photos and videos in a meeting.|
|Local broadcasting|Off|Use NDI or SDI technology to capture and deliver broadcast-quality audio and video over your network.|
|Media bit rate (Kbs)|50000|This setting determines the media bit rate for audio, video, and video-based app sharing transmissions in calls and meetings for the user. It's applied to both the uplink and downlink media traversal for users in the call or meeting. This setting gives you granular control over managing bandwidth in your organization.|
|Network configuration lookup|Off|When **On**, roaming policies in Network topology will be checked.|
|Select video filters|All filters|Controls whether users can customize their video background in a meeting.|
|Live streaming mode|Disabled|Determines whether you provide support for your users to stream their Teams meetings to large audiences through Real-Time Messaging Protocol (RTMP).|

##### PowerShell-only audio & video meeting policies

| Parameter | Default | Description |
|:-----|:-----|:-----|
|AllowBreakoutRooms|True|This setting enables the Breakout Rooms functionality.|
|PreferredMeetingProviderForIslandsMode|TeamsAndSfb|Determines the Outlook meeting add-in availability to users on Islands mode. With the default value of `TeamsAndSfb`, users see both the Skype for Business and Teams add-ins. If you set this value to `Teams`, the Skype for Business add-in will be removed and only the Teams add-in will be shown.|
|TeamsCameraFarEndPTZMode|Disabled|Read more about how to to configure [Far end camera control (FECC) for pan tilt zoom (PTZ) cameras](meeting-policies-audio-and-video.md#far-end-camera-control-fecc-for-pan-tilt-zoom-ptz-cameras).|

##### Related topics to audio & video meeting policies

- [Meeting policy settings for audio & video](meeting-policies-audio-and-video.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

### Customization policies

**Navigation:** Teams admin center > Meetings > Customization policies

Use customization policies to customize the look of Teams meetings with your organization's logo, colors, or other visuals. These settings require a Teams Premium license.

:::image type="content" source="media/teams-meetings-customization-policies-small.png" alt-text="Screenshot of Teams meetings customization policies." lightbox="media/teams-meetings-customization-policies.png":::

#### Custom meeting visuals

| Setting | Default | Description |
|:-----|:-----|:-----|
|Currently Active|No|After adding a theme, this setting allows admins to define their branding by enabling a custom meeting theme. Read more on [Meeting themes for Teams meetings](meeting-themes.md).|
|Allow organizer to control meeting theme|Off|When this setting is on, meeting organizers can turn off meeting themes for specific meeting instances through the meeting options.|
|Custom backgrounds|Off|This setting gives you the ability to upload custom background images for Teams meetings that will appear on your end users' interfaces, ordered by the time of upload. Read how to enable [Custom meeting backgrounds for Teams meetings](custom-meeting-backgrounds.md).|

#### Related topics to customization policies

- [Microsoft Teams Premium - Overview for administrators](enhanced-teams-experience.md)
- [Custom Together Mode scenes in Teams](/platform/apps-in-teams-meetings/teams-together-mode)
- [Set up webinars in Microsoft Teams](set-up-webinars.md)

### Meeting template policies

**Navigation:** Teams admin center > Meetings > Meeting template policies

Meeting templates policies let you create and set up policies that control what templates people in your organization can see. Microsoft Teams custom meeting templates require a Teams Premium license.

:::image type="content" source="media/teams-meeting-template-policies.png" alt-text="Screenshot of Teams messaging template policies.":::

#### Related topics to meeting template policies

- [Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)
- [Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md)
- [Manage meeting templates in Microsoft Teams](manage-meeting-templates.md)
- [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)

### Live events policies

**Navigation:** Teams admin center > Meetings > Live events policies

Teams live events policies are used to turn on or off features, such as who can join a live event, if transcription is provided for attendees, or if recording live events is available for people who schedule and hold live events.

:::image type="content" source="media/teams-live-events-policies.png" alt-text="Screenshot of Teams live events policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Live events scheduling|On|When **On**, users in your organization can create and schedule live events in Teams.|
|Transcription for attendees|Off|Turning this setting on enables live event attendees to see live captions and subtitles during the event. This setting can only be applied to events produced in Teams.|
|Who can join scheduled live events|Everyone|This setting restricts who can attend live events. Teams permission types are updated based on the selection. For PowerShell, the [Set-CsTeamsMeetingBroadcastPolicy](/powershell/module/skype/set-csteamsmeetingbroadcastpolicy) cmdlet with `-BroadcastAttendeeVisibilityMode` gives the options to also use `EveryoneInCompanyAndExternal` or `InvitedUsersInCompanyAndExternal`.|
|Record an event|Organizer can record|This setting controls whether the event is recorded. Read more about [live event recording policies in Microsoft Teams](teams-live-events/live-events-recording-policies.md).|

> [!NOTE]
> GCC High and DoD customers must set up live events policies using Windows PowerShell. Read examples of how to [Use PowerShell to set live events policies in Microsoft Teams](/teams-live-events/set-teams-live-events-policies-using-powershell).

#### Related topics to live events meeting policies

- [What are Teams live events?](what-are-teams-live-events.md)
- [Plan for live events in Microsoft Teams](teams-live-events/plan-for-teams-live-events.md)
- [Live streaming events in Microsoft Teams](teams-stream-overview.md)
- [Configuring encoders for live event streaming in Microsoft Teams](teams-encoder-configuration.md)
- [Set-CsTeamsMeetingBroadcastPolicy](/powershell/module/skype/set-csteamsmeetingbroadcastpolicy)

## Messaging policies

**Navigation:** Teams admin center > Messaging policies

Messaging policies are used to control what chat and channel messaging features are available to users in Teams.

:::image type="content" source="media/teams-messaging-policies-small.png" alt-text="Screenshot of Teams messaging policies." lightbox="media/teams-messaging-policies.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Owners can delete sent messages|Off|When **On**, team owners can delete channel messages or posts that users have sent.|
|Delete sent messages|On|When **On**, users can delete messages they've sent in chat.|
|Edit sent messages|On|When **On**, users can edit messages they've sent in chat.|
|Read receipts|User controlled|When set as **User controlled** or **Turned on for everyone**, the sender of a chat message can be notified when their message was read by the recipient in 1:1 and group chats 20 people or fewer.|
|Chat|On|When **On**, users in your organization can use the Teams app to chat with other people.|
|Giphy in conversations|On|When **On**, users can include Giphys in chat conversations with other people.|
|Giphy content rating|Moderate|This setting controls the amount of adult content allowed with Giphys in chat.|
|Memes in conversations|On|When **On**, users can include Memes in chat conversations with other people.|
|Stickers in conversations|On|When **On**, users can include Stickers in chat conversations with other people.|
|URL previews|On|Controls automatic URL previewing in messages.|
|Translate messages|On|Turn this setting on to let users automatically translate Teams messages into the language specified by their personal language settings for Microsoft 365 or Office 365. Read more on [inline message translation in Microsoft Teams](inline-message-translation-teams.md)|
|Immersive reader for messages|On|When **On**, users can view messages in Microsoft Immersive Reader.|
|Send urgent messages using priority notifications|On|If you turn this setting on, users can send messages using priority notifications. Priority notifications notify users every 2 minutes for 20 minutes or until messages that are marked as urgent are picked up and read by the recipient.|
|Create voice messages|Allowed in chats and channels|This setting controls whether users can leave audio messages in chats and channels.|
|On mobile devices, display favorite channels above recent chats|Not enabled|When **Enabled**, this setting moves favorite channels to the top of the mobile device screen so that a user doesn't need to scroll to find them.|
|Remove users from group chats|On|Turn this setting on to let a user remove other users from a group chat. This feature lets you continue a chat with a smaller group of people without losing the chat history.|
|Suggested replies|On|When **On**, users get text predictions for chat messages.|
|Chat permissions role|Restricted permissions|Defines the supervised chat role of a user.|
|Users with full chat permissions can delete any message|Off|Use this setting to let users with full chat permissions delete any group or meeting chat message.|

### Related topics to messaging policies

- [Manage messaging policies in Teams](messaging-policies-in-teams.md)
- [Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md)
- [Manage external meetings and chat in Microsoft Teams](manage-external-access.md)
- [Native chat experience for external (federated) users in Microsoft Teams](native-chat-for-external-users.md)
- [Set-CsTeamsMessagingPolicy](/powershell/module/skype/set-csteamsmessagingpolicy)

## Voice

### Calling policies

**Navigation:** Teams admin center > Voice > Calling policies

Calling policies are used to control what calling features are available to people in Teams.

:::image type="content" source="media/teams-calling-policies-small.png" alt-text="Screenshot of Teams calling policies." lightbox="media/teams-calling-policies.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Make private calls|On|This setting controls all calling capabilities in Teams. Turn this setting off to turn off all calling functionality in Teams.|
|Cloud recording for calling|Off|This setting allows you to control whether call recording is available for your users.|
|Transcription|Off|This setting allows you to control whether post-call transcriptions are available for your users.|
|Call forwarding and simultaneous ringing to people in your organization|On|Controls whether incoming calls can be forwarded to other users or can ring another person in your organization at the same time.|
|Call forwarding and simultaneous ringing to external phone numbers|On|Controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time.|
|Voicemail is available for routing inbound calls|User controlled|When set to **Enabled** or **User controlled**, inbound calls can be sent to voicemail.|
|Inbound calls can be routed to call groups|On|This setting controls whether incoming calls can be forwarded to a call group.|
|Delegation for inbound and outbound calls|On|This setting enables inbound calls to be routed to delegates, allowing delegates to make outbound calls on behalf of the users for whom they have delegated permissions.|
|Prevent toll bypass and send calls through the PSTN|Off|Turn this setting **On** to send calls through the PSTN and incur charges rather than sending them through the network and bypassing the tolls.|
|Music on hold|Enabled|Controls whether music is played when a PSTN caller is placed on hold.|
|Busy on busy when in a call|Not enabled|Controls how incoming calls are handled when a user is already in a call or conference or has a call placed on hold.|
|Web PSTN calling|On|This setting enables users to call PSTN numbers using the Teams web client.|
|Real-time captions in Teams calls|On|This setting allows you to control whether real-time captions in Teams calls are available for your users.|
|Automatically answer incoming meeting invites|Off|This setting controls whether incoming meeting invites are automatically answered on Teams phones. Keep in mind that this setting applies only to incoming meeting invites. It doesn't apply to other types of calls.|
|Spam filtering|Turn on|This setting allows you to control the type of Spam filtering available on incoming calls.|
|SIP devices can be used for calls|Off|This setting enables users to use a SIP device to make and receive calls.|
|Open apps in browser for incoming PSTN calls|Off|This setting controls whether apps are automatically opened in the browser for incoming PSTN calls to your users. This setting can be used to pass the phone of an inbound caller to an app to find the associated customer record while the call is taking place.|

#### PowerShell-only calling policies

|Parameter|Default|Description|
|:-----|:-----|:-----|
|AllowCallRedirect|None|This setting provides the ability to configure call redirection capabilities on Teams phones. When set to **Enabled** users will have the ability to redirect received calls.|
|CallRecordingExpirationDays|60|This setting controls the expiration of recorded 1:1 calls, measured in days.|

#### Related topics to calling policies

- [Plan your Teams voice solution](cloud-voice-landing-page.md)
- [Calling and call-forwarding features in Teams](teams-calling-policy.md)
- [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)

### Call hold policies

**Navigation:** Teams admin center > Voice > Call hold policies

Call hold policies allow you to specify a custom audio file to play while calls are on hold. The **Music on hold** setting must also be **Enabled** in **Voice** > **Calling policies** or no music will be played.

:::image type="content" source="media/teams-call-hold-policy.png" alt-text="Screenshot of Teams call hold policies.":::

#### Related topics to call hold policies

- [How to setup Music on hold](music-on-hold.md).
- [Set-CsTeamsCallHoldPolicy](/powershell/module/skype/set-csteamscallholdpolicy)

### Call park policies

**Navigation:** Teams admin center > Voice > Call park policies

Call park lets people put a call on hold and transfer it to other people within your organization. Call park policies let you control which users are call park enabled and make other call park setting changes for them.

:::image type="content" source="media/teams-call-park-policy.png" alt-text="Screenshot of Teams call park policy.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Call park|Off|Turn on this setting to let your users place a call on hold on one device and pick it up from another device.|
|Call pickup start of range|10|The first parked call will be rendered a pickup code of the start of range (for instance 10). The next parked call will be rendered a pickup code incremented by 1; that is, 11, and so on, until the end of the range is rendered as a pickup code.|
|Call pickup end of range|99|The pickup code of the last parked call within in the range. After which, the rendered pickup codes start over from the start of the range once again.|
|Park timeout (seconds)|300|The number of seconds to wait before ringing back when the parked call hasn't been picked up. The allowed range is 120-1800 seconds.|

#### Related topics to call park policies

- [Configure Call park and retrieve](call-park-and-retrieve.md)
- [Set-CsTeamsCallParkPolicy](/powershell/module/skype/set-csteamscallparkpolicy)

### Caller ID policies

**Navigation:** Teams admin center > Voice > Caller ID policies

Caller ID policies are used to change or block the Caller ID (also called a Calling Line ID) for users. By default, the user's phone number is displayed when a call is made to a PSTN phone number such as a landline or mobile phone. You can use the Global (Org-wide default) policy and customize it or create a custom policy that provides an alternate number to display, or to block any number from being displayed.

:::image type="content" source="media/teams-policies-caller-id.png" alt-text="Screenshot of Teams caller ID policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Block incoming caller ID|Off|Turn on this setting to block the caller ID of incoming calls from being displayed.|
|Override the caller ID policy|Off|Turn on this setting to let users override the settings in the policy regarding displaying their number to callees or not. Users can then choose whether or not to display their caller ID.|
|Calling Party Name|(Blank)|The name of the person or entity that is displayed on the receiving end of a Teams call. Read more about [Calling Party Name](more-about-calling-line-ID-and-calling-party-name.md).|
|Replace the caller ID with|User's number|Set the caller ID to be displayed for users as **User's number**, **Service number**, or **Anonymous**|
|Replace the caller ID with this service number|(Choose a service number)|Choose a service number to replace the caller ID of users. This option is available if you selected **Service number** in **Replace the caller ID with**.|

#### Related topics to Caller ID policies

- [How can caller ID be used in your organization](how-can-caller-id-be-used-in-your-organization.md)
- [Manage caller ID policies in Microsoft Teams](caller-id-policies.md)
- [Set the Caller ID for a user](set-the-caller-id-for-a-user.md)
- [Set-CsCallingLineIdentity](/powershell/module/skype/Set-CsCallingLineIdentity)

### Emergency policies

**Navigation:** Teams admin center > Voice > Emergency policies

Emergency calling policies are used to control how users in your organization can use dynamic emergency calling features.

:::image type="content" source="media/teams-policies-emergency-calling.png" alt-text="Screenshot of Teams emergency calling policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|External location lookup mode|Off|Turn this setting on to allow your end users to configure their emergency address when they're working from a network location outside of the corporate network. Read more about [emergency addresses for remote locations](emergency-calling-dispatchable-location.md) and how to [add, change, or remove an emergency location](add-change-remove-emergency-location-organization.md) or [place for an emergency location](add-change-remove-emergency-place-organization.md) for your organization.|
|Notification mode|(Blank)|This sets the type of notification sent to a security desk or team when someone calls emergency services. You can set it to just send a notification to them, or if they can, join an emergency call muted or unmuted.|
|Emergency service disclaimer|(Blank)|Text that displays in a banner to remind your end users to confirm their emergency location.|
|Numbers to dial for emergency calls notifications|(Blank)|If you selected either of the **Conference in muted** options for **Notification mode**, you can enter a PSTN phone number of a user or group to call and join the emergency call.
|Users and groups for emergency calls notifications|(Blank)|Search for and select one or more users or groups, such as your organization's security desk, to notify when an emergency call is made. The notification can be sent to email addresses of users, distribution groups, and security groups. A maximum of 50 users can be notified.|
|Dynamic emergency calling|Off|If you turn this setting on, users assigned to the policy can use emergency call routing features when they move from one location to another. This setting is found under **Emergency policies** > **Call routing policies**. Read more about [how to plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).|

#### Related topics to emergency policies

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage emergency call routing policies for Direct Routing](manage-emergency-call-routing-policies.md)
- [Assign or change an emergency location for a user](assign-change-emergency-location-user.md)
- [Assign or change the place for an emergency location for a user](assign-change-emergency-place-user.md)
- [Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)
- [Set-CsTeamsEmergencyCallingPolicy](/powershell/module/skype/set-csteamsemergencycallingpolicy)
- [Set-CsTeamsEmergencyCallRoutingPolicy](/powershell/module/skype/set-csteamsemergencycallroutingpolicy)

### Voice routing policies

**Navigation:** Teams admin center > Voice > Voice routing policies

A voice routing policy for Direct Routing will be linked to a voice route using PSTN usage records. You can add existing PSTN usage records, change the order in which the usages will be processed, and assign the voice routing policy to users or resource accounts.

:::image type="content" source="media/teams-policies-voice-routing.png" alt-text="Screenshot of Teams voice routing policies.":::

<!---

#### PowerShell-only voice routing policies

|Parameter|Default|Description|
|:-----|:-----|:-----|

--->

#### Related topics to voice routing policies

- [Manage call routing policies for Direct Routing](manage-voice-routing-policies.md)
- [Configure call routing for Direct Routing](direct-routing-voice-routing.md)
- [Set-CsOnlineVoiceRoutingPolicy](/powershell/module/skype/set-csonlinevoiceroutingpolicy)
- [Set-CsOnlineVoiceRoute](/powershell/module/skype/set-csonlinevoiceroute)
- [Set-CsOnlinePstnUsage](/powershell/module/skype/set-csonlinepstnusage)

### Voicemail policies

**Navigation:** Teams admin center > Voice > Voicemail policies

Voicemail policies control the available features for the voicemail service in Teams.

:::image type="content" source="media/meetings-policies-voicemail.png" alt-text="Screenshot of Teams voicemail policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Users can edit call answering rules|On|This setting controls whether the user is allowed to configure voicemail call answering rules in Microsoft Teams.|
|Maximum voicemail recording length (seconds)|300|The maximum length of a voicemail. This length must be between 30 and 600 seconds.|
|Primary prompt language|(Blank)|The first language used to play system prompts to callers and the first option on the language selection menu.|
|Secondary prompt language|(Blank)|The second language used to play system prompts to callers and the second option on the language selection menu.|
|Voicemail transcription|On|Turn this setting on to enable transcription for voicemails.|
|Translation for transcriptions|On|Turn this setting on to enable translation for voicemail transcriptions.|
|Mask profanity in voicemail transcription|Off|If you turn this setting on, profanity will be masked in voicemail transcriptions.|
|Users can share data for service improvement|On|If you turn this setting on, users can share voicemail and transcription data for training and improving accuracy. If you turn this setting off, voicemail data won't be shared.|
|Before the user's greeting, play audio file|(none)|The audio file to play to the caller before the user's voicemail greeting is played.|
|After the user's greeting, play audio file|(none)|The audio file to play to the caller after the user's voicemail greeting has played and before the caller is allowed to leave a voicemail message.|
|Disconnect the call if preamble or postamble can't be played|Off|If you turn this setting on, the Pre- or Postamble will play before the caller can leave a message.|

#### Related topics to voicemail policies

- [Manage voicemail policies for your users](manage-voicemail-policies.md)
- [Change the default language for voicemail](change-the-default-language-for-greetings-and-emails.md)
- [Set-CsOnlineVoicemailPolicy](/powershell/module/skype/set-csonlinevoicemailpolicy)
- [Set up Cloud Voicemail](set-up-phone-system-voicemail.md)

## Enhanced encryption policies

### End-to-end encryption

**Navigation:** Teams admin center > Enhanced encryption policies

Enhanced encryption policies are used to control if users in your organization can use enhanced encryption settings in Teams.

:::image type="content" source="media/teams-e2ee-policies.png" alt-text="Screenshot of Teams end-to-end encryption policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|End-to-end call encryption|Not enabled|This setting determines whether end-to-end encrypted calling is available for users. Read more about [how to configure end-to-end encryption for one-to-one Microsoft Teams calls](teams-end-to-end-encryption.md).|
|End-to-end meeting encryption|Not enabled, but users can enable|This setting determines whether end-to-end encrypted meetings are available for users. This setting requires a Teams Premium license. Read more about [how to require end-to-end encryption for sensitive Teams meetings](end-to-end-encrypted-meetings.md).|

#### Related topics to end-to-end encryption policies

- [Security and Microsoft Teams](teams-security-guide.md)
- [Set-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Set-CsTeamsEnhancedEncryptionPolicy)
