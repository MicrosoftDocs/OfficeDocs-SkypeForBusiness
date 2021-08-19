---
title: Enrolling Microsoft Teams Rooms accounts in Microsoft Teams Rooms Premium managed service
author: v-smandalika
ms.author: v-smandalika
manager: dansimp
ms.reviewer:  
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn about how to enroll Microsoft Teams Rooms accounts in Microsoft Teams Rooms Premium managed service.
f1keywords: 
---

# Enrolling in the Microsoft Teams Rooms Premium (MTRP) managed service

To enroll a Microsoft Teams Rooms device in the Microsoft Teams Rooms Premium (MTRP) managed service, start by assigning a **Managed Service Administrator**, for which you have to perform the following steps:

1. Log in to the [Teams Rooms Premium portal](https://portal.rooms.microsoft.com/) with the same administrator privileges used to log in to the Microsoft 365 admin center.
1. Choose **Settings > Roles** in the left navigation pane to assign a **Managed Service Administrator**.  The **Managed Service Administrator** will own the day-to-day management and monitoring of the MTRP-managed services portal. For information on the **Managed Service Administrator** role in setting up device enrollment, see [Managed Service Administrator tasks](#managed-service-administrator-tasks).

## Managed Service Administrator tasks

The **Managed Service Administrator** must execute the following tasks to complete device enrollment in the service:

1. The **Managed Service Administrator** must click on**?** icon at the top right-hand corner of the portal, to launch the **Help** menu. The **Help** menu includes an installation guide ([Link to Installation guide](#link-to-installation-guide)) containing detailed enrollment instructions. For information on the **Installation guide** contents, see [Link to Installation guide](#link-to-installation-guide).
1. Review the **Pre-requisites** section in the **Installation guide**. Confirm that URLs listed in **URLs Required for Communication** list are added to your **traffic allowlist**. Enable **TPM Settings** if disabled, and add **Proxy Settings**, if applicable.  These actions will allow telemetry to be sent to the managed service once the agent is installed.
1. Review the **Process** section in the **Installation guide**. Follow the directions for applying the agent and unique XML key used to provision each Teams Rooms device appropriately for service enrollment.
1. Once the monitoring agent and unique XML key are applied, the **Managed Service Administrator** completes the enrollment process by navigating to **Rooms** in the left navigation pane and choosing the target room name. Service is initiated by choosing **Enroll** under **Rooms**> room name > **Status**. Note that the room will remain in **Onboarding** state until the **Managed Service Administrator** applies the **Enroll** button to start the managed service.

### Link to Installation guide

The **Help** menu provides a link to the **Installation guide** which in turn provides the following information:

- Instructions on URLs that need to be allowlisted to serve to enable room telemetry to be sent to the managed service.
- Instructions for applying the Microsoft Teams Rooms Premium monitoring agent and unique XML key as part of enrolling a device in the managed service.
- Troubleshooting instructions.
