---
title: Enroll a Teams Rooms device in the Microsoft Teams Rooms Premium managed service
author: donnah007
ms.author: v-donnahill
manager: serdars
ms.reviewer: 
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_MTRP
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about how to enroll Microsoft Teams Rooms accounts in Microsoft Teams Rooms Premium managed service.
f1keywords: 
---

# Enroll a device in the Microsoft Teams Rooms Premium managed service

To enroll a Microsoft Teams Rooms device in the Teams Rooms Premium managed service, you need to assign one or more users to the Managed Service Administrator and then complete the enrollment steps using that user.

## Assign users to the Managed Service Administrator role

Complete the following steps to assign users to the Managed Service Administrator role:

1. Log in to the [Teams Rooms Premium portal](https://portal.rooms.microsoft.com/) with the same administrator privileges as that used to log in to the Microsoft 365 admin center.
2. Navigate to **Settings** > **Settings** > **Roles** and then select **Managed Service Administrator**.
3. Under **Managed Service Administrator**, select the **Assignments** tab and then select **Add**.
4. Follow the wizard to name the assignment and select the users who should be added to it. The assignment will apply to all rooms and room groups.
5. At the end of the assignment wizard, select **Add assignment**.

Users who are assigned the Managed Service Administrator role are responsible for the day-to-day management and monitoring of the Teams Rooms Premium managed service portal.

After you've assigned users to the Managed Service Administrator role, continue to the [Enroll a Teams Rooms device](enroll-a-device.md) to add a Teams Rooms device to the managed service portal.

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
