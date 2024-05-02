---
title: Allow users to search for private teams
ms.author: jtremper
author: jacktremper
manager: serdars
ms.reviewer: shubjain
ms.date: 11/01/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.custom: 
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to allow users to search for private teams.
---

# Allow users to search for private teams

By default, users can't search for and find private teams. You can allow users to find private teams by turning on **Private team discovery** in a Teams policy. Users for whom the policy is turned on can search for and find private teams and request to join them. Team owners can approve or deny the request.

## Manage private team discovery

You can allow or prevent private team discovery for users or groups in your organization by using a Teams policy.

To manage if users can search for private teams
1. In the Teams admin center, expand **Teams** and select **Teams policies**.
1. Select the policy that you want to update or create a new one.
1. On the **Teams policy** pane, set **Private teams discovery** to **On** or **Off**.

Policy changes may take several hours to take effect.

## Restrict private team discovery by using sensitivity labels

If you want to enable private team discovery but restrict the discovery of certain teams, such as those containing sensitive information, you can prevent private team discovery by using a sensitivity label. For more information, see [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](/purview/sensitivity-labels-teams-groups-sites#how-to-configure-groups-and-site-settings).

## Related topics

[Find and join a team in Microsoft Teams](https://support.microsoft.com/office/9f284981-39a1-486d-b43d-ab2dcc4c1e0f)
