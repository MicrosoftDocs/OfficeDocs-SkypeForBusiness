---
title: Microsoft Teams EHR connector Virtual Visits report
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
searchScope:
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Healthcare
  - microsoftcloud-healthcare
  - m365solution-healthcare
  - m365solution-scenario
appliesto: 
  - Microsoft Teams
ms.reviewer: 
description: Learn how to use the Teams EHR connector Virtual Visits report in the Microsoft Teams admin center to get an overview of EHR-integrated virtual appointment usage in your organization. 
---

# Microsoft Teams EHR connector Virtual Visits report

The Microsoft Teams Electronic Health Record (EHR) connector Virtual Visits report in the Microsoft Teams admin center gives you a quick and easy way to view Teams EHR-integrated virtual appointment usage in your organization.

To view the report, you must be a global admin or a Teams admin.

## View the report

There are two ways to access and view the report in the Teams admin center.

- Through the [EHR connector usage card](#the-ehr-connector-usage-card) in the dashboard
- Directly by choosing [**EHR connector Virtual Visits**](#the-teams-ehr-connector-virtual-visits-report) in **Analytics & reports** > **Usage reports**

### The EHR connector usage card

In the left navigation of the Microsoft Teams admin center, choose **Dashboard**. and then go to the **EHR connector usage** card.

Here, you get an at-a-glance view of EHR-integrated virtual appointment activity by month, including completed appointments, remaining allocation, and whether you've exceeded the monthly limit (depending on the license you have).

:::image type="content" source="../../media/ehr-connector-report-card.png" alt-text="Screenshot of the EHR connector usage card in the Teams admin center dashboard" lightbox="../../media/admin-connector-report.png":::

:::image type="content" source="../../media/ehr-connector-report-card.png" alt-text="Screenshot of the EHR connector usage card in the Teams admin center dashboard" lightbox="../../media/ehr-connector-report-card.png":::

Choose **View details** to see report details. To purchase more licenses, choose **Buy more**.

### The Teams EHR connector Virtual Visits report

1. In the left navigation of the Teams admin center, go to **Analytics & reports** > **Usage reports**.
1. On the **View reports** tab, choose **EHR connector virtual visits** and a date range. Then, select **Run report**.

    :::image type="content" source="../../media/ehr-connector-report.png" alt-text="Screenshot of the Teams EHR connector Virtual Visits report in the Teams admin center" lightbox="../../media/ehr-connector-report.png":::

#### Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48-hour latency from time of activity. |
|**2**   |The table gives you detailed information about each appointment that took place during the selected date range. <ul><li>**Start time (UTC)** is the date and time when both a staff member and participant are in the appointment or when the first activity happened in the appointment.  </li> <li>**Duration** is the time difference between the start time and when the last person leaves the meeting. If both a staff member and a participant didn’t join the meeting, duration shows as 0 (zero).</li> <li>**Name** shows the ??. <li>**Email** is the email address of.</li> <li> **Department** is the department ID that's associated with the integration record in the EHR system. If the information isn't displayed correctly, complete the integration or update the integration record in your EHR system.</li></li> <li>**Attendees** is the total number of staff members and participants in the appointment.</li> <li>**Within limit** indicates whether the appointment is within the allocation limit. </li> </ul> |
|**3**   |Select **Edit columns** to add or remove columns in the table. |
|**4**   |You can export the report to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, choose **Download** to download the report when it's ready. |

> [!NOTE]
> For more analytics on Teams EHR-integrated virtual appointments, see [Virtual Visits usage report](../../teams-analytics-and-reports/virtual-visits-usage-report.md). With this report, you can view key metrics such as total appointments, lobby wait time, appointment duration, and no shows. Use this information to gain insight into usage trends to help you optimize virtual appointments to deliver better business outcomes.

## Related articles

- [Virtual appointments with Teams - Integration into Cerner EHR](ehr-admin-cerner.md)
- [Virtual appointments with Teams - Integration into Epic EHR](ehr-admin.md)
