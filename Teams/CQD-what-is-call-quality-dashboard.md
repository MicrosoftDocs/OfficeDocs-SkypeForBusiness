---
title: What is Call Quality Dashboard (CQD)?
ms.author: serdars
author: SerdarSoysal
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
  - ms.lync.lac.ToolsCallQualityDashboard
  - seo-marvel-apr2020
description: Learn about Call Quality Dashboard (CQD) and how to use it to  see reports on meeting and call quality in Microsoft Teams.
---

# What is Call Quality Dashboard (CQD)?

The Microsoft Call Quality Dashboard (CQD) - [https://cqd.teams.microsoft.com](https://cqd.teams.microsoft.com) - shows call and meeting quality, at an **org-wide level**, for Microsoft Teams, Skype for Business Online, and Skype for Business Server 2019. 

  
The latest version of CQD features a [near-real-time (NRT) data feed](CQD-data-and-reports.md), which means that call records are available in CQD within 30 minutes of the end of a call.

Wherever CQD includes [end-user identifiable information (EUII) data](CQD-data-and-reports.md#euii-data), it's managed in the same way as [EUII throughout Microsoft 365](https://docs.microsoft.com/office365/Enterprise/office-365-data-retention-deletion-and-destruction-overview).

CQD is designed to help Teams admins, Skype for Business admins, and network engineers monitor call and meeting quality at an org-wide level. You'll use CQD to help you **optimize your network** to drive performance quality. When you need to look into call and meeting information for a **specific user**, use CQD data in conjunction with per-user [call analytics](use-call-analytics-to-troubleshoot-poor-call-quality.md).

For example, using CQD, you can determine that a user's poor call quality (which you observed using per-user call analytics) is due to a network issue that also affects many other users. CQD captures both the individual call experience and the overall quality of calls made using Teams or Skype for Business. With CQD, overall patterns may become apparent, so network engineers can make informed assessments of call quality. CQD provides reports of call quality metrics that give you insight into overall call quality, server-client streams, client-client streams, and voice quality [SLA](https://go.microsoft.com/fwlink/p/?linkid=846252). 
  
![Screenshot of Call Quality Dashboard.](media/teams-difference-between-call-analytics-and-call-quality-dashboard-image3.png)

In CQD, we encourage you to upload building and endpoint information, which lets you use Location-Enhanced Reports to analyze call quality and reliability within a user's building. The data can be assessed to determine if the problem is isolated to a single user or affects a larger segment of users. To turn on building or endpoint-specific views in CQD, an admin must [upload building or endpoint information](CQD-upload-tenant-building-data.md) on the CQD **Tenant Data Upload** page.

![Screenshot of Call Quality Dashboard's Location-Enhanced Reports.](media/teams-difference-between-call-analytics-and-call-quality-dashboard-image4.png)

Don't miss our [Manage call and meeting quality](quality-of-experience-review-guide.md) article, which offers in-depth guidance for the Teams admin or support engineer responsible for managing service quality in Teams.

## Older version of CQD (CQD.lync.com)

The current version of CQD (https://CQD.Teams.microsoft.com) is replacing the older version of CQD (https://CQD.lync.com). You can still use CQD.lync.com (available from the Skype for Business admin center), but as of July 1, 2020, it's using the data from CQD.Teams.microsoft.com. We'll turn off access to CQD.lync.com soon, so you should move to CQD.Teams.microsoft.com if you haven't already done so.

> [!IMPORTANT]
> As of July 1, 2020, you can no longer view or modify your building or query data from the old CQD (CQD.lync.com). If you haven't already migrated this data from CQD.lync.com and still need it, log a support ticket.

## Use Power BI to analyze CQD data

New in January 2020: [Download Power BI query templates for CQD](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/CQD-Power-BI-query-templates.zip?raw=true). Customizable Power BI templates you can use to analyze and report your CQD data.

Read [Use Power BI to analyze CQD data](CQD-Power-BI-query-templates.md) to learn more.



## Related topics

[Improve and monitor call quality for Teams](monitor-call-quality-qos.md)

[Set up Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md)

[Upload tenant and building data](CQD-upload-tenant-building-data.md)

[CQD data and reports](CQD-data-and-reports.md)

[Use CQD to manage call and meeting quality](quality-of-experience-review-guide.md)

[Dimensions and measures available in CQD](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in CQD](stream-classification-in-call-quality-dashboard.md)

[Use Power BI to analyze CQD data](CQD-Power-BI-query-templates.md)


[Teams Troubleshooting](https://docs.microsoft.com/MicrosoftTeams/troubleshoot/teams)