--- 
title: Manage anonymous participants in Teams meetings
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
description: Learn how anonymous meeting participation works in Microsoft Teams.
---

# Manage anonymous participants in Teams meetings

start with a definition of anonymous users (unauthenticated & non federated)
Mention impact on meeting experience, meeting join and Lobby
Passed some content from our last Lobby article especially about Let anonymous people start a meeting policy
Nuances around external orgs that don't have trust set up or specific users who aren't enabled in external access

Four ways to attend meetings:
- Internal user
- Guest
- Participant from a trusted organization
- Anonymous


Circumstances when participant can be anonymous
- Not logged in to anything
- 


Questions:
- When do people show up as anonymous
- What can anonymous participants do


Admin intents
- Specify which users
- Turn on/off generally

## Control access to meetings by anonymous participants (from lobby article)

|Setting|Description|
|:------|:----------|
|**Anonymous users and dial-in callers can start a meeting**|This is a per-organizer policy that allows for leaderless meetings. This setting controls whether anonymous participants and dial-in users can join the meeting without a verified participant in attendance. This setting only applies when **Who can bypass the lobby** is set to **Everyone**. If the **Anonymous users can join a meeting** organization or meeting setting is **Off**, this setting only applies to dial-in callers. By default, this setting is turned off to prevent potential abuse of your meeting links by anonymous users. <br><br> While **Off**, anonymous participants and dial-in users will wait in the lobby until a verified participant (including a dial-in organizer) joins the meeting, at which point they will be automatically admitted. Once the meeting has started, anonymous participants and dial-in users will join the call automatically, even if the organizer leaves. <br><br> If this setting is **On**, anonymous and dial-in participants can start and join the meeting without a verified participant present.|


Anonymous participants are anonymous because they are not logged in to an account that can be verified by Microsoft 365. This could include:

- People who are not logged in to Microsoft 365 with a work or school account 
- People from non-trusted organizations (as configured in [external access](manage-external-access.md)).
- People from organizations that you trust but which do not trust your organization

If you want to prevent anonymous participants from joining meeting completely, you can turn off the **Anonymous users can join a meeting** organization-wide meeting setting. You can also disable anonymous join for specific meeting organizers by using the **Anonymous users can join a meeting** meeting policy.

If you want people joining anonymously to wait in the lobby, you can set the **Who can bypass the lobby** meeting policy to any setting except **Everyone**. (This setting does not affect people dialing in by phone.)

By default, the **Anonymous users and dial-in callers can start a meeting** policy is **Off**. This means that anonymous participants and people calling in by phone will always wait in the lobby if a verified participant has not yet started the meeting. While you can turn this setting on if there are circumstances where you want to allow anonymous participants and people calling in by phone to start meetings, we recommend that you leave it off.  When the setting is on, people with unverified accounts can start meetings, including using the meeting link to have meetings at unscheduled times.


## Allow anonymous users to join meetings

With anonymous join, anyone can join the meeting as an anonymous user by clicking the link in the meeting invitation. To learn more, see [Join a meeting without a Teams account](https://support.office.com/article/c6efc38f-4e03-4e79-b28f-e65a4c039508). You can control anonymous users' ability to join meetings either at your organization level, or per meeting organizer by using two different policy settings.

 ### Using the Microsoft Teams admin center to configure organization-wide policy

You must be a Teams admin to make these changes. See [Use Teams administrator roles to manage Teams](./using-admin-roles.md) to read about getting admin roles and permissions.

1. Go to the [Teams admin center](https://admin.teams.microsoft.com).

2. In the left navigation, go to **Meetings** > **Meeting settings**.

3. Under **Participants**, turn on **Anonymous users can join a meeting**.

    ![Screenshot of participants settings for meetings in the admin center.](media/meeting-settings-participants.png "Screenshot of participants settings for Teams meetings in the Microsoft Teams admin center")

> [!Important]
> If you don't want anonymous users to join meetings scheduled by users in your organization, turn off this setting.

### Using PowerShell to configure per-organizer policy

Admins can now control whether specific users or groups of users can let anonymous users join the meetings they organize. This new per-organizer policy is controlled by using the **-AllowAnonymousUsersToJoinMeeting** parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy). This comes with Teams PowerShell version 2.6.0 and later.

You can use either policy, organization-wide or per-organizer, to manage anonymous join. We recommend that you implement the per-organizer policy. The organization-wide policy setting will be deprecated in the future and the per-organizer policy will be the only way to control anonymous join.

Since both the organization-wide and per-organizer policies control anonymous join, the more restrictive setting will be effective. For example, if you don't allow anonymous join at the organization level, that will be your effective policy regardless of what you configure for the per-organizer policy. Therefore, in order to allow anonymous users to join meetings, you must configure both policies to allow anonymous join by setting the following values:

- **-DisableAnonymousJoin** set to **$false**
- **-AllowAnonymousUsersToJoinMeeting** set to **$true**

Any other combination of values will prevent anonymous users from joining meetings.
> [!NOTE]
> To learn more about managing meeting policies, see [Manage meeting policies in Microsoft Teams](/microsoftteams/meeting-policies-overview).

### Blocking anonymous join for specific client types

When anonymous users are allowed to join meetings, they can use either the Teams client or a custom client built using [Azure Communication Services](/azure/communication-services/). Admins can block selected client types using the **-BlockedAnonymousJoinClientTypes** parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

The possible values are:
- Null (default). All client types are allowed.
- Acs. Blocks custom clients built using [Azure Communication Services](/azure/communication-services/).
- Teams. Blocks the Teams client.

## Allow anonymous users to interact with apps in meetings

Anonymous users will now inherit the user-level global default permission policy. This control will then allow anonymous users to interact with apps in Teams meetings as long as the user-level permission policy has enabled the app. Note that anonymous users can only interact with apps that are already available in a meeting and cannot acquire and/or manage these apps. 

> [!IMPORTANT]
> By default, the setting to allow anonymous users to interact with apps in meetings is enabled.

 **Using the Microsoft Teams admin center**

You must be a Teams service admin to access this setting. See [Use Teams administrator roles to manage Teams](./using-admin-roles.md) to read about getting admin roles and permissions.

1. Go to the [Teams admin center](https://admin.teams.microsoft.com).

2. In the left navigation, go to **Meetings** > **Meeting settings**.

3. Under **Participants**, the setting for **Anonymous users can interact with apps in meetings** can be changed.

> [!Important]
> If you don't want anonymous users to interact with apps in meetings scheduled by users in your organization, turn off this setting.

## Related topics

[Join a meeting without a Teams account](https://support.microsoft.com/office/c6efc38f-4e03-4e79-b28f-e65a4c039508)

[Using the Microsoft Teams admin center to configure organization-wide policy](meeting-settings-in-teams.md#allow-anonymous-users-to-join-meetings)

[External participants receive "Sign in to Teams to join, or contact the meeting organizer"](/microsoftteams/troubleshoot/meetings/external-participants-join-meeting-blocked)
