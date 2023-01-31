--- 
title: Manage meeting policies for participants and guests
ms.author: mabond
author: mkbond007
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: sonua, shalenc
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.participantandguests
  - seo-marvel-apr2020
description: Learn to manage meeting policy settings in Teams for participants and guests.
---



# Meeting policy settings - Participants & guests

<a name="bkmeetingparticipants"> </a>

These settings control which meeting participants wait in the lobby before they're admitted to the meeting and the level of participation they're allowed in a meeting.

- [Let anonymous people join a meeting](#let-anonymous-people-join-a-meeting)
- [Who can present in meetings](#who-can-present-in-meetings)
- [Automatically admit people](#automatically-admit-people)
- [Dial-in users can bypass the lobby](#dial-in-users-can-bypass-the-lobby)
- [Meet now in private meetings](#meet-now-in-private-meetings)
- [Live captions](#live-captions)
- [Chat in meetings](#chat-in-meetings)
- [Teams Q&A](#teams-qa)
- [Meeting reactions](#meeting-reactions)

These settings are found in the Teams admin center under **Meetings** > **Meeting policies** in the **Participants & guests** section.

> [!NOTE]
> Options to join a meeting will vary, depending on the settings for each Teams group, and the connection method. If your group has audio conferencing, and uses it to connect, see [Audio Conferencing](/microsoftteams/audio-conferencing-in-office-365). If your Teams group doesn't have audio conferencing, refer to [Join a meeting in Teams](https://support.office.com/article/join-a-meeting-in-teams-1613bb53-f3fa-431e-85a9-d6a91e3468c9).

## Let anonymous people join a meeting

To learn about anonymous people joining meetings, read [Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md)

## Who can present in meetings

This setting is a per-user policy that lets you change the default value of the **Who can present?** setting in **Meeting options** in the Teams client. The **Who can present in meetings** policy setting affects all meetings, including Meet Now meetings.

The **Who can present?** setting lets meeting organizers choose who can be presenters in a meeting. To learn more, see [Change participant settings for a Teams meeting](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e) and [Roles in a Teams meeting](https://support.microsoft.com/office/c16fa7d0-1666-4dde-8686-0a0bfe16e019).

To specify the default value of the **Who can present?** setting in Teams, set to one of the following settings in the **Who can present in meetings** policy:

- **Organizers, but users can override**: Only the meeting organizer can be a presenter and all meeting participants are designated as attendees. This parameter corresponds to the **Only me** setting in Teams.
- **Everyone in the organization, but user can override**: Authenticated users in the organization, including guests, can be presenters. This setting corresponds to the **People in my organization** setting in Teams.
- **Everyone, but user can override**:  All meeting participants can be presenters. This is the default value. This setting corresponds to the **Everyone** setting in Teams.

Keep in mind that after you set the default value, meeting organizers can still change this setting in Teams and choose who can present in the meetings that they schedule.

## Automatically admit people

To learn about the meeting lobby, read [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md).

## Meet now in private meetings

This is a per-user policy and applies before a meeting starts. This setting controls whether a user can start an unplanned private meeting. By default, this setting is turned on.

## Live captions

This setting is a per-user policy and applies during a meeting. This setting controls whether the **Turn on live captions** option is available for the user to turn on and turn off live captions in meetings that the user attends.  

![Screenshot showing the Turn on live captions option.](media/meeting-policies-live-captions.png)

|Setting value |Behavior  |
|---------|---------|
|**Not enabled but the user can override**     | Live captions aren't automatically turned on for the user during a meeting. The user sees the **Turn on live captions** option in the overflow (**...**) menu to turn them on. This is the default setting. |
|**Not enabled**     | Live captions are disabled for the user during a meeting. The user doesn't have the option to turn them on.          |

For more information on how your end users can turn on **Live captions**, see [Use live captions in a Teams meeting](https://support.microsoft.com/office/4be2d304-f675-4b57-8347-cbd000a21260).

### Live translated captions

> [!NOTE]
> This feature is temporarily available in public preview. After the preview, the meeting organizer must have a Teams Premium license for attendees to use live translated captions.

By default, **Live captions** are displayed in the language that’s spoken during a meeting. **Live translated captions** allow your users to see captions translated into the language they’re most comfortable with.

To enable **Live translated captions**, **Live captions** must be set to **Not enabled but the user can override** in the Teams admin center. To turn off **Live translated captions**, set this to **Not enabled**.

<a name="bkcontentsharing"> </a>

## Chat in meetings

This is a per-user and per-organizer policy. This setting controls whether meeting chat is allowed in the user's meeting. This setting doesn't apply to channel meetings.

|Setting value |Behavior  |
|---------|---------|
|**Turn it on for everyone**     | All participants can write and view chat messages. |
|**Turn it off for everyone**     | Meeting chat is turned off for all participants.  |
|**Turn it on for everyone but anonymous users**     | Meeting chat write access is turned off for anonymous participants only.  |

Once this **Chat in meetings** policy is applied to users, an organizer can't override this policy through **Meeting options**.

The policy applied to the meeting organizer can affect other users in the meeting. For example:

- If the organizer has **Chat in meetings** set to **Turn it on for everyone** or **Turn it on for everyone but anonymous users**, then a user's individual policy will apply and any users with **Turn it off for everyone** set won't be able to chat in the meeting.
- If the organizer has **Chat in meetings** set to **Turn it off for everyone**, the organizer's policy applies and no one will be able to chat in the meeting.

<a name="bkparticipantsandguests"> </a>

## Teams Q&A

This is a per-organizer policy. This setting turns the Questions & Answers experience (Q&A) on or off.

The setting is enforced when a meeting is created or is updated by organizers. By default, this setting is turned off. Learn more about [Q&A in Teams Meetings](/manage-qna-for-teams).

Teams Q&A can be adjusted within the Teams admin center under **Meetings** > **Meeting policies** in the **Participants & guests** section. The parameter `-QnAEngagementMode` controls this policy in PowerShell.

|Setting value |Behavior  |
|---------|---------|
|**On**     | Organizers can add Q&A when creating meetings. |
|**Off**     | Organizers won't have the option to add Q&A when creating meetings.  |

## Meeting reactions

Meeting reactions are on by default. Turning off reactions for a user doesn't mean that a user can't use reactions in meetings they schedule. The meeting organizer can still turn on reactions from the meeting option page, regardless of the default setting.

## Enable meeting policy settings

To enable meeting policy settings, you can use the [Teams admin center](https://admin.teams.microsoft.com/policies/meetings) (**Meeting Policies** > **Edit a policy** > **Participants & guests**) or the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet in Teams PowerShell.

In this example, we use PowerShell to modify the global meeting policy to allow anyone to start or join a meeting.

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AutoAdmittedUsers "Everyone" -AllowAnonymousUsersToStartMeeting $True -AllowPSTNUsersToBypassLobby $True
```

Once you’ve set up a policy, you need to apply it to users. If you modified the Global (Org-wide default) policy, it will automatically apply to users. You need to wait at least 4 hours for any policy changes to take effect, but it can take up to 24 hours.

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Remove the RestrictedAnonymousAccess Teams meeting policy from users](meeting-policies-restricted-anonymous-access.md)
