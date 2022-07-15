---
title: Manage devices with administrative units
author: CarolynRowe
ms.author: crowe
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

# Manage devices in the Teams admin center with administrative units

Administrative units in the Teams admin center provide detailed, role-based access for managing Teams devices. Administrative units grant Teams admin access to specific resources but limit that admin's access to other resources. This is especially helpful if you have local Teams admins in different countries or regions.

For example, Contoso has operations around the globe. Alice is a global IT admin based in London, while Prashant is a local IT admin based in Bangalore, India. Today, when Prashant signs into the Teams admin center as a device administrator, he can see Teams devices around the globe. Alice wants to limit Prashant's access to Teams devices only in Bangalore. Administrative units let her do this. To learn more, see [Administrative units in Azure Active Directory](/azure/active-directory/roles/administrative-units).

> [!NOTE]
> Administrative units are currently available in the Teams admin center only for the Teams devices administrator role.

## Add administrative units

You need to be a global admin to add administrative units. To learn how, see [Add an administrative unit](/azure/active-directory/roles/admin-units-manage#add-an-administrative-unit).

## Assign admins to administrative units

You'll also need to be global admin to assign administrative units. You can assign administrative units using Azure portal, PowerShell, or the Microsoft Graph API. To learn more, see [Assign Azure AD roles with administrative unit scope](/azure/active-directory/roles/admin-units-assign-roles).

## Select administrative units

If you're a Teams devices admin, after a global admin assigns you to an administrative unit, you can sign into the Teams admin center to manage devices. If you're assigned to only one administrative unit, you'll see only the devices that are assigned to that administrative unit. If you're assigned to multiple administrative units, you can switch between those administrative units without signing out from the Teams admin center. 

1. Sign in to the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

2. In the **Your administrative units** dialog box, follow one of these steps:
    - Select the administrative unit that you want to manage, or 
    - Select **All devices** if you have permission to manage all devices for your organization.

3. Select **Save**.

## Switch administrative units

If you're a Teams devices admin, you can switch between administrative units if you're signed into the Teams admin center. To switch to a different administrative unit:

1. Sign in to the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

2. In the left navigation, select **Teams devices**.

3. On the right pane, at the upper left, select the administrative unit shown.

4. In the **Your administrative units** dialog box, follow one of these steps:
    - Select the administrative unit that you want to manage, or 
    - Select **All devices** if you have permission to manage all devices for your organization.

5. Select **Save**.

## Related topics

- [Add users or groups to an administrative unit](/azure/active-directory/roles/admin-units-members-add)
