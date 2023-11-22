---
title: Microsoft Teams app usage report
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: vapati
ms.date: 09/27/2022
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to use the Teams app usage report in Teams admin center to know the active teams and users of an app.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams app usage report

The Teams app usage report in the Microsoft Teams admin center provides you with insights about which apps users are using in Teams. You can gain insights into the apps activity in your organization for different microsoft (Viva learning, Shifts etc.), third-party (Polly, Trello etc.) & Line of Business (LOB) Teams apps.   

You can use this report to understand where exactly different apps are getting used and deep dive into per-app utilization data.

The data represented in this report provide answers to the following questions:

-  How many installed apps do users in your environment have?
-  How many apps have at least one active user in your environment based on type (Microsoft, third-party, and LOB)?
-  How many apps are being used per platform (Windows, Mac, web, or mobile)?
-  How many active users and active teams are using an app?

> [!NOTE]
> Usage for **Side loaded** LOB apps is not included in this report.

This article explains how to access the report and view and interpret the various metrics within the report. 

## View the app usage report

You must be either a global admin, global reader, or Teams service admin to view the reports in the Microsoft Teams admin center. See [Use Teams administrator roles to manage Teams](../using-admin-roles.md) to read about getting admin roles and permissions.

1. In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Apps usage**.

2. Under **Date range**, select a range and then select **Run report**.

:::image type="content" alt-text="Screenshot of the Teams app usage report in the Teams admin center with callouts." source="media/app-usage2-report10.png" lightbox="media/app-usage2-report10.png":::

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |The app usage report can be viewed for trends over the last 7, 30, 90, and 180 days. |
|**2**   |Each report has a date for when this report was generated. Reports usually reflect a 24-48 hour latency from the time an app was used. For example, data for January 10th should show up in the report by around January 12th. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of items.</li> </ul>Hover over the dot representing an item on a given date to see the number of instances of that item on that given date.|
|**4**   |You can filter what you see on the chart by selecting an item in the legend. For example, select **Active Microsoft apps**, **Total installed apps**, and more to see only the info related to each one. Changing this selection doesn’t change the information in the table. <ul><li>**Active Microsoft apps** is the number of Microsoft apps (for example, Viva learning) used across your organization. </li> <li>**Active third-party apps** is the number of third-party apps (for example, Polly) used across your organization.  </li> <li>**Active LOB apps** is the number of Line of Business apps used across your organization. </li><li>**Total active apps** is the total number of apps used across your organization. </li><li>**Total inactive apps** is the number of apps not used in your organization. </li><li>**Total installed apps** is the total number of apps installed within your organization. The start date for all install metrics is October 2021. Only apps installed after that date will be counted.</li></ul> The chart shows you aggregated metrics across the organization on each day within a selected period. For example, if you select January 28th and metric **Active third-party apps**, the chart will show you the total number of third-party apps used on January 28th within your organization.  |
|**5**   |The table gives you a breakdown of usage by each app. <ul><li>**App ID** is the external app identifier present in the app manifest. <br/>More information about the app can be found in the [Manage apps section in Teams admin center](/microsoftteams/manage-apps) by referring to it using this external App ID.</li> <li>**App name** is the name of this application as present in the app manifest. </li> <li>**Publisher** is the publisher of this application as present in the app manifest. This is only available for apps published to the global Store.</li> <li>**Teams using this app** is the number of distinct Teams teams that have at least one user using this app. </li><li>**Users using this app** is the number of distinct users in your organization that are using this app.</li> <li>**Used on Windows** indicates whether that app has been used on Windows by at least one user in your organization.</li><li>**Used on Mac** indicates whether that app has been used on MAC by at least one user in your organization.</li><li>**Used on Web** indicates whether that app has been used on the web by at least one user in your organization. </li> <li>**Last used date** is the date when that app was last used by anyone in your organization. </li></ul> |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |Export the report to a CSV file for offline analysis. Select the **Export to Excel** icon, and the report will be downloaded within your browser.|
|**8** |Time series data represented in the top graph show different usage metrics aggregated for the entire tenant.|
|**9** |Tabular data represented in the bottom half shows different usage metrics aggregated per team.|


## Managing apps in the Microsoft Teams admin center

For more information about how to manage your Teams apps, refer to [About apps in Microsoft Teams](../apps-in-teams.md).

To link an app in this report to the Manage Apps experience in the Microsoft Teams admin center, you can use the following:

- App Name
- External App ID

External App IDs are equivalent to the ID in the Manage apps page for Store apps. For LOB apps, the **External app ID**  column can be enabled in the [Manage apps section in Teams admin center](/microsoftteams/manage-apps) column settings. You can also view it on the app details page of a custom LOB app.

## Related articles

- [Teams analytics and reporting](teams-reporting-reference.md)
