---
title: Attendance report for meetings, webinars, and town halls in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: richardzhang
ms.date: 03/28/2023
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
description: Collect meeting or webinar attendance information from the attendance report in Microsoft Teams. The attendance report shows join times, leave times, and in-meeting duration by attendee.
appliesto: 
  - Microsoft Teams 
---

# Attendance report for meetings and webinars in Microsoft Teams

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

The attendance report for Teams meetings, webinars, and town halls shows organizers who attended a meeting, webinar, or town hall, what time each person joined and left, and more. As an admin, you control whether organizers can download an attendance report (formerly known as an "engagement report"). By default, the ability to download the report is on.

During the meeting or event, organizers can find the attendance report in the **People** > **Participants** pane of the meeting, in areas within the invite, and in the chat. After the meeting or event has ended, organizers can view and download the attendance report under the **Attendance** tab of the meeting invite or meeting chat. Read more about [how meeting organizers can view and download attendance reports in Teams](https://support.microsoft.com/office/ae7cf170-530c-47d3-84c1-3aedac74d310).

For education tenants, the attendance report can be used to track student attendance in online classes. For example, a teacher can download the attendance report at the start of class as a simple way to do a roll call.

## Manage attendance report policies in Teams admin center

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you'd like to update. To create a new policy, select **Add**.
1. Under **Meeting scheduling**, choose one of the following options for **Attendance report**:
    - **Everyone, unless organizers opt-out** - Organizers control whether attendance reports are on or off for their meetings, town halls or webinars.
    - **No one** - Organizers can't view or download attendance reports for webinars, town halls, or meetings they've organized.
    - **Everyone** - The attendance report is available for all webinars, town halls, or meetings organizers create; organizers can't turn off attendance reports.

1. For **Who is in the report**, choose one of the following options:
    - **Everyone, but participants can opt-out** -  This option is the **default setting.** The attendance report initially includes all participants. To opt out, participants can set the **Identify me in attendance reports** toggle to **off** in their Teams privacy settings.
    - **No one, but participants can opt-in** - The attendance report initially excludes all participants. To opt in, Participants can set the **Identify me in attendance reports** toggle to on or off in their Teams privacy settings.
    - **Everyone** - The attendance report includes all participants, and participants can't opt out.
    - **No one** - The attendance report excludes all participants, and participants can't opt in.
1. For **Attendance summary**, choose one of the following options:
    - **Show everything** - Include attendees' join times, leave times, and in-meeting duration. This setting is on by default.
    - **Only show who attended** - Doesn't include attendees' join times, leave times, and in-meeting duration.
1. Once you've made your policy setting selections, select **Save** at the bottom of the page.

> [!NOTE]
> As an administrator, you can’t view the attendance report for meetings, webinars, or town halls that you don’t organize. However, you can view participant details for a given meeting, webinar, or town hallwithin 24 hours of that meeting. In the Teams admin center, go to **Users** > **Manage users**. Choose the display name for the meeting organizer. Select the **Meetings & calls** tab, and then choose the appropriate meeting ID or call ID. Then, select **Participant details**.

## Manage attendance report policies with PowerShell

In PowerShell, you can use the `-AllowEngagementReport` parameter and [Set-CsTeamsMeetingPolicy cmdlet](/powershell/module/skype/set-csteamsmeetingpolicy) to turn on attendance reports. This policy is on by default.

To turn off attendance reports, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowEngagementReport Disabled
```

To turn on attendance reports that initially exclude all participants, but provide participants the ability to opt in, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowEngagementReport ForceEnabled
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowTrackingInReport DisabledUserOverride
```

To give organizers the option to turn on or turn off attendance reports that only show who attended and exclude other data, run the following script:

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
