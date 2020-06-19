---
title: Required diagnostic data for Microsoft Teams
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
# Required diagnostic data for Microsoft Teams

The following article contains a list of Microsoft Teams events, and lists of properties each event collects.

## Events

### A

- **accessibilityUserConfiguration** - When a FirstLine Worker Manager approves a FirstLine Worker request to take time off. To toggle if this is an accessible feature. ???
- **acknowledgeSettingChange** - Acknowledge an update in the we updated a notification setting dialog. This is a feature success metrics used to acknowledge update notifications and to determine overall notification reliability.
- **actionComposeMenu**
  - Create message extension usage.
  - Action ME usage. ???
- **active_session_banner_dismissed** - A user dismissed the location sharing active reminder banner. This confirms that the user successfully dismissed the location sharing banner.
- **activityChatClicked** - Triggered when non-live chat is tapped in the Activity tab or a split view is shown.
- **activityContextMenu** - Overflow actions in the activity feed that help to track if a user can perform contextual actions on the feed.
- **activityFeedClick** - Triggered when a user tap on an activity feed item and navigate to a bot chat, it captures click information on feed item.
- **activityFeedLongPress** - Captures long press gestures on feed items. Helps to track if a user can successfully triage feed items using gestures.
- **activityFeedSwipe** - Captures swipe gestures on feed items. Helps to track if a user can successfully triage feed items using gestures.
- **activityFilterClick** - Captures activity filter usage, which helps to track if a user can filter feed items successfully.
- **activityFilterOptionsClick** - Captures activity filter usage, which helps to track if a user can filter feed items successfully. Also helps to track if a user can successfully triage feed items using gestures.
- **activityFilterOptionsClicked** - Captures activity filter usage, which helps to track if a user can filter feed items successfully.
- **activityLiveChatClicked** - Triggered when chat is clicked from a live meeting on the Activity tab.
- **activityLiveDetailsClicked** - Triggered when **Details** is clicked from a live meeting on the Activity tab.
- **activityTabClicked** - Helps to track if user came back to activity tab in the following situations:
  - The Activity tab is shown.
  - Teams captures an activity tab event.
- **activityTypeDropdown** - Captures activity filter usage to switch between My Activity and Feeds, which helps to track if a user can filter feed items successfully.
- **addChannel** - Adding a channel. This item provides success data around the successful creation of a channel.
- **addMember** - Triggered when a users taps the **Invite people** button in the **More** menu.
- **addMembers** - Add members to a team or private channel to track team or channel management.
- **addToCalendar**
- **addToList** - A user adds a contact to a contact list.
- **addToMeeting**
- **addUserAsContact** - A ser can add a contact by clicking on the **Add contact** icon from the profile card of the contact.
- **admitAll** - The number of times a user clicks on the **Admit all** button from the lobby section.
- **admitParticipant** - The number of times a user admits someone into a meeting from the meeting roster.
- **alertsNavAlert** - Tapping on a feed item.
- **android: null** - Mute or unmute a bot chat. This is enhancing existing telemetry around chats only adds application information.
- **anonymousMeetingJoin** - A user clicked **Join meeting** on qn anonymous join provide name page or tapped **OK** in the name dialog.
- **anonymousMeetingJoinWelcome** - A user clicked on **Join as guest** on an anonymous join meeting landing page.
- **anonymousMeetingPostMeetingChat** - The number of user views of chat from the call end screen.
- **anonymousMeetingPostMeetingRejoin** - The number of times an anonymous user tries to rejoin a meeting.
- **anonymousMeetingSignIn** - The number of times a user navigated to sign-in from the name input screen.
- **anonymousMeetingSignInWelcome** - A user clicked on **Sign in and join** on an anonymous join meeting landing page.
- **anonymousMeetingToggleMuted** - The number of times the mute toggle button was clicked.
- **anonymousMeetingToggleVideo** - The number of times the video toggle button was clicked.
- **appBG** - Appplication BG. ???
- **appKilled** - Appplication terminated.
- **approveTimeOffRequest** -  When a FirstLine Worker Manager approves a FirstLine Worker request to take time off. This is a key functionality of time off requests.
- **assigneeChange** - Triggers when a new assignee is added to a task item.
- **assignmentPickerClicked** - When user clicks the **Assign To** button that brings them to an assignee picker page.
- **assignmentRemoved** - Triggers when an assignee is removed from a task item by clicking the **x** (which is the only way to remove an assignee).
- **attachmentAdded** - Confirms that an attachment in a task was successfully added.
- **attachmentDeleted** - Confirms that an attachment in a task was successfully deleted.
- **attachmentUpdated** - Confirms that an attachment in a task was successfully updated.
- **audioOnlyLowBatteryBanner** - A user taps **Audio only** due to a low battery banner.
- **audioOnlyPoorNetworkBanner** - A user taps **Video off** due to a poor connection banner.
- **audioUserDoubleTap** - Double tap on an audio participant.
- **autoReconnectCallmebackCallDrop** - The number of times user clicked on the **Callmeback** button at a call end screen.
- **autoReconnectDialIn**
  - A user clicks the **Dial in** button on the reconnect UFD.
  - The number of times user clicked on the **Dial In** button while a reconnect is happening.
- **autoReconnectDialInonCallDrop** - A user clicks the **Dial in** button on the call disconnected UFD.
- **autoReconnectDialOut** - A user clicks the **Call me back** button on the reconnect UFD.
- **autoReconnectRejoinonCallDrop** - The number of times user clicked on the **Rejoin** or the **Redial** button at the call end screen.

### B

- **backFromCallMePSTN** - A user doesn't complete the call Me back PSTN number flow.
- **backToPhotoShare** - Returning to a camera.
- **backToStageFromWhiteboard** - Returning to a call screen from a whiteboard.
- **backToWhiteboardFromStage** - Going to a whiteboard from a call screen.
- **badUrlLoginFailed** - User was unable to login.
- **badUrlLoginSuccess** - User was able to login.
- **blockAnonymous** - When a user:
  - Enables calling setting to block calls without caller id from settings.
  - Disables calling setting to block calls without caller id from settings.
  - Enables calling setting to block calls without caller id from action sheet.
  - Disables calling setting to block calls without caller id from action sheet.
- **blockCaller** - Blocking:
  - A number and contact from the new iOS calls action sheet.
  - A contact and number from the contact card.
  - Numbers from settings.
- **blockChat** - Blocking a bot chat. This enhances existing telemetry around chats and is only adding application information.
- **botClickCardAction** - Connector card usage.
- **brbFeedback**
- **brbFormCancelled**
- **brbFormOpened**
- **brbFormSubmit**
- **breakStartEndClicked** - On the clock in screen, a user clicks on the **Start** or the **End break** button. This is key functionality for a FirstLine Worker requesting a break.
- **breakStartEndTriggered** - Register a user's break start or end. This will not trigger until you have checked the location assuming location is required. This is a key functionality for break feature within Shifts.
- **bucketSelected** - Confirms that a bucket has been successfully selected.
- **bucketUnselected** - Confirms that a bucket has been successfully unselected.
- **bucketPickerClicked** - Confirms that the bucket picker successfully launched.

### C

- **chatAvatarEdit**
- **chatAvatarEditGallery**
- **chatAllowJoinViaLink**
- **chatShareLink**
- **composeVault**
- **conversation**
- **contactActivity**
- **channelFollow** - Turn on notifications for a channel.
- **channelUnfollow** - Turn off notifications for a channel.
- **channelsActiveSetting** - A user changes their **notify me when I'm active on desktop** notification setting.
- **chatCreation** - A user creates a chat, this tracks the success of chat creation.
- **createOrJoinTeam** -A user taps the **+** button to create or join a team this tracks team creation and joins.
- **chatAvatarEditCamera**
- **chatAvatarEditView**
- **chat** - Refers to:
  - A new message button or textbox in chat.
  - 1:1 chat tapped on callHistory item.
  - A 1:1 chat click from call list.
- **createTeam, createChannel** - This provides success data around the successful addition of members in a team and the successful creation of a new team under the following circumstances:
  - A user taps the **Skip** button in the **Add Members** page (check existing first).
  - A user taps the **Done** button in the **Add Members** page (check existing first).
  - Shows team or channel creation acknowledgement.
- **cancelNavigationToLink** - A user chose to cancel navigation.
- **cancelRequestToJoinTeam** - Cancel request to join a team.
- **cancelRequestToJoinTeamError** - Error with a cancel join request.
- **castPpt** - Event is triggered when a user:
  - Taps on share a PowerPoint option.
  - Selects a particular PowerPoint.
  - Selects the Teams and Channels folder in the file picker page.
  - Selects a OneDrive folder in the file picker page.
  - Stops the casting session.
  - Taps on multitasking PiP.
  - Selects a display option from file view.
- **castScreen** - Refers to:
  - Tapping on share screen option.
  - Stopping the screen sharing session.
  - Selecting display option from file view.
- **changeIsActiveSetting** - Change desktop activity based notification.
- **channel** - New message button or textbox in chat.
- **channelDetails** - Channel navigation information for when:
  - A user taps on channel header.
  - A user navigates to channel details page.
- **channelFollow/channelUnfollow** - Follow or unfollow a channel.
- **channelNav** - Navigating to a channel from anywhere.
- **channelNotificationSettings** - Triggered when a user:
  - Responds to **New Notification settings** dialog.
  - Taps channel notification settings button in channel view.
  - Selects a channel notification setting.
- **channelTabOverflow** - Clicks on the **More** tab in a channel.
- **chat - No AS Assigned** - Viewing unread chat or editing the chat roster, specifically:
  - Selecting the **Done** button when adding a user to a chat.
  - A user taps on a chat list filter to filter by unread.
- **chatAddChat** - Add a member to chat button tapped (this will be same for 1:1 chat and group chat).
- **chatCM_CopyText** - Tap **Copy text** on a chat context menu.
- **chatCM_DeleteMessage** - Tap **Delete message** on a chat context menu.
- **chatCM_edit** - Tap **Edit** on a chat context menu.
- **chatCM_Forward** - Tap **Forward** on a chat context menu.
- **chatCM_markUnread** - Tap **Mark as unread** on a chat context menu.
- **chatCM_save** - Tap **Save** on a chat context menu.
- **chatCM_SeenBy** - Tap on **Seen** on a context menu option. Read Receipts, such as read by (readby).
- **chatContactsEnter** - User enters the chat contacts tab
- **ChatDetails** - Provides success and discoverability data for a chat details page when:
  - A user taps on a chat header.
  - A user navigates to a chat detail page.
- **chatRecentEnter** - A user enters the chat recent tab.
- **chatSendMessage** - Send a chat message.
- **clickPhotoOfficeLens** - Click on **Take photo** - Launch camera (Android only).
- **composeExpandComposer** - **Format** button tapped.
- **composeFilePick** - Native file picker launched.
- **composeImagePicker** - **Image** button tapped.
- **composeLocation** - **Location** button tapped in compose.
- **composeMention** - @mention.
- **composeOpenEmoticonPicker** - Emoticon picker tapped.
- **composeOpenFunPicker** - Fun picker tapped.
- **consumeVoiceMessage** - Voice message played.
- **ContactCard_SeeMoreOOF** - See more of a long OOF message.
- **conversation, tabs** - Tab clicked.
- **copyLink** - Copy a link to a channel post.
- **createChannel** - Provides success data around the successful creation or discard action for new channel creation, when a user:
  - Taps the **Done** button on the **Create Channel** Page.
  - Taps the **Cancel** button on the **Create Channel** Page.
- **createTeam** - Provides success data around the successful creation or discard action for new team creation, when a user:
  - Taps the **Done** button on the **Create Team** Page.
  - Taps the **Cancel** button on the **Create Team** Page.
- **channelNavTab** - Provides success and discoverability data for files in Teams when:
  - A user clicks on **Files** tab in channel
  - There is a connector card reply.
- **channelSendMessage** - Triggered when:
  - A channel message is sent.
  - A bot is @mentioned in a compose box.
- **chatListNavConversations** - ChatList navConversations. ???
- **callInProgressShown** - A ***Call in progress** banner is shown.
- **callMePSTNConnected** - **Call me** is successful.
- **callOrMeetUpAddParticipantsDone** - A user finalizes their participant addition.
- **callOrMeetUpAutoReconnect** - Poor network performance causes a user's device to go into Autoreconnect mode.
- **callOrMeetUpMuteParticipant** - User mutes a remote participant.
- **callsTabNewCall** - User selects **New Call** in the **Calls** tab.
- **callTransfer** - User starts a call transfer.
- **BYOELiveEventJoin** - BYOE live event is joined by a user.
- **calendarLiveChatClicked** - Chat from live meeting on the Schedule tab.
- **calendarMeetingJoin** - **Meeting Join** button tapped from a Calendar.
- **calendarUpcomingChatClicked** - Chat from an upcoming meeting on the Schedule tab.
- **callAccepted** - Call accepted.
- **callAcceptedSFB** - Call accepted.
- **callAppPreference** - A preferred calling App is selected.
- **callControlsManualDismiss** - Call controls are dismissed manually (user action).
- **callControlsManualInvoke** - Call controls are invoked manually (user action).
- **callHistoryItemExpand** - Call History Item expanded.
- **callHistoryTab** - CallHistoryTab is selected in Calls.
- **callOrMeetUpAddParticipants** - Triggered when:
  - Add participant button is tapped on a 1:1 call screen.
  - Select Person (VoIP) in Add participants.
  - Select PSTN in Add participants.
  - Add people in a live private meeting.
  - Select PSTN in a live private meeting.
  - Select Company contact in a live Private meeting.
  - Select Device contact in a live private meeting.
  - Add Participants Done in a live private meeting.
  - Add people in a live channel meeting.
  - Select PSTN in a live channel meeting.
  - Select Team Member in a live channel meeting.
  - Select Device contact in a live channel meeting.
  - Add Participants Done in a live channel Meeting.
- **callOrMeetUpAddRoom** - Triggered when:
  - User taps **Add room** in roster.
  - User selects a search result in add room.
  - User taps **Dismiss** for Nearby.
  - User taps **Enable BT** or **Location** for Nearby.
  - User selects a nearby room result in add room.
  - User selects a suggested room result in add room.
  - User taps **Done** in add room.
- **callOrMeetUpAudioOffSwitch** - Flip **Audio off** button while in companion join mode in a live call or meetup.
- **callOrMeetUpCallAccepted** - Triggered when:
  - A call is accepted.
  - A PSTN Call is accepted.
- **callOrMeetUpCallEnded** - Triggered when:
  - An **End call** button is tapped.
  - A **Call ended** button is tapped while in callOrMeetupLive.
  - A **Call ended** button is tapped while in lockScreen.
  - A **Call ended** button tapped while in notification.
  - A **Call ended** button tapped while in inApp.
  - A **Call ended** button tapped while in callKit.
  - A **Call Ended** button for PSTN tapped.
- **callOrMeetUpChatWithParticipants** - Chat toggle while in live meeting or call.
- **callOrMeetUpDeviceAudioSwitch** - Triggered when:
  - Switch audio source to speaker.
  - Switch audio source to device.
  - Switch audio source to Bluetooth.
  - Switch audio source to audio off.
  - Switch speaker while in live meeting or a call.
  - Switch speaker to Audio off while in live meeting or a call.
  - Flip **Audio off** button while in companion join mode in live call or meetup.
  - Device Audio Switch while in PSTN.
- **callOrMeetUpEnterDriveMode** - Switches manually to drive mode from the **...** menu.
- **callOrMeetupExitDriveMode** - **Exit drive mode** button tapped.
- **callOrMeetUpHold** - Triggered when:
  - The **Hold** button is tapped while in live meeting or a call.
  - Call Hold in PSTN.
- **callOrMeetUpIncomingVideoSwitch** - Turn off IncomingVideo while in live meeting or a call.
- **callOrMeetUpInvitedParticipants** - Triggered when:
  - Clicked **See all** at the bottom of an **Others invited** participant group during private live meeting.
  - Clicked **See all** at the bottom of an **Others invited** participant group during live channel meeting.
- **callOrMeetUpJoinedParticipants** - Triggered when:
  - Clicked **See all** at the bottom of an **In the meeting** participant group during private live meeting.
  - Clicked **See all** at the bottom of an **In the meeting** participant group during live channel meeting.
- **callOrMeetUpLobbyParticipants** - Triggered when:
  - Clicked **See all** at the bottom of a **Lobby** participant group during private live meeting.
  - Clicked **See all** at the bottom of a **Lobby** participant group during live channel meeting.
- **callOrMeetUpMicrophoneSwitch** - Triggered when:
  - Switch Microphone on.
  - Switch Microphone off.
  - **Microphone** button is tapped while in a live meeting or a call.
  - Microphone switch while in PSTN.
- **callOrMeetUpMuteParticipants** - Mute all participants while in live meeting or a call.
- **callOrMeetUpParticipants** - Participants toggle while in live meeting or a call.
- **callOrMeetUpRemoteMuteUFD** - You have been muted UFD.
- **callOrMeetUpResume** Triggered when:
  - **Resume** button is tapped while in a live meeting or a call.
  - Call Resume in PSTN.
- **callOrMeetUpSearchParticipants** - Triggered when:
  - Clicked **Search** in meeting participants during private live meeting.
  - Clicked **Search** after viewing the **Lobby** participant group during private meeting.
  - Clicked **Search** after viewing the **In the meeting** participant group during private meeting.
  - Clicked **Search** after viewing the **Others invited** participant group during private meeting.
  - Clicked **Search** in meeting participants during a live channel meeting.
  - Clicked **Search** after viewing the **Lobby** participant group during a live channel meeting.
  - Clicked **Search** after viewing the **In the meeting** participant group during a live channel meeting.
  - Clicked **Search** after viewing the **Others invited** participant group during a live channel meeting.
- **callOrMeetUpVideoSwitch** - Triggered when:
  - Switch Video on.
  - Switch Video off.
  - Video button tapped while in live meeting or call.
- **callPark** - Triggered when:
  - User taps **Park Call** in the **…** menu.
  - User taps **Retrieve** button.
  - User taps **Pickup** in retrieve dialog.
  - User taps **Cancel** in retrieve dialog.
- **callPreferenceSetting** - Call preference app setting.
- **callVoicemailTab** - VoicemailTab selected in Calls.
- **cameraPermissionCancel** - A user taps **Cancel** on the camera permission dialog.
- **cameraPermissionGoToSettings** - A user navigates to **Settings** from the camera permissions dialog.
- **cancelFileShare** - A user clicks **Cancel** on the confirmation dialog.
- **cancelFileUpload** - A user clicks **x** on the upload dialog.
- **chatCancelAudioCall** - Cancel a group audio call - Confirm dialog.
- **chatCancelVideoCall** - Cancel a group video call - Confirm dialog.
- **chatStartAudioCall** - Triggered when:
  - 1:1 audio call button tapped.
  - Taps the **Audio** button on a search result.
  - Taps the **Start Call** button on the right.
  - 1:1 audio call tapped from a callHistory item.
  - 1:1 audio call tapped from a voicemail item.
  - Place a group audio call - Confirm dialog.
- **chatStartAudioCallOnBehalfOf** - Delegate starts a call from the action sheet as Boss.
- **chatStartAudioCallOnBehalfOfMyself** - Delegate starts a call from the action sheet as Myself.
- **chatStartAudioCallSFB** - 1:1 audio call button tapped.
- **chatStartVideoCall** - Triggered when:
  - 1:1 video call button tapped.
  - Taps video button on search result.
  - 1:1 video call tapped from callHistory item.
  - Place a group video call - Confirm dialog.
- **chatStartVideoCallSFB** - 1:1 video call button tapped.
- **closeLobbyBanner** - Number of times a user closes the lobby toast using its **Close** button.
- **companionBannerJoin** - Click **Join** on the top-level banner.
- **companionDismiss** - Dismiss the companion banner.
- **companionDismissProximity** - Dismiss the companion banner.
- **companionJoin** - Join as companion option is clicked on the sheet.
- **companionJoinProximity** - Joined through tje companion banner.
- **confirmAudioOn** - User confirms that they want audio on.
- **confirmFileShare** - User clicks **Share** on the confirmation dialog.
- **consultTransfer** - Triggered when:
  - Taps **Transfer** > **Consult first**
  - Transfer target set to Person
  - Transfer target set to Phone Number.
- **consultTransferCall** - Triggered when a user:
  - Initiates a consult call.
  - Confirms transfer dialog - confirm.
  - Confirms transfer dialog - cancel.
  - Hits the banner transfer button.
  - Hits the banner resume button.
- **consultTransferChat** Triggered when a user:
  - Initiates a consult chat.
  - Confirms a transfer dialog - confirm.
  - Confirms a transfer dialog - cancel.
  - Selects a **Banner transfer** button or **Banner resume** button.
- **contactOrganizer** - Clicked **Contact organizer**.
- **crossCloudDialogCancel** - A user clicks **Cancel** on a cross-cloud dialog.
- **crossCloudDialogJoin** - A user clicks **Join as guest** for a cross-cloud dialog.
- **calendarTab** - Click on the **Meetings** tab in the bottom rail. Useful in understanding the calendar usage and compare with other apps on the bottom rail or to determine if there was a failure in rendering the calendar post after a click from the bottom bar.
- **calendarTabClicked** - In the circumstances listed below, this will show calendar usage and allow you to compare with other navbar apps on the bottom rail. This can be used to determine if there was a failure when:
  - The Schedule tab is shown.
  - A user clicks on the **Meetings** tab in the bottom rail.
- **cancelEditMeeting** - Click on the **Close** button while on the meeting scheduler page, after clicking **Edit meeting**. This logs abandoned edit meeting clicks.
- **cancelMeeting** - Click on **Cancel event** from the meeting details page. Used to get aggregated data on the number of cancelled meetings.
- **cancelNewMeeting** - To log abandoned Create meeting clicks and verify what caused them when:
  - A user clicks on the **Close** button while on meeting scheduler page.
  - A user clicks on the **Close** button while on meeting scheduler page after clicking **Edit meeting**.
- **chatWithMeetingParticipants** - Clicks on **Chat** tab from Meeting Details page.
- **cardView - No AS assigned** - Card view and card rendering. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side. This item is required to measure any error with joining a team.
- **chicletExpand** - Understand how users preview cards on mobile, and the preview closure behavior.
- **composeSearchResult** - Message extension result selection, which is helpful to understand the app search result relevance. Also enhances message send telemetry with app data.
- **composeSelectExtension** - Tap on a ME app.
- **composeSendMessage** - Enhances message send telemetry with app data.
- **createComposeExtension** - Create message extension usage, or action ME usage.
- **createPersonalPlan** - A personal list is created, checks list created with ToDo service. Confirms a new personal task list is created in ToDo.
- **createPlannerPlan** - A shared list is created, checks list created with Planner service. Confirms a new shared task list is created in Planner.
- **createDefaultPlannerPlan** - A shared list is created automatically when the Tasks app is opened for the first time by anyone in that group, checks auto list created with Planner service. Confirms the default shared task list is successfully created in Planner the first time a user attempts to create a shared task list.
- **createTask** - Used for when create action fails, checks call to Planner service. Confirms a task create operation failed.
- **createPersonalTask** - Confirms a personal task has been successfully created.
- **createPersonalSubtask** - Confirms a personal sub-task has been successfully created.
- **createPlannerTask** - Checks a call to the Planner service. Confirms that a user has successfully created a task in a shared tasks list.
- **createPlan** - Confirms that a shared task list has been successfully created. Confirms that a shared plan has been successfully created through middle tier.
- **checklistSeeAllClicked** When a user clicks the **See All** button inside task details to view all checklist items.
- **checkListAddClicked** - A user clicks **Add an item** inside task details view for checklist section.
- **checkListItemDeleted** - A user deletes a checklist item from the task.
- **checkListItemAdded** - A user creates a checklist item for task.
- **checkListItemUpdated** - A user updates a checklist item for task.
- **clearFilter** - When a user clears all filters while viewing a tasklist.
- **completionStateChange** - Triggers when a completed or uncompleted filter toggle is clicked in filter view from task list.
- **createTaskList** - When a user navigates to the create plan view from home view.
- **channelPickerClicked** - Confirms that the channel picker successfully launched.
- **commentsClicked** - Confirms that the comments view was successfully launched.
- **channelSelected** - Confirms that a channel was successfully selected for a new plan.
- **commentAdded** - Confirms that a comment was added to a task.
- **commentUpdated** - Confirms that a comments was successfully updated on a task.
- **create_default_plan_and_nav_to_view** - Confirms successful creation of a default shared task list and how long it took for user to land on the resulting view after action.
- **create_personal_plan_and_nav_to_view** - Confirms successful creation of a personal task list and how long it took for user to land on the resulting view after action.
- **create_personal_task** - Confirms successful creation of a personal task item.
- **create_planner_plan_and_nav_to_view** - Confirms successful creation of shared task list and how long it took for user to land on resulting view after action.
- **create_planner_task** - Confirms successful creation of shared task item.
- **createShiftOrTimeOffClicked** - Triggered if you click **Create a shift** or **Time off**.
- **closedBannerMessage** - Triggered when the user closes the banner message of a notification.
- **clockInOutClicked** - On the clock in screen, user clicks on the **Clock In** or **Clock Out** button.
- **clockInOutTriggered** - Register user's clock in or out. This will not trigger until you have checked the location, assuming location is required.
- **closedBannerMessage** - Triggered when a user closes the banner message of a notification.
- **composeParticipantAdded** - When a user adds a participant to the Shifts app.
- **createConversationClicked** - When a user creates a conversation with other workers.
- **createShiftClicked** - When a manager clicks to creates a shift.
- **center_on_team_clicked** - User centers map on groups, this event confirms that user successfully centered the map on the group.

### D

- **dashboardNav**
- **deviceAddressBookSync**
- **deviceAddressBookUnsync**
- **dragDatePickerHandle**
- **disabled** - User taps **Skip notifications** in FRE. This provides key success data for skipping the notification in FRE flow.
- **disableQuietDays** - Quiet Days disabled. Feature success telemetry for quiet days.
- **disableQuietHours** - Quiet Hours disabled.
- **discoverTeams** - Navigate to Browse and Join Teams page.
- **dismissFlyout** - **Dismiss** button pressed.
- **dismissModality** - Exit modality picker without sharing.
- **dismissModalityPicker** - Modality picker button pressed.
- **dismissReadReceiptsNotice** - A user pressed **Got it** from a feature notice.
- **DLPDelete** - A user deleted a blocked message.
- **DLPEdit** - A user edited a blocked message.
- **DLPOverride** - A user overrode blocked message.
- **DLPOverrideReport** - A user reported a false positive and overrode the message.
- **DLPReport** - A user reported a false positive.
- **DLPResolve** - A user attempted to resolve a DLP message.
- **DLPSeeOriginal** - A user tapped to see an original message.
- **downloadFile** - Helps to:
  - Check if a user was able to initiate a download operation.
  - Track if a user can download a file successfully.
- **dialIn** - A user chooses to Dial in into a meeting (various locations).
- **deleteVoicemail** - Delete voicemail item tapped.
- **demotedToAttendee** - User demotes a presenter - **Change** button in the dialog box.
- **denyParticipant** - Number of times user denies someone entry from the roster.
- **detailsTabClicked** - The **Details** tab is clicked on the meeting.
- **dialInBadNetworkBanner** - A user taps **Dial in** for poor connection banner.
- **dialInBadNetworkBannerCancel** - A user cancels the **Dial in** on the native dialog.
- **dialInBadNetworkBannerConfirm** - A user confirms the **Dial in** on the native dialog.
- **dialInCall** - A user clicks **Call** on the **Dial in** pop-up.
- **dialInCancel** - A user clicks **Cancel** on the **Dial in** pop-up.
- **dialOutCall** - Triggered when a user:
  - Joins in Drive mode.
  - Clicks **Call** on the **Call me back** pop-up.
- **dialOutCallAAD** - A user clicks any number from **My numbers** in the action sheet
- **dialOutCallRecent** - A user clicks any number from previous recent numbers in the action sheet.
- **dialOutCancel** - A user clicks **Cancel** on the **Call me back** pop-up.
- **dialOutDialog** - A user clicks **New number** in the action sheet.
- **dialOutFailRetry** - A user clicks **Retry** from a failure banner.
- **DialPad** - The **DialPad** button is tapped from the call list.
- **disableCategory** - Disable a type of notification or disable incoming call notifications.
- **Dismiss_earlycancelledCQF** - A user dismissed the CQF early cancelled call form.
- **Dismiss_ratemycallCQF** - A user dismisses the CQF rate my call form.
- **Dismiss_ratemyliveeventCQF** - A user dismisses the CQF rate my live event form.
- **dismissBadNetworkBanner** - A user taps **Dismiss** for a poor connection banner.
- **dismissStartRecording** - Dismiss error when starting recording.
- **dismissStopRecording** - Dismiss error when stopping recording.
- **dismissUseWifiForVideoBanner** - Triggered when a user dismisses a banner:
  - That tells the user that remote participant video is blocked, and users have to switch to WiFi to see it.
  - That tells the user that users have to switch to WiFi to share video.
- **dtmfPSTNCall** - DTMF button on DialPad is tapped.
- **deleteMeeting** - Click on the **Delete** button from the Meeting Details page.
- **deleteContact**
- **deleteTask** - Verifies with the Planner service as to whether a delete action was successful or unsuccessful. Confirms that a task delete failed, that is, the deletion of a task was unsuccessful.
- **deletePersonalTask** - Confirms a personal task has been successfully deleted.
- **deletePersonalSubtask** - Confirms a personal sub-task has been successfully deleted.
- **deletePlannerTask** - Confirms that a shared task delete operation completed successfully.
- **descriptionChanged** - Confirms a shared task description has changed successfully.
- **dueDateSelected** - Triggers when a user applies a filter by duedate while viewing a tasklist.
- **dueDateUnselected** - Triggers when a user unapplies a filter by dueddate while viewing a tasklist.
- **descriptionClicked** - When a user clicks to view description from task details.
- **deleteClicked** - When a user clicks **Delete** within task details, which brings up the confirmation dialog.
- **dueDatePickerClicked** - Triggers when a user clicks the **Due Date** button in task details, opening the duedate picker page.
- **dueDateChanged** - Triggers when user assigns a duedate to a task.
- **datePickerLaunch** - Confirms that date picker was successfully launched.
- **delete_personal_plan** - Confirms the successful deletion of a personal task list.
- **delete_personal_task** - Confirms the successful deletion of a personal task item.
- **delete_planner_plan** - Confirms the successful deletion of a shared task list.
- **delete_planner_task** - Confirms the successful deletion of a shared task item.
- **dateChanged** - Register user's break start or end. This will not trigger until you have checked that the location assuming location is required.
- **dayClicked** - Clicking the day view when user is seeing their shifts.
- **daySaved** - This saves a day of shifts.
- **dateChanged** - Changing dates that are shown in a calendar view to view shifts.
- **dayClicked** - Clicking the day view when user is seeing their Shifts. It's a key functionality for feature calendar and viewing day shifts.
- **daySaved** - A user saves the day availability.
- **declineTimeOffRequest** - When a user declines the request for time off of work. It's a key functionality for time off, for manager to reject time off request.
- **deleteShift** - Tracks when the user deletes a shift.
- **duration_picker_dismissed** - A user dismisses the duration picker.

### E

- **enableCategory** - Relating to notification settings when enabling:
  - A type of notification.
  - Incoming call notifications.
- **editChannel** - A user taps on a button to edit a channel that they own or administer.
- **editNavigation** - A user taps **Reorder** in the **More** menu to edit the order of bottom bar apps.
- **editTeam** - A user taps on a button to edit a team that they own or administer.
- **enableQuietDays** - a user enables quiet days.
- **editTeam, editChannel** - Relating to the successful addition of members in a team and successful creation of an existing team when a user:
  - Taps the **Cancel** button in the **Add Members** page (existing team or channel).
  - Taps the **Done** button in the **Add Members** page (existing team or channel).
- **edit** - **Edit** button in a chat message.
- **enabled** - Relating to enabling the notification in FRE flow:
  - User taps **Enable notifications** in FRE.
  - User taps Enable in reminder.
- **enabled, notNow** - Notification permission prompt **Accept** button. This captures how many people have enabled the notification and provides information relating to app engagement.
- **enabled/notNow** - FRE Notifications Permission (iOS). Captures user engagement with the notification feature.
- **enablediOSPrompt** - A user actually enables notifications in the iOS notifications permissions prompt. This gives information about users who actually enable notifications in iOS from notifications permissions prompt.
- **enabledQuietDays** - Quiet Days enabled.
- **enableLocationPermission** - Enable location services (TBD). ???
- **enableQuietHours** - Quiet Hours enabled.
- **endEditing** - Save button pressed.
- **endMyShift** - Number of devices in shared mode or number of times signed out.
- **expandCollapseSection** - Tap a section header to expand or collapse a section.
- **endPSTNCallSelected** - a user ends a PSTN and a Content call.
- **endPSTNCallShown** - A user is prompted to end a PSTN or a Content call.
- **editMeetingResponse** - Edit meeting response from the meeting detail page.
- **emergencyCall** - Emergency Call placed calling plan.
- **emergencyCallDirectRouting** - Emergency Call placed direct routing.
- **emergencyCallLocationPolicyBased** - DialEmergency using DialPad.
- **emergencycallSecurityDeskNotify** - Emergency Call placed, security desk informed.
- **enabled/disabled** - Calling permissions or contact permissions (Android only).
- **endFileShare** - A user clicks **Go back** on a file sharing dialog.
- **endPhotoShare** - **x** out from photo share.
- **endVideoShare** - **x** out from Video share.
- **expand/collapse** - Device contacts or company contacts section.
- **editRsvpMeetingOptions** - Click on **RSVP** to change from the previous selection.
- **Expected: atMention - Android: chatSendMessage - iOS: sendMsg** - @mention a bot in a compose box.
- **Expected: botClickCardAction - Android: showCard - iOS: missing** - Tap on card buttons. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side.
- **Expected: chatSendMessage - iOS: composeSendMessage** - Tap on **Reply** and reply to a bot chat in a channel.
- **Expected: composeSendMessage - Android: replyChannel - iOS: missing** - Tap on **Reply** and reply to a bot chat in a channel.
- **Expected: messageLike - Android: reactLike_CM** - Like a bot message.
- **Expected: messageUnread - Android: markAsLastUnread** - Message context menu options for a bot message.
- **editContact**
- **errorShown** - A user saves the day availability.
- **editShiftClicked** - Tracks when a user edits a shift.
- **entryPointClicked** - Tracking clicking **Requests** in the **Schedule** tab. Requests are for when an FLW is requesting a shift time, etc..

### F

- **forcedUpdateAccept** - A user accepts to update the app version in the force update dialog.
- **forcedUpdateExit** - A user closes the app instead of updating the app version in the force update dialog.
- **forcedUpdatePrompt**
- **federatedUpgradeNewChat** - A user upgrades legacy chat to native.
- **files, conversation, oneNote, etc.** - Tab clicked. Relevant to the **About** tab discoverability. ???
- **firstTimeSignedIn** Sign in or sign up event triggered by:
  - Sign-in success.
  - First sign-in Succeeded.
  - Sign-in Errors Seen by User.
  - Record telemetry about MAM/MDM policies implemented on first time login.
  - Record app install referrer parameters after first time successful login.
- **formattingBold** - A user selects bold formatting.
- **formattingHighlight** - A user selects highlight formatting.
- **formattingImportant** - A user selects importance.
- **formattingItatlics** - A user selects italics.
- **formattingTextColor** - A user selects text color formatting.
- **formattingUnderline** - A user selects underline.
- **FRE - No AS Assigned** - Record telemetry about MAM/MDM policies on app launch to gather data about active users. Telemetry for Intune integration for MAM and MDM. Provides success data about failure during FRE.
- **freDone** - FRE done. Feature success telemetry on how many users successfully completed the sign in. This helps preempt sign in issues with the product. And solve login isues proactively.
- **funSearchQueryEntered** - Giphy query entered. Success data for the giphy attachment feature in Teams.
- **funSelectItem** - Giphy image choosen. Success data for the giphy attachment feature in Teams.
- **fileThumbnailPreviewDownloaded** - Helps to identify if a thumbnail was rendered successfully for a file.
- **fileThumbnailPreviewFromCache** - Captures if thumbnail shows from cache successfully and helps to identify if thumbnail was rendered successfully for a file.
- **fileThumbnailPreviewNotAvailable** - Helps to identify if thumbnail was rendered successfully for a file.
- **files**
- **fileSelected** - User picks a PowerPoint presentation. Tracks if the user can select a file successfully.
- **fillFrameVideo** - Fill frame from action sheet.
- **fitToFrameVideo** - Fit to frame from action sheet.
- **flipCamera** - Flip camera.
- **FREActionClicked** - A user clicks on **Get started**, **Try Later**, or **Close** (GPS) in the First Run Experience (FRE).
- **FRETriggered** - A user views the time clock First Run Experience (FRE).

### G

- **guideMe** - Users taps on a banner that informs them about a 3P app blocking notifications and offers troubleshooting guidance.
- **galleryImage** - Image uploaded - gallery.
- **goToNotificationSettings** - Go to the notification settings page from **we updated notification settings** dialog.
- **groupCallJoin** - A user joins a Group call.
- **get_sender_sub_scenario** - get sender sub scenario in activity.
- **group_map_open**
- **group_map_closed**
- **groupClicked** - Tracks when a user clicks on the shift group.
- **GPSPromptClicked** - A user clicks on **Allow** or **Don't Allow** in OS prompt. Allowing GPS or not.
- **groupClicked** - Tracks when a user clicks on the shift group.
- **get_directions_clicked** - A user clicks the **Get directions** button.

### H

- **hideChannel** - Hide a channel from the teams and channel list.
- **hamburgerMenu** - Navigate to the hamburger menu. The hamburger menu contains important actions, such as account switch, notification settings, data setting, and profile settings.
- **hide** - Hide chat.
- **handoffComplete** - A meeting or call was handed off on this device.
- **handoffJoin** A meeting hand-off option is clicked on the action sheet.
- **hardwareAudioOff** - Turn audio off through the hardware buttons.
- **hardwareAudioOn** - Turn audio on through the hardware buttons.

### I

- **image** - Image.
- **importantMessage_select** - A user selects an important message from the priority context menu.
- **importantMessageSend** - A user sends an important message.
- **install** - Install or Install Event.
- **installReferrer** - Record app install referrer parameters after first time install.
- **inviteFreemium** - Tapping the **+** button in the Invite screen.
- **inviteGuest** - Tapping the **+** button in the Invite screen.
- **immediateCallForward** - Immediate call forward target is set, or enabling immediate call forwarding (Calls ring me is disabled).
- **inCallDialOut** - A user clicks the **Call me back** button from in-call more options.
- **initiatePhotoShare** - Initiate photo share.
- **initiateVideoShare** - Initiate video share.
- **invisionWhiteboardClicked** - Invision whiteboard is clicked on:
  - The channel files tab.
  - The meeting chat files tab.
- **importanceToggleClicked** - Triggers when the **!** field is toggled inside task item details.

### J

- **joinMeeting** - detects the success or failure of joining meetings from calendar in the following circumstances:
  - Join the meeting through Dial in.
  - Join the meeting through Call me back.
  - Join the meeting content only.
  - Click on meeting join button from agenda view.
- **joinTeam** - The **Join** button is pressed.
- **Launch source such as direct, link, appShortcut** - Launch directly or via link (record MAM/MDM telemetry on app launch to collect data for active users).
- **joinOptionsEdu** - An EDU user selects options to join a scheduled meeting and is shown the proper options.
- **joinViaCode** - A user joins a meeting via a code.
- **joinFromDeeplinkInTeams** - A user joined through a deeplink from within the Teams app.
- **joinFromDeeplinkOutsideTeams** - A user joined through a deeplink from outside the Teams app.
- **joinFromJoinLauncher** - A user joined from a Join Launcher.
- **joinFromNudge** - A user joined from nudge.
- **joinFromStore** - A user joined after downloading the app from the app store.

### L

- **leaveChat** - Confirm leaving chat.
- **legacyChatLink** - User taps on a link to legacy chat.
- **likeAppDismiss**
- **likeAppNo**
- **likeAppYes**
- **likeMsg** - Click on Like.
- **locationCard** - Click on a location card.
- **liveEventJoin** - A user joins a live event.
- **liveCaptions** - A user turns live captions on or off.
- **liveEventAdditonalLink** - An additional link is clicked.
- **liveEventInfo** - The **Info** button is clicked.
- **liveEventLeave** - The **Leave** button is pressed.
- **liveEventPresenterJoin** - A live event is joined by a presenter.
- **liveEventPresenterJoinAsAttendee** - A live event presenter joined as an attendee.
- **liveEventQnA** - The **Q&A** icon is clicked.
- **liveEventYammer** - The **Yammer** icon is clicked.
- **liveMeetingPushNotificationClicked** - Push notification is clicked.
- **liveMeetingToastClicked** - In-app toast is clicked.
- **lobbyPickAudio** - Number of times a user switches audio output from lobby.
- **lobbyToggleMuted** - Number of times a user turned the mic on or off from lobby.
- **lobbyToggleVideo** - Number of times a user turned video on or off from lobby.
- **linkPreviewCancel** - Understand the preview closure behavior.
- **labelSelected** - Confirms that a label has been successfully selected.
- **labelUnselected** - Confirms that a label has been successfully unselected.
- **labelPickerClicked** - Confirms that the label picker successfully launched.
- **load_chat_plans_list** - Confirms the successful fetching of planner plans for a chat's plan view.
- **load_personal_task_list** - Confirms the successful fetching of a personal tasklist's tasks for the tasklist view.
- **load_shared_task_list** - Confirms the successful fetching of a shared tasklist's tasks for the tasklist view.
- **load_smart_task_list** - Confirms the successful fetching of a smart tasklist's tasks for the tasklist view.
- **load_home_page** - Confirms the successful fetching of both personal and shared tasklists for the main home view.
- **location_data_use_privacy_granted**
- **location_data_use_privacy_denied**
- **location_settings_open**
- **location_sharing_start**
- **location_sharing_stop**
- **logOutClicked** - When a user logs out.
- **live_location_in_chats_from_profile_clicked** - A user clicks **live locations** in profile view.
- **location_settings_open** - A user opens location settings.
- **location_group_map_sync** - A user opens map view.
- **location_message_send** - A user initiates a location sharing session.
- **location_active_tracking** - A user's device is switched to active tracking.
- **location_map_load** - Map view load.
- **location_map_markers_load** - Map view load. Confirms that location markers for all users actively sharing are displayed properly on the map view.
- **location_family_sync** - Showing members of a Family group that were created in MSA family app. Confirms that all family members that can be granted consent are displayed.

### M

- **messagedEditMessage** - A user edits a message.
- **markChannelRead** - A user marks a channel read.
- **mapAppPicker** - Choose map app from map picker (TBD). ???
- **markAsRead** - Mark as read.
- **markAsUnread** - Mark as unread.
- **memberListLoadMore** - Scroll down to load more.
- **messageCopyMessage** - Copy Message.
- **messageDelete** - Message delete.
- **messageEditMessage** - Edit message.
- **messageForwardMessage** - User taps on Forward entry point from message context menu.
- **messageLike/messageUnlike** - Message like or unlike.
- **messageMuteSender** - Mute or unmute sender.
- **messagePriority_select** - A user selects Message priority entry point.
- **messageSeeOriginal** - A user reverts translated message back to original.
- **messageShareMessage** - Share a message.
- **messageTranslate** - A user translates a message.
- **messageUnabletoEdit** - A user is unable to edit a message.
- **multipleAccounts** - Number of accounts for a user.
- **multipleTenants** - Number of tenants per account.
- **mute** - Mute chat.
- **nameGroupChat** - Name group chat.
- **messageBookmarkMessage** - Connector card save. Uses existing telemetry with app specific data. Or save a bot message.
- **meetingJoinNowWithCallMe** - A user joins a meeting with **Call me**.
- **meetingJoinNowWithPSTN** - A user joins a meeting with Dial in.
- **manageBlockedNumbers** - Access blocked numbers through Settings.
- **maskCallerId** - User enables or disables calling setting to mask caller id.
- **meetingDetailChatWithParticipants** - Chat with participants from the Meeting detail page.
- **meetingDetailDeleteMeetingforSelf** - Delete a Meeting from Meeting Detail page for oneself.
- **meetingDetailJoin** - The **Meeting Join** button is tapped from Meeting Detail page.
- **meetingDetailParticipants** - See all participants from the Meeting Detail page.
- **meetingDetailSearchParticipants** - Clicked **Search** in meeting participants on the meeting schedule.
- **meetingJoinLeave** - Leave tapped -> **x** is tapped after the **Join** button is tapped.
- **meetingJoinNow** - **Join now for VOIP** tapped.
- **meetingLeaveChat** - Leave chat.
- **meetingMuteChat** - Mute chat.
- **meetingNotesCreatedInChatLink** - A user clicks on the **Meeting notes created** chicklet in private meeting chat or in channel meeting chat.
- **meetingNotesMentionCharLink** - A user clicks on the @mention link in private meeting chat.
- **meetingNotesMentionChatLink** - A user clicks on the @mention link in channel meeting chat.
- **meetingNotesTabEntryPoint** - A user clicks on the Meeting notes tab in private meeting or in a channel.
- **meetingNotificationSettingsAccepted** - Notification settings option was changed to Accepted only.
- **meetingNotificationSettingsAll** - Notification settings option was changed to All.
- **meetingNotificationSettingsNone** - Notification settings option was changed to None.
- **meetingSeeParticipantsChatDetails** - See all participants.
- **meetingUserAnonB2B** - Anonymous B2B joined the meeting.
- **meetingUserAnonB2C** - Anonymous B2C joined the meeting.
- **meetingUserDialIn** - PSTN (Dial in) user joined the meeting.
- **meetingUserDialOut** - PSTN Call me back user joined the meeting.
- **meetingUserFederated** - A federated user joined the meeting.
- **meetingUserFreemium** - A freemium user joined the meeting.
- **meetingUserGuest** - A guest user joined the meeting.
- **meetingUserTenant** - An in-tenant user joined the meeting.
- **messageScheduledMeeting** - Meeting object in channel tapped (Not only scheduled ones).
- **micPermissionCancel** - A user taps **Cancel** on the mic permission dialog.
- **micPermissionGoToSettings** - A user navigates to settings from the mic permissions dialog.
- **MicrosoftWhiteboardClicked** - Microsoft whiteboard is clicked on the Channel Files tabor the Meeting Chat Files tab.
- **multiCallEndFromUFD** - Number of times user ends the call on hold in a multi-call scenario.
- **multiCallResumeFromUFD** - Number of times a user clicks to resume a call from hold.
- **multiCallSwitch** - Number of times user clicks to switch the call and list of calls on hold shows up.
- **muteOnWhiteboard** - A user mutes or unmutes on the whiteboard screen.
- **muteParticipant** - Mute participant (move to the action sheet).
- **meetingDetailCalendarList** - Meeting Details page tapped from calendarList, or click on the **Details** tab on the Meeting Details page.
- **meetingDetailScheduledMeeting** - Meeting details page tapped from scheduled meeting object (**…**), or click on the **Details** tab of a scheduled meeting.
- **markAsLastUnread** - Connector card context menu.
- **messageLike** - Connector card like. Uses existing telemetry with app specific data.
- **moreOptionsClicked** - Triggers when **...** menu on the top-right is clicked on the task item editor screen.
- **moveTaskClicked** - Option inside task item more options list.
- **messageTriggered** - Triggered when the user's device time zone doesn't match the team time zone.
- **messageTriggered** - This is when a notification is triggered for a message.
- **myShiftPickerClicked** - Only logged if the request being sent is a swap or offer. Tracking user clicks into **My Shift** picker.
- **my_location_button_clicked** - User centers the map on their location by clicking on the **My location** button.
- **my_location_clicked** - A user centers the map on their location by clicking on the **blue dot** on the map.

### N

- **navCalendar**
- **navBookmark** - A user navigates to the Saved tab or app on the bottom bar or app tray.
- **navChat** - A user navigates to the Chat tab or app on the bottom bar or app tray.
- **navChatAndChannel** - Not used. ???
- **navDashboardTab**
- **navMore** - Not used. ???
- **navSaved** - A user navigates to the Saved tab or app on the bottom bar or app tray.
- **navCamera** - A user navigates to the Camera tab or app on the bottom bar or app tray.
- **navContacts** - A user navigates to the Contacts or People tab or app on the bottom bar or app tray.
- **navVideocamera** - A user navigates to the Camera tab or app on the bottom bar or app tray.
- **newChat** - A user creates a chat.
- **noBGActivityDetected** - Exceeds the threshold for background activity failures.
- **notBlockedDevice** - A user doesn't reach the threshold for background activity failures in 30 days.
- **nativeChatLink** - User taps on link to native chat.
- **navActivity, navChat, navTeams, navMore, navOrg, navFiles, navSaved, nav+(Appname)** - Nav Tab is clicked (or the hamburger menu is clicked - navMore).
- **navTeams** - Tap **See all**.
- **notNow** - User taps **Not now** in reminder.
- **notNowUpdate** - UpdateDefer.
- **navFiles**
- **navFilesTab**
- **navPersonalFiles**
- **navCallingSettings**
- **navVoicemail**
- **notificationNavPreCall** - User gets a notification of a meeting starts that navigates them to the precall screen on click.
- **navCalls** - Calls tab tapped.
- **navMeetings** - Calendar tab tapped.
- **navPhotoTab** - Photo tab.
- **navVideoTab** - Video tab.
- **newCall** - Taps **New call** button.
- **newCallDialPad** - Taps the **Dialpad** button on tab.
- **newCallPeople** - Taps the **People** button on tab.
- **navDynamics365** - Triggered when the user open the Dynamics365 app.
- **navNotes** - Triggered when the user open the Notes app.
- **navOrganization** - Triggered when the user open the Organization app.
- **navOrgChart** - Triggered when the user open the Orgchart app.
- **navTasks** - Triggered when the user open the Tasks app.
- **navWiki** - Triggered when the user open the Wiki app.
- **navActivity**- Navigate to the activity feeds page.
- **notificationError**
- **notificationNavChannelConversation**
- **notificationNavChannelThreadConversation**
- **notificationSettingTurnedOff**
- **navPeopleSettings** - This is not being sent in the newer builds. ???
- **navPeople** - Event is triggered when the user opens the People app.
- **navSelectPlan** - When a user selects a shared plan to navigate to from home view.
- **navSelectPersonalList** - When a user selects a personal plan to navigate to from home view.
- **navSelectSmartList** - When a user selects a smart plan to navigate to from home view.
- **navShifts**
- **navWalkieTalkie**
- **navVaultSettings**
- **navVault**

### O

- **officeLens**
- **openAppDrawer** - A user taps on **More** at the bottom bar to open the app drawer.
- **openHamburgerMenu** - A user taps on the **Hamburger** icon (top-left) to open the side menu for access to settings, presence, and tenant switcher.
- **officeLens or cameraImage** - Camera picture selected - standard camera or office lens.
- **open** - Notification Settings tap.
- **openContactCard_ReactionSummary** - Navigate to contact card from the reaction summary page.
- **openModalityPicker** - X = ChatsAndChannels for chats and channels.
- **openPhotoLibrary** - Click on photo library.
- **openQuietDays** - Navigate to Quiet Days page.
- **openQuietHours** - Navigate to Quiet Hours Page.
- **openReactionHoverBubble** - Press the **Add reaction** button on reaction summary page.
- **openReactionSummary** - Invoke reaction summary drawer.
- **openFile** - Helps:
  - To identify if user was able to open file in the chat successfully.
  - To identify if user was able to open file from files listing.
  - To check if user can open files from OneDrive list.
  - To identify if user can open files from channel list.
  - Tracking if user can open file from group chats.
  - Tracking if user can successfully open from files app.
  - To track if user can open from message file chiclet successfully.
  - To track if user can open files from recent list successfully.
  - To track if user can open file from file list successfully.
  - To track if user can open file from messages file chiclet.
  - To track if files can be opened successfully from file list.
- **openFileInApp** - Helps to identify if user opted to open files outside of Teams versus inside of Teams.
- **openInStream** - Open a video in Stream.
- **openSettingsSetUpInstructions** - Open **Settings** from instructions.
- **openEditMeetingForm** - Click on the **Edit** button from the Meeting Details page.
- **openMeetingDetails** - Open the meeting details or the Open Meeting details page of a particular meeting.
- **openNewMeetingForm** - Open the scheduler while setting up a new meeting.
- **refreshCalendarList** - Pull down to refresh agenda view.
- **oneNote** - Triggered when the user open the OneNote app.
- **openApp** - Opening a personal app.
- **orgChart - No AS assigned** - Basic usage telemetry for org chart.
- **open edit** - Wiki usage telemetry - User clicks to edit wiki.
- **openContactCard**
- **openNewMeetingForm** - Confirms a personal sub-task has been successfully updated.
- **onBackClicked** - Whenever a user clicks the back arrow to navigate back a page.
- **openInAppClicked** - Option inside task item more options list, only available for personal tasks.
- **ocvFeedback**
- **ocvFormCancelled**
- **ocvFormOpened**
- **ocvFormSubmit**
- **offerSwapShiftFromL1Triggered** - Register user's clock in or out. This will not trigger until you have checked the location, assuming location is required.
- **offerRecipientClicked** - Only logged if the request being sent is an offer. Tracking user clicks into the team member picker to offer a shift to. Offering means offering a shift time off.
- **offerRecipientClicked** - Only logged if the request being sent is an offer. Tracking user clicks into the team member picker to offer a shift to. Offering means offering a shift time off.
- **offerSwapShiftFromL1** - The type of shift a user tries to offer or swap from a shifts list. iOS action is a **SwipedRight** and Android action is **LongPressed**.
- **offerSwapShiftFromL1Triggered** - The type of shift a user tries to offer or swap from a shifts list. iOS action is a **SwipedRight** and Android action is **LongPressed** is triggered.
- **opensCalendarView** - Tracking user tapping on open shifts from Schedule tab.
- **openShiftsClicked** - How many people tap the **Calendar** icon.

### P

- **pushNotification** - Triggering events are:
  - Launch via notification.
  - Push notification clicked.
  - Reconnecting push notification is tapped.
  - **Reconnect failed** push notification is tapped.
- **processInBG** - Process incoming notification in the background (Android).
- **processInFG** - Process incoming notification in the foreground (Android).
- **pinChannel** - Pin a channel to show it above the teams and channels list.
- **photoLibraryPicker** - **Open photo library** tapped inside image picker.
- **provideFeedbackDismiss**
- **provideFeedbackNo**
- **provideFeedbackYes**
- **provideRatingDismiss**
- **provideRatingNo**
- **provideRatingYes**
- **preJoinDenied** - User is unable to join a meeting.
- **preJoinDialInCall** - User confirms **DIal in** request on prejoin.
- **preJoinDialInCancel** - User cancels **Dial in** request on prejoin.
- **preJoinDialOutCall** - User confirms **Call me back** request on prejoin.
- **preJoinDialOutCancel** - User cancels **Call me back** request on prejoin.
- **pauseVoicemail** - Pause tapped on a voicemail item.
- **pickGalleryPhoto** - Pick a photo from the gallery.
- **pickParticipantChatDetails** - Pick a user from the list.
- **pickRecentPhoto** - Chooses a recent image to share.
- **pinSelf** - Pin myself from the action sheet.
- **pinUser** - Pin a user from the action sheet.
- **play** - Play the recording.
- **playVoicemail** - Play tapped on voicemail item.
- **pptNextSlide** - Next slide as a presenter or in private viewing.
- **pptPreviousSlide** - Previous slide as a presenter or in private viewing.
- **pptReturnToPresenter** - Go to the **Live** slide (the one that the presenter and everyone else is on).
- **pptStopPresenting** - Stop presenting.
- **pptTakeControl** - Take control.
- **preJoinAddRoom** - User clicks the **Add a room** button in pre-join dropdown, or user clicks **Join** in the **Add a room** scenario.
- **preJoinAudioOff** - User clicks the **Audio off** button in pre-join dropdown.
- **preJoinAutoAddRoom** - User tapped **Join now** when room is nearby.
- **preJoinBack** - Back or Close button tapped.
- **preJoinDeviceAudio** - User tapped **Join with device audio** from dropdown.
- **preJoinDialIn** - User clicks the **Dial in** button in the pre-join dropdown.
- **preJoinDialOut** - User clicks the **Call me back** button the in pre-join dropdown.
- **preJoinPSTNOptions** - User clicks dropdown for other join options.
- **privateMeetingJoin** - **Meeting Join** button tapped from Private meeting chat.
- **promotedToPresenter** - User promotes an attendee - **Change** button in the dialog box.
- **proximityPermissionDismissed** - Permission banner is dismissed.
- **proximityPermissionGranted** - Permission is given on the pop-up.
- **proximityPermissionViewed** - Permission banner is tapped.
- **personalAppNavBotChat** - Navigate to the bot within personal app.
- **personalAppNavTab** - Navigate to tabs within personal app.
- **people**
- **peoplePickerInvoked**
- **priorityChange** - Triggers when priority filter is applied while viewing a tasklist.
- **priorityPickerClicked** - Triggers when a user navigates to a priority filter picker from the task list filter screen.
- **progressItemClicked** - Confirms a user has successfully opened the progress picker for a task.
- **parental_consent_grant**
- **parental_consent_remove**
- **pageEntered** - User was able to login.
- **plusButtonClicked** - Triggered when the user closes the banner message of a notification.
- **plusButtonClicked** - Tracking clicking the **plus button** to start a schedule, or to start a request on RequestList.sn.

### Q

- **quickSelectImagePicker** - Quick select.
- **quietHoursValues** - Capture Quiet Hours State on back button navigation.
- **quotedReplySent** - User sent a reply message with context type.
- **quickStartLiveEventJoin** - Quick start live event is joined by a user.
- **quickNotificationAction**

### R

- **removeUser_CM**
- **renewTeam** - Not used. ???
- **resolveIssue** - Users taps on **Resolve** in the notification troubleshooter flyout to navigate to the blocker app.
- **reorderChannelItem** - User reorders pinned channels.
- **reportAbuseOpen**
- **reactAngry_CM** - React with angry from the context menu.
- **reactAngry_HB** - React with angry from the hover bubble.
- **reactHeart_CM** - React with heart from the context menu.
- **reactHeart_HB** - React with heart from the hover bubble.
- **reactLaugh_CM** - React with laugh from the context menu.
- **reactLaugh_HB** - React with laugh from the hover bubble.
- **reactLike_doubleTap** - React with like from the double tap.
- **reactLike_HB** - React with like from the hover bubble.
- **reactSad_CM** - React with sad from the context menu.
- **reactSad_HB** - React with sad from the hover bubble.
- **reactSurprised_CM** - React with surprise from the context menu.
- **reactSurprised_HB** - React with surprise from the hover bubble.
- **readReceipts** - User enabled feature.
- **redeemInvite** - In app redemption.
- **removeReplyObject** - User removed reply object from compose.
- **removeUserConfirm** - User confirmed remove user dialog.
- **removeUserContextMenu** - User removed participant via context menu.
- **removeUserSwipe** - User removed participant via swipe.
- **replyChain** - Selected **New message** button or textbox in reply chain (thread).
- **replyChannel** - Selected **Reply** button in channels.
- **replyNavigation** - User tapped on reply object to navigate to referenced post.
- **replyViaMsgOptions** - User started reply via context menu.
- **replyViaSwipe** - User started reply via swipe.
- **requestJoinTeam** - **Request** button pressed.
- **requestToJoinTeam** - Request to join team (public or private).
- **requestToJoinTeamError** - Error with join request.
- **returnToMessage** - User tapped **Return** button to navigate back to message.
- **reactLike_CM** - React with like from context menu or like a bot message.
- **replySendMessage** - Send channel reply.
- **runningLate** - I am running late.
- **removeMeeting** - Click on **Remove from Calendar** from the Meeting Details page of a cancelled meeting.
- **removeParticipantFromEditMeeting** - Remove a participant after clicking on **Edit meeting** from the Meeting Details page.
- **removeParticipantFromNewMeeting** - Remove a participant from the scheduler page while setting up a new meeting.
- **reactRemoved_HB**
- **reportAbuseSend**
- **reportAbuseConfirmation**
- **removeAssignee** - Confirms that an assignee is removed from the assignment picker view (as opposed to *assignmentRemoved* which triggers when clicking **x** outside of assignment picker view).
- **removeUser** - Confirms that an assignee is removed from within the assignment picker view (as opposed to *assignmentRemoved* which triggers when clicking **x** outside of assignment picker view).
- **rename_personal_plan** - Confirms the successful renaming of a personal task list.
- **rename_planner_plan** - Confirms the successful renaming of a shared task list.
- **requestSent** - Logged if there was a request sent.
- **requestTypeClicked** - Tracking what type of request people select from the requests picker.
- **requestDetailsClicked** - When the request for a shift is clicked (either FLW manager viewing or FLW worker)
- **requestActedOn** - Tracks when the manager acts on open shift requests.
- **requestActionClicked** - When a user requests an action, such as when the request for a shift is clicked (either FLW manager viewing or FLW worker)
- **requestSent** - Tracks when the user requests an open shift.
- **requestTypeClicked** - Tracking what type of request people select from the requests picker, or the request type that the user clicks.
- **retryButtonClicked** - When a user clicks on the retry button.

### S

- **scrollCalendarList**
- **shareInto** -- A user shares something from another app into Teams.
- **scrollDatePicker**
- **selectCalendarDate**
- **safeLink** - Link verified as safe.
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
| statusMsgCancel | User cancels change to status message | Basic | Feature success metrics for add status message feature | App key feature success data   |
| statusMsgExpiry | User sets expiry time | Basic | Feature success metrics for add status message feature | App key feature success data   |
| statusMsgSet | User sets new status message | Basic | Feature success metrics for add status message feature | App key feature success data   |
| statusPageViaContactCard | User enters status compose experience via contact card | Basic | Feature success metrics for add status message feature | App key feature success data   |
| statusPageViaHamburger | User enters status compose experience via hamburger | Basic | Feature success metrics for add status message feature | App key feature success data   |
| selectActivityType | Captures select gestures on feed item | Basic | <ul><li>Helps to check if user was able to initiate download operation</li><li>Helps to track if user can download file successfully</li></ul> | App key feature success data   |
| shareFile | <ul><li>User clicks **Share file**</li><li>Helps to check if user was able to initiate share file operation</li><li>Helps to track if user can share a file successfully</li></ul> | Basic | <ul><li>Helps to check if user was able to initiate share file operation</li><li>Helps to track if user can share a file successfully</li></ul> | App key feature success data   |
| structuredMeetingsBannerDismiss | User dismisses banner that informs them about their meeting role | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
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
| saveEditMeeting | Click on the **Save** button while on the meeting scheduler page after updating a meeting | Basic | To log succesfully saved meetings or those that  failed to update | App key feature success data   |
| saveNewMeeting | Click on the **Save** button while on the meeting scheduler page | Basic | To log succesfully saved meetings and the percentage of meetings that failed to create due to a client side or service error | App key feature success data   |
| searchMeetingParticipants | Search for participants to add within the scheduler form | Basic | To distinguish between the number of appointments created versus the number of meetings created | App key feature success data   |
| seeAllMeetingParticipants | <ul><li>Click on **See All** from the meeting details page</li><li>View all participants</li></ul> | Basic  | Telemetry to log user data across the calendar funnel, where calendar meeting details play an important role, that helps validate clicks on Dial ins, Teams meetings, RSVP clicks, etc.. | App key feature success data   |
| seeMeetingDescription | <ul><li>Opening the Meeting Details page</li><li>Click **See More** on the Meeting description from the Meeting Details page | Basic | Telemetry to log user data across the calendar funnel, where calendar meeting details play an important role, that helps validate clicks on Dial ins, Teams meetings, RSVP clicks, etc.. | App key feature success data   |
| seeRsvpMeetingOptions | <ul><li>Click on **Notify Organizer** from the RSVP pop up</li><li>Click on **Rsvp** options from the Meeting Details page | Basic |     | App key feature success data   |
| selectMeetingRsvpOption | Click on the **RSVP** button to choose an option | Basic |     | App key feature success data   |
| selectMeetingRsvpOptions | Click on the **RSVP** button to choose an option | Basic |     | App key feature success data   |
| showCard | Tap on card buttons. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| searchAbandoned | Helps to track if search was successful versus if user abandoned search | Basic | Helps to track if search was successful vs if user abandoned search | App key feature success data   |
| searchCancelled | <ul><li>Helps to track if search was successful vs if user abandoned search</li><li>Helps to track if search query was successful</li></ul> | Basic | <ul><li>Helps to track if search was successful vs if user abandoned search</li><li>Helps to track if search query was successful</li></ul> | App key feature success data   |
| searchIcon | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li><li>Helps to track if user can find relevant results successfully</li></ul> | Basic | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li><li>Helps to track if user can find relevant results successfully | App key feature success data   |
| searchInitiated | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li></ul> | Basic | <ul><li>Helps to track if search can be triggered</li><li>Helps to track source of search trigger</li></ul> | App key feature success data   |
| searchResultsClicked | <ul><li>Helps to track if user can find relevant results successfully</li><li>Tracking usage of core scenario</li><li>Helps to track if search results was from ALL tab vs individual domain</li></ul> | Basic | <ul><li>Helps to track if user can find relevant results successfully</li><li>Tracking usage of core scenario</li><li>Helps to track if search results was from ALL tab vs individual domain</li></ul> | App key feature success data   |
| searchTab | <ul><li>Helps to track domain information of the search result - people/chat/messages/files</li><li>Helps to track if search results was from ALL tab vs individual domain</li></ul> | Basic | <ul><li>Helps to track domain information of the search result - people, chat, messages, files</li><li>Helps to track if search results was from ALL tab versus individual domain</li></ul> | App key feature success data   |
| searchTabClicked | <ul><li>Helps to track domain information of the search result - people/chat/messages/files</li><li>Helps to track if user can find relevant results successfully</li></ul> | Basic | <ul><li>Helps to track domain information of the search result - people, chat, messages, files</li><li>Helps to track if user can find relevant results successfully</li></ul> | App key feature success data   |
| sharePlanToChat | A shared list is manually shared from the tasks app to the group chat as a chiclet, check chicklet sent via backend messaging  service | Basic | Confirms that a chiclet is successfully sent to the chat when a task list is shared in a group chat | Key App feature success data   |
| statusCheckBoxClicked | Triggers when task item is either completed or uncompleted | Optional |     |     |
| sortChanged | Triggers when user changes sort order while viewing a tasklist | Optional |     |     |
| savePlanClicked | Trigger when user cliks **Create** in the new plan creator from default opening of app | Optional |     |     |
| selectUser | Confirms that an assignee was successfully selected for a task | Optional | Confirms that an assignee was successfully selected for a task |     |
| selectPlannerList | Confirms that the user successfully navigated to a shared task list by tapping it | Optional | Confirms that the user successfully navigated to a shared task list by tapping it |     |
| selectPersonalList | Confirms that the user successfully navigated to a personal task list by tapping it | Optional | Confirms that the user successfully navigated to a personal task list by tapping it |     |
| shiftDetailsTodaysCoworkers | On the clock in screen, user clicks on Start or End break button. | Basic | Key functionality for shifts details feature | App key feature success data   |
| shiftDetailsCalendar | On the clock in screen, user clicks on the **Clock In** or **Clock Out** button. | Basic | Key functionality for calendar feature. | App key feature success data   |
| shiftDetails | This is to see the details of the shift. | Basic | Key functionality for request feature. | App key feature success data   |
| sendRequestClicked | This instrumentation is logged for every individual request | Basic | Key functionality for request feature. | App key feature success data   |
| shareShiftsClicked | The details of an open shift. | Basic  | Key functionality for share shifts feature. | App key feature success data   |
| sendRequestBulkClicked | This instrumentation point is logged once for each bulk request send. In addition, each individual request will log an event. | Basic | Key functionality for request bulk feature. | App key feature success data   |
| sendRequestBulkClicked | This instrumentation point is logged once for each bulk request send. In addition, each individual request will log an event. | Basic | Key functionality for feature, send shifts. | App key feature success data   |
| sendRequestClicked | This instrumentation is logged for every individual request | Basic | Key functionality for feature, send shifts. | App key feature success data   |
| shareShift | The information that is given when a shift is shared. | Basic | Key functionality for feature, share shifts. | App key feature success data   |
| shareShiftsClicked | The details of an open shift. | Basic | Key functionality for feature,shifts. | App key feature success data   |
| shiftAssigneeClicked | The Shifts Calendar view showing the particular shifts details | Basic | Key functionality for feature, shifts. | App key feature success data   |
| shiftDetails | Your own shifts. | Basic | Key functionality for feature, shift shifts. | App key feature success data   |
| shiftDetailsCalendar | Triggered whenever a user receives a notification from a specific team and potentially wants to switch to that particular team. | Basic | Key functionality for feature, switch shifts. | App key feature success data   |
| shiftDetailsMyShifts | Tracking user tapping on **Calendar** from Schedules Tab | Basic | Key functionality for feature, tab shifts. | App key feature success data   |
| switchTeamsDialogTriggered | User views Shifts tab | Basic | Key functionality for feature, tab shifts. | App key feature success data   |
| send_map_pin_clicked | User sends static location | Basic | Confirms that user successfully shared a static location | Key App feature success data   |
| static_place_selected | User drags map to select a static place | Basic | Confirms that user successfully selected a static place by interacting with the map | Key App feature success data   |
| suggested_place_selected | User shares a static location by selecting a suggested place | Basic | Confirms that user successfully shared a static location by selecting a suggested place | Key App feature success data   |
| stop_location_sharing_logout | User logs out of the app | Basic | Confirms that we successfully stopped all location sharing session when the user logged out of the app | Key App feature success data   |
- **shortCircuitContactCount**

### T

| teamCreate | User selects the option to create a new team | Basic | Track team creation | App key feature success data   |
| teamEdit | User edits some aspect of a team that they own or administer | Basic | Track team or channel management | App key feature success data   |
| tapDatePickerHandle |     |     |     |     |
| table | Click on table | Basic | How many people tap on table in chat or channel conversation | App key feature success data   |
| takePhotoPicker | **Take photo** tapped inside image picker | Basic | Feature success metrics for camera integration in image picking experience | App key feature success data   |
| teamNav | View menu options for team |     |     |     |
| tenantSwitch | On Switch Tenant | Basic | Feature success metrics for MTMA (multiple tenant and multiple account) feature, this helps identify and fix issues proactively and provide a smooth switching experience | App key feature success data   |
| tenantSwitchUnsupportedError | Tenant Unsupported Error (when user sees the error) | Basic | Feature success metrics for MTMA, provides telemetry around account or tenant switch errors, so we can identify and fix issues proactively and provide a smooth switching experience | App key feature success data   |
| toggleChannelsInChat | Turn feature on or off | Basic | Feature success metrics for unified chats and channel experience | App key feature success data   |
| translateFailed | Translation failed (excluding offline) | Basic | Feature success metrics for message translation feature | App key feature success data   |
| takePhoto | Take a photo | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| toast | In-app toast clicked | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| transferNow | <ul><li>Taps Transfer > Transfer now</li><li>Transfer target set to Person</li><li>Transfer target set to Phone Number</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
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
| teamsDeviceCallResumed  |             | Basic | Used to track success or failure of a feature and customer engagement | App key feature success data   |
| tasksAppLaunchDefault | Tasks app is opened from the bottom drawer, check app launch via MT service | Basic | Confirms that the tasks app is successfully launched from the app bar | Key App feature success data   |
| tasksAppLaunchDashboard | Tasks app is opened from the dashboard tile or specific plan, check app launch via MT service | Basic | Confirms that the tasks app is successfully launched from the dashboard | Key App feature success data   |
| tasksAppLaunchDashboardSeeAll | Tasks app is opened from the dashboard **See all** button, check app launch via MT service | Basic | Confirms that the tasks app is successfully launched from the **See All** button of the dashboard | Key App feature success data   |
| tasksAppLaunchAdaptiveCard | Tasks app is opened from an adaptivecard in a group chat, check app launch via URL of IC3 service | Basic | Confirms that the tasks app is successfully launched by clicking on a chiclet previously sent to the group chat | Key App feature success data   |
| tasksAppLaunchComposeExtension | Tasks app is opened from the compose extension in a group chat, check app launch via MT service | Basic | Confirms that the tasks app is successfully lanuched from a compose extension | Key App feature success data   |
| teamChannelChanged | Triggered when user clicks and navigates to a plan from plan list. Only sent to appInsights, not Aria | Optional |     |     |
| titleChanged | Triggers when task item title changes, triggers on every character change | Optional |     |     |
| timeOffReasonClicked | This it to track if you cited a reason for time off. | Basic | Key functionality for time off feature. | App key feature success data   |
| toggleClicked | To view a declined time off request. | Basic | Key functionality for shifts reminder feature | App key feature success data   |
| teamShiftPickerClicked | When the user adds a new break entry. Log the event once the user saves the changes | Basic | Key functionality for shift picker feature. | App key feature success data   |
| teamSelectedClicked | When the user clicks on **Add** on a timesheet | Basic | Key functionality for team selected feature. | App key feature success data   |
| tabCalendarClicked | User has chosen a team from the team picker | Basic  | Key functionality for feature, team shifts. | App key feature success data   |
| tabViewed | Only logged if request being sent is a swap. Tracking user clicks into **Team Shift** picker | Basic | Key functionality for feature, team shifts. | App key feature success data   |
| teamSelectedClicked | When the user clicks on Add on a timesheet | Basic  | Key functionality for feature, timesheet shifts. | App key feature success data   |
| teamShiftPickerClicked | When the user adds a new break entry. Log the event once the user saves the changes | Basic | Key functionality for feature, timesheet shifts. | App key feature success data   |
| timesheetAddClicked | When the user adds a note to their break edits. Log the event once the user saves the changes. | Basic | Key functionality for feature, timesheet. | App key feature success data   |
| timesheetBreakAdded | When the user adds a new clock entry. Log the event once the user saves the changes | Basic | Key functionality for feature, timesheet. | App key feature success data   |
| timesheetBreakEdited | When the user confirms their timesheet. Log the event when the user hits confirm in the modal | Basic | Key functionality for feature, timesheet. | App key feature success data   |
| timesheetBreakNoteAdded | When the user deletes their timesheet. Log the event when the user confirms the delete in the modal. | Basic | Key functionality for feature, timesheets. | App key feature success data   |
| timesheetClockAdded | When the user clicks on Edit for a timesheet. | Basic | Key functionality for feature, time sheets. | App key feature success data   |
| timesheetClockEdited | When the user clicks save on an edited timesheet | Basic | Key functionality for feature, timesheet shifts. | App key feature success data   |
| timesheetConfirmed | When the user adds a note to their timesheet edits. Log the event once the user saves the changes | Basic | Key functionality for feature, timesheetnote shifts. | App key feature success data   |
| timesheetDeleted | If a user does or does not have a shift reminder set, and the amount of minutes before a shift a user wants to be alerted. | Basic | Key functionality for feature, reminders. | App key feature success data   |
| timesheetEditClicked | User Configuration telemetry. | Basic | Key functionality to set up user information. | App key feature success data   |
| timesheetEditSaved | User taps on time sheet from a users profile to open that users time sheet. | Basic | Key functionality for feature, time sheets. | App key feature success data   |
| timesheetNoteAdded | To view an approved time off request. | Basic | Key functionality for feature, approve time off. | App key feature success data   |
| toggleClicked | To view a declined time off request. | Basic | Key functionality for feature, decline time off. | App key feature success data   |

### U

| unpinChannel | Unpin a channel | Basic | Track channel engagement | App key feature success data   |
| unsafeLink | Link was determined to be unsafe | Basic | Feature success metrics for ATP Safe Links | App key feature success data   |
| upgrade | Taps the **Upgrade** button in **More** menu | Basic | Feature success metrics for freemiums as this would provide information about the number of successful conversations | App key feature success data   |
| urgentMessageSelect | User selects urgent message from priority context menu | Basic | Feature success metrics for priority messages | App key feature success data   |
| urgentMessageSend | User sends urgent message | Basic | Feature success metrics for priority messages | App key feature success data   |
| url | url | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreview | Url preview | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreviewAdd | URL preview add | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreviewOpen | URL preview open | Basic | Feature success metrics for url preview | App key feature success data   |
| urlPreviewRemove | URL preview removed | Basic | Feature success metrics for url preview | App key feature success data   |
| uploadSelectedFile | <ul><li>Tracks if user can upload files in channel successfully</li><li>Tracks if user can upload files in chat successfully</li><li>Tracks if user can upload files in the reply window</li><li>Tracks if user can upload files successfully in group chat</li><li>Tracking usage of core scenario</li><li>Tracks the start of upload scenario in channel</li><li>Tracks the start of upload scenario in chat</li><li>Tracks the start of end of upload scenario in channel</li><li>Track if user can upload file into files tab successfully</li><li>Helps to identify is user acted on the prompt during file upload</li><li>Helps to identify if user can upload selected file successfully</li></ul> | Basic/Full | <ul><li>Tracks if user can upload files in channel successfully</li><li>Tracks if user can upload files in chat successfully</li><li>Tracks if user can upload files in the reply window</li><li>Tracks if user can upload files successfully in group chat</li><li>Tracking usage of core scenario</li><li>Tracks the start of upload scenario in channel</li><li>Tracks the start of upload scenario in chat</li><li>Tracks the start of end of upload scenario in channel</li><li>Track if user can upload file into files tab successfully</li><li>Helps to identify is user acted on the prompt during file upload</li><li>Helps to identify if user can upload selected file successfully</li></ul> | App key feature success data   |
| uploadSelectFile | <ul><li>Tracks if the user can select file successfully</li><li>Tracks if the user can select upload file button successfully</li></ul> | Basic | <ul><li>Tracks if the user can select file successfully</li><li>Tracks if the user can select upload file button successfully</li></ul> | App key feature success data   |
| userJoinedViaShareLink | User joined a meeting from a link | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| unansweredCallForward | <ul><li>Unanswered call forward target is set</li><li>Enable unanswered call forwarding (Calls ring me is enabled and If unanswered is enabled)</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| unblockCaller | <ul><li>Unblock contact or number from action sheet</li><li>Unblock contact or number from contact card</li><li>Unblock number from settings</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| unpinSelf | Unpin yourself from action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| unpinUser | Unpin user from action sheet | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| updatePlaybackSpeedVoicemail | Voicemail playback speed value changed | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| uploadFile | User clicks **Upload from device** | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| userLongPress | Long press on a participant | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| useWifiForAudioDialog | User clicks **OK** while system prompts that while Admin has blocked audio and video calls on cellular | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| useWifiForVideoDialog | <ul><li>User clicks **OK** while system prompts that while Admin has blocked video calls on cellular</li><li>User trying to enable video in meeting while Admin has blocked it on cellular</li><li>User clicks **OK** while system prompts that while Admin has blocked video in meetings on cellular</li></ul> | Basic | Used to track feature success or failure of a feature and customer engagement | App key feature success data   |
| unblockChat | Unblock a bot chat.This is enhancing existing telemetry around chats and is only adding app information. | Optional | Used to track feature success or failure of a feature and customer engagement |     |
| updateTask | Confirms update tasks action failed | Basic | Confirms that a when a user edited or updated a task failed | Key App feature success data   |
| updatePersonalTask | Confirms a personal task has been successfully updated | Basic | Confirms a personal task has been successfully updated | Essential Service - Telemetry   |
| updatePlannerTask | Confirms that a user has successfully updated a task in a shared taks list | Basic | Confirms that a user has successfully updated a task in a shared taks list | Essential Service - Telemetry  |
| updateTaskState | Confirms that the task state has been updated | Optional | Confirms that the task state has been successfully updated |     |
| update_planner_task_and_nav_to_view | Confirms successful updating of a shared task item and how long it took for user to land on resulting view after action | Basic |     | App key feature success data   |
| update_personal_task_and_nav_to_view | Confirms successful updating of a personal task item and how long it took for user to land on resulting view after action | Basic |     | App key feature success data   |
| userConfiguration | To view a pending time off request. | Basic | Key functionality for feature, time of requests. | App key feature success data   |

### V

- **videoUserDoubleTap** - Double tap on a video participant.
- **viewChannelMembers** - View a channel members list to track channel engagement.
- **viewContactCard** - ContactCard tapped from:
  - A callHistory item.
  - A voicemail item.
  - A call list.
- **viewed** - User was unable to login.
- **viewFullAllDayMeetingList** - Agenda view on Mobile.
- **viewLobbyFromBanner** - The number of times user clicks on **View lobby** from a notification banner.
- **viewMeetingDetails** - Click on the **...** menu on the Meeting Details page. Pertaining to the usage of the **More** menu on mobile calendars.
- **viewMeetingOccurrence** - Open up the meeting details of an instance of a recurring meeting. Telemetry to log user data across the calendar funnel, where calendar meeting details play an important role, that helps validate clicks on Dial ins, Teams meetings, RSVP clicks, and so on.
- **viewMeetingSeries** - To log the successful rendering of a meeting series in the following circumstances:
  - When switching from an instance to the series meeting detail page.
  - When clicking on **View series** from the meeting details page.
- **viewOrgChart** - Basic usage telemetry for an org chart.
- **viewRequests** - The **View requests** button is pressed.
- **voiceDataCollectionOptOut** - A user opts-out of the recording from mobile by clicking the banner.
- **voicemail - No AS Assigned** - A speaker taps on a voicemail item.

### W

- **whiteboardUsed** - User annotates on a whiteboard (any action on the webview).
- **wiki - No AS assigned** - Wiki usage telemetry.

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
