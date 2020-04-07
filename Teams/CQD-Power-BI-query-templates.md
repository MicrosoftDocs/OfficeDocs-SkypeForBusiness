---
title: "Use Power BI to analyze CQD data for Microsoft Teams"
ms.author: lolaj
author: LolaJacobsen
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
localization_priority: Normal
description: "Use Power BI to analyze CQD data for Microsoft Teams."
---


# Use Power BI to analyze CQD data for Microsoft Teams

New in January 2020: [Download Power BI query templates for CQD](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/CQD-Power-BI-query-templates.zip?raw=true). Customizable Power BI templates you can use to analyze and report your CQD data.

For CQD reports in Teams, if you'd rather use Power BI to query and report your data, download our CQD Power BI templates. When you open the templates in Power BI, you'll be prompted to sign in with your CQD admin credentials. You can customize these query templates and distribute them to anyone in your organization who has a Power BI license and CQD admin permissions.

Before you can use these PBIX files, you'll need to [Install the Power BI Connector for Microsoft CQD](CQD-Power-BI-connector.md) using the *MicrosoftCallQuality.pqx* file included in the [download](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/CQD-Power-BI-query-templates.zip?raw=true). 


|  |  |
|---------|---------|
|CQD Helpdesk Report.pbix     |Integrating building and EUII data, this report is designed to let you drill up from a single user to find the upstream root cause of poor call quality for that user (for example, the user is in a building that's experiencing network problems).         |
|CQD Location Enhanced Report.pbix     | Re-imagining CQD SPD location reports. Includes 9 reports, providing Call Quality, Building WiFi, Reliability, and Rate My Call (RMC) information with additional drill-thrus by Building or by User.        |
|CQD Mobile Device Report.pbix     | Provides insights specifically tuned towards mobile device users, including Call Quality, Reliability, and Rate My Call. View mobile network, WiFi network, and mobile operating system reports (Android, iOS).        |
|CQD PSTN Direct Routing Report.pbix     |Provides insights specific for PSTN calls that go through Direct Routing. To learn more, read [Using the CQD PSTN Direct Routing Report](CQD-PSTN-report.md).         |
|CQD Summary Report.pbix     |Better visualizations, improved presentation, increased information density, and rolling dates. These reports make it easier to identifier outliers. Drill into call quality by location with an easy-to-use interactive map. 9 new reports:</p>- Quality Overall<br>- Reliability Overall<br>- RMC (Rate My Call) Overall<br>- Conference Quality<br>- P2P Quality<br>- Conference Reliability<br>- P2P Reliability<br>- Conference RMC<br>- P2P RMC         |
|<strong>(New!)</strong> CQD Teams Utilization Report.pbix     | Shows how users in your organization are using Teams and how much. To learn more, read [Use CQD Power BI report to view Microsoft Teams utilization](CQD-teams-utilization-report.md).        |
|CQD User Feedback (Rate My Call) Report.pbix     | Shows Rate My Call data in a way that you can easily use to help support calling for your organization. Cross reference with verbatims to identify end user education opportunities.        |

> [!TIP]
> Once you've set up your Power BI reports for CQD data, add them as a tab to a channel. After you select **+** in a channel, select **Power BI** and then find your report. Remember, only people with a Power BI license and CQD admin credentials can access these reports.


## Related topics

[Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md)

[Set up Skype for Business Call Analytics](set-up-call-analytics.md)

[Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Call Analytics and Call Quality Dashboard](difference-between-call-analytics-and-call-quality-dashboard.md)
 