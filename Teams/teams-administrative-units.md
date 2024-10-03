---
title: Using administrative units in Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: andrewklutz
ms.date: 10/15/2024
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

This article describes the highlights of Administrative Units (AUs) for Teams administration using the Teams Admin Center (TAC) and the Teams PowerShell Module (TPM). AUs are a way to delegate administrative tasks to a subset of users, groups, or devices using the Microsoft Entra Admin Portal.

You could previously manage Devices via AUs, but only for the Teams Administrator role, as outlined in this article: [Manage devices with administrative units](administrative-unit.md).

With more capabilities enabled to be managed via AU, there's a need to cover the following usages:

## Set up AUs

### Scenario One: Creation of AUs in Entra Portal (AAD)

Full details on how to do this can be found here (please note that Administrative Unit administrators need a Microsoft Entra ID P1 or P2 license): [Create or delete Administrative Units - Entra ID](/entra/identity/role-based-access-control/admin-units-manage?tabs=ms-powershell).

### Scenario Two: Assignment and unassignment of RBAC roles to AUs in Entra Portal (AAD)

Global Administrators can assign any of the following RBAC roles using the method in the adjacent column:

|RBAC Role                              |Assignment method                                           |Documentation |
|---------------------------------------|------------------------------------------------------------|--------------|
|Teams administrator                    |Entra Portal (UI)</br>Teams Powershell</br>Teams Graph APIs |[Learn more](/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0&tabs=powershell#example-2--create-a-role-assignment-with-administrative-unit-scope) |
|Teams device administrator             |Entra Portal (UI)</br>Teams Powershell</br>Teams Graph APIs |[Learn more](/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0&tabs=powershell#example-2--create-a-role-assignment-with-administrative-unit-scope) |
|Teams communication administrator      |Entra Portal (UI)</br>Teams Powershell</br>Teams Graph APIs |[Learn more](/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0&tabs=powershell#example-2--create-a-role-assignment-with-administrative-unit-scope) |
|Teams communication support engineer   |Entra Portal (UI)</br>Teams Powershell</br>Teams Graph APIs |[Learn more](/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0&tabs=powershell#example-2--create-a-role-assignment-with-administrative-unit-scope) |
|Teams communication support specialist |Entra Portal (UI)</br>Teams Powershell</br>Teams Graph APIs |[Learn more](/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0&tabs=powershell#example-2--create-a-role-assignment-with-administrative-unit-scope) |
|Teams telephony administrator          |Entra Portal (UI)</br>Teams Powershell</br>Teams Graph APIs |         |

The role assignments listed in the table can also be applied directly to the intended users or groups. Learn more at [Use Microsoft Entra groups to manage role assignments - Microsoft Entra ID](/entra/identity/role-based-access-control/groups-concept).

## Roles and capabilities

|Management types |Admin |Device admin |Communication admin |Telephony admin |Communication support engineer |Communication support specialist |
|-----------------|------|-------------|--------------------|----------------|-------------------------------|---------------------|
|Teams management |NA    |NA           |NA                  |NA              |NA                             |NA                   |
|User management  |-Manage users list page</br>-User details page</br>--Account tab</br>--Meetings and calls</br>--Policies</br>--Devices tab |NA |-Manage users list page</br>-User details page</br>--Account tab</br>--Meetings and calls</br>--Policies</br>--Voice</br>--Voicemail |-Manage users list page</br>-User details page</br>--Account tab</br>--Meetings and calls</br>-Policies</br>-Voice</br>Voicemail |-Manage users list page</br>-User details page</br>--Meetings and calls |-Manage users list page</br>-User details page</br>--Meetings and calls |
|Devices management |The entire devices section (seven options) |The entire devices section (seven options) |NA |NA |NA |NA |
|Policy management  |Option to only perform user or group policy assignments for the following policies:</br>-Audio conferencing</br>-Meeting</br>-Customization</br>-Live events</br>-Events</br>-Messaging</br>-Calling</br>-Call hold</br>-Call park</br>-Caller ID</br>-Emergency</br>-Mobility</br>-Voice routing</br>-Voicemail</br>-Voice applications |NA |Option to only perform user or group policy assignments for the following policies:</br>-Audio conferencing</br>-Meeting</br>-Customization</br>-Live events</br>-Events</br>-Calling</br>-Call hold</br>-Call park</br>-Caller ID</br>-Emergency</br>-Mobility</br>-Voice routing</br>-Voicemail</br>-Voice applications |NA |NA |NA |
|Voice management |         |         |         | | | |
|Analytics and reporting management |         |         |         | | | |
|Apps management  |NA    |NA           |NA                  |NA              |NA                             |NA                   |




