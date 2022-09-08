---
title: Teams settings and policies reference
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
description: This reference describes each of the settings and policies available in Microsoft Teams
---

# Teams settings and policies reference


## Teams

### Teams policies

**Navigation:** Teams admin center > Teams > Teams policies

:::image type="content" source="media/teams-policies-teams.png" alt-text="Screenshot of Teams team policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Create private channels|On|When On, team owners and members can create private channels which contain a subset of team members.|
|Create shared channels|On|When On, team owners can create shared channels for people within and outside the organization.|
|Invite external users to shared channels|On|When On, owners of a shared channel can invite external people in other Azure AD organizations to join the channel, if Azure AD cross-tenant access settings are configured. |
|Join external shared channels|On|When On, users and teams can be invited to external shared channels, if Azure AD cross-tenant access settings are configured.|

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

### Meeting policies - general

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-policies-meetings-general.png" alt-text="Screenshot of Teams meetings general policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Meet now in channels|On|When on, meeting organizers allow users to start instant meetings within channels that the users belong to.|
|Outlook add-in|On|When On, meeting organizers allow users to schedule private meetings from Outlook.|
|Channel meeting scheduling|On|When on, meeting organizers allow users to schedule channel meetings within channels that the users belong to.|
|Private meeting scheduling|On|When on, meeting organizers allow users to schedule private meetings.|
|Engagement report|Turn on| When On, meeting organizers can see who registered and attended the meetings and webinars they set up.|
|Meeting registration|On|When On, meeting organizers can require registration to join a meeting.|
|Who can register|Everyone|Determines who can register for meetings (if **Meeting registration** is **On**) - **Everyone** or **Everyone in the organization**.|

### Meeting policies - Audio and video

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-policies-meetings-audio-video.png" alt-text="Screenshot of Teams meetings audio and video policies.":::


| Setting | Default | Description |
|:-----|:-----|:-----|
|Mode for IP audio|Outgoing and incoming audio enabled|Description|
|Mode for IP video|Outgoing and incoming video enabled|Description|
|IP video|On|Description|
|Local broadcasting|Off|Use NDI technology to capture and deliver broadcast-quality audio and video over your network.|
|Media bit rate (Kbs)|50000|Determines the media bit rate for audio, video, and video-based app sharing in meetings.|
|Network configuration lookup|Off|When On, roaming policies in Network topology will be checked.|

### Meeting policies - Recording and transcription

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-policies-meetings-recording-transcription.png" alt-text="Screenshot of Teams meetings recording and transcription policies.":::


| Setting | Default | Description |
|:-----|:-----|:-----|
|Transcription|On|Description|
|Cloud recording|On|When On, users can record their Teams meetings and group calls to capture audio, video, and screen sharing activity. The meeting organizer and recording initiator need to recording permissions to record the meeting.|
|Meetings automatically expire|On|When On, meeting recordings will automatically expire in the number of days shown in the Default expiration time setting.|
|Default expiration time|120|The default expiration time for new meeting recordings. From 1 to 99999 days. **Meetings automatically expire** must also be turned **On**.|
|Store recordings outside your country or region|Off|Description|

### Meeting policies - Content sharing

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-policies-meetings-content-sharing.png" alt-text="Screenshot of Teams meetings content sharing policies.":::


| Setting | Default | Description |
|:-----|:-----|:-----|
|Screen sharing mode|Entire screen|Controls whether desktop and window sharing is allowed in the user's meeting.|
|Participants can give or request control|On|Controls whether the user can give control of the shared desktop or window to other meeting participants.|
|External participants can give or request control|Off|Controls whether external participants can be given control or request control of the sharer's screen, depending on what the sharer has set within their organization's meeting policies.|
|PowerPoint Live|On|Description|
|Whiteboard|On|Description|
|Shared notes|On|When On, attendees can create shared meeting notes through the meeting details.|
|Select video filters|All filters|Description|

### Meeting policies - Participants and guests

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-policies-meetings-participants-guests.png" alt-text="Screenshot of Teams meetings participants and guests policies.":::


| Setting | Default | Description |
|:-----|:-----|:-----|
|Let anonymous people join a meeting|On|Description|
|Let anonymous people start a meeting|Off|Description|
|Who can present in meetings|Everyone, but user can override|Description|
|Automatically admit people|People in my organization and guests|Controls who can join a meeting directly and who has to wait in the lobby until they're admitted by an authenticated user. This setting doesn't apply to dial-in users.|
|Dial-in users can bypass the lobby|Off|Controls whether people who dial in by phone join the meeting directly without waiting in the lobby.|
|Meet now in private meetings|On|Description|
|Live captions|Not enabled but the user can override|Description|
|Chat in meetings|Turn it on for everyone|Controls which meeting attendees can participate in the meeting chat. When turned off for anonymous participants, they can read the chat but not post messages.|
|Teams Q&A|On|When On, organizers can enable a question and answer experience for their meetings.|
|Meeting reactions|On|Description|

## Messaging

**Navigation:** Teams admin center > Messaging policies

:::image type="content" source="media/teams-policies-messaging.png" alt-text="Screenshot of Teams messaging policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Owners can delete sent messages|Off|When On, team owners can delete channel messages or posts that users have sent.|
|Delete sent messages|On|When On, users can delete messages they've sent in chat.|
|Edit sent messages|On|When On, users can edit messages they've sent in chat.|
|Read receipts|User controlled|When set as User controlled or Turned on for everyone, the sender of a chat message can be notified when their message was read by the recipient in 1:1 and group chats 20 people or fewer.|
|Chat|On|When On, users in your organization can use the Teams app to chat with other people.|
|Giphy in conversations|On|When On, users can include Giphys in chat conversations with other people.|
|Giphy content rating|Moderate|Description|
|Memes in conversations|On|When On, users can include Memes in chat conversations with other people.|
|Stickers in conversations|On|When On, users can include Stickers in chat conversations with other people.|
|URL previews|On|Controls automatic URL previewing in messages.|
|Translate messages|On|Description|
|Immersive reader for messages|On|When On, users can view messages in Microsoft Immersive Reader.|
|Send urgent messages using priority notifications|On|Description|
|Create voice messages|Allowed in chats and channels|Description|
|On mobile devices, display favorite channels above recent chats|Not enabled|Description|
|Remove users from group chats|On|Description|
|Suggested replies|On|When On, users get text predictions for chat messages.|
|Chat permissions role|Restricted permissions|Defines the supervised chat role of a user.|
|Users with full chat permissions can delete any message|Off|Description|


## Voice

### Calling policies

**Navigation:** Teams admin center > Voice > Calling policies

:::image type="content" source="media/teams-policies-calling.png" alt-text="Screenshot of Teams calling policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Make private calls|On|This setting controls all calling capabilities in Teams. Turn this off to turn off all calling functionality in Teams.|
|Cloud recording for calling|Off|This settings allow you to control whether call recording is available for your users.|
|Transcription|Off|This settings allow you to control whether transcription is available for your users.|
|Call forwarding and simultaneous ringing to people in your organization|On|Controls whether incoming calls can be forwarded to other users or can ring another person in your organization at the same time.|
|Call forwarding and simultaneous ringing to external phone numbers|On|Controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time.|
|Voicemail is available for routing inbound calls|User controlled|When Enabled or User controlled, inbound calls can be sent to voicemail.|
|Inbound calls can be routed to call groups|On|This setting controls whether incoming calls can be forwarded to a call group.|
|Delegation for inbound and outbound calls|On|This setting enables inbound calls to be routed to delegates, allowing delegates to make outbound calls on behalf of the users for whom they have delegated permissions.|
|Prevent toll bypass and send calls through the PSTN|Off|Setting this to **On** will send calls through the PSTN and incur charges rather than sending them through the network and bypassing the tolls.|
|Music on hold|Enabled|Controls whether music is played when a PSTN caller is placed on hold.|
|Busy on busy when in a call|Not enabled|Controls how incoming calls are handled when a user is already in a call or conference or has a call placed on hold.|
|Web PSTN calling|On|This setting enables users to call PSTN numbers using the Teams web client.|
|Real-time captions in Teams calls|On|This settings allow you to control whether real-time captions in Teams calls are available for your users.|
|Automatically answer incoming meeting invites|Off|This setting controls whether incoming meeting invites are automatically answered. Keep in mind that this setting applies only to incoming meeting invites. It doesn't apply to other types of calls.|
|Spam filtering|Turn on|This setting allows you to control the type of Spam filtering available on incoming calls.|
|SIP devices can be used for calls|Off|This setting enables users to use a SIP device to make and receive calls.|
|Open apps in browser for incoming PSTN calls (Preview)|Off|Description|

### Call hold policies

**Navigation:** Teams admin center > Voice > Call hold policies

Call hold policies allow you to specify an audio file to play while calls are on hold.

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
|Calling Party Name|(Blank)|Description|
|Replace the caller ID with|User's number|Set the caller ID to be displayed for users as **User's number**, **Service number**, or **Anonymous**|
|Replace the caller ID with this service number|(Choose a service number)|Choose a service number to replace the caller ID of users. This option is available if you selected **Service number** in **Replace the caller ID with**.|

### Emergency policies

**Navigation:** Teams admin center > Voice > Emergency policies

:::image type="content" source="media/teams-policies-emergency-calling.png" alt-text="Screenshot of Teams emergency calling policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|External location lookup mode|Off|Turn this onto allow your end users to configure their emergency address when they are working from a network location outside of the corporate network.|
|Notification mode|(Blank)|This sets the type of notification sent to a security desk or team when someone calls emergency services. You can set it to just send a notification to them, or if they can, join an emergency call muted or unmuted.|
|Emergency service disclaimer|(Blank)|Text that displays in a banner to remind your end users to confirm their emergency location.|
|Numbers to dial for emergency calls notifications|(Blank)|If you selected either of the **Conference in muted** options for **Notification mode**, you can enter a PSTN phone number of a user or group to call and join the emergency call.
|Users and groups for emergency calls notifications|(Blank)|Search for and select one or more users or groups, such as your organization's security desk, to notify when an emergency call is made. The notification can be sent to email addresses of users, distribution groups, and security groups. A maximum of 50 users can be notified.|

### Voice routing policies

**Navigation:** Teams admin center > Voice > Voice routing policies

:::image type="content" source="media/teams-policies-voice-routing.png" alt-text="Screenshot of Teams voice routing policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|||Description|
|||Description|
|||Description|
|||Description|
|||Description|
|||Description|

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
