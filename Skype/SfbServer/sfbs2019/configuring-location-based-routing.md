---
title: "Configuring Location-Based Routing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 63cdc474-e80f-43b1-a237-9d9ed673300a
description: "Lync Server 2013 CU1, Location-Based Routing is a feature of Enterprise Voice. Location-Based Routing is a call management feature that controls how calls are routed by Lync Server 2013 CU1. It enforces restrictions on whether calls can be routed to PBX or PSTN destinations based on the Lync caller's location. Location-Based Routing applies call authorization rules to PSTN calls based on the caller's network location. The caller's location is determined based on the network site associated with the network subnet the caller is connected on. Configuring Location-Based Routing requires first deploying Enterprise Voice, then configuring network regions, sites and subnets. This sets up the foundation for enabling Location-Based Routing."
---

# Configuring Location-Based Routing in Lync Server 2013
[]
Lync Server 2013 CU1, Location-Based Routing is a feature of Enterprise Voice. Location-Based Routing is a call management feature that controls how calls are routed by Lync Server 2013 CU1. It enforces restrictions on whether calls can be routed to PBX or PSTN destinations based on the Lync caller's location. Location-Based Routing applies call authorization rules to PSTN calls based on the caller's network location. The caller's location is determined based on the network site associated with the network subnet the caller is connected on. Configuring Location-Based Routing requires first deploying Enterprise Voice, then configuring network regions, sites and subnets. This sets up the foundation for enabling Location-Based Routing.
  
Before deploying Location-Based Routing, you must first deploy Enterprise Voice, and configure network regions, sites, and associate network subnets to your network sites. Once completed, you can configure Location-Based Routing. For steps on how to configure network regions, sites and subnets, see [Deploying advanced Enterprise Voice features in Lync Server 2013](deploying-advanced-enterprise-voice-features.md)
  
This section guides you through the configuration of Location-Based Routing using the following example as illustration.
  
![Enterprise Voice location-based routing example](media/Deploy_LyncServer_Voice_LBR_example_topology.png)
  
The following table represents the users defined in this example.
  
****

|**Endpoint type**|**Location**|**Users**|
|:-----|:-----|:-----|
|Lync  <br/> |Delhi corporate office  <br/> |DEL-LYNC-1,DEL-LYNC-2,DEL-LYNC-3  <br/> |
|Lync  <br/> |Hyderabad corporate office  <br/> |HYD-LYNC-1, HYD-LYNC-2, HYD-LYNC-3  <br/> |
|Lync  <br/> |Unknown (i.e. hotel)  <br/> |UNK-LYNC-1  <br/> |
|PBX  <br/> |Delhi corporate office  <br/> |DEL-PBX-1, DEL-PBX-2  <br/> |
|PBX  <br/> |Hyderabad corporate office  <br/> |HYD-PBX-1, HYD-PBX-2  <br/> |
|PSTN  <br/> |Unknown  <br/> |PSTN-1, PSTN-2, PSTN-3  <br/> |
   
The following table represents the systems illustrated in this example environment.
  
****

|**System**|**Location**|**Name**|
|:-----|:-----|:-----|
|Lync Server 2013 CU1 pool  <br/> |any  <br/> |LS-PL1  <br/> |
|Lync Server 2013 CU1, Mediation Server  <br/> |any  <br/> |MS-PL1  <br/> |
|PSTN gateway 1  <br/> |Delhi  <br/> |DEL-GW  <br/> |
|PSTN gateway 2  <br/> |Hyderabad  <br/> |HYD-GW  <br/> |
|PBX 1  <br/> |Delhi  <br/> |DEL-PBX  <br/> |
|PBX 2  <br/> |Hyderabad  <br/> |RED-PBX  <br/> |
   
## In this section

- [Configuring Enterprise Voice in Lync Server 2013](configuring-enterprise-voice.md)
    
- [Deploying network regions, sites, and subnets in Lync Server 2013](deploying-network-regions-sites-and-subnets.md)
    
- [Enabling Location-Based Routing in Lync Server 2013](enabling-location-based-routing.md)
    
## See also

#### 

[Deploying advanced Enterprise Voice features in Lync Server 2013](deploying-advanced-enterprise-voice-features.md)

