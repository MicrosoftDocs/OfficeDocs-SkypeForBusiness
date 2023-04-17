---
title: Microsoft Teams Rooms requirements
ms.author: dstrome
author: dstrome
ms.reviewer: sohailta
ms.date: 04/06/2018
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
ms.subservice: itpro-rooms
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.assetid: 6b2b2684-8e9e-49ea-8c46-1c690964f982
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
  - Tier3
description: Learn about the requirements for supporting Microsoft Teams Rooms, including choosing the appropriate device, microphones, speakers, cameras, and displays.
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams Rooms requirements

Microsoft Teams Rooms scale to different room sizes. Teams Rooms use a wide variety of certified audio and video peripherals based on the size and use of the room. By selecting the right core device and console, combined with microphones, speakers, cameras, and displays appropriate for the space, you can deploy Microsoft Teams Rooms into spaces of any size, from small huddle spaces up through large conference spaces and boardrooms. The full set of all available certified audio and video peripherals that may be used to configure your room is available in the [Device Showcase](https://products.office.com/microsoft-teams/across-devices).

This article summarizes the device deployment and configuration requirements for supporting Microsoft Teams Rooms.

Your deployment involves resource account creation and setup of Teams Rooms as described in [Deploy Microsoft Teams Rooms](rooms-deploy.md).

For more information, see [License options based on your plan: Microsoft Teams Rooms](rooms-licensing.md).

> [!NOTE]
> Microsoft Teams Rooms sign in to Microsoft Teams, Skype for Business Server 2019, or Skype for Business Server 2015 and may join meetings hosted by any of these services.
>
> Earlier platforms like Lync Server 2013 aren't supported by Microsoft Teams Rooms. Microsoft Teams Rooms is not supported in Microsoft 365 or Office 365 operated by 21Vianet, or DoD environments.
>
> If you have an on-prem Exchange server, Microsoft Teams Rooms requires the use of Exchange Server 2013 SP1 or later.

## Supported Microsoft Teams Rooms systems and peripherals

For a list of Windows and Android-based devices, and peripherals, that are certified for use with Teams Rooms systems, see [Teams Rooms certified hardware](certified-hardware.md).

## Wireless network considerations

We strongly recommend that you connect your Teams Rooms devices to a wired network for greater stability and performance, ensuring a seamless meeting experience. If using a wired connection is not available, you may opt to use a wireless connection.

> [!IMPORTANT]
> Wireless networks can be prone to network interference leading to quality degradation. We strongly recommend that you follow your wireless equipment provider's best practices when configuring a wireless connection to improve video and audio quality.

Here are some examples of wireless network configuration best practices recommended by various manufacturers:

- Deploy wireless equipment, such as access points and routers, that can handle and distribute the bandwidth load across all connected devices in the network.
- As much as possible, use access points and routers from a single manufacturer to avoid further congesting the radio-spectrum.
- Ensure wireless equipment is installed in a way that reduces or eliminates inference from objects and other equipment.
- Ensure the wireless network shows strong signal strength (Wi-Fi signal showing full bars is preferred) on Teams Rooms and other device screens.
- Default to prioritizing 5 GHz coverage for devices to optimize for higher bandwidth.
- Enable band steering to ensure that 5 GHz is always given more priority when sharing the same network name (SSID) as 2.4 GHz.
- Keep wireless channel utilization below 50%.
- Keep access point and router firmware up to date with the latest firmware versions and hot fixes.
- Verify that Teams Rooms devices and at least one access point see each other with a signal strength of -60 dBm or better. A dBm value closer to zero is preferred. Follow your equipment manufacturer's recommendations.
- Implement QoS whenever possible to allow monitoring and resolution of issues in real time.

For additional best practices specific to your wireless network hardware, check your manufacturer's documentation.

You can also troubleshoot wireless network issues using the wireless network report built into Windows 10. For more information, see [Analyze the wireless network report - Microsoft Support](https://support.microsoft.com/windows/analyze-the-wireless-network-report-76da0daa-1db2-6049-d154-7bb679eb03ed).

## See also

[Browse All Bundles](https://products.office.com/microsoft-teams/across-devices/devices)

[Plan for Microsoft Teams Rooms](rooms-plan.md)

[Deploy Microsoft Teams Rooms](rooms-deploy.md)

[Configure a Microsoft Teams Rooms console](console.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)
