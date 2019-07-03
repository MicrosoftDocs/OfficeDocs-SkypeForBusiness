---
title: Microsoft Teams PSTN minute pools report
author: LanaChin    
ms.author: v-lanac
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: svemu
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
description: Learn how to use the Teams PSTN minute pools report in the Microsoft Teams admin center to see the number of minutes consumed during the current month within your organization.
appliesto: 
- Microsoft Teams
---
# Microsoft Teams PSTN minute pools report

The Teams PSTN minute pools report in the Microsoft Teams admin center gives you an overview of audio conferencing and calling activity in your organization by showing you the number of minutes consumed during the current month. You can see a breakdown of activity including the license used for calls, total minutes available, used minutes, and license usage by location.

![Screen shot of the Teams PSTN minute pools report in the admin center](../media/teams-reports-teams-usage.png "Screen shot of the Teams PSTN minute pools report in the Microsoft Teams admin center")

## View the report

Go to the Microsoft Teams admin center, in the left navigation, click **Analytics & reports**, and then under **Report**, select **PSTN minute pools**.

## Interpret the report

![Screen shot of the Teams PSTN minute pools report in the admin center](../media/teams-reports-teams-usage-with-callouts.png "Screen shot of the Teams PSTN minute pools report in the Microsoft Teams admin center with numbered callouts")

|Callout |Description  |
|--------|-------------|
|**1**   |The Teams minute pools report can be viewed for trends over the last 7 days or 28 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |The table gives you a breakdown of minute pools by license (capability) and usage location. <ul><li>**Capability**  is the license/service plan used for the call. The license/service plans you may see in this report include: <ul></ul><li>MCOPSTN1 - Domestic Calling Plan (3000-minute US/1200-minute EU plans</li><li>MCOPSTN2 - Domestic & International Calling Plan from which you will see a domestic pool (3000-minute US/Canada/PR, 1200-minute European countries) and an international pool (600-minutes). Minute cap is reached whenever the domestic -OR- international cap is reached within the calendar month.</li><li>MCOPSTN5 - Domestic Calling Plan (120-minute calling plan.)</li><li>MCOPSTN6 - Domestic Calling Plan (240-minute calling plan)</li><li>MCOMEETADD - Audio Conferencing</li></li> <li>**Capability Description** is a description of the license type used for the call.</li> <li>**Country Minute Pool** is the license usage location of the user(s) who share the minute pool.</li><li>**Used Minutes** is the number of minutes used each month</li> <li>**Total Minutes** is the total number of minutes available for the month.</li><li>**Percent Used** is the percent of minutes used for the month.</li></li> </ul> |
|**4**   |Click to drag a column to create a view that groups all data into one or more columns|
|**5**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br>![Screen shot of the Downloads tab showing exported reports to download](../media/teams-reports-export-to-csv.png)|

## Related topics
- [Teams analytics and reporting](teams-reporting-reference.md)

