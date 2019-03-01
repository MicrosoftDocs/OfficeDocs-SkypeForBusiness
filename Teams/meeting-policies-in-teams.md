---
title: Manage meeting policies
author: tonysmit
ms.author: tonysmit
manager: serdars
ms.date: 03/01/2019
ms.topic: article
ms.service: msteams
ms.reviewer: sonua 
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
f1keywords: 
- ms.teamsadmincenter.meetingpolicies.overview
description: Learn to manage meeting policy settings in Teams.
---
# Manage meeting policies in Teams

::: zone target="docs"
Meeting policies are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization. After you create a policy and make your changes, you can then assign uses to the policy. 

By default, a policy named Global (org-wide default) is created. All users in your organization will be assigned this meeting policy by default. You can either make changes to this policy or create one or more custom policies and assign users to them. When you create a custom policy, you can allow or prevent certain features from being available to your users and then assign it to one or more users who will have the settings applied to them. 

## Change or create a meeting policy

To change or create a meeting policy, go to **Microsoft Teams admin center** > **Meetings** > **Meeting policies**. Select a policy from the list, or select **New policy**. Choose your settings, and then click **Save**.

For example, say you have a bunch of users and you want to limit the amount of bandwidth that their meeting would require. You would create a new custom policy named "Limited bandwidth" and disable the following settings:

Under **Audio & video**:
- Turn off cloud recording
- Turn off Allow IP video

Under **Content sharing**:
- Disable screen sharing mode
- Turn off whiteboard
- Turn off shared notes

Then assign the policy to the users.

## Assign a meeting policy to a user

> [!NOTE] 
> A user can be assigned only one meeting policy at one time. 

To assign a policy, go to **Microsoft Teams admin center** > **Users**. 
 
If you are applying the policy to one user, click the user's display name. Next to **Assigned policies**, click **Edit**. Then, in the **Edit user policies** pane, under **Meeting policy**, select the meeting policy from the drop-down list, and click **Save**. You can also edit settings from the list of users. To do this, select the user by clicking to the left of the user's display name. Click **Edit settings**. Then, on the **Edit settings** pane, under **Meeting policy**, select the policy from the drop-down list and then click **Save**. 
 
If you are applying a policy to more than one user, select each of the users by clicking to the left of the user name, and then click **Edit settings**. On the **Edit Settings** pane, under **Meeting policy**, select the policy from the drop-down list and then click **Save**.
 
You can also do this by going to **Microsoft Teams admin center** > **Meetings** >  **Meeting policies**. Select the policy and then click **Manage users**. In the **Manage users** pane, search for the user by display or user name. Select the name and click **Add**. When you are finished adding users, click **Save**.

> [!NOTE] 
> You can't delete a policy if users are assigned to it. You must first assign a different policy to all affected users, and then you delete the original policy.
 
 
## User policy settings

When you select an existing policy on the **Meeting policies** page or click **New policy** to add a new policy, you can configure the following settings.

### New meeting policy name and description
   - **Name** This is the name of the policy that will appear on the **Meeting policies** page. It can't contain special characters or be longer than 64 characters. Note that you can't change an existing policy's name.
   - **Description** You can put in a friendly description for the policy you create. This will be helpful if you want to assign a policy to a group of users.
::: zone-end 

<a name="bkgeneral"> </a>
### General
   - **Allow Meet Now** Turning this on will allow the Meet Now feature to be available to users that join meetings.
   - **Allow the Outlook add-in** Turning this on will let users assigned to the policy have the Outlook add-in available when they schedule meetings.
   - **Allow Channel meeting scheduling** Turning this on will allow Channel Meeting scheduling.
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
   - **Allow anonymous users to start meetings** If this setting is off, then only someone who has been authenticated to the meeting with a Teams app can start the meeting. If it's on, then anyone can start the meeting.
   - **Automatically admit users** If you turn this off, then meeting participants will be left in the lobby until someone starts the meeting. If it's on, meeting participants will be allowed to join the meeting automatically.

[Full article](meeting-policies-in-teams.md)

### Related topics
[Messaging policies in Teams](messaging-policies-in-teams.md)