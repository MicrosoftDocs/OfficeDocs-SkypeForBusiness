---
title: 'Lync Server 2013: Managing Quality of Service (QoS)'
ms.reviewer: 
TOCTitle: Managing Quality of Service (QoS)
author: kenwith
ms.author: kenwith
ms.manager: serdars
ms:assetid: ab1051c3-8380-4d72-86df-37a61b1e4a41
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg405409(v=OCS.15)
ms:contentKeyID: 48185049
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing Quality of Service (QoS) in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

Quality of Service (QoS) is a networking technology used in some organizations to help provide an optimal end-user experience for audio and video communications. QoS is most-commonly used on networks where bandwidth is limited: with a large number of network packets competing for a relatively small amount of available bandwidth, Quality of Service provides a way for administrators to assign higher priorities to packets carrying audio or video data. By giving these packets a higher priority, audio and video communications are likely to complete faster, and with less interruption, than network sessions involving things like file transfers, web browsing, or database backups. That's because network packets used for file transfers or database backups are assigned a "best effort" priority.

<div>


> [!NOTE]  
> As a general rule, Quality of Service applies only to communication sessions on your internal network. When you implement QoS, you configure your servers and routers to support packet marking; however, you configure these devices to support packet marking in a particular manner. You cannot assume that Quality of Service will be supported on the Internet or on other networks. Even if Quality if Service is supported on other networks, there is no guarantee that QoS will be configured the same way that you configured the service on your network.



</div>

Microsoft Lync Server 2013 does not require Quality of Service; if you do not currently use QoS there is no requirement that you install the service before installing Lync Server 2013. If you experience a considerable amount of packet loss on your network the recommended way to alleviate this problem is to add additional bandwidth. If adding more bandwidth is not possible, then you might want to implement Quality of Service instead.

Lync Server 2013 offers full support for Quality of Service: that means that organizations that are already using QoS can easily integrate Lync Server into their existing network infrastructure. In order to do this you must perform the following tasks:

  - [Enabling QoS in Lync Server 2013 for devices that are not based on Windows](lync-server-2013-enabling-qos-for-devices-that-are-not-based-on-windows.md). By default, QoS is disabled for computers and other devices (such as iPhones) that run other operating systems. Although you can use Lync Server to enable and disable Quality of Service for devices, you typically cannot use the product to modify the DSCP codes used by these devices.

  - [Configuring port ranges in Lync Server 2013 for your Conferencing, Application, and Mediation servers](lync-server-2013-configuring-port-ranges-for-your-conferencing-application-and-mediation-servers.md). You must reserve a unique set of ports for different packet types, such as audio and video. With Lync Server 2013 you do not enable or disable Quality of Service by, say, setting a property value to True or to False. Instead, you enable Quality of Service by configuring port ranges and then creating and applying Group Policy. If you later decide not to use QoS you can “disable” Quality of Service simply by removing the appropriate Group Policy objects.

  - [Configuring port ranges for your Edge Servers in Lync Server 2013](lync-server-2013-configuring-port-ranges-for-your-edge-servers.md). Although not required, you can configure your Edge servers to use the same port ranges as your other servers.

  - [Configuring port ranges for your Microsoft Lync clients in Lync Server 2013](lync-server-2013-configuring-port-ranges-for-your-microsoft-lync-clients.md). These port ranges apply only to client computers and are typically not the same as the port ranges configured on your servers.

  - [Configuring a Quality of Service policy in Lync Server 2013 for your Conferencing, Application, and Mediation servers](lync-server-2013-configuring-a-quality-of-service-policy-for-your-conferencing-application-and-mediation-servers.md). These policies determine the DSCP codes that are applied to different packet types.

  - [Configuring a Quality of Service policy for your A/V Edge Servers in Lync Server 2013](lync-server-2013-configuring-a-quality-of-service-policy-for-your-a-v-edge-servers.md). This should only be done for the internal side of your Edge servers. That's because Quality of Service is designed for use on your internal network and not on the Internet.

  - [Configuring Quality of Service policies in Lync Server 2013 for clients running on Windows 7 or Windows 8](lync-server-2013-configuring-quality-of-service-policies-for-clients-running-on-windows-7-or-windows-8.md). Note that Microsoft Lync Server 2013 does not support QoS for other Windows operating systems, such as Windows Vista or Windows XP.

  - [Configuring Quality of Service on Microsoft Lync Phone Edition devices in Lync Server 2013](lync-server-2013-configuring-quality-of-service-on-microsoft-lync-phone-edition-devices.md). By default, QoS is enabled for Lync Phone Edition devices. However, you might want to change the default DSCP value in order to ensure that all audio packets in your organization use the same DSCP code.

<div>


> [!NOTE]  
> If you are using Microsoft Windows Server 2012 or Windows Server 2012 R2 you might be interested in the new set of Windows PowerShell cmdlets available for managing Quality of Service on that platform. For more information, see Network Quality of Service Cmdlets in Windows PowerShell at [https://docs.microsoft.com/powershell/module/netqos/?view=winserver2012-ps](https://docs.microsoft.com/powershell/module/netqos/?view=winserver2012-ps).



</div>

</div>

<span> </span>

</div>

</div>

</div>

