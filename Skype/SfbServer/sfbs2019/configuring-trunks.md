---
title: "Configuring trunks in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0c339511-a185-484e-94f0-dbe918b7e48a
description: "As part of Enterprise Voice deployment, you can configure a trunk between a Mediation Server and one or more of the following peers to provide public switched telephone network (PSTN) connectivity for Enterprise Voice clients and devices in your organization:"
---

# Configuring trunks in Lync Server 2013
[]
As part of Enterprise Voice deployment, you can configure a trunk between a Mediation Server and one or more of the following peers to provide public switched telephone network (PSTN) connectivity for Enterprise Voice clients and devices in your organization:
  
- SIP trunk connection to an Internet telephony service provider (ITSP)
    
- PSTN gateway
    
- Private branch exchange (PBX)
    
For details, see [Planning for PSTN connectivity in Lync Server 2013](planning-for-pstn-connectivity.md) in the Planning documentation. 
  
> [!IMPORTANT]
> Before you begin trunk configuration, verify that the topology has been created and that the Mediation Server and its peer have been configured and associated with one another. For details, see [Define a gateway in Topology Builder in Lync Server 2013](define-a-gateway-in-topology-builder.md) in the Deployment documentation. 
  
> [!NOTE]
> As a part of trunk configuration, you can enable the Lync Server 2013 media bypass feature, which enables media to bypass the Mediation Server. Trunks can be configured either with or without media bypass enabled, but we strongly recommend that you enable it. For details, see [Planning for media bypass in Lync Server 2013](planning-for-media-bypass.md) in the Planning documentation. 
  
## In this section

- [Multiple trunk support in Lync Server 2013](multiple-trunk-support.md)
    
- [Inter-trunk routing in Lync Server 2013](inter-trunk-routing.md)
    
- [View trunk configuration information in Lync Server 2013](view-trunk-configuration-information.md)
    
- [Configure a trunk with media bypass in Lync Server 2013](configure-a-trunk-with-media-bypass.md)
    
- [Configure a trunk without media bypass in Lync Server 2013](configure-a-trunk-without-media-bypass.md)
    
- [Create a new collection of trunk configuration settings in Lync Server 2013](create-a-new-collection-of-trunk-configuration-settings.md)
    
- [Delete an existing collection of SIP trunk configuration settings in Lync Server 2013](delete-an-existing-collection-of-sip-trunk-configuration-settings.md)
    
- [Modify SIP trunk configuration settings in Lync Server 2013](modify-sip-trunk-configuration-settings.md)
    
- [Test SIP trunk configuration settings in Lync Server 2013](test-sip-trunk-configuration-settings.md)
    
- [View information about individual SIP trunks in Lync Server 2013](view-information-about-individual-sip-trunks.md)
    
## See also

#### 

[Define a gateway in Topology Builder in Lync Server 2013](define-a-gateway-in-topology-builder.md)
#### 

[Planning for PSTN connectivity in Lync Server 2013](planning-for-pstn-connectivity.md)
  
[Planning for media bypass in Lync Server 2013](planning-for-media-bypass.md)

