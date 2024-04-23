---
title: Remotely access a Teams Room on Windows console
ms.author: tonysmit
author: tonysmit
manager: pamgreen
ms.reviewer: kimmatlock
ms.date: 4/23/2024
ms.topic: article
audience: admin
appliesto:
  - Microsoft Teams
ms.service: msteams
ms.subservice: itpro-rooms
ms.collection: 
  - M365-collaboration
  - teams-rooms-consoles
  - Tier1
f1.keywords: 
  - NOCSH                           
search.appverid: MET150
ms.localizationpriority: medium
ms.custom: QuickDraft  
ai-usage:  
- ai-assisted  
description: Set up remote access in Microsoft Teams Rooms Pro Management for troubleshooting and managing Teams Rooms consoles devices.
---

# Set up Remote Access in Microsoft Teams Rooms Pro Management portal

This article provides guidance on setting up remote access in Microsoft Teams Rooms Pro Management portal that lets support staff securely troubleshoot hardware and software configuration issues on unattended Teams Rooms consoles.

Remote access is available for all certified Windows based Teams Rooms sonoles running Windows 11.

## Teams Rooms Pro Management Remote Access capabilities and requirements

Teams Rooms Pro Management has its own role-based access control which helps you manage user access to room resource data in your organization. By assigning roles to your portal users, you can limit what they can see and change. Each role has a set of permissions that determines what users with that role can access and change within your organization.

See [Role Base access control in Teams Rooms Pro management portal](/rooms-pro-rbac).

- **Requires tenant level opt-in to enable the feature** By default, remote access isn't enabled for your tenant. It must be enabled to assign role-based permissions. You will also need to provide acknowledgement that you are providing permission to enable this feature which will create an audit log record. Make sure that Microsoft Teams Rooms Pro Management Remote access follows {Microsoft privacy](https://privacy.microsoft.com/) policies.

> [!Note]
> Before you enable and configure remote access, consider your privacy and compliance requirements.

- **Requires Teams Rooms Pro management custom role permissions** By default, Teams Pro management roles are n't enabled for remote access. If you choose to turn on remote access, you will need to apply the remote access permission to a custom role and assign users and rooms to have access to use this feature.  

To create, edit, or assign custom roles, your account must have one of the following permissions:
    - Global Administrator through Azure Active Directory (Azure AD)
    - Teams Rooms Pro Manager through the Microsoft Teams Rooms Pro Management portal

- Role-based access control (RBAC): Admins can set RBAC rules that determine the scope of a Teams Rooms Pro management users’ remote access, such as:
  - **VIEW** The users who can remotely access the device but is limited to only viewing the device console and displays
  - **MODIFY** The users will have full range of actions they can do while accessing Teams rooms devices. For example, who can interact with remote keyboard control.

- **Requires Teams Rooms Pro management portal login** To use remote access, the Teams Room Pro management custom role user must sign into the Teams Rooms Pro management portal from your organization. You can't use remote access to access Teams Rooms devices outside of the Teams Rooms Pro management portal.  

- **View details about past sessions** In the Teams Rooms Pro management portal, you can view audit logs that include details about who connected to the room device, on what device, and for how long.  

## Prerequisites

Before setting up remote access, verify the following prerequisites are met:

- Teams Rooms Pro license for the Teams Rooms console.
- Supported Microsoft Teams Rooms on Windows, see [Teams Rooms Certified Devices](/devices/teams-certified-devices).
- Microsoft Visual C++ 2015-2022 Redistributable (x64) is installed.
- Prepare your organization's network for [Azure Communication Services](/azure/communication-services/concepts/network-prep)
- Add the following URLs to your network allowed list:
  - https://mmrprodnoampubsub.webpubsub.azure.com
  - https://mmrprodemeapubsub.webpubsub.azure.com
  - https://mmrprodapacpubsub.webpubsub.azure.com

## Enable Remote Access

By default, remote access is disabled. To enable remote access:

1. Sign in to the **Teams Rooms Pro Management portal** and go to **Settings** \> **Remote Access**.
2. Under the Remote Access section:
    1. Set **Enable Remote Access** to **Enabled** to allow the use of remote access in your tenant. By default, this setting is **Disabled**.
    2. Enter the email address of the Admin user acknowledging enabling this feature.
3. Select **Save**.

## Set permissions for Remote Access

By default, the Teams Rooms Pro Manager role doesn't have remote access permissions enabled. To create a custom role and assign remote access permissions:

1. From the **Teams Rooms Pro manager portal** navigation, go to **Settings** > **Roles**.
2. Create a **Custom role** to grant remote access to Pro Management Admin, Site Lead, and Site technicians, and to assign the rooms they will be allowed to access.
3. Assign **Remote Access view** or **modify** permissions to the custom role.
4. Create **Assignments** for specific users and devices. Only users and devices scoped into an assignment will have remote access enabled.
5. Select **Finish** and **Save**.

### Using Remote Access

To remotely administer a Teams Rooms console:

1. In the **Teams Rooms Pro management portal**, choose **Rooms**.
2. Select the room device you want to remotely administer and then, in the **Rooms tab**, choose the **Remote Access tab**.
3. Select **Start Session** to establish a secure connection to remotely access the device.

For more details on security, privacy, and audit reporting, see [Security and Privacy for Remote Access in Teams Rooms Pro Management](/microsoftteams/rooms/security-privacy).