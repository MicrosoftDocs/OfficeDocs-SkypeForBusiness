---
title: Microsoft Teams PSTN blocked users report
author: CarolynRowe
ms.author: crowe
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 06/24/2019
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
search.appverid: MET150
description: Use the PSTN blocked users report in Microsoft Teams admin center to get an overview of your organization's Teams users that are blocked from making PSTN calls.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
---
# Microsoft Teams PSTN blocked users report

The PSTN blocked users report in the Microsoft Teams admin center shows you the users in your organization who are blocked from making PSTN calls in Teams. You can view more information about each blocked user, including their assigned phone number and the reason they were blocked from making calls.

## View the PSTN blocked users report

In the left navigation of the Microsoft Teams admin center, click **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **PSTN blocked users**, and then click **Run report**.

![Screenshot of the PSTN blocked users report report in the admin center.](../media/teams-reports-pstn-blocked-users-with-callouts.png "Screenshot of the PSTN blocked users report in the Microsoft Teams admin center with numbered callouts")

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when it was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**2**   |The X axis is the date. The Y axis is the number of users. <br>Hover over the dot on a given date to see the number of users blocked on that date. |
|**3**   |The table gives a breakdown of all users who are blocked from making PSTN calls.  It shows all users who have Phone System or Audio Conferencing assigned and gives you more information about each user. <ul><li>**Display name** is the display name of the user. You can click the display name to go to the user's setting page in the Microsoft Teams admin center. </li> <li>**Phone** is the number that's assigned to the user.</li> <li>**Blocked reason** is the reason the user is blocked from making calls.</li><li>**Blocked action**  tells you whether the user is blocked or unblocked from making PSTN calls in Teams.</li> <li>**Blocked time** is the date and time (UTC) that the user was blocked from making calls.</li></li> </ul>To see the information that you want in the table, make sure to add the columns to the table. |
|**4**   |Select **Edit columns** to add or remove columns in the table.|
|**5**   |Select **Full screen** to view the report in full screen mode.|

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
