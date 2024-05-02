---
title: Manage meeting templates in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: janineco
ms.date: 12/11/2023
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
description: Learn how Microsoft Teams Administrators can specify which meeting templates are available to their users.
---

# Manage meeting templates in Microsoft Teams

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

You can use meeting template policies in Microsoft Teams to determine which meeting templates are available to users in your organization.

## Specify which meeting templates are available to users

By default, the **Global (Org-wide default)** meeting template policy allows users to see all available templates, including default templates and any custom templates that you've created. If you want to limit which templates are available for different people or groups, you can create policies specifying this.

To create a meeting template policy

1. In the Teams admin center, expand **Meetings** and select **Meeting template policies**.
1. Select **Add**.
1. Type a name and description for the policy.
1. In the **Viewable templates** list, select any templates that you don't want users with this policy to see, and then select **Hide**.
1. Select **Save**.

Once you've created the policy, you need to assign it to users or groups. See [Assign policies to users and groups](assign-policies-users-and-groups.md) for more information.

## Change which meeting templates are visible to users

You can update a meeting template policy if you want to change which templates are available to the users with that policy.

To edit a meeting template policy

1. In the Teams admin center, expand **Meetings** and select **Meeting template policies**.
1. Select the policy you want to change, and then select **Edit**.
1. To make a viewable template hidden, select the template in the **Viewable templates** list and then select **Hide**.
1. To make a hidden template viewable, select the template in the **Hidden templates** list and then select **Show**.
1. Select **Save**.

## Related topics

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)
