---
title: Manage meeting policies 
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: sonua, shalenc
audience: admin
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.overview
  - seo-marvel-apr2020
description: Learn to manage meeting policy settings in Teams and use them to control the features available to meeting participants for meetings scheduled by users.
---

# Other meeting policy settings

## Designated presenter role mode

This is a per-user policy. This setting lets you change the default value of the **Who can present?** setting in **Meeting options** in the Teams client. This policy setting affects all meetings, including Meet Now meetings.

The **Who can present?** setting lets meeting organizers choose who can be presenters in a meeting. To learn more, see [Change participant settings for a Teams meeting](https://support.microsoft.com/article/change-participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e) and [Roles in a Teams meeting](https://support.microsoft.com/article/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

You can edit an existing Teams meeting policy by using the [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet. Or, create a new Teams meeting policy by using the [New-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/new-csteamsmeetingpolicy) cmdlet and assign it to users.

To specify the default value of the **Who can present?** setting in Teams, set the **DesignatedPresenterRoleMode** parameter to one of the following:

- **EveryoneUserOverride**:  All meeting participants can be presenters. This is the default value. This parameter corresponds to the **Everyone** setting in Teams.
- **EveryoneInCompanyUserOverride**: Authenticated users in the organization, including guest users, can be presenters. This parameter corresponds to the **People in my organization** setting in Teams.
- **OrganizerOnlyUserOverride**: Only the meeting organizer can be a presenter and all meeting participants are designated as attendees. This parameter corresponds to the **Only me** setting in Teams.

Additionally, you can edit this policy in the Teams admin center.

![Screenshot of Teams admin center](media/designated-presenter-role.png)

Keep in mind that after you set the default value, meeting organizers can still change this setting in Teams and choose who can present in the meetings that they schedule.

## Meeting attendance report

This is a per-user policy. This setting controls whether meeting organizers can download the [meeting attendance report](teams-analytics-and-reports/meeting-attendance-report.md).

Currently, you can only use PowerShell to configure this policy setting. You can edit an existing Teams meeting policy by using the [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet. Or, create a new Teams meeting policy by using the [New-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/new-csteamsmeetingpolicy) cmdlet and assign it to users.

To enable a meeting organizer to download the meeting attendance report, set the **AllowEngagementReport** parameter  to **Enabled**. When enabled, the option to download the report is displayed in the **Participants** pane.

To prevent a meeting organizer from downloading the report, set the parameter to **Disabled**. By default, this setting is disabled and the option to download the report isn't available.

## Meeting provider for Islands mode

This is a per-user policy. This setting controls which Outlook meeting add-in is used for *users who are in Islands mode*. You can specify whether users can only use the Teams Meeting add-in or both the Teams Meeting and Skype for Business Meeting add-ins to schedule meetings in Outlook.

You can only apply this policy to users who are in Islands mode and have the **AllowOutlookAddIn** parameter set to **True** in their Teams meeting policy.

Currently, you can only use PowerShell to set this policy. You can edit an existing Teams meeting policy by using the [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet. Or, create a new Teams meeting policy by using the [New-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/new-csteamsmeetingpolicy) cmdlet and assign it to users.

To specify which meeting add-in you want to be available to users, set the **PreferredMeetingProviderForIslandsMode** parameter as follows:

- Set the parameter to **TeamsAndSfB** to enable both the Teams Meeting add-in and Skype for Business add-in in Outlook. This is the default value.
- Set the parameter to **Teams** to enable only the Teams Meeting add-in in Outlook. This policy setting ensures that all future meetings have a Teams meeting join link. It doesn't migrate existing Skype for Business meeting join links to Teams. This policy setting doesn't affect presence, chat, PSTN calling, or any other capabilities in Skype for Business, which means that users will continue to use Skype for Business for these capabilities.

  If you set the parameter to **Teams**, and then switch back to **TeamsAndSfB**, both meeting add-ins are enabled. Existing Teams meeting join links **won't** be migrated to Skype for Business. Only Skype for Business meetings scheduled after the change will have a Skype for Business meeting join link.

## Video filters mode

This is a per-user policy. This setting controls whether users can customize their video background in a meeting.

Currently, you can only use PowerShell to set this policy. You can edit an existing Teams meeting policy by using the [Set-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet. Or, create a new Teams meeting policy by using the [New-CsTeamsMeetingPolicy](https://docs.microsoft.com/powershell/module/skype/new-csteamsmeetingpolicy) cmdlet, and then assign the policy to users.

To specify whether users can customize their video background in a meeting, set the **VideoFiltersMode** parameter as follows:

|Setting value in PowerShell |Behavior  |
|---------|---------|
|**NoFilters**     |User can't customize their video background.|
|**BlurOnly**     |Users can blur their video background. |
|**BlurandDefaultBackgrounds**     |User has the option to blur their video background or choose from the default set of images to use as their background. |
|**AllFilters**     |User has the option to blur their video background, choose from the default set of images, or upload custom images to use as their background. |

> [!IMPORTANT]
> Images uploaded by users aren't screened by Teams. When you use the **AllFilters** setting, you should have internal organization policies to prevent users from uploading offensive or inappropriate images, or images your organization don't have rights to use for Teams meeting backgrounds.

> [!NOTE]
> These features are not available for all Teams clients. For more information, see the _Video and backgrounds_ title in [Meetings and live events](https://support.microsoft.com/office/meetings-and-live-events-5c3e0646-dc37-45ad-84a4-1666fac62d4e).

## Meeting reactions

The AllowMeetingReactions setting can only be applied using PowerShell. There is no option to toggle AllowMeetingReactions on or off from the Teams admin center.

Meeting reactions are Off by default. Turning off reactions for a user doesn't mean that a user can't use reactions in meetings they schedule. The meeting organizer can still turn on reactions from the meeting option page, regardless of the default setting.

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies to your users in Teams](assign-policies.md)
- [Remove the RestrictedAnonymousAccess Teams meeting policy from users](meeting-policies-restricted-anonymous-access.md)
