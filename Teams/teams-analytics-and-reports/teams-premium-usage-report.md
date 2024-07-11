---
title: Teams Premium feature usage report  
author: wlibebe
ms.author: wlibebe
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: vapati
ms.date: 7/11/2024
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
description: Learn how to use the Teams Premium usage report in the Teams admin center to know how often users are using each  Teams Premium feature.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Teams Premium feature usage report

[!INCLUDE[Teams Premium ECM](../includes/teams-premium-ecm.md)]

The Teams Premium feature usage report in the Microsoft Teams admin center allows you, as an admin, to view aggregated usage of Teams Premium features by users in your org.

From this report, you can:  

- Understand how individual users are benefiting from Teams premium features.

- Understand how organization is getting benefitted from specific Teams features and encourage their use in their org.

- Validate and understand overall value around Teams premium.

The report provides the following metrics:  

- Reached users across organization:  Count of users who attended meetings/events where a given Teams premium feature was used.

- Count of meetings across organization: Count of meetings where a given Teams premium feature is experienced by users.

- Count of meetings for each user: Count of meetings where a user (reached) who attended a meeting where given Teams premium feature was used.

- You can use this report to understand where exactly different apps are getting used and deep dive into per-app utilization data.

> [!NOTE]
> This feature isn’t available for gov clouds (GCC, GCC-H and DoD).

## View the app usage report

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. To learn more, see [Best practices for Microsoft Entra roles](/entra/identity/role-based-access-control/best-practices).

You must be either a global admin, global reader, or Teams service admin to view the reports in the Microsoft Teams admin center. See [Use Teams administrator roles to manage Teams](../using-admin-roles.md) to read about getting admin roles and permissions.

1. In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Teams premium feature usage**.

2. Under **Date range**, select a range and then select **Run report**.

:::image type="content" alt-text="Screenshot of the Teams app usage report in the Teams admin center with callouts." source="media/app-usage2-report10.png" lightbox="media/app-usage2-report10.png":::

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |You can view the Teams Premium feature usage report for trends over the last 7, 30, 90, and 180 days. |
|**2**   |Each report has a date for when this report was generated. Reports usually reflect a 24-48 hour latency from the time an app was used. For example, data for January 10th should show up in the report by around January 12th. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of items.</li> </ul>Hover over each data point on the graph to see the different metrics details on that given date.|
|**4**   |The chart represents different usage metrics across the entire organization. You can filter what you see on the chart by selecting an item in the legend. For example, select **Total reached users**, **Total meetings**, and more to see only the info related to each one. Changing this selection doesn’t change the information in the table. The following is detailed list of metrics available across different tabs: <ul><li>**Total usage**:  This tab covers usage metrics for all Teams Premium features across your tenant.  </li> <ul> <li>**Total reached users:** Count of users who had meetings/events where Teams premium feature was used. </li> <li>**Total meetings:** Count of meetings/events for users where Teams premium feature was used.  </li> </ul> <li>**Intelligent collaboration**: THIS TAB XYZ</li> <ul> <li>**Intelligent recap (Reached users):**  Count of meetings/events for users where Teams premium feature was used.  </li> <li>**Intelligent recap (Total meetings):** Count of meetings where intelligent meeting recap was viewed by users in a recent Teams client version released after 4th June 2024. Meeting count where intelligent recap is used by user is only counted if users updated their Teams client to a version release after 4th June 2024. If usage isn’t reflected for some users, you should update those users’ Teams client to the latest Teams client version. To learn more, see [Version update history for the new and classic Microsoft Teams app](/officeupdates/teams-app-versioning). </li> </ul><li>**Active LOB apps** is the number of Line of Business apps used across your organization. </li><li>**Total active apps** is the total number of apps used across your organization. </li><li>**Total inactive apps** is the number of apps not used in your organization. </li><li>**Total installed apps** is the total number of apps installed within your organization. The start date for all install metrics is October 2021. Only apps installed after that date will be counted.</li></ul> The chart shows you aggregated metrics across the organization on each day within a selected period. For example, if you select January 28th and metric **Active third-party apps**, the chart will show you the total number of third-party apps used on January 28th within your organization.  |
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