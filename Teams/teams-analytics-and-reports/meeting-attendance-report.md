---
title: Manage the attendance report for meetings and events in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: richardzhang
ms.date: 10/25/2023
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
description: Collect meeting, webinar, and town hall attendance and engagement information from the attendance report in Microsoft Teams. The attendance report shows join times, leave times, and in-meeting duration by attendee.
appliesto: 
  - Microsoft Teams 
---

# Manage the attendance report for meetings and events in Microsoft Teams

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

[!INCLUDE[Teams Premium](../includes/teams-premium-ecm.md)]

The attendance and engagement report for Teams meetings and events shows organizers who attended a meeting, webinar, or town hall, what time each attendee joined, left, and more.

Organizers with a Teams Premium license can see engagement information that captures how attendees reacted and interacted during the meeting or event. The engagement data shows the total count of attendees that unmuted, turned on their cameras, raised their hands, used each type of meeting reaction, as well as the total of questions, answers, and discussions initiated by anyone through Q&A.

During the meeting or event, organizers can find the attendance and engagement report in the **People** > **Participants** pane of the meeting, in areas within the invite, and in the chat. After the meeting or event has ended, organizers can view and download the attendance and engagement report under the **Attendance** tab of the invite or chat. Read more about [how meeting organizers can view and download attendance reports in Teams](https://support.microsoft.com/office/ae7cf170-530c-47d3-84c1-3aedac74d310).

For education tenants, the attendance and engagement report can be used to track student attendance and engagement in online classes. For example, a teacher can download the attendance report at the start of class as a simple way to do a roll call. If the teacher has a Teams Premium license, they can also see how many students reacted, raised their hand, unmuted, interacted with Q&A and turned on their cameras during the online class.

As an admin, you control whether organizers can view and download the attendance and engagement report, who can be included in the report, and what information can be included.

## Manage attendance report policies in Teams admin center

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you'd like to update. To create a new policy, select **Add**.
1. Under **Meeting scheduling**, choose one of the following options for **Attendance and engagement report**:
    - **Everyone, unless organizers opt-out** - **This is the default.** Organizers with this policy can view and download the attendance and engagement reports for all meetings and events they create. However, they can also disable the attendance report in their meeting options.
    - **No one** - Organizers with this policy can't view or download attendance and engagement reports for webinars, town halls, or meetings they've organized.
    - **Everyone** - The attendance and engagement report is available to view and download for all webinars, town halls, and meetings organizers with this policy create; organizers can't turn off attendance and engagement reports.

1. For **Include attendees in the report**, choose one of the following options:
    - **Yes, but attendees can opt-out** -  **This is the default.** The attendance and engagement report initially includes all attendees. To opt out, attendees can set the **Identify me in attendance reports** toggle to **off** in their Teams privacy settings.
    - **No, but attendees can opt-in** - The attendance and engagement report initially excludes all attendees. To opt in, attendees can set the **Identify me in attendance reports** toggle to on or off in their Teams privacy settings.
    - **Always** - The attendance and engagement report includes all attendees, and attendees can't opt out.
    - **Never** - The attendance and engagement report excludes all attendees, and attendees can't opt in.
1. For **Attendance information**, choose one of the following options:
    - **Show everything** - **This is the default.** Include attendees' join times, leave times, and in-meeting duration.
    - **Only show who attended** - Doesn't include attendees' join times, leave times, and in-meeting duration.
1. Select **Save**

> [!NOTE]
> As an administrator, you can’t view the attendance and engagement report for meetings and events that you didn't organize. However, you can view attendees details for a given meeting, webinar, or town hall within 24 hours of that meeting or event. In the Teams admin center, go to **Users** > **Manage users**. Choose the display name for the meeting organizer. Select the **Meetings & calls** tab, and then choose the appropriate meeting ID or call ID. Then, select **Participant details**.

## Manage attendance report policies with PowerShell

In PowerShell, you can use the `-AllowEngagementReport` parameter and [Set-CsTeamsMeetingPolicy cmdlet](/powershell/module/skype/set-csteamsmeetingpolicy) to turn on attendance and engagement reports. This policy is on by default.

To turn off attendance reports, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowEngagementReport Disabled
```

To turn on attendance and engagement reports that initially exclude all attendees, but provide attendees the ability to opt in, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowEngagementReport ForceEnabled
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowTrackingInReport DisabledUserOverride
```

To give organizers the option to turn attendance and engagement reports that only show who attended and exclude other data on or off, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowEngagementReport Enabled
Set-CsTeamsMeetingPolicy -Identity <policy name> -InfoShownInReportMode identityOnly
```

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
- [Teams usage report](teams-usage-report.md)
- [Manage who can schedule webinars](../set-up-webinars.md)
- [Manage who can schedule town halls](../set-up-town-halls.md)
- [Teams policies reference - Meeting policies](../settings-policies-reference.md#meeting-policies)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
