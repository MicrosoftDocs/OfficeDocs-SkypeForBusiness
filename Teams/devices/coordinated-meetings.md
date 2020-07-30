---
title: "Set up coordinated meetings with Microsoft Teams Rooms and Surface Hub"
ms.author: dstrome
author: dstrome
ms.reviewer: rahulmi
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
localization_priority: Normal
description: "Configure Teams Rooms devices and Surface Hub to join meetings when one device or the other joins a meeting."
---

# Set up Coordinated Meetings with Microsoft Teams Rooms and Surface Hub

If you have one or more Microsoft Teams Rooms devices or Surface Hubs in a meeting room, you can set up Coordinated Meetings. Coordinated Meetings lets you set up your Teams Rooms devices and Surface Hubs so that when you join a meeting on one device, the other devices in the room are also joined to the same meeting. You can configure your cameras, speakers, and microphones so that the ones that give participants the best experience are enabled while others are disabled. This avoids the dreaded echo and feedback noise participants can experience when adding multiple devices to a meeting.

To set up Coordinated Meetings, you need to make sure your Teams Rooms devices and Surface Hubs are already correctly configured to participate in meetings. Most importantly, each device needs to have its own Exchange room mailbox. For information on how to set them up, see the following articles:

- [Deploy Microsoft Teams Rooms](../rooms/rooms-deploy.md)
- [Create Surface Hub 2S device account](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)

After you've confirmed that your Teams Rooms devices and Surface Hubs can automatically accept meetings and join them successfully, you can set up Coordinated Meetings.

The following steps should be completed for each meeting room separately. Devices in one meeting room shouldn't be set up for Coordinated Meetings with devices in other meeting rooms. 

## Step 1: Plan your Coordinated Meeting experience

Before you make any configuration changes, you need to decide which devices will do what in each meeting room. That is, for a given meeting room, you need to decide which device will have the active microphone, camera, and whiteboard. You don't need to choose a single device. For example, you could enable the microphone on a Teams Rooms device but enable the camera on your Surface Hub. How you configure your devices depends on your specific environment, but here are some general recommendations to start with:

- **Microphone** Teams Rooms device
- **Camera** Teams Rooms device or Surface Hub
- **Whiteboard** Surface Hub

> [!IMPORTANT]
> Make sure you enable the microphone only on one device. If you enable it on more than one device, you'll experience audio echo and feedback.

## Step 2: Get your devices' UPNs

In addition to making the decisions above, you also need to get the user principal names (UPNs) of each of the devices you want to configure for Coordinated Meetings. For each device that will participate in Coordinated Meetings in a meeting room, you need to tell the other devices in the same room to trust it. This is done by adding the UPN of trusted devices to each device.

## Step 2: Configure Teams Rooms

## Step 3: Configure Surface Hub

To make the necessary changes to set up Coordinated Meetings on Surface Hub, you need to use Windows Configuration Designer or Microsoft Intune. For more information about these options, see the following articles:

- [Create a provisioning package for Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)
- [What is Microsoft Intune device management?](https://docs.microsoft.com/mem/intune/remote-actions/device-management)

