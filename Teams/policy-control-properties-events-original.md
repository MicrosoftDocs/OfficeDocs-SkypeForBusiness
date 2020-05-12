---
title: Policy control properties and events for Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: majaisin
description: A list of properties and events for the policy controls for Microsoft Teams.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---
# Policy control events for Microsoft Teams

The following article contains lists of the properties sent with various events, and lists of the events themselves, arranged by product.

## Property lists

### Properties sent with all events

| Property name                    | Description                                                          |
|----------------------------------|----------------------------------------------------------------------|
| EventInfo_Time                   | Event generation time                                                |
| EventInfo_Name                   | Event name - Used to differentiate between event types               |
| EventInfo_BaseType/name          | Event type - Used to differentiate between event types in an event   |
| EventInfo_Source                 | Source of the event generation                                       |
| AppInfo_Language                 | App language                                                         |
| AppInfo_ETag                     | Experiment ID assigned to a user                                     |
| DeviceInfo_OsBuild               | Build version of the OS                                              |
| UserInfo_Mri                     | Type a user ID                                                       |
| Session_RunId                    | Type of a session ID                                                 |
| DeviceInfo_DetailModel           | Model of the device                                                  |
| UserInfo_TimeZone                | Time zone of the user                                                |
| DeviceInfo_OsName                | Device OS name                                                       |
| DeviceInfo_NetworkProvider       | Device network provider                                              |
| DeviceInfo_Model                 | Device Model                                                         |
| DeviceInfo_NetworkType           | Device network type                                                  |
| UserInfo_Language                | User language - similar to app language                              |
| client_ring/UserInfo_Ring        | User ring that helps to release features to early adopters           |
| UserInfo_Id                      | User ID                                                              |
| UserInfo_TenantId                | Tenant ID                                                            |
| EventInfo_SdkVersion             | SDK version used to generate the event                               |
| DeviceInfo_Id                    | Device ID provided by device OS                                      |
| eventpriority                    | Priority of an event                                                 |
| DeviceInfo_Make                  | Device manufacturer                                                  |
| AppInfo_Version                  | Version of the app                                                   |
| DeviceInfo_OsVersion             | Device OS version                                                    |
| Session_Id/SessionId             | Session ID of the request                                            |
| Session_Environment              | Session Environment                                                  |
| isNetworkIssue                   | Captures info if there was a network issue while serving the request |
| UserRole                         | User role in a tenant                                                |
| Tenant_Model                     | Captures if the account is a freemium or enterprise account          |
| licenseType/UserInfo_LicenseType | Licence type assigned to the user                                    |
| UserLocale                       | Locale in which app is being accessed                                |
| Intune_sdkVersion                | Version of the Intune SDK                                            |
| Intune_sdkBundleVersion          | Detailed version of the Intune SDK                                   |
| AppInfo_Environment              | Environment in which the app is being access                         |

### Properties sent with panelaction events

| Property name         | Description                                                        |
|-----------------------|--------------------------------------------------------------------|
| Action_DestinationUri | Uri of the resource being accessed by user action                  |
| Panel_Uri             | Uri of the panel delivered to the user                             |
| Action_Gesture        | Type of gesture performed by user on the app                       |
| Action_ScenarioType   | Feature grouping that relates to business metric for feature       |
| Panel_Type            | Panel type accessed by the user                                    |
| Action_Outcome        | Outcome of the action performed by user                            |
| Team_Id               | ID of the team in which action was performed by the user           |
| Module_Type           | Type of the module which hosted user action                        |
| Module_Name           | Name of the module which hosted user action                        |
| Module_Summary        | Summary of the module that hosted user action                      |
| Thread_Id             | ID of the thread that was accessed by user                         |
| Panel_PreviousUri     | URI of the previous panel                                          |
| Panel_Region          | Region where the panel was hosted in the app                       |
| Panel_LaunchMethod    | Method through which the panel was launched                        |
| Panel_PreviousType    | Type of the previous panel                                         |
| Thread_Type           | Type of thread accessed by user                                    |
| Module_State          | State of the module accessed by user                               |
| Action_Scenario       | Feature inside a group of features that relates to business metric |
| Panel_LaunchSource    | Source information of the panel that was launched                  |
| Tab_Type              | Type of the tab accessed by user                                   |
| Team_Type             | Type of team accessed by user                                      |

### Properties sent with panelview events

| Panel_Uri          | Uri of the panel delivered to the user                   |
|--------------------|----------------------------------------------------------|
| Panel_Type         | Panel type accessed by the user                          |
| Team_Id            | ID of the team in which action was performed by the user |
| Thread_Id          | ID of the thread that was accessed by user               |
| Panel_PreviousUri  | URI of the previous panel                                |
| Panel_Region       | Region where the panel was hosted in the app             |
| Panel_LaunchMethod | Method through which the panel was launched              |
| Panel_PreviousType | Type of the previous panel                               |
| Thread_Type        | Type of thread accessed by user                          |
| Panel_LaunchSource | Source information of the panel that was launched        |
| Tab_Type           | Type of the tab accessed by user                         |
| Team_Type          | Type of team accessed by user                            |

### Properties sent with scenario events

| Property name        | Description |
|----------------------|-------------|
| Scenario_Status      | Status of a scenario - Abandon/OK/ERROR |
| Scenario_Step        | When a scenario contains multiple steps with different failure points, this property captures details about the step |
| Scenario_StatusCode  | Property records status code of the scenario based on scenario success or failure |

### Properties sent with trace events

| Property name | Description                                                                                    |
|---------------|------------------------------------------------------------------------------------------------|
| Trace_message | Contains error string and details about the reasons due to which a failure might have happened |

## Events

### Calendar

| Action_Scenario    | Description | Type | How the event is used | Basic Subtype |
|--------------------|-------------|------|-----------------------|---------------|
| navCalendar        |             |      |                       |               |
| scrollCalendarList |             |      |                       |               |

### Core

| Action_Scenario    | Team Owner | Description | Type | How the event is used | Basic Subtype |
|--------------------|------------|-------------|------|-----------------------|---------------|
| enableCategory     | Core | <ul><li>Enable a type of notification</li><li>Enable incoming call notifications</li></ul> | Basic | Notifications are key to drive engagement. This provides key success data for notification settings | App key feature success data |
| pushNotification   | Core | <ul><li>Launch via notification</li><li>Push notification clicked</li><li>Reconnecting push notification is tapped</li><li>**Reconnect failed** push notification is tapped</li></ul> | Basic | Success of notification delivery and user action on notification | App key feature success data |
| deviceAddressBookSync | Core     |     |     |     |     |
| deviceAddressBookUnsync | Core |     |     |     |     |
| chatAvatarEdit | Core |     |     |     |     |
| chatAvatarEditGallery | Core |     |     |     |     |
| chatAllowJoinViaLink | Core |     |     |     |     |
| chatShareLink | Core |     |     |     |     |
| composeVault | Core |     |     |     |     |
| conversation | Core |     |     |     |     |
| dashboardNav | Core |     |     |     |     |
| navBookmark | Core |     |     |     |     |
| navChat | Core |     |     |     |     |
| navChatAndChannel | Core |     |     |     |     |
| navDashboardTab | Core |     |     |     |     |
| navMore | Core |     |     |     |     |
| navSaved | Core |     |     |     |     |
| navCamera | Core |     |     |     |     |
| navContacts | Core |     |     |     |     |
| navVideocamera | Core |     |     |     |     |
| officeLens | Core |     |     |     |     |
| removeUser_CM | Core |     |     |     |     |
| contactActivity | Core |     |     |     |     |
| deleteContact | Core |     |     |     |     |
| editContact | Core |     |     |     |     |
| openContactCard | Core |     |     |     |     |
| addMembers | Core |     |     |     |     |
| channelFollow | Core |     |     |     |     |
| channelUnfollow | Core |     |     |     |     |
| channelsActiveSetting | Core |     |     |     |     |
| chatCreation | Core |     |     |     |     |
| chatStart | Core |     |     |     |     |
| createOrJoinTeam | Core |     |     |     |     |
| editChannel | Core |     |     |     |     |
| editNavigation | Core |     |     |     |     |
| editTeam | Core |     |     |     |     |
| enableQuietDays | Core |     |     |     |     |
| forcedUpdateAccept | Core |     |     |     |     |
| forcedUpdateExit | Core |     |     |     |     |
| forcedUpdatePrompt | Core |     |     |     |     |
| messagedEditMessage | Core |     |     |     |     |
| newChat | Core |     |     |     |     |
| noBGActivityDetected | Core |     |     |     |     |
| notBlockedDevice | Core |     |     |     |     |
| openAppDrawer | Core |     |     |     |     |
| openHamburgerMenu | Core |     |     |     |     |
| processInBG | Core |     |     |     |     |
| processInFG | Core |     |     |     |     |
| renewTeam | Core |     |     |     |     |
| shareInto | Core |     |     |     |     |
| teamCreate | Core |     |     |     |     |
| teamEdit | Core |     |     |     |     |
| viewChannelMembers | Core |     |     |     |     |
| guideMe | Core |     |     |     |     |
| resolveIssue | Core |     |     |     |     |
| reorderChannelItem | Core |     |     |     |     |
| markChannelRead | Core |     |     |     |     |
| pinChannel | Core |     |     |     |     |
| unpinChannel | Core |     |     |     |     |
| hideChannel | Core |     |     |     |     |
| scrollDatePicker | Core |     |     |     |     |
| selectCalendarDate | Core |     |     |     |     |
| chatAvatarEditCamera | Core |     |     |     |     |
| chatAvatarEditView | Core |     |     |     |     |
| tapDatePickerHandle | Core |     |     |     |     |
| dragDatePickerHandle | Core |     |     |     |     |
| reportAbuseOpen | Core |     |     |     |     |
| [createTeam, createChannel] | Core | <ul><li>Tap “Skip” button in “Add Members” page (check existing first)</li><li> Tap “Done” button in “Add Members” page (check existing first)</li><li>Show team/channel creation acknowledgement</li></ul> | Basic | Teams and channels are essential construct of teams. This item provides success data around successful addition of members in a team and successful creation of a new team | App key feature success data   |
| [editTeam, editChannel] | Core | <ul><li>Tap “Cancel” button in “Add Members” page (existing team/channel)</li><li>Tap “Done” button in “Add Members” page (existing team/channel)</ul></li> | Basic | Teams and channels are essential construct of teams. This item provides success data around successful addition of members in a team and successful creation of an existing team | App key feature success data   |
| officeLens or cameraImage | Core | camera picture selected - standard camera or office lens (need databag prop stating imageCount) | Basic | Key success metrics for office lens integration with teams | App key feature success data |
| acknowledgeSettingChange | Core | Acknowledge update in **we updated notification setting** dialog | Basic | Notification is key for driving engagement. This is a feature success metrics to ack notification update. Used to deduce overall notification reliability. | App key feature success data   |
| addChannel | Core | Admin Add channel | Basic | Teams and channels are essential construct of teams. This item provides success data around successful creation of a channel. |     |
| addMember | Core | Taps the Invite people button in more menu | Basic | This provide key feature success telemetry around freemium invite. Helps the team understand feature discoverability and success metrices. | App key feature success data |
| alertsNavAlert | Core | Tapping on a feed item | Basic | Feature success telemetry, see event description. | App key feature success data   |
| appBG | Core | App BG | Basic  | Time spent on app is a key metric to understand overall app engagement and this metric helps us deduce overall time spent on the app. | App key feature success data   |
| appKilled | Core | App Killed | Basic | Time spent on app is a key metric to understand overall app engagement and this metric helps us deduce overall time spent on the app. | App key feature success data   |
| cancelNavigationToLink | Core | User chose to cancel navigation | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| cancelRequestToJoinTeam | Core | Cancel request to join team | Basic | Teams and channels are essential construct of teams. This item is required to measure feature discoverability and success for joining a team. | App key feature success data   |
| cancelRequestToJoinTeamError | Core | Error with cancel join request | Basic | Teams and channels are essential construct of teams. This item is required to measure feature discoverability and success for successful completion of  joining a team. | App key feature success data   |
| castPpt | Core | <ul><li>Tapping on share a PowerPoint option</li><li>Selecting a particular PowerPoint</li><li>Selecting Teams and Channels folder in file picker page</li><li>Selecting OneDrive folder in file picker page</li><li>Stopping the casting session</li><li>Tapping on multitasking PiP</li>Selecting display option from file view</li></ul> | Not in production you can remove these rows/Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| castScreen | Core | <ul><li>Tapping on share screen option</li><li>Stopping the screen sharing session</li><li>Selecting display option from file view</li></ul> | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| changeIsActiveSetting | Core | Change desktop activity based notification. | Basic | Notifications are key to drive engagement. This provides key success data for push notification | App key feature success data   |
| channel | Core | New message button/textbox in chat. | Basic | Provides key success data for compose messages in channel and overall app engagement. | App key feature success data   |
| ChannelDetails | Core | <ul><li>User taps on channel header</li><li>navigates to channel details page</li></ul> | Basic | Provides key success data for channel navigation | App key feature success data   |
| channelFollow/channelUnfollow | Core | Follow channel | Basic | Provides key success data on following the channel | App key feature success data   |
| channelNav | Core | Navigating to a channel from anywhere | Basic | Provides key success data for channel navigation and entrypoint discoverability | App key feature success data   |
| channelNotificationSettings | Core | <ul><li>Respond to “New Notification settings” dialog</li><li> Tap channel notification settings button in channel view</li><li>Select a channel notification setting</li></ul> | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| channelTabOverflow | Core | Clicks on More tab in channel | Basic | As number of apps are increasing in teams, this is an imp metrics for success data for tabs discoverability and features | App key feature success data   |
| Chat - No AS Assigned | Core | <ul><li>Done button on adding a user to a chat</li><li>User taps on chat list filter to filter by unread</li></ul> | Basic | Key success metrics for viewing unread chat or editing chat roaster | App key feature success data   |
| chatAddChat | Core | Add member to chat button tapped (this will be same for 1:1 chat & group chat) | Basic | Key success metrics for editing chat roaster | App key feature success data   |
| chatCM_CopyText | Core | tap copy text on chat context menu | Basic | For a chat product copy paste is important. Provides success data for copy paste feature in chats | App key feature success data   |
| chatCM_DeleteMessage | Core | tap delete message on chat context menu | Basic | Provides success data for delete message feature in chats | App key feature success data   |
| chatCM_edit | Core | tap edit on chat context menu | Basic | Provides success data for edit message feature in chats | App key feature success data   |
| chatCM_Forward | Core | Tap forward on chat context menu | Basic | Provides success data for forward message feature in chats | App key feature success data   |
| chatCM_markUnread | Core | Tap mark as unread on chat context menu | Basic | Provides success data for mark as read or unread message feature in chats | App key feature success data   |
| chatCM_save | Core | Tap save on chat context menu | Basic | Provides success data for save message feature in chats | App key feature success data   |
| chatCM_SeenBy | Core | Tap on Seen by context menu option. Read Receipts; aka read by (readby) | Basic | Provides success data for read receipts feature in teams | App key feature success data   |
| chatContactsEnter | Core | User enters chat contacts tab | Basic | Provides success data for contacts tab in teams | App key feature success data   |
| ChatDetails | Core | User taps on chat header / navigates to chat detail page | Basic | Provides success and discoverability data for chat details page | App key feature success data   |
| chatRecentEnter | Core | User enters the chat recent tab | Basic | Feature success telemetry, see event description. | App key feature success data   |
| chatSendMessage | Core | Send Chat Message | NSD | As teams is a chat and collaboration product, this is a required success metrics for the product all up. Any dip in this metrics would be alarming | Activity success   |
| clickPhotoOfficeLens | Core | Click on **Take photo** - launch camera (android only) | Basic | Provide success metrics for camera integration and image sharing | App key feature success data   |
| composeExpandComposer | Core | Format button tapped | Basic | Provide success data for rich text box integration | App key feature success data   |
| composeFilePick | Core | native file picker launched | Basic | Provide success data for files sharing  |     |
| composeImagePicker | Core | Image button tapped | Basic | Provide success metrics for image sharing | App key feature success data  |
| composeLocation | Core | Location button tapped in compose | Basic | Provide success metrics for location integration in teams| App key feature success data   |
| composeMention | Core | At mention | Basic | For a collaboration product @mentioning and getting someone's attention is important. This provides success data for @mention feature in teams | App key feature success data   |
| composeOpenEmoticonPicker | Core | emoticon picker tapped | Basic | Provide success data for emoticon picker | App key feature success data   |
| composeOpenFunPicker | Core | Fun picker tapped | Basic | Provide success data for fun picker including giphy and stickers | App key feature success data   |
| consumeVoiceMessage  | Core | Voice message played | Basic | Voice message is important part of mobile messaging and is a competition parity feature. Provides success data for voice message consumption | App key feature success data   |
| ContactCard_SeeMoreOOF | Core | See move of long OOF message |     |     |     |
| conversation, tabs | Core | Tab clicked | Basic | Tabs are essential construct of teams this telemetry is fired whenever a tab is clicked in a channel | App key feature success data   |
| copyLink | Core | Copy link to channel post | Basic | Feature success mertics for Copy link feature | App key feature success data   |
| createChannel | Core | <ul><li>Tap “Done” button in “Create Channel” Page</li><li>Tap “Cancel” button in “Create Channel” Page</li><li>Show validation error</li></ul> | Basic | Teams and channels are essential construct of teams. This item provides success data around successful creation or discard action for new channel creation | App key feature success data   |
| createTeam | Core | <ul><li>Tap “Done” button in “Create Team” Page</li><li>Tap “Cancel” button in “Create Team” Page</li><li>Validation error shown</li></ul> | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| disabled | Core | User taps **Skip notifications** in FRE | Basic | Notifications are key to drive engagement. This provides key success data for skipping the notification in FRE flow | App key feature success data   |
| disableQuietDays | Core | Quiet Days disabled | Basic | Feature success telemetry for quiet days | App key feature success data   |
| disableQuietHours | Core | Quiet Hours disabled | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| discoverTeams | Core | Navigate to Browse & Join Teams page | Basic | Required to measure feature discoverability and success | App key feature success data   |
| dismissFlyout | Core | Dismiss button pressed | Basic | Required to measure feature discoverability and success | App key feature success data   |
| dismissModality | Core | Exit modality picker without sharing |     |     |     |
| dismissModalityPicker | Core | Modality picker button pressed |     |     |     |
| dismissReadReceiptsNotice | Core | User pressed **got it** from feature notice | Basic | Key feature success metrics for read receipts | App key feature success data   |
| DLPDelete | Core | User deleted blocked message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPEdit | Core | User edited blocked message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPOverride | Core | User overrode blocked message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPOverrideReport | Core | User reported false positive and overrode message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPReport | Core | User reported false positive | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPResolve | Core | User attempted to resolve DLP message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPSeeOriginal | Core | User tapped to see original message | Basic | Feature success telemetry, see event description. | App key feature success data  |
| edit | Core | Edit button in the message | Basic | Provides success data for edit message feature in chats | App key feature success data   |
| enabled | Core | <ul><li>User taps **Enable notifications** in FRE</li><li>User taps Enable in reminder</li></ul> | Basic | Notifications are key to drive engagement. This provides key success data on enabling the notification in FRE flow | App key feature success data   |
| enabled, notNow | Core | Notification Permission Prompt Accept button | Basic | Captures how many people have enabled the notification, provide information with app engagement. Required for feature success | App key feature success data   |
| enabled/notNow | Core | FRE Notifications Permission (iOS) | Basic | Lets us capture user engagement with the notification feature. | App key feature success data   |
| enablediOSPrompt | Core | User actually enables notifications in iOS notifications permissions prompt | Basic | This gives us information about Users who actually enables notifications in iOS from notifications permissions prompt | App key feature success data   |
| enabledQuietDays | Core | Quiet Days enabled | Basic | Feature success telemetry for quiet days | App key feature success data   |
| enableLocationPermission | Core | Enable location services (TBD) | Basic | Feature success telemetry for location services | App key feature success data   |
| enableQuietHours | Core | Quiet Hours enabled | Basic | Feature success telemetry for quiet hours | App key feature success data   |
| endEditing | Core | Save button pressed |     | Feature success telemetry for edit feature |     |
| endMyShift | Core | <ul><li>No of devices in shared mode</li><li>No of time signed out</li></ul> | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| expandCollapseSection | Core | Tap a section header to expand/collapse section | Basic | Feature success telemetry | App key feature success data   |
| federatedUpgradeNewChat | Core | User upgrades legacy chat to native | Basic | This is required to get the success data for federated chats feature | App key feature success data   |
| files, conversation, oneNote etc | Core | Tab clicked | Basic | Let us know the  about tab discoverability and feature success for tabbed layout | App key feature success data   |
| firstTimeSignedIn | Core | <ul><li>Sign-in Errors Seen by User</li><li>Record telemetry about MAM/MDM policies implemented on first time login</li><li>Record app install referrer parameters after first time successful login</li></ul> | Basic | Feature success telemetry for intune integration for MAM and MDM. Provides success data about failure during FRE | App key feature success data   |
| firstTimeSignedIn | Core | <ul><li>Sign-in success</li><li>First sign-in Succeeded</li><ul> | Basic | Provides success data about successful sign ins during FRE | App key feature success data   |
| formattingBold | Core | Bold | Optional |     | App key feature success data  |
| formattingHighlight | Core | Highlight | Optional |     | App key feature success data   |
| formattingImportant | Core | Important | Optional |     | App key feature success data   |
| formattingItatlics | Core | Italics | Optional  |     | App key feature success data   |
| formattingTextColor | Core | Text color | Optional |     | App key feature success data   |
| formattingUnderline | Core | Underline | Optional  |     | App key feature success data   |
| FRE - No AS Assigned | Core | Record telemetry about MAM/MDM policies on app launch to gather data about active users | Basic | Feature success telemetry for intune integration for MAM and MDM. Provides success data about failure during FRE | App key feature success data   |
| freDone | Core | FRE done | Basic |     | App key feature success data   |
| funSearchQueryEntered  | Core | Giphy query entered | Optional |     | App key feature success data   |
| funSelectItem | Core | Giphy image choose | Basic | Success data for giphy attachment feature in teams | App key feature success data   |
| galleryImage | Core | image uploaded - gallery | Basic | Success data for image attachment feature in teams | App key feature success data   |
| goToNotificationSettings | Core | Go to notification settings page from **we updated notification settings** dialog | Basic | Notification is key for driving engagement. This is a feature success metrics to understand notifications. Used to deduce overall notification reliability | App key feature success data   |
| hamburgerMenu | Core | Navigate to hamburger menu | Basic | Hamburger contains important actions such as account switch, notification settings, data setting, profile settings, this is important to understand hamburger menu discoverability  | App key feature success data   |
| hide | Core | Hide chat | Basic | Feature success telemetry for hiding chats | App key feature success data   |
| image | Core | image | Basic | Feature success telemetry for image preview | App key feature success data   |
| importantMessage_select | Core | User selects important message from priority context menu | Basic | Feature success telemetry for important message | App key feature success data   |
| importantMessageSend  | Core | User sends important message | Basic | Feature success telemetry for important message | App key feature success data   |
| install | Core | Install Event | Basic | App key feature success data | App key feature success data   |
| install | Core | Install | Basic | This telemetry is used to identify how many people are added to a team | App key feature success data   |
| installReferrer | Core | Record app install referrer parameters after first time install | Basic | Need to understand the path user has installed the app from.  Feature success telemetry. | App key feature success data   |
| inviteFreemium | Core | Taps the + button in Invite screen | Basic | Helps with feature discoverability and success metrices for freemium | App key feature success data   |
| inviteGuest | Core | Taps the + button in Invite screen | Basic | Helps with feature discoverability and success metrices for teams guests | App key feature success data   |
| joinTeam | Core | Join button pressed | Basic | Feature success and usage telemetry | App key feature success data   |
| Launch source eg. direct, link, appShortcut | Core | Launch directly or via link (record MAM/MDM telemetry on app launch to collect data for active users)| Basic | App engagement success metrics, Also success metrics for intune, MAM and MDM integration | App key feature success data   |
| leaveChat | Core | Confirm leave chat | Basic | Feature success telemetry for group chat | App Key feature success   |
| legacyChatLink | Core | User taps on link to legacy chat | Basic | Feature success telemetry for federated chats | App key feature success data   |
| likeAppDismiss | Core |     | Basic | App ratings are an important part of mobile app infrastructure and is tracked at various levels for app success. Success metrics for the app overall | App key feature success data   |
| likeAppNo | Core |     | Basic | App ratings are an important part of mobile app infrastructure and is tracked at various levels for app success. Success metrics for the app overall | App key feature success data   |
| likeAppYes | Core |     | Basic | App ratings are an important part of mobile app infrastructure and is tracked at various levels for app success. Success metrics for the app overall | App key feature success data   |
| likeMsg   | Core | Click on Like | Basic | Feature success metrics, drives content engagement and inturn overall app engagement | App key feature success data   |
| locationCard | Core | Click on location card | Basic | Feature successmetrics for location sharing | App key feature success data   |
| mapAppPicker | Core | Choose map app from map picker (TBD) | Basic | Feature successmetrics for location sharing | App key feature success data   |
| markAsRead | Core | Mark as read | Basic |     | App key feature success data   |
| markAsUnread | Core | Mark as unread | Basic |     | App key feature success data   |
| memberListLoadMore | Core | Scroll down to load more | Basic | Required to define basic feature success  metrices. |     |
| messageCopyMessage | Core | messageCopyMessage | Basic | Feature success metrics for copy message feature | App key feature success data   |
| messageDelete | Core | Message delete | Basic | Feature success metrics for delete message feature | App key feature success data   |
| messageEditMessage | Core | Edit message | Basic | Feature success metrics for edit message feature | App key feature success data   |
| messageForwardMessage | Core | User taps on Forward entry point from message context menu | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| messageLike/messageUnlike | Core | Message like/unlike | Basic | Feature success metrics for message reactions | App key feature success data   |
| messageMuteSender | Core | muteSender/unmuteSender | Basic | Feature success telemetry, see event description. | App key feature success data   |
| messagePriority_select | Core | User selects Message priority entry point | Basic | Feature success metrics for important or urgent messages | App key feature success data |
| messageSeeOriginal | Core | User reverts translated message back to original | Basic | Feature success metrics for message translation | App key feature success data   |
| messageShareMessage | Core | MessageShareMessage | Basic | Feature success metrics for share message | App key feature success data   |
| messageTranslate | Core | User translates a message | Basic | Feature success metrics for message translation | App key feature success data   |
| messageUnabletoEdit | Core | User unable to edit message | Basic | Feature success metrics for edit message feature | App key feature success data   |
| multipleAccounts | Core | No. of accounts for a user | Basic | Feature success metrics for MTMA (multiple tenant and multiple account) feature | App key feature success data   |
| multipleTenants | Core | No. of tenants per account | Basic | Feature success metrics for MTMA (multiple tenant and multiple account) feature | App key feature success data   |
| mute | Core | Mute chat | Basic  | Feature success and usage telemetry, see event description. | App key feature success data   |
| nameGroupChat | Core | Name group chat | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| nativeChatLink | Core | User taps on link to native chat | Basic | Feature success telemetry, see event description. | App key feature success data   |
| navActivity, navChat, navTeams, navMore, navOrg, navFiles, navSaved, nav+(Appname) | Core | Nav Tab clicked (or hamburger menu clicked - navMore) | Basic | Provides navigation information for each of the app. Important to get active user count for various modules | App Key feature success   |
| navTeams | Core | Tap **see all** | Basic | Feature success metrics for teams list | App key feature success data   |
| notNow | Core | User taps not now in reminder | Basic |     | App key feature success data   |
| notNowUpdate | Core | updateDefer | Basic |     |     |
| open | Core | Notification Settings tap | Basic | Lets us capture user engagement with the notification feature. | App key feature success data   |
| openContactCard_ReactionSummary | Core | Navigate to contact card from reaction summary page | Basic | Feature success metrics for people app (contact ard). | App key feature success data   |
| openModalityPicker | Core | X = ChatsAndChannels for chats and channels |     |     |     |
| openPhotoLibrary | Core | Click on photo library | Basic | How many total users open photo gallery. This with combination of image selection and send will give us overall information about the image picking experience and how many people tried to attach the image vs how many successfully attached vs abandoned  | App key feature success data   |
| openQuietDays | Core | Navigate to Quiet Days page | Basic | Feature success telemetry for quiet days | App key feature success data   |
| openQuietHours | Core | Navigate to Quiet Hours Page | Basic | Feature success telemetry for quiet hours | App key feature success data   |
| openReactionHoverBubble | Core | Press add reaction button on reaction summary page | Basic | Feature success telemetry for reactions | App key feature success data   |
| openReactionSummary | Core | Invoke reaction summary drawer | Basic | Feature success telemetry for reactions | App key feature success data   |
| photoLibraryPicker | Core | **Open photo library** tapped inside image picker | Basic | Feature success telemetry for gallery integration for image picking experience | App key feature success data   |
| provideFeedbackDismiss | Core |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| provideFeedbackNo | Core |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| provideFeedbackYes | Core |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| provideRatingDismiss | Core |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| provideRatingNo | Core |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| provideRatingYes | Core |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| quickSelectImagePicker | Core | quick select |     |     |     |
| quietHoursValues | Core | Capture Quiet Hours State on back button navigation | Basic | Feature success telemetry for quiet hours | App key feature success data   |
| quotedReplySent | Core | User sent reply message with context type | Basic | Feature success telemetry for quoted reply | App key feature success data   |
| reactAngry_CM | Core | React with angry from context menu | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactAngry_HB | Core | React with angry from hover bubble | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactHeart_CM | Core | React with heart from context menu | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactHeart_HB | Core | React with heart from hover bubble | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactLaugh_CM | Core | React with laugh from context menu | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactLaugh_HB | Core | React with laugh from hover bubble | Basic | Feature success telemetry for reactions  | App key feature success data   |
| reactLike_doubleTap  | Core | React with like from double tap | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactLike_HB | Core | React with like from hover bubble | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactSad_CM | Core | React with sad from context menu | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactSad_HB | Core | React with sad from hover bubble | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactSurprised_CM | Core | React with surprised from context menu | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactSurprised_HB | Core | React with surprised from hover bubble | Basic | Feature success telemetry for reactions | App key feature success data   |
| readReceipts | Core | User enabled feature | Basic | Feature success telemetry for read receipts | App key feature success data   |
| redeemInvite | Core | In app redemption | Basic | Feature success metrics for freemium invite | App key feature success data   |
| removeReplyObject | Core | User removed reply object from compose | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| removeUserConfirm | Core | UserÂ confirmed remove user dialog| Basic | Feature success metrics for quoted reply | App key feature success data   |
| removeUserContextMenu | Core | User removed partipipcant via context menu | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| removeUserSwipe | Core | User removed participant via swipe | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| replyChain | Core | New message button/textbox in reply chain (thread) | Basic | Feature success metrics for reply message experience in a channel | App key feature success data   |
| replyChannel | Core | Reply button in channels | Basic | Feature success metrics for reply message experience in a channel | App key feature success data   |
| replyNavigation | Core | User tapped on reply object to navigate to referenced post | Basic | Feature success metrics for quoted reply | App key feature success data   |
| replyViaMsgOptions | Core | User started reply via context menu | Basic | Feature success and discoverability metrics for quoted reply | App key feature success data   |
| replyViaSwipe | Core | User started reply via swipe | Basic | Feature success and discoverability metrics for quoted reply | App key feature success data   |
| requestJoinTeam  | Core | Request button pressed | Basic | Feature success and discoverability metrics for teams and channel | App key feature success data   |
| requestToJoinTeam | Core | Request to join team (public or private) | Basic | Feature success and discoverability metrics for teams and channel | App key feature success data   |
| requestToJoinTeamError | Core | Error with join request | Basic | Feature success metrics for teams and channel | App key feature success data   |
| returnToMessage | Core | User tapped **Return** button to navigate back to message | Basic | Feature success metrics for quoted reply | App key feature success data   |
| safeLink | Core | Link verified as safe | Basic | Feature success telemetry | App key feature success data   |
| selectDevice | Core | Selecting a particular device in displays app | Basic                                                | Feature success and usage telemetry, see event description. | App key feature success data   |
| selectGeneralSetting | Core | Go to general settings | Basic | Feature discoverability and success metrics | App key feature success data   |
| selectSettingOption | Core | Go to settings tab from hamburger menu | Basic | Feature discoverability and success metrics | App key feature success data   |
| selectTheme | Core | Enable dark theme | Basic | Direct feature success metrics for dark theme. | App key feature success data   |
| sendForward | Core | User confirms to send forward message from forward picker | Basic | Feature success metrics for forward message feature | App key feature success data   |
| sendImage | Core | Send image | Basic | Feature success metrics for image attachment | App key feature success data   |
| sendLocation | Core | Send location | Basic | Feature success metrics for location sharing experience | App key feature success data   |
| sendMsg | Core | Click on send in reply | NSD | Let us know the success of the main construct of post in teams | Activity success   |
| sendVoiceMessage | Core | Record button released | Basic | Feature success metrics for voice messages | App key feature success data   |
| settingsNavReadReceiptNotice | Core | User went to settings from feature notice | Basic | Feature success metrics for read receipts | App key feature success data   |
| shareHistory | Core | Share history picker tapped | Basic | Feature success metrics for adding users to group chat and share history feature | App key feature success data   |
| showBanner | Core | No. of times the **WiFi Connected, No Internet** banner appears | Optional |     |
| shownReadReceiptNotice | Core | User shown feature notice with settings options  | Basic | Feature discoverability and success metrics for read receipts | App key feature success data   |
| signIn | Core | <ul><li>User taps sign in on welcome page</li><li>Tap Sign In button</li></ul> | Basic | Feature success metrics for teams freemium | App key feature success data   |
| signUp | Core | Taps **Create a free account**/**Sign up for free** | Basic | Feature success metrics for teams freemium | App key feature success data   |
| skipVerificationForLink | Core | User chose to skip verification | Basic | Feature success metrics for ATP safe link | App key feature success data   |
| SMSSendMessage | Core | User sends SMS message | Basic | Feature success metrics for send SMS feature | App key feature success data   |
| startEditing | Core | Edit button pressed |     |     |     |
| StatusMsgCancel | Core | User cancels change to status message | Basic | Feature success metrics for add status message feature | App key feature success data   |
| StatusMsgExpiry | Core | User sets expiry time | Basic | Feature success metrics for add status message feature | App key feature success data   |
| StatusMsgSet | Core | User sets new status message | Basic | Feature success metrics for add status message feature | App key feature success data   |
| StatusPageViaContactCard | Core | User enters status compose experience via contact card | Basic | Feature success metrics for add status message feature | App key feature success data   |
| StatusPageViaHamburger | Core | User enters status compose experience via hamburger | Basic | Feature success metrics for add status message feature | App key feature success data   |
| table | Core | click on table | Basic | How many people tap on table in chat or channel conversation | App key feature success data   |
| takePhotoPicker | Core | **Take photo** tapped inside image picker | Basic | Feature success metrics for camera integration in image picking experience | App key feature success data   |
| teamNav | Core | View menu options for team |     |     |     |
| tenantSwitch | Core | On Switch Tenant | Basic | Feature success metrics for MTMA (multiple tenant and multiple account) feature | App key feature success data   |
| tenantSwitchUnsupportedError | Core | Tenant Unsupported Error (when user sees the error) | Basic | Feature success metrics for MTMA, provides telemetry around account/tenant switch errors | App key feature success data   |
| toggleChannelsInChat | Core | Turn feature on/off | Basic | Feature success metrics for unified chats and channel experience | App key feature success data   |
| translateFailed | Core | Translation failed (excluding offline) | Basic | Feature success metrics for message translation feature | App key feature success data   |
| unsafeLink | Core | Link was determined to be unsafe | Basic | Feature success metrics for ATP safe links | App key feature success data   |
| upgrade | Core | Taps the upgrade button in more menu | Basic | Feature success metrics for freemiums as this would provide information about number of successful conversations | App key feature success data   |
| urgentMessageSelect | Core | User selects urgent message from priority context menu | Basic | Feature success metrics for priority messages | App key feature success data   |
| urgentMessageSend | Core | User sends urgent message | Basic | Feature success metrics for priority messages | App key feature success data   |
| url | Core | url | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreview | Core | urlPreview | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreviewAdd | Core | URL preview add | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreviewOpen | Core | URL preview open | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreviewRemove | Core | URL preview removed | Basic | Feature success metrics for url preview | App key feature success data   |
| viewRequests | Core | View requests button pressed | Basic | Feature success metrics for join teams experience | App key feature success data   |
| chat | Core/MCM | <ul><li>New message button/textbox in chat</li><li>1:1 chat tapped on callHistory item</li><li>1:1 chat click from call List</li></ul> | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| disableCategory | Core/MCM | <ul><li>Disable a type of notification</li><li>Disable incoming call notifications</li></ul> | Basic | Required to get the feature success | App key feature success data   |
| channelNavTab | Core/Mobile platform | <ul><li>Clicks on Files tab in channel/Tabs are a critical feature for Teams and this will be needed to understand feature success and be ready to see if there are any issues in the way its being used </li><li>Connector card reply. Uses existing telemetry with app specific data</li></ul> | Basic/Optional | This is essential metrics for files tab as it provides the success and discoverability data for files in teams | App key feature success data   |
| channelSendMessage | Core/Mobile platform  | <ul><li>Send Channel Message</li><li>@ mention a bot in a compose box</li></ul> | NSD/Optional | As teams is a chat and collaboration product, this is a required success metrics for the product all up. Any dip in this metrics would be alarming | Activity success   |
| chatListNavConversations | Core/Mobile platform | chatListNavConversations | Basic | Feature success telemetry, see event description. | App key feature success data   |
| messageBookmarkMessage | Core/Mobile platform | <ul><li>messageBookmarkMessage/Connector card save. Uses existing telemetry with app specific data</li><li>Save a bot message</li></ul> | Optional |     | App key feature success data   |
| reactLike_CM | Core/Mobile platform | React with like from context menu / Like a bot message | Basic/Optional | Feature success and usage telemetry, see event description. | App key feature success data   |
| replySendMessage | Core/Mobile platform | Send Reply | NSD/Basic|     | <ul><li>Activity success</li><li>App key feature success data</li></ul>   |

### Files

| Action_Scenario | Team Owner | Description | Type | How the event is used | Basic Subtype |
|-----------------|------------|-------------|------|-----------------------|---------------|
| downloadFile | Files | <ul><li>Helps to check if user was able to initiate download operation</li><li>Helps to track if user can download file successfully</li></ul> | Basic | <ul><li>Helps to check if user was able to initiate download operation</li><li>Helps to track if user can download file successfully</li></ul> | App key feature success data   |
| fileThumbnailPreviewDownloaded | Files | Helps to identify is thumbnail was rendered successfully for a file | Basic | Helps to identify is thumbnail was rendered successfully for a file | App key feature success data   |
| fileThumbnailPreviewFromCache | Files | <ul><li>Captures if thumbnail is show from cache successfully</li><li>Helps to identify is thumbnail was rendered successfully for a file</li></ul> | Basic | <ul><li>Captures if thumbnail is show from cache successfully</li><li>Helps to identify is thumbnail was rendered successfully for a file</li></ul> | App key feature success data   |
| fileThumbnailPreviewNotAvailable | Files | Helps to identify is thumbnail was rendered successfully for a file | Basic | Helps to identify is thumbnail was rendered successfully for a file | App key feature success data   |
| openFile | Files | <ul><li>Helps to identify if user was able to open file in the chat successfully</li><li>Helps to identify if user was able to open file from files listing</li><li>Helps to check if user can open files from OneDrive list</li><li>Helps to identify if user can open files from channel list</li><li>Helps tracking if user can open file from group chats</li><li>Helps tracking if user can successfully open from files app</li><li>Helps to track if user can open from message file chiclet successfully</li><li>Helps to track if user can open files from recent list successfully</li><li>Helps to track if user can open file from file list successfully</li><li>Helps to track if user can open file from messages file chiclet</li><li>Helps to track if files can be opened successfully from file list</li></ul> | Basic | <ul><li>Helps to identify if user was able to open file in the chat successfully</li><li>Helps to identify if user was able to open file from files listing</li><li>Helps to check if user can open files from OneDrive list</li><li>Helps to identify if user can open files from channel list</li><li>Helps tracking if user can open file from group chats</li><li>Helps tracking if user can successfully open from files app</li><li>Helps to track if user can open from message file chiclet successfully</li><li>Helps to track if user can open files from recent list successfully</li><li>Helps to track if user can open file from file list successfully</li><li>Helps to track if user can open file from messages file chiclet</li><li>Helps to track if files can be opened successfully from file list</li></ul> | App key feature success data   |
| openFileInApp | Files | Helps to identify is user opted to open files outside of Teams vs inside of teams | Basic | Helps to identify is user opted to open files outside of Teams vs inside of teams | App key feature success data   |
| uploadSelectedFile | Files | <ul><li>Tracks if user can upload files in channel successfully</li><li>Tracks if user can upload files in chat successfully</li><li>Tracks if user can upload files in the reply window</li><li>Tracks if user can upload files successfully in group chat</li><li>Tracking usage of core scenario</li><li>Tracks the start of upload scenario in channel</li><li>Tracks the start of upload scenario in chat</li><li>Tracks the start of end of upload scenario in channel</li><li>Track if user can upload file into files tab successfully</li><li>Helps to identify is user acted on the prompt during file upload</li><li>Helps to identify if user can upload selected file successfully</li></ul> | Basic/Full | <ul><li>Tracks if user can upload files in channel successfully</li><li>Tracks if user can upload files in chat successfully</li><li>Tracks if user can upload files in the reply window</li><li>Tracks if user can upload files successfully in group chat</li><li>Tracking usage of core scenario</li><li>Tracks the start of upload scenario in channel</li><li>Tracks the start of upload scenario in chat</li><li>Tracks the start of end of upload scenario in channel</li><li>Track if user can upload file into files tab successfully</li><li>Helps to identify is user acted on the prompt during file upload</li><li>Helps to identify if user can upload selected file successfully</li></ul> | App key feature success data   |
| uploadSelectFile | Files | <ul><li>Tracks if the user can select file successfully</li><li>Tracks if the user can select upload file button successfully</li></ul> | Basic | <ul><li>Tracks if the user can select file successfully</li><li>Tracks if the user can select upload file button successfully</li></ul> | App key feature success data   |
| files | Files |     |     |     |     |
| navFiles | Files |     |     |     |     |
| navFilesTab | Files |     |     |     |     |
| navPersonalFiles | Files |     |     |     |     |

### MCM

| Action_Scenario | Team Owner | Description | Type | How the event is used | Basic Subtype |
|-----------------|------------|-------------|------|-----------------------|---------------|
| navCallingSettings | MCM |     |     |     |     |
| navVoicemail | MCM |     |     |     |     |
| userJoinedViaShareLink | MCM | User joined a meeting from a link |     |     |     |
| backFromCallMePSTN | MCM |     |     |     |     |
| callMePSTNConnected | MCM | **Call me** is successful |     |     |     |
| callOrMeetUpAddParticipantsDone | MCM | User finalizes their participant addition |     |     |     |
| callOrMeetUpAutoReconnect | MCM | Poor network causes users device to go into Autoreconnect mode |     |     |     |
| callOrMeetUpMuteParticipant | MCM | User mutes a remote participant |     |     |     |
| callsTabNewCall | MCM |     |     |     |     |
| callTransfer | MCM |     |     |     |     |
| callInProgressShown | MCM |     |     |     |     |
| dialIn | MCM | User chooses to Dial in into a meeting (various locations) |     |     |     |
| teamsDeviceCallResumed | MCM |     |     |     |     |
| endPSTNCallSelected | MCM | User ends a PSTN and a Content call |     |     |     |
| endPSTNCallShown | MCM | User is prompted to end a PSTN/Content call |     |     |     |
| groupCallJoin | MCM |     |     |     |     |
| joinViaCode | MCM |     |     |     |     |
| liveEventJoin | MCM | User joins a live event |     |     |     |
| meetingJoinNowWithCallMe | MCM | User joins a meeting with **Call me** |     |     |     |
| meetingJoinNowWithPSTN | MCM | User joins a meeting with Dial in |     |     |     |
| notificationNavPreCall | MCM |     |     |     |     |
| preJoinDenied | MCM | User unable to join a meeting |     |     |     |
| preJoinDialInCancel | MCM | User cancels **Dial in** request on prejoin |     |     |     |
| preJoinDialInCall | MCM | User confirms **DIal in** request on prejoin |     |     |     |
| preJoinDialOutCancel | MCM | User cancels **Call me back** request on prejoin |     |     |     |
| preJoinDialOutCall | MCM | User confirms **Call me back** request on prejoin |     |     |     |
| addUserAsContact | MCM |     |     |     |     |
| shortCircuitContactCount | MCM |     |     |     |     |
| structuredMeetingsBannerDismiss | MCM | User dismisses banner that informs them about their meeting role |     |     |     |
| activityChatClicked | MCM | Non-live chat tapped in Activity tab or split view shown | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| activityLiveChatClicked | MCM | Chat clicked from live meeting on the Activity tab | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| activityLiveDetailsClicked | MCM | Details clicked from live meeting on the Activity tab | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| admitAll | MCM | Number of times user clicks on admit all button from lobby section | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| admitParticipant | MCM | Number of times user admits someone into meeting from roster | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingJoin | MCM | User clicked **Join meeting** on anonymous join provide name page OR tapped **OK** in the name dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingJoinWelcome | MCM | Clicked on **Join as guest** on anonymous join meeting landing page | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingPostMeetingChat | MCM | Number of user views chat from call end screen | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingPostMeetingRejoin | MCM | Number of times anonymous user tries to rejoin meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingSignIn | MCM | Number of times user navigated to sign-in from name input screen | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingSignInWelcome | MCM | Clicked on **Sign in and join** on anonymous join meeting landing page | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingToggleMuted | MCM | Number of times mute toggle button was clicked | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingToggleVideo | MCM | Number of times video toggle button was clicked | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| audioOnlyLowBatteryBanner | MCM | User taps **Audio only** for low battery banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| audioOnlyPoorNetworkBanner | MCM | User taps **Video off** for poor connection banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| audioUserDoubleTap | MCM | Double tap on an audio participant | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| autoReconnectCallmebackCallDrop | MCM | Number of times user clicked on Callmeback button at Call end screen | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| autoReconnectDialIn | MCM | User clicks the Dial in button on the reconnect UFD/Number of times user clicked on DialIn button while reconnect is happening | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| autoReconnectDialInonCallDrop | MCM | User clicks the Dial in button on the call disconnected UFD | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| autoReconnectDialOut | MCM | User clicks the **Call me back** button on the reconnect UFD | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| autoReconnectRejoinonCallDrop | MCM | Number of times user clicked on Rejoin/Redial button at Call end screen | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| backToPhotoShare | MCM | back to camera | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| backToStageFromWhiteboard | MCM | Going back to call screen from whiteboard | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| backToWhiteboardFromStage | MCM | Going to whiteboard from call screen | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| blockAnonymous | MCM | <ul><li>User enables calling setting to block calls without caller id from settings</li><li>User disables calling setting to block calls without caller id from settings</li><li>User enables calling setting to block calls without caller id from action sheet</li><li>User disables calling setting to block calls without caller id from action sheet</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| blockCaller | MCM | <ul><li>Block number and contact from the new iOS calls action sheet</li><li>Block contact and number from the contact card</li><li>Block numbers from settings | Basic | Used to track feature success</li><li>failure of a feature and customer engagement</li></ul> | App key feature success data   |
| BYOELiveEventJoin | MCM | BYOE live event is joined by user | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| calendarLiveChatClicked | MCM | Chat from live meeting on the Schedule tab | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| calendarMeetingJoin | MCM | Meeting Join button tapped from Calendar | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| calendarUpcomingChatClicked | MCM | Chat from upcoming meeting on the Schedule tab | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callAccepted | MCM | Call accepted | | Used to track feature success/failure of a feature and customer engagement |     |
| callAcceptedSFB | MCM | Call accepted  | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callAppPreference | MCM | Preferred Calling App is selected | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callControlsManualDismiss | MCM | Call controls are dismissed manually (user action) | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callControlsManualInvoke | MCM | Call controls are invoked manually (user action) | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callHistoryItemExpand | MCM | Call History Item expanded | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callHistoryTab | MCM | CallHistoryTab selected in Calls | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpAddParticipants | MCM | <ul><li>Add participant button tapped on 1:1 call screen</li><li>Select Person (VoIP) in Add participants</li><li>Select PSTN in Add participants</li><li>Add people in live Private meeting</li><li>Select PSTN in live Private meeting</li><li>Select Company contact in live Private Meeting</li><li>Select Device contact in live Private Meeting</li><li>Add Participants Done in Private Live Meeting</li><li>Add people in live Channel Meeting</li><li>Select PSTN in Live Channel Meeting</li><li>Select Team Member in live channel meeting</li><li>Select Device contact in live channel meeting</li><li>Add Participants Done in live channel Meeting</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpAddRoom | MCM | <ul><li>User taps Add room in roster</li><li>User selects a search result in add room</li><li>User taps Dismiss for Nearby</li><li>User taps Enable BT orLocation for Nearby</li><li>User selects a nearby room result in add room</li><li>User selects a suggested room result in add room</li><li>User taps Done in add room</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpAudioOffSwitch | MCM | Flip Audio off button while in companion join mode in live call or meetup | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpCallAccepted | MCM | <ul><li>Call accepted</li><li>PSTN Call Accepted</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpCallEnded | MCM | <ul><li>End call button tapped</li><li>Call ended button tapped while in callOrMeetupLive</li><li>Call ended button tapped while in lockScreen</li><li>Call ended button tapped while in notification</li><li>Call ended button tapped while in inApp</li><li>Call ended button tapped while in callKit</li><li>Call Ended button for PSTN tapped</li></ul> | No data collected/Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpChatWithParticipants | MCM | Chat toggle while in live meeting/call | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpDeviceAudioSwitch | MCM | <ul><li>Switch audio source to speaker</li><li>Switch audio source to device</li><li>Switch audio source to bluetooth</li><li>Switch audio source to audio off</li><li>Switch speaker while in live meeting/call</li><li>Switch speaker to Audio off while in live meeting/call</li><li>Flip Audio off button while in companion join mode in live call or meetup</li><li>Device Audio Switch while in PSTN</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpEnterDriveMode | MCM | Switches manually to drive mode from ... menu | No data collected | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetupExitDriveMode | MCM | Exit drive mode button tapped | No data collected | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpHold | MCM | <ul><li>Hold button tapped while in live meeting/call</li><li>Call Hold in PSTN</li></ul> | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpIncomingVideoSwitch | MCM | Turn off IncomingVideo while in live meeting/call | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpInvitedParticipants | MCM | <ul><li>Clicked **See all** at the bottom of an **Others invited** participant group during private live meeting</li><li>Clicked **See all** at the bottom of an **Others invited** participant group during live channel meeting</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpJoinedParticipants | MCM | <ul><li>Clicked **See all** at the bottom of an **In the meeting** participant group during private live meeting</li><li>Clicked **See all** at the bottom of an **In the meeting** participant group during live channel meeting</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpLobbyParticipants | MCM | <ul><li>Clicked **See all** at the bottom of a **Lobby** participant group during private live meeting</li><li>Clicked **See all** at the bottom of a **Lobby** participant group during live channel meeting</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpMicrophoneSwitch | MCM | <ul><li>Switch Microphone on</li><li>Switch Microphone off</li><li>Microphone button tapped while in live meeting/call</li><li>Microphone switch while in PSTN</li></ul> | No data collected/Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpMuteParticipants | MCM | Mute all participants while in live meeting/call | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpParticipants | MCM | Participants toggle while in live meeting/call | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpRemoteMuteUFD | MCM | You have been muted UFD | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpResume | MCM | <ul><li>Resume button tapped while in live meeting/call</li><li>Call Resume in PSTN</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpSearchParticipants | MCM | <ul><li>Clicked **Search** in meeting participants during private live meeting </li><li>Clicked **Search** after viewing the **Lobby** participant group during private meeting</li><li>Clicked **Search** after viewing the **In the meeting** participant group during private meeting</li><li>Clicked **Search** after viewing the **Others invited** participant group during private meeting</li><li>Clicked **Search** in meeting participants during a live channel meeting</li><li>Clicked **Search** after viewing the **Lobby** participant group during a live channel meeting</li><li>Clicked **Search** after viewing the **In the meeting** participant group during a live channel meeting</li><li>Clicked **Search** after viewing the **Others invited** participant group during a live channel meeting</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpVideoSwitch | MCM | <ul><li>Switch Video on</li><li>Switch Video off</li><li>Video button tapped while in live meeting/call</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callPark | MCM | <ul><li>User taps **Park Call** in … menu</li><li>User taps **Retrieve** button</li><li>User taps **Pickup** in retrieve dialog</li><li>User taps **Cancel** in retrieve dialog</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callPreferenceSetting | MCM | Call Preference App Setting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| callVoicemailTab | MCM | VoicemailTab selected in Calls | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| cameraPermissionCancel | MCM | User taps cancel on camera permission dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| cameraPermissionGoToSettings | MCM | User navigates to settings from camera permissions dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| cancelFileShare | MCM | User clicks **Cancel** on the confirmation dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| cancelFileUpload | MCM | User clicks **X** on the upload dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| chatCancelAudioCall | MCM | Cancel a group audio call - Confirm dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| chatCancelVideoCall | MCM | Cancel a group video call - Confirm dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| chatStartAudioCall | MCM | <ul><li>1:1 audio call button tapped</li><li>Taps audio button on search result</li><li>Taps Start Call button on right</li><li>1:1 audio call tapped from callHistory item</li><li>1:1 audio call tapped from voicemail item</li><li>Place a group audio call - Confirm dialog</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| chatStartAudioCallOnBehalfOf | MCM | Delegate  starts call from action sheet as Boss | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| chatStartAudioCallOnBehalfOfMyself | MCM | Delegate  starts call from action sheet as Myself| Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| chatStartAudioCallSFB | MCM | 1:1 audio call button tapped | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| chatStartVideoCall | MCM | <ul><li>1:1 video call button tapped</li><li>Taps video button on search result</li><li>1:1 video call tapped from callHistory item</li><li>Place a group video call - Confirm dialog</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| chatStartVideoCallSFB | MCM | 1:1 video call button tapped | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| closeLobbyBanner | MCM | Number of times user closes lobby toast using its close button | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| companionBannerJoin | MCM | Click join on the top-level banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| companionDismiss | MCM | Dismiss Companion Banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| companionDismissProximity | MCM | Dismiss Companion Banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| companionJoin | MCM | Join as companion option is clicked on the sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| companionJoinProximity | MCM | Joined through companion banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| confirmAudioOn | MCM | User confirms that they want an audio on | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| confirmFileShare | MCM | User clicks **Share** on the confirmation dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| consultTransfer | MCM | <ul><li>Taps **Transfer** > **Consult first**</li><li>Transfer target set to Person</li><li>Transfer target set to Phone Number</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| consultTransferCall | MCM | <ul><li>Initiate consult call</li><li>Confirm transfer dialog - confirm</li><li>Confirm transfer dialog - cancel</li><li>Banner transfer button</li><li>Banner resume button</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| consultTransferChat | MCM | <ul><li>Initiate consult chat</li><li>Confirm transfer dialog - confirm</li><li>Confirm transfer dialog - cancel<.li><li>Banner transfer button / Banner resume button</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| contactOrganizer | MCM | Clicked **Contact organizer** | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| crossCloudDialogCancel | MCM | User clicks **Cancel** on a cross-cloud dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| crossCloudDialogJoin | MCM | User clicks **Join as guest** for a cross-cloud dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| deleteVoicemail | MCM | Delete voicemail item tapped | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| demotedToAttendee | MCM | User demotes a presenter - **Change** button in the dialog box | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| denyParticipant | MCM | Number of times user denies someone entry from the roster | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| detailsTabClicked | MCM | **Details** tab is clicked on the meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialInBadNetworkBanner | MCM | User taps **Dial in** for poor connection banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialInBadNetworkBannerCancel | MCM | User cancels the **Dial in** on the native dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialInBadNetworkBannerConfirm | MCM | User confirms the **Dial in** on the native dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialInCall | MCM | User clicks **Call** on the **Dial in** pop-up | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialInCancel | MCM | User clicks **Cancel** on the **Dial in** pop-up | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialOutCall | MCM | <ul><li>Join in Drive mode</li><li>User clicks **Call** on the **Call me back** pop-up</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialOutCallAAD | MCM | User clicks any number from **My numbers** in action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialOutCallRecent | MCM | User clicks any number from previous recent numbers in the action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialOutCancel | MCM | User clicks **Cancel** on the **Call me back** pop-up | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialOutDialog | MCM | User clicks **New number** in action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dialOutFailRetry | MCM | User clicks retry from failure banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| DialPad | MCM | DialPad button tapped from call List | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| Dismiss_earlycancelledCQF | MCM | User dismissed the CQF early cancelled call form | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| Dismiss_ratemycallCQF | MCM | User Dismisses the CQF rate my call form | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| Dismiss_ratemyliveeventCQF | MCM | User Dismisses the CQF rate my live event form | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dismissBadNetworkBanner | MCM | User taps **Dismiss** for poor connection banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dismissStartRecording | MCM | Dismiss error when starting recording | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dismissStopRecording | MCM | Dismiss error when stopping recording | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dismissUseWifiForVideoBanner | MCM | <ul><li>User dismisses banner that tells the user that remote participant video is blocked and users has to swith to Wifi to see it.</li><li>User dismisses banner that tells the user that users has to swith to Wifi to share video</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| dtmfPSTNCall | MCM | DTMF button on DialPad tapped | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| editMeetingResponse | MCM | Edit meeting response from meeting detail page | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| emergencyCall | MCM | Emergency Call Placed Calling Plan | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| emergencyCallDirectRouting | MCM | Emergency Call Placed Direct Routing | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| emergencyCallLocationPolicyBased | MCM | DialEmergency using DialPad | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| emergencycallSecurityDeskNotify | MCM | Emergency Call Placed, security Desk informed | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| enabled/disabled | MCM | Calling Permissions / Contact Permissions (Android only) |     | Used to track feature success/failure of a feature and customer engagement |     |
| endFileShare | MCM | User clicks **Go back** on file sharing dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| endPhotoShare | MCM | X out from Photo share | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| endVideoShare | MCM | X out from Video share | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| expand/collapse | MCM | Device contacts / Company Contacts section | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| fillFrameVideo | MCM | Fill frame from action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| fitToFrameVideo | MCM | Fit to frame from action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| flipCamera | MCM | flip camera | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| handoffComplete | MCM | Meeting/call got handed off on this device | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| handoffJoin | MCM | Meeting hand-off option is clicked on the action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| hardwareAudioOff | MCM | Turn audio off through the hardware buttons | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| hardwareAudioOn | MCM | Turn audio on through the hardware buttons | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| immediateCallForward | MCM | <ul><li>Immediate call forward target is set</li><li>Enable immediate call forwarding (Calls ring me is disabled)</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| inCallDialOut | MCM | User clicks the **Call me back** button from in-call more options | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| initiatePhotoShare | MCM | initiate photo share | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| initiateVideoShare | MCM | initiate video share | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| invisionWhiteboardClicked | MCM | <ul><li>Invision whiteboard is clicked on channel files tab</li><li>Invision whiteboard is clicked on meeting chat files tab</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| joinFromDeeplinkInTeams | MCM | User joined through a deeplink from within the Teams app | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| joinFromDeeplinkOutsideTeams | MCM | User joined through a deeplink from outside of Teams app | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| joinFromJoinLauncher | MCM | User joined from a Join Launcher | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| joinFromNudge | MCM | User joined from nudge | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| joinFromStore | MCM | User joined after downloading the app from the app store | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| liveCaptions | MCM | User turns on live captions / User turns off live captions | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| liveEventAdditonalLink | MCM | Additional link is clicked | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| liveEventInfo | MCM | Info button is clicked | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| liveEventLeave | MCM | Leave button is pressed | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| liveEventPresenterJoin | MCM | Live event is joined by presenter | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| liveEventPresenterJoinAsAttendee | MCM | Live event presenter joined as attendee | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| liveEventQnA | MCM | Q&A icon is clicked | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| liveEventYammer | MCM | Yammer icon is clicked | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| liveMeetingPushNotificationClicked  | MCM | Push notification clicked | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| liveMeetingToastClicked | MCM | In-app toast clicked | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| lobbyPickAudio | MCM | Number of times user switches audio output from lobby | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| lobbyToggleMuted | MCM | Number of times user turned mic on/off from lobby | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data  |
| lobbyToggleVideo | MCM | Number of times user turned video on/off from lobby | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| manageBlockedNumbers | MCM | Access blocked numbers through Settings | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| maskCallerId | MCM | <ul><li>User enables calling setting to mask caller id</li><li>user disables calling setting to mask caller id</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingDetailChatWithParticipants | MCM | Chat with participants from Meeting detail page | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingDetailDeleteMeetingforSelf | MCM | Delete Meeting from Meeting Detail Page for yourself | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingDetailJoin | MCM | Meeting Join button tapped from meeting detail page | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingDetailParticipants | MCM | See all participants from Meeting detail page | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingDetailSearchParticipants | MCM | Clicked **Search** in meeting participants on meeting schedule | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingJoinLeave | MCM | Leave tapped -> X is tapped after Join button is tapped | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingJoinNow | MCM | Join now for VOIP tapped | NSD |     |     |
| meetingLeaveChat | MCM | Leave chat | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingMuteChat | MCM | Mute chat | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingNotesCreatedInChatLink | MCM | <ul><li>User clicks on the **Meeting notes created** chicklet in private meeting chat</li><li>User clicks on the **Meeting notes created** chicklet in channel meeting chat</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingNotesMentionCharLink | MCM | User clicks on the @mention link in private meeting chat | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingNotesMentionChatLink | MCM | User clicks on the @mention link in channel meeting chat | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingNotesTabEntryPoint | MCM | <ul><li>User clicks on Meeting notes tab in private meeting</li><li>User clicks on Meeting notes tab in a channel</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingNotificationSettingsAccepted | MCM | Notification settings was changed to Accepted only | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingNotificationSettingsAll | MCM | Notification settings was changed to All | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingNotificationSettingsNone | MCM | Notification settings was changed to None | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingSeeParticipantsChatDetails | MCM | See all participants | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingUserAnonB2B | MCM | Anonymous B2B joined the meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingUserAnonB2C | MCM | Anonymous B2C joined the meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingUserDialIn | MCM | PSTN (Dial in) user joined the meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingUserDialOut | MCM | PSTN Call me back user joined the meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingUserFederated | MCM | Federated user joined the meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingUserFreemium | MCM | Freemium user joined the meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingUserGuest | MCM | Guest user joined the meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| meetingUserTenant | MCM | In-tenant user joined the meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| messageScheduledMeeting | MCM | Meeting object in channel tapped (Not only scheduled ones) | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| micPermissionCancel | MCM | User taps cancel on mic permission dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| micPermissionGoToSettings | MCM | User navigates to settings from mic permissions dialog | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| MicrosoftWhiteboardClicked | MCM | <ul><li>Microsoft whiteboard is clicked on channel files tab</li><li>Microsoft whiteboard is clicked on meeting chat files tab</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| multiCallEndFromUFD | MCM | Number of times user ends the call on hold in multi call scenario | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| multiCallResumeFromUFD | MCM | Number of times user clicks to resume a call from hold | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| multiCallSwitch | MCM | Number of times user clicks to switch the call and list of calls on hold shows up | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| muteOnWhiteboard | MCM | User mutes/unmutes on whiteboard screen | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| muteParticipant | MCM | Mute participant (move to the action sheet) | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| navCalls | MCM | Calls Tab Tapped | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| navMeetings | MCM | Calendar tab tapped | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| navPhotoTab | MCM | photo tab | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| navVideoTab | MCM | video tab | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| newCall | MCM | Taps new call button | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| newCallDialPad | MCM | Taps Dialpad button on tab | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| newCallPeople | MCM | Taps People button on tab | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| openInStream | MCM | Open video in Stream | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| openSettingsSetUpInstructions | MCM | Open **Settings** from instructions| Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pauseVoicemail | MCM | Pause tapped on voicemail item | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pickGalleryPhoto | MCM | pick photo from gallery | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pickParticipantChatDetails | MCM | Pick a user from the list | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pickRecentPhoto | MCM | chooses recent image to share | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pinSelf | MCM | Pin myself from action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pinUser | MCM | Pin user from action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| play | MCM | Play the recording | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| playVoicemail | MCM | Play tapped on voicemail item | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pptNextSlide| MCM | <ul><li>Next slide as a presenter</li><li>Next slide in private viewing</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pptPreviousSlide | MCM | <ul><li>Previous slide as a presenter</li><li>Previous slide in private viewing</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pptReturnToPresenter | MCM | Go to the **Live** slide (the one that the presenter and everyone else is on) | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pptStopPresenting | MCM | Stop presenting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| pptTakeControl | MCM | Take control | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| preJoinAddRoom | MCM | <ul><li>User clicks the **Add a room** button in pre-join dropdown</li><li>User clicks **Join** in the **Add a room** scenario</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| preJoinAudioOff | MCM | User clicks the **Audio off** button in pre-join dropdown | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| preJoinAutoAddRoom | MCM | User tapped **Join now** when room is nearby | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| preJoinBack | MCM | Back/Close button tapped | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| preJoinDeviceAudio | MCM | User tapped **Join with device audio** from dropdown | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| preJoinDialIn | MCM | User clicks the Dial in button in pre-join dropdown | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| preJoinDialOut | MCM | User clicks the **Call me back** button in pre-join dropdown | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| preJoinPSTNOptions | MCM | User clicks dropdown for other join options | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| privateMeetingJoin | MCM | Meeting Join button tapped from Private meeting chat | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| promotedToPresenter | MCM | User promotes an attendee - **Change** button in the dialog box | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| proximityPermissionDismissed | MCM | Permission banner is dismissed | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| proximityPermissionGranted | MCM | Permission is given on the pop-up | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| proximityPermissionViewed | MCM | Permission bunner is tapped | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| quickStartLiveEventJoin | MCM | Quick start live event is joined by user | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| runningLate | MCM | I am running late | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| scheduledMeetingJoin | MCM | Meeting Join button tapped from scheduled meeting object | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| searchContacts | MCM | Search from Call List | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| selection | MCM | <ul><li>Device contact selected</li><li>Company contact selected</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| selectMeetingChicklet | MCM | meeting |     | Used to track feature success/failure of a feature and customer engagement |     |
| selfLongPress | MCM | Long press on myself | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| Send_earlycancelledCQF | MCM | User Submits feedback on CQF early cancelled call form | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| Send_ratemycallCQF | MCM | User Submits feedback on CQF rate my call form | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| Send_ratemyliveeventCQF | MCM | User Submits feedback on CQF rate my live event form | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| Setting/Dismiss | MCM | Device contacts setting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| sharePPTFromChannels | MCM | User clicks **Teams and Channels** | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| sharePPTFromOneDrive | MCM | User clicks **OneDrive** | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| shareRecording | MCM | Share recording | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| shareScreen | MCM | <ul><li>Start Screen Share</li><li>Stop Screen Share</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| shareTray | MCM | User clicks on **Share…** in the action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| simultaneousCallForward | MCM | <ul><li>Simultaneous call forward target is set</li><li>Enable simultaneous call forwarding (Calls ring me is enabled & Also ring is set)</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| startPresentPhoto | MCM | start presenting photo | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| startPresentVideo | MCM | Start presenting video | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| startPSTNCall | MCM | <ul><li>PSTN Result in Global Search (People)</li><li>PSTN call placed from Device contactCard</li><li>PSTN Call placed from callList</li><li>DialPSTN Number using DialPad</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| startRecording | MCM | Start recording | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| startVoicemailCall | MCM | Change Voicemail Greeting tapped | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| stopMeetingButton | MCM | Number of times user leaves the lobby without being admitted into the meeting | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| stopPresentPhoto | MCM | stop presenting photo | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| stopPresentVideo | MCM | Stop presenting video | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| stopRecording | MCM | Stop recording | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| stuckOnConnectingDialInSelected | MCM | User tapped Dial in on the drawer | Basic | Used to track feature success/failure of a feature and customer engagement |     |
| stuckOnConnectingRetrySelected | MCM | User tapped retry on the drawer | Basic | Used to track feature success/failure of a feature and customer engagement |     |
| stuckOnConnectingShownDismissed | MCM | User dismissed the drawer | Basic | Used to track feature success/failure of a feature and customer engagement |     |
| takePhoto | MCM | take a photo | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| toast | MCM | In-app toast clicked | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| transferNow | MCM | <ul><li>Taps Transfer > Transfer now</li><li>Transfer target set to Person</li><li>Transfer target set to Phone Number</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| unansweredCallForward | MCM | <ul><li>Unanswered call forward target is set</li><li>Enable unanswered call forwarding (Calls ring me is enabled and If unanswered is enabled)</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| unblockCaller | MCM | <ul><li>Unblock contact/number from action sheet</li><li>Unblock contact/number from contact card</li><li>Unblock number from settings</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| unpinSelf | MCM | Unpin user from action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| unpinUser | MCM | Unpin user from action sheet | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| updatePlaybackSpeedVoicemail | MCM | Voicemail playback speed value changed | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| uploadFile | MCM | User clicks **Upload from device** | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| userLongPress | MCM | Long press on a participant | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| useWifiForAudioDialog | MCM | User clicks ok while system prompts that while Admin has blocked audio and video calls on cellular | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| useWifiForVideoDialog | MCM | <ul><li>User clicks ok while system prompts that while Admin has blocked video calls on cellular</li><li>User trying to enable video in meeting while Admin has blocked it on cellular</li><li>User clicks ok while system prompts that while Admin has blocked video in meetings on cellular</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| videoUserDoubleTap | MCM | Double tap on a video participant | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| viewContactCard | MCM | <ul><li>ContactCard tapped from callHistory item</li><li>ContactCard tapped from voicemail item</li><li>ContactCard click from call list</li></ul> | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| viewLobbyFromBanner | MCM | Number of times user clicks on view lobby from notification banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| voiceDataCollectionOptOut | MCM | User opts-out of the recording from mobile by clicking the banner | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| Voicemail - No AS Assigned | MCM | Speaker tapped on voicemail item | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| whiteboardUsed | MCM | User annotates on whiteboard (any action on the webview) | Basic | Used to track feature success/failure of a feature and customer engagement | App key feature success data   |
| activityTabClicked | MCM/Feeds | <ul><li>Activity tab shown</li><li>Captures activity tab event</li></ul> | Basic | Helps to track if user came back to activity tab | App key feature success data   |
| fileSelected | MCM/Files | <ul><li>User picks one of PowerPoint presentations</li><li>Tracks if the user can select file successfully</li></ul> | Basic | Tracks if the user can select file successfully | App key feature success data   |
| shareFile | MCM/Files | <ul><li>User clicks **Share file**</li><li>Helps to check if user was able to initiate share file operation</li><li>Helps to track if user can share file successfully</li></ul> | Basic | <ul><li>Helps to check if user was able to initiate share file operation</li><li>Helps to track if user can share file successfully</li></ul> | App key feature success data   |
| joinMeeting | MCM/Mobile calendar | <ul><li>Join the meeting through Dial in</li><li>Join the meeting through Call me back</li><li>Join the meeting content only</li><li>Click on meeting join button from agenda view</li></ul> | Basic | Feature success and failure detection of joining meetings from calendar | App key feature success data   |
| viewMeetingSeries | MCM/Mobile calendar  | <ul><li>Switch from instance to series meeting detail page</li><li>Click on view series from the meeting details page</li><li> | Basic | To log succesful rendering of meeting series | Z   |

### Mobile platform

| Action_Scenario | Team Owner | Description | Type | How the event is used | Basic Subtype |
|-----------------|------------|-------------|------|-----------------------|---------------|
| navDynamics365  | Mobile Platform |        |      |                       |               |
| navNotes        | Mobile Platform |        |      |                       |               |
| navOrganization | Mobile Platform |        |      |                       |               |
| navOrgChart     | Mobile Platform |        |      |                       |               |
| navTasks        | Mobile Platform |        |      |                       |               |
| navWiki         | Mobile Platform |        |      |                       |               |
| oneNote         | Mobile Platform |        |      |                       |               |
| addToList       | Mobile Platform |        |      |                       |               |
| actionComposeMenu | Mobile platform | <ul><li>Create message extension usage</li><li>Action ME usage</li></ul> | Optional |     |     |
| Android : null | Mobile platform | Mute or unmute a bot chat. This is enhancing existing telemetry around chats and is only adding app information. | Optional |     |     |
| blockChat | Mobile platform | Block a bot chat.This is enhancing existing telemetry around chats and is only adding app information. | Optional     |     |     |
| botClickCardAction | Mobile platform | Connector card usage | Optional |     |     |
| CardView - No AS assigned | Mobile platform | Card view and card rendering. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side  | Basic | Teams and channels are essential construct of teams. This item is required to measure error with joining a team | App key feature success data   |
| chicletExpand | Mobile platform | <ul><li>Understand how users preview cards on mobile</li><li>Understand the preview closure behavior | Optional |     |     |
| composeSearchResult | Mobile platform | <ul><li>Message extension result selection - helpful to understand the app search result relevance</li><li>Enhances message send telemetry with app data</li></ul> | Optional/Basic  |     | App key feature success data   |
| composeSelectExtension | Mobile platform | tap on a ME app | Basic |     | Teams setup and inventory data   |
| composeSendMessage | Mobile platform | Enhances message send telemetry with app data | Basic |     | App key feature success data   |
| createComposeExtension | Mobile platform | <ul><li>Create message extension usage</li><li>Action ME usage</li></ul> | Optional |     |     |
| Expected: atMention | Mobile platform | @ mention a bot in a compose box | Optional |     |     |
| Android: chatSendMessage |     |     |     |     |     |
| iOS: sendMsg |     |     |     |     |     |
| Expected: botClickCardAction | Mobile platform | Tap on card buttons. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side | Basic |     | App key feature success data   |
| Android: showCard |     |     |     |     |     |
| iOS: missing |     |     |     |     |     |
| Expected: chatSendMessage | Mobile platform |     | Basic |     | App key feature success data   |
| iOS: composeSendMessage |     |     |     |     |     |
| Expected: composeSendMessage | Mobile platform | Tap on reply and reply to a bot chat in a channel | Optional |     |     |
| Android: replyChannel |     |     |     |     |     |
| iOS: missing |     |     |     |     |     |
| Expected: messageLike Android: reactLike_CM | Mobile platform | Like a bot message | Optional |     |     |
| Expected: messageUnread | Mobile platform | Message context menu options for a bot message | Optional |     |
| Android: markAsLastUnread |     |     |     |     |     |
| linkPreviewCancel | Mobile platform | Understand the preview closure behavior | Optional |     |     |
| markAsLastUnread | Mobile platform | Connector card context menu | Optional |     |     |
| messageLike | Mobile platform | Connector card like. Uses existing telemetry with app specific data | Optional |     |     |
| openApp | Mobile platform | Opening a personal app | Basic |     | App key feature success data   |
| personalAppNavBotChat | Mobile platform | navigate to the bot within personal app | Optional |     |     |
| personalAppNavTab | Mobile platform | Navigate to tabs within personal app | Optional |     |     |
| showCard | Mobile platform | Tap on card buttons. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side | Basic |     | App key feature success data   |
| tabActionCopyLink | Mobile platform | Understand how users discover & use tab copy link on mobile | Optional |     |     |
| tabActionMoreOptions | Mobile platform | Understand ellipsis usage from within a Tab for more option - discoverability & usage | Optional |     |     |
| tabActionOpenInBrowser | Mobile platform | Open in browser usage. This is necessary to understand if users prefer opening tab outside Teams | Optional |     |     |
| tabActionOpenInBrowserFromTab | Mobile platform | Understand open in browser usage from within a Tab for more option - discoverability & usage | Optional |     |     |
| tabActionOpenInTeams | Mobile platform | Open in usage. This is key in understanding if the tab can be by default set to open in Teams | Basic |     | App key feature success data   |
| tabActionRemove | Mobile platform | Understand how discoverable delete option is and the usage of the feature | Optional |     |     |
| tabActionRename | Mobile platform | Understand how discoverable rename is and the usage of the feature | Optional |     |     |
| tabActionSetting | Mobile platform | Understand how users discover & use tab config on mobile | Optional |     |     |
| Android - fix | Mobile platform |     |     |     |     |
| tabListMoreOptions | Mobile platform | Understand the usage of the more options for a tab | Optional |     |     |
| tabOpen | Mobile platform | Tabs are a critical feature for Teams and this will be needed to understand feature success & be ready to see if there are any issues in the way its being used | Basic |     |     |
| tapChicletExpand | Mobile platform | Understand how users preview cards on mobile | Optional |     |     |
| tapSettings | Mobile platform | Understand the number of users re-configuring apps on mobile | Optional |     |     |
| unblockChat | Mobile platform | Unblock a bot chat.This is enhancing existing telemetry around chats and is only adding app information. | Optional |     |     |
| OrgChart - No AS assigned | <ul><li>Mobile platform - orgChart</li><li>Mobile platform - wiki</li></ul> | Basic usage telemetry for org chart/Wiki usage telemetry | Basic |     | App key feature success data   |
| viewOrgChart | <ul><li>Mobile platform - orgChartQuickActionButton</li><li>Mobile platform - orgChartQuickActionButton</li></ul> | Basic usage telemetry for org chart | Basic |     | App key feature success data   |
| open edit | Mobile platform - wiki | Wiki usage telemetry | Basic |     | App key feature success data   |
| Wiki - No AS assigned | Mobile platform - wiki | Wiki usage telemetry | Basic |     | App key feature success data   |
| activityFeedClick | <ul><li>Mobile platform</li><li>Feeds</li></ul> | Tap on an activity feed item and navigate to bot chat / Captures click information on feed item | Basic | Helps to track if user got the relevant feed item (CTR) and if user can successfully act on a feed. | App key feature success data   |

### Not applicable

| Action_Scenario  | Team Owner | Description | Type | How the event is used | Basic Subtype |
|------------------|------------|-------------|------|-----------------------|---------------|
| navVaultSettings | NA         |             |      |                       |               |
| navVault         | NA         |             |      |                       |               |
| reactRemoved_HB  | NA         |             |      |                       |               |

### Notifications

| Action_Scenario                          | Team Owner    | Description | Type | How the event is used | Basic Subtype |
|------------------------------------------|---------------|-------------|------|-----------------------|---------------|
| navActivity                              | Notifications |             |      |                       |               |
| notificationError                        | Notifications |             |      |                       |               |
| notificationNavChannelConversation       | Notifications |             |      |                       |               |
| notificationNavChannelThreadConversation | Notifications |             |      |                       |               |
| notificationSettingTurnedOff             | Notifications |             |      |                       |               |
| quickNotificationAction                  | Notifications |             |      |                       |               |

### People

| Action_Scenario     | Team Owner | Description | Type | How the event is used | Basic Subtype |
|---------------------|------------|-------------|------|-----------------------|---------------|
| navPeopleSettings   | People     |             |      |                       |               |
| navPeople           | People     |             |      |                       |               |
| people              | People     |             |      |                       |               |
| peoplePickerInvoked | People     |             |      |                       |               |

### Search

| Action_Scenario | Team Owner | Description | Type | How the event is used | Basic Subtype |
|-----------------|------------|-------------|------|-----------------------|---------------|
| searchAbandoned | Search | Helps to track if search was successful vs if user abandoned search | Basic | Helps to track if search was successful vs if user abandoned search | App key feature success data   |
| searchCancelled | Search | <ul><li>Helps to track if search was successful vs if user abandoned search</li><li>Helps to track if search query was successful</li></ul> | Basic | <ul><li>Helps to track if search was successful vs if user abandoned search</li><li>Helps to track if search query was successful</li></ul> | App key feature success data   |
| searchIcon | Search | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li><li>Helps to track if user can find relevant results successfully</li></ul> | Basic | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li><li>Helps to track if user can find relevant results successfully | App key feature success data   |
| searchInitiated | Search | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li></ul> | Basic | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li></ul> | App key feature success data   |
| searchResultsClicked | Search | <ul><li>Helps to track if user can find relevant results successfully</li><li>Tracking usage of core scenario</li><li>Helps to track if search results was from ALL tab vs individual domain</li></ul> | Basic | <ul><li>Helps to track if user can find relevant results successfully</li><li>Tracking usage of core scenario</li><li>Helps to track if search results was from ALL tab vs individual domain</li></ul> | App key feature success data   |
| searchTab | Search | <ul><li>Helps to track domain information of the search result - people/chat/messages/files</li><li>Helps to track if search results was from ALL tab vs individual domain</li><li> | Basic | <ul><li>Helps to track domain information of the search result - people/chat/messages/files</li><li>Helps to track if search results was from ALL tab vs individual domain</li></ul> | App key feature success data   |
| searchTabClicked | Search | <ul><li>Helps to track domain information of the search result - people/chat/messages/files</li><li>Helps to track if user can find relevant results successfully</li></ul> | Basic | <ul><li>Helps to track domain information of the search result - people/chat/messages/files</li><li>Helps to track if user can find relevant results successfully</li></ul> | App key feature success data   |

### Teams EDU

| Action_Scenario         | Team Owner | Description | Type | How the event is used | Basic Subtype |
|-------------------------|------------|-------------|------|-----------------------|---------------|
| reportAbuseSend         | Teams EDU  |             |      |                       |               |
| reportAbuseConfirmation | Teams EDU  |             |      |                       |               |
| navAssignments          | Teams EDU  |             |      |                       |               |
| joinOptionsEdu          | Teams EDU  |             |      |                       |               |

### Teams FLW

| Action_Scenario                   | Team Owner | Description | Type | How the event is used | Basic Subtype |
|-----------------------------------|------------|-------------|------|-----------------------|---------------|
| group_map_open                    | Teams FLW  |             |      |                       |               |
| group_map_closed                  | Teams FLW  |             |      |                       |               |
| location_data_use_privacy_granted | Teams FLW  |             |      |                       |               |
| location_data_use_privacy_denied  | Teams FLW  |             |      |                       |               |
| location_settings_open            | Teams FLW  |             |      |                       |               |
| location_sharing_start            | Teams FLW  |             |      |                       |               |
| location_sharing_stop             | Teams FLW  |             |      |                       |               |
| parental_consent_grant            | Teams FLW  |             |      |                       |               |
| parental_consent_remove           | Teams FLW  |             |      |                       |               |
| active_session_banner_dismissed   | Teams FLW  |             |      |                       |               |
| brbFeedback                       | Teams FLW  |             |      |                       |               |
| brbFormCancelled                  | Teams FLW  |             |      |                       |               |
| brbFormOpened                     | Teams FLW  |             |      |                       |               |
| brbFormSubmit                     | Teams FLW  |             |      |                       |               |
| ocvFeedback                       | Teams FLW  |             |      |                       |               |
| ocvFormCancelled                  | Teams FLW  |             |      |                       |               |
| ocvFormOpened                     | Teams FLW  |             |      |                       |               |
| ocvFormSubmit                     | Teams FLW  |             |      |                       |               |
| navShifts                         | Teams FLW  |             |      |                       |               |
| navWalkieTalkie                   | Teams FLW  |             |      |                       |               |

### Teams FLW Android Prod

| Action_Scenario | Team Owner | Description | Type | How the event is used | Basic Subtype |
|-----------------|------------|-------------|------|-----------------------|---------------|
| AccessibilityUserConfiguration | Teams FLW Android Prod | When a FLW Manager approves a FLW request to take time off. | Basic | To toggle if this is accessible feature. | App key feature success data   |
| Viewed | Teams FLW Android Prod | User was unable to login. | Basic | Key functionality for schedule feature. | App key feature success data   |
| ErrorShown | Teams FLW Android Prod | User saves the day availability. | Basic | Key functionality for error shown. | App high value activity error data   |
| CreateShiftOrTimeOffClicked | Teams FLW Android Prod | This is to track if you clicked  create a shift or time off clicked | Basic | Key functionality for time off feature. | App key feature success data   |
| TimeOffReasonClicked | Teams FLW Android Prod | This it to track if you cited a reason for time off. | Basic | Key functionality for time off feature. | App key feature success data   |
| RequestSent | Teams FLW Android Prod | This is to log if there was a request sent. | Basic | Key functionality for request feature. | App key feature success data   |

### Teams FLW iOS Prod and Teams FLW Android Prod

| Action_Scenario | Team Owner | Description | Type | How the event is used | Basic Subtype |
|-----------------|------------|-------------|------|-----------------------|---------------|
| PageEntered | Teams FLW iOS Prod and Teams FLW Android Prod | User was able to login. | Basic | Key functionality for shifts details feature | App key feature success data   |
| DateChanged | Teams FLW iOS Prod and Teams FLW Android Prod | Register user's break start or end. This will not trigger until you have checked the location assuming location is required. | Basic | Key functionality for datechanged feature. | App key feature success data   |
| ShiftDetailsCalendar | Teams FLW iOS Prod and Teams FLW Android Prod | On the clock in screen, user clicks on the **Clock In** or **Clock Out** button. | Basic | Key functionality for calendar feature. | App key feature success data   |
| OfferSwapShiftFromL1Triggered | Teams FLW iOS Prod and Teams FLW Android Prod | Register user's clock in or out. This will not trigger until you have checked the location assuming location is required. | Basic | Key functionality for requests feature. | App key feature success data   |
| PlusButtonClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Triggered when the user closes the banner message of a notification. | Basic | Key functionality for requests feature. | App key feature success data   |
| ToggleClicked | Teams FLW iOS Prod and Teams FLW Android Prod | To view a declined time off request. | Basic | Key functionality for shifts reminder feature | App key feature success data   |
| ClosedBannerMessage | Teams FLW iOS Prod and Teams FLW Android Prod | Triggered when the user closes the banner message of a notification. | Basic | Key functionality for timezone feature. | App key feature success data   |
| MessageTriggered | Teams FLW iOS Prod and Teams FLW Android Prod | This is when a notification is triggered for a message. | Basic | Key functionality for timezone feature. | App key feature success data   |
| ShiftDetails | Teams FLW iOS Prod and Teams FLW Android Prod | This is to see the details of the shift. | Basic | Key functionality for request feature. | App key feature success data   |
| RequestTypeClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Tracking what type of request people select from the requests picker | Basic | Key functionality for request feature. | App key feature success data   |
| SendRequestClicked | Teams FLW iOS Prod and Teams FLW Android Prod | This instrumentation is logged for every individual request | Basic | Key functionality for request feature. | App key feature success data   |
| DayClicked | Teams FLW iOS Prod and Teams FLW Android Prod  | Clicking the day view when user is seeing their Shifts | Basic | Key functionality for day clicked feature. | App key feature success data   |
| DaySaved | Teams FLW iOS Prod and Teams FLW Android Prod | This is to save a day of shifts. | Basic | Key functionality for create shift feature. | App key feature success data   |
| GroupClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Tracks when a user clicks on the group of the shift | Basic | Key functionality for group clicked feature. | App key feature success data   |
| ShareShiftsClicked | Teams FLW iOS Prod and Teams FLW Android Prod | The details of an open shift. | Basic  | Key functionality for share shifts feature. | App key feature success data   |
| RequestTypeClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Tracking what type of request people select from the requests picker | Basic | Key functionality for request type feature. | App key feature success data   |
| RequestDetailsClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When the request for a shift is clicked (either FLW manager viewing or FLW worker) | Basic | Key functionality for request feature. | App key feature success data   |
| MyShiftPickerClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Only logged if request being sent is a swap or offer. Tracking user clicks into **My Shift** picker. | Basic | Key functionality for shift picker feature. | App key feature success data   |
| TeamShiftPickerClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When the user adds a new break entry. Log the event once the user saves the changes | Basic | Key functionality for shift picker feature. | App key feature success data   |
| OfferRecipientClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Only logged if request being sent is an offer. Tracking user clicks into the team member picker to offer a shift to. Offering means offering a shift time off. | Basic | Key functionality for offer feature | App key feature success data   |
| TeamSelectedClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When the user clicks on Add on a timesheet | Basic | Key functionality for team selected feature. | App key feature success data   |
| SendRequestBulkClicked | Teams FLW iOS Prod and Teams FLW Android Prod | This instrumentation point is logged once for each bulk request send. In addition, each individual request will log an event. | Basic | Key functionality for request bulk feature. | App key feature success data   |
| ApproveTimeOffRequest | Teams FLW iOS Prod and Teams FLW Android Prod | When an  FLW Manager approves a FLW request to take time off. | Basic | Key functionality of Time Off requests. | App key feature success data   |
| BadUrlLoginFailed | Teams FLW iOS Prod and Teams FLW Android Prod | User was unable to login. | Basic | If a user was unable to login. | Crash data – Unexpected app exit data   |
| BadUrlLoginSuccess | Teams FLW iOS Prod and Teams FLW Android Prod | User was able to login. | Basic | If a user was able to login. | App key feature performance data   |
| BreakStartEndClicked | Teams FLW iOS Prod and Teams FLW Android Prod | On the clock ins creen, user clicks on Start or End break button. | Basic | Key functionality for an FLW requesting a break. | App key feature success data   |
| BreakStartEndTriggered | Teams FLW iOS Prod and Teams FLW Android Prod | Register user's break start or end. This will not trigger until you have checked the location assuming location is required. | Basic | Key functionality for break feature within Shifts. | App key feature success data   |
| ClockInOutClicked | Teams FLW iOS Prod and Teams FLW Android Prod | On the clock in screen, user clicks on the **Clock In** or **Clock Out** button. | Basic | Key functionality for a worker clocking in and clocking out | App key feature success data   |
| ClockInOutTriggered | Teams FLW iOS Prod and Teams FLW Android Prod | Register user's clock in or out. This will not trigger until you have checked the location assuming location is required. | Basic | Key functionality if a worker clocked in with location | App key feature success data   |
| ClosedBannerMessage | Teams FLW iOS Prod and Teams FLW Android Prod | Triggered when the user closes the banner message of a notification. | Basic | Key functionality if a user closes a notification. | App key feature success data   |
| ComposeParticipantAdded | Teams FLW iOS Prod and Teams FLW Android Prod | When a user adds a participant to the shifts app. | Basic | Key functionality for adding people. | App key feature success data   |
| CreateConversationClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When a user creates a conversation with other workers. | Basic | Key functionality for creating message. | App key feature success data   |
| CreateShiftClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When a manager clicks to creates a shift. | Basic | Key functionality for shift creation. | App key feature success data   |
| DateChanged | Teams FLW iOS Prod and Teams FLW Android Prod | Changing dates that are shown in calendar view to view shifts. | Basic | Key functionality for feature calendar, and viewing date ranges. | App key feature success data   |
| DayClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Clicking the day view when user is seeing their Shifts | Basic | Key functionality for feature calendar, and viewing day shifts. | App key feature success data   |
| DaySaved | Teams FLW iOS Prod and Teams FLW Android Prod | User saves the day availability. | Basic | Key functionality for shifts, to save available days. | App key feature success data   |
| DeclineTimeOffRequest | Teams FLW iOS Prod and Teams FLW Android Prod | When a user declines the request for time off of work. | Basic | Key functionality for time off, for manager to reject time off request. | App key feature success data   |
| DeleteShift | Teams FLW iOS Prod and Teams FLW Android Prod | Tracks when the user deletes a shift. | Basic | Key functionality for feature, deleting a shift | App key feature success data   |
| EditShiftClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Tracks when a user edits a shift. | Basic | Key functionality for feature, editing a shift. | App key feature success data   |
| EntryPointClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Tracking clicking **Requests** in the **Schedule** tab. Requests are for when an FLW is requesting a shift time, etc. | Basic | Key functionality for requests. | App key feature success data   |
| FREActionClicked | Teams FLW iOS Prod and Teams FLW Android Prod | User clicks on **Get started**, **Try Later**, or **Close** (GPS) in First Run Experience (FRE). | Basic | Key functionality to track success of first run experience feature. | App key feature success data   |
| FRETriggered | Teams FLW iOS Prod and Teams FLW Android Prod | User views the time clock First Run Experience (FRE). | Basic | Key functionality to track success of first run experience within time clock feature. | App key feature success data   |
| GPSPromptClicked | Teams FLW iOS Prod and Teams FLW Android Prod | User clicks on **Allow** or **Don't Allow** in OS prompt. Allowing GPS or not. | Basic | Key functionality for feature, GPS location for user being on site for clocking in/out feature. | App key feature success data   |
| GroupClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Tracks when a user clicks on the group of the shift | Basic | Key functionality for feature, groups of shifts. | App key feature success data   |
| LogOutClicked   | Teams FLW iOS Prod and Teams FLW Android Prod | When a user logs out. | Basic | Key functionality for log out. | App key feature success data |
| MessageTriggered | Teams FLW iOS Prod and Teams FLW Android Prod | Triggered when the user's device time zone doesn't match the team time zone | Basic | Key functionality for feature of time zone. | App key feature success data   |
| MyShiftPickerClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Only logged if request being sent is a swap or offer. Tracking user clicks into **My Shift** picker. | Basic | Key functionality for feature, my shifts. | App key feature success data   |
| OfferRecipientClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Only logged if request being sent is an offer. Tracking user clicks into the team member picker to offer a shift to. Offering means offering a shift time off. | Basic | Key functionality for feature, offer shifts. | App key feature success data   |
| OfferSwapShiftFromL1 | Teams FLW iOS Prod and Teams FLW Android Prod | The type of shift a user tries to offer or swap from a shifts list. iOS action is a **SwipedRight** and Android action is **LongPressed** | Basic | Key functionality for feature, swap shifts. | App key feature success data   |
| OfferSwapShiftFromL1Triggered | Teams FLW iOS Prod and Teams FLW Android Prod | The type of shift a user tries to offer or swap from a shifts list. iOS action is a **SwipedRight** and Android action is **LongPressed** is triggered. | Basic  | Key functionality for feature, swap shifts. | App key feature success data   |
| OpensCalendarView | Teams FLW iOS Prod and Teams FLW Android Prod | Tracking user tapping on open shifts from Schedule tab | Basic | Key functionality for feature, Open Shifts | App key feature success data   |
| OpenShiftsClicked | Teams FLW iOS Prod and Teams FLW Android Prod | How many people tap the calendar icon. | Basic | Key functionality for feature, Calendar. | App key feature success data   |
| PlusButtonClicked | Teams FLW iOS Prod and Teams FLW Android Prod | <ul><li>Tracking clicking the **plus button** to start a schedule.</li><li>Tracking clicking the **plus button** to start a request on RequestList.sn</li></ul> | Basic | <ul><li>Key functionality for feature, schedule creation</li><li>Key functionality for feature, requests.</li></ul> | App key feature success data   |
| RequestActedOn | Teams FLW iOS Prod and Teams FLW Android Prod | Tracks when the manager acts on open shift requests | Basic | Key functionality for feature, open shifts requests. | App key feature success data   |
| RequestActionClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When a user requests an action. | Basic | Key functionality for feature, open shifts requests. | App key feature success data   |
| RequestDetailsClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When the request for a shift is clicked (either FLW manager viewing or FLW worker) | Basic | Key functionality for feature, request shifts. | App key feature success data   |
| RequestSent | Teams FLW iOS Prod and Teams FLW Android Prod | Tracks when the user requests an open shift | Basic | Key functionality for feature, request shifts. | App key feature success data   |
| RequestTypeClicked | Teams FLW iOS Prod and Teams FLW Android Prod | Tracking what type of request people select from the requests picker / Request type that the user clicks | Basic | Key functionality for feature, request shifts. | App key feature success data   |
| RetryButtonClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When a user clicks on the retry button. | Basic | Key functionality for feature, retry shifts. | App key feature success data   |
| SendRequestBulkClicked | Teams FLW iOS Prod and Teams FLW Android Prod | This instrumentation point is logged once for each bulk request send. In addition, each individual request will log an event. | Basic | Key functionality for feature, send shifts. | App key feature success data   |
| SendRequestClicked | Teams FLW iOS Prod and Teams FLW Android Prod | This instrumentation is logged for every individual request | Basic | Key functionality for feature, send shifts. | App key feature success data   |
| ShareShift | Teams FLW iOS Prod and Teams FLW Android Prod | The information that is given when a shift is shared. | Basic | Key functionality for feature, share shifts. | App key feature success data   |
| ShareShiftsClicked | Teams FLW iOS Prod and Teams FLW Android Prod | The details of an open shift. | Basic | Key functionality for feature,shifts. | App key feature success data   |
| ShiftAssigneeClicked | Teams FLW iOS Prod and Teams FLW Android Prod | The Shifts Calendar view showing the particular shifts details | Basic | Key functionality for feature, shifts. | App key feature success data   |
| ShiftDetails | Teams FLW iOS Prod and Teams FLW Android Prod | Your own shifts. | Basic | Key functionality for feature, shift shifts. | App key feature success data   |
| ShiftDetailsCalendar | Teams FLW iOS Prod and Teams FLW Android Prod | Triggered whenever a user receives a notification from a specific team and potentially wants to switch to that particular team. | Basic | Key functionality for feature, switch shifts. | App key feature success data   |
| ShiftDetailsMyShifts | Teams FLW iOS Prod and Teams FLW Android Prod | Tracking user tapping on calendar from Schedules Tab | Basic | Key functionality for feature, tab shifts. | App key feature success data   |
| SwitchTeamsDialogTriggered | Teams FLW iOS Prod and Teams FLW Android Prod | User views **Shifts** tab | Basic | Key functionality for feature, tab shifts. | App key feature success data   |
| TabCalendarClicked | Teams FLW iOS Prod and Teams FLW Android Prod | User has chosen a team from the team picker | Basic  | Key functionality for feature, team shifts. | App key feature success data   |
| TabViewed | Teams FLW iOS Prod and Teams FLW Android Prod | Only logged if request being sent is a swap. Tracking user clicks into **Team Shift** picker | Basic | Key functionality for feature, team shifts. | App key feature success data   |
| TeamSelectedClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When the user clicks on Add on a timesheet | Basic  | Key functionality for feature, timesheet shifts. | App key feature success data   |
| TeamShiftPickerClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When the user adds a new break entry. Log the event once the user saves the changes | Basic | Key functionality for feature, timesheet shifts. | App key feature success data   |
| TimesheetAddClicked | Teams FLW iOS Prod and Teams FLW Android Prod | When the user adds a note to their break edits. Log the event once the user saves the changes. | Basic | Key functionality for feature, timesheet. | App key feature success data   |
| TimesheetBreakAdded | Teams FLW iOS Prod and Teams FLW Android Prod | When the user adds a new clock entry. Log the event once the user saves the changes | Basic | Key functionality for feature, timesheet. | App key feature success data   |
| TimesheetBreakEdited | Teams FLW iOS Prod and Teams FLW Android Prod | When the user confirms their timesheet. Log the event when the user hits confirm in the modal | Basic | Key functionality for feature, timesheet. | App key feature success data   |
| TimesheetBreakNoteAdded | Teams FLW iOS Prod and Teams FLW Android Prod | When the user deletes their timesheet. Log the event when the user confirms the delete in the modal. | Basic | Key functionality for feature, timesheets. | App key feature success data   |
| TimesheetClockAdded | Teams FLW iOS Prod and Teams FLW Android Prod | When the user clicks on Edit for a timesheet. | Basic | Key functionality for feature, time sheets. | App key feature success data   |
| TimesheetClockEdited | Teams FLW iOS Prod and Teams FLW Android Prod | When the user clicks save on an edited timesheet | Basic | Key functionality for feature, timesheet shifts. | App key feature success data   |
| TimesheetConfirmed | Teams FLW iOS Prod and Teams FLW Android Prod | When the user adds a note to their timesheet edits. Log the event once the user saves the changes | Basic | Key functionality for feature, timesheetnote shifts. | App key feature success data   |
| TimesheetDeleted | Teams FLW iOS Prod and Teams FLW Android Prod | If a user does or does not have a shift reminder set, and the amount of minutes before a shift a user wants to be alerted. | Basic | Key functionality for feature, reminders. | App key feature success data   |
| TimesheetEditClicked | Teams FLW iOS Prod and Teams FLW Android Prod | User Configuration telemetry. | Basic | Key functionality to set up user information. | App key feature success data   |
| TimesheetEditSaved | Teams FLW iOS Prod and Teams FLW Android Prod | User taps on time sheet from a users profile to open that users time sheet. | Basic | Key functionality for feature, time sheets. | App key feature success data   |
| TimesheetNoteAdded | Teams FLW iOS Prod and Teams FLW Android Prod | To view an approved time off request. | Basic | Key functionality for feature, approve time off. | App key feature success data   |
| ToggleClicked | Teams FLW iOS Prod and Teams FLW Android Prod | To view a declined time off request. | Basic | Key functionality for feature, decline time off. | App key feature success data   |
| UserConfiguration | Teams FLW iOS Prod and Teams FLW Android Prod | To view a pending time off request. | Basic | Key functionality for feature, time of requests. | App key feature success data   |
| ShiftDetailsTodaysCoworkers | TeamsFLW Android Prod | On the clock in screen, user clicks on Start or End break button. | Basic | Key functionality for shifts details feature | App key feature success data   |
