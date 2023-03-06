---
title: Attendance report for meetings and webinars in Microsoft Teams
ms.author: mabond
author: mkbond007
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: richardzhang
ms.date: 02/24/2023
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - tier1
description: Collect meeting or webinar attendance information from the attendance report in Microsoft Teams. The attendance report shows join times, leave times, and in-meeting duration by attendee.
appliesto: 
  - Microsoft Teams
ms.custom: 
---
# Attendance report for meetings and webinars in Microsoft Teams

As an admin, you control whether meeting organizers can download an attendance report by settings in a Teams meeting policy. By default, the ability to download the report is on.

During the meeting, organizers can find the attendance report in the **People** > **Participants** pane of the meeting, in areas within the meeting invite, and in the meeting chat. After the meeting has ended, organizers can view and download the attendance report under the **Attendance** tab of the meeting invite or meeting chat. Read more about [how meeting organizers can view and download attendance reports in Teams](https://support.microsoft.com/office/ae7cf170-530c-47d3-84c1-3aedac74d310).

For education tenants, the attendance report can be used to track student attendance in online classes. For example, a teacher can download the attendance report at the start of class as a simple way to do a roll call.

## Set attendance report policies in Teams admin center

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, click **Add**.
1. Under **Meeting scheduling**, choose one of the following for **Attendance report**:
    - **Everyone, unless organizers opt-out** - Meeting organizers to can turn on or off attendance reports for a meeting. This setting is on by default.
    - **No one** - Meeting organizers can't view or download attendance reports for a webinar or meeting they have organized.
    - **Everyone** - Meeting organizers can't turn off attendance reports for a webinar or meeting.
1. For **Who's in the report**, choose one of the following:
    - **Everyone, but users can opt-out** - The attendance report will initially include all users, but users can opt-out. This setting is on by default.
    - **No one, but users can opt-in** - The attendance report will initially exclude all users, but users can opt-in.
    - **Everyone** - The attendance report will include all users, and users can't opt-out.
    - **No one** - The attendance report will exclude all users, and users can't opt-in.
1. Once you have made your policy setting selections, hit **Save** at the bottom of the page.

> [!NOTE]
> As an administrator, you can’t view the attendance report for meetings that you don’t organize. However, you can view participant details for a given meeting within 24 hours of that meeting. In the Teams admin center, go to **Users** > **Manage users**. Choose the display name for the meeting organizer. Select the **Meetings & calls** tab, and then choose the appropriate meeting ID or call ID. Then, select **Participant details**.

## Set attendance report policies with PowerShell

In PowerShell, you can use the `-AllowEngagementReport` parameter and [Set-CsTeamsMeetingPolicy cmdlet](/powershell/module/skype/set-csteamsmeetingpolicy) to turn on attendance reports. This policy is on by default.

To turn off attendance reports, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowEngagementReport Disabled
```

To turn on attendance reports that will initially exclude all users but that will give users the ability to opt-in, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowEngagementReport ForceEnabled
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowTrackingInReport DisabledUserOverride
```

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
- [Teams usage report](teams-usage-report.md)
- [Teams policies reference - Meeting policies](../settings-policies-reference.md#meeting-policies)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
