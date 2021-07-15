---
title: Use administrative unit functionality in Microsoft Teams
author: cichur
ms.author: v-cichur
ms.reviewer: aaglick
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to use administrative unit functionality in Microsoft Teams
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Administrative unit functionality for device management in Teams

Using the Microsoft Teams admin center, you can have more granular role-based access for device management. We are implementing the Administrative Unit concept for device management through the admin center. With Administrative unit concept, you'll be able to ensure access to set of resources to a dedicated administrator, rather than providing access to all the resources. Learn about [administrative unit concept](https://docs.microsoft.com/en-us/azure/active-directory/roles/administrative-units).

Create administrative units in Azure Portal and assign admins for respective administrative units. Learn more about assigning administrative units at [manage admin units](/azure/active-directory/roles/admin-units-manage). You can extend the same functionality for Teams devices management. The administrative unit concept is available only for the Teams Device Administrator role currently.

When an administrative unit admin signs in, they can see only those user devices which are mapped to that particular administrative unit. An IT admin will be able to perform operations and manage only those set of devices.

If the same administrative unit admin is part of multiple administrative unit admins, they can switch between administrative units seamlessly without signing out from the portal. In the changed administrative unit view, they would be able to see only those set of devices which are associated with the new administrative unit.

  [!admin unit](media/admin-unit.png)