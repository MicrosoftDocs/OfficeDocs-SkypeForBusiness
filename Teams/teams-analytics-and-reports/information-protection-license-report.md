---
title: Microsoft Teams information protection license report
author: 
ms.author: anandab-msft
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: 
f1.keywords:
- NOCSH
localization_priority: Normal
search.appverid: 
ms.collection: 
  - M365-collaboration
description: Learn how to use the Teams Information protection license report in the Microsoft Teams admin center to see how apps in your organization are using change notification events subscription APIs.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams information protection license report

The Teams information protection license report gives insight into apps that have [subscribed](/graph/api/resources/subscription?view=graph-rest-1.0) to [change notification](/graph/api/resources/webhooks?view=graph-rest-1.0) events to listen to created, updated, or deleted messages at tenant level (that is, /teams/getAllMessage or /chats/getAllMessages). A change notification corresponding to the message is sent successfully only when the user has the [required license](/graph/teams-licenses).  You can see how many change notifications was triggered by a given user.


## View the information protection license report

You must be a Teams service admin to make these changes. See [Use Teams administrator roles to manage Teams](../using-admin-roles.md) to read about getting admin roles and permissions.

1. In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Information Protection License**.
2. Under **Date range**, select a range.
3. Under **Apps**, select an app and then select **Run report**.

    ![Screenshot of the Teams information protection license report in the Teams admin center with callouts](../media/teams-info-protection-license-report-with-callouts.png "Screenshot of the Teams information protection license report in the Teams admin center with callouts")

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |The information protection license report can be viewed for trends over the last 7 days, 30, or 90 days. |
|**2**   |App name will display a list of all apps that have subscribed to change notification events of messages in the last n days as selected in the date range. |
|**3**   |The table gives you a breakdown of usage per user for the selected app.<ul><li>**Display name** is the display name of the user. Select the display name to go to the user's details page in the Microsoft Teams admin center.</li><li>**Has Required License** is yes if the user has one of the required licenses as defined (here)[https://docs.microsoft.com/en-us/graph/teams-licenses]. If the user does not have the required license, the _Assign license_ link is displayed which navigated to the user's license detail page in the Microsoft admin center (**Users** > **Active Users** > select username).</li><li>**License Protected Events** is the number of unique change notification events sent to the app against a message which was created, updated or deleted by that user.</li></ul> |
|**4**   |Export the report to a CSV file for offline analysis. Select **Export to Excel**, and then the **Downloads** tab. Select **Download** to download the report when it's ready. |
|**5**   |Export the report to a CSV file for offline analysis. Select **Export to Excel**, and then the **Downloads** tab. Select **Download** to download the report when it's ready. When you view the report in Excel, you'll also see an **Id** and **email** column, which represents the User ID and email address of the user. |

## Make the user-specific data anonymous

To make the data in the Teams user activity report anonymous, you have to be a global administrator. This will hide identifiable information such as display name, email, and Azure AD ID in reports and their exports.

1. In the Microsoft 365 admin center, go to **Settings** \> **Org Settings**, and under the **Services** tab, choose **Reports**.
    
2. Select **Reports**, and then choose to **Display anonymous identifiers**. This setting gets applied both to the usage reports in the Microsoft 365 admin center and the Teams admin center.
  
3. Select **Save changes**.
