---
title: Remotely access a Teams Room on Windows console
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
ms.reviewer: kimmatlock
ms.date: 5/06/2024
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
description: Set up remote access in Microsoft Teams Rooms Pro Management for troubleshooting and managing Teams Rooms consoles devices.
---

# Set up Remote Access in Microsoft Teams Rooms Pro Management portal

This article provides guidance on setting up remote access in Microsoft Teams Rooms Pro Management portal. Using remote access lets support staff securely troubleshoot hardware and software configuration issues on unattended Teams Rooms consoles without having the console next to them.

Remote access is only available for certified Windows based Teams Rooms consoles running Windows 11.

> [!Note]
> Microsoft Teams Rooms consoles running Android support is coming soon.

## Teams Rooms Pro Management Remote Access capabilities and requirements

Teams Rooms Pro Management has its own role-based access control, which helps you manage user access to room resource information across your organization. By assigning roles to your portal users, you can limit what they can see and change. Each role has a set of permissions that determines the level of access a user assigned to a specific role can access and change within your organization.

See [Role Base access control in Teams Rooms Pro management portal](/microsoftteams/rooms/rooms-pro-rbac).

- **Requires tenant level opt-in to enable the feature** By default, remote access isn't enabled for your tenant. It must be turned on using assign role-based permissions. You need put in the email address that provides an acknowledgement you're explicitly enabling this feature. Providing this acknowledgement creates an audit log record so someone can be held accountable. The Microsoft Teams Rooms Pro Management Remote access feature follows [Microsoft privacy](https://privacy.microsoft.com/) policies.

> [!Note]
> Before you enable and set up remote access, consider your privacy and compliance requirements.

- **Requires Teams Rooms Pro management custom role permissions** By default, there aren't any Teams Pro management roles  enabled for remote access. If you do want to turn on remote access for someone, you need first create a custom role, add the remote access permission to this custom role, and then assign those users and rooms to that custom role.

When you create, edit, or assign custom roles, the account must have one of the following permissions:
    - Global Administrator in Azure Active Directory (Azure AD)
    - Teams Rooms Pro Manager in the Microsoft Teams Rooms Pro Management portal

> [IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

- **Role-based access control (RBAC)**: You can use RBAC roles to determine the scope of a Teams Rooms Pro management remote access users. For remote access, it as two RBAC roles:

  - **VIEW** These users can remotely access the device, but with this level, they're limited to only viewing the Teams Rooms consoles and displays. No changes can be saved.
  - **MODIFY** These users can remotely access the device, but with this level, they have a full range of actions they can take including making setting changes and saving those changes. For example, they can interact with a remote keyboard control.

- **Requires Teams Rooms Pro management portal login** To use remote access, the Teams Room Pro management user that is assigned your custom RBAC role, with the correct permissions assigned, must sign into the Teams Rooms Pro management portal for your organization. You can't use remote access to access Teams Rooms devices from outside of the Teams Rooms Pro management portal.  

- **View details about past sessions** In the Teams Rooms Pro management portal, you can view audit logs that include details about who connected to the room console, on what device, and for how long.

## Prerequisites

Before setting up remote access, verify the following prerequisites are met:

- Buy a Teams Rooms Pro license for the Teams Rooms console.
- Verify the console is supported and is running Microsoft Teams Rooms on Windows. See [Teams Rooms Certified Devices](/microsoftteams/rooms/certified-hardware).
- Install Microsoft Visual C++ 2015-2022 Redistributable (x64).
- Prepare your organization's network for [Azure Communication Services]([/azure/communication-services/concepts/network-prep](/azure/communication-services/concepts/voice-video-calling/network-requirements#firewall-configuration).
- Add the following URLs to your network's allowed list:
  - https://mmrprodnoampubsub.webpubsub.azure.com
  - https://mmrprodemeapubsub.webpubsub.azure.com
  - https://mmrprodapacpubsub.webpubsub.azure.com

## Limitations

Teams Rooms Pro management remote access has these limitations:

- It's not available in GCC, GCC-High, or DoD government tenants.
- It's not available in Teams Rooms multitenant management portal.
- You can't establish a Teams Rooms Pro management session from one tenant to a different tenant.
- It's only available in selected markets and some localized versions.

## Supported platforms, browsers, and devices

- Windows 11 on Teams Rooms for Windows
- Microsoft Edge browser

## Data and privacy

Microsoft logs a small amount of session data to monitor health of the remote access sessions. This data includes:

- The start and end time of the session. This information is stored on Microsoft servers for 180 days.
- The user that accessed a device. This information is stored on Microsoft servers for 180 days.
- Any errors coming from a remote access session, such as unexpected disconnections. This information is stored on Microsoft servers for 180 days.

The Teams Rooms Pro Management portal then logs a small amount of data. This data includes:

- It logs the remote access logs session details about the user accessing the Teams Rooms device. Microsoft can't access a session or view any actions or keystrokes that occur in the session.
- It logs if a remote access session can't be established because the Teams Room console is currently in a call.
- It logs when a Teams Rooms Pro management user accesses the device, a red ring is displayed on the console for anyone that is seeing the console in the room.
- It logs when a Teams Rooms Pro management user remotely accesses the device. However, audio isn't enabled.

> [!Note]
> There are no additional Windows services required for the remote access feature.
## Enable remote access

By default, remote access is disabled. To enable remote access:

1. Sign in to the [Teams Rooms Pro Management portal](https://portal.rooms.microsoft.com/) with the same administrator privileges as that used to sign in to the Microsoft 365 admin center.
2. In the **Teams Rooms Pro Management portal**, go to **Settings** > **Remote Access**.
3. In the **Remote Access** section, set **Enable Remote Access** to **Enabled** to allow the use of remote access in your tenant. By default, this setting is **Disabled**.
4. Then enter the email address of the user. This acknowledges that they're enabling this feature.
5. Select **Save**.

## Set permissions for remote access

By default, the Teams Rooms Pro Manager role doesn't have remote access permissions enabled. To create a custom role and assign remote access permissions:

1. Sign in to the [Teams Rooms Pro Management portal](https://portal.rooms.microsoft.com/) with the same administrator privileges as that used to sign in to the Microsoft 365 admin center.
2. In the **Teams Rooms Pro Management portal**, go to **Settings** > **Roles**.
3. Create a custom role that grants remote access permissions to Pro management admin, site lead, and site technicians, and then add the rooms they'll be accessing.
4. Assign **Remote Access view** or **Remote Access modify** permissions to the same custom role.
5. Create **Assignments** for specific users and consoles that will be using the remote access feature.
6. Select **Finish** and **Save**.

## Using Remote Access

To remotely administer a Teams Rooms console:

1. In the **Teams Rooms Pro management portal**, choose **Rooms**.
2. Select the room device you want to remotely administer and then, in the **Rooms tab**, choose the **Remote Access** tab.
3. Select **Start Session** to establish a secure connection and remotely access the console.

  > [!Note]
  > The console must be in a monitored state within the Teams Rooms Pro Management portal and the console must not be in  an active call.

 These are the commands available during a session:

  |**Command**|**Description**|
    |:-----|:-----|
    |Restart a device| N/A|
    |Shortcut commands| N/A|
    |Restart a session| **Enable (default)** it will automatically restart the device at the end of the session. **Disable** It won't automatically restart the device at the end of the current session. The next session will reset the value to **Enable**.|
    |Help|Links to this documentation.|
    |Displays|MTR console, Front of Room Display 1, or Front of Room Display 2 (if available).|
    |Enter full screen|Expand the modal window to enter full screen|
    |End session|Terminates the session.|

> [!NIMPORTANT]
  > Users with view only access permission can use these commands. However, they won't have the ability to interact with the Teams Rooms console or save any changes. For those users that have modify access permissions, they can interact with the console and save any changes.

## Security best practices for remote access

|**Security best practice**|**More information**|
|:-----|:-----|
|When remotely administering the device, don't enter passwords for privileged accounts.|When accounts and passwords are sensitive, be careful with those account names and passwords.|
|If you disconnect the Teams user that is signed in during a remote access session, ensure that you sign out before you disconnect the remote access session. |If you don't sign out in this scenario, the session remains open and visible in the room.|
|Limit the Permitted Viewers list. |Local administrator rights aren't required for a user to be able to use remote control.|

## Privacy information for Teams Rooms Pro Management remote access

Microsoft Teams Rooms Pro Management Remote access feature follows [Microsoft privacy](https://privacy.microsoft.com/) policies. More specifically:

- There's no active listening on the console.
- There's no processing of passwords and user credentials if they're used.
- There's only Just in Time (JIT) sessions enabled.

Before you set up remote access, consider your privacy, security, and compliance requirements from the tenant organization.

For more information about security, privacy, and audit reporting, see [Security and Privacy for Remote Access in Teams Rooms Pro Management](/microsoftteams/rooms/security).

## Audit reporting
Teams Rooms Pro managers can run an audit log to identify remote access sessions and users who have remote access permissions.  Log history is available under **Settings/General**.

### Terms of use
Microsoft reserves the right to update and modify this feature at any time without notice to you. The current licensing model allows unlimited number of sessions. See [Microsoft Terms of Use](https://www.microsoft.com/legal/terms-of-use).
