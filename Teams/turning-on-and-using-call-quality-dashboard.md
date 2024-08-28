---
title: Call Quality Dashboard (CQD) setup
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: mikedav, siunies, gageames, jamp
ms.date: 07/25/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
search.appverid: MET150
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Reporting
  - ms.teamsadmincenter.directrouting.cqd
  - ms.lync.lac.ToolsCallQualityDashboard
  - seo-marvel-apr2020
description: Learn about how to turn on and use the Call Quality Dashboard (CQD) and get summary reports of quality of calls.
---
# Set up the Call Quality Dashboard

Open the Microsoft Call Quality Dashboard (CQD) at [https://cqd.teams.microsoft.com](https://cqd.teams.microsoft.com) (sign in with your admin credentials). Or go to the Teams admin center and select **Analytics & reports** > **Call Quality Dashboard**.

On the page that opens, select **Sign in** and enter the credentials for an administrator account that has "Activate CQD" privileges. This must be done only the first time your tenant accesses CQD in order to allow users holding less privileged admin roles to log in. CQD shows call and meeting quality at an org-wide level for Microsoft Teams and Skype for Business Server 2019.

> [!IMPORTANT]
> To use CQD with Skype for Business Server 2019, you'll have to [Configure Call Data Connector](/skypeforbusiness/hybrid/configure-call-data-connector). See [Plan Call Data Connector](/skypeforbusiness/hybrid/plan-call-data-connector) before you start.

## Assign admin roles for access to CQD

Assign [roles](/microsoft-365/admin/add-users/about-admin-roles) for accessing CQD to the people who need to use it.

If you want non-admin users (such as support engineers and helpdesk agents) to use Call Quality Dashboard, you can assign those users one of the following roles, which gives access to CQD.

Due to the fact that CQD is an aggregate reporting tool, users assigned to one or more [Administrative Units](/azure/active-directory/roles/administrative-units) don't see end-user identifying information (EUII) even if their role would ordinarily allow it.

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. To learn more, see [About Admin roles in the Microsoft 365 admin center](/microsoft-365/admin/add-users/about-admin-roles).

|&nbsp;  |View reports  |View EUII fields  |Create reports  |Upload building data  |Activate CQD |
|---------|:-------:|:-------:|:-------:|:-------:|:-------:|
|Global Administrator     |Yes         |Yes         |Yes         |Yes         |Yes  |
|Teams Administrator     |Yes         |Yes         |Yes         |Yes         |Yes  |
|Teams Communications Administrator     |Yes         |Yes         |Yes         |Yes         |Yes  |
|Teams Communications Support Engineer     |Yes         |Yes         |Yes         |No         |No  |
|Teams Communications Support Specialist     |Yes         |No         |Yes         |No         |No  |
|Skype for Business Administrator     |Yes         |Yes         |Yes         |Yes         |Yes  |
|Global Reader |Yes         |Yes         |Yes         |No         |No  |
|Reports Reader<sup>1</sup>     |Yes         |No         |Yes         |No         | No  |

<sup>1</sup> In addition to reading CQD reports, the Reports Reader can view all the [activity reports](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263) in the admin center and any reports from the [Microsoft 365 Adoption content pack](https://support.office.com/article/77ff780d-ab19-4553-adea-09cb65ad0f1f).

> [!NOTE]
> If you're not seeing [EUII (end-user identifiable information)](cqd-data-and-reports.md#euii-data) and you have one of the roles that's permitted to see this information, keep in mind that CQD only keeps EUII for 28 days. Anything older than 28 days is deleted. Additionally, users assigned to one or more [Administrative Units](/azure/active-directory/roles/administrative-units) don't see EUII even if their role would ordinarily allow it.

For more information about these roles, see [About Office 365 admin roles](/office365/admin/add-users/about-admin-roles).

After the first time you sign in with a role that can activate CQD, CQD will become accessible to admins with the lesser privileged roles as shown in the table.

## Use Power BI to analyze CQD data

[Download Power BI query templates for CQD](https://www.microsoft.com/download/details.aspx?id=102291). These are customizable Power BI templates you can use to analyze and report your CQD data.

Read [Use Power BI to analyze CQD data](CQD-Power-BI-query-templates.md) to learn more.

## Related topics

[Improve and monitor call quality for Teams](monitor-call-quality-qos.md)

[What is CQD?](CQD-what-is-call-quality-dashboard.md)

[Upload tenant and building data](CQD-upload-tenant-building-data.md)

[CQD data and reports](cqd-data-and-reports.md)

[Use CQD to manage call and meeting quality](quality-of-experience-review-guide.md)

[Dimensions and measures available in CQD](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in CQD](stream-classification-in-call-quality-dashboard.md)

[Use Power BI to analyze CQD data](CQD-Power-BI-query-templates.md)
