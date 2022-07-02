---
title: Multi-tenant auditing
author: donnah007
ms.author: v-donnahill
manager: serdars
ms.reviewer: dstrome 
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Audit logging for TRM.
f1keywords: 
---


# Audit logging in the Teams Rooms Managed service

Audit in Teams Rooms Managed (TRM) service lets you search for audit records for activities performed in the portal by users and admins. This feature is enabled by default. Only the Managed Service Administrator has permission to export and then view the logs.

> [!NOTE]
> Actions performed in the TRM service are not logged in Microsoft 365 or Office 365 auditing 

## Exporting logs

When you export all results for an audit log search, the raw data from the unified audit log is copied to a comma-separated value (CSV) file that is downloaded to your local computer. 

**To download logs** 

1. Go to **Settings > General > Audit Logs**.
1. To define the date range for logs of interest, enter the **Start date** and **End date.**

   > [!NOTE]
   > Logs are only available for up to 180 days.

1. Select **Download logs.**

   ![Audit log date range](../media/multi-tenant-auditing.png)

   A message displayed at the bottom of the window prompts you to open or save the CSV file. 

1. Select **Save** > **Save as**, and save the CSV file to your local computer. 

1. It takes a while to download many search results when searching for all activities, or on a broad date range. When the CSV file is finished downloading, a message at the bottom of the window is displayed.

## Detailed properties in the audit log

The following table describes the properties that are included in the CSV.

|Property|Description|
| - | - |
|activity.category|<p>The category of the object on which the was action performed. Possible values:</p><p>**User, Assignment, PartnerInvitation, Role**</p>|
|activity.objectName|The name of the object that was modified.|
|activity.operation|The type of operation performed. Possible values are: **Create, Update, Delete** |
|activity.resultStatus|<p>Indicates whether the action (specified in the **activity.operation** property) was successful or not.</p><p>The value is either **Successful** or **Failed**.</p>|
|activity.tenantId|The GUID of the tenant on which the action was performed|
|creationTime|The date and time in Coordinated Universal Time (UTC) in the ISO format when the user performed the activity.|
|user.userId|The user who performed the action that resulted in the record being logged.|
|user.userTenantId|The GUID of the tenant for the user who performed the action|


