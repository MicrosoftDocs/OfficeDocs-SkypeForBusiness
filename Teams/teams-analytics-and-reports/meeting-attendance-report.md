---
title: Attendance report for meetings and webinars in Microsoft Teams
ms.author: mabond
author: mkbond007
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: asappiah
ms.date: 05/12/2020
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Collect meeting or webinar attendance information from the attendance report in Microsoft Teams. The attendance report shows join times, leave times, and in-meeting duration by attendee.
appliesto: 
  - Microsoft Teams
ms.custom: 
---
# Attendance report for meetings and webinars in Microsoft Teams

As an admin, you control whether meeting organizers can download an attendance report by settings in a Teams meeting policy. By default, the ability to download the report is turned on.

During the meeting, organizers can find the attendance report in the **People** > **Participants** pane of the meeting, as well as areas within the meeting invite and in the meeting chat. For education tenants, attendance report is useful to track student attendance in online classes. For example, the teacher can download the attendance report at the start of class as a simple way to do a roll call. Read more about [how organizers can view and download attendance reports in Teams](https://support.microsoft.com/office/ae7cf170-530c-47d3-84c1-3aedac74d310).

## Set attendance report policies in Teams admin center

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, click **Add**.
1. Under **Meeting scheduling**, choose one of the following for **Attendance report**:
    - **Everyone, unless organizers opt-out** - Meeting organizers to have the option to turn on or off attendance reports for a meeting. This setting is on by default.
    - **No one** - Meeting organizers can't view or download attendance reports for a webinar or meeting they have organized.
    - **Everyone** - Meeting organizers can't turn off attendance reports for a webinar or meeting.
1. For **Who's in the report**, choose one of the following:
    - **Everyone, but users can opt-out** - All users are initially included from the attendance report, but they can opt-out. This setting is on by default.
    - **No one, but users can opt-in** - All users are initially excluded from the attendance report, but they can opt-in.
    - **Everyone** - All users are included in the attendance report, and users can't opt-out.
    - **No one** - All users are excluded from the attendance report, and users can't opt-in.
1. For **Attendance information collection**, choose one of the following:
    - **All information** - Include meeting attendees' join times, leave times, and in-meeting duration. This setting is on by default.
    - **Only who attended** - Doesn't include meeting attendees' join times, leave times, and in-meeting duration.
1. Once you have made your policy setting selections, hit **Save** at the bottom of the page.

> [!NOTE]
> As an administrator, you can’t view the attendance report for meetings that you don’t organize. However, you can view participant details for a given meeting within 24 hours of that meeting. In the Teams admin center, go to **Users** > **Manage users**. Choose the display name for the meeting organizer. Select the **Meetings & calls** tab, and then choose the appropriate meeting ID or call ID. Then, select **Participant details**.

## Set attendance report policies with PowerShell

In PowerShell, the `-AllowEngagementReport` parameter and [Set-CsTeamsMeetingPolicy cmdlet](/powershell/module/skype/set-csteamsmeetingpolicy) can be used to turn this on. This policy is on by default.

To turn off attendance reports, run the following:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowEngagementReport Disabled
```

To turn on attendance reports that initially exclude all users, but that give users the option to opt-in, and that will only gather the identity of users attending the meeting, run the following:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowEngagementReport ForceEnabled
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowTrackingInReport DisabledUserOverride
Set-CsTeamsMeetingPolicy -Identity <policy name> -InfoShownInReportMode identityOnly
```

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
- [Teams usage report](teams-usage-report.md)
- [Teams policies reference - Meeting policies](../settings-policies-reference.md#meeting-policies)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
