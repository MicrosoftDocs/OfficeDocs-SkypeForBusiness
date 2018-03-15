---
title: "Configure media bypass in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f50a7a13-c6a0-48f1-bee1-e45fa2b2f9b8
description: "This section assumes that you have already published and configured either at least one or more Mediation Servers (as described in Define a Mediation Server in Topology Builder in Lync Server 2013 and Publish the topology in Lync Server 2013, or in Define and configure a Front End pool or Standard Edition server in Lync Server 2013 and Publish the topology in Lync Server 2013, respectively, all in the Deployment documentation)."
---

# Configure media bypass in Lync Server 2013
[]
This section assumes that you have already published and configured either at least one or more Mediation Servers (as described in [Define a Mediation Server in Topology Builder in Lync Server 2013](define-a-mediation-server-in-topology-builder.md) and [Publish the topology in Lync Server 2013](publish-the-topology.md), or in [Define and configure a Front End pool or Standard Edition server in Lync Server 2013](define-and-configure-a-front-end-pool-or-standard-edition-server.md) and [Publish the topology in Lync Server 2013](publish-the-topology.md), respectively, all in the Deployment documentation).
  
This section also assumes that you have defined at least one gateway peer to provide PSTN connectivity, as described in [Define a gateway in Topology Builder in Lync Server 2013](define-a-gateway-in-topology-builder.md). If the peer you connect to is the SBC of a SIP trunking provider, make sure that the provider is a qualified provider and that the provider supports media bypass. For example, many SIP trunking providers will only allow their SBC to receive traffic from the Mediation Server. If so, then bypass must not be enabled for the trunk in question. Also, you cannot enable media bypass unless your organization reveals its internal network IP addresses to the SIP trunking provider.
  
> [!NOTE]
> Media bypass will not interoperate with every PSTN gateway, IP-PBX, and SBC. Microsoft has tested a set of PSTN gateways and SBCs with certified partners and has done some testing with Cisco IP-PBXs. Media bypass is supported only with products and versions listed on Unified Communications Open Interoperability Program - Lync Server at [https://go.microsoft.com/fwlink/p/?linkId=214406](https://go.microsoft.com/fwlink/p/?linkId=214406). 
  
This section describes how to enable media bypass to reduce the processing required of the Mediation Server. Before you enable media bypass, make sure that your environment meets the conditions required to support media bypass, as described in [Planning for media bypass in Lync Server 2013](planning-for-media-bypass.md) in the Planning documentation. Also make sure that you used the information in [Planning for media bypass in Lync Server 2013](planning-for-media-bypass.md) to decide whether to enable media bypass global settings to always bypass the Mediation Server or to use site and region information when determining whether to bypass the Mediation Server. 
  
If you have already optionally configured call admission control (CAC), another advanced Enterprise Voice feature, note that the bandwidth reservation performed by call admission control does not apply to any calls for which media bypass is employed. The verification of whether to employ media bypass is performed first, and if media bypass is employed, call admission control is not used for the call; only if the media bypass check fails is the check performed for call admission control. The two features are thus mutually exclusive for any particular call that is routed to the PSTN. This is the logic because media bypass assumes that bandwidth constraints do not exist between the media endpoints on a call; media bypass cannot be performed on links with restricted bandwidth. As a result, one of the following will apply to a PSTN call: a) media bypasses the Mediation Server, and call admission control does not reserve bandwidth for the call; or b) call admission control applies bandwidth reservation to the call, and media is processed by the Mediation Server involved in the call.
  
## Next Steps: Enable Media Bypass on the Trunk Connection

After configuring initial settings for PSTN connectivity (dial plans, voice policies, PSTN usage records, outbound call routes, and translation rules), begin the process of enabling media bypass by using the steps in [Configure a trunk with media bypass in Lync Server 2013](configure-a-trunk-with-media-bypass.md).
  
## See also

#### 

[Configure a trunk with media bypass in Lync Server 2013](configure-a-trunk-with-media-bypass.md)
  
[Configure media bypass in Lync Server 2013 to always bypass the Mediation Server](configure-media-bypass-to-always-bypass-the-mediation-server.md)
  
[Configure media bypass global settings in Lync Server 2013 to use site and region information](configure-media-bypass-global-settings-to-use-site-and-region-information.md)
#### 

[Global media bypass options in Lync Server 2013](global-media-bypass-options.md)
#### 

[Planning for media bypass in Lync Server 2013](planning-for-media-bypass.md)

