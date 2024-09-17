---
title: Accessing the Pro Management portal
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: srpall
ms.date: 03/24/2024
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
description: Learn about how to access the Microsoft Teams Rooms Pro Management portal.
f1keywords: 
---

# Accessing the Pro Management portal

To access the Teams Rooms Pro Management portal, you need to assign one or more users to the Teams Rooms Pro Manager role and then complete the enrollment steps using that user.

## Assign users to the Teams Rooms Pro Manager role

Complete the following steps to assign users to the Teams Rooms Pro Manager role:

1. Log in to the [Teams Rooms Pro Management portal](https://portal.rooms.microsoft.com/) with the same administrator privileges as that used to log in to the Microsoft 365 admin center.
1. Navigate to **Settings** > **Settings** > **Roles** and then select **Teams Rooms Pro Manager**.
1. Under __Teams Rooms Pro Manager__ select the **Assignments** tab and then select **Add**.
4. Follow the wizard to name the assignment and select the users who should be added to it. The assignment will apply to all rooms and room groups.
5. At the end of the assignment wizard, select **Add assignment**.

Users who are assigned the Teams Rooms Pro Manager role are responsible for the day-to-day management and monitoring of Teams Rooms and will have access to all rooms and features within the Teams Rooms Pro management portal. To assign additional roles to restrict access to specific rooms and users, see more under [Role Based Access Control](/microsoftteams/rooms/rooms-pro-rbac)

After you've assigned users to the Teams Rooms Pro Manager role, continue to the [Enroll a Teams Rooms device](enroll-a-device.md) to add a Teams Rooms device to the Teams Rooms Pro management portal.

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
