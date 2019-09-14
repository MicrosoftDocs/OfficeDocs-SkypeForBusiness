---
title: Microsoft Teams PSTN minute pools report
author: LanaChin    
ms.author: v-lanac
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: v-rifer
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

## View the report

In the left navigation of the Microsoft Teams admin center, click **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **PSTN minute pools**, and then click **Run report**.

![Screen shot of the Teams PSTN minute pools report in the admin center](../media/teams-reports-teams-usage-with-callouts.png "Screen shot of the Teams PSTN minute pools report in the Microsoft Teams admin center with numbered callouts")

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when this report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |The table gives you a breakdown of minute pools by license (capability) and usage location. <ul><li>**Country or region** ???</li><li>**Capability description** is the description of the license type used for the call.  The license types you may see in this report include: <ul><li>Domestic and international calling plan (1200 domestic minutes)</li><li>Domestic and international calling plan (3000 domestic minutes)</li><li>Domestic and international calling plan (600 international minutes)</li></ul></li><li>**Total minutes** is the total number of minutes available for the month.</li><li>**Minutes used*** is the number of minutes used each month</li> <li>**Minutes available** is the number of available minutes for the month.</li><li>**Capability** is the license used for the call. The licenses you may see in this report include:<ul><li>**MCOPSTNPP** - Communications Credits</li><li>**MCOPSTN1** - Domestic Calling Plan (3000 min US / 1200 min EU plans)</li><li>**MCOPSTN2** - International Calling Plan</li><li>**MCOPSTN5** - Domestic Calling Plan (120 min calling plan)</li><li>**MCOPSTN6** - Domestic Calling Plan (240 min calling plan)</li><li>**MCOMEETADD** - Audio Conferencing</li><li>**MCOMEETACPEA** - Pay Per Minute Audio Conferencing</li></ul></li> </ul> |
|**4**   |Click to drag a column to create a view that groups all data into one or more columns|
|**5**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br>![Screen shot of the Downloads tab showing exported reports to download](../media/teams-reports-export-to-csv.png)|

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)

