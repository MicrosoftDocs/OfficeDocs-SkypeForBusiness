---
title: Manage devices by using administrative units
author: mahoffman
ms.author: v-mahoffman
ms.reviewer: prasad.ghlove
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to use administrative units in Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Manage devices by using administrative units

We've implemented the administrative unit concept for managing devices in the Teams admin center. This gives you more detailed, role-based access for managing devices. By using an administrative unit, you can ensure access to a set of resources and limit access to other resources  by a dedicated administrator. You can extend the same functionality for Teams devices management.

> [!NOTE]
> The administrative unit concept is currently available only for the Teams Device Administrator role.

As an example, Contoso has operations across different geographies. Alice is a Global IT admin in London, while Prashant is an IT admin for India. Today, when Prashant signs into the Teams admin center with the Device Administrator role, they get to see devices across the globe. Alice wants to restrict Prashant’s access only to those devices that are present in India. The administrative units concept helps solve this problem. Learn more [administrative unit concept](/azure/active-directory/roles/administrative-units).

![a diagram that shows scenarios.](media/au-diagram.png)

## Creation of administrative units

Create administrative units in Azure portal and assign admins for respective administrative units. Learn more about assigning administrative units at [manage admin units](/azure/active-directory/roles/admin-units-manage).

![an example company administrative units.](media/au-example.png)

Once created, Global IT admin can then add device users who correspond to that administrative unit.

![an example company with users preview.](media/au-example2.png)

The assignment of the role can be done through PowerShell using the [Add-AzureADMSScopedRoleMembership](/powershell/module/azuread/add-azureadmsscopedrolemembership?view=azureadps-2.0) cmdlet.

Once you've assigned roles to users for Administrative Units, users need to sign into Teams admin center to start managing scoped devices.

## Experience for Administrative Unit Admin

If the same admins are assigned responsibility of multiple administrative units, they can switch between administrative units without signing out from the portal. In the changed administrative unit view, they'll see only those set of devices that are associated with the new administrative unit.
