---
title: Manage meeting policies for audio and video
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: casjacks
ms.date: 03/15/2021
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.audioandvideo
  - seo-marvel-apr2020
description: Learn to manage meeting policy settings in Teams for audio and video.
---

# Meeting policy settings for audio & video

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

<a name="bkaudioandvideo"> </a>
<a name="ndi"> </a>

This article describes the meeting policy settings specific to audio and video for meetings, webinars, and town halls. In town halls, only presenters, organizers, and co-organizers can use their cameras and microphones.

To access audio and video settings, follow these steps:

1. In the Teams admin center, expand **Meetings**.
1. Select **Meeting policies**.
1. Select the policy that you want to edit.
1. Scroll to the **Audio & video** section of the policy page.
1. When you've completed your changes, select **Save**.

## Mode for IP audio

This is a per-user policy. This setting controls whether audio can be turned on in meetings and group calls. Here are the values for this setting.

|Setting value|Behavior|
|---|---|
|**Outgoing and incoming audio enabled**|Outgoing and incoming audio is allowed in the meeting. This is the default setting.|
|**Not enabled**|Outgoing and incoming audio is turned off in the meeting.|

If set to **Not enabled** for a user, that user can still schedule and organize meetings but they can't use audio. To join a meeting, they must dial in or have the meeting call and join them by phone. Meeting participants who don't have any policies assigned (for example, anonymous participants) have this set to **Outgoing and incoming audio enabled** by default. On Teams mobile clients, if this setting isn't enabled, the user has to dial in to the meeting.

This setting doesn't apply to 1:1 calls. To restrict 1:1 calls, [configure a Teams calling policy](teams-calling-policy.md) and turn off the **Make private calls** setting in the Teams admin center. This setting also doesn't apply to conference room devices such as Surface Hub and Microsoft Teams Rooms devices.

This setting isn't available for Microsoft 365 Government Community Cloud (GCC), GCC High, or Department of Defense (DoD) environments.

To learn more, see [Manage audio/video for meeting participants](#manage-audiovideo-for-meeting-participants).

## Mode for IP video

This is a per-user policy. This setting controls whether outgoing and incoming video can be turned on in meetings and group calls. Here are the values for this setting.

|Setting value|Behavior|
|---|---|
|**Outgoing and incoming video enabled**|Outgoing and incoming video is allowed in the meeting. This is the default setting.|
|**Not enabled**|Outgoing and incoming video is turned off in the meeting. On Teams mobile clients, users can't share videos or photos in the meeting. <br><br>If **Mode for IP audio** is off, then **Mode for IP video** also stays off.|

If set to **Not enabled** for a  user, that user can't turn on video or view videos shared by other meeting participants. Meeting participants who don't have any policies assigned (for example, anonymous participants) have this set to **Outgoing and incoming video enabled** by default.

This setting doesn't apply to conference room devices such as Surface Hub and Microsoft Teams Rooms devices.

This setting isn't available for Microsoft 365 Government Community Cloud (GCC), GCC High, or Department of Defense (DoD) environments.

To learn more, see [Manage audio/video for meeting participants](#manage-audiovideo-for-meeting-participants).

## Video conferencing

> [!IMPORTANT]
> Currently, the **Video conferencing** setting doesn't turn off video for meetings and events. Your organizers should instead use the **Allow camera for attendees** setting in their **Meeting Options** to control video access in their meetings and events. To learn more, see the [Which video conferencing policy setting takes precedence](#which-video-policy-setting-takes-precedence) and [Manage audio/video for meeting participants](#manage-audiovideo-for-meeting-participants) sections in this article.

This is a combination of a per-organizer and per-user policy that controls which users' meetings have outgoing video. The Video conferencing setting controls whether video can be turned on in meetings hosted by a user and in 1:1 and group calls started by a user. On Teams mobile clients, this setting controls whether users can share photos and videos in a meeting.

When both the meeting organizer and participants have this policy set to **On**, participants can share video during the meeting. Meeting participants who don't have any assigned policies (for example, anonymous and trusted participants) inherit the meeting organizer's policy.

For a given user, if this setting is on:

- Meetings they organize will allow video
- They can use their video in meetings they attend

If this setting is off:

- Meetings they organize won't allow video
- They can't use their video in meetings they attend 

For a given user, the **Mode for IP video** setting affects video in both meetings they organize and meetings they attend. See the following table for details.

||Meetings the user organizes|Meetings the user attends|
|:-|:------------------------|:------------------------|
|**Mode for IP video** set to **On** for the user|All attendees can use video unless the policy assigned to them prohibits it.|User can use video unless the organizer's policy prohibits it.|
|**Mode for IP video** set to **Off** for the user|No attendees can use video.|User can't use video. Other attendees may be able to use video if the policy assigned to them and the policy assigned to the meeting organizer allow it.|

To learn more, see [Manage audio/video for meeting participants](#manage-audiovideo-for-meeting-participants).

### Which video policy setting takes precedence?

For a user, the most restrictive policy setting for video takes precedence. Here are some examples.

|Video conferencing|Mode for IP video|Meeting experience|
|---|---|---|
|Organizer: **On**<br><br>Participant: **On**|Participant: **Not enabled**|The **Mode for IP video** setting takes precedence. The participant who is assigned this policy can't turn on or view videos shared by others.|
|Organizer: **On**<br><br>Participant: **On**|Participant: **Outgoing and incoming video enabled**|The participant who is assigned this policy can turn on or view videos shared by others.|
|Organizer: **On**<br><br>Participant: **Off**|Participant: **Outgoing and incoming video enabled**|The **Video conferencing** setting takes precedence. The organizer can use the **Allow camera for attendees** setting in their **Meeting Options** to control video access in their meetings and events.|
|Organizer: **On**<br><br>Participant: **Off**|Participant: **Not enabled**|The **Mode for IP video** setting takes precedence. The participant can't see incoming or outgoing video.|
|Organizer: **Off**||The **Video conferencing** setting takes precedence. The organizer should instead use the **Allow camera for attendees** setting in their **Meeting Options** to control video access in their meetings and events.|

#### Manage audio/video for meeting participants

|If you want to...|Set the following policy settings|
|---|---|
|Enable audio and video for participants in meetings|Mode for IP audio: **Outgoing and incoming audio enabled** (default)<br> Mode for IP video: **Outgoing and incoming video enabled** (default)<br>Video conferencing: **N/A**|
|Disable audio and video for participants in meetings|Mode for IP audio: **Not enabled**<br> Mode for IP video: **Disabled**<br>Video conferencing: **N/A**|
|Disable video for participants in meetings (participants have audio only)|Mode for IP audio: **Enable outgoing and incoming audio**<br> Mode for IP video: **Not enabled**<br>Video conferencing: **N/A**

The most restrictive policy between the meeting organizer’s policy and the user’s policy applies. For example, if an organizer has a policy that restricts video and a user’s policy doesn't restrict video, meeting participants inherit the policy of the meeting organizer and don't have access to video in meetings. This means that they can join the meeting with audio only.

#### Teams mobile clients

For users on Teams mobile clients, the ability to share photos and videos during a meeting is also determined by the **Video conferencing** or **Video conferencing mode** setting. Depending on which policy setting takes precedence, the ability to share videos and photos won't be available. This doesn't affect screen sharing, which you configure using a separate [Screen sharing mode](meeting-policies-content-sharing.md#screen-sharing-mode) setting. Additionally, you can set a [Teams mobility policy](/powershell/module/teams/new-csteamsmobilitypolicy) to prevent mobile users from using video conferencing over a cellular connection, which means they must use a WiFi connection.

## Media bit rate (Kbps)

This is a per-user policy. This setting determines the media bit rate for audio, video, and video-based app-sharing transmissions in calls and meetings for the user. It's applied to both the uplink and downlink media traversal for users in the call or meeting. (For example, if you set a value of 2,000 Kbps, it is 2,000 Kbps for the uplink media and 2,000 Kbps for the downlink media.) This setting gives you granular control over managing bandwidth in your organization. Depending on the meetings scenarios required by users, we recommend having enough bandwidth in place for a good quality experience. The minimum value is 30 Kbps and the maximum value depends on the meeting scenario. To learn more about the minimum recommended bandwidth for good quality meetings, calls, and live events in Teams, see [Bandwidth requirements](prepare-network.md#bandwidth-requirements).

If there isn't enough bandwidth for a meeting, participants see a message that indicates poor network quality.

For meetings that need the highest-quality video experience, such as CEO board meetings and Teams live events, we recommend you set the bandwidth to 10 Mbps. Even when the maximum experience is set, Teams adapts to low-bandwidth conditions when certain network conditions are detected, depending on the scenario.

The Media bit rate policy doesn't affect the Teams web client.

## Participants can use video effects

<a name="bkvideofilters"> </a>

This is a per-user policy. This setting controls whether users can customize their video background in a meeting. The following table lists the options.

|Setting value in PowerShell|Setting value in Teams admin center|Behavior|
|---|---|---|
|**NoFilters**|**Off**|User can't customize their video background.|
|**BlurOnly**|**Only background blur**|User has the option to blur their video background.|
|**BlurandDefaultBackgrounds**|**Only background blur and default backgrounds**|User has the option to blur their video background or choose from the default set of images to use as their background.|
|**AllFilters**|**All video effects**|User has the option to blur their video background, choose from the default set of images, or upload custom images to use as their background.|

Use [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) or [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy) with the *VideoFiltersMode* parameter to configure the values in PowerShell.

> [!NOTE]
> Images uploaded by users aren't screened by Teams. When you use the **All video effects** setting, you should have internal organization policies to prevent users from uploading offensive or inappropriate images, or images your organization doesn't have rights to use for Teams meeting backgrounds.

For information about using custom background images for your organization, see [Custom meeting backgrounds for Teams Meetings](custom-meeting-backgrounds.md).

## Far end camera control (FECC) for pan tilt zoom (PTZ) cameras

Far end camera control is a policy that can be assigned to Teams Rooms resource accounts. It allows PTZ cameras that are connected to Teams Rooms to be controlled by meeting participants in the Teams client app during meetings.

To use far end camera control, meeting participants will need to get the **PTZ Camera Controls** app.  See [Allow and block apps](manage-apps.md#allow-or-block-apps) to learn how to make the app available in your organization's app store.

To specify who can use far end camera control in a meeting, create and assign a new policy to a Teams Rooms resource account using the [New-CsTeamsMeetingPolicy](/powershell/module/teams/new-csteamsmeetingpolicy) cmdlet, or use [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) to modify an existing one. Set the `TeamsCameraFarEndPTZMode` parameter to one of the following values:

|Setting value|Behavior|
|---|---|
|`Disabled`|This is the default setting. When set to `Disabled`, no one can use PTZ camera controls.|
|`AutoAcceptAll`|PTZ camera controls are automatically available to any meeting participant.|
|`AutoAcceptInTenant`|PTZ camera controls are automatically available only to participants in the same organization as the Teams Room.|

When `TeamsCameraFarEndPTZMode` is set to `AutoAcceptAll` or `AutoAcceptInTenant`, camera control can still be manually turned off from Teams Rooms at any point during a meeting. Camera control is also unavailable when the camera is turned off.

Any camera with mechanical PTZ and UVC controls is supported. For a list of cameras certified for Teams, including both PTZ and non-PTZ cameras, see [Teams Rooms certified systems and peripherals](/microsoftteams/rooms/certified-hardware?tabs=Peripherals). This feature isn't yet supported on cameras with digital PTZ controls.  

> [!NOTE]
> Update your camera firmware before testing PTZ controls. See the original equipment manufacturer (OEM) documentation to update firmware.

## Related topics

- [Teams policies reference](settings-policies-reference.md#audio--video)
- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
