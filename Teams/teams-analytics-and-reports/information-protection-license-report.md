---
title: Microsoft Teams information protection license report
author: anandab-msft
ms.author: anandab
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: 
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: 
ms.collection: 
  - M365-collaboration
description: Learn how to use the Teams Information protection license report in the Microsoft Teams admin center to see how apps in your organization are using change notification events subscription APIs.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams information protection license report


Teams information protection license report gives API usage insight of [Microsoft Graph API which has license and payment requirements](https://docs.microsoft.com/en-us/graph/teams-licenses). This report higlights all the app which are using these API in [model A](https://docs.microsoft.com/en-us/graph/teams-licenses#modela-requirements), it does not show usage when API is used in model is [model B](https://docs.microsoft.com/en-us/graph/teams-licenses#modelb-requirements) or [evaluation mode](https://docs.microsoft.com/en-us/graph/teams-licenses#evaluation-mode-default-requirements). 


## View the information protection license report

You must be a Teams service admin to make these changes. See [Use Teams administrator roles to manage Teams](../using-admin-roles.md) to read about getting admin roles and permissions.

1. In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Information Protection License**.
2. Under **Date range**, select a range.
3. Under **Apps**, select an app and then select **Run report**.

    ![Screenshot of the Teams information protection license report in the Teams admin center with callouts.](../media/teams-info-protection-license-report-chart-with-callouts.png "Screenshot of the Teams information protection license report in the Teams admin center with callouts")
    
    ![Screenshot of the Teams information protection license report in the Teams admin center with callouts.](../media/teams-info-protection-license-report-change-notification-with-callouts.png "Screenshot of the Teams information protection license report in the Teams admin center with callouts")
    
    ![Screenshot of the Teams information protection license report in the Teams admin center with callouts.](../media/teams-info-protection-license-report-patch-api-tab-with-callouts.png "Screenshot of the Teams information protection license report in the Teams admin center with callouts")
    
    ![Screenshot of the Teams information protection license report in the Teams admin center with callouts.](../media/teams-info-protection-license-report-chat-export-api-tab-with-callouts.png "Screenshot of the Teams information protection license report in the Teams admin center with callouts")
    
    ![Screenshot of the Teams information protection license report in the Teams admin center with callouts.](../media/teams-info-protection-license-report-team-export-api-tab-with-callouts.png "Screenshot of the Teams information protection license report in the Teams admin center with callouts")


    

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |The information protection license report can be viewed for trends over the last 3 months. |
|**2**   |App name will display a list of all apps that have used [Microsoft Graph API which has license and payment requirements](https://docs.microsoft.com/en-us/graph/teams-licenses) during the selected time period.|
|**3**   |No of user who has valid [license](https://docs.microsoft.com/en-us/graph/teams-licenses#required-licenses-for-modela).  |
|**4**   |No. of users who does not have any valid [license](https://docs.microsoft.com/en-us/graph/teams-licenses#required-licenses-for-modela).  |
|**5**   |Total API call volume allowed to an app beyond which a consumption fee per API call will be charged to app. |
|**6**   |Total API call volume used by app for the given date range. |
|**7**   |Select any particular label to show  or hide it in chart. |
|**8**   |Each tab displays usage of a particualar set of APIs namely [change notification](/graph/api/resources/webhooks?view=graph-rest-1.0), [export API](/microsoftteams/export-teams-content), [update message API](/graph/api/message-update). Select a tab to view usage details of that API. |
|**9**   |(Change Notification API) - Display name of user against which a change notification was trigerred. |
|**10**   |(Change Notification API) - Whether the given user has required license to succesfully send change notification to the app |
|**11**   |(Change Notification API) - Total change notification that was trigerred because of this user.|
|**12**   |(Change Notification API) - Total change notification that was sent to the app, this will less than total change notification trigerred if user doesnot have valid license.|
|**13**|(Patch API) - Display name of user Where an attempt to update the message was done. |
|**14**|(Patch API) - Whether the given user has required license to for the message to get succssfully updated. |
|**15**|(Patch API) - Total attempts to update messages.|
|**16**|(Patch API) - Total message that was successfully updated.|
|**17**|(Chat Export API) - Display name of user where an attempt to export user's chat message was done. |
|**18**|(Chat Export API) - Whether the given user has required license to for the message to get succssfully exported. |
|**19**|(Chat Export API) - Total attempts to export chat messages.|
|**20**|(Chat Export API) - Total attempts where chat message was successfully exported.|
|**21**|(Team Export API) - Display name of team where an attempt to export that team's message was done. |
|**22**|(Team Export API) - Total attempts to eport team messages.|
|**23**|(Team Export API) - Total attempts where team message was successfully exported.|


## Make the user-specific data anonymous

To make the data in the Teams user activity report anonymous, you have to be a global administrator. This will hide identifiable information such as display name, email, and Azure AD ID in reports and their exports.

1. In the Microsoft 365 admin center, go to **Settings** \> **Org Settings**, and under the **Services** tab, choose **Reports**.
    
2. Select **Reports**, and then choose to **Display anonymous identifiers**. This setting gets applied both to the usage reports in the Microsoft 365 admin center and the Teams admin center.
  
3. Select **Save changes**.
