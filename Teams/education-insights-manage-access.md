---
title: Manage user access to Education Insights
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: karsmith
description: Manage user access to Education Insights in Microsoft Teams.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Manage user access to Education Insights

This document provides the steps required to manage user access to [Education Insights in Microsoft Teams](class-insights.md).

You need to provide permissions for education leaders, district leaders, school principals, head teachers, counselors, heads of learning areas, program directors, social workers, and psychologists. Educators are *automatically* given permission when they own a class team.

To provide organization-level Insights, you must [import data from the Student Information System (SIS)](education-insights-sis-data-sync.md) so that Insights has the hierarchical structure of the educational system mapped correctly.

> [!NOTE]
> Only Global Administrator can manage user access to Insights.

> [!TIP]
> We recommend that you enable Insights for all your education leaders so that they have the data to understand each school, and the ability to quickly identify problems and provide support to their educators. Even if you're running a pilot, it may still be helpful to keep Insights enabled for all education leaders, but only target communications to the pilot group of users.



## Grant permissions

* Open the Insights app, click **Settings**, and select **User permissions**

:::image type="content" source="media/insights-user-permissions.png" alt-text="Settings":::

* Select **Add users**.
* Enter the username or email address of each user.
* Select the permission level:
  * **Access to all organization** means the user sees all the org units at all levels.
  * **Access to specific schools** means the user sees the selected schools. Start typing and select the school from the list. You can add multiple schools together.
* Click **Add new users**.

:::image type="content" source="media/insights-add-users.png" alt-text="Grant permissions":::

> [!NOTE]
> Only provide permission to those education leaders that need them and only to the organizational units they are responsible for. If you are unsure whether user permission for a specific organization is required, consult your institution's privacy subject matter experts, such as legal or HR personnel.

## Edit permissions
* Select specific user, then select **Edit permissions**.
* Update the permission level or schools list, and click **Update permissions**.

:::image type="content" source="media/insights-edit-users.png" alt-text="Edit permissions":::

## Remove permissions
* Select the users you want to remove, then select **Remove users**.
* These users no longer have access to organization-level Insights, but can still access class-level Insights if they own a class team.

:::image type="content" source="media/insights-remove-users.png" alt-text="Remove permissions":::
