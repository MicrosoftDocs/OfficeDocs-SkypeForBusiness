---
title: Microsoft Teams meeting attendance report
ms.author: mabond
author: mkbond007
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: asappiah
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Get a meeting attendance report from inside Teams. This report complements the usage reports available from the Teams admin center.
appliesto: 
  - Microsoft Teams
ms.custom: 
---
# Microsoft Teams meeting attendance report

As an admin, you control whether meeting organizers can download an Attendance report by setting a Teams meeting policy. By default, the ability to download the report is turned on.

Meeting organizers can find this report in the **Participants** pane of the meeting, by clicking the download arrow as shown below. They can download the report as a .CSV file (text format).

:::image type="content" source="../media/meetings-attendance-download.JPG" alt-text="Control for downloading meeting attendance reports in Microsoft Teams.":::

> [!NOTE]
> As an administrator, you can’t view the attendance report for meetings that you don’t organize. However, you can view participant details for a given meeting within 24 hours of that meeting. In the Teams admin center, go to **Users** > **Manage users**. Choose the display name for the meeting organizer. Select the **Meetings & calls** tab, and then choose the appropriate meeting ID or call ID. Then, select **Participant details**.

For education tenants, this report is useful to track student attendance in online classes. For example, the teacher can download the Attendance report at the start of class as a simple way to do a "roll call." To learn more, read [Download attendance reports in Teams](https://support.office.com/article/download-attendance-reports-in-teams-ae7cf170-530c-47d3-84c1-3aedac74d310).

If meeting organizers need access to more meeting attendance data than they get from the report available within the meeting, you can assign the *Report reader* role so they can access the Teams admin reports themselves. To learn about this, read [Who can access the Teams activity reports](../teams-activity-reports.md#who-can-access-the-teams-activity-reports).

To turn it off in the Teams admin center, go to **Meetings** > **Meeting policies**, and set the **Attendance report** setting to **Off**. You can also edit an existing Teams meeting policy by using the [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy) cmdlet and set the `AllowEngagementReport` parameter to `Disabled`.

## Set attendance report policies in Teams admin center

1. From the Teams admin center, go to **Meetings** > **Meeting policies** and choose the policy you want to update. To create a new policy, click **Add**.
1. Under **Meeting scheduling**, choose the following for **Attendance report**
    1. If you want meeting organizers to have the option to turn on or off Attendance reports for a meeting, select **Everyone, unless organizers opt-out**. This setting is on by default.
    1. If you don't want meeting organizers to have the ability to view or download Attendance reports for a webinar or meeting they have organized, select **No one**.
    1. If you want all webinars or meetings to include an Attendance report without the option for meeting organizers to turn on or off, select **Everyone**.
1. For **Who's in the report**, choose the following:
    1. If you want all users to initially be included in the Attendance report but want to give them the option to opt out, select **Everyone, but users can opt-out**. This setting is on by default.
    1. If you don't want users to initially be included in the Attendance report but want to give them the option to opt in, select **No one, but users can opt-in**.
    1. If you want all users to be included in the Attendance report without the option to opt out, select **Everyone**.
    1. If you don't want users to be included in the Attendance report without the option to opt out, select **No one**.
1. For **Attendance information collection**, choose the following:
    1. If you want to include meeting attendees' join times, leave times, and in-meeting duration, select **All information**. This setting is on by default.
    1. If you don't want to include meeting attendees' join times, leave times, and in-meeting duration, select **Only who attended**.
1. Once you have made your policy setting selections, hit **Save** at the bottom of the page.

## Set attendance report policies with PowerShell

In PowerShell, the **AllowEngagementReport** parameter and [Set-CsTeamsMeetingPolicy cmdlet](/powershell/module/skype/set-csteamsmeetingpolicy) can be used to turn this on. This policy is on by default.

To turn off attendance reports, run the following command in PowerShell:

    ```powershell
    Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowEngagementReport Disabled
    ```

To turn on attendance reports for all webinars and meetings with users not initially included and only gathering the identity of users attending the meeting:

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
