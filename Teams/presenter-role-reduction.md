---
title: Limit presenter role permissions for your org 
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: janineco
ms.date: 3/26/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
description: Learn how to limit presenter role permissions and capabilities in your org for IT Admins in Microsoft Teams. 
---

# Limit presenter role permissions for your org

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

In Microsoft Teams, presenters have responsibilities related to presenting, sharing content and  collaborating within the meeting or event. Presenters can mute attendees, change roles within the meeting, manage the lobby, and more.

If a meeting organizer has **Who can present** set to **Everyone** in their meeting options, anyone who the meeting link joins the meeting as a presenter.  When meeting organizers have **Who can present** set to **People in my organization** in their meeting options, anyone in their org with the meeting link joins the meeting as a presenter. These meeting option configurations can lead to attendees who are presenters by default having too many controls when they attend meetings. Event organizers select presenters when they create the invite, but they might want their presenters to focus on giving the presentation and engaging with attendees.

As an admin, you can limit presenter role permissions for your tenant. Limiting presenter role permissions only applies to personal accounts, excluding Meeting Teams Rooms.

For a complete table of the permissions presenters have when you restrict their role permissions, see the [Presenter capabilities](#presenter-capabilities) section in this article.

To learn more about the roles meeting organizers can assign, see [Roles in Microsoft Teams meetings](https://support.microsoft.com/office/roles-in-microsoft-teams-meetings-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

## Limit presenter role permissions using PowerShell

To limit presenter role permissions for your tenant, you must use the **`-LimitPresenterRolePermissions`** parameter within the [CsTeamsMeetingConfiguration](/powershell/module/skype/set-csteamsmeetingconfiguration) PowerShell cmdlet.

|Parameter value in PowerShell| Behavior|
|---------|---------------|
|True| Presenter role capabilities are reduced in your tenant. Presenters can’t enable or disable attendees’ mics and cameras, change the roles of other participants, lower hands, or remove other participants from the meeting.|
|False| **This is the default value.** Presenters in this tenant can enable and disable attendee mics and cameras, change the roles of other participants, lower hands, and remove other participants from the meeting. |

To limit presenter role capabilities for tenants with this policy, use the following script:

```powershell
Set-CsTeamsMeetingConfiguration -Identity <policy name> -LimitPresenterRolePermissions  $true
```

## Presenter capabilities

Here’s a complete table of the permissions that presenters have when you restrict their role permissions:

| Capability |Without policy to limit presenter role permissions| With policy to limit presenter role permissions|
|---------|---------------|---------------|
|Change the roles of other participants   | Yes| **No**|
|Disable attendee mics/cameras  | Yes| **No**|
|Enable individual or all attendee mics/cameras   | Yes| **No**|
|Lower hands | Yes| **No**|
|Remove participants| Yes| **No**|
|Mute other participants  | Yes| **No**|
|Add or remove an app  | Yes| Yes|
|Admit people from the lobby  | Yes| Yes|
|Change app settings  | Yes| Yes|
|Manage what attendees see <sup>1</sup>| Yes| Yes|
|Participate in meeting chat  | Yes| Yes|
|Privately view a PowerPoint file shared by someone else  | Yes| Yes|
|Share content  | Yes| Yes|
|Speak and share video  | Yes| Yes|
|Start or stop live transcription  | Yes| Yes|
|Start or stop recording  | Yes| Yes|
|Take control of someone else's PowerPoint presentation  | Yes| Yes|
|Use an app| Yes| Yes|
|Attendance report  | No| No|
|Change meeting options  | No| No|
|Edit meeting details | No| No|
|Graph API Supported | No| No|
|Manage breakout rooms  | No| No|
|Manage recording permissions  | No| No|
|Reschedule or cancel the meeting | No| No|

<sup>1</sup> When **Manage what attendees see** is enabled, presenters can still lower raised hands, and enable and disable attendees’ mics and cameras. You can enable **Manage what attendees see** through a meeting template or organizers can enable this option through their meeting options. To learn more about **Manage what attendees see**, see [Manage the meeting presentation experience for sensitive Teams meetings](manage-meeting-presentation-experience.md#manage-which-content-and-video-is-shared-with-attendees).

## Related topics

- [Meetings, webinars, and live events overview](quick-start-meetings-live-events.md)
- [Feature comparison](meeting-webinar-town-hall-feature-comparison.md)
- [Manage Teams with Microsoft Teams PowerShell](/microsoftteams/teams-powershell-managing-teams)
- [Manage the meeting presentation experience for sensitive Teams meetings](manage-meeting-presentation-experience.md#manage-which-content-and-video-is-shared-with-attendees)
- [Plan for meetings](plan-meetings.md)
- [Plan for webinars](plan-webinars.md)
- [Plan for town halls](plan-town-halls.md)
