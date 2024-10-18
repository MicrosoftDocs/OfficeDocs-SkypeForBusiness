---
title: Prepare your network for Team phones
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: prashibadkur
ms.date: 10/16/2024
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
search.appverid: MET150
description: Learn about how to prepare your network infrastructure for deploying Microsoft Teams phones so that you can take advantage of all of the available features.
---

# Plan your network environment for Teams Phones

This section contains an overview of the steps required to prepare your network environment so that you can use all of the features of Microsoft Teams phones. This section also includes information on configuring local administive access to your Teams phones.
  
## Confirm network configuration

In order to function properly, Microsoft Phone devices must have access to a network that meets these requirements:
  
- Review access to: Microsoft Teams, Intune, Microsoft Entra ID, & Microsoft Common destinations. Open required ports to the required destinations documented in [Teams Android Device - Network Security](/microsoftteams/rooms/security?tabs=Android#network-security)

- Review network bandwidth and quality of service (QoS) requirements: [QoS on Teams Phones](/microsoftteams/devices/qos-on-teams-phones)

- Review if your organization utilizes a proxy, you need the proxy address or proxy autoconfiguration (PAC) file url

- Review if your organization utilizes certificates for network access, you need the certificates for a successful setup

> [!IMPORTANT]
> Be sure to use a network connection with enough bandwidth (we recommend 100 kbps up/down per Teams Phone) to ensure your calls perform well.

### Certificates

Your Microsoft Teams Phone device uses certificates for Microsoft Teams, network usage, and authentication. If the related servers use public certificates, which is the case for online, there should be no further action required on the part of the admin to install certificates. If, on the other hand, the certificate authority is a private CA then the device needs to trust that CA. This means having the CA + CA chain certificates installed on the device. Certificates can be installed via Intune or via OEM tooling.

### Proxy

> [!IMPORTANT]
> Microsoft Teams Phones does not support proxy authentication as it may interfere with regular operations of the room. Ensure that Microsoft Teams Phones have been exempted from proxy authentication before going into production. If your proxy server utilizes internally signed certificates, you must install the internal certificate chain, including the root CA, on the Microsoft Teams Phone.

Proxy settings on Teams Phones vary by device manufacturer. Consult OEM documentation for how to best configure Teams Phone devices for a network with a proxy.

## Wireless network considerations

We strongly recommend that you connect your Teams Rooms devices to a wired network for greater stability and performance, ensuring a seamless meeting experience. If using a wired connection isn't available, you may opt to use a wireless connection.

> [!IMPORTANT]
> Wireless networks can be prone to network interference leading to quality degradation. We strongly recommend that you follow your wireless equipment provider's best practices when configuring a wireless connection to improve video and audio quality.

Here are some examples of wireless network configuration best practices recommended by various manufacturers:

- Deploy wireless equipment, such as access points and routers, that can handle and distribute the bandwidth load across all connected devices in the network.
- As much as possible, use access points and routers from a single manufacturer to avoid further congesting the radio-spectrum.
- Ensure wireless equipment is installed in a way that reduces or eliminates interference from objects and other equipment.
- Ensure the wireless network shows strong signal strength (Wi-Fi signal showing full bars is preferred) on Teams Rooms and other device screens.
- Default to prioritizing 5-GHz coverage for devices to optimize for higher bandwidth.
- Enable band steering to ensure that 5 GHz is always given more priority when sharing the same network name as 2.4 GHz.
- Keep wireless channel utilization below 50%.
- Keep access point and router firmware up to date with the latest firmware versions and hot fixes.
- Verify that Teams Rooms devices and at least one access point see each other with a signal strength of -60 dBm or better. A dBm value closer to zero is preferred. Follow your equipment manufacturer's recommendations.
- Implement QoS whenever possible to allow monitoring and resolution of issues in real time.

For more best practices specific to your wireless network hardware, check your manufacturer's documentation.

## Tenant Restrictions

For organizations which utilize [tenant restrictions](/entra/identity/enterprise-apps/tenant-restrictions) features of Microsoft Entra ID, this is supported on some Teams Devices if your organization utilizes the proxy deployment variant with header injection. However, tenant restrictions aren't supported today on Teams Phone devices. Consult with your Android device OEM for potential workarounds.

## Device administrative access

Local administrative access to Teams Phone devices is controlled by the Teams device equipment manufacturer. Consult the device documentation for default accounts and passwords and instructions for how to change those passwords.
