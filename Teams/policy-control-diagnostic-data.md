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

### PanelAction

> [!NOTE]
> For information on the properties of PanelAction events, see [Properties sent with panelaction events](#properties-sent-with-panelaction-events).

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
- **BYOELiveEventJoin** - BYOE live event is joined by a user.
- **calendarLiveChatClicked** - Chat from live meeting on the Schedule tab.
- **calendarMeetingJoin** - **Meeting Join** button tapped from a Calendar.
- **calendarTab** - Click on the **Meetings** tab in the bottom rail. Useful in understanding the calendar usage and compare with other apps on the bottom rail or to determine if there was a failure in rendering the calendar post after a click from the bottom bar.
- **calendarTabClicked** - In the circumstances listed below, this will show calendar usage and allow you to compare with other navbar apps on the bottom rail. This can be used to determine if there was a failure when:
  - The Schedule tab is shown.
  - A user clicks on the **Meetings** tab in the bottom rail.
- **calendarUpcomingChatClicked** - Chat from an upcoming meeting on the Schedule tab.
- **callAccepted** - Call accepted.
- **callAcceptedSFB** - Call accepted.
- **callAppPreference** - A preferred calling App is selected.
- **callControlsManualDismiss** - Call controls are dismissed manually (user action).
- **callControlsManualInvoke** - Call controls are invoked manually (user action).
- **callHistoryItemExpand** - Call History Item expanded.
- **callHistoryTab** - CallHistoryTab is selected in Calls.
- **callInProgressShown** - A ***Call in progress** banner is shown.
- **callMePSTNConnected** - **Call me** is successful.
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
- **callOrMeetUpAddParticipantsDone** - A user finalizes their participant addition.
- **callOrMeetUpAddRoom** - Triggered when:
  - User taps **Add room** in roster.
  - User selects a search result in add room.
  - User taps **Dismiss** for Nearby.
  - User taps **Enable BT** or **Location** for Nearby.
  - User selects a nearby room result in add room.
  - User selects a suggested room result in add room.
  - User taps **Done** in add room.
- **callOrMeetUpAudioOffSwitch** - Flip **Audio off** button while in companion join mode in a live call or meetup.
- **callOrMeetUpAutoReconnect** - Poor network performance causes a user's device to go into Autoreconnect mode.
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
- **callOrMeetUpMuteParticipant** - User mutes a remote participant.
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
- **callsTabNewCall** - User selects **New Call** in the **Calls** tab.
- **callTransfer** - User starts a call transfer.
- **callVoicemailTab** - VoicemailTab selected in Calls.
- **cameraPermissionCancel** - A user taps **Cancel** on the camera permission dialog.
- **cameraPermissionGoToSettings** - A user navigates to **Settings** from the camera permissions dialog.
- **cancelEditMeeting** - Click on the **Close** button while on the meeting scheduler page, after clicking **Edit meeting**. This logs abandoned edit meeting clicks.
- **cancelFileShare** - A user clicks **Cancel** on the confirmation dialog.
- **cancelFileUpload** - A user clicks **x** on the upload dialog.
- **cancelMeeting** - Click on **Cancel event** from the meeting details page. Used to get aggregated data on the number of cancelled meetings.
- **cancelNavigationToLink** - A user chose to cancel navigation.
- **cancelRequestToJoinTeam** - Cancel request to join a team.
- **cancelRequestToJoinTeamError** - Error with a cancel join request.
- **cancelNewMeeting** - To log abandoned Create meeting clicks and verify what caused them when:
  - A user clicks on the **Close** button while on meeting scheduler page.
  - A user clicks on the **Close** button while on meeting scheduler page after clicking **Edit meeting**.
- **cardView - No AS assigned** - Card view and card rendering. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side. This item is required to measure any error with joining a team.
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
- **center_on_team_clicked** - User centers map on groups, this event confirms that user successfully centered the map on the group.
- **channelFollow** - Turn on notifications for a channel.
- **channelUnfollow** - Turn off notifications for a channel.
- **channelsActiveSetting** - A user changes their **notify me when I'm active on desktop** notification setting.
- **chatCreation** - A user creates a chat, this tracks the success of chat creation.
- **changeIsActiveSetting** - Change desktop activity based notification.
- **channel** - New message button or textbox in chat.
- **channelDetails** - Channel navigation information for when:
  - A user taps on channel header.
  - A user navigates to channel details page.
- **channelFollow/channelUnfollow** - Follow or unfollow a channel.
- **channelNav** - Navigating to a channel from anywhere.
- **channelNavTab** - Provides success and discoverability data for files in Teams when:
  - A user clicks on **Files** tab in channel
  - There is a connector card reply.
- **channelNotificationSettings** - Triggered when a user:
  - Responds to **New Notification settings** dialog.
  - Taps channel notification settings button in channel view.
  - Selects a channel notification setting.
- **channelSelected** - Confirms that a channel was successfully selected for a new plan.
- **channelSendMessage** - Triggered when:
  - A channel message is sent.
  - A bot is @mentioned in a compose box.
- **channelTabOverflow** - Clicks on the **More** tab in a channel.
- **chat** - Refers to:
  - A new message button or textbox in chat.
  - 1:1 chat tapped on callHistory item.
  - A 1:1 chat click from call list.
- **chat - No AS Assigned** - Viewing unread chat or editing the chat roster, specifically:
  - Selecting the **Done** button when adding a user to a chat.
  - A user taps on a chat list filter to filter by unread.
- **chatAddChat** - Add a member to chat button tapped (this will be same for 1:1 chat and group chat).
- **chatAvatarEdit**
- **chatAvatarEditCamera**
- **chatAvatarEditGallery**
- **chatAllowJoinViaLink**
- **chatAvatarEditView**
- **chatListNavConversations** - ChatList navConversations. ???
- **chatCancelAudioCall** - Cancel a group audio call - Confirm dialog.
- **chatCancelVideoCall** - Cancel a group video call - Confirm dialog.
- **chatCM_CopyText** - Tap **Copy text** on a chat context menu.
- **chatCM_DeleteMessage** - Tap **Delete message** on a chat context menu.
- **chatCM_edit** - Tap **Edit** on a chat context menu.
- **chatCM_Forward** - Tap **Forward** on a chat context menu.
- **chatCM_markUnread** - Tap **Mark as unread** on a chat context menu.
- **chatCM_save** - Tap **Save** on a chat context menu.
- **chatCM_SeenBy** - Tap on **Seen** on a context menu option. Read Receipts, such as read by (readby).
- **chatContactsEnter** - User enters the chat contacts tab.
- **chatDetails** - Provides success and discoverability data for a chat details page when:
  - A user taps on a chat header.
  - A user navigates to a chat detail page.
- **chatRecentEnter** - A user enters the chat recent tab.
- **chatSendMessage** - Send a chat message.
- **chatShareLink**
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
- **chatWithMeetingParticipants** - Clicks on **Chat** tab from Meeting Details page.
- **checkListAddClicked** - A user clicks **Add an item** inside task details view for checklist section.
- **checkListItemAdded** - A user creates a checklist item for task.
- **checkListItemDeleted** - A user deletes a checklist item from the task.
- **checkListItemUpdated** - A user updates a checklist item for task.
- **channelPickerClicked** - Confirms that the channel picker successfully launched.
- **checklistSeeAllClicked** When a user clicks the **See All** button inside task details to view all checklist items.
- **chicletExpand** - Understand how users preview cards on mobile, and the preview closure behavior.
- **clearFilter** - When a user clears all filters while viewing a tasklist.
- **clickPhotoOfficeLens** - Click on **Take photo** - Launch camera (Android only).
- **clockInOutClicked** - On the clock in screen, user clicks on the **Clock In** or **Clock Out** button.
- **clockInOutTriggered** - Register user's clock in or out. This will not trigger until you have checked the location, assuming location is required.
- **closedBannerMessage** - Triggered when a user closes the banner message of a notification.
- **closeLobbyBanner** - Number of times a user closes the lobby toast using its **Close** button.
- **commentAdded** - Confirms that a comment was added to a task.
- **commentsClicked** - Confirms that the comments view was successfully launched.
- **commentUpdated** - Confirms that a comments was successfully updated on a task.
- **companionBannerJoin** - Click **Join** on the top-level banner.
- **companionDismiss** - Dismiss the companion banner.
- **companionDismissProximity** - Dismiss the companion banner.
- **companionJoin** - Join as companion option is clicked on the sheet.
- **companionJoinProximity** - Joined through tje companion banner.
- **completionStateChange** - Triggers when a completed or uncompleted filter toggle is clicked in filter view from task list.
- **composeExpandComposer** - **Format** button tapped.
- **composeFilePick** - Native file picker launched.
- **composeImagePicker** - **Image** button tapped.
- **composeLocation** - **Location** button tapped in compose.
- **composeMention** - @mention.
- **composeOpenEmoticonPicker** - Emoticon picker tapped.
- **composeOpenFunPicker** - Fun picker tapped.
- **composeParticipantAdded** - When a user adds a participant to the Shifts app.
- **composeSearchResult** - Message extension result selection, which is helpful to understand the app search result relevance. Also enhances message send telemetry with app data.
- **composeSelectExtension** - Tap on a ME app.
- **composeSendMessage** - Enhances message send telemetry with app data.
- **composeVault**
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
- **consumeVoiceMessage** - Voice message played.
- **ContactCard_SeeMoreOOF** - See more of a long OOF message.
- **contactOrganizer** - Clicked **Contact organizer**.
- **conversation, tabs** - Tab clicked.
- **copyLink** - Copy a link to a channel post.
- **contactActivity**
- **conversation**
- **createChannel** - Provides success data around the successful creation or discard action for new channel creation, when a user:
  - Taps the **Done** button on the **Create Channel** Page.
  - Taps the **Cancel** button on the **Create Channel** Page.
- **createComposeExtension** - Create message extension usage, or action ME usage.
- **createConversationClicked** - When a user creates a conversation with other workers.
- **createDefaultPlannerPlan** - A shared list is created automatically when the Tasks app is opened for the first time by anyone in that group, checks auto list created with Planner service. Confirms the default shared task list is successfully created in Planner the first time a user attempts to create a shared task list.
- **createOrJoinTeam** -A user taps the **+** button to create or join a team this tracks team creation and joins.
- **createPersonalPlan** - A personal list is created, checks list created with ToDo service. Confirms a new personal task list is created in ToDo.
- **createPersonalSubtask** - Confirms a personal sub-task has been successfully created.
- **createPersonalTask** - Confirms a personal task has been successfully created.
- **createPlan** - Confirms that a shared task list has been successfully created. Confirms that a shared plan has been successfully created through middle tier.
- **createPlannerPlan** - A shared list is created, checks list created with Planner service. Confirms a new shared task list is created in Planner.
- **createPlannerTask** - Checks a call to the Planner service. Confirms that a user has successfully created a task in a shared tasks list.
- **createShiftClicked** - When a manager clicks to creates a shift.
- **createShiftOrTimeOffClicked** - Triggered if you click **Create a shift** or **Time off**.
- **createTask** - Used for when create action fails, checks call to Planner service. Confirms a task create operation failed.
- **createTaskList** - When a user navigates to the create plan view from home view.
- **createTeam** - Provides success data around the successful creation or discard action for new team creation, when a user:
  - Taps the **Done** button on the **Create Team** Page.
  - Taps the **Cancel** button on the **Create Team** Page.
- **createTeam, createChannel** - This provides success data around the successful addition of members in a team and the successful creation of a new team under the following circumstances: ???
  - A user taps the **Skip** button in the **Add Members** page (check existing first).
  - A user taps the **Done** button in the **Add Members** page (check existing first).
  - Shows team or channel creation acknowledgement.
- **crossCloudDialogCancel** - A user clicks **Cancel** on a cross-cloud dialog.
- **crossCloudDialogJoin** - A user clicks **Join as guest** for a cross-cloud dialog.
- **dashboardNav**
- **dateChanged** - Changing dates that are shown in a calendar view to view shifts.
- **dayClicked** - Clicking the day view when user is seeing their Shifts. It's a key functionality for feature calendar and viewing day shifts.
- **datePickerLaunch** - Confirms that date picker was successfully launched.
- **daySaved** - A user saves the day availability, saves a day of Shifts.
- **declineTimeOffRequest** - When a user declines the request for time off of work. It's a key functionality for time off, for manager to reject time off request.
- **deleteClicked** - When a user clicks **Delete** within task details, which brings up the confirmation dialog.
- **deleteContact**
- **deleteMeeting** - Click on the **Delete** button from the Meeting Details page.
- **deletePersonalTask** - Confirms a personal task has been successfully deleted.
- **deletePersonalSubtask** - Confirms a personal sub-task has been successfully deleted.
- **deletePlannerTask** - Confirms that a shared task delete operation completed successfully.
- **deleteShift** - Tracks when the user deletes a shift.- **duration_picker_dismissed** - A user dismisses the duration picker.
- **deleteTask** - Verifies with the Planner service as to whether a delete action was successful or unsuccessful. Confirms that a task delete failed, that is, the deletion of a task was unsuccessful.
- **deleteVoicemail** - Delete voicemail item tapped.
- **demotedToAttendee** - User demotes a presenter - **Change** button in the dialog box.
- **denyParticipant** - Number of times user denies someone entry from the roster.
- **descriptionChanged** - Confirms a shared task description has changed successfully.
- **descriptionClicked** - When a user clicks to view description from task details.
- **detailsTabClicked** - The **Details** tab is clicked on the meeting.
- **deviceAddressBookSync**
- **deviceAddressBookUnsync**
- **dialIn** - A user chooses to Dial in into a meeting (various locations).
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
- **disabled** - User taps **Skip notifications** in FRE. This provides key success data for skipping the notification in FRE flow.
- **disableQuietDays** - Quiet Days disabled. Feature success telemetry for quiet days.
- **disableQuietHours** - Quiet Hours disabled.
- **discoverTeams** - Navigate to Browse and Join Teams page.
- **Dismiss_earlycancelledCQF** - A user dismissed the CQF early cancelled call form.
- **Dismiss_ratemycallCQF** - A user dismisses the CQF rate my call form.
- **Dismiss_ratemyliveeventCQF** - A user dismisses the CQF rate my live event form.
- **dismissBadNetworkBanner** - A user taps **Dismiss** for a poor connection banner.
- **dismissFlyout** - **Dismiss** button pressed.
- **dismissModality** - Exit modality picker without sharing.
- **dismissModalityPicker** - Modality picker button pressed.
- **dismissReadReceiptsNotice** - A user pressed **Got it** from a feature notice.
- **dismissStartRecording** - Dismiss error when starting recording.
- **dismissStopRecording** - Dismiss error when stopping recording.
- **dismissUseWifiForVideoBanner** - Triggered when a user dismisses a banner:
  - That tells the user that remote participant video is blocked, and users have to switch to WiFi to see it.
  - That tells the user that users have to switch to WiFi to share video.
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
- **dragDatePickerHandle**
- **dtmfPSTNCall** - DTMF button on DialPad is tapped.
- **dueDateChanged** - Triggers when user assigns a duedate to a task.
- **dueDatePickerClicked** - Triggers when a user clicks the **Due Date** button in task details, opening the duedate picker page.
- **dueDateSelected** - Triggers when a user applies a filter by duedate while viewing a tasklist.
- **dueDateUnselected** - Triggers when a user unapplies a filter by dueddate while viewing a tasklist.
- **edit** - **Edit** button in a chat message.
- **editChannel** - A user taps on a button to edit a channel that they own or administer.
- **editContact**
- **editMeetingResponse** - Edit meeting response from the meeting detail page.
- **editNavigation** - A user taps **Reorder** in the **More** menu to edit the order of bottom bar apps.
- **editRsvpMeetingOptions** - Click on **RSVP** to change from the previous selection.
- **editShiftClicked** - Tracks when a user edits a shift.
- **editTeam** - A user taps on a button to edit a team that they own or administer.
- **editTeam, editChannel** - Relating to the successful addition of members in a team and successful creation of an existing team when a user:
  - Taps the **Cancel** button in the **Add Members** page (existing team or channel).
  - Taps the **Done** button in the **Add Members** page (existing team or channel).
- **emergencyCall** - Emergency Call placed calling plan.
- **emergencyCallDirectRouting** - Emergency Call placed direct routing.
- **emergencyCallLocationPolicyBased** - DialEmergency using DialPad.
- **emergencycallSecurityDeskNotify** - Emergency Call placed, security desk informed.
- **enableCategory** - Relating to notification settings when enabling:
  - A type of notification.
  - Incoming call notifications.
- **enabled** - Relating to enabling the notification in FRE flow:
  - User taps **Enable notifications** in FRE.
  - User taps Enable in reminder.
- **enabled/disabled** - Calling permissions or contact permissions (Android only).
- **enabled, notNow** - Notification permission prompt **Accept** button, FRE Notifications Permission (iOS). This captures how many people have enabled the notification feature and provides information relating to app engagement.
- **enablediOSPrompt** - A user actually enables notifications in the iOS notifications permissions prompt. This gives information about users who actually enable notifications in iOS from notifications permissions prompt.
- **enabledQuietDays** - Quiet Days enabled.
- **enableLocationPermission** - Enable location services (TBD). ???
- **enableQuietDays** - a user enables quiet days.
- **enableQuietHours** - Quiet Hours enabled.
- **endEditing** - Save button pressed.
- **endFileShare** - A user clicks **Go back** on a file sharing dialog.
- **endMyShift** - Number of devices in shared mode or number of times signed out.
- **endPhotoShare** - **x** out from photo share.
- **entryPointClicked** - Tracking clicking **Requests** in the **Schedule** tab. Requests are for when an FLW is requesting a shift time, etc..
- **endPSTNCallSelected** - a user ends a PSTN and a Content call.
- **endPSTNCallShown** - A user is prompted to end a PSTN or a Content call.
- **endVideoShare** - **x** out from Video share.
- **errorShown** - A user saves the day availability.
- **expand/collapse** - Device contacts or company contacts section.
- **expandCollapseSection** - Tap a section header to expand or collapse a section.
- **Expected: atMention - Android: chatSendMessage - iOS: sendMsg** - @mention a bot in a compose box.
- **Expected: botClickCardAction - Android: showCard - iOS: missing** - Tap on card buttons. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side.
- **Expected: chatSendMessage - iOS: composeSendMessage** - Tap on **Reply** and reply to a bot chat in a channel.
- **Expected: composeSendMessage - Android: replyChannel - iOS: missing** - Tap on **Reply** and reply to a bot chat in a channel.
- **Expected: messageLike - Android: reactLike_CM** - Like a bot message.
- **Expected: messageUnread - Android: markAsLastUnread** - Message context menu options for a bot message.
- **federatedUpgradeNewChat** - A user upgrades legacy chat to native.
- **files**
- **files, conversation, oneNote, etc.** - Tab clicked. Relevant to the **About** tab discoverability. ???
- **fileSelected** - User picks a PowerPoint presentation. Tracks if the user can select a file successfully.
- **fileThumbnailPreviewDownloaded** - Helps to identify if a thumbnail was rendered successfully for a file.
- **fileThumbnailPreviewFromCache** - Captures if thumbnail shows from cache successfully and helps to identify if thumbnail was rendered successfully for a file.
- **fileThumbnailPreviewNotAvailable** - Helps to identify if thumbnail was rendered successfully for a file.
- **fillFrameVideo** - Fill frame from action sheet.
- **firstTimeSignedIn** Sign in or sign up event triggered by:
  - Sign-in success.
  - First sign-in Succeeded.
  - Sign-in Errors Seen by User.
  - Record telemetry about MAM/MDM policies implemented on first time login.
  - Record app install referrer parameters after first time successful login.
- **fitToFrameVideo** - Fit to frame from action sheet.
- **flipCamera** - Flip camera.
- **forcedUpdateAccept** - A user accepts to update the app version in the force update dialog.
- **forcedUpdateExit** - A user closes the app instead of updating the app version in the force update dialog.
- **forcedUpdatePrompt**
- **formattingBold** - A user selects bold formatting.
- **formattingHighlight** - A user selects highlight formatting.
- **formattingImportant** - A user selects importance.
- **formattingItatlics** - A user selects italics.
- **formattingTextColor** - A user selects text color formatting.
- **formattingUnderline** - A user selects underline.
- **FRE - No AS Assigned** - Record telemetry about MAM/MDM policies on app launch to gather data about active users. Telemetry for Intune integration for MAM and MDM. Provides success data about failure during FRE.
- **freActionClicked** - A user clicks on **Get started**, **Try Later**, or **Close** (GPS) in the First Run Experience (FRE).
- **freDone** - FRE done. Feature success telemetry on how many users successfully completed the sign in. This helps preempt sign in issues with the product. And solve login isues proactively.
- **freTriggered** - A user views the time clock First Run Experience (FRE).
- **funSearchQueryEntered** - Giphy query entered. Success data for the giphy attachment feature in Teams.
- **funSelectItem** - Giphy image choosen. Success data for the giphy attachment feature in Teams.
- **galleryImage** - Image uploaded - gallery.
- **get_directions_clicked** - A user clicks the **Get directions** button.
- **goToNotificationSettings** - Go to the notification settings page from **we updated notification settings** dialog.
- **GPSPromptClicked** - A user clicks on **Allow** or **Don't Allow** in OS prompt. Allowing GPS or not.
- **group_map_closed**
- **group_map_open**
- **groupCallJoin** - A user joins a Group call.
- **groupClicked** - Tracks when a user clicks on the shift group.
- **guideMe** - Users taps on a banner that informs them about a 3P app blocking notifications and offers troubleshooting guidance.
- **hamburgerMenu** - Navigate to the hamburger menu. The hamburger menu contains important actions, such as account switch, notification settings, data setting, and profile settings.
- **handoffComplete** - A meeting or call was handed off on this device.
- **handoffJoin** A meeting hand-off option is clicked on the action sheet.
- **hardwareAudioOff** - Turn audio off through the hardware buttons.
- **hardwareAudioOn** - Turn audio on through the hardware buttons.
- **hide** - Hide chat.
- **hideChannel** - Hide a channel from the teams and channel list.
- **image** - Image.
- **immediateCallForward** - Immediate call forward target is set, or enabling immediate call forwarding (Calls ring me is disabled).
- **importanceToggleClicked** - Triggers when the **!** field is toggled inside task item details.
- **importantMessage_select** - A user selects an important message from the priority context menu.
- **importantMessageSend** - A user sends an important message.
- **inCallDialOut** - A user clicks the **Call me back** button from in-call more options.
- **initiatePhotoShare** - Initiate photo share.
- **initiateVideoShare** - Initiate video share.
- **install** - Install or Install Event.
- **installReferrer** - Record app install referrer parameters after first time install.
- **invisionWhiteboardClicked** - Invision whiteboard is clicked on:
  - The channel files tab.
  - The meeting chat files tab.
- **inviteFreemium** - Tapping the **+** button in the Invite screen.
- **inviteGuest** - Tapping the **+** button in the Invite screen.
- **joinFromDeeplinkInTeams** - A user joined through a deeplink from within the Teams app.
- **joinFromDeeplinkOutsideTeams** - A user joined through a deeplink from outside the Teams app.
- **joinFromJoinLauncher** - A user joined from a Join Launcher.
- **joinFromNudge** - A user joined from nudge.
- **joinFromStore** - A user joined after downloading the app from the app store.
- **joinMeeting** - detects the success or failure of joining meetings from calendar in the following circumstances:
  - Join the meeting through Dial in.
  - Join the meeting through Call me back.
  - Join the meeting content only.
  - Click on meeting join button from agenda view.
- **joinOptionsEdu** - An EDU user selects options to join a scheduled meeting and is shown the proper options.
- **joinTeam** - The **Join** button is pressed.
- **joinViaCode** - A user joins a meeting via a code.
- **labelPickerClicked** - Confirms that the label picker successfully launched.
- **labelSelected** - Confirms that a label has been successfully selected.
- **labelUnselected** - Confirms that a label has been successfully unselected.
- **Launch source such as direct, link, appShortcut** - Launch directly or via link (record MAM/MDM telemetry on app launch to collect data for active users).
- **leaveChat** - Confirm leaving chat.
- **legacyChatLink** - User taps on a link to legacy chat.
- **likeAppDismiss**
- **likeAppNo**
- **likeAppYes**
- **likeMsg** - Click on Like.
- **linkPreviewCancel** - Understand the preview closure behavior.
- **liveCaptions** - A user turns live captions on or off.
- **liveEventAdditonalLink** - An additional link is clicked.
- **liveEventInfo** - The **Info** button is clicked.
- **liveEventJoin** - A user joins a live event.
- **liveEventLeave** - The **Leave** button is pressed.
- **liveEventPresenterJoin** - A live event is joined by a presenter.
- **liveEventPresenterJoinAsAttendee** - A live event presenter joined as an attendee.
- **liveEventQnA** - The **Q&A** icon is clicked.
- **liveEventYammer** - The **Yammer** icon is clicked.
- **liveMeetingPushNotificationClicked** - Push notification is clicked.
- **liveMeetingToastClicked** - In-app toast is clicked.
- **live_location_in_chats_from_profile_clicked** - A user clicks **live locations** in profile view.
- **lobbyPickAudio** - Number of times a user switches audio output from lobby.
- **lobbyToggleMuted** - Number of times a user turned the mic on or off from lobby.
- **lobbyToggleVideo** - Number of times a user turned video on or off from lobby.
- **logOutClicked** - When a user logs out.
- **location_active_tracking** - A user's device is switched to active tracking.
- **locationCard** - Click on a location card.
- **location_family_sync** - Showing members of a Family group that were created in MSA family app. Confirms that all family members that can be granted consent are displayed.
- **location_group_map_sync** - A user opens map view.
- **location_map_load** - Map view load.
- **location_map_markers_load** - Map view load. Confirms that location markers for all users actively sharing are displayed properly on the map view.
- **location_message_send** - A user initiates a location sharing session.
- **location_data_use_privacy_denied**
- **location_data_use_privacy_granted**
- **location_settings_open** - A user opens location settings.
- **location_sharing_start**
- **location_sharing_stop**
- **manageBlockedNumbers** - Access blocked numbers through Settings.
- **mapAppPicker** - Choose map app from map picker (TBD). ???
- **markAsRead** - Mark as read.
- **markAsUnread** - Mark as unread.
- **markChannelRead** - A user marks a channel read.
- **messageBookmarkMessage** - Connector card save. Uses existing telemetry with app specific data. Or save a bot message.
- **markAsLastUnread** - Connector card context menu.
- **maskCallerId** - User enables or disables calling setting to mask caller id.
- **meetingDetailCalendarList** - Meeting Details page tapped from calendarList, or click on the **Details** tab on the Meeting Details page.
- **meetingDetailChatWithParticipants** - Chat with participants from the Meeting detail page.
- **meetingDetailDeleteMeetingforSelf** - Delete a Meeting from Meeting Detail page for oneself.
- **meetingDetailJoin** - The **Meeting Join** button is tapped from Meeting Detail page.
- **meetingDetailParticipants** - See all participants from the Meeting Detail page.
- **meetingDetailScheduledMeeting** - Meeting details page tapped from scheduled meeting object (**…**), or click on the **Details** tab of a scheduled meeting.
- **meetingDetailSearchParticipants** - Clicked **Search** in meeting participants on the meeting schedule.
- **meetingJoinLeave** - Leave tapped -> **x** is tapped after the **Join** button is tapped.
- **meetingJoinNow** - **Join now for VOIP** tapped.
- **meetingJoinNowWithCallMe** - A user joins a meeting with **Call me**.
- **meetingJoinNowWithPSTN** - A user joins a meeting with Dial in.
- **meetingLeaveChat** - Leave chat.
- **meetingMuteChat** - Mute chat.
- **meetingNotesCreatedInChatLink** - A user clicks on the **Meeting notes created** chicklet in private meeting chat or in channel meeting chat.
- **meetingNotesMentionCharLink** - A user clicks on the @mention link in private meeting chat.
- **meetingNotesMentionChatLink** - A user clicks on the @mention link in channel meeting chat.
- **meetingNotesTabEntryPoint** - A user clicks on the Meeting notes tab in private meeting or in a channel.
- **meetingNotificationSettingsAccepted** - Notification settings option was changed to Accepted only.
- **meetingNotificationSettingsAll** - Notification settings option was changed to All.
- **meetingNotificationSettingsNone** - Notification settings option was changed to None.
- **messagePriority_select** - A user selects Message priority entry point.
- **messageSeeOriginal** - A user reverts translated message back to original.
- **meetingSeeParticipantsChatDetails** - See all participants.
- **memberListLoadMore** - Scroll down to load more.
- **messagedEditMessage** - A user edits a message.
- **messageShareMessage** - Share a message.
- **messageTranslate** - A user translates a message.
- **messageUnabletoEdit** - A user is unable to edit a message.
- **meetingUserAnonB2B** - Anonymous B2B joined the meeting.
- **meetingUserAnonB2C** - Anonymous B2C joined the meeting.
- **meetingUserDialIn** - PSTN (Dial in) user joined the meeting.
- **meetingUserDialOut** - PSTN Call me back user joined the meeting.
- **meetingUserFederated** - A federated user joined the meeting.
- **meetingUserFreemium** - A freemium user joined the meeting.
- **meetingUserGuest** - A guest user joined the meeting.
- **meetingUserTenant** - An in-tenant user joined the meeting.
- **messageCopyMessage** - Copy Message.
- **messageDelete** - Message delete.
- **messageEditMessage** - Edit message.
- **messageForwardMessage** - User taps on Forward entry point from message context menu.
- **messageLike/messageUnlike** - Message like or unlike.
- **messageMuteSender** - Mute or unmute sender.
- **messageLike** - Connector card like. Uses existing telemetry with app specific data.
- **messageScheduledMeeting** - Meeting object in channel tapped (Not only scheduled ones).
- **messageTriggered** - Triggered when the user's device time zone doesn't match the team time zone.
- **messageTriggered** - This is when a notification is triggered for a message.
- **micPermissionCancel** - A user taps **Cancel** on the mic permission dialog.
- **micPermissionGoToSettings** - A user navigates to settings from the mic permissions dialog.
- **MicrosoftWhiteboardClicked** - Microsoft whiteboard is clicked on the Channel Files tabor the Meeting Chat Files tab.
- **moreOptionsClicked** - Triggers when **...** menu on the top-right is clicked on the task item editor screen.
- **moveTaskClicked** - Option inside task item more options list.
- **multiCallEndFromUFD** - Number of times user ends the call on hold in a multi-call scenario.
- **multiCallResumeFromUFD** - Number of times a user clicks to resume a call from hold.
- **multiCallSwitch** - Number of times user clicks to switch the call and list of calls on hold shows up.
- **multipleAccounts** - Number of accounts for a user.
- **multipleTenants** - Number of tenants per account.
- **mute** - Mute chat.
- **muteOnWhiteboard** - A user mutes or unmutes on the whiteboard screen.
- **muteParticipant** - Mute participant (move to the action sheet).
- **my_location_button_clicked** - User centers the map on their location by clicking on the **My location** button.
- **my_location_clicked** - A user centers the map on their location by clicking on the **blue dot** on the map.
- **myShiftPickerClicked** - Only logged if the request being sent is a swap or offer. Tracking user clicks into **My Shift** picker.
- **nameGroupChat** - Name group chat.
- **navBookmark** - A user navigates to the Saved tab or app on the bottom bar or app tray.
- **navCalendar**
- **nativeChatLink** - User taps on link to native chat.
- **navActivity**- Navigate to the activity feeds page.
- **navActivity, navChat, navTeams, navMore, navOrg, navFiles, navSaved, nav+(Appname)** - Nav Tab is clicked (or the hamburger menu is clicked - navMore). ??? - navMore has been deleted as not used
- **navCallingSettings**
- **navCalls** - Calls tab tapped.
- **navCamera** - A user navigates to the Camera tab or app on the bottom bar or app tray.
- **navChat** - A user navigates to the Chat tab or app on the bottom bar or app tray.
- **navContacts** - A user navigates to the Contacts or People tab or app on the bottom bar or app tray.
- **navDashboardTab**
- **navDynamics365** - Triggered when the user open the Dynamics365 app.
- **navFiles**
- **navFilesTab**
- **navMeetings** - Calendar tab tapped.
- **navNotes** - Triggered when the user open the Notes app.
- **navOrganization** - Triggered when the user open the Organization app.
- **navOrgChart** - Triggered when the user open the Orgchart app.
- **navPeople** - Event is triggered when the user opens the People app.
- **navPeopleSettings** - This is not being sent in the newer builds. ???
- **navPersonalFiles**
- **navPhotoTab** - Photo tab.
- **navSaved** - A user navigates to the Saved tab or app on the bottom bar or app tray.
- **navSelectPlan** - When a user selects a shared plan to navigate to from home view.
- **navSelectPersonalList** - When a user selects a personal plan to navigate to from home view.
- **navSelectSmartList** - When a user selects a smart plan to navigate to from home view.
- **navShifts**
- **navTasks** - Triggered when the user open the Tasks app.
- **navTeams** - Tap **See all**.
- **navVault**
- **navVaultSettings**
- **navVideocamera** - A user navigates to the Camera tab or app on the bottom bar or app tray.
- **navVideoTab** - Video tab.
- **navVoicemail**
- **navWalkieTalkie**
- **navWiki** - Triggered when the user open the Wiki app.
- **newChat** - A user creates a chat.
- **newCall** - Taps **New call** button.
- **newCallDialPad** - Taps the **Dialpad** button on tab.
- **newCallPeople** - Taps the **People** button on tab.
- **noBGActivityDetected** - Exceeds the threshold for background activity failures.
- **notBlockedDevice** - A user doesn't reach the threshold for background activity failures in 30 days.
- **notNow** - User taps **Not now** in reminder.
- **notNowUpdate** - UpdateDefer.
- **notificationError**
- **notificationNavChannelConversation**
- **notificationNavChannelThreadConversation**
- **notificationSettingTurnedOff**
- **notificationNavPreCall** - User gets a notification of a meeting starts that navigates them to the precall screen on click.
- **ocvFeedback**
- **ocvFormCancelled**
- **ocvFormOpened**
- **ocvFormSubmit**
- **offerRecipientClicked** - Only logged if the request being sent is an offer. Tracking user clicks into the team member picker to offer a shift to. Offering means offering a shift time off.
- **offerSwapShiftFromL1** - The type of shift a user tries to offer or swap from a shifts list. iOS action is a **SwipedRight** and Android action is **LongPressed**.
- **offerSwapShiftFromL1Triggered** - The type of shift a user tries to offer or swap from a shifts list. iOS action is a **SwipedRight** and Android action is **LongPressed** is triggered. ???
- **offerSwapShiftFromL1Triggered** - Register user's clock in or out. This will not trigger until you have checked the location, assuming location is required. ???
- **officeLens**
- **officeLens or cameraImage** - Camera picture selected - standard camera or office lens.
- **onBackClicked** - Whenever a user clicks the back arrow to navigate back a page.
- **oneNote** - Triggered when the user open the OneNote app.
- **open** - Notification Settings tap.
- **open edit** - Wiki usage telemetry - User clicks to edit wiki.
- **openApp** - Opening a personal app.
- **openAppDrawer** - A user taps on **More** at the bottom bar to open the app drawer.
- **openEditMeetingForm** - Click on the **Edit** button from the Meeting Details page.
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
- **openInAppClicked** - Option inside task item more options list, only available for personal tasks.
- **opensCalendarView** - Tracking user tapping on open shifts from Schedule tab.
- **openContactCard**
- **openContactCard_ReactionSummary** - Navigate to contact card from the reaction summary page.
- **openFileInApp** - Helps to identify if user opted to open files outside of Teams versus inside of Teams.
- **openHamburgerMenu** - A user taps on the **Hamburger** icon (top-left) to open the side menu for access to settings, presence, and tenant switcher.
- **openInStream** - Open a video in Stream.
- **openMeetingDetails** - Open the meeting details or the Open Meeting details page of a particular meeting.
- **openModalityPicker** - X = ChatsAndChannels for chats and channels.
- **openNewMeetingForm** - Confirms a personal sub-task has been successfully updated.
- **openNewMeetingForm** - Open the scheduler while setting up a new meeting.
- **openPhotoLibrary** - Click on photo library.
- **openQuietDays** - Navigate to Quiet Days page.
- **openQuietHours** - Navigate to Quiet Hours Page.
- **openReactionHoverBubble** - Press the **Add reaction** button on reaction summary page.
- **openReactionSummary** - Invoke reaction summary drawer.
- **openSettingsSetUpInstructions** - Open **Settings** from instructions.
- **openShiftsClicked** - How many people tap the **Calendar** icon.
- **orgChart - No AS assigned** - Basic usage telemetry for org chart.
- **pageEntered** - User was able to login.
- **parental_consent_grant**
- **parental_consent_remove**
- **pauseVoicemail** - Pause tapped on a voicemail item.
- **people**
- **peoplePickerInvoked**
- **personalAppNavBotChat** - Navigate to the bot within personal app.
- **personalAppNavTab** - Navigate to tabs within personal app.
- **photoLibraryPicker** - **Open photo library** tapped inside image picker.
- **pickGalleryPhoto** - Pick a photo from the gallery.
- **pickParticipantChatDetails** - Pick a user from the list.
- **pickRecentPhoto** - Chooses a recent image to share.
- **pinChannel** - Pin a channel to show it above the teams and channels list.
- **pinSelf** - Pin myself from the action sheet.
- **pinUser** - Pin a user from the action sheet.
- **play** - Play the recording.
- **playVoicemail** - Play tapped on voicemail item.
- **plusButtonClicked** - Triggered when the user closes the banner message of a notification.
- **plusButtonClicked** - Tracking clicking the **plus button** to start a schedule, or to start a request on RequestList.sn.
- **pptNextSlide** - Next slide as a presenter or in private viewing.
- **pptPreviousSlide** - Previous slide as a presenter or in private viewing.
- **pptReturnToPresenter** - Go to the **Live** slide (the one that the presenter and everyone else is on).
- **pptStopPresenting** - Stop presenting.
- **pptTakeControl** - Take control.
- **preJoinAddRoom** - User clicks the **Add a room** button in pre-join dropdown, or user clicks **Join** in the **Add a room** scenario.
- **preJoinAudioOff** - User clicks the **Audio off** button in pre-join dropdown.
- **preJoinAutoAddRoom** - User tapped **Join now** when room is nearby.
- **preJoinBack** - Back or Close button tapped.
- **preJoinDenied** - User is unable to join a meeting.
- **preJoinDeviceAudio** - User tapped **Join with device audio** from dropdown.
- **preJoinDialIn** - User clicks the **Dial in** button in the pre-join dropdown.
- **preJoinDialInCall** - User confirms **DIal in** request on prejoin.
- **preJoinDialInCancel** - User cancels **Dial in** request on prejoin.
- **preJoinDialOut** - User clicks the **Call me back** button the in pre-join dropdown.
- **preJoinDialOutCall** - User confirms **Call me back** request on prejoin.
- **preJoinDialOutCancel** - User cancels **Call me back** request on prejoin.
- **preJoinPSTNOptions** - User clicks dropdown for other join options.
- **priorityChange** - Triggers when priority filter is applied while viewing a tasklist.
- **priorityPickerClicked** - Triggers when a user navigates to a priority filter picker from the task list filter screen.
- **privateMeetingJoin** - **Meeting Join** button tapped from Private meeting chat.
- **processInBG** - Process incoming notification in the background (Android).
- **processInFG** - Process incoming notification in the foreground (Android).
- **progressItemClicked** - Confirms a user has successfully opened the progress picker for a task.
- **promotedToPresenter** - User promotes an attendee - **Change** button in the dialog box.
- **provideFeedbackDismiss**
- **provideFeedbackNo**
- **provideFeedbackYes**
- **provideRatingDismiss**
- **provideRatingNo**
- **provideRatingYes**
- **proximityPermissionDismissed** - Permission banner is dismissed.
- **proximityPermissionGranted** - Permission is given on the pop-up.
- **proximityPermissionViewed** - Permission banner is tapped.
- **pushNotification** - Triggering events are:
  - Launch via notification.
  - Push notification clicked.
  - Reconnecting push notification is tapped.
  - **Reconnect failed** push notification is tapped.
- **quickNotificationAction**
- **quickSelectImagePicker** - Quick select.
- **quickStartLiveEventJoin** - Quick start live event is joined by a user.
- **quietHoursValues** - Capture Quiet Hours State on back button navigation.
- **quotedReplySent** - User sent a reply message with context type.
- **reactAngry_CM** - React with angry from the context menu.
- **reactAngry_HB** - React with angry from the hover bubble.
- **reactHeart_CM** - React with heart from the context menu.
- **reactHeart_HB** - React with heart from the hover bubble.
- **reactLaugh_CM** - React with laugh from the context menu.
- **reactLaugh_HB** - React with laugh from the hover bubble.
- **reactLike_CM** - React with like from context menu or like a bot message.
- **reactLike_doubleTap** - React with like from the double tap.
- **reactLike_HB** - React with like from the hover bubble.
- **reactSad_CM** - React with sad from the context menu.
- **reactSad_HB** - React with sad from the hover bubble.
- **reactSurprised_CM** - React with surprise from the context menu.
- **reactSurprised_HB** - React with surprise from the hover bubble.
- **reactRemoved_HB**
- **readReceipts** - User enabled feature.
- **redeemInvite** - In app redemption.
- **refreshCalendarList** - Pull down to refresh agenda view.
- **removeAssignee** - Confirms that an assignee is removed from the assignment picker view (as opposed to *assignmentRemoved* which triggers when clicking **x** outside of assignment picker view).
- **removeMeeting** - Click on **Remove from Calendar** from the Meeting Details page of a cancelled meeting.
- **removeParticipantFromEditMeeting** - Remove a participant after clicking on **Edit meeting** from the Meeting Details page.
- **removeParticipantFromNewMeeting** - Remove a participant from the scheduler page while setting up a new meeting.
- **removeReplyObject** - User removed reply object from compose.
- **removeUser** - Confirms that an assignee is removed from within the assignment picker view (as opposed to *assignmentRemoved* which triggers when clicking **x** outside of assignment picker view).
- **removeUser_CM**
- **removeUserConfirm** - User confirmed remove user dialog.
- **removeUserContextMenu** - User removed participant via context menu.
- **removeUserSwipe** - User removed participant via swipe.
- **reorderChannelItem** - User reorders pinned channels.
- **reportAbuseConfirmation**
- **reportAbuseOpen**
- **reportAbuseSend**
- **replyChain** - Selected **New message** button or textbox in reply chain (thread).
- **replyChannel** - Selected **Reply** button in channels.
- **replyNavigation** - User tapped on reply object to navigate to referenced post.
- **replySendMessage** - Send channel reply.
- **replyViaMsgOptions** - User started reply via context menu.
- **replyViaSwipe** - User started reply via swipe.
- **requestActedOn** - Tracks when the manager acts on open shift requests.
- **requestActionClicked** - When a user requests an action, such as when the request for a shift is clicked (either FLW manager viewing or FLW worker)
- **requestDetailsClicked** - When the request for a shift is clicked (either FLW manager viewing or FLW worker)
- **requestJoinTeam** - **Request** button pressed.
- **requestSent** - Tracks when the user requests an open shift, and logs if there was a request sent.
- **requestToJoinTeam** - Request to join team (public or private).
- **requestToJoinTeamError** - Error with join request.
- **requestTypeClicked** - Tracking what type of request people select from the requests picker, or the request type that the user clicks.
- **resolveIssue** - Users taps on **Resolve** in the notification troubleshooter flyout to navigate to the blocker app.
- **retryButtonClicked** - When a user clicks on the retry button.
- **returnToMessage** - User tapped **Return** button to navigate back to message.
- **runningLate** - I am running late.
- **safeLink** - Link verified as safe.
- **saveEditMeeting** - Click on the **Save** button while on the meeting scheduler page after updating a meeting.
- **saveNewMeeting** - Click on the **Save** button while on the meeting scheduler page. To log successfully saved meetings and the percentage of meetings that failed to create due to a client side or service error.
- **savePlanClicked** - Triggers when user clicks **Create** in the new plan creator from the default opening of the app.
- **scheduledMeetingJoin** - The **Meeting Join** button is tapped from the scheduled meeting object.
- **scrollCalendarList**
- **scrollDatePicker**
- **searchAbandoned** - Helps to track if search was successful versus if a user abandoned search.
- **searchCancelled** - Helps to track if:
  - Search was successful or if user abandoned search.
  - Helps to track if a search query was successful.
- **searchContacts** - Search from the Call List.
- **searchIcon** - Helps to track:
  - If search can be triggered.
  - The source of a search trigger.
  - If a user can find relevant results successfully.
- **searchInitiated** - Helps to track if search can be triggered, and helps to track the source of search trigger.
- **searchMeetingParticipants** - Search for participants to add within the scheduler form. To distinguish between the number of appointments created versus the number of meetings created.
- **searchResultsClicked** - Helps to track:
  - If a user can find relevant results successfully.
  - If search results were from the All tab versus an individual domain.
- **searchTab** - Helps to track:
  - Domain information of the search result - for people, chat, messages, and files.
  - If search results was from ALL tab vs individual domain.
- **searchTabClicked** - Helps to track:
  - Domain information of the search result - for people, chat, messages, and files.
  - If a user can find relevant results successfully.
- **seeAllMeetingParticipants** - Click on **See All** from the meeting details page, or view all participants. Logs user data across the calendar funnel, where calendar meeting details play an important role, this helps validate clicks on Dial ins, Teams meetings, RSVP clicks, etc..
- **seeMeetingDescription** - Opening the Meeting Details page or clicking **See More** on the Meeting description from the Meeting Details page. Logs user data across the calendar funnel, where calendar meeting details play an important role, this helps validate clicks on Dial ins, Teams meetings, RSVP clicks, etc..
- **seeRsvpMeetingOptions** - Click on **Notify Organizer** from the RSVP pop up, or click on **Rsvp** options from the Meeting Details page.
- **selectActivityType** - Captures select gestures on feed item.
- **selectCalendarDate**
- **selectDevice** - Selecting a particular device in the displays app.
- **selectGeneralSetting** - Go to general settings.
- **selection** - Device contact selected, or company contact selected.
- **selectMeetingChicklet** | Meeting.
- **selectMeetingRsvpOption** - Click on the **RSVP** button to choose an option.
- **selectMeetingRsvpOptions** - Click on the **RSVP** button to choose an option.
- **selectPersonalList** - Confirms that the user successfully navigated to a personal task list by tapping it.
- **selectPlannerList** - Confirms that the user successfully navigated to a shared task list by tapping it.
- **selectSettingOption** - Go to the settings tab from the hamburger menu.
- **selectTheme** - Enable dark theme.
- **selectUser** - Confirms that an assignee was successfully selected for a task.
- **selfLongPress** - Long press on myself.
- **Send_earlycancelledCQF** - A user submits feedback on CQF early cancelled call form.
- **send_map_pin_clicked** - A user sends a static location.
- **Send_ratemycallCQF** - A user submits feedback on CQF rate my call form.
- **Send_ratemyliveeventCQF** - A user Submits feedback on CQF rate my live event form.
- **sendForward** - A user confirms to send a forward message from the forward picker.
- **sendImage** - Send image.
- **sendLocation** - Send location.
- **sendMsg** - Click on **Send** in reply.
- **sendRequestBulkClicked** - This is logged once for each bulk request send. In addition, each individual request will log an event.
- **sendRequestBulkClicked** - This is logged once for each bulk request send. In addition, each individual request will log an event.
- **sendRequestClicked** - This is logged for every individual request.
- **sendVoiceMessage** - Record button released.
- **Setting/Dismiss** - Device contacts setting.
- **settingsNavReadReceiptNotice** - User went to settings from the feature notice.
- **shareFile** - Triggered when a user clicks **Share file**. Also helps to check if:
  - The user was able to initiate share file operation.
  - The user can share a file successfully.
- **shareHistory** - Share history picker tapped.
- **shareInto** -- A user shares something from another app into Teams.
- **sharePlanToChat** - A shared list is manually shared from the tasks app to the group chat as a chiclet, check chicklet sent via the backend messaging service.
- **sharePPTFromChannels** - A user clicks **Teams and Channels**.
- **sharePPTFromOneDrive** - A user clicks **OneDrive**.
- **shareRecording** - Share a recording.
- **shareScreen** - Start or stop a screen share.
- **shareShift** - The information that is given when a shift is shared.
- **shareShiftsClicked** - The details of an open shift.
- **shareTray** - A user clicks on **Share…** in the action sheet.
- **shiftAssigneeClicked** - The Shifts Calendar view showing the particular shifts details.
- **shiftDetails** - This allows you to see the details of your own shift.
- **shiftDetailsCalendar** - On the clock in screen, the user clicks on the **Clock In** or **Clock Out** button. Triggered whenever a user receives a notification from a specific team and potentially wants to switch to that particular team.
- **shiftDetailsMyShifts** - Tracking user tapping on **Calendar** from the Schedules tab.
- **shiftDetailsTodaysCoworkers** - On the clock in screen, the user clicks on the **Start** or **End break** button.
- **shortCircuitContactCount**
- **showBanner** - Number of times the **WiFi Connected, No Internet** banner appears.
- **showCard** - Tap on card buttons. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side.
- **shownReadReceiptNotice** - The user shown feature notice with settings options.
- **signIn** - The user taps **Sign in** on welcome page, or the **Sign In** button is tapped.
- **signUp** - The user taps **Create a free account** or **Sign up for free**.
- **simultaneousCallForward** - Triggered when:
  - Simultaneous call forward target is set.
  - Simultaneous call forwarding is enabled (Calls ring me is enabled & Also ring is set).
- **skipVerificationForLink** - Thw user chose to skip verification.
- **SMSSendMessage** - The user sends a SMS message.
- **sortChanged** - Triggers when user changes sort order while viewing a tasklist.
- **startEditing** - **Edit** button pressed.
- **startPresentPhoto** - Start presenting photo.
- **startPresentVideo** - Start presenting video.
- **startPSTNCall** - Triggerd due to:
  - PSTN Result in Global Search (People).
  - PSTN call placed from Device contactCard.
  - PSTN Call placed from callList.
  - DialPSTN Number using DialPad.
- **startRecording** - Start recording.
- **startVoicemailCall** - **Change voicemail greeting** tapped.
- **static_place_selected** - A user drags map to select a static place.
- **statusCheckBoxClicked** - Triggers when task item is either completed or uncompleted.
- **statusMsgCancel** - The user cancels change to status message.
- **statusMsgExpiry** - The user sets the expiry time.
- **statusMsgSet** - The user sets new status message.
- **statusPageViaContactCard** - The user enters the status compose experience via a contact card.
- **statusPageViaHamburger** - The user enters the status compose experience via the hamburger.
- **stop_location_sharing_logout** - A user logs out of the app.
- **stopMeetingButton** - The number of times user leaves the lobby without being admitted into the meeting.
- **stopPresentPhoto** - Stop presenting photo.
- **stopPresentVideo** - Stop presenting video.
- **stopRecording** - Stop recording.
- **structuredMeetingsBannerDismiss** - User dismisses the banner that informs them about their meeting role.
- **stuckOnConnectingDialInSelected** - A user tapped **Dial in** on the drawer.
- **stuckOnConnectingRetrySelected** - A user tapped **Retry** on the drawer.
- **stuckOnConnectingShownDismissed** - A user dismissed the drawer.
- **suggested_place_selected** - A user shares a static location by selecting a suggested place.
- **switchTeamsDialogTriggered** - A user views the Shifts tab.
- **tabActionCopyLink** - Understand how users discover and use tab copy link on mobile.
- **tabActionMoreOptions** - Understand ellipsis usage from within a Tab for more option - discoverability and usage.
- **tabActionOpenInBrowser** - Open in browser usage. This is necessary to understand if users prefer opening a tab outside Teams.
- **tabActionOpenInBrowserFromTab** - Understand open in browser usage from within a Tab for more option - discoverability and usage.
- **tabActionOpenInTeams** - Open in usage. This is key in understanding if the tab can be by default set to open in Teams.
- **tabActionRemove** - Understand how discoverable the delete option is and the usage of the feature.
- **tabActionRename** - Understand how discoverable rename is and the usage of the feature.
- **tabActionSetting, Android - fix** - Understand how users discover and use tab config on mobile.
- **table** - Click on a table.
- **tabListMoreOptions** - Understand the usage of the more options for a tab.
- **tabOpen** - Tabs are a critical feature for Teams and this will be needed to understand feature success and be ready to see if there are any issues in the way it's being used.
- **tabViewed** - Only logged if the request being sent is a swap. Tracking user clicks into the **Team Shift** picker.
- **takePhoto** - Take a photo.
- **takePhotoPicker** - **Take photo** tapped inside the image picker.
- **tapChicletExpand** - Understand how users preview cards on mobile.
- **tapDatePickerHandle**
- **tapSettings** - Understand the number of users re-configuring apps on mobile.
- **tasksAppLaunchAdaptiveCard** - The Tasks app is opened from an adaptivecard in a group chat, check the app launch via the URL of the IC3 service.
- **tasksAppLaunchComposeExtension** - The Tasks app is opened from the compose extension in a group chat, check the app launch via the MT service.
- **tasksAppLaunchDashboard** - The Tasks app is opened from the dashboard tile or specific plan, check the app launch via the MT service.
- **tasksAppLaunchDashboardSeeAll** - The Tasks app is opened from the dashboard **See all** button on the dashboard, check the app launch via the MT service.
- **tasksAppLaunchDefault** - The Tasks app is opened from the bottom drawer, check the app launch via the MT service.
- **tabCalendarClicked** - User has chosen a team from the team picker.
- **teamChannelChanged** - Triggered when a user clicks and navigates to a plan from plan list. Only sent to appInsights, not Aria.
- **teamCreate** - A user selects the option to create a new team.
- **teamEdit** - A user edits some aspect of a team that they own or administer.
- **teamNav** - View menu options for a team.
- **teamsDeviceCallResumed**
- **teamSelectedClicked** - When the user clicks on **Add** on a timesheet.
- **teamShiftPickerClicked** - When the user adds a new break entry. The event is logged once the user saves the changes.
- **tenantSwitch** - On Switch Tenant. Feature success metrics for MTMA (multiple tenant and multiple account) feature, this helps identify and fix issues proactively and provide a smooth switching experience.
- **tenantSwitchUnsupportedError** - Tenant Unsupported Error (when user sees the error). Feature success metrics for MTMA, provides telemetry around account or tenant switch errors, so we can identify and fix issues proactively and provide a smooth switching experience.
- **timeOffReasonClicked** - This it to track if you cited a reason for time off.
- **timesheetAddClicked** - When the user adds a note to their break edits. The event is logged once the user saves the changes.
 **timesheetBreakAdded** - When the user adds a new clock entry. The event is logged once the user saves the changes.
- **timesheetBreakEdited** - When the user confirms their timesheet. The event is logged when the user hits confirm in the modal.
- **timesheetBreakNoteAdded** - When the user deletes their timesheet. The event is logged when the user confirms the delete in the modal.
- **timesheetClockAdded** - When the user clicks on Edit for a timesheet.
- **timesheetClockEdited**  When the user clicks save on an edited timesheet.
- **timesheetConfirmed** - When the user adds a note to their timesheet edits. The event is logged once the user saves the changes.
- **timesheetDeleted** - If a user does or does not have a shift reminder set, and the amount of minutes before a shift a user wants to be alerted.
- **timesheetEditClicked** - User Configuration telemetry.
- **timesheetEditSaved** - User taps on a time sheet from a user's profile to open that user's time sheet.
- **timesheetNoteAdded** - To view an approved time off request.
- **titleChanged** - Triggers when a task item title changes, triggers on every character change.
- **toast** - In-app toast is clicked.
- **toggleChannelsInChat** - Turn feature on or off. Feature success metrics for unified chats and channel experience.
- **toggleClicked** - To view a declined time off request.
- **transferNow** - Triggered when:
- A user taps **Transfer** > **Transfer now**.
- Transfer target is set to a Person.
- Transfer target is set to a Phone Number.
- **translateFailed** - Translation failed (excluding offline). Feature success metrics for message translation feature.
- **unansweredCallForward** - An unanswered call forward target is set. Also enables unanswered call forwarding (Calls ring me is enabled and If unanswered is enabled).
- **unblockCaller** - Unblock:
  - Contact or number from the action sheet.
  - Contact or number from a contact card.
  - Number from settings.
- **unblockChat** - Unblock a bot chat.
- **unpinChannel** - Unpin a channel.
- **unpinSelf** - Unpin yourself from the action sheet.
- **unpinUser** - Unpin a user from the action sheet.
- **unsafeLink** - A link was determined to be unsafe.
- **updatePersonalTask** - Confirms a personal task has been successfully updated.
- **updatePlaybackSpeedVoicemail** - Voicemail playback speed value is changed.
- **updateTask** - Confirms update tasks action failed.
- **updateTaskState** - Confirms that the task state has been updated.
action.
- **upgrade** - Tapping the **Upgrade** button in the **More** menu.
- **uploadFile** - A user clicks **Upload from device**.
- **uploadSelectedFile** - Triggered under these circumstances:
  - Tracks if user can upload files in channel successfully.
  - Tracks if user can upload files in chat successfully.
  - Tracks if user can upload files in the reply window.
  - Tracks if user can upload files successfully in group chat.
  - Tracking usage of core scenario.
  - Tracks the start of upload scenario in channel.
  - Tracks the start of upload scenario in chat.
  - Tracks the start of end of upload scenario in channel.
  - Track if user can upload file into files tab successfully.
  - Helps to identify is user acted on the prompt during file upload.
  - Helps to identify if user can upload selected file successfully.
- **uploadSelectFile** - Tracks if the user can select a file successfully, and tracks if the user can select the **Upload file** button successfully.
- **urgentMessageSelect** - A user selects an urgent message from the priority context menu.
- **urgentMessageSend** - A user sends an urgent message.
- **url** - URL.
- **urlPreview** - URL preview.
- **urlPreviewAdd** - URL preview add.
- **urlPreviewOpen** - URL preview open.
- **urlPreviewRemove** - URL preview removed.
- **userConfiguration** - To view a pending time off request.
- **userJoinedViaShareLink** - A user joined a meeting from a link.
- **userLongPress** - Long press on a participant.
- **useWifiForAudioDialog** - A user clicks **OK** while the system prompts, while an Admin has blocked audio and video calls on cellular.
- **useWifiForVideoDialog** - A user:
  - Clicks **OK** while the system prompts, while an Admin has blocked video calls on cellular.
  - Trying to enable video in meeting, while an Admin has blocked it on cellular.
  - Clicks **OK** while the system prompts, while an Admin has blocked video in meetings on cellular.
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
- **whiteboardUsed** - User annotates on a whiteboard (any action on the webview).
- **wiki - No AS assigned** - Wiki usage telemetry.

### Scenario

> [!NOTE]
> For information on the properties of PanelAction events, see [Properties sent with scenario events](#properties-sent-with-scenario-events).

- **create_default_plan_and_nav_to_view** - Confirms successful creation of a default shared task list and how long it took for user to land on the resulting view after action.
- **create_personal_plan_and_nav_to_view** - Confirms successful creation of a personal task list and how long it took for user to land on the resulting view after action.
- **create_personal_task** - Confirms successful creation of a personal task item.
- **create_planner_plan_and_nav_to_view** - Confirms successful creation of shared task list and how long it took for user to land on resulting view after action.
- **create_planner_task** - Confirms successful creation of shared task item.
- **delete_personal_plan** - Confirms the successful deletion of a personal task list.
- **delete_personal_task** - Confirms the successful deletion of a personal task item.
- **delete_planner_plan** - Confirms the successful deletion of a shared task list.
- **delete_planner_task** - Confirms the successful deletion of a shared task item.
- **get_sender_sub_scenario** - get sender sub scenario in activity.
- **load_chat_plans_list** - Confirms the successful fetching of planner plans for a chat's plan view.
- **load_home_page** - Confirms the successful fetching of both personal and shared tasklists for the main home view.
- **load_personal_task_list** - Confirms the successful fetching of a personal tasklist's tasks for the tasklist view.
- **load_shared_task_list** - Confirms the successful fetching of a shared tasklist's tasks for the tasklist view.
- **load_smart_task_list** - Confirms the successful fetching of a smart tasklist's tasks for the tasklist view.
- **rename_personal_plan** - Confirms the successful renaming of a personal task list.
- **rename_planner_plan** - Confirms the successful renaming of a shared task list.
- **update_planner_task_and_nav_to_view** - Confirms the successful updating of a shared task item and how long it took for user to land on resulting view after action.
- **update_personal_task_and_nav_to_view** - Confirms the successful updating of a personal task item and how long it took for the user to land on resulting view after - **updatePlannerTask** - Confirms that a user has successfully updated a task in a shared taks list.

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
