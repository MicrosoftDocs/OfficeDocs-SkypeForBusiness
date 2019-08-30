---
title: Microsoft Teams PSTN usage report
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
description: Learn how to use the Teams PSTN usage report in the Microsoft Teams admin center to get an overview of calling and audio conferencing usage in your organization.
appliesto: 
- Microsoft Teams
---
# Microsoft Teams PSTN usage report

The Teams PSTN usage report in the Microsoft Teams admin center gives you an overview of PSTN calling and audio conferencing activity in your organization. You can see the number of minutes that users spent in inbound and outbound PSTN calls and the cost of these calls. Use this information to gain insight into calling and audio conferencing usage in your organization and help you to investigate, plan, and make business decisions.

## View the report

In the left navigation of the Microsoft Teams admin center, click **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **PSTN usage report**, and then click **Run report**.

![Screen shot of the PSTN usage report in the admin center](../media/teams-reports-teams-usage-with-callouts.png "Screen shot of the PSTN usage report in the Microsoft Teams admin center with numbered callouts")

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |The PSTN usage report can be viewed for trends over the last 7 days or 28 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |The table gives you a breakdown of PSTN usage per user. <ul><li>**Time stamp**</li><li>**Display name**</li><li>**Username**</li><li>**Phone number** is the number that received the call for inbound calls or the number dialed for outbound calls.</li><li>**Call type** is whether the call was a PSTN outbound or inbound call and the type of call such as a call placed by a user or an audio conference. The calls types you may see are:</li><li>**Called to**</li><li>**To country or region**</li><li>**Called from**</li><li>**From country or region**</li><li>**Charge** is the amount of money or cose of the call that's charged to your account. </li><li>**Currency** is the type of currency used to calculate the cost of the call. </li><li>**Duration** is how long the call was connected.</li><li>**Domestic/International** tells you whether the call was domestic (within a country/region) or international (outside a country/region) based on the user's location.</li><li>**Call ID**</li><li>**Number type** is the user's phone number type, such as a service of toll-free number. </li><li>**Country or region**</li> <li>**Conference ID** is the conference ID of the audio conference. </li><li>**Capability** is the license used for the call. The license types you may see are:</li></ul> |
|**4**   |Select **Edit columns** to add or remove columns in the table. |
|**5**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br>![Screen shot of the Downloads tab showing exported reports to download](../media/teams-reports-export-to-csv.png)|

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)