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
|Default expiration time|120|The default expiration time for new meeting recordings. From 1 to 99999 days. Meetings automatically expire must also be turned On.|
|Store recordings outside your country or region|Off|Description|

### Meeting policies - Content sharing

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-policies-meetings-content-sharing.png" alt-text="Screenshot of Teams meetings content sharing policies.":::


| Setting | Default | Description |
|:-----|:-----|:-----|
|Screen sharing mode|Entire screen|Description|
|Participants can give or request control|On|Description|
|External participants can give or request control||Description|
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
|Make private calls|On|Description|
|Cloud recording for calling|Off|Description|
|Transcription|Off|Description|
|Call forwarding and simultaneous ringing to people in your organization|On|Controls whether incoming calls can be forwarded to other users or can ring another person in your organization at the same time.|
|Call forwarding and simultaneous ringing to external phone numbers|On|Controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time.|
|Voicemail is available for routing inbound calls|User controlled|When Enabled or User controlled, inbound calls can be sent to voicemail.|
|Inbound calls can be routed to call groups|On|Description|
|Delegation for inbound and outbound calls|On|Description|
|Prevent toll bypass and send calls through the PSTN|Off|Description|
|Music on hold|Enabled|Description|
|Busy on busy when in a call|Not enabled|Controls how incoming calls are handled when a user is already in a call or conference or has a call placed on hold.|
|Web PSTN calling|On|Description|
|Real-time captions in Teams calls|On|Description|
|Automatically answer incoming meeting invites|Off|Description|
|Spam filtering|Turn on|Description|
|SIP devices can be used for calls||Description|
|Open apps in browser for incoming PSTN calls|Off|Description|

### Call hold policies

**Navigation:** Teams admin center > Voice > Call hold policies

Call hold policies allow you to specify an audio file to play while calls are on hold.

### Call park policies

**Navigation:** Teams admin center > Voice > Call park policies

:::image type="content" source="media/teams-policies-call-park.png" alt-text="Screenshot of Teams call park policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Call park|Off|Description|
|Call pickup start of range|10|Description|
|Call pickup end of range|99|Description|
|Park timeout (seconds)|300|Description|

### Caller ID policies

**Navigation:** Teams admin center > Voice > Caller ID policies

:::image type="content" source="media/teams-policies-caller-id.png" alt-text="Screenshot of Teams caller ID policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Block incoming caller ID|Off|Description|
|Override the caller ID policy|Off|Description|
|Calling Party Name|(Blank)|Description|
|Replace the caller ID with|User's number|Description|
|Replace the caller ID with this service number|(Choose a service number)|Description|

