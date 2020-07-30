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
- **Camera** Teams Rooms device and "allow users to activate" Surface Hub
- **Whiteboard** Surface Hub

> [!IMPORTANT]
> Make sure you enable the microphone only on one device. If you enable it on more than one device, you'll experience audio echo and feedback.

## Step 2: Get your devices' UPNs

When you set up a Coordinated Meeting experience in a meeting room, you need to tell the Teams Rooms devices and Surface Hubs in that room which devices to coordinate with. This is done by adding the user principal name (UPN) of the devices it should coordinate with to its configuration. If you don't know the UPNs for each of the devices you want to set up for Coordinated Meetings, you can find them using the Microsoft 365 admin center. 

You need to be assigned an admin role to access the Microsoft 365 admin center. For more information, see [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).

To get the UPNs of your Teams Rooms devices and Surface Hubs, do the following:

1. Sign in to the Microsoft 365 admin center by visiting https://admin.microsoft.com
2. Go to **Users** > **Active users**
3. Find the name of your Teams Rooms device or Surface Hub in the **Display name** column (you can use the **Search** box if you have many users)
4. Find the UPN in the **Username** column (it'll look something like alias@contoso.com or alias@contoso.onmicrosoft.com)
5. Repeat this for each device that will participate in Coordinated Meetings

## Step 3: Create a deployment worksheet

After you've planned your Coordinated Meeting experience and gathered a list of your devices' UPNs, it's a good idea to create a deployment worksheet. A deployment worksheet will help you visualize the configuration you want to set across all of your devices, allowing you to validate your choices and check for errors.

In a spreadsheet app, add rows for the following in the first column:

- **Audio default** Determines on which device the microphone will be active when a meeting starts. Only one device (typically a Teams Rooms device) can have this field set to `true` while the rest of the devices must have this field set to `false` to avoid audio echo and feedback.
- **Audio enabled** Determines whether participants in a meeting can toggle the microphone on or off. This should be set to `true` on the same device as **Audio default** to allow participants to mute the microphone as needed. The rest of the defaults should be set to `false` so that participants can't accidentally turn on a microphone and cause audio echo or feedback.
- **Video default** Determines on which device the camera will be active when a meeting starts. For the best experience, we recommend that only the Teams Rooms device be set to `true` while all other devices are set to `false`.
- **Video enabled** Determines whether participants in a meeting can toggle the camera on or off. This should be set to `true` on the same device as **Video default** to allow participants to turn off the camera as needed. You can also set this to `true` on any other devices in the event participants want to share different video perspectives (such as if a participant is using the Surface Hub whiteboard). If you don't want participants to turn a camera on or off on a device, set this to `false`.
- **Whiteboard default**
- **Whiteboard enabled**
- **Trusted accounts** This is a comma-separated list of UPNs for each Teams Room device or Surface Hub that the device should accept meeting join requests from, or to which meeting join requests should be sent.

In subsequent columns, add each of your Teams Rooms devices and Surface Hubs. In each column, fill out the values that correspond to the experience you want for the meeting room. Here's an example with three devices: one Teams Rooms device and two Surface Hubs:

- Audio and video are turned on and can be toggled on or off on the Teams Rooms device
- Audio is turned off and can't be toggled on either Surface Hubs
- Video is turned off but can be toggled on or off on both Surface Hubs
- Whiteboard is turned on only on Surface Hub 1 and can be toggled on or off on both Surface Hubs.


| Fields             | Teams Room                         | Surface Hub 1                      | Surface Hub 2                      |
|--------------------|------------------------------------|------------------------------------|------------------------------------|
| Audio default      | true                               | false                              | false                              |
| Audio enabled      | true                               | false                              | false                              |
| Video default      | true                               | false                              | false                              |
| Video enabled      | true                               | true                               | true                               |
| Whiteboard default | false                              | true                               | false                              |
| Whiteboard enabled | false                              | true                               | true                               |
| Trusted accounts   | hub1@contoso.com, hub2@contoso.com | room@contoso.com, hub2@contoso.com | room@contoso.com, hub1@contoso.com |



## Step 2: Configure Teams Rooms

## Step 3: Configure Surface Hub

To make the necessary changes to set up Coordinated Meetings on Surface Hub, you need to use Windows Configuration Designer or Microsoft Intune. For more information about these options, see the following articles:

- [Create a provisioning package for Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)
- [What is Microsoft Intune device management?](https://docs.microsoft.com/mem/intune/remote-actions/device-management)

