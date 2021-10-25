---
title: Microsoft Teams app usage report
author: SerdarSoysal
ms.author: serdars
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: v-quhur
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to use the Teams app usage report in the Microsoft Teams admin center.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams app usage report

The Teams app usage report in the Microsoft Teams admin center provides you with information about which apps users are using in Teams.  

## View the App Usage report

1.  In the left navigation of the admin center at <https://admin.teams.microsoft.com>, click **Analytics & reports** > **Usage reports**. 
2.  On the **View reports** tab, under **Report**, select **Apps Usage**.

3.  Under **Date range**, select a range, and then click **Run report**.

      :::image type="content" source="media/app-usage-report4.png" alt-text="Screenshot of the Apps Usage report.":::<br><br>

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |The Teams Apps usage report can be viewed for trends over the last 7, 30 or 90 days.<br><br>![Screenshot of the Teams app usage report in the Teams admin center with callouts.](media/app-usage-report5.png "Screenshot of the Teams app usage report in the Teams admin center with callouts")|
|**2**   |Each report has a date for when the report was generated. The reports usually reflect a 24-hour latency from the time an app was opened.
|**3**    | The X axis on the charts is the selected date range for the report. The Y axis is the number of users who for the given day hovered over in chart, those users have opened an app at least once and by doing so are considered an Active User and accrue towards the total seen on mouse hover over.|
|**4**   |Hover over the dot representing an Apps Usage on any date to see the number of that App’s Total Active Users on that date.  |
|**5**   |All Apps will be included. At the upper right, select the **Filter** icon to see additional filters.  |
|**6**   |The table gives you a breakdown of active users and teams by App name.<br><ul><li>**App name** is the display name of the app used in Teams.</li><li>**Active users** is the number of users who opened the app at least once during the specified time period.</li><li>**App type** is a static value of either “Microsoft” or “Third Party”.</li><li>**Active teams** is the number of teams who have opened the App by at least one member of the team and during the specified time periods.</li><li>**Publisher** is the software publisher of the app.</li><li>**Version** is the software version of the app, from the app publisher.</li></ul><b> Note :</b> Currently, 'Active users' and 'Active teams' are calculated for apps used in channels only.|
|**7**  |At the upper right, select the **?**, and then select **Edit columns** to add or remove columns in the table.|
|**8**  |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of Downloads page.](media/app-usage-report7.png "Screenshot of Downloads page.")|
|**9**   |When you view the report in Excel, you'll also see an **Id** column, which represents the app ID. A team ID is typically an alphanumeric string. If the **Id** column shows as **\n****, this means that a user requested their information to be deleted.<br><br>![Screenshot of the downloaded Excel report.](media/app-usage-report8.png "Screenshot of the downloaded Excel report.")|

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)