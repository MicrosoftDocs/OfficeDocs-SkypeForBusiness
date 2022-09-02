---
title: Required mobile diagnostic data for Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: majaisin
description: A list of mobile properties and events for the policy controls for Microsoft Teams.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---
# Required mobile diagnostic data for Microsoft Teams

The following article contains a list of Microsoft Teams mobile events, and lists of properties each event collects.

For more information about diagnostic data, including how to control what diagnostic data is sent to Microsoft, see [Diagnostic data sent from the Teams app to Microsoft](policy-control-overview.md#diagnostic-data-sent-from-the-teams-app-to-microsoft). To view the diagnostic data being sent to Microsoft, you can use the [Diagnostic Data Viewer](https://support.microsoft.com/topic/cf761ce9-d805-4c60-a339-4e07f3182855).

## Events

> [!NOTE]
> There are common properties for all events listed below, to review them, see [Properties sent with all events](#properties-sent-with-all-events).

### PanelAction

> [!NOTE]
> For information on the properties of PanelAction events, see [Properties sent with panelaction events](#properties-sent-with-panelaction-events).

- **acceptUser** - The user has accepted a 1:1 chat.
- **accessibilityUserConfiguration** - When a user toggles an accessibility feature.
- **acknowledgeSettingChange** - Acknowledge an update in the we updated a notification setting dialog. This is a feature success metrics used to acknowledge update notifications and to determine overall notification reliability.
- **actionComposeMenu**
  - Create message extension usage.
  - Action message extension usage.
- **active_session_banner_dismissed** - The location sharing active reminder banner was dismissed.
- **activityChatClicked** - Triggered when non-live chat is selected in the **Activity** tab or a split view is shown.
- **activityContextMenu** - Overflow actions in the activity feed.
- **activityFeedClick** - An activity feed item is tapped on and a bot chat is navigated to.
- **activityFeedLongPress** - Captures long press gestures on feed items.
- **activityFeedSwipe** - Captures swipe gestures on feed items.
- **activityFilterClick** - Captures activity filter usage.
- **activityFilterOptionsClick** - Captures activity filter usage.
- **activityFilterOptionsClicked** - Captures activity filter usage.
- **activityLiveChatClicked** - Triggered when chat is selected from a live meeting on the **Activity** tab.
- **activityLiveDetailsClicked** - Triggered when **Details** is selected from a live meeting on the **Activity** tab.
- **activityTabClicked** - Helps to determine if:
  - The **Activity** tab is shown.
  - Teams captures an **Activity** tab event.
- **activityTypeDropdown** - Captures activity filter usage to switch between **My Activity** and **Feeds**.
- **addChannel** - Adding a channel. This item provides success data around the successful creation of a channel.
- **addMember** - Triggered the **Invite people** button is selected in the **More** menu.
- **addMembers** - Add members to a team or private channel.
- **addToCalendar** - Select the **Add to calendar** button for calendar events missing in private calendar.
- **addToList** - A contact is added to a contact list.
- **addToMeeting** - Select the **Add to meeting** button in the participant list for a meeting (for participants who are a part of the chat).
- **addUserAsContact** - A contact can be added by selecting the **Add contact** icon from the profile card of the contact.
- **admitAll** - The number of times the **Admit all** button is selected from the lobby section.
- **admitParticipant** - The number of times someone is admitted into a meeting from the meeting roster.
- **alertsNavAlert** - Tapping on a feed item.
- **aliasDiscoverabilitySettingOpened** - Entry point to discoverabaility settings.
- **android: null** - Mute or unmute a bot chat. This is enhancing existing telemetry around chats only adds application information.
- **anonymousMeetingJoin** - **Join meeting** is selected on an anonymous join provide name page or **OK** is tapped in the name dialog.
- **anonymousMeetingJoinWelcome** - **Join as guest** is selected on an anonymous join meeting landing page.
- **anonymousMeetingPostMeetingChat** - The number of user views of chat from the call end screen.
- **anonymousMeetingPostMeetingRejoin** - The number of times an anonymous user tries to rejoin a meeting.
- **anonymousMeetingSignIn** - The number of times a user navigated to sign-in from the name input screen.
- **anonymousMeetingSignInWelcome** - The **Sign in and join** is selected on an anonymous join meeting landing page.
- **anonymousMeetingToggleMuted** - The number of times the mute toggle button was selected.
- **anonymousMeetingToggleVideo** - The number of times the video toggle button was selected.
- **appKilled** - The application is terminated.
- **approveTimeOffRequest** -  When a Frontline Worker (FLW) Manager approves a Frontline Worker request to take time off.
- **assigneeChange** - Triggers when a new assignee is added to a task item.
- **assignmentPickerClicked** - The **Assign To** button is selected, opening an assignee picker page.
- **assignmentRemoved** - Triggers when an assignee is removed from a task item by selecting the **x** (which is the only way to remove an assignee).
- **attachmentAdded** - Confirms that an attachment in a task was successfully added.
- **attachmentDeleted** - Confirms that an attachment in a task was successfully deleted.
- **attachmentUpdated** - Confirms that an attachment in a task was successfully updated.
- **audioOnlyLowBatteryBanner** - The **Audio only** option is selected due to a low battery banner.
- **audioOnlyPoorNetworkBanner** - The **Video off** option is selected due to a poor connection banner.
- **audioUserDoubleTap** - Double tap on an audio participant.
- **autoReconnectCallmebackCallDrop** - The number of times the **Callmeback** button was selected at a call end screen.
- **autoReconnectDialIn**
  - The **Dial in** button is selected on the reconnect UFD.
  - The number of times the **Dial In** button was selected while a reconnect is happening.
- **autoReconnectDialInonCallDrop** - The **Dial in** button is selected on the call disconnected UFD.
- **autoReconnectDialOut** - The **Call me back** button is selected on the reconnect UFD.
- **autoReconnectRejoinonCallDrop** - The number of times the **Rejoin** or the **Redial** button was selected at the call end screen.
- **backFromCallMePSTN** - Call Me back PSTN number flow is not completed.
- **backToPhotoShare** - Returning to a camera.
- **backToStageFromWhiteboard** - Returning to a call screen from a whiteboard.
- **backToWhiteboardFromStage** - Going to a whiteboard from a call screen.
- **blockAnonymous** - When:
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
- **brbFormOpened** - The user requested to send feedback.
- **brbFormSubmit** - The user submitted feedback.
- **breakStartEndClicked** - On the clock in screen, the **Start** or the **End break** button is selected.
- **breakStartEndTriggered** - Register a user chooses to use break start or end.
- **bucketSelected** - Confirms that a bucket has been successfully selected.
- **bucketUnselected** - Confirms that a bucket has been successfully unselected.
- **bucketPickerClicked** - Confirms that the bucket picker successfully launched.
- **BYOELiveEventJoin** - BYOE (broadcast your own event) live event is joined by a user.
- **calendarLiveChatClicked** - Chat from live meeting on the **Schedule** tab.
- **calendarMeetingJoin** - **Meeting Join** button selected from a calendar.
- **calendarTab** - Select the **Meetings** tab in the bottom rail. Useful in understanding the calendar usage and comparing with other apps on the bottom rail, or determining if there was a failure in rendering the calendar post after selecting from the bottom bar.
- **calendarTabClicked** - In the circumstances listed below, this will show calendar usage and allow you to compare with other navbar apps on the bottom rail. This can be used to determine if there was a failure when:
  - The **Schedule** tab is shown.
  - The **Meetings** tab is selected in the bottom rail.
- **calendarUpcomingChatClicked** - Chat from an upcoming meeting on the **Schedule** tab.
- **callAccepted** - Call accepted.
- **callAcceptedSFB** - Call accepted.
- **callAppPreference** - A preferred calling App is selected.
- **callControlsManualDismiss** - Call controls are dismissed manually.
- **callControlsManualInvoke** - Call controls are invoked manually.
- **callHistoryItemExpand** - Call History item expanded.
- **callHistoryTab** - **CallHistory** tab is selected in Calls.
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
  - **Add room** is selected in roster.
  - A search result is selected in add room.
  - **Dismiss** is selected for Nearby.
  - **Enable BT** or **Location** is selected for Nearby.
  - A nearby room result is selected in add room.
  - A suggested room result is selected in add room.
  - **Done** is selected in add room.
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
  - **Microphone** button is selected while in a live meeting or a call.
  - Microphone switch while in PSTN.
- **callOrMeetUpMuteParticipant** - A remote participant is muted.
- **callOrMeetUpMuteParticipants** - Mute all participants while in live meeting or a call.
- **callOrMeetUpParticipants** - Participants toggle while in live meeting or a call.
- **callOrMeetUpRemoteMuteUFD** - You have been muted UFD.
- **callOrMeetUpResume** Triggered when:
  - **Resume** button is selected while in a live meeting or a call.
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
  - Video button selected while in live meeting or call.
- **callPark** - Triggered when:
  - **Park Call** is selected in the **...** menu.
  - **Retrieve** button is selected.
  - **Pickup** is selected in the retrieve dialog.
  - **Cancel** is selected in the retrieve dialog.
- **callPreferenceSetting** - Call preference app setting.
- **callsTabNewCall** - **New Call** is selected in the **Calls** tab.
- **callTransfer** - A call transfer is started.
- **callVoicemailTab** - **Voicemail** tab selected in Calls.
- **cameraPermissionCancel** - **Cancel** is selected the camera permission dialog.
- **cameraPermissionGoToSettings** - **Settings** is navigated to from the camera permissions dialog.
- **cancelEditMeeting** - Select the **Close** button while on the meeting scheduler page, after selecting **Edit meeting**. This logs when a user abandons the edit meeting selection.
- **cancelFileShare** - **Cancel** is selected on the confirmation dialog.
- **cancelFileUpload** - **x** is selected on the upload dialog.
- **cancelMeeting** - Select **Cancel event** from the meeting details page. Used to get aggregated data on the number of cancelled meetings.
- **cancelNavigationToLink** - Cancel navigation was chosen.
- **cancelRequestToJoinTeam** - Cancel request to join a team.
- **cancelRequestToJoinTeamError** - Error with a cancel join request.
- **cancelNewMeeting** - To log abandoned Create meeting selections and verify what caused them when:
  - The **Close** button is selected while on meeting scheduler page.
  - The **Close** button is selected while on meeting scheduler page after selecting **Edit meeting**.
- **cardView - No AS assigned** - Card view and card rendering. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side. This item is required to measure any error with joining a team.
- **castPpt** - Event is triggered when:
  - A PowerPoint option is selected.
  - A particular PowerPoint is selected.
  - The Teams and Channels folder is selected in the file picker page.
  - Selects a OneDrive folder in the file picker page.
  - Stops the casting session.
  - Taps on multitasking PiP.
  - Selects a display option from file view.
- **castScreen** - Refers to:
  - Tapping on share screen option.
  - Stopping the screen sharing session.
  - Selecting display option from file view.
- **center_on_team_clicked** - A user successfully centers map on groups.
- **channelFollow** - Turn on notifications for a channel.
- **channelUnfollow** - Turn off notifications for a channel.
- **channelsActiveSetting** - The **notify me when I'm active on desktop** notification setting is changed.
- **chatCreation** - Successful chat creation.
- **changeIsActiveSetting** - Change desktop activity based notification.
- **channel** - New message button or textbox in chat.
- **channelDetails** - Channel navigation information for when:
  - A channel header is selected.
  - The channel details page is navigated to.
- **channelFollow/channelUnfollow** - Follow or unfollow a channel.
- **channelNav** - Navigating to a channel from anywhere.
- **channelNavTab** - Provides success and discoverability data for files in Teams when:
  - The **Files** tab is selected in channel.
  - There is a connector card reply.
- **channelNotificationSettings** - Triggered when:
  - The **New Notification settings** dialog is selected.
  - The channel notification settings button is selected in channel view.
  - A channel notification setting is selected.
- **channelSelected** - Confirms that a channel was successfully selected for a new plan.
- **channelSendMessage** - Triggered when:
  - A channel message is sent.
  - A bot is @mentioned in a compose box.
- **channelTabOverflow** - Selects the **More** tab in a channel.
- **chat** - Refers to:
  - A new message button or textbox in chat.
  - 1:1 chat selected on a callHistory item.
  - A 1:1 chat selection from call list.
- **chat - No AS Assigned** - Viewing unread chat or editing the chat roster, specifically:
  - Selecting the **Done** button when adding a user to a chat.
  - A chat list filter is selected, to filter by unread.
- **chatAddChat** - Add a member to chat button tapped (this will be same for 1:1 chat and group chat).
- **chatAllowJoinViaLink** - Turns the Join Link capabilities in the Chat Details page on or off.
- **chatAvatarEdit** - Tracks how many groups change their avatar from the Chat Details page.
- **chatAvatarEditCamera** - Triggered when a user edits the avatar from a live camera feed.
- **chatAvatarEditGallery** - Triggered when a user edits the avatar from the phone's gallery.
- **chatAvatarEditView** - Triggered when a user views the existing avatar image.
- **chatListNavConversations** - When a user taps into a chat list item.
- **chatCancelAudioCall** - Cancel a group audio call - Confirm dialog.
- **chatCancelVideoCall** - Cancel a group video call - Confirm dialog.
- **chatCM_CopyText** - Tap **Copy text** on a chat context menu.
- **chatCM_DeleteMessage** - Tap **Delete message** on a chat context menu.
- **chatCM_edit** - Tap **Edit** on a chat context menu.
- **chatCM_Forward** - Tap **Forward** on a chat context menu.
- **chatCM_markUnread** - Tap **Mark as unread** on a chat context menu.
- **chatCM_save** - Tap **Save** on a chat context menu.
- **chatCM_SeenBy** - Tap on **Seen** on a context menu option. Read Receipts, such as read by (readby).
- **chatContactsEnter** - The **Chat Contacts** tab is entered.
- **chatDetails** - Provides success and discoverability data for a chat details page when:
  - A chat header is selected.
  - A chat detail page is navigated to.
- **chatRecentEnter** - The **Chat Recent** tab is entered.
- **chatSendMessage** - Send a chat message.
- **chatShareLink** Tracks how many users send a group invite link.
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
- **chatWithMeetingParticipants** - Selects the **Chat** tab from Meeting Details page.
- **checkListAddClicked** - **Add an item** is selected inside the task details view for checklist section.
- **checkListItemAdded** - A checklist item is created for a task.
- **checkListItemDeleted** - A  checklist item is deleted from a task.
- **checkListItemUpdated** - A  checklist item is updated for a task.
- **channelPickerClicked** - Confirms that the channel picker successfully launched.
- **checklistSeeAllClicked** When the **See All** button is selected inside task details to view all checklist items.
- **chicletExpand** - Understand how cards are previewed on mobile and the preview closure behavior.
- **clearFilter** - When all filters are cleared while viewing a tasklist.
- **clickPhotoOfficeLens** - Select **Take photo** - Launch camera (Android only).
- **clockInEntryTeamSelectionShown** - A user selects a team for time clock while not clocked in.
- **clockInOutClicked** - On the clock in screen, the **Clock In** or **Clock Out** button are selected.
- **clockInOutTriggered** - Register a user's clock in or out. This will not trigger until you have checked the location, assuming location is required.
- **closedBannerMessage** - Triggered when the banner message of a notification is closed.
- **closeLobbyBanner** - Number of times the lobby toast is closed using its **Close** button.
- **commentAdded** - Confirms that a comment was added to a task.
- **commentsClicked** - Confirms that the comments view was successfully launched.
- **commentUpdated** - Confirms that a comment was successfully updated on a task.
- **companionBannerJoin** - Select **Join** on the top-level banner.
- **companionDismiss** - Dismiss the companion banner.
- **companionDismissProximity** - Dismiss the companion banner.
- **companionJoin** - Join as companion option is selected on the sheet.
- **companionJoinProximity** - Joined through the companion banner.
- **completeVaultFRE** - User completes process of generating a master key which is used to encrypt their Safe data.
- **completionStateChange** - Triggers when a completed or uncompleted filter toggle is selected in filter view from task list.
- **composeExpandComposer** - **Format** button tapped.
- **composeFilePick** - Native file picker launched.
- **composeImagePicker** - **Image** button tapped.
- **composeLocation** - **Location** button tapped in compose.
- **composeMention** - @mention.
- **composeOpenEmoticonPicker** - Emoticon picker tapped.
- **composeOpenFunPicker** - Fun picker tapped.
- **composeParticipantAdded** - When a participant is added to the Shifts app.
- **composeSearchResult** - Message extension result selection, which is helpful to understand the app search result relevance. Also enhances message send telemetry with app data.
- **composeSelectExtension** - Tap on a ME app.
- **composeSendSmartReply** - A smart reply item is clicked.
- **composeSendMessage** - Enhances message send telemetry with app data.
- **confirmAudioOn** - A user confirms that they want audio on.
- **confirmFileShare** - **Share** is selected on the confirmation dialog.
- **consultTransfer** - Triggered when:
  - Selects **Transfer** > **Consult first**
  - Transfer target set to Person
  - Transfer target set to Phone Number.
- **consultTransferCall** - Triggered when:
  - A consult call is initiated.
  - Confirm is selected on a confirms transfer dialog.
  - Cancel is selected on a confirms transfer dialog.
  - The **Banner transfer** button is selected.
  - The **Banner resume** button is selected.
- **consultTransferChat** Triggered when:
  - A consult chat is initiated.
  - Confirm is selected on a confirms transfer dialog.
  - Confirms is selected on a confirms transfer dialog.
  - A **Banner transfer** button or **Banner resume** button is selected.
- **consumeVoiceMessage** - Voice message played.
- **ContactCard_SeeMoreOOF** - See more of a long OOF message.
- **contactOrganizer** - Selected **Contact organizer**.
- **conversation, tabs** - Tab selected.
- **copyLink** - Copy a link to a channel post.
- **contactActivity** - When the button to view a user's activity from the contact card is selected.
- **conversation** - When a user navigates to the **Chat** or **Posts** tab.
- **cortanaClose** - When a user manually dismisses Cortana canvas.
- **cortanaEduCategorySelect** - When a user clicks on an education tips category item.
- **cortanaEduOpen** - When education page shows on Cortana canvas.
- **cortanaInvoke** - When Cortana starts listening.
- **cortanaKWSSwitchToggle** - When a user tap on KWS switch in Cortana settings page.
- **cortanaMicPermissionDialogButtonClick** - When a user grants or declines mic permission on Cortana canvas.
- **cortanaOpen** - When a user opens Cortana canvas.
- **cortanaOptionsOpen** - When the user taps options button on Cortana canvas.
- **cortanaSafetyFirstActions** - When the user accepts safety first declaration.
- **cortanaSafetyFirstLaunch** - When the user opens Cortana for the first time after FRE is finished.
- **cortanaSettingsOpen** - When a user opens Cortana settings page via clicking Cortana settings button on Cortana canvas.
- **cortanaStopResponding** - When a user clicks cancel button on Cortana canvas.
- **cortanaUserSettingsLaunch** - When the user opens Cortana settings in Teams settings.
- **cortanaVoiceSelect** - When a user selects Cortana voice font in Cortana settings page.
- **createChannel** - Provides success data around the successful creation or discard action for new channel creation, when:
  - The **Done** button is selected on the **Create Channel** Page.
  - The **Cancel** button is selected on the **Create Channel** Page.
- **createComposeExtension** - Create message extension usage, or action ME usage.
- **createConversationClicked** - When a conversation is created with other workers.
- **createDefaultPlannerPlan** - A shared list is created automatically when the Tasks app is opened for the first time by anyone in that group, checks auto list created with Planner service. Confirms the default shared task list is successfully created in Planner the first time a user attempts to create a shared task list.
- **createOrJoinTeam** - The **+** button is selected to create or join a team.
- **createPersonalPlan** - A personal list is created, checks list created with ToDo service. Confirms a new personal task list is created in ToDo.
- **createPersonalSubtask** - Confirms a personal sub-task has been successfully created.
- **createPersonalTask** - Confirms a personal task has been successfully created.
- **createPlan** - Confirms that a shared task list has been successfully created. Confirms that a shared plan has been successfully created through middle tier.
- **createPlannerPlan** - A shared list is created, checks list created with Planner service. Confirms a new shared task list is created in Planner.
- **createPlannerTask** - Checks a call to the Planner service. Confirms that a task has successfully been created in a shared tasks list.
- **createShiftClicked** - When a manager selects **Create a shift**.
- **createShiftOrTimeOffClicked** - Triggered if you select **Create a shift** or **Time off**.
- **createTask** - Used for when create action fails, checks call to Planner service. Confirms a task create operation failed.
- **createTaskList** - When a user navigates to the create plan view from home view.
- **createTeam** - Provides success data around the successful creation or discard action for new team creation, when:
  - The **Done** button is selected on the **Create Team** Page.
  - The **Cancel** button is selected on the **Create Team** Page.
- **createTeam, createChannel** - This provides success data around the successful addition of members in a team and the successful creation of a new team when:
  - The **Skip** button is selected in the **Add Members** page (check existing first).
  - The **Done** button is selected in the **Add Members** page (check existing first).
  - Shows team or channel creation acknowledgement.
- **crossCloudDialogCancel** - **Cancel** is selected for a cross-cloud dialog.
- **crossCloudDialogJoin** - **Join as guest** is selected for a cross-cloud dialog.
- **dashboardNav** - A user navigates to a tile on the chat dashboard.
- **dateChanged** - A user modified a shift date.
- **datePickerLaunch** - Confirms that date picker was successfully launched.
- **dayClicked** - Selecting the day view when user is seeing their shifts.
- **daySaved** - A user saves the day availability, saves a day of shifts.
- **declineTimeOffRequest** - When a user declines the request for time off of work. It's a key functionality for time off, for manager to reject time off request.
- **deleteClicked** - When **Delete** is selected within task details, which brings up the confirmation dialog.
- **deleteContact** - A user deletes an existing private contact.
- **deleteMeeting** - Select the **Delete** button from the Meeting Details page.
- **deletePersonalTask** - Confirms a personal task has been successfully deleted.
- **deletePersonalSubtask** - Confirms a personal sub-task has been successfully deleted.
- **deletePersonalVaultItem** - User requests to delete their personal Safe.
- **deletePlannerTask** - Confirms that a shared task delete operation completed successfully.
- **deleteShift** - Shift deletion.
- **duration_picker_dismissed** - When the duration picker is dismissed.
- **deleteTask** - Verifies with the Planner service as to whether a delete action was successful or unsuccessful. Confirms that a task delete failed, that is, the deletion of a task was unsuccessful.
- **deleteVoicemail** - Delete voicemail item tapped.
- **demotedToAttendee** - A user demotes a presenter - **Change** button in the dialog box.
- **denyParticipant** - Number of times a user denies someone entry from the roster.
- **descriptionChanged** - Confirms a shared task description has changed successfully.
- **descriptionClicked** - When a user selects **View description** from task details.
- **detailsTabClicked** - The **Details** tab is selected on the meeting.
- **deviceAddressBookSync** - Fired when address book sync is turned on from the settings page.
- **deviceAddressBookUnsync** - Fired when address book sync is turned off from the settings page.
- **deviceSyncEnabled** - Device sync enabled.
- **deviceSyncDisabled** - Device sync disabled.
- **dialIn** - A user chooses to Dial in into a meeting (various locations).
- **dialInBadNetworkBanner** - **Dial in** is selected for a poor connection banner.
- **dialInBadNetworkBannerCancel** - The **Dial in** is cancelled on the native dialog.
- **dialInBadNetworkBannerConfirm** - The **Dial in** is confirmed on the native dialog.
- **dialInCall** - **Call** is selected on the **Dial in** pop-up.
- **dialInCancel** - **Cancel** is selected on the **Dial in** pop-up.
- **dialOutCall** - Triggered when a user:
  - Joins in Drive mode.
  - Selects **Call** on the **Call me back** pop-up.
- **dialOutCallAAD** - When any number is selected from **My numbers** in the action sheet
- **dialOutCallRecent** - When any number is selected from previous recent numbers in the action sheet.
- **dialOutCancel** - **Cancel** is selected on the **Call me back** pop-up.
- **dialOutDialog** - **New number** is selected in the action sheet.
- **dialOutFailRetry** - **Retry** is selected from a failure banner.
- **DialPad** - The **DialPad** button is selected from the call list.
- **directShare** - Shared an invite link to a Sms/Email native app.
- **disableCategory** - Disable a type of notification or disable incoming call notifications.
- **disabled** - **Skip notifications** is selected in the First-run experience (FRE). This provides key success data for skipping the notification in the FRE flow.
- **disableQuietDays** - Quiet Days disabled. Feature success telemetry for quiet days.
- **disableQuietHours** - Quiet Hours disabled.
- **discoverTeams** - Navigate to Browse and Join Teams page.
- **Dismiss_earlycancelledCQF** - The CQF early cancelled call form is dismissed.
- **Dismiss_ratemycallCQF** - The CQF rate my call form is dismissed.
- **Dismiss_ratemyliveeventCQF** - The CQF rate my live event form is dismissed.
- **dismissBadNetworkBanner** - **Dismiss**  is selected for a poor connection banner.
- **dismissFlyout** - **Dismiss** button is selected.
- **dismissModality** - The modality picker is exited without sharing.
- **dismissModalityPicker** - The **Modality picker** button is selected.
- **dismissReadReceiptsNotice** - **Got it** is selected from a feature notice.
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
  - Determine if a download operation was initiated.
  - Determine if a file was downloaded successfully.
- **dragDatePickerHandle**
- **dtmfPSTNCall** - DTMF button on DialPad is tapped.
- **dueDateChanged** - Triggers when a user assigns a duedate to a task.
- **dueDatePickerClicked** - Triggers when the **Due Date** button is selected in task details, opening the duedate picker page.
- **dueDateSelected** - Triggers when a user applies a filter by duedate while viewing a tasklist.
- **dueDateUnselected** - Triggers when a user unapplies a filter by dueddate while viewing a tasklist.
- **edit** - **Edit** button in a chat message.
- **editChannel** - A user selects a button to edit a channel that they own or administer.
- **editContact** - A user edits an existing private contact, this can be done by navigating to the contact card.
- **editMeetingResponse** - Edit meeting response from the meeting detail page.
- **editNavigation** - **Reorder** is selected in the **More** menu to edit the order of bottom bar apps.
- **editRsvpMeetingOptions** - Select **RSVP** to change from the previous selection.
- **editShiftClicked** - Edit a shift.
- **editSmartReply** - A smart reply item is edited.
- **editTeam** - A user taps on a button to edit a team that they own or administer.
- **editTeam, editChannel** - Relating to the successful addition of members in a team and successful creation of an existing team when:
  - The **Cancel** button is selected in the **Add Members** page (existing team or channel).
  - The **Done** button is selected in the **Add Members** page (existing team or channel).
- **emergencyCall** - Emergency Call placed calling plan.
- **emergencyCallDirectRouting** - Emergency Call placed direct routing.
- **emergencyCallLocationPolicyBased** - DialEmergency using DialPad.
- **emergencycallSecurityDeskNotify** - Emergency Call placed, security desk informed.
- **enableCategory** - Relating to notification settings when enabling:
  - A type of notification.
  - Incoming call notifications.
- **enabled** - Relating to enabling the notification in the First-run experience (FRE) flow:
  - **Enable notifications** is selected in the First-run experience (FRE).
  - Enable is selected in a reminder.
- **enabled/disabled** - Calling permissions or contact permissions (Android only).
- **enabled, notNow** - Notification permission prompt **Accept** button, First-run experience (FRE) Notifications Permission (iOS). This captures how many people have enabled the notification feature and provides information.
- **enablediOSPrompt** - A user actually enables notifications in the iOS notifications permissions prompt. This gives information about users who actually enable notifications in iOS from notifications permissions prompt.
- **enabledQuietDays** - Quiet Days enabled.
- **enableLocationPermission** - When a user enables location permissions for the share location feature.
- **enableQuietDays** - A user enables quiet days.
- **enableQuietHours** - Quiet Hours enabled.
- **endEditing** - **Save** button pressed.
- **endFileShare** - **Go back** is selected on a file sharing dialog.
- **endMyShift** - Number of devices in shared mode or number of times signed out.
- **endPhotoShare** - **x** out from photo share.
- **entryPointClicked** - Selecting **Requests** in the **Schedule** tab. Requests are for when a Frontline Worker (FLW) is requesting a shift time, etc..
- **endPSTNCallSelected** - A user ends a PSTN and a Content call.
- **endPSTNCallShown** - A user is prompted to end a PSTN or a Content call.
- **endVideoShare** - **x** out from Video share.
- **errorShown** - An error is shown.
- **expand/collapse** - Device contacts or company contacts section.
- **expandCollapseSection** - Tap a section header to expand or collapse a section.
- **Expected: atMention - Android: chatSendMessage - iOS: sendMsg** - @mention a bot in a compose box.
- **Expected: botClickCardAction - Android: showCard - iOS: missing** - Tap on card buttons. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side.
- **Expected: chatSendMessage - iOS: composeSendMessage** - Tap on **Reply** and reply to a bot chat in a channel.
- **Expected: composeSendMessage - Android: replyChannel - iOS: missing** - Tap on **Reply** and reply to a bot chat in a channel.
- **Expected: messageLike - Android: reactLike_CM** - Like a bot message.
- **Expected: messageUnread - Android: markAsLastUnread** - Message context menu options for a bot message.
- **federatedUpgradeNewChat** - Legacy chat is upgraded to native.
- **files** - Tracks if the file listing is done successfully in the chat and channel files tab.
- **fileSelected** - A PowerPoint presentation is selected.
- **fileThumbnailPreviewDownloaded** - Helps to identify if a thumbnail was rendered successfully for a file.
- **fileThumbnailPreviewFromCache** - Captures if thumbnail shows from cache successfully and helps to identify if thumbnail was rendered successfully for a file.
- **fileThumbnailPreviewNotAvailable** - Helps to identify if thumbnail was rendered successfully for a file.
- **fillFrameVideo** - Fill frame from action sheet.
- **firstTimeSignedIn** Sign in or sign up event triggered by:
  - Sign-in success.
  - First sign-in succeeded.
  - Sign-in Errors are seen by a user.
  - Record telemetry about MAM/MDM policies implemented on first time login.
  - Record app install referrer parameters after first time successful login.
- **fitToFrameVideo** - Fit to frame from action sheet.
- **flipCamera** - Flip camera.
- **forcedUpdateAccept** - A user accepts to update the app version in the force update dialog.
- **forcedUpdateExit** - A user closes the app instead of updating the app version in the force update dialog.
- **forcedUpdatePrompt** - Used in situations where users on older versions, that may not have the latest security and privacy fixes, need to be reached.
- **formattingBold** - A user selects bold formatting.
- **formattingHighlight** - A user selects highlight formatting.
- **formattingImportant** - A user selects importance.
- **formattingItatlics** - A user selects italics.
- **formattingTextColor** - A user selects text color formatting.
- **formattingUnderline** - A user selects underline.
- **FRE - No AS Assigned** - Record telemetry about MAM/MDM policies on app launch. Telemetry for Intune integration for MAM and MDM. Provides success data about failure during First-run experience (FRE).
- **freActionClicked** - **Get started**, **Try Later**, or **Close** (GPS) is selected in the First-run experience (FRE).
- **freDone** - First-run experience (FRE) has been done.
- **freTriggered** - A user views the time clock on the First-run experience (FRE).
- **funSearchQueryEntered** - Giphy query entered. Success data for the giphy attachment feature in Teams.
- **funSelectItem** - Giphy image chosen. Success data for the giphy attachment feature in Teams.
- **galleryImage** - Image uploaded - gallery.
- **get_directions_clicked** - The **Get directions** button is selected.
- **giphyUserDisabled** - User selects to decline Giphy terms/conditions.
- **giphyUserEnabled** - User selects to accept Giphy terms/conditions.
- **goToNotificationSettings** - Go to the notification settings page from **we updated notification settings** dialog.
- **GPSPromptClicked** - The **Allow** or **Don't Allow** is selected in an OS prompt. either allowing GPS or not.
- **group_map_closed** - A user opens the map view from chat.
- **group_map_open** - User closes the map view.
- **groupCallJoin** - A user joins a Group call.
- **groupClicked** - Tracks when a user selects the shift group.
- **guideMe** - Users selects a banner that informs them about a 3P app blocking notifications and offers troubleshooting guidance.
- **hamburgerMenu** - Navigate to the hamburger menu. The hamburger menu contains important actions, such as account switch, notification settings, data setting, and profile settings.
- **handoffComplete** - A meeting or call was handed off on this device.
- **handoffJoin** A meeting hand-off option is selected on the action sheet.
- **hardwareAudioOff** - Turn audio off through the hardware buttons.
- **hardwareAudioOn** - Turn audio on through the hardware buttons.
- **hide** - Hide chat.
- **hideChannel** - Hide a channel from the teams and channel list.
- **image** - Image.
- **inAppNotification**- Triggered when a notification is tapped while the user is active in the app.
- **immediateCallForward** - Immediate call forward target is set, or enabling immediate call forwarding (Calls ring me is disabled).
- **importanceToggleClicked** - Triggers when the **!** field is toggled inside task item details.
- **importantMessage_select** - A user selects an important message from the priority context menu.
- **importantMessageSend** - A user sends an important message.
- **inCallDialOut** - A user selects the **Call me back** button from in-call more options.
- **initiatePhotoShare** - Initiate photo share.
- **initiateVideoShare** - Initiate video share.
- **install** - Install or Install Event.
- **installReferrer** - Record app install referrer parameters after first time install.
- **invisionWhiteboardClicked** - Invision whiteboard is selected:
  - The **Channel Files** tab.
  - The meeting **Chat Files** tab.
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
  - Select the **Meeting join** button from agenda view.
- **joinOptionsEdu** - An EDU user selects options to join a scheduled meeting and is shown the proper options.
- **joinTeam** - The **Join** button is pressed.
- **joinViaCode** - A user joins a meeting via a code.
- **labelPickerClicked** - Confirms that the label picker successfully launched.
- **labelSelected** - Confirms that a label has been successfully selected.
- **labelUnselected** - Confirms that a label has been successfully unselected.
- **launchLinksGallery** - When a user enters the links gallery from the dashboard.
- **launchSlideshow** - User Launches Slideshow full screen image viewer from one of three possible app feature locations. 
- **Launch source such as direct, link, appShortcut** - Launches directly or via link (recording Mobile Application Management (MAM) or Mobile Device Management (MDM) telemetry on app launch to collect data for active users).
- **lastSearchableAliasTurnedOff** - The user has disabled all searchable aliases for account.
- **leaveChat** - Confirm leaving chat.
- **legacyChatLink** - A link is selected to a legacy chat.
- **link** - User initiated redeem of invite link by entering Teams application.
- **likeAppDismiss** - When the prompt that asks whether a user likes the app or not is dismissed without a response.
- **likeAppNo** - When the prompt that asks whether user likes the app receives a response of no.
- **likeAppYes** - When the prompt that asks whether user likes the app receives a response of yes.
- **likeMsg** - Select **Like**.
- **linkPreviewCancel** - Understand the preview closure behavior.
- **listUserClicked** - When a user selects a user in Working Now.
- **liveCaptions** - Live captions are turned on or off.
- **liveEventAdditonalLink** - An additional link is selected.
- **liveEventInfo** - The **Info** button is selected.
- **liveEventJoin** - A user joins a live event.
- **liveEventLeave** - The **Leave** button is pressed.
- **liveEventPresenterJoin** - A live event is joined by a presenter.
- **liveEventPresenterJoinAsAttendee** - A live event presenter joined as an attendee.
- **liveEventQnA** - The **Q&A** icon is selected.
- **liveEventYammer** - The **Yammer** icon is selected.
- **liveMeetingPushNotificationClicked** - Push notification is selected.
- **liveMeetingToastClicked** - In-app toast is selected.
- **live_location_in_chats_from_profile_clicked** - **Live locations** is selected in profile view.
- **lobbyPickAudio** - Number of times a user switches audio output from lobby.
- **lobbyToggleMuted** - Number of times a user turned the mic on or off from lobby.
- **lobbyToggleVideo** - Number of times a user turned video on or off from lobby.
- **logOutClicked** - When a user logs out.
- **location_active_tracking** - A user's device is switched to active tracking.
- **locationCard** - Select a location card.
- **location_family_sync** - Showing members of a Family group that were created in MSA family app. Confirms that all family members that can be granted consent are displayed.
- **location_data_use_privacy_denied** - The user denied acceptance of privacy terms.
- **location_group_map_sync** - Map view is opened.
- **location_map_load** - Map view load.
- **location_map_markers_load** - Map view load. Confirms that location markers for all users actively sharing are displayed properly on the map view.
- **location_message_send** - A user initiates a location sharing session.
- **location_data_use_privacy_denied** - A user dismisses or selects **Not now** on a popup explaining use of location data by TFL.
- **location_data_use_privacy_granted** - A user selects **Allow** on a popup explaining the use of location data by TFL.
- **location_settings_open** - A user opens location settings.
- **location_sharing_start** - A user shares their live location in a chat.
- **location_sharing_stop** - A user stops sharing their live location in a chat.
- **loginFailed** - User was unable to login.
- **loginSuccess** - User was able to login.
- **logoutVault** - User logs out of the app and in turn logs out of Safe. 
- **manageBlockedNumbers** - Access blocked numbers through Settings.
- **manageVaultKey** - User changes their Safe key management choice (MSA vs self tracked).
- **manualSendMessage** - A message is sent out manually.
- **mapAppPicker** - When a user selects which mapping app to use when they tap on a location card.
- **markAsRead** - Mark as read.
- **markAsUnread** - Mark as unread.
- **markChannelRead** - A user marks a channel read.
- **messageBookmarkMessage** - Connector card save. Uses existing telemetry with app specific data. Or save a bot message.
- **markAsLastUnread** - Connector card context menu.
- **maskCallerId** - A user enables or disables calling setting to mask caller id.
- **meetingAttachmentFileClick** - A meeting attachment item is clicked.
- **meetingAttachmentFileOptions** - A meeting attachment item options is clicked.
- **meetingAttachmentSeeMoreClick** - A meeting attachment see more button is clicked.
- **meetingDetailCalendarList** - Meeting Details page selected from calendarList, or select the **Details** tab on the Meeting Details page.
- **meetingDetailChatWithParticipants** - Chat with participants from the Meeting detail page.
- **meetingDetailDeleteMeetingforSelf** - Delete a Meeting from Meeting Detail page for oneself.
- **meetingDetailJoin** - The **Meeting Join** button is selected from Meeting Detail page.
- **meetingDetailParticipants** - See all participants from the Meeting Detail page.
- **meetingDetailScheduledMeeting** - Meeting details page selected from scheduled meeting object (**...**), or select the **Details** tab of a scheduled meeting.
- **meetingDetailSearchParticipants** - Selected **Search** in meeting participants on the meeting schedule.
- **meetingInsightFileClick** - A meeting related file item is clicked.
- **meetingInsightFileLocatorClick** - A meeting related content locator tip button is clicked.
- **meetingInsightFileOptions** - A meeting related file item options is clicked.
- **meetingInsightSeeMoreClick** - A meeting related content see more button is clicked.
- **meetingJoinLeave** - Leave tapped -> **x** is tapped after the **Join** button is tapped.
- **meetingJoinNow** - **Join now for VOIP** selected.
- **meetingJoinNowWithCallMe** - A user joins a meeting with **Call me**.
- **meetingJoinNowWithPSTN** - A user joins a meeting with Dial in.
- **meetingLeaveChat** - Leave chat.
- **meetingMuteChat** - Mute chat.
- **meetingNotesCreatedInChatLink** - The **Meeting notes created** chicklet is selected in private meeting chat or in channel meeting chat.
- **meetingNotesMentionCharLink** - The @mention link is selected in private meeting chat.
- **meetingNotesMentionChatLink** - The @mention link is selected in channel meeting chat.
- **meetingNotesTabEntryPoint** - The **Meeting Notes** tab is selected in private meeting or in a channel.
- **meetingNotificationSettingsAccepted** - Notification settings option was changed to Accepted only.
- **meetingNotificationSettingsAll** - Notification settings option was changed to All.
- **meetingNotificationSettingsNone** - Notification settings option was changed to None.
- **messagePriority_select** - A Message priority entry point is selected.
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
- **memeGenerated** - When a meme is generated given a user input of image and text data. 
- **meProfileFetch** - Indicates a successful profile fetch and creation.
- **messageCopyMessage** - Copy Message.
- **messageDelete** - Message delete.
- **messageEditMessage** - Edit message.
- **messageForwardMessage** - A user selects a Forward entry point from message context menu.
- **messageLike/messageUnlike** - Message like or unlike.
- **messageMuteSender** - Mute or unmute sender.
- **messageLike** - Connector card like. Uses existing telemetry with app specific data.
- **messageScheduledMeeting** - Meeting object in channel selected (Not only scheduled ones).
- **messageTriggered** - This is when a notification is triggered for a message.
- **micPermissionCancel** - **Cancel** is selected on the mic permission dialog.
- **micPermissionGoToSettings** - A user navigates to settings from the mic permissions dialog.
- **MicrosoftWhiteboardClicked** - Microsoft whiteboard is selected on the **Channel Files** tab or the **Meeting Chat Files** tab.
- **moreOptionsClicked** - Triggers when **...** menu on the top-right is selected on the task item editor screen.
- **moveTaskClicked** - Option inside task item more options list.
- **msaAddDeleteAliasLinkClicked** - Link to setup an alias on MSA Profile page.
- **multiCallEndFromUFD** - Number of times a user ends the call on hold in a multi-call scenario.
- **multiCallResumeFromUFD** - Number of times a user selects to resume a call from hold.
- **multiCallSwitch** - Number of times a user selects an option to switch the call and list of calls on hold shows up.
- **multipleAccounts** - Number of accounts for a user.
- **multipleTenants** - Number of tenants per account.
- **mute** - Mute chat.
- **muteOnWhiteboard** - A user mutes or unmutes on the whiteboard screen.
- **muteParticipant** - Mute participant (move to the action sheet).
- **my_location_button_clicked** - User centers the map on their location by selecting the **My location** button.
- **my_location_clicked** - A user centers the map on their location by selecting the **blue dot** on the map.
- **myShiftPickerClicked** - Only logged if the request being sent is a swap or offer. **My Shift** picker is selected.
- **nameGroupChat** - Name group chat.
- **nativeTimeClockBreak** - A break on the time clock.
- **nativeChatLink** - A link to native chat is selected.
- **navActivity**- Navigate to the activity feeds page.

- **navBookmark** - A user navigates to the **Saved** tab or app on the bottom bar or app tray.
- **navCalendar** - Measures if a user navigates to a calendar.
- **navCallingSettings** - A user navigates to the calling settings.
- **navCalls** - **Calls** tab tapped.
- **navCamera** - A user navigates to the **Camera** tab or app on the bottom bar or app tray.
- **navChat** - A user navigates to the **Chat** tab or app on the bottom bar or app tray.
- **navContacts** - A user navigates to the **Contacts** or **People** tab or app on the bottom bar or app tray.
- **navDashboardTab** - A user navigates to the **Dashboard** tab within a conversation.
- **navDynamics365** - Triggered when the Dynamics365 app is opened.
- **navFiles** - Files app is selected, tracks if a user can launch the files app in the app tray (iOS).
- **navFilesTab** - Files app is selected, tracks if a user can launch the files app in the bottom nav bar (iOS).
- **navMeetings** - **Calendar** tab tapped.
- **navNotes** - Triggered when the Notes app is opened.
- **navOrganization** - Triggered when the Organization app is opened.
- **navOrgChart** - Triggered when the Orgchart app is opened.
- **navPeople** - Event is triggered when the People app is opened.
- **navPeopleSettings** - Triggered when you navigate to the **People** category in the Settings menu.
- **navPersonalFiles** - Files app is selected, tracks if a user can launch the files app in the bottom nav bar (Android).
- **navPhotoTab** - **Photo** tab.
- **navSaved** - A user navigates to the **Saved** tab or app on the bottom bar or app tray.
- **navSelectPlan** - When a user selects a shared plan to navigate to from home view.
- **navSelectPersonalList** - When a user selects a personal plan to navigate to from home view.
- **navSelectSmartList** - When a user selects a smart plan to navigate to from home view.
- **navTasks** - Triggered when the Tasks app is opened.
- **navTeams** - Tap **See all**.
- **navVideocamera** - A user navigates to the **Camera** tab or app on the bottom bar or app tray.
- **navVideoTab** - **Video** tab.
- **navVoicemail** - A user navigates to the voicemail page.
- **navWalkieTalkie** A user has opened the walkie talkie app.
- **navWiki** - Triggered when the Wiki app is opened.
- **newChat** - A user creates a chat.
- **newCall** - Taps **New call** button.
- **newCallDialPad** - Taps the **Dialpad** button on tab.
- **newCallPeople** - Taps the **People** button on tab.
- **noBGActivityDetected** - Exceeds the threshold for background activity failures.
- **notBlockedDevice** - A user doesn't reach the threshold for background activity failures in 30 days.
- **notNow** - **Not now** is selected in reminder.
- **notNowUpdate** - UpdateDefer.
- **notification/ notification_clicked** – Triggered when a notification is tapped.
- **notificationNavChannelConversation** - Launch the app using a notification for a channel conversation.
- **notificationNavChannelThreadConversation** - Launch the app using a notification for a specific message in a channel conversation.
- **notificationSettingTurnedOff** - Turn off push notifications for the Teams Android app.
- **notificationNavPreCall** - A user gets a notification of a meeting starts that navigates them to the precall screen on selection.
- **ocvFeedback** - Relating to the performance of the OCV feedback form.
- **ocvFormCancelled** - An event sent when the OCV feedback form is cancelled and the user returns to the app.
- **ocvFormOpened** - An event sent when the OCV form is opened.
- **ocvFormSubmit** - An event sent when the user clicks submit on the OCV feedback form.
- **offerRecipientClicked** - Only logged if the request being sent is an offer. The user enters the team member picker to offer a shift. Offering means offering a shift time off.
- **offerSwapShiftFromL1** - The type of shift a user tries to offer or swap from a shifts list. iOS action is a **SwipedRight** and Android action is **LongPressed**.
- **offerSwapShiftFromL1Triggered** - A user offers to swap a shift with another user.
- **officeLens** - Fires when the app launches the officeLens camera feature, either when:
  - A user tries to attach a photo to their message
  - A user tries to take a photo and upload directly to the gallery.
- **officeLens or cameraImage** - Camera picture selected - standard camera or office lens.
- **onBackClicked** - Whenever the back arrow is selected to navigate back a page.
- **oneNote** - When a user opens the OneNote app.
- **open** - Notification Settings tap.
- **open edit** - Wiki usage telemetry - User selects to edit the wiki.
- **openApp** - Opening a personal app.
- **openAppDrawer** - **More** is selected at the bottom bar to open the app drawer.
- **openEditMeetingForm** - The **Edit** button is selected from the Meeting Details page.
- **openFile** - Helps:
  - To identify a file was able to be opened in the chat successfully.
  - To identify a file was able to be opened from a files listing.
  - To check if files can be opened from a OneDrive list.
  - To identify open files can be opened from a channel list.
  - Determining if files can be opened from group chats.
  - Determining if a file can be successfully opened from files app.
  - Determining if a message file can be opened from the chicklet successfully.
  - Determining if files from recent list can be opened successfully.
  - Determining if a file from file list can be opened successfully.
  - Determining if a file can be opened from a messages file chicklet.
  - Determining  if files can be opened successfully from a file list.
- **openInAppClicked** - Option inside task item more options list, only available for personal tasks.
- **opensCalendarView** - Tapping on **Open shifts** from the **Schedule** tab.
- **openContactCard** - A user taps on a **Contact** icon or a contact in the people app to launch the profile card of that contact.
- **openContactCard_ReactionSummary** - Navigate to contact card from the reaction summary page.
- **openFileInApp** - Helps to identify if user opted to open files outside of Teams versus inside of Teams.
- **openHamburgerMenu** - The **Hamburger** icon (top-left) is selected to open the side menu for access to settings, presence, and tenant switcher.
- **openInStream** - Open a video in Stream.
- **openMeetingDetails** - Open the meeting details or the Open Meeting details page of a particular meeting.
- **openModalityPicker** - X = ChatsAndChannels for chats and channels.
- **openNewMeetingForm** - Confirms a personal sub-task has been successfully updated.
- **openNewMeetingForm** - Open the scheduler while setting up a new meeting.
- **openPhotoLibrary** - Select a photo library.
- **openQuietDays** - Navigate to Quiet Days page.
- **openQuietHours** - Navigate to Quiet Hours Page.
- **openReactionHoverBubble** - Press the **Add reaction** button on the reaction summary page.
- **openReactionSummary** - Invoke reaction summary drawer.
- **openSettingsSetUpInstructions** - Open **Settings** from instructions.
- **openSharedLink** - When a user opens a link from the dashboard links tile or the links gallery.
- **openShiftsClicked** - How many people tap the **Calendar** icon.
- **orgChart - No AS assigned** - Basic usage telemetry for org chart.
- **pageEntered** - A user entered a page.
- **parental_consent_grant** - A user grants permission for a minor in their MSFamily to use the Live Location feature in TFL.
- **parental_consent_remove** - A user revokes permission for a minor in their MSFamily to use the Live Location feature in TFL.
- **pauseVoicemail** - **Pause** tapped on a voicemail item.
- **peoplePickerDismissed** - Indicates the People Picker has been dismissed.
- **peoplePickerInvoked** - People Picker is used across seven places in Teams mobile, including (but not limited to):
  - New chat picker.
  - Forward a message.
  - add participant to a meeting.
- **personalAppNavBotChat** - Navigate to the bot within personal app.
- **personalAppNavTab** - Navigate to tabs within personal app.
- **photoLibraryPicker** - **Open photo library** tapped inside image picker.
- **pickGalleryPhoto** - Pick a photo from the gallery.
- **pickParticipantChatDetails** - Pick a user from the list.
- **pickRecentPhoto** - Chooses a recent image to share.
- **pinChannel** - Pin a channel to show it above the teams and channels list.
- **pinSelf** - Pin myself from the action sheet.
- **pinUser** - Pin a user from the action sheet.
- **place_created** - The user created a shared place.
- **place_deleted** - The user deleted a shared place.
- **place_edited** - The user edited a shared place.
- **play** - Play the recording.
- **playVoicemail** - **Play** tapped on voicemail item.
- **plusButtonClicked** - Selecting the **plus button** (**+**).
- **pptNextSlide** - Next slide as a presenter or in private viewing.
- **pptPreviousSlide** - Previous slide as a presenter or in private viewing.
- **pptReturnToPresenter** - Go to the **Live** slide (the one that the presenter and everyone else is on).
- **pptStopPresenting** - Stop presenting.
- **pptTakeControl** - Take control.
- **preJoinAddRoom** - The **Add a room** button is selected in pre-join dropdown, **Join** is selected in the **Add a room** scenario.
- **preJoinAudioOff** - The **Audio off** button is selected in pre-join dropdown.
- **preJoinAutoAddRoom** - **Join now** is selected when a room is nearby.
- **preJoinBack** - **Back** or **Close** button selected.
- **preJoinDenied** - A user is unable to join a meeting.
- **preJoinDeviceAudio** - **Join with device audio** is selected from dropdown.
- **preJoinDialIn** - The **Dial in** button is selected in the pre-join dropdown.
- **preJoinDialInCall** - A user confirms the **DIal in** request on prejoin.
- **preJoinDialInCancel** - A user cancels the **Dial in** request on prejoin.
- **preJoinDialOut** - The **Call me back** button is selected the in pre-join dropdown.
- **preJoinDialOutCall** - A user confirms the **Call me back** request on prejoin.
- **preJoinDialOutCancel** - A user cancels the **Call me back** request on prejoin.
- **preJoinPSTNOptions** - A user selects a dropdown for other join options.
- **priorityChange** - Triggers when priority filter is applied while viewing a tasklist.
- **priorityPickerClicked** - Triggers when a user navigates to a priority filter picker from the task list filter screen.
- **privateMeetingJoin** - **Meeting Join** button tapped from Private meeting chat.
- **processInBG** - Process incoming notification in the background (Android).
- **processInFG** - Process incoming notification in the foreground (Android).
- **profileNameSaved** - Profile name was updated.
- **progressItemClicked** - Confirms a user has successfully opened the progress picker for a task.
- **promotedToPresenter** - User promotes an attendee - **Change** button in the dialog box.
- **provideFeedbackDismiss** - Dismiss the prompt that asks whether the user would like to send feedback about why they didn't like the app.
- **provideFeedbackNo** - Respond no to prompt that asks whether the user would like to send feedback about why they didn't like the app.
- **provideFeedbackYes** - Respond yes to prompt that asks whether the user would like to send feedback about why they didn't like the app.
- **provideRatingDismiss** - Dismiss the prompt that asks whether the user would like to rate us on the app store after saying they liked the app.
- **provideRatingNo** - Respond no to the prompt that asks whether the user would like to rate us on app store after saying they liked the app.
- **provideRatingYes** - Respond yes to the prompt that asks whether the user would like to rate us on app store after saying they liked the app.
- **proximityPermissionDismissed** - Permission banner is dismissed.
- **proximityPermissionGranted** - Permission is given on the pop-up.
- **proximityPermissionViewed** - Permission banner is tapped.
- **pushNotification** - Triggering events are:
  - Launch via notification.
  - Push notification selected.
  - Reconnecting push notification is tapped.
  - **Reconnect failed** push notification is tapped.
- **quickNotificationAction** - When a user interacts with one of the quick action responses on a notification (such as the ability to like a message directly from the push notification).
- **quickSelectImagePicker** - Quick select.
- **quickStartLiveEventJoin** - Quick start live event is joined by a user.
- **quietHoursValues** - Capture Quiet Hours State on back button navigation.
- **quotedReplySent** - A user sent a reply message with context type.
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
- **reactRemoved_HB** - When a user removes a reaction through the reaction summary page experience.
- **readReceipts** - User enabled feature.
- **redeemInvite** - In app redemption.
- **redeemLinkInAppStart** - User initiated redeem of invite link from within Teams application.
- **refreshCalendarList** - Pull down to refresh agenda view.
- **refreshLinksGallery** - When a user swipes down to refresh the links gallery.
- **removeAssignee** - Confirms that an assignee is removed from the assignment picker view (as opposed to *assignmentRemoved* which triggers when selecting **x** outside of assignment picker view).
- **removeMeeting** - Select **Remove from Calendar** from the Meeting Details page of a cancelled meeting.
- **removeParticipantFromEditMeeting** - Remove a participant after selecting **Edit meeting** from the Meeting Details page.
- **removeParticipantFromNewMeeting** - Remove a participant from the scheduler page while setting up a new meeting.
- **removeReplyObject** - A user removed reply object from compose.
- **removeUser** - Confirms that an assignee is removed from within the assignment picker view (as opposed to *assignmentRemoved* which triggers when selecting **x** outside of assignment picker view).
- **removeUser_CM** - When a user removes someone via the chat participant list.
- **removeUserConfirm** - A user confirmed a remove user dialog.
- **removeUserContextMenu** - A user removed a participant via context menu.
- **removeUserSwipe** - A user removed a participant via swipe.
- **reorderChannelItem** - A user reorders pinned channels.
- **reportAbuseConfirmation** - When a user selects the **Done** button on the confirmation screen.
- **reportAbuseOpen** The number of times the **Report a concern** button is selected in the context menu.
- **reportAbuseSend** - When a user selects the **Report** button, the telemetry should store the type of report selected.
- **replyChain** - Selected **New message** button or textbox in reply chain (thread).
- **replyChannel** - Selected **Reply** button in channels.
- **replyNavigation** - Reply object was selected to navigate to referenced post.
- **replySendMessage** - Send channel reply.
- **replyViaMsgOptions** - User started reply via context menu.
- **replyViaSwipe** - User started reply via swipe.
- **requestActedOn** - Triggered when a manager acts on open shift requests.
- **requestActionClicked** - When a user requests an action, such as when the request for a shift is selected (either a Frontline Worker (FLW) manager viewing or a Frontline Worker.
- **requestDetailsClicked** - When the request for a shift is selected (either a Frontline Worker (FLW) manager viewing or Frontline Worker).
- **requestJoinTeam** - **Request** button pressed.
- **requestSent** - Logs if there was a request sent.
- **requestToJoinTeam** - Request to join team (public or private).
- **requestToJoinTeamError** - Error with join request.
- **requestTypeClicked** - Determining the type of request people select from the requests picker.
- **resetLocalVault** - User resets and clears all Safe data from their device.
- **resolveIssue** - **Resolve** is selected in the notification troubleshooter flyout to navigate to the blocker app.
- **responseClicked** - A user selects a response page.
- **retryButtonClicked** - The **Retry** button is selected.
- **returnToMessage** - The **Return** button is selected to navigate back to the message.
- **runningLate** - The user is running late.
- **safeLink** - Link verified as safe.
- **saveEditMeeting** - Select the **Save** button while on the meeting scheduler page after updating a meeting.
- **saveNewMeeting** - Select the **Save** button while on the meeting scheduler page. To log successfully saved meetings and the percentage of meetings that failed to create due to a client side or service error.
- **savePlanClicked** - Triggers **Create** is selected in the new plan creator from the default opening of the app.
- **scenarioChannelDashboard** - The user navigates to a tile on the dashboard.
- **scenarioDashboardNav** - The user navigates to the dashboard tab within a conversation (sibling of the chat tab).
- **scheduledMeetingJoin** - The **Meeting Join** button is selected from the scheduled meeting object.
- **scrollCalendarList** - Measures scrolls in calendar.
- **scrollDatePicker** - Scroll through the calendar date picker control.
- **searchAbandoned** - Determines if search was abandoned.
- **searchCancelled** - Determine if:
  - Search was successful or if the user abandoned search.
  - A search query was successful.
- **searchContacts** - Search from the Call List.
- **searchInitiated** - Determines if search can be triggered, and the source of search trigger.
- **searchMeetingParticipants** - Search for participants to add within the scheduler form. To distinguish between the number of appointments created versus the number of meetings created.
- **searchResultsClicked** - Determines:
  - If relevant results can be found successfully.
  - If search results were from the All tab versus an individual domain.
- **searchTabClicked** - Determines:
  - Domain information of the search result - for people, chat, messages, and files.
  - If the relevant results are found successfully.
- **seeAllMeetingParticipants** - Select **See All** from the meeting details page, or view all participants. Logs user data across the calendar funnel, where calendar meeting details play an important role, this helps validate selections for Dial ins, Teams meetings, RSVPs, etc..
- **seeMeetingDescription** - Opening the Meeting Details page or selecting **See More** on the Meeting description from the Meeting Details page. Data is logged across the calendar funnel, where calendar meeting details play an important role, this helps validate selections for Dial ins, Teams meetings, RSVPs, etc..
- **seeRsvpMeetingOptions** - Select **Notify Organizer** from the RSVP pop up, or select **Rsvp** options from the Meeting Details page.
- **selectActivityType** - Captures select gestures on feed item.
- **selectCalendarDate** - Select a specific date on the calendar date picker control.
- **selectDevice** - Selecting a particular device in the displays app.
- **selectGeneralSetting** - Go to general settings.
- **selection** - Device contact selected, or company contact selected.
- **selectMeetingChicklet** | Meeting.
- **selectMeetingRsvpOption** - Select the **RSVP** button to choose an option.
- **selectMeetingRsvpOptions** - Select the **RSVP** button to choose an option.
- **selectPersonalList** - Confirms that the user successfully navigated to a personal task list by tapping it.
- **selectPlannerList** - Confirms that the user successfully navigated to a shared task list by tapping it.
- **selectSettingOption** - Go to the **Settings** tab from the hamburger menu.
- **selectTheme** - Enable dark theme.
- **selectUser** - Confirms that an assignee was successfully selected for a task.
- **selfLongPress** - Long press on myself.
- **Send_earlycancelledCQF** - A user submits feedback on CQF early cancelled call form.
- **send_map_pin_clicked** - A user sends a static location.
- **Send_ratemycallCQF** - A user submits feedback on CQF rate my call form.
- **Send_ratemyliveeventCQF** - A user submits feedback on CQF rate my live event form.
- **sendForward** - A user confirms to send a forward message from the forward picker.
- **sendImage** - Send image.
- **sendLocation** - Send location.
- **sendMsg** - Select **Send** in reply.
- **sendRequestBulkClicked** - This is logged once for each bulk request send.
- **sendRequestClicked** - **Shift request sent** is selected.
- **sendVoiceMessage** - **Record** button is released.
- **Setting/Dismiss** - Device contacts setting.
- **settingsNavReadReceiptNotice** - User went to settings from the feature notice.
- **settingsOpened** - This is triggered when the user's device time zone doesn't match the team time zone, and the user goes to Settings.
- **setupPinVault** - User saves a Safe pin for their account. 
- **shareCharmCompleted** - User completed sharing of an invite link via application share charm.
- **shareCharmOpened** - User initiated sharing of an invite link via application share charm. 
- **shareFile** - Triggered when **Share file** is selected. Also helps to check if:
  - The user was able to initiate share file operation.
  - The user can share a file successfully.
- **shareHistory** - Share history picker selected.
- **shareInto** -- A user shares something from another app into Teams.
- **sharePlanToChat** - A shared list is manually shared from the tasks app to the group chat as a chicklet, check chicklet sent via the backend messaging service.
- **sharePPTFromChannels** - **Teams and Channels** is selected.
- **sharePPTFromOneDrive** - **OneDrive** is selected.
- **shareRecording** - Share a recording.
- **shareScreen** - Start or stop a screen share.
- **shareShift** - The information that is given when a shift is shared.
- **shareShiftsClicked** - The details of an open shift.
- **shareTray** - **Share...** is selected in the action sheet.
- **shiftAssigneeClicked** - The Shifts Calendar view showing the particular shifts details.
- **shiftDetails** - This allows you to see the details of a shift.
- **shiftDetailsCalendar** - User goes to shift details.
- **shiftDetailsMyShifts** - Tapping on **Calendar** from the **Schedules** tab.
- **shiftDetailsTodaysCoworkers** - On the clock in screen, the **Start** or **End break** button is selected.
- **shortCircuitContactCount** - The number of address book matched short circuited contacts received from a contacts fetch.
- **showBanner** - Number of times the **WiFi Connected, No Internet** banner appears.
- **showCard** - Tap on card buttons. Cards are key platform constructs and measuring their usage and pattern is necessary to understand platform usage and keep a look out for potential issues on the client side.
- **shownReadReceiptNotice** - The user shown feature notice with settings options.
- **signIn** - **Sign in** is selected on welcome page, or the **Sign In** button is tapped.
- **SignInWithOTP** - User selects the option to sign in as a guest with one time passcode (OTP). 
- **signUp** - **Create a free account** or **Sign up for free** is selected.
- **SignUpFromSignIn**- User taps on **Create a new account** option from sign-in.
- **simultaneousCallForward** - Triggered when:
  - Simultaneous call forward target is set.
  - Simultaneous call forwarding is enabled (Calls ring me is enabled & Also ring is set).
- **skipVerificationForLink** - The user chose to skip verification.
- **smartReply** - Smart reply toggle button is clicked.
- **SMSSendMessage** - The user sends a SMS message.
- **sortChanged** - Triggers when user changes sort order while viewing a tasklist.
- **SSOAccountListItem**: Triggered when the user taps on an SSO account to sign in.
- **startEditing** - **Edit** button selected.
- **startPresentPhoto** - Start presenting photo.
- **startPresentVideo** - Start presenting video.
- **startPSTNCall** - Triggered due to:
  - PSTN Result in Global Search (People).
  - PSTN call placed from Device contactCard.
  - PSTN Call placed from callList.
  - DialPSTN Number using DialPad.
- **startRecording** - Start recording.
- **startVoicemailCall** - **Change voicemail greeting** selected.
- **static_place_selected** - A user drags map to select a static place.
- **statusCheckBoxClicked** - Triggers when task item is either completed or uncompleted.
- **statusMsgCancel** - A user cancels change to status message.
- **statusMsgExpiry** - A user sets the expiry time.
- **statusMsgSet** - A user sets a new status message.
- **statusPageViaContactCard** - A user enters the status compose experience via a contact card.
- **statusPageViaHamburger** - A user enters the status compose experience via the hamburger.
- **stop_location_sharing_logout** - A user logs out of the app.
- **stopMeetingButton** - The number of times a user leaves the lobby without being admitted into the meeting.
- **stopPresentPhoto** - Stop presenting photo.
- **stopPresentVideo** - Stop presenting video.
- **stopRecording** - Stop recording.
- **structuredMeetingsBannerDismiss** - a user dismisses the banner that informs them about their meeting role.
- **stuckOnConnectingDialInSelected** - **Dial in** is selected on the drawer.
- **stuckOnConnectingRetrySelected** - **Retry** is selected on the drawer.
- **stuckOnConnectingShownDismissed** - A user dismissed the drawer.
- **suggested_place_selected** - A user shares a static location by selecting a suggested place.
- **Switching**- Tenant or account is switched from the app. This is required to measure account/tenant switch issues proactively and provides a smooth account/tenant switch experience.
- **switchTeamAction** - A user switches teams within the time clock. This should fire after the user selects which team they want to switch to.
- **switchTeamsDialogTriggered** - A user views the **Shifts** tab.
- **tabActionCopyLink** - How users discover and use the tab copy link on mobile.
- **tabActionMoreOptions** - Understand ellipsis (**...**) usage from within a tab.
- **tabActionOpenInBrowser** - Open in browser usage. This is necessary to understand if users prefer opening a tab outside Teams.
- **tabActionOpenInBrowserFromTab** - Understand open in browser usage from within a Tab for more option - discoverability and usage.
- **tabActionOpenInTeams** - Open in usage. This is key in understanding if the tab can be by default set to open in Teams.
- **tabActionRemove** - Understand how discoverable the delete option is and the usage of the feature.
- **tabActionRename** - Understand how discoverable rename is and the usage of the feature.
- **tabActionSetting, Android - fix** - How users discover and use tab config on mobile.
- **table** - Select a table.
- **tabListMoreOptions** - Understand the usage of the more options for a tab.
- **tabOpen** - Notes success in opening tabs, or if there are issues in the way tabs open.
- **tabViewed** - Only logged if the request being sent is a swap, for entries into the **Team Shift** picker.
- **takePhoto** - Take a photo.
- **takePhotoPicker** - **Take photo** selected inside the image picker.
- **tapChicletExpand** - How users preview cards on mobile.
- **tapDatePickerHandle** - Expand the calendar date picker control.
- **tapSettings** - The number of users re-configuring apps on mobile.
- **tasksAppLaunchAdaptiveCard** - The Tasks app is opened from an adaptivecard in a group chat, check the app launch via the URL of the IC3 service.
- **tasksAppLaunchComposeExtension** - The Tasks app is opened from the compose extension in a group chat, check the app launch via the MT service.
- **tasksAppLaunchDashboard** - The Tasks app is opened from the dashboard tile or specific plan, check the app launch via the MT service.
- **tasksAppLaunchDashboardSeeAll** - The Tasks app is opened from the dashboard **See all** button on the dashboard, check the app launch via the MT service.
- **tasksAppLaunchDefault** - The Tasks app is opened from the bottom drawer, check the app launch via the MT service.
- **tabCalendarClicked** - A user has chosen a team from the team picker.
- **teamChannelChanged** - Triggered when a user selects and navigates to a plan from plan list. Only sent to appInsights, not Aria.
- **teamCreate** - A user selects the option to create a new team.
- **teamEdit** - A user edits some aspect of a team that they own or administer.
- **teamNav** - View menu options for a team.
- **teamsDeviceCallResumed** - A user with a bluetooth connected peripheral (mobile phone dock) reactivates a call from hold.
- **teamSelectedClicked** - When a user selects **Team selected** for a timesheet.
- **teamShiftPickerClicked** - When a user adds a new break entry. The event is logged once the user saves the changes.
- **tenantSwitch** - On Switch Tenant. Feature success metrics for MTMA (multiple tenant and multiple account) feature, this helps identify and fix issues proactively and provide a smooth switching experience.
- **tenantSwitchUnsupportedError** - Tenant Unsupported Error (when a user sees the error). Feature success metrics for MTMA (multiple tenant and multiple account), provides telemetry around account or tenant switch errors, so we can identify and fix issues proactively and provide a smooth switching experience.
- **timeClockClicked** - A user selects the **Time clock** button on the My Shifts tab.
- **timeOffReasonClicked** - Determining if a reason for time off is cited.
- **timesheetAddClicked** - When a user adds a note to their break edits. The event is logged once the user saves the changes.
 **timesheetBreakAdded** - Adding a new clock entry. The event is logged once the changes are saved.
- **timesheetBreakEdited** - When a user confirms their timesheet. The event is logged when the user hits confirm in the modal.
- **timesheetBreakNoteAdded** - When a user deletes their timesheet. The event is logged when the user confirms the delete in the modal.
- **timesheetClockAdded** - When a user selects Edit for a timesheet.
- **timesheetClockEdited**  When a user selects Save on an edited timesheet.
- **timesheetConfirmed** - When a user adds a note to their timesheet edits. The event is logged once the user saves the changes.
- **timesheetDeleted** - If a user does or does not have a shift reminder set, and the amount of minutes before a shift a user wants to be alerted.
- **timesheetEditClicked** - User Configuration telemetry.
- **timesheetEditSaved** - A user taps on a time sheet from a user's profile to open that user's time sheet.
- **timesheetNoteAdded** - To view an approved time off request.
- **titleChanged** - Triggers when a task item title changes, triggers on every character change.
- **toast** - In-app toast is selected.
- **toggleChannelsInChat** - Turn feature on or off. Feature success metrics for unified chats and channel experience.
- **toggleClicked** - A toggle is selected.
- **transferNow** - Triggered when:
  - A user selects **Transfer** > **Transfer now**.
  - Transfer target is set to a Person.
  - Transfer target is set to a Phone Number.
- **translateFailed** - Translation failed (excluding offline). Feature success metrics for message translation feature.
- **trigger_created** - The user created a geofence.
- **trigger_deleted** - The user deleted a geofence.
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
- **upgrade** - Selecting the **Upgrade** button in the **More** menu.
- **uploadFile** - A user selects **Upload from device**.
- **uploadSelectedFile** - Triggered under these circumstances:
  - Upload files in channel successfully.
  - Upload files in chat successfully.
  - Upload files in the reply window.
  - Upload files successfully in group chat.
  - Usage of core scenario.
  - The start of upload scenario in channel.
  - The start of upload scenario in chat.
  - The start of end of upload scenario in channel.
  - Upload a file into the **Files** tab successfully.
  - If a prompt is acted on during file upload.
  - If a selected file is uploaded successfully.
- **uploadSelectFile** - Select a file successfully; Select the **Upload file** button successfully.
- **urgentMessageSelect** - Selects an urgent message from the priority context menu.
- **urgentMessageSend** - Sends an urgent message.
- **url** - URL.
- **urlPreview** - URL preview.
- **urlPreviewAdd** - URL preview add.
- **urlPreviewOpen** - URL preview open.
- **urlPreviewRemove** - URL preview removed.
- **userConfiguration** - To view a pending time off request.
- **userJoinedViaShareLink** - A user joined a meeting from a link.
- **userLongPress** - Long press on a participant.
- **userProfileOpened** - A user selects a **User** icon to open a user profile.
- userTimesheetOpened** - A user selects a timesheet from a user's profile to open that person's timesheet.
- **useWifiForAudioDialog** - A user selects **OK** while the system prompts, while an Admin has blocked audio and video calls on cellular.
- **useWifiForVideoDialog** - Triggered when:
  - **OK** is selected while the system prompts, while an Admin has blocked video calls on cellular.
  - Trying to enable video in meeting, while an Admin has blocked it on cellular.
  - **OK** is selected while the system prompts, while an Admin has blocked video in meetings on cellular.
- **videoUserDoubleTap** - Double tap on a video participant.
- **viewChannelMembers** - View a channel members list.
- **viewContactCard** - ContactCard selected from:
  - A callHistory item.
  - A voicemail item.
  - A call list.
- **viewed** - A user viewed a page.
- **viewFullAllDayMeetingList** - Agenda view on Mobile.
- **viewLobbyFromBanner** - The number of times a user selects **View lobby** from a notification banner.
- **viewMeetingDetails** - Select the **...** menu on the Meeting Details page. Pertaining to the usage of the **More** menu on mobile calendars.
- **viewMeetingOccurrence** - Open up the meeting details of an instance of a recurring meeting. Telemetry to log user data across the calendar funnel, where calendar meeting details play an important role, that helps validate Selects Dial ins, Teams meetings, RSVPs, and so on.
- **viewMeetingSeries** - To log the successful rendering of a meeting series in the following circumstances:
  - When switching from an instance to the series meeting detail page.
  - When selecting **View series** from the meeting details page.
- **viewOrgChart** - Basic usage telemetry for an org chart.
- **viewRequests** - The **View requests** button is pressed.
- **voiceDataCollectionOptOut** - A user opts-out of the recording from mobile by clicking the banner.
- **voicemail - No AS Assigned** - A speaker taps on a voicemail item.
- **whiteboardUsed** - A user annotates on a whiteboard (any action on the webview).
- **wiki - No AS assigned** - Wiki usage telemetry.
- **poorNetworkBanner** - Poor network banner shown.
- **badNetworkBanner** - Bad network banner shown.

### PanelView

> [!NOTE]
> For information on the properties of PanelView events, see [Properties sent with panelview events](#properties-sent-with-panelview-events).

- **appInstall**: Triggered when a user opens the app for the first time after installation.
- **fileDeleteFailed** - Triggered when a file delete operation fails.
- **fileDeleteSuccess** - Triggered when a file delete operation succeeds.
- **filePreview** - Triggered in following scenarios:
  - When share option is tapped in file preview screen.
  - When copy option is tapped in file preview screen.
  - When download option is tapped in file preview screen.
  - When a file preview is successfully loaded.
- **files** - Triggered in following scenarios:
  - When a file is previewed within Teams app.
  - When file upload option is tapped in OneDrive files screen.
  - When "Copy Link" option is tapped in file preview screen.
  - When the file sharing screen is dismissed.
  - When files options menu is opened or when one of the options in that menu is tapped.
  - When "in-call" files screen is opened.
  - When a file is tapped to open.
- **filesChannel** - Triggered when channel files screen is opened.
- **fileSources** - Triggered when files options menu is opened or when one of the options in that menu is tapped.
- **filesPersonal** - Triggered when a batch of files is loaded in OneDrive or recent files screen.
- **fileUploadDeleteTriggered** - Triggered when a file attachment is deleted or detached from message area.
- **fileUploadFailed** - Triggered when a file upload operation fails.
- **fileUploadIndividualNotification** - Triggered when the contents of file upload notification change or when the notification is interacted with. The interactions may include gestures like swiping to dismiss the notification or tapping the notification etc.
- **fileUploadSuccess** - Triggered when a file upload operation succeeds.
- **fileUploadSummaryNotification** - Triggered when the contents of file upload summary notification change or when the notification is interacted with. The interactions may include gestures like swiping to dismiss the notification or tapping the notification etc.
- **meetingFiles** - Triggered when meeting files screen is opened.
- **meetNowActionSheet** - Triggered when user creates a Meet Now meeting.
- **navPersonalFiles** - Triggered when navigation to files screen is performed.
- **signInSSOPage**: Triggered when the user views a single sign-on page while signed in.
-- **signInError**: Triggered when the user hits any error while signed in. This is needed to proactively identify and fix issues that users face during sign-in. 
-- **TfLSignInSuccessful**: Triggered when the user successfully signs in to a personal Microsoft account. This is needed to understand sign-in and sign-up reliability and proactively identify and fix issues.
-- **TfWFreemiumSignInSuccessful**: Triggered when the user successfully signs in to a freemium account. This is needed to understand sign-in and sign-up reliability and proactively identify and fix issues.
-- **TfWSignInSuccessful**: Triggered when the user successfully signs in to a work or school account. This is needed to understand sign-in and sign-up reliability and proactively identify and fix issues.
- **appDrawer** - Triggered when app drawer is opened successfully.
- **appPolicyChange** - Triggered when a user resets and save new tabs order locally.
- **app_stageview** - Triggered when a stage view is successfully rendered.

### Scenario

> [!NOTE]
> For information on the properties of PanelAction events, see [Properties sent with scenario events](#properties-sent-with-scenario-events).
> 
- **acquire_resource_token_interactive**- Required service call which is triggered when an authentication token is acquired by interactive sign-in. 
- **acquire_resource_token_silent**- Required service call which is triggered when an authentication token is acquired by silent sign-in.
- **add_buddy** - Captures status of adding a contact.
- **app_crash2** – Triggered when the app is crashed unexpectedly. Provides information on how frequently the Teams app is crashing. 
- **app_incremental_sync_launch** - Confirms that the pill count gets updated successfully for cold launch.
- **app_incremental_sync_resume** - Confirms that the pill count gets updated successfully for warm/hot launch.
- **app_start_cold** - To monitor cold app launch (Android only).
- **app_start_hot** - To monitor hot app launch (Android only).
- **app_start_warm** - To monitor warm app launch (Android only).
- **auth_adal_tokens**- Required service call to do silent authentication. Triggered when a user starts the app, or the token is refreshed on expiry.
- **chat_add_giphy** - Confirms that the Giphy GIF rendering action succeeded or failed.
- **chat_send_message_sfc**- Triggered when a chat message is sent in SfC interop chat.
- **cortanaError** - To monitor Cortana error happens.
- **cortanaView** - To monitor Cortana canvas appear.
- **cortanaRestart** - To monitor Cortana restart.
- **cortanaSetNewConversation** To monitor Cortana sets new conversation.
- **cortanaSpeechRecognization** To monitor Cortana speech recognization latency.
- **cortanaStart** To monitor Cortana backend start.
- **cortanaStartListening** To monitor Cortana start listening.
- **cortanaStopListening** To monitor Cortana stop listening.
- **cortanaThinking** To monitor Cortana state change to thinking(waiting for service's response).
- **cortanaTokenRefresh** To monitor Cortana token refresh in foreground.
- **cortanaWarmingUp** To monitor Cortana warming up start(Cortana is open but token is still fetching).
- **cortana_admin_policy_refresh** - To monitor Cortana admin policy refresh.
- **cortana_background_token_refresh** - To monitor Cortana token refresh.
- **cortana_initialization** - To monitor Cortana initialization steps.
- **cortana_sdk_events** - To monitor Cortana turn related events.
- **cortana_skill_action_execution** - To monitor Cortana action execution.
- **cortana_skill_action_delay** - Confirms the start of delay action.
- **cortana_watchdog** - To monitor Cortana watchdog recovery process.
- **create_default_plan_and_nav_to_view** - Confirms successful creation of a default shared task list and how long it took for a user to land on the resulting view after action.
- **create_new_chat_thread_sfc**- Triggered when a new chat thread is created for an SfC interop chat.
- **create_personal_plan_and_nav_to_view** - Confirms successful creation of a personal task list and how long it took for a user to land on the resulting view after action.
- **create_personal_task** - Confirms successful creation of a personal task item.
- **create_planner_plan_and_nav_to_view** - Confirms successful creation of shared task list and how long it took for a user to land on resulting view after action.
- **create_planner_task** - Confirms successful creation of shared task item.
- **forwardExistingAmsObject** Confirms that the media forward action succeeded or failed.
- **delete_personal_plan** - Confirms the successful deletion of a personal task list.
- **delete_personal_task** - Confirms the successful deletion of a personal task item.
- **delete_planner_plan** - Confirms the successful deletion of a shared task list.
- **delete_planner_task** - Confirms the successful deletion of a shared task item.
- **json_parse_failure**- Provides information on the frequently of JSON parsing issues.
- **fetch_me_profile** - The users profile creation status.
- **getProfilePicture**- Necessary service call to get user profile picture. 
- **get_resource_token_async**: Required service call to acquire tokens for Azure Active Directory resources asynchronously.
- **get_resource_token_sync**: Required service call to acquire tokens for Azure Active Directory resources synchronously.
- **get_sender_sub_scenario** - Get sender sub scenario in activity.
- **interactiveAuthNopa2** – Triggered when no password user is interrupted to do interactive authentication.
- **load_chat_plans_list** - Confirms the successful fetching of planner plans for a chat's plan view.
- **load_home_page** - Confirms the successful fetching of both personal and shared tasklists for the main home view.
- **load_personal_task_list** - Confirms the successful fetching of a personal tasklist's tasks for the tasklist view.
- **load_shared_task_list** - Confirms the successful fetching of a shared tasklist's tasks for the tasklist view.
- **load_smart_task_list** - Confirms the successful fetching of a smart tasklist's tasks for the tasklist view.
- **meetingAttachmentRender** - Confirms the render of meeting attachments.
- **meetingInsightFetch** - Confirms the fetch of meeting related content.
- **meetingInsightLocatorRender** - Confirms the render of meeting related content locator tip.
- **meetingInsightRender** - Confirms the render of meeting related content.
- **meetingInsightVisible** - Confirms the visibility of meeting related content.
- **open_image** Confirms that the full screen image rendering succeeded or failed.
- **rename_personal_plan** - Confirms the successful renaming of a personal task list.
- **rename_planner_plan** - Confirms the successful renaming of a shared task list.
- **save_image** Confirms that the image save action succeeded or failed.
- **saveMeProfile**- Required service call that gets triggered when user saves the profile
- **share_image** - Confirms that the image share action succeeded or failed.
- **smart_reply_enabled** - Confirms that smart reply is enabled for current user.
- **smart_reply_received** - Confirms that a smart reply suggestion is received.
- **smart_reply_banned** - Confirms that smart reply cannot be displayed for current user.
- **park_call_for_hold_v2** - Confirms that putting call on hold succeeded or failed using call park.
- **unpark_call_for_hold_v2** - Confirms that resuming call succeeded or failed using call un-park. 
- **update_planner_task_and_nav_to_view** - Confirms the successful updating of a shared task item and how long it took for a user to land on resulting view after action.
- **update_personal_task_and_nav_to_view** - Confirms the successful updating of a personal task item and how long it took for a user to land on resulting view after 
- **updatePlannerTask** - Confirms that a user has successfully updated a task in a shared task list.
- **upload_images** Confirms that the image upload action succeeded or failed.
- **upload_voice_messages** Confirms that the voice message upload action succeeded or failed.
- **voiceMessageUpload** Confirms that the voice message upload action succeeded or failed.
- **cancel_channel_meeting** Confirms that the cancellation of a channel meeting has succeeded or failed.
- **cancel_meeting** Confirms that the cancellation of a meeting has succeeded or failed.
- **cancel_private_meeting** Confirms that the cancellation of a private meeting has succeeded or failed.
- **edit_channel_meeting** Confirms that the edit operation of a channel meeting has succeeded or failed.
- **edit_meeting** Confirms that the edit operation of a meeting has succeeded or failed.
- **server_fetch_agenda_view** Confirms that the calendar event sync using the Middle Tier API has succeeded or failed.
- **server_fetch_date_picker_view** Confirms that the calendar event sync using the Outlook REST API has succeeded or failed.
- **server_fetch_agenda_view_group** Confirms that the calendar event sync using the Middle Tier API for the TFL group has succeeded or failed.
- **server_fetch_date_picker_view_incremental** Confirms that the calendar event incremental sync using the Outlook REST API has succeeded or failed.
- **meeting_details** - Confirms that the meeting details sync has succeeded or failed.
- **show_meeting_participants** - Confirms that showing the meeting participant list has succeeded or failed.
- **search** - Confirms that the whole search session has succeeded or failed.
- **time_based_retention_shared_channel** – Captures performance data for pruning the database.
- **toggle_searchability** - Captures status of network call for stamping/unstamping an alias.
- **sync_user_entitlements_and_app_definitions** -  Required service call to fetch aggregatedEntitlements.
- **bots_load_mediacards** - Captures instanced when Connector cards are configured in chat and channel.
- **bots_load_one_card** - Captures if at least one card is present and loaded when chatting with a bot.
- **load_assignments** - Captures exceptional handling for loading assignment app.
- **load_channel_tab** - Captures loading of channel tab. (Android  only)
- **load_messaging_extension_results** - Captures loading of messaging extension search/query result. (Android  only)
- **load_static_tab** - Captures loading of static tab. (Android  only)
- **app_authenticated** - Confirms that the authentication is sucessful and a token is fetched. (Android  only)
- **blocked_by_conditional_access** - When receive conditional access blocked error code in authentication. (we try to force refresh the primary token in that case). (Android  only)
- **get_resource_token_sync** - Triggered when we attempt to fetch token for app resources synchronously. (Android  only)
- **get_resource_token_async** - Triggered when we attempt to fetch token for app resources asynchronously. (Android  only)

## OnePlayer events
> [!NOTE]
> For OnePlayer events, only properties listed in [Property lists for OnePlayer events](#property-lists-for-oneplayer-events) apply.
### OnePlayer user action events
- **PlayerPlay** - Confirms if the user taps on the play button in the OnePlayer view.
- **PlayerPause** - Confirms if the user taps on the pause button in the OnePlayer view.
- **PlayerSeek** - Confirms if the user seeks the video either using the seek bar or forward/backward buttons in the OnePlayer view (iOS only).
- **VideoPlayerSeekForward** - Confirms if the user seeks the video either using the seek bar or forward buttons in the OnePlayer view (Android only).
- **VideoPlayerSeekBackward** - Confirms if the user seeks the video either using the seek bar or backward buttons in the OnePlayer view (Android only).
- **ChangePlaybackSpeed** - Confirms if the user has selected a new playback speed.
- **changePlaybackQuality** - Confirms if the user has selected a new video quality for playback.
- **ShareVideo** - Confirms if the user has tapped on the share icon.
- **PlayerClose** - Confirms if the user has tapped on the close icon.
- **VideoCaptionsOn** - Confirms if the user has switched on the captions.
- **VideoCaptionsOff** - Confirms if the user has switched off the captions.
- **ChangePlayerOrientation** - Confirms if the user has changed the orientation of the device.
- **OpenPlayerSettingsMenu** - Confirms if the user has opened the settings menu.
- **OpenPlaybackSpeedMenu** - Confirms if the user has opened the playback speed menu.
- **PlayerAction** - Custom action provided by the host app.

### OnePlayer playback events
- **PlayerHeartbeat** - This is a recurring event that sends the current status of the player and playback to a log.

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

## Property lists for OnePlayer events

### 1. Properties sent with all OnePlayer events
##### 1.1 Standard properties
| Property name | Description                                                                                    |
|---------------|------------------------------------------------------------------------------------------------|
| eventType | Type of event (AppLogic, ErrorAlert, Performance, UserAction) |
| accountType   | Type of user account (for example, business) |
| component     | OnePlayer |
| language      | Locale/language of the app |
| platform      | Platform of OnePlayer (iOS/Android) |
| tenantId      | Tenant ID|
| version       | Version of the OnePlayer being used |
| aadUserId     | User ID |                                

##### 1.2 Player properties
| Property name | Description                                                                                    |
|---------------|------------------------------------------------------------------------------------------------|
| engineName    | Underlying player name (AVFoundation for iOS/ExoPlayer for Android) |
| engineVersion | Operating System version |
| loadMode      | Load mode of the player |
| playbackSessionId | Session ID for playback |

##### 1.3 Host properties 
| Property name | Description                                                                                    |
|---------------|------------------------------------------------------------------------------------------------|
| hostIntegrationType | Host integration type (for example, Package, OneUp) |
| hostPlatform  | Platform for host app |
| hostProperties| Host properties, if any (iOS only) |
| hostApp       | Name of the host app |
| hostVersion   | Version of the host app |

##### 1.4 Experimentation properties
| Property name | Description                                                                                    |
|---------------|------------------------------------------------------------------------------------------------|
| ring          | Ring to which the user belongs |
| hostSettings  | Attributes set by the host app (moreOptionsEnabled, shareFeatureEnabled, playbackQualityFeatureEnabled, playbackSpeedFeatureEnabled) |
| flightFilters | Description |
| flightsOverridden | Bool for flights overridden or not |

##### 1.5 Service properties
| Property name | Description                                                                                    |
|---------------|------------------------------------------------------------------------------------------------|
| contentType   | Type of content being served |
| environment   | Environment name  |
| mediaService  | Which media service is being used (SPO, ODB, ODC, IC3-AMS, Unknown) |
| mediaType     | Type of the media being played  |
| playbackTech  | Playback tech of the media  |
| correlationId | Correlation ID for the media, if any |

### 2. Properties sent with all OnePlayer User Action Events 
| Property name | Description                                                                                    |
|---------------|------------------------------------------------------------------------------------------------|
| actionType    | Type of action being performed, such as tap, drag, and flick( iOS only)|
| isIntentional | Boolean value if the action is intentional or not (iOS only) |

#### 2.1 Properties sent with changePlaybackQuality Event
| Property name | Description                                                                                    |
|---------------|------------------------------------------------------------------------------------------------|
| currentPlaybackQuality | current playback quality |

#### 2.2 Properties sent with ChangePlaybackSpeed Event
| Property name | Description |
|---------------|------------------------------------------------------------------------------------------------|
| previousPlaybackRate  | Previous playback rate of the video (iOS only) |
| currentPlaybackRate   | Current playback rate of the video |

#### 2.3 Properties sent with PlayerSeek Event (iOS only)
| Property name | Description |
|---------------|------------------------------------------------------------------------------------------------|
| seekSource    | Source of seek (seekbar, forwardButton, backwardButton) |
| seekValue     | Seek position |

### 3. Properties sent with OnePlayer Heartbeat Event
| Property name | Description |
|---------------|------------------------------------------------------------------------------------------------|
| mediaCurrentTime | Current playback time of the media (iOS only)|
| isLoaded | Is media loaded |
| loadTimeMs | Load time taken in milliseconds |
| numberOfStalls | Number of stalls during playback (iOS only) |
| bufferingCount | Number of stalls during playback (Android only) |
| observedBitrate | Observed bit rate during playback (iOS only) |
| avgBitrateBitsPerSecond | Observed bit rate during playback (Android only) |
| playedSeconds | Played seconds till the event |
| rebufferingSeconds | Rebuffering seconds during playback |
| timeSinceSourceSetMs | Time since source was set (ms) |
| triggerType | Trigger type (buffering, error, errorLog, canPlayThrough, intervalHeartbeat, sourceset, unload) |
| errorId | Error ID for the error, if any |
| errorCorrelationId | Error correlation ID for the error, if any |
| errorLog | Error log for the error, if any |
| errorType | Error type for the error, if any |
| errorMessage | Error message for the error, if any |
| errorStack | Extended error info for the error, if any |
| metaUrl | Meta URL for media |
| odspDocId | ODSP doc ID for media |
| siteId | Site ID for media |
| teamsCallId | Teams call ID for media, if any |
