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

# Use administrative units to manage devices

We've implemented administrative units in the Teams admin center, which gives you more detailed, role-based access for managing Teams devices. By using an administrative unit, you can give a Teams admin access to specific resources but limit that admin's access to other resources. This is especially helpful if you have local Teams admins in different countries or regions.

For example, Contoso has operations around the globe. Alice is a global IT admin based in London, while Prashant is a local IT admin based in Bangalore, India. Today, when Prashant signs into the Teams admin center as a device administrator, he can see Teams devices around the globe. Alice wants to limit Prashant's access to Teams devices only in Bangalore. Administrative units let her do this. To learn more, see [Administrative units in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/roles/administrative-units).

> [!NOTE]
> Administrative units are currently available in the Teams admin center only for the Teams devices administrator role.

## Add administrative units

If you're a global admin, you can add administrative units. To learn how, see [Add an administrative unit](https://docs.microsoft.com/en-us/azure/active-directory/roles/admin-units-manage#add-an-administrative-unit).

## Assign admins to administrative units

If you're a global admin, you can use the Azure portal, PowerShell, or the Microsoft Graph API to assign admins to an administrative unit. 

- **Use the Azure portal to assign admins to an administrative uni**. As a global admin, you can use the Azure portal to assign admins to an administrative unit. To learn how, see [Assign Azure AD roles with administrative unit scope](https://docs.microsoft.com/en-us/azure/active-directory/roles/admin-units-assign-roles).

- **Use PowerShell to assign admins to an administrative uni**. As a global admin, you can use this PowerShell cmdlet to assign admins to an administrative unit: [Add-AzureADMSScopedRoleMembership](/powershell/module/azuread/add-azureadmsscopedrolemembership?view=azureadps-2.0). To learn how, see [Add users to an administrative unit](https://docs.microsoft.com/azure/active-directory/roles/admin-units-add-manage-users#add-users-to-an-administrative-unit).

- **Use the Microsoft Graph API to assign admins to an administrative unit**. As a global admin, you can use the Microsoft Graph API to assign admins to an administrative unit. To learn how, see [Add users to an administrative unit](https://docs.microsoft.com/azure/active-directory/roles/admin-units-add-manage-users#add-users-to-an-administrative-unit).

## Select administrative units

If you're a Teams devices admin, after a global admin assigns you to an administrative unit, you can sign into the Teams admin center to manage devices. If you're assigned to only one administrative unit, you'll see only the devices that are assigned to that administrative unit. If you're assigned to multiple administrative units, you can switch between those administrative units without signing out from the Teams admin center. To do that:

1. Sign in to the [Teams admin center](https://admin.teams.microsoft.com/).

2. In the **Your administrative units** dialog box, follow one of these steps:
    - Select the administrative unit that you want to manage, or 
    - Select **All devices** if you have permission to manage all devices for your organization.

3. Select **Save**.

## Switch administrative units

If you're a Teams devices admin, you can switch between administrative units if you're signed in to the Teams admin center. To switch to a different administrative unit:

1. Sign in to the [Teams admin center](https://admin.teams.microsoft.com/).

2. In the left navigation, select **Teams devices**.

3. On the right pane, at the upper left, select the administrative unit shown.

4. In the **Your administrative units** dialog box, follow one of these steps:
    - Select the administrative unit that you want to manage, or 
    - Select **All devices** if you have permission to manage all devices for your organization.

5. Select **Save**.