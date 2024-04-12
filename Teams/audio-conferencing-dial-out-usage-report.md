---
title: Audio Conferencing dial-out usage report
ms.author: jtremper
author: jacktremper
manager: pamgreen
ms.reviewer: 
ms.date: 11/16/2023
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
  - m365initiative-meetings
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
audience: Admin
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
  - CSH
ms.custom:
  - Audio Conferencing
  - LIL_Placement
description: "Learn which countries/regions have dial-in conferencing numbers, and how they're automatically assigned."
---

# Audio Conferencing dial-out usage report

The Audio Conferencing dial-out usage report in the Teams admin center gives you an overview of usage and dollars spent for the audio conferencing dial-out service. This report allows admins to consume user-level data in terms of communication credits spent and dial-out minutes used. It will help admins determine the future communication credits needed going forward from any point in time.

## View the Audio Conferencing dial-out usage report

In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** \> **Usage reports**. On the **View reports** tab, under **Report**, select the **Audio Conferencing dial-out usage report**.

Under **Date range**, you can select a predefined range of 7 or 28 days, or set a custom range.

Under **Country Previsioned**, select a preferred country/region, or select all, and then select **Run report**.

## Report details

The Audio Conferencing dial-out usage report has three main tabs that display information in a chart format based on the range selected in the dropdowns above it:

- The **Cost** tab shows the communication credits spent over the selected period and the table provides user level detail.
- The **Call duration** tab shows the total dial-out minutes over the selected period and the table provides user level detail.
- The **Dial-out calls** tab shows the total number of dial-out calls over the selected period and the table provides user level detail.

Each report has a date for when it was generated. The reports usually reflect a 24 to 48 hour latency from the activity time.

> [!NOTE]
> All dial-out minutes/calls/credit spent will be counted under the meeting organizer. It's not necessarily the same person who dialed out.

### Cost tab

The top of this tab section has a chart that displays a line  showing cost information over the date range and for the country/region or countries/regions selected.

There's a **Cost** section underneath the chart showing a price, which is the total cost per minutes of calls within the select time range.

### Call duration tab

The top of this tab section has a chart that displays a line that showing call duration over the date range and for the country/region or countries/regions selected.

There's a **Call duration** section underneath the chart showing the total minutes of calls used within the select time range.

### Dial-out calls

The top of this tab section has a chart that displays a line  showing dial-out calls over the date range and for the country/region or countries/regions selected.

There's a **Dial-out calls** section underneath the chart showing the total number of dial-out calls within the select time range.

## Using the report

The bottom of the page has a table, which shows user level breakdowns with the following headings:

- Meeting organizer
- Username
- Total minutes
- Credit spent
- Currency
- Country or region provisioned

If you need to search for usage for a specific user, there's a search bar on the right above the report. The meeting organizer names are all selectable hyperlinks that take you to a more detailed usage report for the user. This user view has the same three tabs as the main report, however the chart at the top of the page shows details for that specific user.

You can export any report shown in this table to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, select **Download** to download the report when it's ready.
