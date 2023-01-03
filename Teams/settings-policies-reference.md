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

## Teams

### Teams policies

**Navigation:** Teams admin center > Teams > Teams policies

:::image type="content" source="media/teams-policies-teams.png" alt-text="Screenshot of Teams team policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Create private channels|On|When **On**, team owners and members can create private channels which contain a subset of team members.|
|Create shared channels|On|When **On**, team owners can create shared channels for people within and outside the organization.|
|Invite external users to shared channels|On|When **On**, owners of a shared channel can invite external people in other Azure AD organizations to join the channel, if Azure AD cross-tenant access settings are configured.|
|Join external shared channels|On|When **On**, users and teams can be invited to external shared channels, if Azure AD cross-tenant access settings are configured.|

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

## Meetings

### Meeting policies

#### Meeting scheduling

**Navigation:** Teams admin center > Meetings > Meeting policies

| Setting | Default | Description |
|:-----|:-----|:-----|
|Private meeting scheduling|On|When **On**, meeting organizers allow users to schedule private meetings.|
|Meet now in private meetings|On|Controls whether a user can start an instant private meeting.|
|Channel meeting scheduling|On|When **On**, meeting organizers allow users to schedule channel meetings within channels that the users belong to.|
|Meet now in channels|On|When **On**, meeting organizers allow users to start instant meetings within channels that the users belong to.|
|Outlook add-in|On|When **On**, meeting organizers allow users to schedule private meetings from Outlook.|
|Meeting registration|On|When **On**, meeting organizers can require registration to join a meeting.|
|Who can register|Everyone|Determines who can register for meetings (if **Meeting registration** is **On**) - **Everyone** or **Everyone in the organization**.|
|Engagement report|Turn on|When **On**, meeting organizers can see who registered and attended the meetings they set up.|

#### Meeting join & lobby

**Navigation:** Teams admin center > Meetings > Meeting policies

| Setting | Default | Description |
|:-----|:-----|:-----|
|Anonymous users can join a meeting|On|This per-organizer setting allows anyone to join meetings as an anonymous user by selecting the link in the meeting invitation.|
|Anonymous and dial-in users can start a meeting|Off|This setting is a per-organizer policy that allows for leaderless dial-in conferencing meetings. This setting controls whether dial-in users can join the meeting without an authenticated user from the organization in attendance.|
|Who can bypass the lobby|Everyone in my organization and guests|Controls who can join a meeting directly and who has to wait in the lobby until they're admitted by an authenticated user. This setting doesn't apply to dial-in users.|
|People dialing in can bypass the lobby|Off|Controls whether people who dial in by phone join the meeting directly without waiting in the lobby.|

#### Meeting engagement

**Navigation:** Teams admin center > Meetings > Meeting policies

| Setting | Default | Description |
|:-----|:-----|:-----|
|Meeting chat|Turn it on for everyone|Controls which meeting attendees can participate in the meeting chat. When turned off for anonymous participants, they can read the chat but not post messages.|
|Q&A|On|When **On**, organizers can enable a question and answer experience for their meetings.|
|Reactions|On|This setting controls whether users can use live reactions such as Like, Love, Applause, Laugh, and Surprise in Teams meetings.|

#### Content sharing

**Navigation:** Teams admin center > Meetings > Meeting policies

| Setting | Default | Description |
|:-----|:-----|:-----|
|Who can present|Everyone, but user can override|Controls what the default value is for **Who can  present?** in **Meeting options** for the Teams client.|
|Screen sharing mode|Entire screen|Controls whether desktop and window sharing is allowed in the user's meeting.|
|Participants can give or request control|On|Controls whether the user can give control of the shared desktop or window to other meeting participants. This setting isn't supported if either user is in Teams in a browser.|
|External participants can give or request control|Off|Controls whether external users can be given or request control of the shared desktop or window. This must be turned on in both organizations for an external user to take control in Teams meetings hosted by people in your organization.|
|PowerPoint Live|On|Controls whether a user can share PowerPoint slide decks in a meeting. External participants, including anonymous, guest, and external access users, inherit the policy of the meeting organizer.|
|Whiteboard|On|Controls whether a user can share the Whiteboard in a meeting. External participants, including anonymous, guest, and external access users, inherit the policy of the meeting organizer.|
|Shared notes|On|When **On**, attendees can create shared meeting notes through the meeting details.|

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

#### PowerShell-only meeting policies

| Parameter | Default | Description |
|:-----|:-----|:-----|
|-AllowBreakoutRooms|True|This setting enables the Breakout Rooms functionality.|
|-AllowCartCaptionsScheduling|DisabledUserOverride|This setting determines whether a user can add a URL for captions from a Communicatons Access Real-Time Translation (CART) captioner to provide real-time captions in meetings.|
|-BlockedAnonymousJoinClientTypes|(empty list)|This setting allows users to join a Teams meeting anonymously using a Teams client or using a custom application built using Azure Communication Services. When anonymous meeting join is enabled, both types of clients may be used by default. This optional parameter can be used to block one of the client types that can be used. If both clients are specified, this will be equivalent to disabling anonymous join completely.|
|-ChannelRecordingDownload|Allow|This setting controls how channel meeting recordings are saved, permissioned, and who can download them.|
|-LiveInterpretationEnabledType|DisabledUserOverride|This setting allows meeting organizers to configure a meeting for language interpretation and select attendees to become interpreters that other attendees can select and listen to the real-time translation they provide.|
|-MeetingInviteLanguages|None|This setting controls how the join information in meeting invitations is displayed by enforcing a common language or enabling up to two languages to be displayed. All Teams supported languages can be specified using language codes.|
|-|||
|-|||
|-|||
|-|||
|-|||

##### Related topics to meeting policies

- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
- [Manage meeting policies in Microsoft Teams](meeting-policies-overview.md)
- [Meeting policy settings - Participants & guests](meeting-policies-participants-and-guests.md)
- [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md)
- [Meeting policy settings - Content sharing](meeting-policies-content-sharing.md)
- [Meeting policy settings for recording & transcription](meetings-policies-recording-and-transcription.md)
- [Meeting policy settings for audio & video](meeting-policies-audio-and-video.md)

### Live events policies

**Navigation:** Teams admin center > Meetings > Live events policies

| Setting | Default | Description |
|:-----|:-----|:-----|
|Live events scheduling|On|When **On**, users in your organization can create and schedule live events in Teams.|
|Transcription for attendees|Off|Turning this on enables live event attendees to see live captions and subtitles during the event. This setting can only be applied to events produced in Teams.|
|Who can join scheduled live events|Everyone|This setting restricts who can attend live events. Teams permission types are updated based on the selection.|
|Record an event|Organizer can record|This controls whether the event is recorded.|

## Messaging policies

**Navigation:** Teams admin center > Messaging policies

:::image type="content" source="media/teams-policies-messaging.png" alt-text="Screenshot of Teams messaging policies.":::

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
|Translate messages|On|Turn this setting on to let users automatically translate Teams messages into the language specified by their personal language settings for Microsoft 365 or Office 365.|
|Immersive reader for messages|On|When **On**, users can view messages in Microsoft Immersive Reader.|
|Send urgent messages using priority notifications|On|If you turn this on, users can send messages using priority notifications. Priority notifications notify users every 2 minutes for 20 minutes or until messages that are marked as urgent are picked up and read by the recipient.|
|Create voice messages|Allowed in chats and channels|This setting controls whether users can leave audio messages in chats and channels.|
|On mobile devices, display favorite channels above recent chats|Not enabled|When **Enabled**, this setting moves favorite channels to the top of the mobile device screen so that a user doesn't need to scroll to find them.|
|Remove users from group chats|On|Turn this setting on to let a user remove other users from a group chat. This feature lets you continue a chat with a smaller group of people without losing the chat history.|
|Suggested replies|On|When **On**, users get text predictions for chat messages.|
|Chat permissions role|Restricted permissions|Defines the supervised chat role of a user.|
|Users with full chat permissions can delete any message|Off|Use this setting to let users with full chat permissions delete any group or meeting chat message.|

## Voice

### Calling policies

**Navigation:** Teams admin center > Voice > Calling policies

:::image type="content" source="media/teams-policies-calling.png" alt-text="Screenshot of Teams calling policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Make private calls|On|This setting controls all calling capabilities in Teams. Turn this off to turn off all calling functionality in Teams.|
|Cloud recording for calling|Off|This settings allow you to control whether call recording is available for your users.|
|Transcription|Off|This settings allow you to control whether post-call transcriptions are available for your users.|
|Call forwarding and simultaneous ringing to people in your organization|On|Controls whether incoming calls can be forwarded to other users or can ring another person in your organization at the same time.|
|Call forwarding and simultaneous ringing to external phone numbers|On|Controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time.|
|Voicemail is available for routing inbound calls|User controlled|When set to **Enabled** or **User controlled**, inbound calls can be sent to voicemail.|
|Inbound calls can be routed to call groups|On|This setting controls whether incoming calls can be forwarded to a call group.|
|Delegation for inbound and outbound calls|On|This setting enables inbound calls to be routed to delegates, allowing delegates to make outbound calls on behalf of the users for whom they have delegated permissions.|
|Prevent toll bypass and send calls through the PSTN|Off|Setting this to **On** will send calls through the PSTN and incur charges rather than sending them through the network and bypassing the tolls.|
|Music on hold|Enabled|Controls whether music is played when a PSTN caller is placed on hold.|
|Busy on busy when in a call|Not enabled|Controls how incoming calls are handled when a user is already in a call or conference or has a call placed on hold.|
|Web PSTN calling|On|This setting enables users to call PSTN numbers using the Teams web client.|
|Real-time captions in Teams calls|On|This settings allow you to control whether real-time captions in Teams calls are available for your users.|
|Automatically answer incoming meeting invites|Off|This setting controls whether incoming meeting invites are automatically answered on Teams phones. Keep in mind that this setting applies only to incoming meeting invites. It doesn't apply to other types of calls.|
|Spam filtering|Turn on|This setting allows you to control the type of Spam filtering available on incoming calls.|
|SIP devices can be used for calls|Off|This setting enables users to use a SIP device to make and receive calls.|
|Open apps in browser for incoming PSTN calls|Off|This setting controls whether apps are automatically opened in the browser for incoming PSTN calls to your users. This can be used to pass  the phone of an inbound caller to an app to find the associated customer record while the call is taking place.|

#### PowerShell-only calling policies

|Parameter|Default|Description|
|:-----|:-----|:-----|
|-AllowCallRedirect|None|This setting provides the ability to configure call redirection capabilities on Teams phones. When set to **Enabled** users will have the ability to redirect received calls.|
|-CallRecordingExpirationDays|60|This setting controls the expiration of recorded 1:1 calls, measured in days.|

#### Related topics to calling policies

- 
-  

### Call hold policies

**Navigation:** Teams admin center > Voice > Call hold policies

Call hold policies allow you to specify a custom audio file to play while calls are on hold. The **Music on hold** setting must also be **Enabled** in **Voice** > **Calling policies** or no music will be played.

### Call park policies

**Navigation:** Teams admin center > Voice > Call park policies

:::image type="content" source="media/teams-policies-call-park.png" alt-text="Screenshot of Teams call park policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Call park|Off|Turn on this setting to let your users place a call on hold on one device and pick it up from another device.|
|Call pickup start of range|10|The first parked call will be rendered a pickup code of the start of range (for instance 10). The next parked call will be rendered a pickup code incremented by 1; that is, 11, and so on, until the end of the range is rendered as a pickup code.|
|Call pickup end of range|99|The pickup code of the last parked call within in the range. After which, the rendered pickup codes start over from the start of the range once again.|
|Park timeout (seconds)|300|The number of seconds to wait before ringing back when the parked call hasn't been picked up. The allowed range is 120-1800 seconds.|

### Caller ID policies

**Navigation:** Teams admin center > Voice > Caller ID policies

:::image type="content" source="media/teams-policies-caller-id.png" alt-text="Screenshot of Teams caller ID policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Block incoming caller ID|Off|Turn on this setting to block the caller ID of incoming calls from being displayed.|
|Override the caller ID policy|Off|Turn on this setting to let users override the settings in the policy regarding displaying their number to callees or not. This means that users can choose whether to display their caller ID.|
|Calling Party Name|(Blank)|The name of the person or entity that is displayed on the receiving end of a Teams call.|
|Replace the caller ID with|User's number|Set the caller ID to be displayed for users as **User's number**, **Service number**, or **Anonymous**|
|Replace the caller ID with this service number|(Choose a service number)|Choose a service number to replace the caller ID of users. This option is available if you selected **Service number** in **Replace the caller ID with**.|

### Emergency policies

**Navigation:** Teams admin center > Voice > Emergency policies

:::image type="content" source="media/teams-policies-emergency-calling.png" alt-text="Screenshot of Teams emergency calling policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|External location lookup mode|Off|Turn this on to allow your end users to configure their emergency address when they are working from a network location outside of the corporate network.|
|Notification mode|(Blank)|This sets the type of notification sent to a security desk or team when someone calls emergency services. You can set it to just send a notification to them, or if they can, join an emergency call muted or unmuted.|
|Emergency service disclaimer|(Blank)|Text that displays in a banner to remind your end users to confirm their emergency location.|
|Numbers to dial for emergency calls notifications|(Blank)|If you selected either of the **Conference in muted** options for **Notification mode**, you can enter a PSTN phone number of a user or group to call and join the emergency call.
|Users and groups for emergency calls notifications|(Blank)|Search for and select one or more users or groups, such as your organization's security desk, to notify when an emergency call is made. The notification can be sent to email addresses of users, distribution groups, and security groups. A maximum of 50 users can be notified.|
|Dynamic emergency calling|Off|If you turn this on, users assigned to the policy can use emergency call routing features when they move from one location to another.|

### Voice routing policies

**Navigation:** Teams admin center > Voice > Voice routing policies

:::image type="content" source="media/teams-policies-voice-routing.png" alt-text="Screenshot of Teams voice routing policies.":::

If you've deployed Direct Routing in your organization, you use voice routing policies (also known as call routing policies) to allow Teams users to receive and make phone calls to the Public Switched Telephone Network (PSTN) using your on-premises telephony infrastructure. A voice routing policy is a container for PSTN usage records.

### Voicemail policies

**Navigation:** Teams admin center > Voice > Voicemail policies

:::image type="content" source="media/meetings-policies-voicemail.png" alt-text="Screenshot of Teams voicemail policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Users can edit call answering rules|On|This setting controls whether the user is allowed to configure voicemail call answering rules in Microsoft Teams.|
|Maximum voicemail recording length (seconds)|300|The maximum length of a voicemail. This must be between 30 and 600 seconds.|
|Primary prompt language|(Blank)|The first language used to play system prompts to callers and the first option on the language selection menu.|
|Secondary prompt language|(Blank)|The second language used to play system prompts to callers and the second option on the language selection menu.|
|Voicemail transcription|On|Turn this on to enable transcription for voicemails.|
|Translation for transcriptions|On|Turn this on to enable translation for voicemail transcriptions.|
|Mask profanity in voicemail transcription|Off|If you turn this on, profanity will be masked in voicemail transcriptions.|
|Users can share data for service improvement|On|If you turn this on, users can share voicemail and transcription data for training and improving accuracy. If you turn this off, voicemail data won't be shared.|
