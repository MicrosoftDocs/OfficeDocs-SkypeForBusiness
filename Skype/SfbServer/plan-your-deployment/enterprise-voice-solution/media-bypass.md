---
title: "Plan for media bypass in Skype for Business"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 9ea090b3-f607-46f7-97dd-2510052524e5
description: "Decisions necessary for planning for media bypass in Skype for Business Server Enterprise Voice. Includes interoperation with call admission control (CAC)."
---

# Plan for media bypass in Skype for Business

Decisions necessary for planning for media bypass in Skype for Business Server Enterprise Voice. Includes interoperation with call admission control (CAC).

Media bypass refers to removing the Mediation Server from the media path whenever possible for calls whose signaling traverses the Mediation Server.

Media bypass can improve voice quality by reducing latency, needless translation, possibility of packet loss, and the number of points of potential failure. Scalability can be improved, because elimination of media processing for bypassed calls reduces the load on the Mediation Server. This reduction in load complements the ability of the Mediation Server to control multiple gateways.

 Where a branch site without a Mediation Server is connected to a central site by one or more WAN links with constrained bandwidth, media bypass lowers the bandwidth requirement by allowing media from a client at a branch site to flow directly to its local gateway without first having to flow across the WAN link to a Mediation Server at the central site and back.

By relieving the Mediation Server from media processing, media bypass may also reduce the number of Mediation Servers that an Enterprise Voice infrastructure requires. As a general rule, enable media bypass wherever possible.

The following figure shows basic media and signaling pathways in topologies with and without media bypass.

**Media and signaling pathways with and without media bypass**

![Voice CAC Media Bypass Connection Enforcement](../../media/Plan_CS_VoiceCAC_enforcementofconnectionstoPSTN.jpg)

Media bypass is useful when you want to minimize the number of Mediation Servers deployed. Typically, a Mediation Server pool will be deployed at a central site, and it will control gateways at branch sites. Enabling media bypass allows media for public switched telephone network (PSTN) calls from clients at branch sites to flow directly through the gateways at those sites. Skype for Business Server outbound call routes and Enterprise Voice policies must be properly configured so that PSTN calls from clients at a branch site are routed to the appropriate gateway.

Wi-Fi networks typically experience more packet loss than wired networks. Recovery from this packet loss is not typically something that can be accommodated by gateways. Therefore, we recommend that you evaluate the quality of a Wi-Fi network before determining whether bypass should be enabled for a wireless subnet. There is a tradeoff in latency reduction versus recovery from packet loss to consider, as well. RTAudio, a codec which is available for calls that do not bypass the Mediation Server, is better suited for handling packet loss.

## Planning your media bypass deployment

After your Enterprise Voice structure is in place, planning for media bypass is straightforward.

- If you have a centralized topology without WAN links to branch sites, you can enable global media bypass, because fine-tuned control is unnecessary.

- If you have a distributed topology that consists of one or more network regions and their affiliated branch sites, determine the following:

  - Whether your Mediation Server peers are able to support the capabilities required for media bypass.

  - Which sites in each network region are well-connected.

  - Which combination of media bypass and call admission control is appropriate for your network.

When you enable media bypass, a unique bypass ID is automatically generated for a network region, and for all network sites without bandwidth constraints within that region. Sites with bandwidth constraints within the region and sites connected to the region over WAN links with bandwidth constraints are each assigned their own unique bypass IDs.

When a user makes a call to the PSTN, the Mediation Server compares the bypass ID of the client subnet with the bypass ID of the gateway subnet. If the two bypass IDs match, media bypass is used for the call. If the bypass IDs do not match, media for the call must flow through the Mediation Server.

When a user receives a call from the PSTN, the user's client compares its bypass ID to that of the PSTN gateway. If the two bypass IDs match, media flows directly from the gateway to the client, bypassing the Mediation Server.

Only Lync 2010 or newer clients and devices support media bypass interactions with a Mediation Server.

> [!IMPORTANT]
> In addition to enabling media bypass globally, you must enable media bypass individually on each PSTN trunk. If bypass is enabled globally, but is not enabled for a particular PSTN trunk, media bypass will not be invoked for any calls involving that PSTN trunk. In addition, when media bypass is set to **Use Site and Region Information**, you must associate all routable subnets with the sites in which they are located. If there are routable subnets within a site for which bypass is not wanted, these subnets should be grouped within a new site before you enable media bypass. Doing so will assure that the unroutable subnets are assigned a different bypass ID.

## Media bypass modes

You must configure media bypass both globally and for each individual PSTN trunk. When enabling media bypass globally, you have two choices: **Always Bypass** and **Use Site and Region Information**.

As the name suggests, **Always Bypass** means that bypass will be attempted for all PSTN calls. **Always Bypass** is used for deployments where there is no need to enable call admission control, nor is there a need to specify detailed configuration information regarding when to attempt media bypass. Furthermore, **Always Bypass** is used when there is full connectivity between clients and PSTN gateways. In this configuration, all subnets are mapped to one and only one bypass ID, which is computed by the system.

With **Use Site and Region Information**, the bypass ID associated with site and region configuration is used to make the bypass decision. This configuration provides the flexibility to configure bypass for most common topologies, as it gives you fine-grained control over when bypass happens, in addition to supporting interactions with call admission control (CAC). The system tries to ease your task by automatically assigning bypass IDs as follows.

- The system automatically assigns a single unique bypass ID to each region.

- Any site connected to a region over a WAN link without bandwidth constraints inherits the same bypass ID as the region.

- A site associated with the region over a WAN link with constrained bandwidth is assigned a different bypass ID from that of the region.

- Subnets associated with each site inherit the bypass ID for that site.

## Media bypass and call admission control

Media bypass and call admission control (CAC) work together to manage bandwidth control for call media. Media bypass facilitates media flow over well-connected links; CAC manages traffic on links with bandwidth constraints. Because Media Bypass and CAC are mutually exclusive, you must be mindful of one when planning for the other. The following combinations are supported:

- CAC and Media Bypass are both enabled. Media Bypass must be set to **Use Site and Region Information**. This site and region information is the same as that used for CAC.

    If you enable CAC, you cannot select **Always Bypass**, and vice-versa, because the two configurations are mutually exclusive. That is, only one of the two will apply to any given PSTN call. First, a check is made to determine if media bypass applies to the call. If it does, then CAC is not used. This makes sense, because if a call is eligible for bypass, it is by definition using a connection where CAC is not needed. If bypass cannot be applied to the call (that is, if the client's and gateway's bypass IDs do not match), then CAC is applied to the call.

- CAC not enabled and Media Bypass set to **Always Bypass**.

    In this configuration, both client and trunk subnets are mapped to one and only one bypass ID, which is computed by the system.

- CAC not enabled and Media Bypass set to **Use Site and Region Information**.

    Where **Use Site and Region Information** is enabled, bypass determination works essentially the same way, regardless of whether CAC is enabled or not. That is, for any given PSTN call, the client's subnet is mapped to a particular site, and the bypass ID for that subnet is extracted. Similarly, the gateway's subnet is mapped to a particular site, and the bypass ID for that subnet is extracted. Only if the two bypass IDs are identical will bypass happen for the call. If they are not identical, media bypass will not occur.

    Even though CAC is disabled globally, bandwidth policy needs to be defined for each site and link if you want to use site-and-region configuration to control the bypass decision. The actual value of the bandwidth constraint or its modality doesn't matter. The ultimate goal is to have the system automatically calculate different bypass IDs to associate with different locales that are not well connected. Defining a bandwidth constraint by definition means a link is not well connected.

- CAC is enabled and media bypass is not enabled. This would apply only where all gateways and IP-PBXs are not well connected or do not meet other requirements for media bypass. For details about requirements for media bypass, see [Requirements for Media Bypass](https://technet.microsoft.com/library/6162a204-0e7c-460a-8eb2-e592c6590a8a.aspx).

## Technical requirements

For each call to the PSTN, the Mediation Server determines whether media from the Skype for Business endpoint of origin can be sent directly to a Mediation Server peer without traversing the Mediation Server. The peer can be a PSTN gateway, IP-PBX, or Session Border Controller (SBC) at an Internet telephony service provider (ITSP) that is associated with the trunk between the Mediation Server where the call is routed.

Media bypass can be employed when the following requirements are met:

- A Mediation Server peer must support the necessary capabilities for media bypass, the most important being the ability to handle multiple forked responses (known as "early dialogs"). Contact the manufacturer of your gateway or PBX, or your ITSP, to obtain the value for the maximum number of early dialogs that the gateway, PBX, or SBC can accept.

- The Mediation Server peer must accept media traffic directly from Skype for Business endpoints. Many ITSPs allow their SBC to receive traffic only from the Mediation Server. Contact your ITSP to determine whether its SBC accepts media traffic directly from Skype for Business endpoints.

- Skype for Business clients and a Mediation Server peer must be well connected, meaning that they are either located in the same network region or at network sites that connect to the region over WAN links that have no bandwidth constraints


