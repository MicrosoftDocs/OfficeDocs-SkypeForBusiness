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



## Allow anonymous users to join meetings

With anonymous join, anyone can join the meeting as an anonymous user by clicking the link in the meeting invitation. To learn more, see [Join a meeting without a Teams account](https://support.office.com/article/join-a-meeting-without-a-teams-account-c6efc38f-4e03-4e79-b28f-e65a4c039508). You can control anonymous users' ability to join meetings either at your organization level, or per meeting organizer by using two different policy settings.

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
