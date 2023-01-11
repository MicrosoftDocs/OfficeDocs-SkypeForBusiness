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

Anonymous participants in meetings are those who's identity can't be verified. This could include:

- People who are not logged in to Microsoft 365 with a work or school account 
- People from non-trusted organizations (as configured in [external access](manage-external-access.md)).
- People from organizations that you trust but which do not trust your organization

Anonymous meeting join is controlled by an organization level setting and user level policies. For anonymous meeting join to work, the **anonymous participants can join a meeting** organization level setting must be turned on and the meeting organizer must be assigned a policy where the **Let anonymous people join a meeting** is turned on. Anonymous join is turned on by default for the organization and in the default global meeting policy.

To understand how anonymous participants interact with the meeting lobby, see [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md).

#### Meetings with trusted organizations

When you set up [trusted organizations for external meetings and chat](manage-external-access.md), keep in mind that the organizations that you trust must also trust your organization, and their users must be enabled for external access. If not, these participants will show up as anonymous when joining your meetings.

## Manage anonymous meeting join for the organization

The organization level anonymous meeting join setting must be turned on for anyone in the organization to create meetings that allow anonymous participants.

> [!Important]
> The **Anonymous participants can join a meeting** organization-wide setting will be removed in the future. We recommend leaving this setting **On** and using the the **Let anonymous people join a meeting** user level meeting policy control instead.

To configure anonymous meeting join for the organization
1. Go to the [Teams admin center](https://admin.teams.microsoft.com).

1. In the left navigation, go to **Meetings** > **Meeting settings**.

1. Under **Participants**, set **Anonymous participants can join a meeting** to **On** or **Off**.

    ![Screenshot of participants settings for meetings in the admin center.](media/meeting-settings-participants.png "Screenshot of participants settings for Teams meetings in the Microsoft Teams admin center")

1. Select **Save**.

## Manage anonymous meeting join for meeting organizers

A meeting policy with anonymous meeting join turned on must be assigned to each meeting organizer who needs to create meetings that allow anonymous participants.

To configure anonymous meeting join for specific meeting organizers
1. Go to the [Teams admin center](https://admin.teams.microsoft.com).

1. In the left navigation, go to **Meetings** > **Meeting policies**.

1. Select the policy that you want to modify.

1. Set **Let anonymous people join a meeting** to **On**.

1. Select **Save**.

## Configure anonymous meeting join using PowerShell

You can control whether anonymous participants can join meetings by using:

- The `-DisableAnonymousJoin` parameter in [Set-CsTeamsMeetingConfiguration](/powershell/module/skype/set-csteamsmeetingconfiguration) to configure the organization level setting
- The `-AllowAnonymousUsersToJoinMeeting` parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) to configure a user level meeting policy

In order to allow anonymous participants to join meetings, you must configure both to allow anonymous join by setting the following values:

- `Set-CsTeamsMeetingPolicy -DisableAnonymousJoin` set to **$false**
- `Set-CsTeamsMeetingConfiguration -AllowAnonymousUsersToJoinMeeting` set to **$true** for the relevant meeting organizers

## Control if anonymous participants can start a meeting

The **anonymous participants and dial-in callers can start a meeting** policy setting controls whether anonymous participants and dial-in users can join a meeting without a verified participant in attendance. 

By default, the **Anonymous participants and dial-in callers can start a meeting** policy is **Off**. This means that anonymous participants and people calling in by phone will always wait in the lobby if a verified participant has not yet started the meeting. While you can turn this setting on if there are circumstances where you want to allow anonymous participants and people calling in by phone to start meetings, we recommend that you leave it off.  When the setting is on, people with unverified accounts can start meetings, including using the meeting link to have meetings at unscheduled times.

For information on how to configure this setting, see [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md).

## Block anonymous join for specific client types

When anonymous participants are allowed to join meetings, they can use either the Teams client or a custom client built using [Azure Communication Services](/azure/communication-services/). 

Admins can block either of these client types by using the `-BlockedAnonymousJoinClientTypes` parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy#-blockedanonymousjoinclienttypes).

## Allow anonymous participants to interact with apps in meetings

Anonymous participants will now inherit the user-level global default permission policy. This control will then allow anonymous participants to interact with apps in Teams meetings as long as the user-level permission policy has enabled the app. 

Note that anonymous participants can only interact with apps that are already available in a meeting and cannot acquire and/or manage these apps. 

By default, the setting to allow anonymous participants to interact with apps in meetings is enabled.

To configure app access for anonymous meeting participants

1. Go to the [Teams admin center](https://admin.teams.microsoft.com).

1. In the left navigation, go to **Meetings** > **Meeting settings**.

1. Under **Participants**, set  **Anonymous participants can interact with apps in meetings** to **On** or **Off**.

## Related topics

[Join a meeting without a Teams account](https://support.microsoft.com/office/c6efc38f-4e03-4e79-b28f-e65a4c039508)

[Using the Microsoft Teams admin center to configure organization-wide policy](meeting-settings-in-teams.md#allow-anonymous-users-to-join-meetings)

[External participants receive "Sign in to Teams to join, or contact the meeting organizer"](/microsoftteams/troubleshoot/meetings/external-participants-join-meeting-blocked)
