---
title: Accessing the Pro Management portal
author: altsou
ms.author: altsou
manager: serdars
ms.reviewer: 
ms.date: 08/16/2021
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: itpro-rooms
audience: Admin
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_MTRP
  - Tier3
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about how to access the Microsoft Teams Rooms Pro Management portal.
f1keywords: 
---

# Accessing the Pro Management portal

In order to access the Pro portal you will first need to have Microsoft Teams Rooms Pro licenses added to your tenant. The first time the [Teams Rooms Pro Management portal](https://portal.rooms.microsoft.com/) is accessed must be done by a tenant global administrator in order to consent the application. 

The global admin can then [assign roles](https://learn.microsoft.com/en-us/microsoftteams/rooms/rooms-pro-rbac) to other users in the tenant for accessing the portal. The Built-in "Teams Rooms Pro Manager" role will give users full control over the Pro portal so it can be managed without a tenant global admin account. Tenant global admins will always have "Teams Rooms Pro Manager" permissions to the Pro portal, if roles are ever accidentally removed or if users are deleted you can always use a global admin account to get back to the role assignments. 

## Assign users to the Teams Rooms Pro Manager role

Complete the following steps to assign users to the Teams Rooms Pro Manager role:

1. Log in to the [Teams Rooms Pro Management portal](https://portal.rooms.microsoft.com/) with the tenant global admin account.
2. Navigate to **Settings** > **Settings** > **Roles** and then select **Teams Rooms Pro Manager**.
3. Under **Teams Rooms Pro Manager**, select the **Assignments** tab and then select **Add Assignment**.
4. Follow the wizard to name the assignment and select the users who should be added to it. The assignment will apply to all rooms and room groups.
5. At the end of the assignment wizard, select **Add assignment**.

Users who are assigned the Teams Rooms Pro Manager role have full access to all settings and rooms in the Pro portal. You can also assign users "Site Lead" or "Site Technician" default roles or define customer roles for those responsible for the day-to-day management and monitoring of Teams Rooms. 

After you've assigned users to roles, continue to the [Enroll a Teams Rooms device](enroll-a-device.md) to add a Teams Rooms device to the managed service portal.

<!-- ## Enroll a Teams Rooms device

 To enroll a device in the Teams Rooms Premium managed service, see [Monitoring device software installation](monitor-software-installation-guide.md).

2. Select on the **?** icon at the top right-hand corner of the portal to launch the help menu. The help menu includes an [Installation guide](https://portal.rooms.microsoft.com/docs/MMR%20Monitoring%20Software%20Installation%20Guide%20Feb%202021.pdf) containing detailed enrollment instructions:

    1. Review the **Pre-requisites** section in the Installation guide. Confirm that the URLs listed in the **URLs Required for Communication** list are added to your firewall's traffic allow list.
    2. Follow the instructions in the **Enabling TPM Settings** section to enable the Trusted Platform Module (TPM) functionality on your device.
    3. Follow the instructions in the **Adding Proxy Settings** section to configure your device to use your proxy gateway, if you have one.
    4. Follow the instructions in the **Process** section to install the monitoring agent software and configure the self enrollment key on your device.

3. After the monitoring agent and unique XML key are configured on your device, navigate to **Rooms** > room name > **Status**, and then select **Enroll**.

    > [!NOTE]
    > The Teams Rooms device will remain in the **Onboarding** state until a Managed Service Administrator enrolls the device using the portal.

    See [Monitoring device software installation](monitoring-software-installation-guide.md).

<!--## Link to Installation guide

The **Help** menu provides a link to the [Installation guide](https://portal.rooms.microsoft.com/docs/MMR%20Monitoring%20Software%20Installation%20Guide%20Feb%202021.pdf) which in turn provides the following information:

- Instructions on URLs that need to be allow-listed to serve to enable room telemetry to be sent to the managed service.
- Instructions for applying the Microsoft Teams Rooms Premium monitoring agent and unique XML key as part of enrolling a device in the managed service.
- Troubleshooting instructions.-->
