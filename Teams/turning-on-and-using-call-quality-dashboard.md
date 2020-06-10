---
title: Set up Call Quality Dashboard (CQD)
ms.author: lolaj
author: LolaJacobsen
manager: serdars
ms.reviewer: mikedav, siunies, gageames
ms.topic: article
ms.assetid: 553fa13c-92d2-4d5c-a3d5-41a073cb047c
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
search.appverid: MET150
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords: 
  - CSH
ms.custom: 
  - Reporting
  - ms.teamsadmincenter.directrouting.cqd
  - ms.lync.lac.ToolsCallQualityDashboard
  - seo-marvel-apr2020
description: Learn about how to turn on and use the Call Quality Dashboard and get summary reports of quality of calls.
---

# Set up Call Quality Dashboard (CQD)

Open the Microsoft Call Quality Dashboard (CQD) at [https://cqd.teams.microsoft.com](https://cqd.teams.microsoft.com) (sign in with your admin credentials). Or go to the Teams admin center and select **Call Quality Dashboard**. On the page that opens, click **Sign in** and enter your Global Administrator account or Microsoft Teams Service Admin account information. After the first time you sign in, CQD will begin collecting and processing data. Keep in mind that it may take one or more hours to process enough data to display meaningful results in the reports.

CQD shows call and meeting quality, at an org-wide level, for Microsoft Teams, Skype for Business Online, and Skype for Business Server 2019. 

> [!IMPORTANT]
> To use CQD with Skype for Business Server 2019, you will have to [Configure Call Data Connector](https://docs.microsoft.com/skypeforbusiness/hybrid/configure-call-data-connector). See [Plan Call Data Connector](https://docs.microsoft.com/skypeforbusiness/hybrid/plan-call-data-connector) before you start.


## Assign admin roles for access to CQD

If you want non-admin users (such as support engineers and helpdesk agents) to use Call Quality Dashboard, you can assign those users one of the following roles, which gives access to CQD. 


|  |View reports  |View EUII fields  |Create reports  |Upload building data  |
|---------|:-------:|:-------:|:-------:|:-------:|
|Office 365 Global Administrator     |Yes         |Yes         |Yes         |Yes         |
|Teams Service Administrator     |Yes         |Yes         |Yes         |Yes         |
|Teams Communications Administrator     |Yes         |Yes         |Yes         |Yes         |
|Teams Communications Support Engineer     |Yes         |Yes         |Yes         |No         |
|Teams Communications Support Specialist     |Yes         |No         |Yes         |No         |
|Skype for Business Administrator     |Yes         |Yes         |Yes         |Yes         |
|Azure AD Global Reader |Yes         |Yes         |Yes         |No         |
|Office 365 Reports Reader<sup>1</sup>     |Yes         |No         |Yes         |No         |

<sup>1</sup> In addition to reading CQD reports, the Office 365 Reports Reader can view all the [activity reports](https://support.office.com/article/activity-reports-0d6dfb17-8582-4172-a9a9-aed798150263) in the admin center and any reports from the [Microsoft 365 Adoption content pack](https://support.office.com/article/Office-365-Adoption-content-pack-77ff780d-ab19-4553-adea-09cb65ad0f1f).

> [!NOTE]
> If you're not seeing EUII (end-user identifiable information) and you have one of the roles that's permitted to see this information, keep in mind that CQD only keeps EUII for 30 days. Anything older than 30 days is deleted.

For more information about these roles, see [About Office 365 admin roles](/office365/admin/add-users/about-admin-roles).


After the first time you sign in, CQD will begin collecting and processing data. As of December 2019, you can still access the older version of CQD (cqd.lync.com), although the legacy portal gives you a link to the latest CQD (cqd.teams.microsoft.com). Eventually, the older version of CQD will be decommissioned.


## Use Power BI to analyze CQD data

New in January 2020: [Download Power BI query templates for CQD](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/CQD-Power-BI-query-templates.zip?raw=true). Customizable Power BI templates you can use to analyze and report your CQD data.

Read [Use Power BI to analyze CQD data](CQD-Power-BI-query-templates.md) to learn more.

## Migrate reports from previous version of CQD

If  you created reports or uploaded tenant data (mapping) files to CQD for Skype for Business (https://cqd.lync.com) and want to migrate them to CQD for Teams (https://cqd.teams.microsoft.com), here's how:

1.    Go to [https://cqd.lync.com/cqd/](https://cqd.lync.com/cqd/) and browse to the report set you want to export. 
2.    Hover over the report and, on the "..." menu, choose **Export Report Tree**. Save the export file.
3.    Go to [https://cqd.teams.microsoft.com/cqd/](https://cqd.teams.microsoft.com/cqd/)  and browse to the location where you want to import the reports.
4.    From the links on the left, click **Import** and select the exported file. 
5.    After the reports are imported, you'll see this message: "Report import was successful. The new report has been added at the end of report set." 



## Related topics

[Improve and monitor call quality for Teams](monitor-call-quality-qos.md)

[What is CQD?](CQD-what-is-call-quality-dashboard.md)

[Upload tenant and building data](CQD-upload-tenant-building-data.md)

[CQD data and reports](CQD-data-and-reports.md)

[Use CQD to manage call and meeting quality](quality-of-experience-review-guide.md)

[Dimensions and measures available in CQD](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in CQD](stream-classification-in-call-quality-dashboard.md)

[Use Power BI to analyze CQD data](CQD-Power-BI-query-templates.md)
