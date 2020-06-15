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
| joinMeeting        | <ul><li>Join the meeting through Dial in</li><li>Join the meeting through Call me back</li><li>Join the meeting content only</li><li>Click on meeting join button from agenda view</li></ul> | Basic | Feature success and failure detection of joining meetings from calendar  | App key feature success data   |
| viewMeetingSeries  | <ul><li>Switch from instance to series meeting detail page</li><li>Click on view series from the meeting details page</li></ul> | Basic | To log successful rendering of meeting series. |     |

### Core

| Action_Scenario    | Description | Type | How the event is used | Basic Subtype |
|--------------------|-------------|------|-----------------------|---------------|
| enableCategory     | <ul><li>Enable a type of notification</li><li>Enable incoming call notifications</li></ul> | Basic | Notifications are key to drive engagement. This provides key success data for notification settings | App key feature success data   |
| pushNotification   | <ul><li>Launch via notification</li><li>Push notification clicked</li><li>Reconnecting push notification is tapped</li><li>**Reconnect failed** push notification is tapped</li></ul> | Basic | Success of notification delivery and user action on notification | App key feature success data   |
| deviceAddressBookSync |     |     |     |     |
| deviceAddressBookUnsync |     |     |     |     |
| chatAvatarEdit |     |     |     |     |
| chatAvatarEditGallery |     |     |     |     |
| chatAllowJoinViaLink |     |     |     |     |
| chatShareLink |     |     |     |     |
| composeVault |     |     |     |     |
| conversation |     |     |     |     |
| dashboardNav |     |     |     |     |
| navBookmark | User navigates to the Saved tab or app on the bottom bar or app tray | Basic | Track the discovery and usage of overflow apps | App key feature success data   |
| navChat | User navigates to the Chat tab or app on the bottom bar or app tray | Basic | Track the discover and usage of apps | App key feature success data   |
| navChatAndChannel | Not used ??? |     |     |     |
| navDashboardTab |     |     |     |     |
| navMore | Not used ??? |     |     |     |
| navSaved | User navigates to the Saved tab or app on the bottom bar or app tray | Basic | Track the discovery and usage of overflow apps | App key feature success data   |
| navCamera | User navigates to the Camera tab or app on the bottom bar or app tray | Basic | Track the discovery and usage of overflow apps | App key feature success data   |
| navContacts | User navigates to the Contacts or People tab or app on the bottom bar or app tray | Basic | Track the discovery and usage of overflow apps | App key feature success data   |
| navVideocamera | User navigates to the Camera tab or app on the bottom bar or app tray | Basic | Track the discovery and usage of overflow apps | App key feature success data   |
| officeLens |     |     |     |     |
| removeUser_CM |     |     |     |     |
| contactActivity |     |     |     |     |
| addMembers | Add members to a team or private channel | Basic | Track team or channel management | App key feature success data   |
| channelFollow | Turn on notifications for a channel | Basic | Track channel engagement | App key feature success data   |
| channelUnfollow | Turn off notifications for a channel | Basic | Track channel engagement | App key feature success data   |
| channelsActiveSetting | User changes their **notify me when I'm active on desktop** notification setting | Basic | For tracking notification setting usage | App key feature success data   |
| chatCreation | User creates chat | Basic | Track success of chat creation | App key feature success data   |
| chatStart |     |     |     |     |
| createOrJoinTeam | User taps **+** button to create or join a team | Basic | Track team creation and joins | App key feature success data   |
| editChannel | User taps on a button to edit a channel that they own or administer | Basic | Track team or channel management | App key feature success data   |
| editNavigation | User taps **Reorder** in **more** menu to edit the order of bottom bar apps | Basic | Track the success or discovery of navigation editing | App key feature success data   |
| editTeam | User taps on a button to edit a team that they own or administer | Basic | Track team or channel management | App key feature success data   |
| enableQuietDays | User enables quiet days | Basic | Track success of quiet hours feature | App key feature success data   |
| forcedUpdateAccept | User accepts to update the app version in the force update dialog | Basic | Tracks the acceptance rate of update prompts | App key feature success data   |
| forcedUpdateExit | User closes the app instead of updating the app version in the force update dialog | Basic | Tracks the acceptance rate of update prompts | App key feature success data   |
| forcedUpdatePrompt | ??? |     |     |     |
| messagedEditMessage | User edits message | Basic | Track usage of message editing |     |
| newChat | User creates chat | Basic | Track success of chat creation |     |
| noBGActivityDetected | Exceeds the threshold for background activity failures | Basic | Track notification failures caused by background processing issues | App key feature success data   |
| notBlockedDevice | User doesn't reach the threshold for background activity failures in 30 days | Basic | Track notification failures caused by background processing issues | App key feature success data   |
| openAppDrawer | User taps on **More** at the bottom bar to open the app drawer | Basic | Track the discovery and usage of overflow apps | App key feature success data   |
| openHamburgerMenu | User taps on hamburger icon (top-left) to open the side menu for access to settings, presence, tenant switcher | Basic | Track a number of investigation scenarios | App key feature success data   |
| processInBG | Process incoming notification in the background (Android) | Basic | Track notification failures caused by background processing issues | App key feature success data   |
| processInFG | Process incoming notification in the foreground (Android) | Basic | Track notification failures caused by background processing issues | App key feature success data   |
| renewTeam | Not used ??? |     |     |     |
| shareInto | User shares something from another app into Teams | Basic | Track sharing into Teams | App key feature success data   |
| teamCreate | User selects the option to create a new team | Basic | Track team creation | App key feature success data   |
| teamEdit | User edits some aspect of a team that they own or administer | Basic | Track team or channel management | App key feature success data   |
| viewChannelMembers | View channel members list | Basic | Track channel engagement | App key feature success data   |
| guideMe | Users taps on a banner that informs them about a 3P app blocking notifications and offers troubleshooting guidance | Basic | Track the success of the notification troubleshooter | App key feature success data   |
| resolveIssue | Users taps on **Resolve** in the notification troubleshooter flyout to navigate to the blocker app | Basic | Track the success of the notification troubleshooter | App key feature success data   |
| reorderChannelItem | User reorders pinned channels | Basic | Track pinned channel management | App key feature success data   |
| markChannelRead | User marks a channel read | Basic | Track pinned channel management | App key feature success data   |
| pinChannel | Pin a channel to show it above the teams and channels list | Basic | Track channel engagement | App key feature success data   |
| unpinChannel | Unpin a channel | Basic | Track channel engagement | App key feature success data   |
| hideChannel | Hide channel from the teams and channel list | Basic | Track channel engagement | App key feature success data   |
| scrollDatePicker |     |     |     |     |
| selectCalendarDate |     |     |     |     |
| chatAvatarEditCamera |     |     |     |     |
| chatAvatarEditView |     |     |     |     |
| tapDatePickerHandle |     |     |     |     |
| dragDatePickerHandle |     |     |     |     |
| reportAbuseOpen |     |     |     |     |
| chat | <ul><li>New message button or textbox in chat</li><li>1:1 chat tapped on callHistory item</li><li>1:1 chat click from call list</li></ul> | Basic | Feature success and usage telemetry see event description | App key feature success data   |
| createTeam, createChannel | <ul><li>Tap the **Skip** button in the **Add Members** page (check existing first)</li><li> Tap the **Done** button in the **Add Members** page (check existing first)</li><li>Show team or channel creation acknowledgement</li></ul> | Basic | Teams and channels are an essential construct of teams. This item provides success data around successful addition of members in a team and successful creation of a new team. | App key feature success data   |
| editTeam, editChannel | <ul><li>Tap the **Cancel** button in the **Add Members** page (existing team or channel)</li><li>Tap the **Done** button in the **Add Members** page (existing team or channel)</ul></li> | Basic | Teams and channels are an essential construct of teams. This item provides success data around successful addition of members in a team and successful creation of an existing team. | App key feature success data   |
| officeLens or cameraImage | Camera picture selected - standard camera or office lens (need databag prop stating imageCount) | Basic | Key success metrics for office lens integration with Teams. | App key feature success data   |
| acknowledgeSettingChange | Acknowledge update in **we updated notification setting** dialog | Basic | Notification is key for driving engagement. This is a feature success metrics to acknowledge notification update. Used to deduce overall notification reliability. | App key feature success data   |
| addChannel | Admin Add channel | Basic | Teams and channels are essential construct of teams. This item provides success data around successful creation of a channel. |     |
| addMember | Taps the **Invite people** button in the **More** menu | Basic | This provide key feature success telemetry around a freemium invite. Helps the team understand feature discoverability and success metrices. | App key feature success data   |
| alertsNavAlert | Tapping on a feed item | Basic | Feature success telemetry, see event description. | App key feature success data   |
| appBG | App BG | Basic  |     | App key feature success data   |
| appKilled | App Killed | Basic | Time spent on app is a key metric to understand overall app engagement and this metric helps us deduce overall time spent on the app. | App key feature success data   |
| cancelNavigationToLink | User chose to cancel navigation | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| cancelRequestToJoinTeam | Cancel request to join team | Basic | Teams and channels are essential construct of teams. This item is required to measure feature discoverability and success for joining a team. | App key feature success data   |
| cancelRequestToJoinTeamError | Error with cancel join request | Basic | Teams and channels are essential construct of teams. This item is required to measure feature discoverability and success for successful completion of joining a team. | App key feature success data   |
| castPpt | <ul><li>Tapping on share a PowerPoint option</li><li>Selecting a particular PowerPoint</li><li>Selecting Teams and Channels folder in file picker page</li><li>Selecting OneDrive folder in file picker page</li><li>Stopping the casting session</li><li>Tapping on multitasking PiP</li>Selecting display option from file view</li></ul> | ??? <ul><li>Not in production you can remove these rows</li><li>Basic</li></ul> | Feature success and usage telemetry, see event description. | App key feature success data   |
| castScreen | <ul><li>Tapping on share screen option</li><li>Stopping the screen sharing session</li><li>Selecting display option from file view</li></ul> | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| changeIsActiveSetting | Change desktop activity based notification. | Basic | Notifications are key to drive engagement. This provides key success data for push notification | App key feature success data   |
| channel | New message button or textbox in chat. | Basic | Provides key success data for compose messages in channel and overall app engagement. | App key feature success data   |
| ChannelDetails | <ul><li>User taps on channel header</li><li>User navigates to channel details page</li></ul> | Basic | Provides key success data for channel navigation | App key feature success data   |
| channelFollow/channelUnfollow | Follow channel | Basic | Provides key success data on following the channel | App key feature success data   |
| channelNav | Navigating to a channel from anywhere | Basic | Provides key success data for channel navigation and entrypoint discoverability | App key feature success data   |
| channelNotificationSettings | <ul><li>Respond to **New Notification settings** dialog</li><li> Tap channel notification settings button in channel view</li><li>Select a channel notification setting</li></ul> | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| channelTabOverflow | Clicks on **More** tab in channel | Basic | As the number of apps increase in Teams, this is an important metric for success data for tabs discoverability and features | App key feature success data   |
| Chat - No AS Assigned | <ul><li>Done button on adding a user to a chat</li><li>User taps on chat list filter to filter by unread</li></ul> | Basic | Key success metrics for viewing unread chat or editing chat roaster | App key feature success data   |
| chatAddChat | Add member to chat button tapped (this will be same for 1:1 chat and group chat) | Basic | Key success metrics for editing chat roaster | App key feature success data   |
| chatCM_CopyText | Tap copy text on chat context menu | Basic | For a chat product copy paste is important. Provides success data for copy paste feature in chats | App key feature success data   |
| chatCM_DeleteMessage | Tap delete message on chat context menu | Basic | Provides success data for delete message feature in chats | App key feature success data   |
| chatCM_edit | Tap edit on chat context menu | Basic | Provides success data for edit message feature in chats | App key feature success data   |
| chatCM_Forward | Tap forward on chat context menu | Basic | Provides success data for forward message feature in chats | App key feature success data   |
| chatCM_markUnread | Tap mark as unread on chat context menu | Basic | Provides success data for mark as read or unread message feature in chats | App key feature success data   |
| chatCM_save | Tap save on chat context menu | Basic | Provides success data for save message feature in chats | App key feature success data   |
| chatCM_SeenBy | Tap on Seen by context menu option. Read Receipts, such as read by (readby) | Basic | Provides success data for read receipts feature in teams | App key feature success data   |
| chatContactsEnter | User enters chat contacts tab | Basic | Provides success data for contacts tab in teams | App key feature success data   |
| ChatDetails | <ul><li>User taps on chat header</li><li>User navigates to chat detail page</li></ul> | Basic | Provides success and discoverability data for chat details page | App key feature success data   |
| chatRecentEnter | User enters the chat recent tab | Basic | Feature success telemetry, see event description. | App key feature success data   |
| chatSendMessage | Send Chat Message | NSD | As teams is a chat and collaboration product, this is a required success metrics for the product. Any dip in this metrics would be alarming. | Activity success   |
| clickPhotoOfficeLens | Click on **Take photo** - launch camera (Android only) | Basic | Provide success metrics for camera integration and image sharing | App key feature success data   |
| composeExpandComposer | Format button tapped | Basic | Provide success data for rich text box integration | App key feature success data   |
| composeFilePick | native file picker launched | Basic | Provide success data for files sharing  |     |
| composeImagePicker | Image button tapped | Basic | Provide success metrics for image sharing | App key feature success data   |
| composeLocation | Location button tapped in compose | Basic | Provide success metrics for location integration in Teams| App key feature success data   |
| composeMention | At mention | Basic | For a collaboration product @mentioning and getting someone's attention is important. This provides success data for @mention feature in Teams | App key feature success data   |
| composeOpenEmoticonPicker | Emoticon picker tapped | Basic | Provide success data for emoticon picker | App key feature success data   |
| composeOpenFunPicker | Fun picker tapped | Basic | Provide success data for fun picker, including giphy and stickers | App key feature success data   |
| consumeVoiceMessage  | Voice message played | Basic | Voice message is important part of mobile messaging and is a competition parity feature. Provides success data for voice message consumption. | App key feature success data   |
| ContactCard_SeeMoreOOF | See move of long OOF message |     |     |     |
| conversation, tabs | Tab clicked | Basic | Tabs are essential construct of Teams. This telemetry is fired whenever a tab is clicked in a channel. | App key feature success data   |
| copyLink | Copy link to channel post | Basic | Feature success metrics for Copy link feature | App key feature success data   |
| createChannel | <ul><li>Tap **Done** button in **Create Channel** Page</li><li>Tap **Cancel** button in **Create Channel** Page</li><li>Show validation error</li></ul> | Basic | Teams and channels are essential construct of Teams. This item provides success data around successful creation or discard action for new channel creation. | App key feature success data   |
| createTeam | <ul><li>Tap **Done** button in **Create Team** Page</li><li>Tap **Cancel** button in **Create Team** Page</li><li>Validation error shown</li></ul> | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| disabled | User taps **Skip notifications** in FRE | Basic | Notifications are key to drive engagement. This provides key success data for skipping the notification in FRE flow. | App key feature success data   |
| disableQuietDays | Quiet Days disabled | Basic | Feature success telemetry for quiet days | App key feature success data   |
| disableQuietHours | Quiet Hours disabled | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| discoverTeams | Navigate to Browse and Join Teams page | Basic | Required to measure feature discoverability and success | App key feature success data   |
| dismissFlyout | Dismiss button pressed | Basic | Required to measure feature discoverability and success | App key feature success data   |
| dismissModality | Exit modality picker without sharing |     |     |     |
| dismissModalityPicker | Modality picker button pressed |     |     |     |
| dismissReadReceiptsNotice | User pressed **Got it** from feature notice | Basic | Key feature success metrics for read receipts | App key feature success data   |
| DLPDelete | User deleted blocked message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPEdit | User edited blocked message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPOverride | User overrode blocked message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPOverrideReport | User reported false positive and overrode message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPReport | User reported false positive | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPResolve | User attempted to resolve DLP message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| DLPSeeOriginal | User tapped to see original message | Basic | Feature success telemetry, see event description. | App key feature success data   |
| edit | Edit button in the message | Basic | Provides success data for edit message feature in chats | App key feature success data   |
| enabled | <ul><li>User taps **Enable notifications** in FRE</li><li>User taps Enable in reminder</li></ul> | Basic | Notifications are key to drive engagement. This provides key success data on enabling the notification in FRE flow | App key feature success data   |
| enabled, notNow | Notification Permission Prompt Accept button | Basic | Captures how many people have enabled the notification, provide information with app engagement. Required for feature success | App key feature success data   |
| enabled/notNow | FRE Notifications Permission (iOS) | Basic | Lets us capture user engagement with the notification feature. | App key feature success data   |
| enablediOSPrompt | User actually enables notifications in iOS notifications permissions prompt | Basic | This gives us information about Users who actually enables notifications in iOS from notifications permissions prompt | App key feature success data   |
| enabledQuietDays | Quiet Days enabled | Basic | Feature success telemetry for quiet days | App key feature success data   |
| enableLocationPermission | Enable location services (TBD) ??? | Basic | Feature success telemetry for location services | App key feature success data   |
| enableQuietHours | Quiet Hours enabled | Basic | Feature success telemetry for quiet hours | App key feature success data   |
| endEditing | Save button pressed |     | Feature success telemetry for edit feature |     |
| endMyShift | <ul><li>Number of devices in shared mode</li><li>Number of times signed out</li></ul> | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| expandCollapseSection | Tap a section header to expand or collapse section | Basic | Feature success telemetry | App key feature success data   |
| federatedUpgradeNewChat | User upgrades legacy chat to native | Basic | This is required to get the success data for federated chats feature | App key feature success data   |
| files, conversation, oneNote etc | Tab clicked | Basic | Let us know the **About** tab discoverability and feature success for tabbed layout | App key feature success data   |
| firstTimeSignedIn | <ul><li>Sign-in success</li><li>First sign-in Succeeded</li><li>Sign-in Errors Seen by User</li><li>Record telemetry about MAM/MDM policies implemented on first time login</li><li>Record app install referrer parameters after first time successful login</li></ul> | Basic | Feature success telemetry for sign in or sign up. Provides data about failure during FRE | App key feature success data   |
| formattingBold | User selects bold formatting | Optional | Track usage of formatting features | App key feature success data   |
| formattingHighlight | User selects highlight formatting | Optional | Track usage of formatting features | App key feature success data   |
| formattingImportant | User selects importance | Optional | Track usage of formatting features | App key feature success data   |
| formattingItatlics | User selects italics | Optional  | Track usage of formatting features | App key feature success data   |
| formattingTextColor | User selects text color formatting | Optional | Track usage of formatting features | App key feature success data   |
| formattingUnderline | User selects underline | Optional  | Track usage of formatting features | App key feature success data   |
| FRE - No AS Assigned | Record telemetry about MAM/MDM policies on app launch to gather data about active users | Basic | Feature success telemetry for Intune integration for MAM and MDM. Provides success data about failure during FRE | App key feature success data   |
| freDone | FRE done | Basic | Feature success telemetry on how many users successfully completed the sign in. This helps us preempt the sign in issues with the product. And solve login isues proactively. | App key feature success data   |
| funSearchQueryEntered  | Giphy query entered | Optional | Success data for giphy attachment feature in Teams | App key feature success data   |
| funSelectItem | Giphy image choose | Basic | Success data for giphy attachment feature in Teams | App key feature success data   |
| galleryImage | Image uploaded - gallery | Basic | Success data for image attachment feature in Teams | App key feature success data   |
| goToNotificationSettings | Go to notification settings page from **we updated notification settings** dialog | Basic | Notification is key for driving engagement. This is a feature success metrics to understand notifications. Used to deduce overall notification reliability. | App key feature success data   |
| hamburgerMenu | Navigate to hamburger menu | Basic | Hamburger contains important actions such as account switch, notification settings, data setting, profile settings, this is important to understand hamburger menu discoverability. | App key feature success data   |
| hide | Hide chat | Basic | Feature success telemetry for hiding chats | App key feature success data   |
| image | Image | Basic | Feature success telemetry for image preview | App key feature success data   |
| importantMessage_select | User selects important message from priority context menu | Basic | Feature success telemetry for important message | App key feature success data   |
| importantMessageSend  | User sends important message | Basic | Feature success telemetry for important message | App key feature success data   |
| install | <ul><li>Install</li><li>Install Event</li></ul> | Basic | App key feature success data on overall installation of Teams | App key feature success data   |
| installReferrer | Record app install referrer parameters after first time install | Basic | Feature success telemetry as we need to understand the path user has installed the app from to proactively identify the issues in users login experience with Teams. | App key feature success data   |
| inviteFreemium | Taps the **+** button in Invite screen | Basic | Helps with feature discoverability and success metrices for freemium | App key feature success data   |
| inviteGuest | Taps the **+** button in Invite screen | Basic | Helps with feature discoverability and success metrices for Teams guests | App key feature success data   |
| joinTeam | Join button pressed | Basic | Feature success and usage telemetry | App key feature success data   |
| Launch source eg. direct, link, appShortcut | Launch directly or via link (record MAM/MDM telemetry on app launch to collect data for active users)| Basic | App engagement success metrics, Also success metrics for Intune, MAM and MDM integration | App key feature success data   |
| leaveChat | Confirm leave chat | Basic | Feature success telemetry for group chat | App key feature success data   |
| legacyChatLink | User taps on link to legacy chat | Basic | Feature success telemetry for federated chats | App key feature success data   |
| likeAppDismiss |     | Basic | App ratings are an important part of mobile app infrastructure and are tracked at various levels for app success. Success metrics for the app overall. | App key feature success data   |
| likeAppNo |     | Basic | App ratings are an important part of mobile app infrastructure and are tracked at various levels for app success. Success metrics for the app overall. | App key feature success data   |
| likeAppYes |     | Basic | App ratings are an important part of mobile app infrastructure and are tracked at various levels for app success. Success metrics for the app overall. | App key feature success data   |
| likeMsg   | Click on Like | Basic | Feature success metrics, drives content engagement and inturn overall app engagement | App key feature success data   |
| locationCard | Click on location card | Basic | Feature success metrics for location sharing | App key feature success data   |
| mapAppPicker | Choose map app from map picker (TBD)??? | Basic | Feature success metrics for location sharing | App key feature success data   |
| markAsRead | Mark as read | Basic |     | App key feature success data   |
| markAsUnread | Mark as unread | Basic |     | App key feature success data   |
| memberListLoadMore | Scroll down to load more | Basic | Required to define basic feature success metrics. |     |
| messageCopyMessage | messageCopyMessage | Basic | Feature success metrics for copy message feature | App key feature success data   |
| messageDelete | Message delete | Basic | Feature success metrics for delete message feature | App key feature success data   |
| messageEditMessage | Edit message | Basic | Feature success metrics for edit message feature | App key feature success data   |
| messageForwardMessage | User taps on Forward entry point from message context menu | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| messageLike/messageUnlike | Message like or unlike | Basic | Feature success metrics for message reactions | App key feature success data   |
| messageMuteSender | Mute or unmute sender | Basic | Feature success telemetry, see event description. | App key feature success data   |
| messagePriority_select | User selects Message priority entry point | Basic | Feature success metrics for important or urgent messages | App key feature success data   |
| messageSeeOriginal | User reverts translated message back to original | Basic | Feature success metrics for message translation | App key feature success data   |
| messageShareMessage | MessageShareMessage | Basic | Feature success metrics for share message | App key feature success data   |
| messageTranslate | User translates a message | Basic | Feature success metrics for message translation | App key feature success data   |
| messageUnabletoEdit | User unable to edit message | Basic | Feature success metrics for edit message feature | App key feature success data   |
| multipleAccounts | Number of accounts for a user | Basic | Feature success metrics for MTMA (multiple tenant and multiple account) feature | App key feature success data   |
| multipleTenants | Number of tenants per account | Basic | Feature success metrics for MTMA (multiple tenant and multiple account) feature | App key feature success data   |
| mute | Mute chat | Basic  | Feature success and usage telemetry, see event description. | App key feature success data   |
| nameGroupChat | Name group chat | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| nativeChatLink | User taps on link to native chat | Basic | Feature success telemetry, see event description. | App key feature success data   |
| navActivity, navChat, navTeams, navMore, navOrg, navFiles, navSaved, nav+(Appname) | Nav Tab clicked (or hamburger menu clicked - navMore) | Basic | Provides navigation information for each of the apps. Important to get active user count for various modules. | App key feature success data   |
| navTeams | Tap **See all** | Basic | Feature success metrics for teams list | App key feature success data   |
| notNow | User taps **Not now** in reminder | Basic |     | App key feature success data   |
| notNowUpdate | UpdateDefer | Basic |     |     |
| open | Notification Settings tap | Basic | Allows us to capture user engagement with the notification feature. | App key feature success data   |
| openContactCard_ReactionSummary | Navigate to contact card from reaction summary page | Basic | Feature success metrics for people app (contact card). | App key feature success data   |
| openModalityPicker | X = ChatsAndChannels for chats and channels |     |     |     |
| openPhotoLibrary | Click on photo library | Basic | How many total users open photo gallery. This, with combination of image selection and send, will give us overall information about the image picking experience and how many people tried to attach the image versus how many successfully attached versus abandoned. | App key feature success data   |
| openQuietDays | Navigate to Quiet Days page | Basic | Feature success telemetry for quiet days | App key feature success data   |
| openQuietHours | Navigate to Quiet Hours Page | Basic | Feature success telemetry for quiet hours | App key feature success data   |
| openReactionHoverBubble | Press add reaction button on reaction summary page | Basic | Feature success telemetry for reactions | App key feature success data   |
| openReactionSummary | Invoke reaction summary drawer | Basic | Feature success telemetry for reactions | App key feature success data   |
| photoLibraryPicker | **Open photo library** tapped inside image picker | Basic | Feature success telemetry for gallery integration for image picking experience | App key feature success data   |
| provideFeedbackDismiss |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| provideFeedbackNo |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| provideFeedbackYes |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| provideRatingDismiss |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| provideRatingNo |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| provideRatingYes |     | Basic | Provides first hand information about user feedback, which is essential to overall product | App key feature success data   |
| quickSelectImagePicker | Quick select |     |     |     |
| quietHoursValues | Capture Quiet Hours State on back button navigation | Basic | Feature success telemetry for quiet hours | App key feature success data   |
| quotedReplySent | User sent reply message with context type | Basic | Feature success telemetry for quoted reply | App key feature success data   |
| reactAngry_CM | React with angry from context menu | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactAngry_HB | React with angry from hover bubble | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactHeart_CM | React with heart from context menu | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactHeart_HB | React with heart from hover bubble | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactLaugh_CM | React with laugh from context menu | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactLaugh_HB | React with laugh from hover bubble | Basic | Feature success telemetry for reactions  | App key feature success data   |
| reactLike_doubleTap  | React with like from double tap | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactLike_HB | React with like from hover bubble | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactSad_CM | React with sad from context menu | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactSad_HB | React with sad from hover bubble | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactSurprised_CM | React with surprise from context menu | Basic | Feature success telemetry for reactions | App key feature success data   |
| reactSurprised_HB | React with surprise from hover bubble | Basic | Feature success telemetry for reactions | App key feature success data   |
| readReceipts | User enabled feature | Basic | Feature success telemetry for read receipts | App key feature success data   |
| redeemInvite | In app redemption | Basic | Feature success metrics for freemium invite | App key feature success data   |
| removeReplyObject | User removed reply object from compose | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| removeUserConfirm | User confirmed remove user dialog| Basic | Feature success metrics for quoted reply | App key feature success data   |
| removeUserContextMenu | User removed participant via context menu | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| removeUserSwipe | User removed participant via swipe | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| replyChain | New message button or textbox in reply chain (thread) | Basic | Feature success metrics for reply message experience in a channel | App key feature success data   |
| replyChannel | Reply button in channels | Basic | Feature success metrics for reply message experience in a channel | App key feature success data   |
| replyNavigation | User tapped on reply object to navigate to referenced post | Basic | Feature success metrics for quoted reply | App key feature success data   |
| replyViaMsgOptions | User started reply via context menu | Basic | Feature success and discoverability metrics for quoted reply | App key feature success data   |
| replyViaSwipe | User started reply via swipe | Basic | Feature success and discoverability metrics for quoted reply | App key feature success data   |
| requestJoinTeam  | Request button pressed | Basic | Feature success and discoverability metrics for teams and channel | App key feature success data   |
| requestToJoinTeam | Request to join team (public or private) | Basic | Feature success and discoverability metrics for teams and channel | App key feature success data   |
| requestToJoinTeamError | Error with join request | Basic | Feature success metrics for teams and channel | App key feature success data   |
| returnToMessage | User tapped **Return** button to navigate back to message | Basic | Feature success metrics for quoted reply | App key feature success data   |
| safeLink | Link verified as safe | Basic | Feature success telemetry | App key feature success data   |
| selectDevice | Selecting a particular device in displays app | Basic | Feature success and usage telemetry, see event description. | App key feature success data   |
| selectGeneralSetting | Go to general settings | Basic | Feature discoverability and success metrics | App key feature success data   |
| selectSettingOption | Go to settings tab from hamburger menu | Basic | Feature discoverability and success metrics | App key feature success data   |
| selectTheme | Enable dark theme | Basic | Direct feature success metrics for dark theme. | App key feature success data   |
| sendForward | User confirms to send forward message from forward picker | Basic | Feature success metrics for forward message feature | App key feature success data   |
| sendImage | Send image | Basic | Feature success metrics for image attachment | App key feature success data   |
| sendLocation | Send location | Basic | Feature success metrics for location sharing experience | App key feature success data   |
| sendMsg | Click on send in reply | NSD | Let us know the success of the main construct of post in Teams | Activity success   |
| sendVoiceMessage | Record button released | Basic | Feature success metrics for voice messages | App key feature success data   |
| settingsNavReadReceiptNotice | User went to settings from feature notice | Basic | Feature success metrics for read receipts | App key feature success data   |
| shareHistory | Share history picker tapped | Basic | Feature success metrics for adding users to group chat and share history feature | App key feature success data   |
| showBanner | Number of times the **WiFi Connected, No Internet** banner appears | Optional |     |     |
| shownReadReceiptNotice | User shown feature notice with settings options  | Basic | Feature discoverability and success metrics for read receipts | App key feature success data   |
| signIn | <ul><li>User taps **Sign in** on welcome page</li><li>Tap **Sign In** button</li></ul> | Basic | Feature success metrics for sign in experience in Teams. Helps us identify sign in issues proactively. | App key feature success data   |
| signUp | Taps **Create a free account**/**Sign up for free** | Basic | Feature success metrics for sign in experience in Teams. Helps us identify sign up issues proactively. | App key feature success data   |
| skipVerificationForLink | User chose to skip verification | Basic | Feature success metrics for ATP safe link | App key feature success data   |
| SMSSendMessage | User sends SMS message | Basic | Feature success metrics for send SMS feature | App key feature success data   |
| startEditing | Edit button pressed |     |     |     |
| StatusMsgCancel | User cancels change to status message | Basic | Feature success metrics for add status message feature | App key feature success data   |
| StatusMsgExpiry | User sets expiry time | Basic | Feature success metrics for add status message feature | App key feature success data   |
| StatusMsgSet | User sets new status message | Basic | Feature success metrics for add status message feature | App key feature success data   |
| StatusPageViaContactCard | User enters status compose experience via contact card | Basic | Feature success metrics for add status message feature | App key feature success data   |
| StatusPageViaHamburger | User enters status compose experience via hamburger | Basic | Feature success metrics for add status message feature | App key feature success data   |
| table | Click on table | Basic | How many people tap on table in chat or channel conversation | App key feature success data   |
| takePhotoPicker | **Take photo** tapped inside image picker | Basic | Feature success metrics for camera integration in image picking experience | App key feature success data   |
| teamNav | View menu options for team |     |     |     |
| tenantSwitch | On Switch Tenant | Basic | Feature success metrics for MTMA (multiple tenant and multiple account) feature, this helps identify and fix issues proactively and provide a smooth switching experience | App key feature success data   |
| tenantSwitchUnsupportedError | Tenant Unsupported Error (when user sees the error) | Basic | Feature success metrics for MTMA, provides telemetry around account or tenant switch errors, so we can identify and fix issues proactively and provide a smooth switching experience | App key feature success data   |
| toggleChannelsInChat | Turn feature on or off | Basic | Feature success metrics for unified chats and channel experience | App key feature success data   |
| translateFailed | Translation failed (excluding offline) | Basic | Feature success metrics for message translation feature | App key feature success data   |
| unsafeLink | Link was determined to be unsafe | Basic | Feature success metrics for ATP Safe Links | App key feature success data   |
| upgrade | Taps the **Upgrade** button in **More** menu | Basic | Feature success metrics for freemiums as this would provide information about the number of successful conversations | App key feature success data   |
| urgentMessageSelect | User selects urgent message from priority context menu | Basic | Feature success metrics for priority messages | App key feature success data   |
| urgentMessageSend | User sends urgent message | Basic | Feature success metrics for priority messages | App key feature success data   |
| url | url | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreview | Url preview | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreviewAdd | URL preview add | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreviewOpen | URL preview open | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreviewRemove | URL preview removed | Basic | Feature success metrics for url preview | App key feature success data   |
| viewRequests | **View requests** button pressed | Basic | Feature success metrics for join Teams experience | App key feature success data   |

### Core/Mobile platform

| Action_Scenario | Description | Type | How the event is used | Basic Subtype |
|-----------------|-------------|------|-----------------------|---------------|
| channelNavTab | <ul><li>Clicks on **Files** tab in channel</li><li>Tabs are a critical feature for Teams and this will be needed to understand feature success and be ready to see if there are any issues in the way its being used </li><li>Connector card reply. Uses existing telemetry with app specific data</li></ul> | Basic/Optional | This is an essential metric for the files tab as it provides the success and discoverability data for files in Teams | App key feature success data   |
| channelSendMessage | <ul><li>Send Channel Message</li><li>@ mention a bot in a compose box</li></ul> | NSD/Optional | As teams is a chat and collaboration product, this is a required success metric for the product all up. Any dip in these metrics would be alarming | Activity success   |
| chatListNavConversations | ChatList NavConversations | Basic | Feature success telemetry, see event description. | App key feature success data   |
| messageBookmarkMessage | <ul><li>messageBookmarkMessage</li><li>Connector card save. Uses existing telemetry with app specific data</li><li>Save a bot message</li></ul> | Optional |     | App key feature success data   |
| reactLike_CM | <ul><li>React with like from context menu</li><li>Like a bot message</li></ul> | Basic/Optional | Feature success and usage telemetry, see event description. | App key feature success data   |
| replySendMessage | Send channel reply | NSD/Basic|     | <ul><li>Activity success</li><li>App key feature success data</li></ul>   |

### Feeds

| Action_Scenario | Description | Type | How the event is used | Basic Subtype |
|-----------------|-------------|------|-----------------------|---------------|
| activityTabClicked | <ul><li>Activity tab shown</li><li>Captures activity tab event</li></ul> | Basic | Helps to track if user came back to activity tab | App key feature success data   |
| activityContextMenu | Overflow actions in activity feed | Basic | Helps to track if user can do contextual actions on feed | App key feature success data   |
| activityFeedLongPress | Captures long press gestures on feed item | Basic | <ul><li>Helps to track if user can successfully triage feed items using gestures</li><li>Tracking usage of core scenario</li></ul> | App key feature success data   |
| activityFeedSwipe | Captures swipe gestures on feed item | Basic | Helps to track if user can successfully triage feed items using gestures | App key feature success data   |
| activityFilterClick | Captures activity filter usage | Basic | Helps to track if user can filter feed items successfully | App key feature success data   |
| activityFilterOptionsClick | Captures activity filter usage | Basic | <ul><li>Helps to track if user can filter feed items successfully</li><li>Helps to track if user can successfully triage feed items using gestures</li></ul> | App key feature success data   |
| activityFilterOptionsClicked | Captures activity filter usage | Basic | <ul><li>Helps to track if user can filter feed items successfully</li><li>Tracking usage of core scenario</li></ul> | App key feature success data   |
| activityTypeDropdown | Captures activity filter usage to switch between My Activity and Feeds | Basic | Helps to track if user can filter feed items successfully | App key feature success data   |
| selectActivityType | Captures select gestures on feed item | Basic | <ul><li>Helps to check if user was able to initiate download operation</li><li>Helps to track if user can download file successfully</li></ul> | App key feature success data   |

### Files

| Action_Scenario | Description | Type | How the event is used | Basic Subtype |
|-----------------|-------------|------|-----------------------|---------------|
| downloadFile | <ul><li>Helps to check if user was able to initiate download operation</li><li>Helps to track if user can download file successfully</li></ul> | Basic | <ul><li>Helps to check if user was able to initiate download operation</li><li>Helps to track if user can download file successfully</li></ul> | App key feature success data   |
| fileThumbnailPreviewDownloaded | Helps to identify is thumbnail was rendered successfully for a file | Basic | Helps to identify is thumbnail was rendered successfully for a file | App key feature success data   |
| fileThumbnailPreviewFromCache | <ul><li>Captures if thumbnail shows from cache successfully</li><li>Helps to identify if thumbnail was rendered successfully for a file</li></ul> | Basic | <ul><li>Captures if thumbnail shows from cache successfully</li><li>Helps to identify if thumbnail was rendered successfully for a file</li></ul> | App key feature success data   |
| fileThumbnailPreviewNotAvailable | Helps to identify if thumbnail was rendered successfully for a file | Basic | Helps to identify if thumbnail was rendered successfully for a file | App key feature success data   |
| openFile | <ul><li>Helps to identify if user was able to open file in the chat successfully</li><li>Helps to identify if user was able to open file from files listing</li><li>Helps to check if user can open files from OneDrive list</li><li>Helps to identify if user can open files from channel list</li><li>Helps tracking if user can open file from group chats</li><li>Helps tracking if user can successfully open from files app</li><li>Helps to track if user can open from message file chiclet successfully</li><li>Helps to track if user can open files from recent list successfully</li><li>Helps to track if user can open file from file list successfully</li><li>Helps to track if user can open file from messages file chiclet</li><li>Helps to track if files can be opened successfully from file list</li></ul> | Basic | <ul><li>Helps to identify if user was able to open file in the chat successfully</li><li>Helps to identify if user was able to open file from files listing</li><li>Helps to check if user can open files from OneDrive list</li><li>Helps to identify if user can open files from channel list</li><li>Helps tracking if user can open file from group chats</li><li>Helps tracking if user can successfully open from files app</li><li>Helps to track if user can open from message file chiclet successfully</li><li>Helps to track if user can open files from recent list successfully</li><li>Helps to track if user can open file from file list successfully</li><li>Helps to track if user can open file from messages file chiclet</li><li>Helps to track if files can be opened successfully from file list</li></ul> | App key feature success data   |
| openFileInApp | Helps to identify if user opted to open files outside of Teams versus inside of Teams | Basic | Helps to identify if user opted to open files outside of Teams versus inside of Teams | App key feature success data   |
| uploadSelectedFile | <ul><li>Tracks if user can upload files in channel successfully</li><li>Tracks if user can upload files in chat successfully</li><li>Tracks if user can upload files in the reply window</li><li>Tracks if user can upload files successfully in group chat</li><li>Tracking usage of core scenario</li><li>Tracks the start of upload scenario in channel</li><li>Tracks the start of upload scenario in chat</li><li>Tracks the start of end of upload scenario in channel</li><li>Track if user can upload file into files tab successfully</li><li>Helps to identify is user acted on the prompt during file upload</li><li>Helps to identify if user can upload selected file successfully</li></ul> | Basic/Full | <ul><li>Tracks if user can upload files in channel successfully</li><li>Tracks if user can upload files in chat successfully</li><li>Tracks if user can upload files in the reply window</li><li>Tracks if user can upload files successfully in group chat</li><li>Tracking usage of core scenario</li><li>Tracks the start of upload scenario in channel</li><li>Tracks the start of upload scenario in chat</li><li>Tracks the start of end of upload scenario in channel</li><li>Track if user can upload file into files tab successfully</li><li>Helps to identify is user acted on the prompt during file upload</li><li>Helps to identify if user can upload selected file successfully</li></ul> | App key feature success data   |
| uploadSelectFile | <ul><li>Tracks if the user can select file successfully</li><li>Tracks if the user can select upload file button successfully</li></ul> | Basic | <ul><li>Tracks if the user can select file successfully</li><li>Tracks if the user can select upload file button successfully</li></ul> | App key feature success data   |
| files |     |     |     |     |
| navFiles |     |     |     |     |
| navFilesTab |     |     |     |     |
| navPersonalFiles |     |     |     |     |
| fileSelected | <ul><li>User picks a PowerPoint presentation</li><li>Tracks if the user can select file successfully</li></ul> | Basic | Tracks if the user can select a file successfully | App key feature success data   |
| shareFile | <ul><li>User clicks **Share file**</li><li>Helps to check if user was able to initiate share file operation</li><li>Helps to track if user can share a file successfully</li></ul> | Basic | <ul><li>Helps to check if user was able to initiate share file operation</li><li>Helps to track if user can share a file successfully</li></ul> | App key feature success data   |

### MCM

| Action_Scenario | Description | Type | How the event is used | Basic Subtype |
|-----------------|-------------|------|-----------------------|---------------|
| backFromCallMePSTN | User does not complete the call Me back PSTN number flow | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callInProgressShown | ***Call in progress** banner shown | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callMePSTNConnected | **Call me** is successful | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpAddParticipantsDone | User finalizes their participant addition | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpAutoReconnect | Poor network causes users device to go into Autoreconnect mode | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpMuteParticipant | User mutes a remote participant | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callsTabNewCall | User selects **New Call** in the **Calls** tab | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callTransfer | User starts a call transfer | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialIn | User chooses to Dial in into a meeting (various locations) | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| endPSTNCallSelected | User ends a PSTN and a Content call | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| endPSTNCallShown | User is prompted to end a PSTN or a Content call | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| groupCallJoin | User joins a Group call | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| joinOptionsEdu | EDU user selects options to join a scheduled meeting and is shown the proper options | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| joinViaCode | User joins a meeting via a code | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| liveEventJoin | User joins a live event | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingJoinNowWithCallMe | User joins a meeting with **Call me** | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingJoinNowWithPSTN | User joins a meeting with Dial in | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| navCallingSettings | User navigates to the Calling Settings | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| navVoicemail | User navigates to the voicemail page | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| notificationNavPreCall | User gets a notification of a meeting starts that navigates them to the precall screen on click | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinDenied | User unable to join a meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinDialInCall | User confirms **DIal in** request on prejoin | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinDialInCancel | User cancels **Dial in** request on prejoin | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinDialOutCall | User confirms **Call me back** request on prejoin | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinDialOutCancel | User cancels **Call me back** request on prejoin | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| structuredMeetingsBannerDismiss | User dismisses banner that informs them about their meeting role | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| userJoinedViaShareLink | User joined a meeting from a link | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| activityChatClicked | Non-live chat tapped in Activity tab or split view shown | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| activityLiveChatClicked | Chat clicked from live meeting on the Activity tab | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| activityLiveDetailsClicked | Details clicked from live meeting on the Activity tab | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| admitAll | Number of times user clicks on admit all button from lobby section | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| admitParticipant | Number of times user admits someone into meeting from roster | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingJoin | User clicked **Join meeting** on anonymous join provide name page or tapped **OK** in the name dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingJoinWelcome | Clicked on **Join as guest** on anonymous join meeting landing page | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingPostMeetingChat | Number of user views chat from call end screen | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingPostMeetingRejoin | Number of times anonymous user tries to rejoin meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingSignIn | Number of times user navigated to sign-in from name input screen | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingSignInWelcome | Clicked on **Sign in and join** on anonymous join meeting landing page | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingToggleMuted | Number of times mute toggle button was clicked | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| anonymousMeetingToggleVideo | Number of times video toggle button was clicked | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| audioOnlyLowBatteryBanner | User taps **Audio only** for low battery banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| audioOnlyPoorNetworkBanner | User taps **Video off** for poor connection banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| audioUserDoubleTap | Double tap on an audio participant | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| autoReconnectCallmebackCallDrop | Number of times user clicked on **Callmeback** button at Call end screen | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| autoReconnectDialIn | <ul><li>User clicks the **Dial in** button on the reconnect UFD</li><li>Number of times user clicked on DialIn button while reconnect is happening</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| autoReconnectDialInonCallDrop | User clicks the **Dial in** button on the call disconnected UFD | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| autoReconnectDialOut | User clicks the **Call me back** button on the reconnect UFD | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| autoReconnectRejoinonCallDrop | Number of times user clicked on **Rejoin** or **Redial** button at Call end screen | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| backToPhotoShare | Back to camera | Basic | Used to track feature success orfailure of a feature and customer engagement | App key feature success data   |
| backToStageFromWhiteboard | Going back to call screen from whiteboard | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| backToWhiteboardFromStage | Going to whiteboard from call screen | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| blockAnonymous | <ul><li>User enables calling setting to block calls without caller id from settings</li><li>User disables calling setting to block calls without caller id from settings</li><li>User enables calling setting to block calls without caller id from action sheet</li><li>User disables calling setting to block calls without caller id from action sheet</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| blockCaller | <ul><li>Block number and contact from the new iOS calls action sheet</li><li>Block contact and number from the contact card</li><li>Block numbers from settings | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| BYOELiveEventJoin | BYOE live event is joined by user | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| calendarLiveChatClicked | Chat from live meeting on the Schedule tab | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| calendarMeetingJoin | **Meeting Join** button tapped from Calendar | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| calendarUpcomingChatClicked | Chat from upcoming meeting on the Schedule tab | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callAccepted | Call accepted | | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callAcceptedSFB | Call accepted  | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callAppPreference | Preferred Calling App is selected | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callControlsManualDismiss | Call controls are dismissed manually (user action) | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callControlsManualInvoke | Call controls are invoked manually (user action) | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callHistoryItemExpand | Call History Item expanded | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callHistoryTab | CallHistoryTab selected in Calls | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpAddParticipants | <ul><li>Add participant button tapped on 1:1 call screen</li><li>Select Person (VoIP) in Add participants</li><li>Select PSTN in Add participants</li><li>Add people in live Private meeting</li><li>Select PSTN in live Private meeting</li><li>Select Company contact in live Private Meeting</li><li>Select Device contact in live Private Meeting</li><li>Add Participants Done in Private Live Meeting</li><li>Add people in live Channel Meeting</li><li>Select PSTN in Live Channel Meeting</li><li>Select Team Member in live channel meeting</li><li>Select Device contact in live channel meeting</li><li>Add Participants Done in live channel Meeting</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpAddRoom | <ul><li>User taps **Add room** in roster</li><li>User selects a search result in add room</li><li>User taps **Dismiss** for Nearby</li><li>User taps **Enable BT** or **Location** for Nearby</li><li>User selects a nearby room result in add room</li><li>User selects a suggested room result in add room</li><li>User taps **Done** in add room</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpAudioOffSwitch | Flip **Audio off** button while in companion join mode in live call or meetup | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpCallAccepted | <ul><li>Call accepted</li><li>PSTN Call Accepted</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpCallEnded | <ul><li>**End call** button tapped</li><li>**Call ended** button tapped while in callOrMeetupLive</li><li>**Call ended** button tapped while in lockScreen</li><li>**Call ended** button tapped while in notification</li><li>**Call ended** button tapped while in inApp</li><li>**Call ended** button tapped while in callKit</li><li>**Call Ended** button for PSTN tapped</li></ul> | No data collected/Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpChatWithParticipants | Chat toggle while in live meeting or call | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpDeviceAudioSwitch | <ul><li>Switch audio source to speaker</li><li>Switch audio source to device</li><li>Switch audio source to Bluetooth</li><li>Switch audio source to audio off</li><li>Switch speaker while in live meeting or a call</li><li>Switch speaker to Audio off while in live meeting or a call</li><li>Flip Audio off button while in companion join mode in live call or meetup</li><li>Device Audio Switch while in PSTN</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpEnterDriveMode | Switches manually to drive mode from **...** menu | No data collected | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetupExitDriveMode | **Exit drive mode** button tapped | No data collected | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpHold | <ul><li>**Hold** button tapped while in live meeting or a call</li><li>Call Hold in PSTN</li></ul> | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpIncomingVideoSwitch | Turn off IncomingVideo while in live meeting or a call | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpInvitedParticipants | <ul><li>Clicked **See all** at the bottom of an **Others invited** participant group during private live meeting</li><li>Clicked **See all** at the bottom of an **Others invited** participant group during live channel meeting</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpJoinedParticipants | <ul><li>Clicked **See all** at the bottom of an **In the meeting** participant group during private live meeting</li><li>Clicked **See all** at the bottom of an **In the meeting** participant group during live channel meeting</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpLobbyParticipants | <ul><li>Clicked **See all** at the bottom of a **Lobby** participant group during private live meeting</li><li>Clicked **See all** at the bottom of a **Lobby** participant group during live channel meeting</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpMicrophoneSwitch | <ul><li>Switch Microphone on</li><li>Switch Microphone off</li><li>Microphone button tapped while in live meeting or a call</li><li>Microphone switch while in PSTN</li></ul> | No data collected/Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpMuteParticipants | Mute all participants while in live meeting or a call | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpParticipants | Participants toggle while in live meeting or a call | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpRemoteMuteUFD | You have been muted UFD | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpResume | <ul><li>**Resume** button tapped while in live meeting or a call</li><li>Call Resume in PSTN</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpSearchParticipants | <ul><li>Clicked **Search** in meeting participants during private live meeting </li><li>Clicked **Search** after viewing the **Lobby** participant group during private meeting</li><li>Clicked **Search** after viewing the **In the meeting** participant group during private meeting</li><li>Clicked **Search** after viewing the **Others invited** participant group during private meeting</li><li>Clicked **Search** in meeting participants during a live channel meeting</li><li>Clicked **Search** after viewing the **Lobby** participant group during a live channel meeting</li><li>Clicked **Search** after viewing the **In the meeting** participant group during a live channel meeting</li><li>Clicked **Search** after viewing the **Others invited** participant group during a live channel meeting</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callOrMeetUpVideoSwitch | <ul><li>Switch Video on</li><li>Switch Video off</li><li>Video button tapped while in live meeting/call</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callPark | <ul><li>User taps **Park Call** in **…** menu</li><li>User taps **Retrieve** button</li><li>User taps **Pickup** in retrieve dialog</li><li>User taps **Cancel** in retrieve dialog</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callPreferenceSetting | Call Preference App Setting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| callVoicemailTab | VoicemailTab selected in Calls | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| cameraPermissionCancel | User taps cancel on camera permission dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| cameraPermissionGoToSettings | User navigates to settings from camera permissions dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| cancelFileShare | User clicks **Cancel** on the confirmation dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| cancelFileUpload | User clicks **x** on the upload dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| chatCancelAudioCall | Cancel a group audio call - Confirm dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| chatCancelVideoCall | Cancel a group video call - Confirm dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| chatStartAudioCall | <ul><li>1:1 audio call button tapped</li><li>Taps **Audio** button on search result</li><li>Taps **Start Call** button on right</li><li>1:1 audio call tapped from callHistory item</li><li>1:1 audio call tapped from voicemail item</li><li>Place a group audio call - Confirm dialog</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| chatStartAudioCallOnBehalfOf | Delegate starts call from action sheet as Boss | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| chatStartAudioCallOnBehalfOfMyself | Delegate starts call from action sheet as Myself| Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| chatStartAudioCallSFB | 1:1 audio call button tapped | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| chatStartVideoCall | <ul><li>1:1 video call button tapped</li><li>Taps video button on search result</li><li>1:1 video call tapped from callHistory item</li><li>Place a group video call - Confirm dialog</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| chatStartVideoCallSFB | 1:1 video call button tapped | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| closeLobbyBanner | Number of times user closes lobby toast using its **Close** button | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| companionBannerJoin | Click join on the top-level banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| companionDismiss | Dismiss Companion Banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| companionDismissProximity | Dismiss Companion Banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| companionJoin | Join as companion option is clicked on the sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| companionJoinProximity | Joined through companion banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| confirmAudioOn | User confirms that they want an audio on | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| confirmFileShare | User clicks **Share** on the confirmation dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| consultTransfer | <ul><li>Taps **Transfer** > **Consult first**</li><li>Transfer target set to Person</li><li>Transfer target set to Phone Number</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| consultTransferCall | <ul><li>Initiate consult call</li><li>Confirm transfer dialog - confirm</li><li>Confirm transfer dialog - cancel</li><li>Banner transfer button</li><li>Banner resume button</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| consultTransferChat | <ul><li>Initiate consult chat</li><li>Confirm transfer dialog - confirm</li><li>Confirm transfer dialog - cancel<.li><li>Banner transfer button / Banner resume button</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| contactOrganizer | Clicked **Contact organizer** | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| crossCloudDialogCancel | User clicks **Cancel** on a cross-cloud dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| crossCloudDialogJoin | User clicks **Join as guest** for a cross-cloud dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| deleteVoicemail | Delete voicemail item tapped | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| demotedToAttendee | User demotes a presenter - **Change** button in the dialog box | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| denyParticipant | Number of times user denies someone entry from the roster | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| detailsTabClicked | **Details** tab is clicked on the meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialInBadNetworkBanner | User taps **Dial in** for poor connection banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialInBadNetworkBannerCancel | User cancels the **Dial in** on the native dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialInBadNetworkBannerConfirm | User confirms the **Dial in** on the native dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialInCall | User clicks **Call** on the **Dial in** pop-up | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialInCancel | User clicks **Cancel** on the **Dial in** pop-up | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialOutCall | <ul><li>Join in Drive mode</li><li>User clicks **Call** on the **Call me back** pop-up</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialOutCallAAD | User clicks any number from **My numbers** in action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialOutCallRecent | User clicks any number from previous recent numbers in the action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialOutCancel | User clicks **Cancel** on the **Call me back** pop-up | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialOutDialog | User clicks **New number** in action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dialOutFailRetry | User clicks retry from failure banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| DialPad | DialPad button tapped from call List | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| disableCategory | <ul><li>Disable a type of notification</li><li>Disable incoming call notifications</li></ul> | Basic | Used to track success or failure of a feature and customer engagement | App key feature success data   |
| Dismiss_earlycancelledCQF | User dismissed the CQF early cancelled call form | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| Dismiss_ratemycallCQF | User Dismisses the CQF rate my call form | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| Dismiss_ratemyliveeventCQF | User Dismisses the CQF rate my live event form | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dismissBadNetworkBanner | User taps **Dismiss** for poor connection banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dismissStartRecording | Dismiss error when starting recording | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dismissStopRecording | Dismiss error when stopping recording | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dismissUseWifiForVideoBanner | <ul><li>User dismisses banner that tells the user that remote participant video is blocked and users has to switch to Wifi to see it.</li><li>User dismisses banner that tells the user that users has to switch to Wifi to share video</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| dtmfPSTNCall | DTMF button on DialPad tapped | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| editMeetingResponse | Edit meeting response from meeting detail page | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| emergencyCall | Emergency Call placed calling plan | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| emergencyCallDirectRouting | Emergency Call placed direct routing | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| emergencyCallLocationPolicyBased | DialEmergency using DialPad | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| emergencycallSecurityDeskNotify | Emergency Call placed, security desk informed | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| enabled/disabled | Calling permissions or contact permissions (Android only) |     | Used to track feature success or failure of a feature and customer engagement |     |
| endFileShare | User clicks **Go back** on file sharing dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| endPhotoShare | X out from Photo share | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| endVideoShare | X out from Video share | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| expand/collapse | Device contacts or company contacts section | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| fillFrameVideo | Fill frame from action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| fitToFrameVideo | Fit to frame from action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| flipCamera | Flip camera | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| handoffComplete | Meeting or call got handed off on this device | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| handoffJoin | Meeting hand-off option is clicked on the action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| hardwareAudioOff | Turn audio off through the hardware buttons | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| hardwareAudioOn | Turn audio on through the hardware buttons | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| immediateCallForward | <ul><li>Immediate call forward target is set</li><li>Enable immediate call forwarding (Calls ring me is disabled)</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| inCallDialOut | User clicks the **Call me back** button from in-call more options | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| initiatePhotoShare | Initiate photo share | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| initiateVideoShare | Initiate video share | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| invisionWhiteboardClicked | <ul><li>Invision whiteboard is clicked on channel files tab</li><li>Invision whiteboard is clicked on meeting chat files tab</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| joinFromDeeplinkInTeams | User joined through a deeplink from within the Teams app | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| joinFromDeeplinkOutsideTeams | User joined through a deeplink from outside the Teams app | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| joinFromJoinLauncher | User joined from a Join Launcher | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| joinFromNudge | User joined from nudge | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| joinFromStore | User joined after downloading the app from the app store | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| liveCaptions | <ul><li>User turns on live captions</li><li>User turns off live captions</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| liveEventAdditonalLink | Additional link is clicked | Basic | Used to track feature success/ or failure of a feature and customer engagement | App key feature success data   |
| liveEventInfo | Info button is clicked | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| liveEventLeave | Leave button is pressed | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| liveEventPresenterJoin | Live event is joined by presenter | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| liveEventPresenterJoinAsAttendee | Live event presenter joined as attendee | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| liveEventQnA | Q&A icon is clicked | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| liveEventYammer | Yammer icon is clicked | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| liveMeetingPushNotificationClicked | Push notification clicked | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| liveMeetingToastClicked | In-app toast clicked | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| lobbyPickAudio | Number of times user switches audio output from lobby | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| lobbyToggleMuted | Number of times user turned mic on or off from lobby | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| lobbyToggleVideo | Number of times user turned video on or off from lobby | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| manageBlockedNumbers | Access blocked numbers through Settings | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| maskCallerId | <ul><li>User enables calling setting to mask caller id</li><li>user disables calling setting to mask caller id</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingDetailChatWithParticipants | Chat with participants from Meeting Detail page | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingDetailDeleteMeetingforSelf | Delete Meeting from Meeting Detail page for yourself | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingDetailJoin | Meeting Join button tapped from Meeting Detail page | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingDetailParticipants | See all participants from Meeting Detail page | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingDetailSearchParticipants | Clicked **Search** in meeting participants on meeting schedule | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingJoinLeave | Leave tapped -> **x** is tapped after **Join** button is tapped | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingJoinNow | **Join now for VOIP** tapped | NSD |     |     |
| meetingLeaveChat | Leave chat | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingMuteChat | Mute chat | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingNotesCreatedInChatLink | <ul><li>User clicks on the **Meeting notes created** chicklet in private meeting chat</li><li>User clicks on the **Meeting notes created** chicklet in channel meeting chat</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingNotesMentionCharLink | User clicks on the @mention link in private meeting chat | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingNotesMentionChatLink | User clicks on the @mention link in channel meeting chat | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingNotesTabEntryPoint | <ul><li>User clicks on Meeting notes tab in private meeting</li><li>User clicks on Meeting notes tab in a channel</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingNotificationSettingsAccepted | Notification settings was changed to Accepted only | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingNotificationSettingsAll | Notification settings was changed to All | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingNotificationSettingsNone | Notification settings was changed to None | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingSeeParticipantsChatDetails | See all participants | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingUserAnonB2B | Anonymous B2B joined the meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingUserAnonB2C | Anonymous B2C joined the meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingUserDialIn | PSTN (Dial in) user joined the meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingUserDialOut | PSTN Call me back user joined the meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingUserFederated | Federated user joined the meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingUserFreemium | Freemium user joined the meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingUserGuest | Guest user joined the meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| meetingUserTenant | In-tenant user joined the meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| messageScheduledMeeting | Meeting object in channel tapped (Not only scheduled ones) | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| micPermissionCancel | User taps cancel on mic permission dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| micPermissionGoToSettings | User navigates to settings from mic permissions dialog | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| MicrosoftWhiteboardClicked | <ul><li>Microsoft whiteboard is clicked on Channel Files tab</li><li>Microsoft whiteboard is clicked on Meeting Chat Files tab</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| multiCallEndFromUFD | Number of times user ends the call on hold in a multi-call scenario | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| multiCallResumeFromUFD | Number of times user clicks to resume a call from hold | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| multiCallSwitch | Number of times user clicks to switch the call and list of calls on hold shows up | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| muteOnWhiteboard | User mutes or unmutes on whiteboard screen | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| muteParticipant | Mute participant (move to the action sheet) | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| navCalls | Calls Tab tapped | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| navMeetings | Calendar tab tapped | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| navPhotoTab | Photo tab | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| navVideoTab | Video tab | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| newCall | Taps new call button | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| newCallDialPad | Taps Dialpad button on tab | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| newCallPeople | Taps People button on tab | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| openInStream | Open video in Stream | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| openSettingsSetUpInstructions | Open **Settings** from instructions| Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pauseVoicemail | Pause tapped on voicemail item | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pickGalleryPhoto | pick photo from gallery | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pickParticipantChatDetails | Pick a user from the list | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pickRecentPhoto | Chooses a recent image to share | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pinSelf | Pin myself from action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pinUser | Pin user from action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| play | Play the recording | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| playVoicemail | Play tapped on voicemail item | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pptNextSlide| <ul><li>Next slide as a presenter</li><li>Next slide in private viewing</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pptPreviousSlide | <ul><li>Previous slide as a presenter</li><li>Previous slide in private viewing</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pptReturnToPresenter | Go to the **Live** slide (the one that the presenter and everyone else is on) | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pptStopPresenting | Stop presenting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| pptTakeControl | Take control | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinAddRoom | <ul><li>User clicks the **Add a room** button in pre-join dropdown</li><li>User clicks **Join** in the **Add a room** scenario</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinAudioOff | User clicks the **Audio off** button in pre-join dropdown | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinAutoAddRoom | User tapped **Join now** when room is nearby | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinBack | Back or Close button tapped | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinDeviceAudio | User tapped **Join with device audio** from dropdown | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinDialIn | User clicks the **Dial in** button in pre-join dropdown | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinDialOut | User clicks the **Call me back** button in pre-join dropdown | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| preJoinPSTNOptions | User clicks dropdown for other join options | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| privateMeetingJoin | **Meeting Join** button tapped from Private meeting chat | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| promotedToPresenter | User promotes an attendee - **Change** button in the dialog box | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| proximityPermissionDismissed | Permission banner is dismissed | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| proximityPermissionGranted | Permission is given on the pop-up | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| proximityPermissionViewed | Permission banner is tapped | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| quickStartLiveEventJoin | Quick start live event is joined by user | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| runningLate | I am running late | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| scheduledMeetingJoin | **Meeting Join** button tapped from scheduled meeting object | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| searchContacts | Search from Call List | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| selection | <ul><li>Device contact selected</li><li>Company contact selected</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| selectMeetingChicklet | Meeting |     | Used to track feature success or failure of a feature and customer engagement |     |
| selfLongPress | Long press on myself | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| Send_earlycancelledCQF | User Submits feedback on CQF early cancelled call form | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| Send_ratemycallCQF | User Submits feedback on CQF rate my call form | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| Send_ratemyliveeventCQF | User Submits feedback on CQF rate my live event form | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| Setting/Dismiss | Device contacts setting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| sharePPTFromChannels | User clicks **Teams and Channels** | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| sharePPTFromOneDrive | User clicks **OneDrive** | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| shareRecording | Share recording | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| shareScreen | <ul><li>Start Screen Share</li><li>Stop Screen Share</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| shareTray | User clicks on **Share…** in the action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| simultaneousCallForward | <ul><li>Simultaneous call forward target is set</li><li>Enable simultaneous call forwarding (Calls ring me is enabled & Also ring is set)</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| startPresentPhoto | Start presenting photo | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| startPresentVideo | Start presenting video | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| startPSTNCall | <ul><li>PSTN Result in Global Search (People)</li><li>PSTN call placed from Device contactCard</li><li>PSTN Call placed from callList</li><li>DialPSTN Number using DialPad</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| startRecording | Start recording | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| startVoicemailCall | Change Voicemail Greeting tapped | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| stopMeetingButton | Number of times user leaves the lobby without being admitted into the meeting | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| stopPresentPhoto | Stop presenting photo | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| stopPresentVideo | Stop presenting video | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| stopRecording | Stop recording | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| stuckOnConnectingDialInSelected | User tapped Dial in on the drawer | Basic | Used to track feature success or failure of a feature and customer engagement |     |
| stuckOnConnectingRetrySelected | User tapped retry on the drawer | Basic | Used to track feature success or failure of a feature and customer engagement |     |
| stuckOnConnectingShownDismissed | User dismissed the drawer | Basic | Used to track feature success or failure of a feature and customer engagement |     |
| takePhoto | Take a photo | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| toast | In-app toast clicked | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| transferNow | <ul><li>Taps Transfer > Transfer now</li><li>Transfer target set to Person</li><li>Transfer target set to Phone Number</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| unansweredCallForward | <ul><li>Unanswered call forward target is set</li><li>Enable unanswered call forwarding (Calls ring me is enabled and If unanswered is enabled)</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| unblockCaller | <ul><li>Unblock contact or number from action sheet</li><li>Unblock contact or number from contact card</li><li>Unblock number from settings</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| unpinSelf | Unpin yourself from action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| unpinUser | Unpin user from action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| updatePlaybackSpeedVoicemail | Voicemail playback speed value changed | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| uploadFile | User clicks **Upload from device** | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| userLongPress | Long press on a participant | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| useWifiForAudioDialog | User clicks **OK** while system prompts that while Admin has blocked audio and video calls on cellular | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| useWifiForVideoDialog | <ul><li>User clicks **OK** while system prompts that while Admin has blocked video calls on cellular</li><li>User trying to enable video in meeting while Admin has blocked it on cellular</li><li>User clicks **OK** while system prompts that while Admin has blocked video in meetings on cellular</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| videoUserDoubleTap | Double tap on a video participant | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| viewContactCard | <ul><li>ContactCard tapped from callHistory item</li><li>ContactCard tapped from voicemail item</li><li>ContactCard click from call list</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| viewLobbyFromBanner | Number of times user clicks on view lobby from notification banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| voiceDataCollectionOptOut | User opts-out of the recording from mobile by clicking the banner | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| Voicemail - No AS Assigned | Speaker tapped on voicemail item | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| whiteboardUsed | User annotates on whiteboard (any action on the webview) | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |

### Mobile platform

| Action_Scenario | Description | Type | How the event is used | Basic Subtype |
|-----------------|-------------|------|-----------------------|---------------|
| addToCalendar   |             |      |                       |               |
| addToMeeting    |             |      |                       |               |
| calendarTab | Click on the **Meetings** tab in the bottom rail | Basic | <ul><li>To understand the calendar usage and compare with other apps on the bottom rail</li><li> To determine if there was a failure in rendering the calendar post click from the bottom bar</li></ul> | App key feature success data   |
| calendarTabClicked | <ul><li>Schedule tab shown</li><li>Click on the **Meetings** tab in the bottom rail</li></ul> | Basic | <ul><li>To understand calendar usage and compare with other navbar apps on the bottom rail</li><li>To determine if there was a failure | App key feature success data   |
| cancelEditMeeting | Click on the **Close** button while on the meeting scheduler page, after clicking **Edit meeting** | Basic | To log abandoned edit meeting clicks | App key feature success data   |
| cancelMeeting | Click on **Cancel event** from the meeting details page | Basic | To get aggregated data on the number of cancelled meetings | App key feature success data   |
| cancelNewMeeting | <ul><li>Click on the **Close** button while on meeting scheduler page</li><li>Click on the **Close** button while on meeting scheduler page after clicking **Edit meeting**  | Basic | To log abandoned Create meeting clicks and verify what caused them | App key feature success data   |
| chatWithMeetingParticipants | Clicks on **Chat** tab from Meeting Details page | Basic | To understand the usage of Chats as an entry point from the Meeting Details page | App key feature success data   |
| deleteMeeting | Click on the **Delete** button from the Meeting Details page | Basic  | To get aggregated data on the number of deleted meetings | App key feature success data   |
| editRsvpMeetingOptions | Click on **RSVP** to change from the previous selection | Basic  |     | App key feature success data   |
| meetingDetailCalendarList | <ul><li>Meeting Details page tapped from calendarList</li><li>Click on **Details** tab on the Meeting Details page | Basic | Telemetry to log user data across the calendar funnel, where calendar meeting details play an important role, that helps validate clicks on Dial ins, Teams meetings, RSVP clicks, etc.. | App key feature success data   |
| meetingDetailScheduledMeeting | <ul><li>Meeting details page tapped from scheduled meeting object (**…**)</li><li>Click on the **Details** tab of a scheduled meeting | Basic | Telemetry to log user data across the calendar funnel, where calendar meeting details play an important role, that helps validate clicks on Dial ins, Teams meetings, RSVP clicks, etc.. | App key feature success data   |
| openEditMeetingForm | Click on the **Edit** button from the Meeting Details page | Basic  | To log whether edit meeting clicks were successful or not | App key feature success data   |
| openMeetingDetails | Open the meeting details or the Open Meeting details page of a particular meeting | Basic  | Telemetry to log user data across the calendar funnel, where calendar meeting details play an important role, that helps validate clicks on Dial ins, Teams meetings, RSVP clicks, etc.. | App key feature success data   |
| openNewMeetingForm | Open the scheduler while setting up a new meeting | Basic  | To understand the number of meetings created from mobile and compare popularity with other clients for meetig creation | App key feature success data   |
| refreshCalendarList | Pul down to refresh agenda view | Basic | To check if the Agenda view has been refreshed | App key feature success data   |
| removeMeeting | Click on **Remove from Calendar** from the Meeting Details page of a cancelled meeting | Basic | To get a sense of aggregated data of unwanted meetings being pushed on to personal calendars | App key feature success data   |
| removeParticipantFromEditMeeting | Remove a participant after clicking on **Edit meeting** from the Meeting Details page | Basic | To log if an added participant was succesfully removed or not | App key feature success data   |
| removeParticipantFromNewMeeting | Remove a participant from the scheduler page while setting up a new meeting | Basic | To log if an added participant was succesfully removed or not | App key feature success data   |
| saveEditMeeting | Click on the **Save** button while on the meeting scheduler page after updating a meeting | Basic | To log succesfully saved meetings or those that  failed to update | App key feature success data   |
| saveNewMeeting | Click on the **Save** button while on the meeting scheduler page | Basic | To log succesfully saved meetings and the percentage of meetings that failed to create due to a client side or service error | App key feature success data   |
| searchMeetingParticipants | Search for participants to add within the scheduler form | Basic | To distinguish between the number of appointments created versus the number of meetings created | App key feature success data   |
| seeAllMeetingParticipants | <ul><li>Click on **See All** from the meeting details page</li><li>View all participants</li></ul> | Basic  | Telemetry to log user data across the calendar funnel, where calendar meeting details play an important role, that helps validate clicks on Dial ins, Teams meetings, RSVP clicks, etc.. | App key feature success data   |
| seeMeetingDescription | <ul><li>Opening the Meeting Details page</li><li>Click **See More** on the Meeting description from the Meeting Details page | Basic | Telemetry to log user data across the calendar funnel, where calendar meeting details play an important role, that helps validate clicks on Dial ins, Teams meetings, RSVP clicks, etc.. | App key feature success data   |
| seeRsvpMeetingOptions | <ul><li>Click on **Notify Organizer** from the RSVP pop up</li><li>Click on **Rsvp** options from the Meeting Details page | Basic |     | App key feature success data   |
| selectMeetingRsvpOption | Click on the **RSVP** button to choose an option | Basic |     | App key feature success data   |
| selectMeetingRsvpOptions | Click on the **RSVP** button to choose an option | Basic |     | App key feature success data   |
| viewFullAllDayMeetingList | Agenda view on Mobile | Basic | To log tje popularity of vew tyoe on calendar mobile | App key feature success data   |
| viewMeetingDetails | Click on **...** menu on the Meeting Details page | Basic | Understand the usage of the More menu on calendar mobile | App key feature success data   |
| viewMeetingOccurrence | Open up meeting details of an instance of a recurring meeting | Basic | Telemetry to log user data across the calendar funnel, where calendar meeting details play an important role, that helps validate clicks on Dial ins, Teams meetings, RSVP clicks, etc.. | App key feature success data   |
| navDynamics365  | Event is triggered when the user open the Dynamics365 app | Basic | Provides key success data for app navigation and entrypoint discoverability
 | App key feature success data   |
| navNotes | Event is triggered when the user open the Notes app | Basic | Provides key success data for app navigation and entrypoint discoverability
 | App key feature success data   |
| navOrganization | Event is triggered when the user open the Organization app | Basic | Provides key success data for app navigation and entrypoint discoverability
 | App key feature success data   |
| navOrgChart | Event is triggered when the user open the Orgchart app | Basic | Provides key success data for app navigation and entrypoint discoverability
 | App key feature success data   |
| navTasks | Event is triggered when the user open the Tasks app | Basic | Provides key success data for app navigation and entrypoint discoverability
 | App key feature success data   |
| navWiki | Event is triggered when the user open the Wiki app | Basic | Provides key success data for app navigation and entrypoint discoverability
 | App key feature success data   |
| oneNote | Event is triggered when the user open the OneNote app | Basic | Provides key success data for app navigation and entrypoint discoverability
 | App key feature success data   |
| actionComposeMenu | <ul><li>Create message extension usage</li><li>Action ME usage</li></ul> | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| Android: null | Mute or unmute a bot chat. This is enhancing existing telemetry around chats and is only adding app information. | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| blockChat | Block a bot chat.This is enhancing existing telemetry around chats and is only adding app information. | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| botClickCardAction | Connector card usage | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| CardView - No AS assigned | Card view and card rendering. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side  | Basic | Teams and channels are essential constructs of Teams. This item is required to measure any error with joining a team | App key feature success data   |
| chicletExpand | <ul><li>Understand how users preview cards on mobile</li><li>Understand the preview closure behavior | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| composeSearchResult | <ul><li>Message extension result selection - helpful to understand the app search result relevance</li><li>Enhances message send telemetry with app data</li></ul> | Optional/Basic  | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| composeSelectExtension | Tap on a ME app | Basic | Used to track feature success or failure of a feature and customer engagement | Teams setup and inventory data   |
| composeSendMessage | Enhances message send telemetry with app data | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| createComposeExtension | <ul><li>Create message extension usage</li><li>Action ME usage</li></ul> | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| <ul><li>Expected: atMention</li><li>Android: chatSendMessage</li><li>iOS: sendMsg</li></ul> | @ mention a bot in a compose box | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| <ul><li>Expected: botClickCardAction</li><li>Android: showCard</li><li>iOS: missing</li></ul> | Tap on card buttons. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| <ul><li>Expected: chatSendMessage</li><li>iOS: composeSendMessage | Tap on **Reply** and reply to a bot chat in a channel | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| <ul><li>Expected: composeSendMessage</li><li>Android: replyChannel</li><li>iOS: missing</li></ul> | Tap on **Reply** and reply to a bot chat in a channel | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| <ul><li>Expected: messageLike</li><li>Android: reactLike_CM</li></ul> | Like a bot message | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| <ul><li>Expected: messageUnread</li><li>Android: markAsLastUnread | Message context menu options for a bot message | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| linkPreviewCancel | Understand the preview closure behavior | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| markAsLastUnread | Connector card context menu | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| messageLike | Connector card like. Uses existing telemetry with app specific data | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| openApp | Opening a personal app | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| personalAppNavBotChat | navigate to the bot within personal app | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| personalAppNavTab | Navigate to tabs within personal app | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| showCard | Tap on card buttons. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| tabActionCopyLink | Understand how users discover and use tab copy link on mobile | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| tabActionMoreOptions | Understand ellipsis usage from within a Tab for more option - discoverability & usage | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| tabActionOpenInBrowser | Open in browser usage. This is necessary to understand if users prefer opening tab outside Teams | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| tabActionOpenInBrowserFromTab | Understand open in browser usage from within a Tab for more option - discoverability & usage | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| tabActionOpenInTeams | Open in usage. This is key in understanding if the tab can be by default set to open in Teams | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| tabActionRemove | Understand how discoverable the delete option is and the usage of the feature | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| tabActionRename | Understand how discoverable rename is and the usage of the feature | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| <ul><li>tabActionSetting</li><li>Android - fix</li></ul> | Understand how users discover and use tab config on mobile | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| tabListMoreOptions | Understand the usage of the more options for a tab | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| tabOpen | Tabs are a critical feature for Teams and this will be needed to understand feature success and be ready to see if there are any issues in the way its being used | Basic | Used to track feature success or failure of a feature and customer engagement |     |
| tapChicletExpand | Understand how users preview cards on mobile | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| tapSettings | Understand the number of users re-configuring apps on mobile | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| unblockChat | Unblock a bot chat.This is enhancing existing telemetry around chats and is only adding app information. | Optional | Used to track feature success or failure of a feature and customer engagement |     |

### Mobile platform - Other

| Action_Scenario | Team Owner | Description | Type | How the event is used | Basic Subtype |
|-----------------|------------|-------------|------|-----------------------|---------------|
| OrgChart - No AS assigned | <ul><li>Mobile platform - orgChart</li><li>Mobile platform - wiki</li></ul> | Basic usage telemetry for org chart | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| viewOrgChart | <ul><li>Mobile platform - orgChartQuickActionButton</li><li>Mobile platform - orgChartQuickActionButton</li></ul> | Basic usage telemetry for org chart | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| open edit | Mobile platform - wiki | Wiki usage telemetry - User clicks to edit wiki | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| Wiki - No AS assigned | Mobile platform - wiki | Wiki usage telemetry | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| activityFeedClick | <ul><li>Mobile platform</li><li>Feeds</li></ul> | <ul><li>Tap on an activity feed item and navigate to bot chat</li><li>Captures click information on feed item</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |

### Not applicable

| Action_Scenario         | Description | Type  | How the event is used                                                 | Basic Subtype                  |
|-------------------------|-------------|-------|-----------------------------------------------------------------------|--------------------------------|
| reactRemoved_HB         |             |       |                                                                       |                                |
| teamsDeviceCallResumed  |             | Basic | Used to track success or failure of a feature and customer engagement | App key feature success data   |
| People                  |             |       |                                                                       |                                |
| reportAbuseSend         |             |       |                                                                       |                                |
| reportAbuseConfirmation |             |       |                                                                       |                                |

### Notifications

| Action_Scenario                          | Description                          | Type  | How the event is used  | Basic Subtype                  |
|------------------------------------------|--------------------------------------|-------|------------------------|--------------------------------|
| navActivity                              | Navigate to the activity feeds page  | Basic | Feature success metric | App key feature success data   |
| notificationError                        |                                      |       |                        |                                |
| notificationNavChannelConversation       |                                      |       |                        |                                |
| notificationNavChannelThreadConversation |                                      |       |                        |                                |
| notificationSettingTurnedOff             |                                      |       |                        |                                |
| quickNotificationAction                  |                                      |       |                        |                                |

### People

| Action_Scenario     | Description | Type | How the event is used | Basic Subtype |
|---------------------|-------------|------|-----------------------|---------------|
| deleteContact       |             |      |                       |               |
| editContact         |             |      |                       |               |
| openContactCard     |             |      |                       |               |
| addUserAsContact | User can add a contact by clicking on 'add contact' icon from the profile card of the contact | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| shortCircuitContactCount | This does not belong to the People area ??? | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| addToList | User adds a contact to a contact list | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| navPeopleSettings | This is not being sent in the newer builds |     |     |     |
| navPeople | Event is triggered when the user opens the People app | Basic | Provides key data success for app navigation and entrypoint discoverability | App key feature success data   |
| peoplePickerInvoked |             |      |                       |               |

### Search

| Action_Scenario | Description | Type | How the event is used | Basic Subtype |
|-----------------|-------------|------|-----------------------|---------------|
| searchAbandoned | Helps to track if search was successful versus if user abandoned search | Basic | Helps to track if search was successful vs if user abandoned search | App key feature success data   |
| searchCancelled | <ul><li>Helps to track if search was successful vs if user abandoned search</li><li>Helps to track if search query was successful</li></ul> | Basic | <ul><li>Helps to track if search was successful vs if user abandoned search</li><li>Helps to track if search query was successful</li></ul> | App key feature success data   |
| searchIcon | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li><li>Helps to track if user can find relevant results successfully</li></ul> | Basic | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li><li>Helps to track if user can find relevant results successfully | App key feature success data   |
| searchInitiated | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li></ul> | Basic | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li></ul> | App key feature success data   |
| searchResultsClicked | <ul><li>Helps to track if user can find relevant results successfully</li><li>Tracking usage of core scenario</li><li>Helps to track if search results was from ALL tab vs individual domain</li></ul> | Basic | <ul><li>Helps to track if user can find relevant results successfully</li><li>Tracking usage of core scenario</li><li>Helps to track if search results was from ALL tab vs individual domain</li></ul> | App key feature success data   |
| searchTab | <ul><li>Helps to track domain information of the search result - people/chat/messages/files</li><li>Helps to track if search results was from ALL tab vs individual domain</li></ul> | Basic | <ul><li>Helps to track domain information of the search result - people, chat, messages, files</li><li>Helps to track if search results was from ALL tab versus individual domain</li></ul> | App key feature success data   |
| searchTabClicked | <ul><li>Helps to track domain information of the search result - people/chat/messages/files</li><li>Helps to track if user can find relevant results successfully</li></ul> | Basic | <ul><li>Helps to track domain information of the search result - people, chat, messages, files</li><li>Helps to track if user can find relevant results successfully</li></ul> | App key feature success data   |

### Tasks

| Action_Scenario | Description | Type | How the event is used | Basic Subtype |
|-----------------|-------------|------|-----------------------|---------------|
| createPersonalPlan | A personal list is created, checks list created with ToDo service | Basic | Confirms a new personal task list is created in ToDo | Key App feature success data   |
| createPlannerPlan | A shared list is created, checks list created with Planner service | Basic | Confirms a new shared task list is created in Planner | Key App feature success data   |
| createDefaultPlannerPlan | A shared list is created automatically when the Tasks app is opened for the first time by anyone in that group, checks auto list created with Planner service | Basic | Confirms the default shared task list is successfully created in Planner the first time a user attempts to create a shared task list. | Key App feature success data   |
| sharePlanToChat | A shared list is manually shared from the tasks app to the group chat as a chiclet, check chicklet sent via backend messaging  service | Basic | Confirms that a chiclet is successfully sent to the chat when a task list is shared in a group chat | Key App feature success data   |
| tasksAppLaunchDefault | Tasks app is opened from the bottom drawer, check app launch via MT service | Basic | Confirms that the tasks app is successfully launched from the app bar | Key App feature success data   |
| tasksAppLaunchDashboard | Tasks app is opened from the dashboard tile or specific plan, check app launch via MT service | Basic | Confirms that the tasks app is successfully launched from the dashboard | Key App feature success data   |
| tasksAppLaunchDashboardSeeAll | Tasks app is opened from the dashboard **See all** button, check app launch via MT service | Basic | Confirms that the tasks app is successfully launched from the **See All** button of the dashboard | Key App feature success data   |
| tasksAppLaunchAdaptiveCard | Tasks app is opened from an adaptivecard in a group chat, check app launch via URL of IC3 service | Basic | Confirms that the tasks app is successfully launched by clicking on a chiclet previously sent to the group chat | Key App feature success data   |
| tasksAppLaunchComposeExtension | Tasks app is opened from the compose extension in a group chat, check app launch via MT service | Basic | Confirms that the tasks app is successfully lanuched from a compose extension | Key App feature success data   |
| updateTask | Confirms update tasks action failed | Basic | Confirms that a when a user edited or updated a task failed | Key App feature success data   |
| deleteTask | Verifies with Planner service as to whether a delete action was successful or unsuccessful | Basic | Confirms that a task delete failed, that is, the deletion of a task was unsuccessful | Essential Service - Telemetry   |
| createTask | Used for when create action fails, checks call to Planner service | Basic | Confirms a task create operation failed | Essential Service - Telemetry   |
| updatePersonalTask | Confirms a personal task has been successfully updated | Basic | Confirms a personal task has been successfully updated | Essential Service - Telemetry   |
| deletePersonalTask | Confirms a personal task has been successfully deleted | Basic | Confirms a personal task has been successfully deleted | Essential Service - Telemetry   |
| createPersonalTask | Confirms a personal task has been successfully created | Basic | Confirms a personal task has been successfully created | Essential Service - Telemetry   |
| openNewMeetingForm | Confirms a personal sub-task has been successfully updated | Basic | Confirms a personal sub-task has been successfully updated | Essential Service - Telemetry   |
| deletePersonalSubtask | Confirms a personal sub-task has been successfully deleted | Basic | Confirms a personal sub-task has been successfully deleted | Essential Service - Telemetry   |
| createPersonalSubtask | Confirms a personal sub-task has been successfully created | Basic | Confirms a personal sub-task has been successfully created | Essential Service - Telemetry   |
| updatePlannerTask | Confirms that a user has successfully updated a task in a shared taks list | Basic | Confirms that a user has successfully updated a task in a shared taks list | Essential Service - Telemetry  |
| deletePlannerTask | Confirms that a shared taks delete operation completed succesasfully | Basic | Confirms that a shared taks delete operation completed succesasfully | Essential Service - Telemetry  |
| createPlannerTask | checks call to Planner service | Basic | Confirms that a user has successfully created a task in a shared taks list | Key App feature success data   |
| teamChannelChanged | Triggered when user clicks and navigates to a plan from plan list. Only sent to appInsights, not Aria | Optional |     |     |
| priorityChange | Triggers when priority filter is applied while viewing tasklist | Optional |     |     |
| assigneeChange | Triggers when new assignee is added to a task item | Optional |     |     |
| descriptionChanged | Confirms a task description has changed | Optional | Confirms that a shared task description changed successfully |     |
| createPlan | Confirms that a shared task list has been successfully created | Optional | Confirms that a shared plan has been successfully created through middle tier. |     |
| dueDateSelected | Triggers when user applies a filter by duedate while viewing a tasklist | Optional |     |     |
| dueDateUnselected | Triggers when user unapplies a filter by dueddate while viewing a tasklist | Optional |     |     |
| descriptionClicked | When user clicks to view description from task details | Optional |     |     |
| priorityPickerClicked | Triggers when user navigates to priority filter picker from task list filter screen | Optional |     |     |
| checklistSeeAllClicked | When user clicks the **See All** button inside task details to view all checklist items | Optional |     |     |
| assignmentPickerClicked | When user clicks the **Assign To** button that brings them to assignee picker page | Optional |     |     |
| assignmentRemoved | Triggers when assignee is removed from task item by clicked the **x** (this is the only way to remove an assignee) | Optional |     |     |
| importanceToggleClicked | Triggers when **!** field is toggled inside task item details | Optional |     |     |
| deleteClicked | When user click **Delete** within task details, which brings up the confirmation dialog | Optional |     |     |
| onBackClicked | Whenever a user clicks the back arrow to navigate back a page | Optional |     |     |
| checkListAddClicked | User clicks **Add an item** inside task details view for checklist section | Optional |     |     |
| checkListItemDeleted | User deletes a checklist item from the task | Optional |     |     |
| checkListItemAdded | User creates a checklist item for task | Optional |     |     |
| checkListItemUpdated | User updates a checklist item for task | Optional |     |     |
| titleChanged | Triggers when task item title changes, triggers on every character change | Optional |     |     |
| dueDatePickerClicked | Triggers when user clicks the **Due Date** button in task details, opens the duedate picker page | Optional |     |     |
| dueDateChanged | Triggers when user assigns a duedate to a task | Optional |     |     |
| statusCheckBoxClicked | Triggers when task item is either completed or uncompleted | Optional |     |     |
| moreOptionsClicked | Triggers when **...** menu on the top-right is clicked on the task item editor screen | Optional |     |     |
| moveTaskClicked | Option inside task item more options list | Optional |     |     |
| openInAppClicked | Option inside task item more options list, only available for personal tasks | Optional |     |     |
| sortChanged | Triggers when user changes sort order while viewing a tasklist | Optional |     |     |
| clearFilter | When user clears all filters while viewing a tasklist | Optional |     |     |
| completionStateChange | Triggers when completed/uncompleted filter toggle is clicked in filter view from task list | Optional |     |     |
| removeAssignee | Confirms that an assignee is removed from the assignment picker view (as opposed to *assignmentRemoved* which triggers when clicking **x** outside of assignment picker view) | Optional | Confirms that an assignee is removed from  assignment picker view |     |
| removeUser | Confirms that an assignee is removed from within assignment picker view (as opposed to *assignmentRemoved* which triggers when clicking **x** outside of assignment picker view) | Optional | Confirms that an assignee is removed from within assignment picker view |     |
| savePlanClicked | Trigger when user cliks **Create** in the new plan creator from default opening of app | Optional |     |     |
| navSelectPlan | When a user selects a shared plan to navigate to from home view | Optional |     |     |
| navSelectPersonalList | When a user selects a personal plan to navigate to from home view | Optional |     |     |
| navSelectSmartList | When a user selects a smart plan to navigate to from home view| Optional |     |     |
| createTaskList | When user navigates to the create plan view from home view | Optional |     |     |
| updateTaskState | Confirms that the task state has been updated | Optional | Confirms that the task state has been successfully updated |     |
| channelPickerClicked | Confirms that the channel picker successfully launched | Optional | Confirms that the channel picker successfully launched. |     |
| datePickerLaunch | Confirms that date picker was successfully launched | Optional | Confirms that the date picker was successfully launched |     |
| labelSelected | Confirms that a label has been successfully selected | Optional | Confirms that a label was successfully selected |     |
| labelUnselected | Confirms that a label has been successfully unselected | Optional | Confirms that a label has been successfully unselected |     |
| bucketSelected | Confirms that a bucket has been successfully selected | Optional | Confirms that a bucket has been successfully selected |     |
| bucketUnselected | Confirms that a bucket has been successfully unselected | Optional | Confirms that a bucket has been successfully unselected |     |
| bucketPickerClicked | Confirms that the bucket picker successfully launched | Optional | Confirms that the bucket picker successfully launched |     |
| labelPickerClicked | Confirms that the label picker successfully launched | Optional | Confirms that the label picker successfully launched |     |
| commentsClicked | Confirms that the comments view was  successfully launched | Optional | Confirms that the comments view was  successfully launched |     |
| attachmentAdded | Confirms that an attachment in a task was successfully added | Optional | Confirms that an attachment in a task was successfully added |     |
| attachmentDeleted | Confirms that an attachment in a task was successfully deleted | Optional | Confirms that an attachment in a task was successfully deleted |     |
| attachmentUpdated | Confirms that an attachment in a task was successfully updated | Optional | Confirms that an attachment in a task was successfully updated |     |
| selectUser | Confirms that an assignee was successfully selected for a task | Optional | Confirms that an assignee was successfully selected for a task |     |
| channelSelected | Confirms that a channel was successfully selected for a new plan | Optional | Confirms that a channel was successfully selected for a new plan |     |
| selectPlannerList | Confirms that the user successfully navigated to a shared task list by tapping it | Optional | Confirms that the user successfully navigated to a shared task list by tapping it |     |
| selectPersonalList | Confirms that the user successfully navigated to a personal task list by tapping it | Optional | Confirms that the user successfully navigated to a personal task list by tapping it |     |
| commentAdded | Confirms that a comment was added to a task | Optional | Confirms that a comment was added to a task |     |
| commentUpdated | Confirms that a comments was successfully updated on a task | Optional | Confirms that a comments was successfully updated on a task |     |
| progressItemClicked | Confirms a user has successfully opened the progress picker for a task | Optional | Confirms a user has successfully opened the progress picker for a task |     |

### Teams FLW

| Action_Scenario                   | Description | Type | How the event is used | Basic Subtype |
|-----------------------------------|-------------|------|-----------------------|---------------|
| group_map_open                    |             |      |                       |               |
| group_map_closed                  |             |      |                       |               |
| location_data_use_privacy_granted |             |      |                       |               |
| location_data_use_privacy_denied  |             |      |                       |               |
| location_settings_open            |             |      |                       |               |
| location_sharing_start            |             |      |                       |               |
| location_sharing_stop             |             |      |                       |               |
| parental_consent_grant            |             |      |                       |               |
| parental_consent_remove           |             |      |                       |               |
| active_session_banner_dismissed   |             |      |                       |               |
| brbFeedback                       |             |      |                       |               |
| brbFormCancelled                  |             |      |                       |               |
| brbFormOpened                     |             |      |                       |               |
| brbFormSubmit                     |             |      |                       |               |
| ocvFeedback                       |             |      |                       |               |
| ocvFormCancelled                  |             |      |                       |               |
| ocvFormOpened                     |             |      |                       |               |
| ocvFormSubmit                     |             |      |                       |               |
| navShifts                         |             |      |                       |               |
| navWalkieTalkie                   |             |      |                       |               |

### Teams FLW Android Production

| Action_Scenario | Description | Type | How the event is used | Basic Subtype |
|-----------------|-------------|------|-----------------------|---------------|
| AccessibilityUserConfiguration | When a FLW Manager approves a FLW request to take time off. | Basic | To toggle if this is an accessible feature. | App key feature success data   |
| Viewed | User was unable to login. | Basic | Key functionality for schedule feature. | App key feature success data   |
| ErrorShown | Teams FLW Android Prod | User saves the day availability. | Basic | Key functionality for error shown. | App high value activity error data   |
| CreateShiftOrTimeOffClicked | This is to track if you clicked create a shift or time off clicked | Basic | Key functionality for time off feature. | App key feature success data   |
| TimeOffReasonClicked | This it to track if you cited a reason for time off. | Basic | Key functionality for time off feature. | App key feature success data   |
| RequestSent | This is to log if there was a request sent. | Basic | Key functionality for request feature. | App key feature success data   |
| ShiftDetailsTodaysCoworkers | On the clock in screen, user clicks on Start or End break button. | Basic | Key functionality for shifts details feature | App key feature success data   |

### Teams FLW iOS Prod and Teams FLW Android Production

| Action_Scenario | Description | Type | How the event is used | Basic Subtype |
|-----------------|-------------|------|-----------------------|---------------|
| PageEntered | User was able to login. | Basic | Key functionality for shifts details feature | App key feature success data   |
| DateChanged | Register user's break start or end. This will not trigger until you have checked the location assuming location is required. | Basic | Key functionality for datechanged feature. | App key feature success data   |
| ShiftDetailsCalendar | On the clock in screen, user clicks on the **Clock In** or **Clock Out** button. | Basic | Key functionality for calendar feature. | App key feature success data   |
| OfferSwapShiftFromL1Triggered | Register user's clock in or out. This will not trigger until you have checked the location assuming location is required. | Basic | Key functionality for requests feature. | App key feature success data   |
| PlusButtonClicked | Triggered when the user closes the banner message of a notification. | Basic | Key functionality for requests feature. | App key feature success data   |
| ToggleClicked | To view a declined time off request. | Basic | Key functionality for shifts reminder feature | App key feature success data   |
| ClosedBannerMessage | Triggered when the user closes the banner message of a notification. | Basic | Key functionality for timezone feature. | App key feature success data   |
| MessageTriggered | This is when a notification is triggered for a message. | Basic | Key functionality for timezone feature. | App key feature success data   |
| ShiftDetails | This is to see the details of the shift. | Basic | Key functionality for request feature. | App key feature success data   |
| RequestTypeClicked | Tracking what type of request people select from the requests picker | Basic | Key functionality for request feature. | App key feature success data   |
| SendRequestClicked | This instrumentation is logged for every individual request | Basic | Key functionality for request feature. | App key feature success data   |
| DayClicked | Clicking the day view when user is seeing their Shifts | Basic | Key functionality for day clicked feature. | App key feature success data   |
| DaySaved | This is to save a day of shifts. | Basic | Key functionality for create shift feature. | App key feature success data   |
| GroupClicked | Tracks when a user clicks on the group of the shift | Basic | Key functionality for group clicked feature. | App key feature success data   |
| ShareShiftsClicked | The details of an open shift. | Basic  | Key functionality for share shifts feature. | App key feature success data   |
| RequestTypeClicked | Tracking what type of request people select from the requests picker | Basic | Key functionality for request type feature. | App key feature success data   |
| RequestDetailsClicked | When the request for a shift is clicked (either FLW manager viewing or FLW worker) | Basic | Key functionality for request feature. | App key feature success data   |
| MyShiftPickerClicked | Only logged if request being sent is a swap or offer. Tracking user clicks into **My Shift** picker. | Basic | Key functionality for shift picker feature. | App key feature success data   |
| TeamShiftPickerClicked | When the user adds a new break entry. Log the event once the user saves the changes | Basic | Key functionality for shift picker feature. | App key feature success data   |
| OfferRecipientClicked | Only logged if request being sent is an offer. Tracking user clicks into the team member picker to offer a shift to. Offering means offering a shift time off. | Basic | Key functionality for offer feature | App key feature success data   |
| TeamSelectedClicked | When the user clicks on **Add** on a timesheet | Basic | Key functionality for team selected feature. | App key feature success data   |
| SendRequestBulkClicked | This instrumentation point is logged once for each bulk request send. In addition, each individual request will log an event. | Basic | Key functionality for request bulk feature. | App key feature success data   |
| ApproveTimeOffRequest | When an  FLW Manager approves a FLW request to take time off. | Basic | Key functionality of Time Off requests. | App key feature success data   |
| BadUrlLoginFailed | User was unable to login. | Basic | If a user was unable to login. | Crash data – Unexpected app exit data   |
| BadUrlLoginSuccess | User was able to login. | Basic | If a user was able to login. | App key feature performance data   |
| BreakStartEndClicked | On the clock ins creen, user clicks on **Start** or **End break** button. | Basic | Key functionality for an FLW requesting a break. | App key feature success data   |
| BreakStartEndTriggered | Register user's break start or end. This will not trigger until you have checked the location assuming location is required. | Basic | Key functionality for break feature within Shifts. | App key feature success data   |
| ClockInOutClicked | On the clock in screen, user clicks on the **Clock In** or **Clock Out** button. | Basic | Key functionality for a worker clocking in and clocking out | App key feature success data   |
| ClockInOutTriggered | Register user's clock in or out. This will not trigger until you have checked the location assuming location is required. | Basic | Key functionality if a worker clocked in with location | App key feature success data   |
| ClosedBannerMessage | Triggered when the user closes the banner message of a notification. | Basic | Key functionality if a user closes a notification. | App key feature success data   |
| ComposeParticipantAdded | When a user adds a participant to the shifts app. | Basic | Key functionality for adding people. | App key feature success data   |
| CreateConversationClicked | When a user creates a conversation with other workers. | Basic | Key functionality for creating message. | App key feature success data   |
| CreateShiftClicked | When a manager clicks to creates a shift. | Basic | Key functionality for shift creation. | App key feature success data   |
| DateChanged | Changing dates that are shown in calendar view to view shifts. | Basic | Key functionality for feature calendar, and viewing date ranges. | App key feature success data   |
| DayClicked | Clicking the day view when user is seeing their Shifts | Basic | Key functionality for feature calendar, and viewing day shifts. | App key feature success data   |
| DaySaved | User saves the day availability. | Basic | Key functionality for shifts, to save available days. | App key feature success data   |
| DeclineTimeOffRequest | When a user declines the request for time off of work. | Basic | Key functionality for time off, for manager to reject time off request. | App key feature success data   |
| DeleteShift | Tracks when the user deletes a shift. | Basic | Key functionality for feature, deleting a shift | App key feature success data   |
| EditShiftClicked | Tracks when a user edits a shift. | Basic | Key functionality for feature, editing a shift. | App key feature success data   |
| EntryPointClicked | Tracking clicking **Requests** in the **Schedule** tab. Requests are for when an FLW is requesting a shift time, etc.. | Basic | Key functionality for requests. | App key feature success data   |
| FREActionClicked | User clicks on **Get started**, **Try Later**, or **Close** (GPS) in First Run Experience (FRE). | Basic | Key functionality to track success of first run experience feature. | App key feature success data   |
| FRETriggered | User views the time clock First Run Experience (FRE). | Basic | Key functionality to track success of first run experience within time clock feature. | App key feature success data   |
| GPSPromptClicked | User clicks on **Allow** or **Don't Allow** in OS prompt. Allowing GPS or not. | Basic | Key functionality for feature, GPS location for user being on site for clocking in/out feature. | App key feature success data   |
| GroupClicked | Tracks when a user clicks on the group of the shift | Basic | Key functionality for feature, groups of shifts. | App key feature success data   |
| LogOutClicked | When a user logs out. | Basic | Key functionality for log out. | App key feature success data   |
| MessageTriggered | Triggered when the user's device time zone doesn't match the team time zone | Basic | Key functionality for feature of time zone. | App key feature success data   |
| MyShiftPickerClicked | Only logged if request being sent is a swap or offer. Tracking user clicks into **My Shift** picker. | Basic | Key functionality for feature, my shifts. | App key feature success data   |
| OfferRecipientClicked | Only logged if request being sent is an offer. Tracking user clicks into the team member picker to offer a shift to. Offering means offering a shift time off. | Basic | Key functionality for feature, offer shifts. | App key feature success data   |
| OfferSwapShiftFromL1 | The type of shift a user tries to offer or swap from a shifts list. iOS action is a **SwipedRight** and Android action is **LongPressed** | Basic | Key functionality for feature, swap shifts. | App key feature success data   |
| OfferSwapShiftFromL1Triggered | The type of shift a user tries to offer or swap from a shifts list. iOS action is a **SwipedRight** and Android action is **LongPressed** is triggered. | Basic  | Key functionality for feature, swap shifts. | App key feature success data   |
| OpensCalendarView | Tracking user tapping on open shifts from Schedule tab | Basic | Key functionality for feature, Open Shifts | App key feature success data   |
| OpenShiftsClicked | How many people tap the calendar icon. | Basic | Key functionality for feature, Calendar. | App key feature success data   |
| PlusButtonClicked | <ul><li>Tracking clicking the **plus button** to start a schedule.</li><li>Tracking clicking the **plus button** to start a request on RequestList.sn</li></ul> | Basic | <ul><li>Key functionality for feature, schedule creation</li><li>Key functionality for feature, requests.</li></ul> | App key feature success data   |
| RequestActedOn | Tracks when the manager acts on open shift requests | Basic | Key functionality for feature, open shifts requests. | App key feature success data   |
| RequestActionClicked | When a user requests an action. | Basic | Key functionality for feature, open shifts requests. | App key feature success data   |
| RequestDetailsClicked | When the request for a shift is clicked (either FLW manager viewing or FLW worker) | Basic | Key functionality for feature, request shifts. | App key feature success data   |
| RequestSent | Tracks when the user requests an open shift | Basic | Key functionality for feature, request shifts. | App key feature success data   |
| RequestTypeClicked | <ul><li>Tracking what type of request people select from the requests picker</li><li>Request type that the user clicks</li><ul> | Basic | Key functionality for feature, request shifts. | App key feature success data   |
| RetryButtonClicked | When a user clicks on the retry button. | Basic | Key functionality for feature, retry shifts. | App key feature success data   |
| SendRequestBulkClicked | This instrumentation point is logged once for each bulk request send. In addition, each individual request will log an event. | Basic | Key functionality for feature, send shifts. | App key feature success data   |
| SendRequestClicked | This instrumentation is logged for every individual request | Basic | Key functionality for feature, send shifts. | App key feature success data   |
| ShareShift | The information that is given when a shift is shared. | Basic | Key functionality for feature, share shifts. | App key feature success data   |
| ShareShiftsClicked | The details of an open shift. | Basic | Key functionality for feature,shifts. | App key feature success data   |
| ShiftAssigneeClicked | The Shifts Calendar view showing the particular shifts details | Basic | Key functionality for feature, shifts. | App key feature success data   |
| ShiftDetails | Your own shifts. | Basic | Key functionality for feature, shift shifts. | App key feature success data   |
| ShiftDetailsCalendar | Triggered whenever a user receives a notification from a specific team and potentially wants to switch to that particular team. | Basic | Key functionality for feature, switch shifts. | App key feature success data   |
| ShiftDetailsMyShifts | Tracking user tapping on **Calendar** from Schedules Tab | Basic | Key functionality for feature, tab shifts. | App key feature success data   |
| SwitchTeamsDialogTriggered | User views Shifts tab | Basic | Key functionality for feature, tab shifts. | App key feature success data   |
| TabCalendarClicked | User has chosen a team from the team picker | Basic  | Key functionality for feature, team shifts. | App key feature success data   |
| TabViewed | Only logged if request being sent is a swap. Tracking user clicks into **Team Shift** picker | Basic | Key functionality for feature, team shifts. | App key feature success data   |
| TeamSelectedClicked | When the user clicks on Add on a timesheet | Basic  | Key functionality for feature, timesheet shifts. | App key feature success data   |
| TeamShiftPickerClicked | When the user adds a new break entry. Log the event once the user saves the changes | Basic | Key functionality for feature, timesheet shifts. | App key feature success data   |
| TimesheetAddClicked | When the user adds a note to their break edits. Log the event once the user saves the changes. | Basic | Key functionality for feature, timesheet. | App key feature success data   |
| TimesheetBreakAdded | When the user adds a new clock entry. Log the event once the user saves the changes | Basic | Key functionality for feature, timesheet. | App key feature success data   |
| TimesheetBreakEdited | When the user confirms their timesheet. Log the event when the user hits confirm in the modal | Basic | Key functionality for feature, timesheet. | App key feature success data   |
| TimesheetBreakNoteAdded | When the user deletes their timesheet. Log the event when the user confirms the delete in the modal. | Basic | Key functionality for feature, timesheets. | App key feature success data   |
| TimesheetClockAdded | When the user clicks on Edit for a timesheet. | Basic | Key functionality for feature, time sheets. | App key feature success data   |
| TimesheetClockEdited | When the user clicks save on an edited timesheet | Basic | Key functionality for feature, timesheet shifts. | App key feature success data   |
| TimesheetConfirmed | When the user adds a note to their timesheet edits. Log the event once the user saves the changes | Basic | Key functionality for feature, timesheetnote shifts. | App key feature success data   |
| TimesheetDeleted | If a user does or does not have a shift reminder set, and the amount of minutes before a shift a user wants to be alerted. | Basic | Key functionality for feature, reminders. | App key feature success data   |
| TimesheetEditClicked | User Configuration telemetry. | Basic | Key functionality to set up user information. | App key feature success data   |
| TimesheetEditSaved | User taps on time sheet from a users profile to open that users time sheet. | Basic | Key functionality for feature, time sheets. | App key feature success data   |
| TimesheetNoteAdded | To view an approved time off request. | Basic | Key functionality for feature, approve time off. | App key feature success data   |
| ToggleClicked | To view a declined time off request. | Basic | Key functionality for feature, decline time off. | App key feature success data   |
| UserConfiguration | To view a pending time off request. | Basic | Key functionality for feature, time of requests. | App key feature success data   |

### TFL

| Action_Scenario         | Description | Type | How the event is used | Basic Subtype |
|-------------------------|-------------|------|-----------------------|---------------|
| navVaultSettings        |             |      |                       |               |
| navVault                |             |      |                       |               |
| active_session_banner_dismissed | User dismissed location sharing active reminder banner | Basic | Confirms that the user successfully dismissed the location sharing banner | Key App feature success data   |
| center_on_team_clicked | User centers map on groups | Basic | Confirms that user successfully centered the map on the group | Key App feature success data   |
| duration_picker_dismissed | User dismisses the duration picker | Basic | Confirms that user successfully dismissed duration picker. | Key App feature success data   |
| get_directions_clicked | User clicks **Get directions** button | Basic | Confirms that user successfully got directions to a location | Key App feature success data   |
| live_location_in_chats_from_profile_clicked | User clicks **live locations** in profile view | Basic | Confirms that user successfully accessed the list of live location sessions in profile | Key App feature success data   |
| my_location_button_clicked | User centers the map on their location by clicking on the **My location** button | Basic | Confirms that user successfully centered the map on their location by tapping the "my location" button on the map | Key App feature success data   |
| my_location_clicked | User centers the map on their location by clicking on the **blue dot** on the map | Basic | Confirms that user successfully centered the map on their location by tapping the **blue dot**  on the map | Key App feature success data   |
| send_map_pin_clicked | User sends static location | Basic | Confirms that user successfully shared a static location | Key App feature success data   |
| static_place_selected | User drags map to select a static place | Basic | Confirms that user successfully selected a static place by interacting with the map | Key App feature success data   |
| suggested_place_selected | User shares a static location by selecting a suggested place | Basic | Confirms that user successfully shared a static location by selecting a suggested place | Key App feature success data   |
| location_settings_open | User opens location settings | Basic | Confirms location settings dialog was successfully opened | Key App feature success data   |
| location_group_map_sync | User opens map view | Basic | Confirms that the all available locations are sync-ed successfully | Key App feature success data   |
| location_message_send | User initiates a location sharing session | Basic | Confirms that the location sharing message was successfully sent | Key App feature success data   |
| location_active_tracking | User's device is switched to active tracking | Basic | Confirms that user's location services are switched successfully to active tracking | Key App feature success data   |
| location_map_load | Map view load | Basic | Confirms that the big map view successfully loaded | Key App feature success data   |
| location_map_markers_load | Map view load | Basic | Confirms that location markers for all users actively sharing are displayed properly on the map view | Key App feature success data   |
| stop_location_sharing_logout | User logs out of the app | Basic | Confirms that we successfully stopped all location sharing session when the user logged out of the app | Key App feature success data   |
| location_family_sync | Showing members of a Family group that were created in MSA family app | Basic | Confirms that we are displaying all family members that can be granted consent. We do not send any additional data other than the success confirmation | Key App feature success data   |
