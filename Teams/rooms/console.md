---
title: Create a Teams Rooms for Windows image
ms.author: tonysmit
author: mstonysmith
ms.reviewer: Travis-Snoozy
manager: pamgreen
ms.date: 08/21/2024
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
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: This article describes how to create and apply Microsoft Teams Room for Windows installation media.
---

# Overview - Microsoft Teams Room for Windows image

This article describes how to build a Microsoft Teams Rooms image of Teams Rooms.

> [!IMPORTANT]
> The information in this article is intended for test environments or for organizations that have very specific and uncommon deployment blockers that prevent the usage of OEM-supplied images or recovery media. Before following the information in this article, we strongly recommend that you discuss your specific Teams Rooms deployment with your Microsoft representative.
> [!NOTE]
> The following steps should only be used when creating a [WIM-based image](/windows-hardware/manufacture/desktop/capture-and-apply-an-image) for mass deployment. If you are recovering individual devices, contact your Original Equipment Manufacturer (OEM) for support.

## Prepare the installation media
<a name="Prep_Media"> </a>

Creating the Microsoft Teams Rooms installation media requires a USB storage device with at least 32 GB of capacity. There should be no other files on the device; any existing files on the USB storage will be lost. The script requires that a specific Windows ISO be supplied in order to generate the installation media. That ISO is available only through [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/).

> [!NOTE]
> Failure to create your Microsoft Teams Rooms installation media according to these instructions will likely result in unexpected behavior.

> [!NOTE]
> The process below is for creating installation media to image new Microsoft Teams Rooms devices. Existing devices, by default, update automatically from Windows Update and the Windows Store.

1. Download the [CreateSrsMedia.ps1 script](https://go.microsoft.com/fwlink/?linkid=867842).
2. Run the CreateSrsMedia.ps1 script from an elevated prompt on a Windows machine.
3. Follow the script's instructions to create a Microsoft Teams Rooms USB setup disk.

> [!TIP]
> Each time the CreateSrsMedia.ps1 script starts, the screen output will include the name of a log file or transcript for the session. If there are issues with running the script, make sure to have a copy of that transcript available when requesting support.

When finishes, you can safely eject and remove the USB disk from your computer and proceed to [Install Windows and the Microsoft Teams Rooms console app](console.md#Reimage).

## Install Windows and the Microsoft Teams Rooms console app
<a name="Reimage"> </a>

You now need to apply the installation media you've created. The target device runs as an appliance and the default user will be set to only run the Microsoft Teams Rooms app.

> [!IMPORTANT]
> Installation is supported only on [certified Microsoft Teams Rooms on Windows hardware](certified-hardware.md?tabs=Windows). Microsoft will not provide any support for non-certified hardware, even if installation succeeds.

1. If the target device will be installed in a dock (for example, a Surface Pro), disconnect it from the dock.
2. Ensure the target device isn't connected to the network.
3. Ensure the target device is connected to AC power.
4. Plug your USB setup disk into the target device.
5. Boot to the USB setup disk. Refer to the manufacturer instructions. If your target device is a Surface Pro, use the following steps to boot to the USB setup disk:

    a. Press and continue to hold the volume down (-) button.
    b. Press and release the power button.
    c. Once Windows setup is booted, release the volume down (-) button.

6. The system shuts down once installation is complete.

After the system has shut down, it's safe to remove the USB installation media. A drive image can now be captured from this device, for use in bulk deployment of identical hardware if necessary.

## See also

[Plan for Microsoft Teams Rooms](rooms-plan.md)
  
[Deploy Microsoft Teams Rooms](rooms-deploy.md)
  
[Configure a Microsoft Teams Rooms console](console.md)
  
[Manage Microsoft Teams Rooms](rooms-manage.md)

