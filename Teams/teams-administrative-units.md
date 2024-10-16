---
title: Using administrative units in Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: andrewklutz
ms.date: 10/16/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use administrative units to manage groups of users or other entities in Microsoft Teams.
---

# Administrative units for Microsoft Teams

This article describes the highlights of Administrative Units for Teams administration using the Teams admin center and the Teams PowerShell module. Administrative Units are a way to delegate administrative tasks to a subset of users, groups, or devices using the Microsoft Entra Admin Portal.

You could previously manage Devices via Administrative Units, but only for the Teams Administrator role, as outlined in this article: [Manage devices with administrative units](administrative-unit.md).

With more capabilities enabled to be managed via Administrative Units, there's a need to cover the following usages:

## Set up Administrative Units

### Scenario One: Creation of Administrative Units in the Microsoft Entra admin center (AAD)

Full details on how to create Administrative Units can be found here (Administrative Unit administrators need a Microsoft Entra ID P1 or P2 license): [Create or delete Administrative Units - Entra ID](/entra/identity/role-based-access-control/admin-units-manage?tabs=ms-powershell).

### Scenario Two: Assignment and unassignment of RBAC roles to Administrative Units in the Microsoft Entra admin center (AAD)

Global Administrators can assign any of the following RBAC roles using the method in the adjacent column:

|RBAC Role                              |Assignment method                                           |Documentation |
|---------------------------------------|------------------------------------------------------------|--------------|
|Teams administrator                    |Microsoft Entra admin center (UI)</br>Teams PowerShell</br>Teams Graph APIs |[Learn more](/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0&tabs=powershell#example-2--create-a-role-assignment-with-administrative-unit-scope) |
|Teams device administrator             |Microsoft Entra admin center (UI)</br>Teams PowerShell</br>Teams Graph APIs |[Learn more](/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0&tabs=powershell#example-2--create-a-role-assignment-with-administrative-unit-scope) |
|Teams communication administrator      |Microsoft Entra admin center (UI)</br>Teams PowerShell</br>Teams Graph APIs |[Learn more](/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0&tabs=powershell#example-2--create-a-role-assignment-with-administrative-unit-scope) |
|Teams communication support engineer   |Microsoft Entra admin center (UI)</br>Teams PowerShell</br>Teams Graph APIs |[Learn more](/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0&tabs=powershell#example-2--create-a-role-assignment-with-administrative-unit-scope) |
|Teams communication support specialist |Microsoft Entra admin center (UI)</br>Teams PowerShell</br>Teams Graph APIs |[Learn more](/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0&tabs=powershell#example-2--create-a-role-assignment-with-administrative-unit-scope) |
|Teams telephony administrator          |Microsoft Entra admin center (UI)</br>Teams PowerShell</br>Teams Graph APIs |         |

The role assignments listed in the table can also be applied directly to the intended users or groups. Learn more at [Use Microsoft Entra groups to manage role assignments - Microsoft Entra ID](/entra/identity/role-based-access-control/groups-concept).

## Roles and capabilities

|Management types |Admin |Device admin |Communication admin |Telephony admin |Communication support engineer |Communication support specialist |
|-----------------|------|-------------|--------------------|----------------|-------------------------------|---------------------|
|Teams management |NA    |NA           |NA                  |NA              |NA                             |NA                   |
|User management  |-Manage users list page</br>-User details page</br>--Account tab</br>--Meetings and calls</br>--Policies</br>--Devices tab |NA |-Manage users list page</br>-User details page</br>--Account tab</br>--Meetings and calls</br>--Policies</br>--Voice</br>--Voicemail |-Manage users list page</br>-User details page</br>--Account tab</br>--Meetings and calls</br>-Policies</br>-Voice</br>Voicemail |-Manage users list page</br>-User details page</br>--Meetings and calls |-Manage users list page</br>-User details page</br>--Meetings and calls |
|Devices management |The entire devices section (seven options) |The entire devices section (seven options) |NA |NA |NA |NA |
|Policy management  |Option to only perform user or group policy assignments for the following policies:</br>-Audio conferencing</br>-Meeting</br>-Customization</br>-Live events</br>-Events</br>-Messaging</br>-Calling</br>-Call hold</br>-Call park</br>-Caller ID</br>-Emergency</br>-Mobility</br>-Voice routing</br>-Voicemail</br>-Voice applications |NA |Option to only perform user or group policy assignments for the following policies:</br>-Audio conferencing</br>-Meeting</br>-Customization</br>-Live events</br>-Events</br>-Calling</br>-Call hold</br>-Call park</br>-Caller ID</br>-Emergency</br>-Mobility</br>-Voice routing</br>-Voicemail</br>-Voice applications |NA |NA |NA |
|Voice management |Phone Number assignment – From User Details Page (Only Direct Routing numbers) |NA |Phone Number assignment – From User Details Page (Only Direct Routing numbers) |NA |NA |NA |
|Analytics and reporting management |-Usage reports (only PSTN reports</br>)-Call quality dashboard (UII info redacted) |NA |-Usage reports (only PSTN reports</br>)-Call quality dashboard (UII info redacted) |NA |Call quality dashboard (UII info redacted) |Call quality dashboard (UII info redacted) |
|Apps management  |NA    |NA           |NA                  |NA              |NA                             |NA                   |

## Individual feature areas

### Device management

As a scoped administrator with the Teams device admin or Teams administrator role, you can:

- Access the Devices section in Teams admin center and view the list of devices assigned to the users in the Administrative unit
- Filter, sort, and search the devices by various criteria.
- Select a device and view its details, configuration, and status.
- Perform actions on the device, such as restart, reset, update, or assign to a user.

> [!NOTE]
> Export of devices isn’t available for scoped admin roles, you need to have tenant-wide permissions to export devices.

To learn more, see [Manage devices with administrative units](administrative-unit.md).

### User management

As a scoped administrator with the Teams administrator role or any of the Teams communication roles, you can:

- Filter, sort, and search the users by various criteria.
- Select a user and view their details, meetings, policies, and devices.
- Assign or unassign a Direct Routing phone number to a user in your Administrative Unit.
- Assign or unassign policies to a user in your Administrative Unit.
- Perform real-time or past meetings troubleshooting for a user in your Administrative Unit.

> [!NOTE]
> Export of users isn’t available for scoped admin roles, you need to have tenant-wide permissions to export users.

### Policy management

As a scoped administrator with the Teams administrator role or any of the Teams communication roles, you can:

- Access the Policy sections in the Teams admin center and view the list of policies available in the tenant.
- Assign or unassign policies to a user or a group in your Administrative Unit.
- View the policy assignments and the effective policy for a user or a group in your Administrative Unit. Batch policy assignments are also enabled.

### Phone number management

As a scoped administrator with the Teams administrator role or any of the Teams communication roles, you can:

- Assign or unassign Direct Routing phone numbers to users in your Administrative Unit from the User Details page in the Teams admin center.

### Analytics and reporting management

As a scoped administrator with the Teams administrator role or any of the Teams communication roles, you can:

- Access the Usage reports section in the Teams admin center and view the reports (Only PSTN) scoped to the users in your Administrative Unit.
- Filter, sort, and export the reports by various criteria.
- Access the Call Quality Dashboard section in the Teams admin center and view the call quality data for the users in your Administrative Unit.

## Limitations for Administrative Units

Tasks that aren't available in this phase for a scoped administrator (regardless of the RBAC role), in either the Teams admin center or through the Teams PowerShell module:

- Teams and channel settings
- Audio conferencing, voice, and voicemail settings
- Guest access
- External access
- Calling plan and Operator Connect numbers 
- Emergency addresses
- Teams apps
- Tenant level settings and conference bridges
- Policy packages
- Emergency addresses, network topology, networks, and locations
- Frontline teams and apps
- Teams advisor and network planner
- Rules

## Teams PowerShell and Administrative Units

The functionality outlined in this article is available for the RBAC roles using Teams PowerShell. The differences in Powershell are:

- An admin assigned with multiple Admin units is able to manage all the users across each admin unit simultaneously.
- In the Teams admin center, the scoped admin would have to select the particular Administrative Unit and manage those users within the Administrative Unit at any given time.

An example of using Teams PowerShell and Administrative Units is:

- An organization has three branches: North, South, and East. North and South branches are assigned to a single admin, and East is assigned to another admin.
- The scoped admin assigned with North and South branches is able to manage all the users across both North and South simultaneously using Teams PowerShell.
- In the Teams admin center, the scoped admin can either manage the North or South branch in turn, but not both at the same time.
