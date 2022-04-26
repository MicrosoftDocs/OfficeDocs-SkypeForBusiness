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
description: Learn how to use the EHR connector Virtual Visits report in the Microsoft Teams admin center to get an overview of EHR-integrated virtual appointment activity in your organization. 
---

# Microsoft Teams EHR connector Virtual Visits report

The Microsoft Teams Electronic Health Record (EHR) connector Virtual Visits report in the Microsoft Teams admin center gives you a quick and easy way to view Teams EHR-integrated virtual appointment activity in your organization.

To view the report, you must be a global admin or a Teams admin. 

## View the report

## The EHR connector usage card

In the left navigation of the Microsoft Teams admin center, choose **Dashboard**. and then go to the **EHR connector usage** card. Here, you get an at-a-glance view of EHR-integrated virtual appointment activity by month, including completed appointments, remaining allocation, and whether you've exceeded the monthly limit (depending on the license you have).

 ![Screenshot of the EHR connector usage card in the Teams admin center dashboard](../../media/admin-connector-report.png)

Choose **View details** to see a detailed report. To purchase more licenses, choose **Buy more**.

## The Teams EHR connector Virtual Visits report

To view the report, you can do one of the following:

- Choose **View details** in the **EHR connector usage** card in the Teams admin center dashboard. Then, choose a date range and select **Run report**.
- In the left navigation of the Teams admin center, go to **Analytics & reports** > **Usage reports**. On the **View reports** tab, choose **EHR connector virtual visits** usage and a date range. Then, select **Run report**.

The table gives you more information about each Teams EHR-integrated virtual appointment that took place during the selected date range.

|Column  |Description  |
|---------|---------|
|Start time (UTC)  | The date and time when both a staff member and participant are in the appointment or when the first activity happened in the appointment.      |
|Duration    | The time difference between the start time and when the last person leaves the appointment. If both a staff member and a participant didn’t join the appointment, duration shows as 0 (zero).        |
|Name     | ??        |
|Email    | Email address of ??       |
|Department    | The department ID that's associated with the integration record in the EHR system.        |
|Attendees    | The total number of staff members and participants in the appointment.        |
|Visit within limit  | Whether the appointment is within the allocation limit.      |

> [!NOTE]
> For more detailed analytics on Teams EHR-integrated virtual appointments, see [Virtual Visits usage report](../../teams-analytics-and-reports/virtual-visits-usage-report.md). You can view key metrics such as lobby wait time, appointment duration, and no shows. Use this information to gain insight into usage trends to help you optimize virtual appointments to deliver better business outcomes.

## 

## Related articles

- [Virtual appointments with Teams - Integration into Cerner EHR](ehr-admin-cerner.md)
- [Virtual appointments with Teams - Integration into Epic EHR](ehr-admin.md)
