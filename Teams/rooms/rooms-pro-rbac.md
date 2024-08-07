---
title: Role-based access control in the Microsoft Teams Rooms Pro Management Portal
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: altsou
ms.date: 04/04/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about role-based access control in the Microsoft Teams Rooms Pro Management Portal.
f1keywords: 
---

# Role-based access control in the Microsoft Teams Rooms Pro Management Portal

Role-based access control (RBAC) in the Microsoft Teams Rooms Pro Management portal helps you manage user access to room resource data in your organization. By assigning roles to your portal users, you can limit what they can see and change. Each role has a set of permissions that determine what users with that role can access and change within your organization.

To create, edit, or assign roles, your account must have one of the following permissions:

- Global Administrator through Microsoft Entra ID
- Teams Rooms Pro Manager through the Microsoft Teams Rooms Pro Management portal

> [!IMPORTANT]
>Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

## What is a role?

A role defines the set of permissions granted to users assigned to that role. For now, the Microsoft Teams Rooms Pro Management portal has three built-in roles: **Teams Rooms Pro Manager**, **Site Lead**, and **Site Technician**. They cover some common scenarios for users in your organization that may be involved in managing your rooms.

To see roles, in the left navigation of the Microsoft Teams Rooms Pro Management portal, go to **Roles**, and then select any of the roles to see the role’s properties, permissions, and assignments.  

- **Properties**: The name, role type, and description
- **Permissions**: Lists features and level of permissions to which the role has access.
- **Assignments**: A list of role assignments defining which users have the configured permissions over the scope of room resource accounts. A role can have multiple assignments, and a user can be in multiple assignments.

## Built-in roles

You can assign built-in roles to groups or users without further configuration. Keep in mind that you can't delete or edit the name, description, type, or permissions of a built-in role.

- **Teams Rooms Pro Manager**: Has full access to the Microsoft Teams Rooms Pro Management portal.
- **Site Lead**: Organizes rooms, has access to reports and can manage tickets. Can't reset enrollment key or make changes to service configurations.  
- **Site Technician**: Manages tickets for specific rooms. Doesn't have permissions to modify service configurations or organize rooms.

The following table summarizes what each role can do.

|Features |Permission |Teams Rooms Pro Manager  |Site Lead  |Site Tech  |
|---------|---------|---------|---------|---------|
|Room management     |View        |&#10004;           |&#10004;           |&#10004;  |
|    |Modify         |&#10004;           |&#10004;           |&#10004; |
|    |Unenroll         |&#10004;           |&#10004;           |&#10004; |
|Room actions    |Read-only actions         |&#10004;           |&#10004;           |&#10004;  |
|    |Read-write actions         |&#10004;           |&#10004;         ||
|Room groups   |Create         |&#10004;           |           ||
|    |View       |&#10004;          |&#10004;           ||
|    |Modify         |&#10004;           |           ||
|Update management    |Create         |&#10004;           |           ||
|    |View         |&#10004;           |           ||
|    |Modify         |&#10004;           |           ||
|Reports   |View        |&#10004;           |&#10004;           ||
|Ticket management   |View         |&#10004;           |&#10004;           |&#10004;  |
|    |Modify        |&#10004;           |&#10004;           |&#10004;  |
|Role management    |View         |&#10004;           |         ||
|    |Modify         |&#10004;           |         ||
|Inventory management    |View         |&#10004;           |         ||
|    |Modify         |&#10004;           |         ||
|Microsoft Teams Rooms Pro Management service settings    |View         |&#10004;           |         ||
|    |Modify        |&#10004;           |         ||
## Create a custom role

If the built-in roles do not suit your organizational needs, you can create a role and configure its permissions as desired. To create a role, you must be a Global Administrator or Teams Rooms Pro Manager role. 

> [!IMPORTANT]
>Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

1. In the left navigation of the Microsoft Teams Rooms Pro Management portal, go to **Settings** > **Roles**.
2. Select **Create role**.
3. On the **General settings** page, under **Role properties**, enter a name for this role. Under **Description**, enter details about this role. Choose **Next**.
4. On the **Permissions** page, under **Role permissions**, choose the permissions for this role by selecting the appropriate check-boxes. Choose **Next** to create the first assignment for this role.
5. On the **Assignments** page, under **Assignment properties**, enter a name for this assignment. The description is optional. Under **Notification settings** select the **E-mail notifications** check-box if users of this role should receive email notifications from the service on rooms in the **Scope** of this assignment. Choose **Next**.
6. On the **Members** page, in the **Search for user or security group** box, enter the name of a user or security group in your tenant to which you want to give permissions, and then complete the selection. Choose **Next**. 
7. On the **Scope** page, in the **Search for room or room group** box, type the name of either a room or room group that the user will be allowed to manage. Choose **Next**.
8. On the **Finish** page, review the details of the role and assignment. If you're satisfied with the configuration, choose **Add new role**. If you want to edit a section, use the **Previous** button or select the step in the left navigation.  

## Assign a role

To assign roles, you must be a Global Administrator or Teams Rooms Pro Manager role or have a role with role management permissions.

> [!IMPORTANT]
>Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

1. In the left navigation of the Microsoft Teams Rooms Pro Management portal, expand **Settings** > **Roles**.

    :::image type="content" source="../media/microsoft-teams-rooms-premium-roles.png" alt-text="Screenshot of Access control page showing roles.":::

2. Select the role you want to assign.
3. In the role pane, select **Assignments** > **Add assignment**.

    :::image type="content" source="../media/microsoft-teams-rooms-premium-role-assignments.png" alt-text="Screenshot of Add option to add a role.":::

4. On the **General settings** page, under **Assignment properties**, enter a name for this assignment. The description is optional. Under **Notification settings**, select the **E-mail notifications** check-box if users of this role should receive email notifications from the service on rooms in the **Scope** of this assignment. Choose **Next**. 
5. On the **Members** page, in the **Search for user or security group** box, enter the name of a user or security group in your tenant to which you want to give permissions, and then complete the selection. Choose **Next**. 
6. On the **Scope** page, in the **Search for room or room group** box, type the name of either a room or room group that the user will be allowed to manage. Choose **Next**.
7. On the **Finish** page, review the details of the assignment. If you're satisfied with the configuration, choose **Add assignment**. If you want to edit a section, use the **Previous** button or select the step in the left navigation.  

## Related topics

- [Microsoft Teams Rooms Pro Management portal](rooms-pro-management.md)
