---
title: Manage the attendance and engagement report for meetings and events in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: richardzhang
ms.date: 10/14/2024
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
description: Collect meeting, webinar, and town hall attendance and engagement information from the attendance report in Microsoft Teams. The attendance report shows join times, leave times, and in-meeting duration by attendee. The engagement report shows how attendees reacted and interacted during the meeting or event.
appliesto: 
  - Microsoft Teams 
---

# Manage the attendance and engagement report for meetings and events in Microsoft Teams

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

[!INCLUDE[Teams Premium](../includes/teams-premium-ecm.md)]

The attendance and engagement report for Teams meetings and events provides detailed information about organizers and attendees. The report shows who attended a meeting, webinar, or town hall, along with the exact times each attendee joined and left, and other engagement metrics.

Organizers with a Teams Premium license can see engagement information that captures how attendees reacted and interacted during the meeting or event.
The engagement data shows the total count of attendees that performed the following actions:

- Unmuted during the meeting or event
- Turned on their cameras
- Raised their hands
- Used each type of meeting reaction
- Initiated questions, answers, and discussions through Q&A.

During the meeting or event, organizers can find the attendance report in the **People** > **Participants** pane of the meeting. After the meeting or event ends, organizers can view and download the attendance and engagement report under the **Attendance** tab of the invite. Organizers can also access the attendance report through the meeting or event's chat. To learn more about how meeting and event organizers can view and download the attendance and engagement report, see [Manage meeting attendance reports in Microsoft Teams](https://support.microsoft.com/office/ae7cf170-530c-47d3-84c1-3aedac74d310).

For education tenants, the attendance and engagement report can be used to track student attendance and engagement in online classes. For example, a teacher can download the attendance report at the start of class as a simple way to do a roll call. If the teacher has a Teams Premium license, they can also use the engagement report to see how many students reacted, raised their hand, unmuted, interacted with Q&A and turned on their cameras during the online class.

As an admin, you control whether organizers can view and download the attendance and engagement report, who can be included in the report, and what information can be included.

## Manage attendance report policies in Teams admin center

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you'd like to update. To create a new policy, select **Add**.
1. Navigate to the **Meeting scheduling** section.
1. Choose one of the following options for **Attendance and engagement report**:

    |Option|Behavior|
    |:------|:-----|
    |On, but organizers can turn it off|**This is the default.** Organizers with this policy can view and download the attendance and engagement reports for all meetings and events they create. They can also disable the attendance report in their meeting options.|
    |Off|Organizers with this policy can't view or download attendance and engagement reports for meetings and events they organize.|
    |On|Organizers with this policy can view and download the attendance and engagement report for all meetings and events they create; organizers can't turn off attendance and engagement reports.|

1. For **Include attendees in the report**, choose one of the following options:

    |Option|Behavior|
    |:------|:-----|
    |Yes, but attendees can opt out|**This is the default.** The attendance and engagement report initially includes all attendees with this policy. To opt out, attendees can set the **Identify me in attendance reports** toggle to **Off** in their Teams privacy settings.|
    |No, but attendees can opt in|The attendance and engagement report initially excludes all attendees with this policy. To opt in, attendees can set the **Identify me in attendance reports** toggle to **On** or **Off** in their Teams privacy settings.|
    |Always|The attendance and engagement report includes all attendees with this policy, and attendees can't opt out.|
    |Never|The attendance and engagement report excludes all attendees with this policy, and attendees can't opt in.|

1. For **Attendee information**, choose one of the following options:

    |Option|Behavior|
    |:------|:-----|
    |Show everything|**This is the default.** Include attendees' join times, leave times, and in-meeting duration.|
    |Only show who attended|Excludes attendees' join times, leave times, and in-meeting duration.|

1. Select **Save**

> [!NOTE]
> As an admin, you can’t view the attendance and engagement report for meetings and events that you didn't organize. However, you can view attendees' details for a given meeting, webinar, or town hall within 24 hours of that meeting or event. In the Teams admin center, go to **Users** > **Manage users**. Choose the display name for the meeting organizer. Select the **Meetings & calls** tab, and then choose the appropriate meeting ID or call ID. Then, select **Participant details**.

## Manage attendance report policies with PowerShell

To manage attendance and engagement reports, you can use the **`-AllowEngagementReport`** parameter in the PowerShell [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet.

To turn off attendance and engagement reports, use the following script:

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
- [Plan for webinars](../plan-webinars.md)
- [Plan for town halls](../plan-town-halls.md)
- [Plan for meetings](../plan-meetings.md)
- [Teams policies reference - Meeting policies](../settings-policies-reference.md#meeting-policies)
- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
