---
title: Manage meeting policies
author: tonysmit
ms.author: tonysmit
manager: serdars
ms.date: 04/18/2019
ms.topic: article
ms.service: msteams
ms.reviewer: sonua 
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
f1keywords: 
- ms.teamsadmincenter.meetingpolicies.overview
- ms.teamsadmincenter.meetingpolicies.audioandvideo
- ms.teamsadmincenter.meetingpolicies.contentsharing
- ms.teamsadmincenter.meetingpolicies.general
- ms.teamsadmincenter.meetingpolicies.participantandguests
description: Learn to manage meeting policy settings in Teams.
---
# Manage meeting policies in Teams

::: zone target="docs"
Meeting policies are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization. After you create a policy and make your changes, you can then assign users to the policy. 

By default, a policy named Global (org-wide default) is created. All users in your organization will be assigned this meeting policy by default. You can either make changes to this policy or create one or more custom policies and assign users to them. When you create a custom policy, you can allow or prevent certain features from being available to your users, and then assign it to one or more users who will have the settings applied to them. 

## Change or create a meeting policy

To change or create a meeting policy, go to **Microsoft Teams admin center** > **Meetings** > **Meeting policies**. Select a policy from the list, or select **New policy**. Choose your settings, and then select **Save**.

For example, say you have a bunch of users and you want to limit the amount of bandwidth that their meeting would require. You would create a new custom policy named "Limited bandwidth" and disable the following settings:

Under **Audio & video**:
- Turn off cloud recording
- Turn off Allow IP video

Under **Content sharing**:
- Disable screen sharing mode
- Turn off whiteboard
- Turn off shared notes

Then assign the policy to the users.

> [!NOTE] 
> A user can be assigned only one meeting policy at a time. 

## Assign a meeting policy to users

If you are applying the policy to one user, select **Users** on the left navigation pane, and then click the user's display name. On the user's page, next to **Assigned policies**, select **Edit**. Then, in the **Edit user policies** pane, under **Meeting policy**, select the meeting policy from the drop-down list, and then select **Save**. You can also assign policies from the list of users. To do this, select the user by clicking to the left of the user's display name. Select **Edit settings**. Then, on the **Edit settings** pane, under **Meeting policy**, select the policy from the drop-down list, and then select **Save**. 
 
If you are applying a policy to more than one user, select **Users** on the left navigation pane, and then select each user by clicking to the left of the user name, and then click **Edit settings**. On the **Edit Settings** pane, under **Meeting policy**, select the policy from the drop-down list, and then select **Save**.
 
You can also assign a meeting policy to one or more users as follows:

1. Go to **Microsoft Teams admin center** > **Meetings** > **Meeting policies**.
2. Select the policy by clicking to the left of the policy name.
3. Select **Manage users**.
4. In the **Manage users** pane, search for the user by display name or by user name, select the name, and then select **Add**. Repeat this step for each user that you want to add.
5. When you are finished adding users, select **Save**.
 
> [!NOTE] 
> You can't delete a policy if users are assigned to it. You must first assign a different policy to all affected users, and then you can delete the original policy.
 
 
## User policy settings

When you select an existing policy on the **Meeting policies** page or select **New policy** to add a new policy, you can configure the following settings.

### New meeting policy name and description
   - **Name** This is the name of the policy that will appear on the **Meeting policies** page. It can't contain special characters or be longer than 64 characters. Note that you can't change an existing policy's name.
   - **Description** You can put in a friendly description for the policy you create. This will be helpful if you want to assign a policy to a group of users.
::: zone-end 

<a name="bkgeneral"> </a>
### General
   - **Allow Meet now in channels** Turning this on will allow the Meet Now feature to be available to users who join meetings.
   - **Allow the Outlook add-in** Turning this on will let users assigned to the policy have the Outlook add-in available when they schedule meetings.
   - **Allow channel meeting scheduling** Turning this on will allow Channel Meeting scheduling.
   - **Allow scheduling private meetings** Turning this on will allow users that join a meeting to schedule private meetings.

<a name="bkaudioandvideo"> </a>

### Audio & video
   - **Allow transcription** If you turn this on, transcription of the meeting will be available to users.
   - **Allow cloud recording** Turning this on will allow recordings to be saved in the cloud.
   - **Allow IP video** Turning this on will allow IP videos during meetings.
   - **Media bit rate (KBs)** You can set the bit rate for meetings. The default is 50 MB.

<a name="bkcontentsharing"> </a>

### Content sharing
   - **Screen sharing mode** You can select the screen sharing mode. This will be the size of the screen that will be used during a meeting that a user assigned with the policy can use.
   - **Allow a participant to give or request control** This allows all participants in a meeting to give and request control of screen sharing.
   - **Allow an external participant to give or request control** This allows an external (someone not part of your organziation) participant to give and request control of a meeting when the screen is being shared.
   - **Allow PowerPoint sharing** If you turn this on, users that schedule meetings can share PowerPoint slide decks during a meeting.
   - **Allow whiteboard** If you turn this on, the whiteboard will be available to meeting participants during a meeting.
   - **Allow shared notes** If you turn this on, shared notes will be available to meeting participants during a meeting.

<a name="bkparticipantsandguests"> </a>

### Participants & guests
   - **Allow people that dial in to start a meeting** You can turn on or off if you want to let people who haven't been authenticated because they dialed in using their phone to start a meeting.
   - **Automatically admit people** Determines what types of participants will automatically be added to meetings organized by this user. Set this to **Everyone in your organization** if you would like meetings to place every external user in the lobby but allow all users in the company to join the meeting immediately. Set this to **Everyone** if you'd like to admit anonymous users by default. Set this to **Everyone in your organization and federated organizations** if you would like meetings to allow federated users to join like your company's users, but place all other external users in a lobby.
   - **Allow dial-in users to bypass the lobby** You can turn on or off if you want to let people who dialed in using their phone to bypass the lobby and join the meeting.
   - **Allow organizers to override lobby settings** Turn this setting on to let meeting organizers disregard the lobby settings to admit users to meetings.
   - **Allow Meet now in private meetings** Turn this setting on to allow meeting attendees to meet privately via chat before the meeting begins. 
   - **Enable live captions** Enable this setting to display captions in supported languages during a meeting. 
   - **Allow chat in meetings** Enable this setting to permit chats during a meeting. This is helpful if users have questions or want to insert a hyperlink or note during a discussion, but they don't want to interrupt the conversation.

[Full article](meeting-policies-in-teams.md)

### Related topics
[Messaging policies in Teams](messaging-policies-in-teams.md)
