---
title: Teams settings and policies reference
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: 
ms.date: 04/24/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - Tier1
f1.keywords: 
  - NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: This reference describes each of the settings and policies available in Microsoft Teams.
---

# Teams settings and policies reference

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

This reference describes each of the policies available in Microsoft Teams. Each section is broken down by the corresponding policy area in the Teams admin center, along with any PowerShell-only policies that may also exist.

## Teams

### Teams settings

Teams settings are used to control notification, tagging, email integration, and file storage providers.

#### Notifications and feeds

**Navigation:** Teams admin center > Teams > Teams settings

:::image type="content" source="media/notifications-tac.png" alt-text="Screenshot of Teams notifications and feeds settings in the Teams admin center." lightbox="media/notifications-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Suggested feeds can appear in a user's activity feed|On|When **On**, suggested feeds can appear in a user's activity feed.|

#### Tagging

**Navigation:** Teams admin center > Teams > Teams settings

:::image type="content" source="media/tagging-tac.png" alt-text="Screenshot of Teams tagging settings in the Teams admin center." lightbox="media/tagging-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Who can manage tags|Microsoft Default|Specifies who can manage tags in new teams.|
|Team owners can change who can manage tags|On|When **On**, team owners can change who can manage tags. When **Off**, team owners can't change the value set in **Who can manage tags** above.|
|Suggested tags|(none)|Used to specify suggested tag names to team owners or members who are creating tags.|
|Custom tags|On|When **On**, team owners and members can create custom tags. When **Off**, only suggested tags can be used.|
|Shifts app can apply tags|On|When **On**, tags are automatically assigned to people who are on shift in real time.|

##### Related topics for tagging

[Manage tags in Microsoft Teams](manage-tags.md)

#### Email integration

**Navigation:** Teams admin center > Teams > Teams settings

:::image type="content" source="media/email-integration-tac.png" alt-text="Screenshot of Teams email integration settings in the Teams admin center." lightbox="media/email-integration-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Users can send emails to a channel email address|On|When **On**, users can send emails to a channel email address and the email will appear in the channel.|
|Accept channel email from these SMTP domains|(none)|Used to limit the domain from which channels can receive emails.|

#### Files

**Navigation:** Teams admin center > Teams > Teams settings

:::image type="content" source="media/files-tac.png" alt-text="Screenshot of Teams cloud storage service files settings in the Teams admin center." lightbox="media/files-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Citrix files|On|When **On**, Citrix can be added as a cloud storage service in a team.|
|DropBox|On|When **On**, DropBox can be added as a cloud storage service in a team.|
|Box|On|When **On**, Box can be added as a cloud storage service in a team.|
|Google Drive|On|When **On**, Google Drive can be added as a cloud storage service in a team.|
|Egnyte|On|When **On**, Egnyte can be added as a cloud storage service in a team.|

##### Related topics for files

[Add a cloud storage service to Teams](https://support.microsoft.com/office/4e1e1a12-21ae-4616-b539-33d11e4cd68e)

#### Organization

**Navigation:** Teams admin center > Teams > Teams settings

:::image type="content" source="media/organization-tac.png" alt-text="Screenshot of Teams organization settings in the Teams admin center." lightbox="media/organization-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Show organization tab for users|On|When **On**, users see the **Organization** tab in their personal chat in Teams. The **Organization** tab shows the organizational hierarchy as defined in Microsoft Entra ID.|

##### Related topics for Organization

[Use the Organization tab in Teams](https://support.microsoft.com/office/ff02568b-290a-46d6-ae7a-cda22f723894)

#### Devices

**Navigation:** Teams admin center > Teams > Teams settings

:::image type="content" source="media/devices-tac.png" alt-text="Screenshot of Teams devices settings in the Teams admin center." lightbox="media/devices-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Require a secondary form of authentication to access meeting content|No access|Skype for Business users require a secondary form of authentication to access meeting content.|
|Set content PIN|Required for outside scheduled meeting|Specifies if Skype for Business users require a content PIN.|
|Surface hub accounts can send emails|On|When **On**, Surface Hub accounts can send emails.|

#### Search by name

**Navigation:** Teams admin center > Teams > Teams settings

:::image type="content" source="media/search-by-name-tac.png" alt-text="Screenshot of Teams search by name settings in the Teams admin center." lightbox="media/search-by-name-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Scope directory search using an Exchange address book policy|Off|When **On**, hides the **Search teams** box and public teams listing in **Join or create a team** in Teams|

##### Related topics for search by name

[Limit who users can see when searching the directory in Teams](teams-scoped-directory-search.md)

#### Safety and communications

:::image type="content" source="media/safety-and-communications-tac.png" alt-text="Screenshot of Teams safety and communications settings in the Teams admin center." lightbox="media/safety-and-communications-tac-expand.png":::

**Navigation:** Teams admin center > Teams > Teams settings

| Setting | Default | Description |
|:-----|:-----|:-----|
|Role-based chat permissions|Off|When **On**, supervised chat is available for all users.|

##### Related topics for safety and communications

[Supervised chats in Microsoft Teams](supervise-chats-edu.md)

#### Shared channels

:::image type="content" source="media/shared-channels-tac.png" alt-text="Screenshot of Teams shared channel settings in the Teams admin center." lightbox="media/shared-channels-tac-expand.png":::

**Navigation:** Teams admin center > Teams > Teams settings

| Setting | Default | Description |
|:-----|:-----|:-----|
|Provide a link to my support request page|Off|When **On**, you can provide users a link to your designated support request page for external collaboration assistance.|

##### Related topics for shared channels

[Shared channels in Microsoft Teams](shared-channels.md)

### Teams policies

**Navigation:** Teams admin center > Teams > Teams policies

Teams policies are used to control what settings or features are available to users when they're using teams and channels.

:::image type="content" source="media/teams-policies-tac.png" alt-text="Screenshot of Teams team policies in the Teams admin center." lightbox="media/teams-policies-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Create private channels|On|When **On**, team owners and members can create private channels that contain a subset of team members.|
|Create shared channels|On|When **On**, team owners can create shared channels for people within and outside the organization.|
|Invite external users to shared channels|On|When **On**, owners of a shared channel can invite external people in other Microsoft Entra organizations to join the channel, if Microsoft Entra cross-tenant access settings are configured.|
|Join external shared channels|On|When **On**, users and teams can be invited to external shared channels, if Microsoft Entra cross-tenant access settings are configured.|

**PowerShell-only Teams policies**

|Parameter|Default|Description|
|:-----|:-----|:-----|
|AllowOrgWideTeamCreation|None|Determines whether a user is allowed to create an org-wide team. Set this value to **True** to allow or **False** to prohibit. Read more on [how organization-wide teams in Microsoft Teams help everyone collaborate](create-an-org-wide-team.md).|
|EnablePrivateTeamDiscovery|None|Determines whether a user is allowed to discover private teams in suggestions and search results. Set this value to **True** to allow or **False** to prohibit.|

#### Related topics for Teams policies

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

#### Related topics for template policies

- [Manage team templates in the admin center](templates-policies.md)
- [Get started with team templates in the Teams admin center](get-started-with-teams-templates-in-the-admin-console.md)
- [Get-CsTeamTemplate](/powershell/module/teams/get-csteamtemplate)
- [Get-CsTeamTemplateList](/powershell/module/teams/get-csteamtemplatelist)

### Teams update policies

**Navigation:** Teams admin center > Teams > Update policies

Update policies are used to manage Teams and Office preview users who can see pre-release or preview features in the Teams app. Public preview isn't enabled by default.

:::image type="content" source="media/update-policy-tac.png" alt-text="Screenshot of Teams update policy in the Teams admin center." lightbox="media/update-policy-tac-expand.png":::

|Setting | Default | Description |
|:-----|:-----|:-----|
Show Teams preview features|On for users in current channel (Preview)|Turns on Teams Public preview features for any user enrolled in Office Current Channel (Preview).|
|Use new Teams client|Microsoft controlled| Allows Microsoft to: <br>- Control whether the "Try the new Teams" toggle switch is shown. <br>- Manage the installation of the new Teams client and determine default client behavior based on the rollout schedule.|

You could set the preview policy using the PowerShell `Set-CsTeamsUpdateManagementPolicy` cmdlet with the `-AllowPublicPreview` parameter.

To set the new Teams client policy using PowerShell, use the `Set-CsTeamsUpdateManagementPolicy` cmdlet with the `-UseNewTeamsClient` parameter.

#### Related topics for Teams update policies

- [Microsoft Teams Public Preview](public-preview-doc-updates.md)
- [Public Preview Features - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-teams-public-preview/bd-p/MicrosoftTeamsPublicPreview)
- [Upgrade to the new Teams using policies](new-teams-deploy-using-policies.md)

### Teams upgrade settings

Teams upgrade settings let you set up your upgrade experience from Skype for Business to Teams for your users.

#### Coexistence mode

**Navigation:** Teams admin center > Teams > Teams upgrade settings

:::image type="content" source="media/coexistence-mode-tac.png" alt-text="Screenshot of Teams upgrade coexistence mode settings in the Teams admin center." lightbox="media/coexistence-mode-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Coexistence mode|Teams only|Determines both routing of incoming calls and chats and the app that is used by the user to initiate chats and calls or to schedule meetings.|
|Notify Skype for Business users that an upgrade to Teams is available.|Off|When **On**, your users see a yellow banner in their Skype for Business app telling them that they'll soon be upgraded to Teams.|

##### Related topics for coexistence mode

[Coexistence modes - Reference](migration-interop-guidance-for-teams-with-skype.md)

#### App preferences

**Navigation:** Teams admin center > Teams > Teams upgrade settings

:::image type="content" source="media/app-preferences-tac.png" alt-text="Screenshot of Teams upgrade app preferences settings in the Teams admin center." lightbox="media/app-preferences-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Preferred app for users to join Skype for Business meetings|Skype for Business|Sets the app is used for joining Skype for Business meetings. This setting isn't dependent on the **Coexistence mode** setting.|
|Download the Teams app in the background for Skype for Business users|On|When **On**, downloads the Teams app in the background for users running the Skype for Business app on Windows PCs. This happens if the Coexistence mode for the user is **Teams Only**, or if a pending upgrade notification is enabled in the Skype for Business app.|

##### Related topics for app preferences

[Configure the Skype Meetings App to work with Teams](configure-skype-meetings-app-to-work-with-teams.md)

## Teams apps

### Permission policies

**Navigation:** Teams admin center > Teams apps > Permission policies

App permission policies control which apps you want to make available to Teams users in your organization.

:::image type="content" source="media/permission-policies-tac.png" alt-text="Screenshot of Teams app permission policies in the Teams admin center." lightbox="media/permission-policies-tac-expand.png":::

The types of apps to permission are divided into three categories - Microsoft apps, Third-party apps, and Custom apps. Each app category includes the following options for permissions:

- **Allow all apps** - Users can install and use any app published by your organization in the Teams app store.
- **Allow specific apps and block all others** - Allow specific apps you want to allow from the Teams app store and all other apps would be blocked.
- **Block specific apps and allow all others** - Add which apps you want to block from the Teams app store and all the other apps would be allowed.
- **Block all apps** - Users can't install apps that are published by your organization in the Teams app store.

#### Related topics for permission policies

- [Use app permission policies to control user access to apps](teams-app-permission-policies.md)
- [Overview of app management and governance in Teams admin center](manage-apps.md)
- [Information accessed and actions performed by apps and related admin considerations](app-permissions.md)
- [View app permissions and grant admin consent in Teams admin center](app-permissions-admin-center.md)
- [Resource-specific consent in Microsoft Teams](resource-specific-consent.md)
- [Set-CsTeamsAppPermissionPolicy](/powershell/module/skype/set-csteamsapppermissionpolicy)

### Setup policies

**Navigation:** Teams admin center > Teams apps > Setup policies

App setup policies control how apps are made available to a user with the Teams app.

:::image type="content" source="media/app-setup-tac.png" alt-text="Screenshot of Teams app setup policies in the Teams admin center." lightbox="media/app-setup-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Upload custom apps|Off|This setting determines if a user can upload a custom app package in the Teams app. Turning it on lets you create or develop a custom app to be used personally or across your organization without having to submit it to the Teams app store. Uploading a custom app also lets you test an app before you distribute it more widely by only assigning it to a single user or group of users. Read more about how to [Manage custom and sideloaded apps in Teams admin center](teams-custom-app-policies-and-settings.md).|
|User pinning|On|If you turn on this setting, the user’s existing app pins will be added to the list of pinned apps set in this policy. Users can rearrange, add, and remove pins as they choose. If you turn off this setting, the user’s existing app pins will be removed and replaced with the apps defined in this policy.|
|Installed apps|(none)|Choose which apps and messaging extensions you want installed in your users' personal Teams environment and in meetings they create. Users can install other available apps from the Teams app store.|
|Pinned apps|Activity, Chat, Teams, Calendar, Calling, Files|Choose the order apps are pinned in messaging extensions and the Teams app bar.|

#### Related topics for setup policies

- [Use app setup policies to pin and auto-install apps in Teams](teams-app-setup-policies.md)
- [Use of Teams apps for external attendees or guest from outside an organization](non-standard-users.md)
- [Understand Microsoft Teams apps and their capabilities](apps-in-teams.md)

### Customize app store

**Navigation:** Teams admin center > Teams apps > Customize store

Customize store settings allow you to customize the Teams app store with your organization's logo, logomark, and custom background or color.

:::image type="content" source="media/customize-app-store-tac.png" alt-text="Screenshot of Teams customize app store policies in the Teams admin center." lightbox="media/customize-app-store-tac-expand.png":::

The defaults for all the customization options use Teams app default backgrounds and colors. You can upload your org's logo, logomark, background image, and select a custom text color.

#### Related topics for customize store

- [Customize your organization's app store in Microsoft Teams](customize-your-app-store.md)

## Meetings

### Conference bridges

Conference bridges let people dial into meetings using a phone. You can use the default settings for a conference bridge or change the phone numbers (toll and toll-free) and other settings such as the PIN or the languages that are used.

:::image type="content" source="media/bridge-settings-tac.png" alt-text="Screenshot of Teams conference bridges policies in the Teams admin center." lightbox="media/bridge-settings-tac-expand.png":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Meeting entry and exit notifications|On|When **On**, users who have already joined the meeting are notified when someone enters or leaves the meeting.|
|Entry/exit announcement type|Tones|When **On**, a tone is played when someone enters or leaves the meeting.|
|PIN length|5|When **On**, the PIN that meeting organizers use to start meetings if they can't join using the Microsoft Teams app is five characters long.|
|Automatically send emails to users if their dial-in settings change|On|When **On**, your users get an email when: <br>-You assign an Audio Conferencing license to them or when you're changing the audio conferencing provider to Microsoft. <br>-Their conference ID or default conference phone number changes. <br>-Their  audio conferencing PIN is reset. <br>-Their license is removed or when the audio conferencing provider changes from Microsoft to another provider or none.|
|Mask phone numbers|From participants outside your organization|When **On**, only meeting attendees inside the meeting organizer's org can see the full phone number.|

#### Related topics for conference bridges

- [Turn on or off entry and exit announcements for meetings in Microsoft Teams](turn-on-or-off-entry-and-exit-announcements-for-meetings-in-teams.md)
- [Set the PIN length for Audio Conferencing meetings in Microsoft Teams](set-the-pin-length-for-audio-conferencing-meetings-in-teams.md)
- [Audio Conferencing in Microsoft Teams](audio-conferencing-in-office-365.md)
- [Emails sent to users when their settings change in Microsoft Teams](emails-sent-to-users-when-their-settings-change-in-teams.md)
- [Mask phone numbers in Microsoft Teams meetings](ptsn-mask-phone-numbers.md)

### Meeting policies

Meeting policies are used to control what features are available in meetings organized by users who have the policy assigned to them. Meeting policies also affect the meeting join experience of meeting participants.

#### Meeting scheduling

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-meetings-meeting-scheduling.png" alt-text="Screenshot of Teams meeting scheduling policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Private meeting scheduling|On|When **On**, meeting organizers allow users to schedule private meetings.|
|Meet now in private meetings|On|Controls whether a user can start an instant private meeting.|
|Channel meeting scheduling|On|When **On**, meeting organizers allow users to schedule channel meetings within channels that the users belong to.|
|Meet now in channel meetings|On|When **On**, meeting organizers allow users to start instant meetings within channels that the users belong to.|
|Outlook add-in|On|When **On**, meeting organizers allow users to schedule private meetings from Outlook. Read more about [the Teams Meeting add-in in Outlook](Teams-add-in-for-Outlook.md).|
|Meeting registration|On|When **On**, meeting organizers can require registration to join a meeting.|
|Who can register|Everyone|Determines who can register for meetings (if **Meeting registration** is **On**) - **Everyone** or **People in my organization**.|
|Attendance report|Everyone, unless organizers opt-out|This setting allows meeting organizers the ability to see the toggle that turns on or off Attendance Reports within Meeting options.|
|Who is in the report|Everyone, but participants can opt out|This setting controls whether participants in the meeting can opt in or out of offering their attendance information in the Attendance Report. Only the post-meeting report is supported.|
|Attendance summary|Show everything|This setting controls whether to show attendance time information - such as join times, leave times, and in-meeting duration - for each meeting participant. Only the post-meeting report is supported.|

##### Related topics for meeting scheduling

- [Manage who can start instant meetings and schedule meetings](manage-who-can-schedule-meetings.md)
- [Meetings, webinars, and live events](quick-start-meetings-live-events.md)
- [Attendance report for meetings and webinars in Microsoft Teams](/MicrosoftTeams/teams-analytics-and-reports/meeting-attendance-report)

#### Meeting join & lobby

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-meetings-meeting-join-lobby.png" alt-text="Screenshot of Teams meeting join & lobby policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Anonymous users can join a meeting|On|When this setting is on, anyone can join Teams meetings, including Teams users in other organizations that aren't on your allowed domains list. If anonymous join is turned off in org-wide meeting settings, anonymous users can't join any meetings, regardless of what you set here.|
|Anonymous users and dial-in callers can start a meeting|Off|When this setting is turned on, anonymous users and dial-in callers can start a meeting without someone in attendance. When this setting is off, they must wait in the lobby until the meeting is started by someone in your organization, a guest, or a user from a trusted organization. This setting only works if **Anonymous users can join a meeting** is turned on in both the org-wide meeting settings and in this meeting policy and **Who can bypass the lobby** is set to **Everyone**.|
|Who can bypass the lobby|People in my organization and guests|Controls who can join a meeting directly and who must wait in the lobby until they're admitted. This setting controls the default value of who can bypass the lobby in Meeting options; organizers and co-organizers can change this when they set up Teams meetings.|
|People dialing in can bypass the lobby|Off|Controls whether people who dial in by phone join the meeting directly or wait in the lobby, regardless of the **Who can bypass the lobby** setting. When this setting is turned off, dial-in callers must wait in the lobby until they're admitted. This setting controls the default value for Meeting options; organizers and co-organizers can change this when they set up Teams meetings.|

**PowerShell-only meeting join & lobby policies**

|Parameter|Default|Description|
|:-----|:-----|:-----|
|BlockedAnonymousJoinClientTypes|(empty list)|This setting allows users to join a Teams meeting anonymously using a Teams client or using a custom application built using Azure Communication Services. When anonymous meeting join is enabled, both types of clients may be used by default. This optional parameter can be used to block one of the client types that can be used. If both clients are specified, this will be equivalent to disabling anonymous join completely.|

##### Related topics for meeting join & lobby policies

- [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md)
- [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md)
- [Plan for meetings with external participants in Microsoft Teams](plan-meetings-external-participants.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

#### Meeting engagement

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-meetings-meeting-engagement.png" alt-text="Screenshot of Teams meeting engagement policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Meeting chat|On for everyone|Controls which meeting attendees can participate in the meeting chat. When turned off for anonymous participants, they can't read the chat or post messages. Read more about how to [Manage chat in Microsoft Teams meetings](manage-meeting-chat.md)|
|External meeting chat|On|When this is turned on, people can read or write messages in external meeting chats from untrusted organizations.|
|Q&A|On|When **On**, organizers can enable a question and answer experience for their meetings. Read more on [Q&A in Teams Meetings](manage-qna-for-teams.md).|
|Reactions|On|This setting controls whether users can use live reactions such as Like, Love, Applause, Laugh, and Surprise in Teams meetings.|

**PowerShell-only meeting engagement policies**

|Parameter|Default|Description|
|:-----|:-----|:-----|
|StreamingAttendeeMode|Enabled|This setting enables view-only mode for meetings that exceed the capacity of the main meeting. Read more about [Teams view-only meeting experience](view-only-meeting-experience.md).|

##### Related topics for meeting engagement policies

- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

#### Content sharing

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-meetings-content-sharing.png" alt-text="Screenshot of Teams meetings content sharing policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Who can present|Everyone|Controls who can be a presenter in Teams meetings. Organizers and co-organizers can change this when they set up Teams meetings.|
|Screen sharing mode|Entire screen|Controls whether a user is allowed to share a desktop and a window in a Teams meeting. Read more on how to [Configure desktop sharing in Microsoft Teams](configure-desktop-sharing.md).|
|Participants can give or request control|On|Controls whether the user can give control of the shared desktop or window to other meeting participants. This setting isn't supported if either user is in Teams in a browser.|
|External participants can give or request control|Off|This setting controls whether external participants, anonymous users, and guests can be given control or request control of people in your organization's shared screen during a Teams meeting. This setting must be turned on in both organizations for an external participant to take control.|
|PowerPoint Live|On|Controls whether a user can share PowerPoint slide decks in a meeting. External participants, including anonymous, guest, and external access users, inherit the policy of the meeting organizer.|
|Whiteboard|On|Controls whether a user can share the Whiteboard in a meeting. External participants, including anonymous, guest, and external access users, inherit the policy of the meeting organizer. Read more on [how to manage the Whiteboard in Microsoft Teams](manage-whiteboard.md).|
|Shared notes|On|When **On**, attendees can create shared meeting notes through the meeting details.|

**PowerShell-only content sharing policies**

|Parameter|Default|Description|
|:-----|:-----|:-----|
|AllowMeetingCoach|True|This setting lets users turn on Speaker Coach during a Teams meeting. Read more on [how to turn Speaker Coach on or off](meeting-speaker-coach.md).|

##### Related topics for content sharing policies

- [Manage meeting policies for content sharing](meeting-policies-content-sharing.md)
- [Manage who can present and request control in Teams meetings](meeting-who-present-request-control.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

#### Recording & transcription

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-meetings-recording-and-transcription.png" alt-text="Screenshot of Teams meetings recording & transcription policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Meeting recording|On|When **On**, users can record their Teams meetings and group calls to capture audio, video, and screen sharing activity. The meeting organizer and recording initiator need to have recording permissions to record the meeting.|
|Recordings automatically expire|On|When **On**, meeting recordings automatically expire in the number of days shown in the Default expiration time setting.|
|Default expiration time|120|The default expiration time for new meeting recordings. From 1 to 99999 days. **Recordings automatically expire** must also be turned **On**.|
|Store recordings outside your country or region|Off|If you want to store meeting recordings outside of your country or region, turn on both this setting and **Meeting recording**. This setting isn't applicable to recordings stored in OneDrive or SharePoint.|
|Transcription|On|Controls whether captions and transcription features are available during playback of meeting recordings. The person who started the recording needs this setting turned on for these features to work with their recording.|
|Live captions|Off, but organizers and co-organizers can turn them on|This setting is a per-user policy and applies during a meeting. This setting controls whether the **Turn on live captions** option is available for the user to turn on and turn off live captions in meetings that the user attends.|
|Copilot|On with transcript|Controls whether Copilot will be enabled with a persisted transcript or a non-persisted transcript.|

**PowerShell-only recording & transcription policies**

|Parameter|Default|Description|
|:-----|:-----|:-----|
|AllowCartCaptionsScheduling|DisabledUserOverride|This setting determines whether a user can add a URL for captions from a Communications Access Real-Time Translation (CART) captioner to provide real-time captions in meetings.|
|ChannelRecordingDownload|Allow|This setting controls how channel meeting recordings are saved, permissioned, and who can download them.|
|EnrollUserOverride|Disabled|This setting sets voice profile capture, or enrollment, in Teams settings for a tenant.|
|LiveInterpretationEnabledType|DisabledUserOverride|This setting allows meeting organizers to configure a meeting for language interpretation and select attendees to become interpreters that other attendees can select and listen to the real-time translation they provide.|
|MeetingInviteLanguages|None|This setting controls how the join information in meeting invitations displays by enforcing a common language or by enabling up to two languages. All Teams supported languages can be specified using language codes.|
|SpeakerAttributionMode|EnabledUserOverride|Speakers are identified in transcription. If enabled, users can override this setting and choose not to be identified in their Teams profile settings.|
|RoomAttributeUserOverride|(none)|This setting controls the voice-based user identification in meeting rooms. This setting is required for Teams Rooms account. Read more about how to [Manage voice recognition technology controls for an Intelligent Speaker](rooms/voice-recognition.md).|

##### Related topics for recording & transcription policies

- [Teams meeting recording](meeting-recording.md)
- [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)
- [Use OneDrive for Business and SharePoint or Stream for meeting recordings](tmr-meeting-recording-change.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

#### Audio & video

**Navigation:** Teams admin center > Meetings > Meeting policies

:::image type="content" source="media/teams-meetings-audio-and-video.png" alt-text="Screenshot of Teams meetings audio and video policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Mode for IP audio|Outgoing and incoming audio enabled|This setting controls whether incoming and outgoing audio can be turned on in meetings and group calls.|
|Mode for IP video|Outgoing and incoming video enabled|This setting controls whether incoming and outgoing video can be turned on in meetings and group calls.|
|IP video|On|This setting controls whether video can be turned on in meetings hosted by a user and in 1:1 and group calls started by a user. On Teams mobile clients, this setting controls whether users can share photos and videos in a meeting.|
|Local broadcasting|Off|Use NDI or SDI technology to capture and deliver broadcast-quality audio and video over your network.|
|Media bit rate (Kbs)|50000|This setting determines the media bit rate for audio, video, and video-based app sharing transmissions in calls and meetings for the user. It's applied to both the uplink and downlink media traversal for users in the call or meeting. This setting gives you granular control over managing bandwidth in your organization.|
|Network configuration lookup|Off|When **On**, roaming policies in Network topology are checked.|
|Participants can use video effects|All video effects|Controls if participants can customize their camera feed with video background images and filters.|
|Live streaming|Off|Determines whether you provide support for your users to stream their Teams meetings to large audiences through Real-Time Messaging Protocol (RTMP).|

**PowerShell-only audio & video meeting policies**

| Parameter | Default | Description |
|:-----|:-----|:-----|
|AllowBreakoutRooms|True|This setting enables the Breakout Rooms functionality.|
|PreferredMeetingProviderForIslandsMode|TeamsAndSfb|Determines the Outlook meeting add-in availability to users on Islands mode. With the default value of `TeamsAndSfb`, users see both the Skype for Business and Teams add-ins. If you set this value to `Teams`, the Skype for Business add-in will be removed and only the Teams add-in will be shown.|
|TeamsCameraFarEndPTZMode|Disabled|Read more about how to to configure [Far end camera control (FECC) for pan tilt zoom (PTZ) cameras](meeting-policies-audio-and-video.md#far-end-camera-control-fecc-for-pan-tilt-zoom-ptz-cameras).|

##### Related topics for audio & video meeting policies

- [Meeting policy settings for audio & video](meeting-policies-audio-and-video.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)

#### Watermark

**Navigation:** Teams admin center > Meetings > Meeting policies

 Watermarks can be displayed in Teams meetings both for content shared on screen and for attendee video. For watermarks to be available in templates and sensitivity labels, and to the meeting organizer, they must be enabled. These settings require a Teams Premium license.

:::image type="content" source="media/teams-meetings-watermark.png" alt-text="Screenshot of Teams meetings watermark policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Watermark videos|Off|This setting controls watermarks on attendee videos.|
|Watermark shared content|Off|This setting controls watermarks on content shared on screen in a meeting.|

##### Related topics for watermark policies

- [Require a watermark for sensitive Teams meetings](watermark-meeting-content-video.md)
- [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)
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
|Custom backgrounds|Off|This setting gives you the ability to upload custom background images for Teams meetings that appear on your end users' interfaces, ordered by the time of upload. Read how to enable [Custom meeting backgrounds for Teams meetings](custom-meeting-backgrounds.md).|

##### Related topics for customization policies

- [Microsoft Teams Premium - Overview for administrators](enhanced-teams-experience.md)
- [Custom Together Mode scenes in Teams](/platform/apps-in-teams-meetings/teams-together-mode)
- [Set up webinars in Microsoft Teams](set-up-webinars.md)
- [Meeting themes for Teams meetings](meeting-themes.md)
- [Custom meeting backgrounds for Teams Meetings](custom-meeting-backgrounds.md)

### Meeting settings

Meeting settings allow you to customize meeting email invitations and configure network settings including port ranges for media traffic. These settings apply to all meetings organized by users in your organization.

#### Participants

**Navigation:** Teams admin center > Meetings > Meeting settings

:::image type="content" source="media/teams-meeting-settings-participants.png" alt-text="Screenshot of Teams meeting settings for anonymous participants.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Anonymous users can join a meeting|On|This setting will be removed in the future. We recommend leaving this setting **On** and using the **Anonymous users can join a meeting** user level meeting policy control to allow or prevent anonymous meeting join instead.|
|Anonymous users can interact with apps in meetings|On|When **On**, anonymous participants can interact with apps in Teams meetings as long as the app is enabled in a Teams apps permission policy.|

##### Related topics for participants

[Manage anonymous participant access to Teams meetings (IT admins)](anonymous-users-in-meetings.md)

#### Email invitation

**Navigation:** Teams admin center > Meetings > Meeting settings

:::image type="content" source="media/teams-meeting-settings-email-invitation.png" alt-text="Screenshot of Teams meeting settings for email invitations.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Logo URL|(none)|The URL where your organization's logo is stored. Displayed in meeting invites.|
|Legal URL|(none)|The URL for your organization's legal site. Displayed in meeting invites.|
|Help URL|(none)|The URL for your organization's help or support site. Displayed in meeting invites.|
|Footer|(none)|Footer text to be included in meeting invitations. Displayed in meeting invites.|

##### Related topics for email invitation

[Manage meeting settings in Microsoft Teams](meeting-settings-in-teams.md)

#### Network

**Navigation:** Teams admin center > Meetings > Meeting settings

:::image type="content" source="media/teams-meeting-settings-network.png" alt-text="Screenshot of Teams meeting settings for network.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Insert Quality of Service (QoS) markers for real-time media traffic|Off|When **On**, all real-time media traffic for meetings is marked so that the network packets can be prioritized.|
|Select a port range for each type of real-time media traffic|Specify port ranges|Allows you to specify port ranges for different types of media traffic or automatically use available ports.|
|Audio|Starting port: 50000 / Ending port: 50019|Start and end ports for audio traffic. (Only available when **Select a port range for each type of real-time media traffic** is set to **Specify port ranges**)|
|Video|Starting port: 50020 / Ending port: 50039|Start and end ports for video traffic. (Only available when **Select a port range for each type of real-time media traffic** is set to **Specify port ranges**)|
|Screen sharing|Starting port: 50040 / Ending port: 50059|Start and end ports for screen sharing traffic. (Only available when **Select a port range for each type of real-time media traffic** is set to **Specify port ranges**)|

##### Related topics for network

[Implement Quality of Service (QoS) in Microsoft Teams](qos-in-teams.md)

### Live events policies

**Navigation:** Teams admin center > Meetings > Live events policies

Teams live events policies are used to turn on or off features, such as who can join a live event, if transcription is provided for attendees, or if recording live events is available for people who schedule and hold live events.

:::image type="content" source="media/teams-live-events-policies.png" alt-text="Screenshot of Teams live events policies.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Live events scheduling|On|When **On**, users in your organization can create and schedule live events in Teams.|
|Transcription for attendees|Off|Turning on this setting enables live event attendees to see live captions and subtitles during the event. This setting can only be applied to events produced in Teams.|
|Who can join scheduled live events|Everyone|This setting restricts who can attend live events. Teams permission types are updated based on the selection. For PowerShell, the [Set-CsTeamsMeetingBroadcastPolicy](/powershell/module/skype/set-csteamsmeetingbroadcastpolicy) cmdlet with `-BroadcastAttendeeVisibilityMode` gives the options to also use `EveryoneInCompanyAndExternal` or `InvitedUsersInCompanyAndExternal`.|
|Record an event|Organizer can record|This setting controls whether the event is recorded. Read more about [live event recording policies in Microsoft Teams](teams-live-events/live-events-recording-policies.md).|

> [!NOTE]
> GCC High and DoD customers must set up live events policies using Windows PowerShell. Read examples of how to [Use PowerShell to set live events policies in Microsoft Teams](/teams-live-events/set-teams-live-events-policies-using-powershell).

#### Related topics for live events meeting policies

- [What are Teams live events?](what-are-teams-live-events.md)
- [Plan for live events in Microsoft Teams](teams-live-events/plan-for-teams-live-events.md)
- [Live streaming events in Microsoft Teams](teams-stream-overview.md)
- [Configuring encoders for live event streaming in Microsoft Teams](teams-encoder-configuration.md)
- [Set-CsTeamsMeetingBroadcastPolicy](/powershell/module/skype/set-csteamsmeetingbroadcastpolicy)

### Live event settings

Teams live events settings let you control org-wide settings for all live events that are scheduled in your organization.

#### Support URL

**Navigation:** Teams admin center > Meetings > Live event settings

:::image type="content" source="media/teams-live-events-settings-support-url.png" alt-text="Screenshot of Teams live event support URL setting.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Custom support URL|(none)|URL for live event attendees to contact support during a live event.|

#### Video distribution providers

**Navigation:** Teams admin center > Meetings > Live event settings

:::image type="content" source="media/teams-live-events-settings-video-distribution-providers.png" alt-text="Screenshot of Teams live event settings for video distribution providers.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Video distribution provider|Off|When **On**, you can select a software defined network (SDN) solution or enterprise content delivery network (eCDN) solution.|
|SDN provider name|(none)|The SDN provider that you want to use for live events.|

> [!NOTE]
> Additional fields may be available depending on the selected SDN provider.

##### Related topics for live events settings

[Configure live event settings in Microsoft Teams](/microsoftteams/teams-live-events/configure-teams-live-events)

### Meeting template policies

**Navigation:** Teams admin center > Meetings > Meeting template policies

Meeting templates policies let you create and set up policies that control what templates people in your organization can see. Microsoft Teams custom meeting templates require a Teams Premium license.

:::image type="content" source="media/teams-meeting-template-policies.png" alt-text="Screenshot of Teams messaging template policies.":::

#### Related topics for meeting template policies

- [Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)
- [Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md)
- [Manage meeting templates in Microsoft Teams](manage-meeting-templates.md)
- [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)

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
|Translate messages|On|Turn on this setting to let users automatically translate Teams messages into the language specified by their personal language settings for Microsoft 365 or Office 365. Read more on [inline message translation in Microsoft Teams](inline-message-translation-teams.md)|
|Immersive reader for messages|On|When **On**, users can view messages in Microsoft Immersive Reader.|
|Send urgent messages using priority notifications|On|If you turn on this setting, users can send messages using priority notifications. Priority notifications notify users every 2 minutes for 20 minutes or until messages that are marked as urgent are picked up and read by the recipient.|
|Create voice messages|Allowed in chats and channels|This setting controls whether users can leave audio messages in chats and channels.|
|On mobile devices, display favorite channels above recent chats|Not enabled|When **Enabled**, this setting moves favorite channels to the top of the mobile device screen so that a user doesn't need to scroll to find them.|
|Remove users from group chats|On|Turn on this setting to let a user remove other users from a group chat. This feature lets you continue a chat with a smaller group of people without losing the chat history.|
|Suggested replies|On|When **On**, users get text predictions for chat messages.|
|Chat permissions role|Restricted permissions|Defines the supervised chat role of a user.|
|Users with full chat permissions can delete any message|Off|Use this setting to let users with full chat permissions delete any group or meeting chat message.|

### Related topics for messaging policies

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
|Make private calls|On|This setting controls all calling capabilities in Teams. Turn off this setting to turn off all calling functionality in Teams.|
|Cloud recording for calling|Off|This setting allows you to control whether call recording is available for your users.|
|Transcription|Off|This setting allows you to control whether post-call transcriptions are available for your users.|
|Routing for PSTN calls|Use default settings|This setting controls how inbound PSTN calls should be routed. These PSTN calls can be sent to voicemail, sent to unanswered settings, use default call routing, or you can allow your users to decide.|
|Routing for federated calls|Use default settings|This setting controls how inbound federated calls should be routed. These federated calls can be sent to voicemail, sent to unanswered settings, or use default call routing.|
|Call forwarding and simultaneous ringing to people in your organization|On|Controls whether incoming calls can be forwarded to other users or can ring another person in your organization at the same time.|
|Call forwarding and simultaneous ringing to external phone numbers|On|Controls whether incoming calls can be forwarded to an external number or can ring an external number at the same time.|
|Voicemail for inbound calls|Let users decide|When set to **On** or **Let users decide**, inbound calls can be sent to voicemail.|
|Inbound calls can be routed to call groups|On|This setting controls whether incoming calls can be forwarded to a call group.|
|Delegation for inbound and outbound calls|On|This setting enables inbound calls to be routed to delegates, allowing delegates to make outbound calls on behalf of the users for whom they have delegated permissions.|
|Prevent toll bypass and send calls through the PSTN|Off|Turn on this setting to send calls through the PSTN and incur charges rather than sending them through the network and bypassing the tolls.|
|Music on hold for PSTN calls|On|Controls whether music is played when a PSTN caller is placed on hold.|
|Busy on busy during calls|Off|Controls how incoming calls are handled when a user is already in a call or conference or has a call placed on hold.|
|Web PSTN calling|On|This setting enables users to call PSTN numbers using the Teams web client.|
|Real-time captions in Teams calls|On|This setting allows you to control whether real-time captions in Teams calls are available for your users.|
|Automatically answer incoming meeting invites|Off|This setting controls whether incoming meeting invites are automatically answered on Teams phones. Keep in mind that this setting applies only to incoming meeting invites. It doesn't apply to other types of calls.|
|Spam filtering|On|This setting allows you to control the type of Spam filtering available on incoming calls.|
|SIP devices can be used for calls|Off|This setting enables users to use a SIP device to make and receive calls.|
|Open apps in browser for incoming PSTN calls|Off|This setting controls whether apps are automatically opened in the browser for incoming PSTN calls to your users. This setting can be used to pass the phone of an inbound caller to an app to find the associated customer record while the call is taking place.|

**PowerShell-only calling policies**

|Parameter|Default|Description|
|:-----|:-----|:-----|
|AllowCallRedirect|None|This setting provides the ability to configure call redirection capabilities on Teams phones. When set to **Enabled** users have the ability to redirect received calls.|
|CallRecordingExpirationDays|60|This setting controls the expiration of recorded 1:1 calls, measured in days.|

#### Related topics for calling policies

- [Plan your Teams voice solution](cloud-voice-landing-page.md)
- [Configure calling policies in Microsoft Teams](teams-calling-policy.md)
- [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)

### Call hold policies

**Navigation:** Teams admin center > Voice > Call hold policies

Call hold policies allow you to specify a custom audio file to play while calls are on hold. The **Music on hold** setting must also be **Enabled** in **Voice** > **Calling policies** or no music will be played.

:::image type="content" source="media/teams-call-hold-policy.png" alt-text="Screenshot of Teams call hold policies.":::

#### Related topics for call hold policies

- [How to setup Music on hold](music-on-hold.md)
- [Set-CsTeamsCallHoldPolicy](/powershell/module/skype/set-csteamscallholdpolicy)

### Call park policies

**Navigation:** Teams admin center > Voice > Call park policies

Call park lets people put a call on hold and transfer it to other people within your organization. Call park policies let you control which users are call park enabled and make other call park setting changes for them.

:::image type="content" source="media/teams-call-park-policy.png" alt-text="Screenshot of Teams call park policy.":::

| Setting | Default | Description |
|:-----|:-----|:-----|
|Call park|Off|Turn on this setting to let your users place a call on hold on one device and pick it up from another device.|
|Call pickup start of range|10|The first parked call renders a pickup code of the start of range (for instance 10). The next parked call renders a pickup code incremented by 1; that is, 11, and so on, until the end of the range is rendered as a pickup code.|
|Call pickup end of range|99|The pickup code of the last parked call within in the range. After which, the rendered pickup codes start over from the start of the range once again.|
|Park timeout (seconds)|300|The number of seconds to wait before ringing back when the parked call hasn't been picked up. The allowed range is 120-1800 seconds.|

#### Related topics for call park policies

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
|Replace the caller ID with this resource account/service number|(Choose a resource account/service number)|Choose a resource account or service number to replace the caller ID of users. This option is available if you selected ***Resource account** or **Service number** in **Replace the caller ID with**.|

#### Related topics for Caller ID policies

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
|External location lookup mode|Off|Turn on this setting to allow your end users to configure their emergency address when they're working from a network location outside of the corporate network. Read more about [emergency addresses for remote locations](emergency-calling-dispatchable-location.md) and how to [add, change, or remove an emergency location](add-change-remove-emergency-location-organization.md) or [place for an emergency location](add-change-remove-emergency-place-organization.md) for your organization.|
|Notification mode|(Blank)|This setting controls the type of notification sent to a security desk or team when someone calls emergency services. You can set it to just send a notification to them, or if they can, join an emergency call muted or unmuted.|
|Emergency service disclaimer|(Blank)|Text that displays in a banner to remind your end users to confirm their emergency location.|
|Numbers to dial for emergency calls notifications|(Blank)|If you selected either of the **Conference in muted** options for **Notification mode**, you can enter a PSTN phone number of a user or group to call and join the emergency call.
|Users and groups for emergency calls notifications|(Blank)|Search for and select one or more users or groups, such as your organization's security desk, to notify when an emergency call is made. The notification can be sent to email addresses of users, distribution groups, and security groups. A maximum of 50 users can be notified.|
|Dynamic emergency calling|Off|If you turn on this setting, users assigned to the policy can use emergency call routing features when they move from one location to another. This setting is found under **Emergency policies** > **Call routing policies**. Read more about [how to plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).|

#### Related topics for emergency policies

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage emergency call routing policies for Direct Routing](manage-emergency-call-routing-policies.md)
- [Manage emergency locations for your organization](add-change-remove-emergency-location-organization.md)
- [Add places to emergency locations](add-change-remove-emergency-place-organization.md)
- [Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)
- [Set-CsTeamsEmergencyCallingPolicy](/powershell/module/skype/set-csteamsemergencycallingpolicy)
- [Set-CsTeamsEmergencyCallRoutingPolicy](/powershell/module/skype/set-csteamsemergencycallroutingpolicy)

### Voice routing policies

**Navigation:** Teams admin center > Voice > Voice routing policies

A voice routing policy for Direct Routing is linked to a voice route using PSTN usage records. You can add existing PSTN usage records, change the order in which the usages are processed, and assign the voice routing policy to users or resource accounts.

:::image type="content" source="media/teams-policies-voice-routing.png" alt-text="Screenshot of Teams voice routing policies.":::

#### Related topics for voice routing policies

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
|Voicemail transcription|On|Turn on this setting to enable transcription for voicemails.|
|Translation for transcriptions|On|Turn on this setting to enable translation for voicemail transcriptions.|
|Mask profanity in voicemail transcription|Off|If you turn on this setting, profanity will be masked in voicemail transcriptions.|
|Users can share data for service improvement|On|If you turn on this setting, users can share voicemail and transcription data for training and improving accuracy. If you turn off this setting, voicemail data won't be shared.|
|Before the user's greeting, play audio file|(none)|The audio file to play to the caller before the user's voicemail greeting is played.|
|After the user's greeting, play audio file|(none)|The audio file to play to the caller after the user's voicemail greeting has played and before the caller is allowed to leave a voicemail message.|
|Disconnect the call if preamble or postamble can't be played|Off|If you turn on this setting, the Pre- or Postamble will play before the caller can leave a message.|

#### Related topics for voicemail policies

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

#### Related topics for end-to-end encryption policies

- [Security and Microsoft Teams](teams-security-guide.md)
- [Set-CsTeamsEnhancedEncryptionPolicy](/powershell/module/teams/Set-CsTeamsEnhancedEncryptionPolicy)
