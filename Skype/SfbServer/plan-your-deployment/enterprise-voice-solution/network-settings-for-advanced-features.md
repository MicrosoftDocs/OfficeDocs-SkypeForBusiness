---
title: "Network settings for the advanced Enterprise Voice features in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 7f6de9e4-c8a4-44e4-8d14-21fe8c45283a
description: "Learn about network regions, network sites, and IP subnets. All these must be configured to deploy Plan for media bypass in Skype for Business, Plan for call admission control in Skype for Business Server), or Plan for emergency services in Skype for Business Server in Skype for Business Server Enterprise Voice."
---

# Network settings for the advanced Enterprise Voice features in Skype for Business Server

Learn about network regions, network sites, and IP subnets. All these must be configured to deploy [Plan for media bypass in Skype for Business](media-bypass.md), [Plan for call admission control in Skype for Business Server](call-admission-control.md), or [Plan for emergency services in Skype for Business Server](emergency-services.md) in Skype for Business Server Enterprise Voice.

Skype for Business Server has three advanced Enterprise Voice features: [Plan for call admission control in Skype for Business Server](call-admission-control.md), [Plan for emergency services in Skype for Business Server](emergency-services.md), and [Plan for media bypass in Skype for Business](media-bypass.md). These features share certain configuration requirements for network regions, network sites, and association of each subnet in the Skype for Business Server topology with a network site.

This topic provides an overview of the configuration requirements that are common to all three of these advanced Enterprise Voice features.

## Network Regions

A network region is a network hub or network backbone used only in the configuration of call admission control (CAC), E9-1-1, and media bypass.

> [!NOTE]
> Network regions are not the same as Skype for Business Server dial-in conferencing regions, which are required to associate dial-in conferencing access numbers with one or more Skype for Business Server dial plans. For details about dial-in conferencing regions, see [Planning for Dial-In Conferencing](https://technet.microsoft.com/library/9aff949e-3dac-481a-be46-a180c72e8066.aspx).

CAC requires that every network region have an associated Skype for Business Server central site, which manages media traffic within the region (that is, it makes decisions based on policies that you have configured, regarding whether or not a real-time audio or video session can be established). Skype for Business Server central sites do not represent geographical locations, but rather logical groups of servers that are configured as a pool or a set of pools.

To configure a network region, you can either use the **Regions** tab on the **Network Configuration** section of Skype for Business Server Control Panel, or run the **New-CsNetworkRegion** or **Set-CsNetworkRegion** Skype for Business Server Management Shell cmdlets. For instructions, see [Deploy network regions, sites and subnets in Skype for Business](../../deploy/deploy-enterprise-voice/deploy-network.md) in the Deployment documentation, or refer to the Skype for Business Server Management Shell documentation.

The same network region definitions are shared by all three advanced Enterprise Voice features. If you have already created network regions for one feature, you do not need to create new network regions for the other features. You may, however, need to modify an existing network region definition to apply feature-specific settings. For example, if you have created network regions for E9-1-1 (which do not require an associated central site) and, later, you deploy call admission control, you must modify each of the network region definitions to specify a central site.

To associate a Skype for Business Server central site with a network region, you specify the central site name, either by using the **Network Configuration** section of Skype for Business Server Control Panel, or by running the **New-CsNetworkRegion** or **Set-CsNetworkRegion** cmdlets. For instructions, see [Deploy network regions, sites and subnets in Skype for Business](../../deploy/deploy-enterprise-voice/deploy-network.md) in the Deployment documentation, or refer to the Skype for Business Server Management Shell documentation.

## Network Sites

A network site represents a geographical location, such as a branch office, a regional office, or a main office. Each network site must be associated with a specific network region.

> [!NOTE]
> Network sites are used only by the advanced Enterprise Voice features. They are not the same as the branch sites that you configure in your Skype for Business Server topology.

To configure a network site and associate it with a network region, you can either use the **Network Configuration** section of Skype for Business Server Control Panel, or run the Skype for Business Server Management Shell **New-CsNetworkSite** or **Set-CsNetworkSite** cmdlets. For details, see [Create or Modify a Network Site](https://technet.microsoft.com/library/14e24856-9996-4da4-9f31-300940bdf5aa.aspx) in the Deployment documentation, or refer to the Skype for Business Server Management Shell documentation.

## Identify IP Subnets

For each network site, you will need to work with your network administrator to determine which IP subnets are assigned to each network site. If your network administrator has already organized the IP subnets into network regions and network sites, then your work is significantly simplified.

For example, the New York site in the North America region can be assigned the following IP subnets: 172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24. If Bob, who usually works in Detroit, travels to the New York office for training, turns on his computer and connects to the network, his computer will get an IP address in one of the four ranges that are allocated for New York—for example, 172.29.80.103.

> [!CAUTION]
> The IP subnets specified during network configuration on the server must match the format that is provided by client computers in order to be properly used for media bypass. A Skype for Business client takes its local IP address and masks the IP address with the associated subnet mask. When determining the bypass ID associated with each client, the Registrar will compare the list of IP subnets associated with each network site against the subnet that is provided by the client for an exact match. For this reason, it is important that subnets entered during network configuration on the server are actual subnets instead of virtual subnets. (If you deploy call admission control, but not media bypass, call admission control will function properly even if you configure virtual subnets.) For example, if a Skype for Business client signs in on a computer with an IP address of 172.29.81.57 with an IP subnet mask of 255.255.255.0, it will request the bypass ID that is associated with subnet 172.29.81.0. If the subnet is defined as 172.29.0.0/16, although the client belongs to the virtual subnet, the Registrar will not consider this a match because the Registrar is specifically looking for subnet 172.29.81.0. Therefore, it is important that the administrator enters subnets exactly as provided by Skype for Business clients (which are provisioned with subnets during network configuration, either statically or by Dynamic Host Configuration Protocol (DHCP).)

## Associating Subnets with Network Sites

Every subnet in the enterprise network must be associated with a network site (that is, every subnet needs to be associated with a geographic location). This association of subnets enables the advanced Enterprise Voice features to locate the endpoints geographically. For example, locating the endpoints enables CAC to regulate the flow of real-time audio and video data going to and from the network site.

To associate subnets with network sites, you can either use the **Network Configuration** section of Skype for Business Server Control Panel, or you can use the Skype for Business Server Management Shell. For instructions, see [Associate a Subnet with a Network Site](https://technet.microsoft.com/library/aa69e3ac-542a-4ba1-9582-2e6bee29f633.aspx) in the Deployment documentation, or refer to the Skype for Business Server Management Shell documentation.

## See also

[Plan for call admission control in Skype for Business Server](call-admission-control.md)

[Plan for emergency services in Skype for Business Server](emergency-services.md)

[Plan for media bypass in Skype for Business](media-bypass.md)

