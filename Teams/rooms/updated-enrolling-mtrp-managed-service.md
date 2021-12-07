---
title: Enroll a Teams Rooms device in the Microsoft Teams Rooms Premium managed service
author: v-smandalika
ms.author: v-smandalika
manager: serdars
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
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about how to enroll Microsoft Teams Rooms accounts in Microsoft Teams Rooms Premium managed service.
f1keywords: 
---

# Enroll a device in the Microsoft Teams Rooms Premium managed service

To enroll a Microsoft Teams Rooms device in the Teams Rooms Premium managed service, you need to assign one more users to the Managed Service Administrator and then complete the enrollment steps using that user.

## Assign users to the Managed Service Administrator role

Complete the following steps to assign users to the Managed Service Administrator role:

1. Log in to the [Teams Rooms Premium portal](https://portal.rooms.microsoft.com/) with the same administrator privileges as that used to log in to the Microsoft 365 admin center.
2. Navigate to **Settings** > **Settings** > **Roles** and then select **Managed Service Administrator**.
3. Under **Managed Service Administrator**, select the **Assignments** tab and then select **Add**.
4. Follow the wizard to name the assignment and select the users who should be added to it. The assignment will apply to all rooms and room groups.
5. At the end of the assignment wizard, select **Add assignment**.

Users who are assigned the Managed Service Administrator role are responsible for the day-to-day management and monitoring of the Teams Rooms Premium managed service portal.

After you've assigned users to the Managed Service Administrator role, continue to the [Enroll a device](#enroll-a-teams-rooms-device) section to add a Teams Rooms device to the managed service portal.

## Enroll a Teams Rooms device

To enroll a device in the Teams Rooms Premium managed service, see [Monitoring device software installation](monitoring-software-installation-guide.md).

3. After the monitoring agent and unique XML key are configured on your device, navigate to **Rooms** > room name > **Status**, and then select **Enroll**.

    > [!NOTE]
    > The Teams Rooms device will remain in the **Onboarding** state until a Managed Service Administrator enrolls the device using the portal.

    See [Monitoring device software installation](monitoring-software-installation-guide.md).


