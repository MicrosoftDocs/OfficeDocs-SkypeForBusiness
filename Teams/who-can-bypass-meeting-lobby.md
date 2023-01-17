--- 
title: Control who can bypass the meeting lobby in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: rbronisevsky
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: Learn to use the meeting lobby in Microsoft Teams to allow only certain meeting participants to join the meeting directly.
---

# Control who can bypass the meeting lobby in Microsoft Teams

The Teams meeting lobby is a way of preventing certain types of meeting participants from joining a meeting until a meeting organizer, co-organizer, or presenter admits them. When a participant goes to the lobby, organizers, co-organizers, and presenters are notified and can choose to admit them to the meeting or not.

Using the lobby settings in the Teams admin center, you can create defaults for which types of meeting participants are able to bypass the lobby and which participants must wait there until admitted to the meeting. You can control how the following types of participants interact with the lobby:

- Meeting organizer and co-organizers
- People in your organization
- Guests
- People in trusted organizations
- Anonymous participants

The identities of people joining meetings are verified by Microsoft 365 unless the participant is anonymous. Anonymous participants can't be verified.

## Prerequisites for meeting with people outside your organization

There are several settings in Teams that control whether people outside the organization can interact with Teams. The following settings must be enabled for people outside the organization to join meetings:

- [Guest access in Teams](guest-access.md) must be enabled in order for guests to be able to join meetings.
- [External access](manage-external-access.md) must be enabled in order for people in trusted organizations to join meetings. A mutual trust between your organization and the external organization must be configured and the meeting organizer in your organization as well as any participants from the external organization must be enabled for external access.
- Both the **Anonymous users can join a meeting** meeting setting (organization level) and meeting policy (for the organizer who is creating the meeting) must be **On** in order for anonymous participants to join meetings.

If any of these settings are turned off, that type of external participant won't be able to join meetings regardless of lobby settings.

## Overview of lobby settings and policies

The following table shows the Teams meeting policies that affect how meeting participants interact with the lobby.

|Setting|Description|
|:------|:----------|
|**Anonymous users and dial-in callers can start a meeting**|This is a per-organizer policy that allows for leaderless meetings. This setting controls whether anonymous participants and dial-in users can join the meeting without a verified participant in attendance. This setting only applies when **Who can bypass the lobby** is set to **Everyone**. If the **Anonymous users can join a meeting** organization or meeting setting is **Off**, this setting only applies to dial-in callers. By default, this setting is turned off to prevent potential abuse of your meeting links by anonymous users. <br><br> While **Off**, anonymous participants and dial-in users will wait in the lobby until a verified participant (including a dial-in organizer) joins the meeting, at which point they will be automatically admitted. Once the meeting has started, anonymous participants and dial-in users will join the call automatically, even if the organizer leaves. <br><br> If this setting is **On**, anonymous and dial-in participants can start and join the meeting without a verified participant present.|
|**People dialing in can bypass the lobby**|This is a per-organizer policy. This setting controls whether people who dial in by phone join the meeting directly or wait in the lobby. When this setting is **Off**, dial-in users will wait in the lobby until an organizer, co-organizer, or presenter joins the meeting and admits them. When this setting is **On**, dial-in users will automatically join the meeting without going through the lobby. (If **Anonymous users and dial-in callers can start a meeting** is **Off**, they will wait in the lobby until the meeting starts.)|
|**Who can bypass the lobby**|This is a per-organizer policy. This setting controls which types of participants (except those dialing in by phone) join a meeting directly and which types of participants wait in the lobby until they're admitted by an organizer, co-organizer, or presenter.|

The following table shows how each option for the **Who can bypass the lobby** policy affects each *type of meeting participant*.

|Policy value:|Everyone|People in my organization, trusted organizations, and guests|People in my organization and guests|People in my organization|Only people who were invited|Only organizers and co-organizers|
|:--------|:------|:-----|:-----|:------|:-------|:---------------|
|*Organizer and co-organizers*|Bypass|Bypass|Bypass|Bypass|Bypass|Bypass|
|*People in the organization*|Bypass|Bypass|Bypass|Bypass|People who were sent or forwarded an invite will bypass; others wait in the lobby|Lobby|
|*Guests*|Bypass|Bypass|Bypass|Lobby|People who were sent or forwarded an invite will bypass; others wait in the lobby|Lobby|
|*People in trusted organizations*|Bypass|Bypass|Lobby|Lobby|People who were sent or forwarded an invite will bypass; others wait in the lobby|Lobby|
|*Anonymous participants*|Bypass|Lobby|Lobby|Lobby|Lobby|Lobby|

**Only people who were invited** applies only to verified participants who were sent an invite or to whom an invite was forwarded. Users added as a part of a distribution group will wait in the lobby.

## Choose who can bypass the lobby in meetings hosted by your organization

You can configure the settings and policies described above in the Teams admin center. See the sections below for guidance on which setting to choose for different circumstances. For information about how meeting policies work, see [Manage meeting policies in Microsoft Teams](/microsoftteams/meeting-policies-overview).

> [!Important]
> Meeting organizers can change the default values that you choose for the **People dialing in can bypass the lobby** and **Who can bypass the lobby** settings. If you need to enforce these settings to a particular value, you can use a meeting template or sensitivity label (Teams Premium required).  For more information, see [Configure the Microsoft Teams meeting lobby for sensitive meetings](configure-lobby-sensitive-meetings.md).

To set meeting join and lobby policies
1. In the Teams admin center, expand **Meetings** and then select **Meeting policies**.
1. Select the policy that you want to update.
1. In the **Participant & guests** sections, update the settings that you want to change:
   - **Let anonymous people join a meeting**
   - **Let anonymous people start a meeting**
   - **Automatically admit people** (Who can bypass the lobby)
   - **Dial-in users can bypass the lobby**

    ![Screenshot showing the meeting join and lobby policy in the Teams admin center.](media/meeting-join-and-lobby-tac-settings.png)
1. Select **Save**.

Note that changes can take up to twenty-four hours to take effect.

If you want to allow anonymous meeting access, be sure the **Anonymous users can join a meeting** meeting setting is also turned on.

To set the organization-wide meeting setting for anonymous meeting join
1. In the Teams admin center, expand **Meetings** and then select **Meeting settings**.
1. In the **Participants** section, set **Anonymous users can join a meeting** to **On** or **Off**.
    ![Screenshot showing the meeting join and lobby settings in the Teams admin center.](media/anonymous-users-can-join-meetings-org-setting.png)
1. Select **Save**.

## Control access to meetings by anonymous participants

Anonymous participants are anonymous because they are not logged in to an account that can be verified by Microsoft 365. This could include:

- People who are not logged in to Microsoft 365 with a work or school account 
- People from non-trusted organizations (as configured in [external access](manage-external-access.md)).
- People from organizations that you trust but which do not trust your organization

If you want to prevent anonymous participants from joining meeting completely, you can turn off the **Anonymous users can join a meeting** organization-wide meeting setting. You can also disable anonymous join for specific meeting organizers by using the **Anonymous users can join a meeting** meeting policy.

If you want people joining anonymously to wait in the lobby, you can set the **Who can bypass the lobby** meeting policy to any setting except **Everyone**. (This setting does not affect people dialing in by phone.)

By default, the **Anonymous users and dial-in callers can start a meeting** policy is **Off**. This means that anonymous participants and people calling in by phone will always wait in the lobby if a verified participant has not yet started the meeting. While you can turn this setting on if there are circumstances where you want to allow anonymous participants and people calling in by phone to start meetings, we recommend that you leave it off.  When the setting is on, people with unverified accounts can start meetings, including using the meeting link to have meetings at unscheduled times.

## Control access to meetings by people dialing in by phone

By default, the **People dialing in can bypass the lobby** policy is **Off**, but meeting organizers can change this when they set up the meeting. You can change the default by updating the **People dialing in can bypass the lobby** policy or you can enforce a particular value by using a meeting template.

## Control access to meetings by guests and people from trusted organizations

There are two types of people outside your organization who can join meetings as verified participants:

- Guests - people who have an [Azure Active Directory (Azure AD) B2B collaboration account](/azure/active-directory/external-identities/what-is-b2b) in your organization
- External access users - people who have Azure AD accounts in a trusted organization defined in Teams [external access](manage-external-access.md)

If you want all verified meeting participants from outside your organization to wait in the lobby, you can set the Who can bypass the lobby policy to **People in my organization** or **Only organizers and co-organizers** (as long as a guest isn't the organizer or co-organizer). If you want only people from trusted organizations (external access users) to wait in the lobby, you can choose **People in my organization and guests**.

## Control access to meetings by people without invitations

If you want to allow only people who have invitations to join meetings directly and have all other participants wait in the lobby, set **Who can bypass the lobby** to **Only people who were invited**. (People invited via distribution list are not included.)

The **Only people who were invited** setting includes verified participants to whom the invite was forwarded, not just those invited directly by the organizer. It doesn’t include people who have the meeting join link but not the invitation itself and unverified (anonymous) participants. They must wait in the lobby.

Note that meeting organizers can disable forwarding the meeting invite if they only want people directly invited by them to attend the meeting.

## Control access to meetings by non-organizers

If you have meetings where sensitive information is shared or that are subject to regulatory requirements, you might want to have all participants wait in the lobby until they are admitted by a meeting organizer or co-organizers. In this case, you can set **Who can bypass the lobby** to **Only organizers and co-organizers**.

Since **Who can bypass the lobby** only sets a default that meeting organizers can change, consider enforcing the value with a sensitivity label or meeting template if you have compliance requirements in this area. For more information, see [Configure the Microsoft Teams meeting lobby for sensitive meetings](configure-lobby-sensitive-meetings.md).

## Set meeting policies by using PowerShell

You can set the meeting policies described in this article by using the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) PowerShell cmdlet with the following parameters:

- [-AllowAnonymousUsersToJoinMeeting](/powershell/module/skype/set-csteamsmeetingpolicy?#-allowanonymoususerstojoinmeeting) to control if anonymous users can join meetings
- [-AllowPSTNUsersToBypassLobby](/powershell/module/skype/set-csteamsmeetingpolicy#-allowpstnuserstobypasslobby) to control if people dialing in by phone can bypass the lobby
- [-AutoAdmittedUsers](/powershell/module/skype/set-csteamsmeetingpolicy?#-autoadmittedusers) to control who can bypass the lobby

## Related topics

[Join a meeting without a Teams account](https://support.microsoft.com/office/c6efc38f-4e03-4e79-b28f-e65a4c039508)

[Using the Microsoft Teams admin center to configure organization-wide policy](meeting-settings-in-teams.md#allow-anonymous-users-to-join-meetings)

[External participants receive "Sign in to Teams to join, or contact the meeting organizer"](/microsoftteams/troubleshoot/meetings/external-participants-join-meeting-blocked)
