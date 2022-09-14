---
title: "Use Power BI to analyze CQD data for Microsoft Teams"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: siunies
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - remotework
search.appverid: MET150
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
description: "Use Power BI to analyze CQD data for Microsoft Teams."
---

# Use Power BI to analyze CQD data for Microsoft Teams

New in July 2022: The new Quality of Experience (QER) template has been added to the [Power BI query templates for CQD download](https://www.microsoft.com/download/details.aspx?id=102291). The QER is a powerful reporting template that supercedes the original CQD Power BI query templates released in 2020. While the original templates will remain available for demonstration purposes, they are no longer supported or updated and we recommend customers switch to the QER template which will continue to receive updates. Note that this does not apply to the CQD Teams Auto Attendant & Call Queue Historical Report.

For Call Quality Dashboard (CQD) reports in Teams, if you'd rather use Power BI to query and report your data, download our CQD Power BI templates. When you open the templates in Power BI, you'll be prompted to sign in with your CQD admin credentials. You can customize these query templates and distribute them to anyone in your organization who has a Power BI license and CQD admin permissions.

Before you can use these PBIT files, you'll need to [Install the Power BI Connector for Microsoft CQD](CQD-Power-BI-connector.md) using the *MicrosoftCallQuality.pqx* file included in the [download](https://www.microsoft.com/download/details.aspx?id=102291). 

Make sure you have the right [CQD access role](turning-on-and-using-call-quality-dashboard.md#assign-admin-roles-for-access-to-cqd) to access the Power BI reports. 

|Pbit |Description |
|:----------|:---------|
|<strong>(New!)</strong> QER.pbit     |  The Quality of Experience Report (QER) template empowers customers to proactively identify issues that are impacting the Teams meeting and calling experience before they escalate. Reports are also provided to enable administrators to respond quickly to escalating issues and help answer the question, "What happened during the meeting?"  This template provides the following reports:</p><li>Search – enables searching by Meeting URL, Conference ID, Subnet, or UPN.</li><li>Meeting Health Details – detailed metrics for a single meeting.</li><li>User Health Details – detailed metrics for a single user.</li><li>Media Health – high level overview of Key Health Indicators (KHI) for overall tenant meeting and calling health.</li><li>Media Setup – analyze media setup failures.</li><li>Media Reliability – analyze media reliability issues.</li><li>Audio/Video/Sharing Health – review mid-level KHIs for audio, video, or sharing health.</li><li>Audio/Video/Sharing Health Details – review detailed metrics on audio, video, or sharing health.</li><li>VPN – review the impact of VPN on meeting health. (Estimated or Mapped VPN)</li><li>Top 10 Reports – identify problem areas in your tenant.</li><li>Dailies – review daily report of KHIs.</li><li>Usage – general meeting and calling usage.</li><li>User Feedback – review user survey feedback, also known as Rate My Call.</li><li>Transport – identify networks that are blocking UDP.</li><li>Devices – review the impact of devices.</li><li>Clients - review client focused metrics.</li><li>Building Data – review the building data file in CQD.</li><li>PSTN Health and User Details – two reports that provide a high level summary as well as individual user health for PSTN based calls.</li><li>Network Metrics – two reports that display raw network metric details for jitter, packet loss, and latency.</li> <br/> This template is provided on an as-is basis, and supercedes the deprecated templates as indicated below.|
|CQD Teams Auto Attendant & Call Queue Historical Report.pbit     |  This template provides the following three reports:</p><li>Auto Attendant – showing analytics for calls coming into your Auto Attendants.</li><li>Call Queue – showing analytics for calls coming into your Call Queues.</li><li>Agent Timeline – showing a timeline view of agents being active in Call Queue calls.</li><br>To learn more, read [Auto Attendant & Call Queue Historical Report](aa-cq-cqd-historical-reports.md). |
|CQD Teams Utilization Report.pbit     | Shows how users in your organization are using Teams and how much. Make sure you upload the building data to maximize your reporting experience. To learn more, read [Use CQD Power BI report to view Microsoft Teams utilization](CQD-teams-utilization-report.md). |
|CQD PSTN Direct Routing Report.pbit <br/> *(Deprecated)*    | Example template that provides insights specific for PSTN calls that go through Direct Routing. To learn more, read [Using the CQD PSTN Direct Routing Report](CQD-PSTN-report.md). |
|CQD Helpdesk Report.pbit <br/> *(Deprecated)*     |Integrating building and EUII data, this template demonstrates how to build a report to enable drill through from a single user to find the upstream root cause of poor call quality for that user (for example, the user is in a building that's experiencing network problems). |
|CQD Location Enhanced Report.pbit <br/> *(Deprecated)*     | This example template re-imagines the CQD SPD location reports. Includes 9 reports, providing Call Quality, Building WiFi, Reliability, and Rate My Call (RMC) information with additional drill-thrus by Building or by User. Make sure you upload the building data to maximize your reporting experience. |
|CQD Mobile Device Report.pbit <br/> *(Deprecated)*     | This example template provides insights specifically tuned towards mobile device users, including Call Quality, Reliability, and Rate My Call. View mobile network, WiFi network, and mobile operating system reports (Android, iOS). |
|CQD Summary Report.pbit <br/> *(Deprecated)*    | A demonstration of how CQD combined with Power BI can provide better visualizations, improved presentation, increased information density, and rolling dates. These reports make it easier to identifier outliers. Drill into call quality by location with an easy-to-use interactive map. Nine new reports:</p>- Quality Overall<br>- Reliability Overall<br>- RMC (Rate My Call) Overall<br>- Conference Quality<br>- P2P Quality<br>- Conference Reliability<br>- P2P Reliability<br>- Conference RMC<br>- P2P RMC         |
|CQD User Feedback (Rate My Call) Report.pbit <br/> *(Deprecated)*    | Demonstration of a Power BI report using Rate My Call data in a way that you can easily use to help support calling for your organization. Cross-reference with verbatims to identify end user education opportunities. |

> [!TIP]
> Once you've set up your Power BI reports for CQD data, add them as a tab to a channel. After you select **+** in a channel, select **Power BI** and then find your report. To learn more, read [Embed report with the Power BI tab for Teams](/power-bi/service-embed-report-microsoft-teams). Remember, only people with a Power BI license and CQD admin credentials can access these reports.

## Related topics

[Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md)

[Set up Skype for Business Call Analytics](set-up-call-analytics.md)

[Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Call Analytics and Call Quality Dashboard](./monitor-call-quality-qos.md)
