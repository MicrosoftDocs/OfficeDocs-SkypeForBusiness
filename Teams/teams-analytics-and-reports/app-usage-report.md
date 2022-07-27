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
ms.localizationpriority: high
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

1. In the left navigation of the admin center at <https://admin.teams.microsoft.com>, click **Analytics & reports** > **Usage reports**.<br><br>![Screenshot of the Usage Reports menu item.](media/app-usage-report1.png "Screenshot of the Usage Reports menu item.")
2. On the **View reports** tab, under **Report**, select **Apps Usage**.

3. Under **Date range**, select a range, and then click **Run report**. The Teams Apps usage report can be viewed for trends over the last 7, 30 or 90 days.<br><br>![Screenshot of the Apps Usage report.](media/app-usage-report2.png "Screenshot of the Apps Usage report.")


## Interpret the report

:::image type="content" alt-text="Screenshot of the Teams app usage report in the Teams admin center with callouts." source="media/app-usage-report5.png" lightbox="media/app-usage-report5.png":::

Each report has a date at the upper left that shows when the report was created. Reports usually reflect a 24-hour latency from the time an app was opened.

The Y axis on the chart is the number of users who for the date you selected by hovering over the chart are considered active users because they have opened an app at least once.

The X axis on the chart is the date range that you selected for the report.

Hover over the dot (4) representing an app's usage on any date to see the total number of that app’s active users on that date.

To select other apps, at the upper right, click the **Filter** icon (5), select or type new criteria, and then click **Apply**.

The table at the bottom of the report (6) shows active users and teams by app name.

   - **App name** is the display name of the app used in Teams.
   - **Active users** is the number of users who opened the app at least once during the specified time period.
   - **App type** is a static value of either “Microsoft” or “Third Party”.
   - **Active teams** is the number of teams who have opened the app by at least one member of the team and during the specified time periods.
   - **Publisher** is the software publisher of the app.
   - **Version** is the software version of the app, from the app publisher.

   > [!NOTE]
   > **Active users** and **Active teams** are calculated for apps used in channels only.

To add or remove columns in the table, at the upper right, click the **Edit columns** icon (7), on the **Edit columns** tab, select new criteria, and then click **Apply**.

To export the report to a CSV file for offline analysis, at the upper right, select the **Export to Excel** icon (8), and then on the **Downloads** tab under **Status**, click **Download**.

   :::image type="content" alt-text="Screenshot of Downloads pane." source="media/app-usage-report7.png" lightbox="media/app-usage-report7.png":::

When you view the report in Excel, you'll also see an **Id** column, which represents the app ID, typically an alphanumeric string. If the **Id** is **\n**, this means that a user asked that their information be deleted.

   ![Screenshot of the downloaded Excel report.](media/app-usage-report8.png "Screenshot of the downloaded Excel report.")

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
