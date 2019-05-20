---
title: 'Managing Quality of Service (QoS)'
ms.reviewer: 
ms:assetid: ab1051c3-8380-4d72-86df-37a61b1e4a41
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg405409(v=OCS.15)
ms:contentKeyID: 48185049
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Quality of Service (QoS) is a networking technology used in some organizations to help provide an optimal end-user experience for audio and video communications."
---

# Managing Quality of Service (QoS) in Skype for Business Server


Quality of Service (QoS) is a networking technology used in some organizations to help provide an optimal end-user experience for audio and video communications. QoS is most-commonly used on networks where bandwidth is limited: with a large number of network packets competing for a relatively small amount of available bandwidth, Quality of Service provides a way for administrators to assign higher priorities to packets carrying audio or video data. By giving these packets a higher priority, audio and video communications are likely to complete faster, and with less interruption, than network sessions involving things like file transfers, web browsing, or database backups. That's because network packets used for file transfers or database backups are assigned a "best effort" priority.


> [!NOTE]  
> As a general rule, Quality of Service applies only to communication sessions on your internal network. When you implement QoS, you configure your servers and routers to support packet marking; however, you configure these devices to support packet marking in a particular manner. You cannot assume that Quality of Service will be supported on the Internet or on other networks. Even if Quality if Service is supported on other networks, there is no guarantee that QoS will be configured the same way that you configured the service on your network.

Skype for Business Server does not require Quality of Service; if you do not currently use QoS there is no requirement that you install the service before installing Skype for Business Server. If you experience a considerable amount of packet loss on your network the recommended way to alleviate this problem is to add additional bandwidth. If adding more bandwidth is not possible, then you might want to implement Quality of Service instead.

Skype for Business Server offers full support for Quality of Service: that means that organizations that are already using QoS can easily integrate Skype for Business Server into their existing network infrastructure. In order to do this you must perform the following tasks:

  - [Enabling QoS for devices that are not based on Windows](enabling-qos-for-devices-that-are-not-based-on-windows.md). By default, QoS is disabled for computers and other devices (such as iPhones) that run other operating systems. Although you can use Skype for Business Server to enable and disable Quality of Service for devices, you typically cannot use the product to modify the DSCP codes used by these devices.

  - [Configuring port ranges and a Quality of Service policy for your Conferencing, Application, and Mediation servers](configuring-port-ranges-for-your-conferencing-application-and-mediation-servers.md). You must reserve a unique set of ports for different packet types, such as audio and video. With Skype for Business Server you do not enable or disable Quality of Service by, say, setting a property value to True or to False. Instead, you enable Quality of Service by configuring port ranges and then creating and applying Group Policy. If you later decide not to use QoS you can “disable” Quality of Service simply by removing the appropriate Group Policy objects.

  - [Configuring port ranges and a Quality of Service policy for your Edge Servers](configuring-port-ranges-for-your-edge-servers.md). Although not required, you can configure your Edge servers to use the same port ranges as your other servers. Configuring a Quality of Service policy should only be done for the internal side of your Edge servers. That's because Quality of Service is designed for use on your internal network and not on the Internet.

- [Configuring port ranges and a Quality of Service policy for your clients in Skype for Business Server](configuring-port-ranges-for-your-skype-clients.md)  These port ranges apply only to client computers and are typically different from the port ranges configured on your servers. Note that Skype for Business Server does not support QoS for Windows operating systems other than Windows 10.


