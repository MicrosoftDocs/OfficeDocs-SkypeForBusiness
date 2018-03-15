---
title: "Configuring Enterprise Voice in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7df179fa-d3a2-4b23-a433-b750aedf980b
description: "In this articleCreate a TrunkDefines Voice PoliciesDefine Voice RoutesEnable Users for Enterprise Voice"
---

# Configuring Enterprise Voice in Lync Server 2013
[]
 **In this article**
  
[Create a Trunk](#sectionSection0)
  
[Defines Voice Policies](#sectionSection1)
  
[Define Voice Routes](#sectionSection2)
  
[Enable Users for Enterprise Voice](#sectionSection3)
  
To deploy Enterprise Voice, you'll need to configure the following:
  
- Create a Trunk
    
- Define a Voice Policy
    
- Define a Voice Route
    
- Enable Users for Enterprise Voice
    
## Create a Trunk
<a name="sectionSection0"> </a>

You must define trunks in your Enterprise Voice deployment. For Location-Based Routing, you must create a trunk configuration per trunk. Use the Lync Server Topology Builder to define your trunks, and use the Lync Server Windows PowerShell command, New-CsTrunkConfiguration, or the Lync Server Control Panel to define the corresponding trunk configurations. More information on how to enable Location-Based Routing on trunk configurations can be found in the section, Enable Location-Based Routing to Trunks, in the topic, [Enabling Location-Based Routing in Lync Server 2013](enabling-location-based-routing.md). For this example, the following table illustrates the trunks used in this scenario.
  
For more information, see [Define additional trunks in Topology Builder in Lync Server 2013](define-additional-trunks-in-topology-builder.md).
  
****

|**Trunk name**|**System type**|**Name**|**Location**|**Mediation Server**|
|:-----|:-----|:-----|:-----|:-----|
|Trunk 1 DEL-GW  <br/> |PSTN gateway  <br/> |DEL-GW  <br/> |Delhi  <br/> |MS1  <br/> |
|Trunk 2 HYD-GW  <br/> |PSTN gateway  <br/> |HYD-GW  <br/> |Hyderabad  <br/> |MS1  <br/> |
|Trunk 3 DEL-PBX  <br/> |PBX  <br/> |DEL-PBX  <br/> |Delhi  <br/> |MS1  <br/> |
|Trunk 4 HYD-PBX  <br/> |PBX  <br/> |HYD-PBX  <br/> |Hyderabad  <br/> |MS1  <br/> |
   
## Defines Voice Policies
<a name="sectionSection1"> </a>

You must define voice policies for your Enterprise Voice deployment. Define a Voice Policy to enforce Location-Based Routing restrictions to a subset of users if only a subset of them is required to use Location-Based Routing. For this example, the following table illustrates the voice policies used in this scenario. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.
  
For more information, see [Configuring voice policies and PSTN usage records to authorize calling features and privileges in Lync Server 2013](configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features.md).
  
****

||**Voice policy 1**|**Voice policy 2**|
|:-----|:-----|:-----|
|Voice policy ID  <br/> |Delhi voice policy  <br/> |Hyderabad voice policy  <br/> |
|PSTN usages  <br/> |Delhi usage, PBX Del usage, PBX Hyd usage  <br/> |Hyderabad usage, PBX Hyd usage, PBX Del usage  <br/> |
|PreventPSTNTollBypass  <br/> |False  <br/> |False  <br/> |
   
## Define Voice Routes
<a name="sectionSection2"> </a>

You must define voice routes for your Enterprise Voice deployment. For this example, the following table illustrates the voice routes used in this scenario. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.
  
For more information, see [Configuring voice routes for outbound calls in Lync Server 2013](configuring-voice-routes-for-outbound-calls.md).
  
****

||**Voice route 1**|**Voice route 2**|**Voice route 3**|**Voice route 4**|
|:-----|:-----|:-----|:-----|:-----|
|Name  <br/> |Delhi route  <br/> |Hyderabad route  <br/> |PBX Del route  <br/> |PBX Hyd route  <br/> |
|PSTN usages  <br/> |Delhi usage  <br/> |Hyderabad usage  <br/> |PBX Del usage  <br/> |PBX Hyd usage  <br/> |
|Trunk  <br/> |Trunk 1 DEL-GW  <br/> |Trunk 2 HYD-GW  <br/> |Trunk 3 DEL-PBX  <br/> |Trunk 4 HYD-PBX  <br/> |
   
## Enable Users for Enterprise Voice
<a name="sectionSection3"> </a>

Enable users for Enterprise Voice and assign them a voice policy you've previously defined. For this example, the following table illustrates the assignment used in this scenario. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.
  
For more information, see [Enable users for Enterprise Voice in Lync Server 2013](enable-users-for-enterprise-voice.md).
  
****

||**Users located in Delhi**|**Users located in Hyderabad**|
|:-----|:-----|:-----|
|Associated voice policy  <br/> |Delhi voice policy  <br/> |Hyderabad voice policy  <br/> |
|Sample users  <br/> |DEL-LYNC-1,DEL-LYNC-2,DEL-LYNC-3  <br/> |HYD-LYNC-1, HYD-LYNC-2, HYD-LYNC-3  <br/> |
   
## See also
<a name="sectionSection3"> </a>

#### 

[Configuring Location-Based Routing in Lync Server 2013](configuring-location-based-routing.md)

