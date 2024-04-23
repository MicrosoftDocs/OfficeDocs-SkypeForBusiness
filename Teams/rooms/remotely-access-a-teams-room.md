---
title: Remote access to manage Teams rooms
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

## Prerequisites

Before setting up remote access, verify the following prerequisites are met:

- Teams Rooms Pro license for the Teams Rooms console.
- Supported Microsoft Teams Rooms on Windows, see [Teams Rooms Certified Devices](https://docs.microsoft.com/en-us/microsoftteams/devices/teams-certified-devices).
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