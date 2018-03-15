---
title: "Enabling Location-Based Routing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 029ede7e-0c4e-4ad2-af99-909ae674d6fe
description: "In this articleEnable Location-Based Routing to Network SitesEnable Location-Based Routing to TrunksEnable Location-Based Routing to Voice PoliciesEnable Location-Based Routing in the routing configuration"
---

# Enabling Location-Based Routing in Lync Server 2013
[]
 **In this article**
  
[Enable Location-Based Routing to Network Sites](#sectionSection0)
  
[Enable Location-Based Routing to Trunks](#sectionSection1)
  
[Enable Location-Based Routing to Voice Policies](#sectionSection2)
  
[Enable Location-Based Routing in the routing configuration](#sectionSection3)
  
Once Enterprise Voice is deployed and network regions, sites and subnets are defined, you can enable Location-Based Routing. Location-Based Routing must be enabled for the following Enterprise Voice elements:
  
- Network sites
    
- Trunk configurations
    
- Voice policies
    
- Routing configuration
    
## Enable Location-Based Routing to Network Sites
<a name="sectionSection0"> </a>

After you have deployed Enterprise Voice, and configured network sites, you are ready to configure Location-Based Routing. First, you create a voice routing policy to associate the network site with the appropriate PSTN usages. When assigning PSTN usages to a voice routing policy, make sure to only use PSTN usages that are associated to voice routes that use a PSTN gateway local to the site or a PSTN gateway that is located in a region where Location-Based Routing restrictions are not needed.Use the Lync Server Windows PowerShell command, New-CsVoiceRoutingPolicy, or Lync Server Control Panel to create voice routing policies.
  
```
New-CsVoiceRoutingPolicy -Identity <voice routing policy ID> -Name <voice routing policy name> -PstnUsages <usages>
```

For more information, see [New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md).
  
For this example, the following table and Windows PowerShell commands illustrate two voice routing policies and their associated PSTN usages defined in this scenario. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.
  
```
New-CsVoiceRoutingPolicy -Identity "DelhiVoiceRoutingPolicy" -Name "Delhi voice routing policy" -PstnUsages @{add="Delhi usage", "PBX Del usage", "PBX Hyd usage"}
New-CsVoiceRoutingPolicy -Identity "HyderabadVoiceRoutingPolicy" -Name " Hyderabad voice routing policy" -PstnUsages @{add="Hyderabad usage", "PBX Del usage", "PBX Hyd usage"}
```

****

||**Voice routing policy 1**|**Voice routing policy 2**|
|:-----|:-----|:-----|
|Voice policy ID  <br/> |Delhi voice routing policy  <br/> |Hyderabad voice routing policy  <br/> |
|PSTN usages  <br/> |Delhi usage, PBX Del usage, PBX Hyd usage  <br/> |Hyderabad usage, PBX Hyd usage, PBX Del usage  <br/> |
   
Next, configure Location-Based Routing for the applicable network sites and associate your voice routing policies to them. Use the Lync Server Windows PowerShell command, New-CsNetworkSite, to enable Location-Based Routing and associate voice routing policies to your network sites that must enforce routing restrictions. 
  
```
Set-CsNetworkSite -Identity <site ID> -EnableLocationBasedRouting <$true|$false> -VoiceRoutingPolicy <voice routing policy ID>
```

In this example, the following table illustrates Location-Based Routing for two different network sites, Delhi and Hyderabad, defined in this scenario using the Lync Server Windows PowerShell. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.
  
```
Set-CsNetworkSite -Identity "Delhi" -EnableLocationBasedRouting $true -VoiceRoutingPolicy "DelhiVoiceRoutingPolicy"
Set-CsNetworkSite -Identity "Hyderabad" -EnableLocationBasedRouting $true -VoiceRoutingPolicy "HyderabadVoiceRoutingPolicy"
```

****

||**Site 1 (Delhi)**|**Site 2 (Hyderabad)**|
|:-----|:-----|:-----|
|Site Name  <br/> |Site 1 (Delhi)  <br/> |Site 2 (Hyderabad)  <br/> |
|EnableLocationBasedRouting  <br/> |True  <br/> |True  <br/> |
|Voice routing policy  <br/> |Delhi voice routing policy  <br/> |Hyderabad voice routing policy  <br/> |
|Subnets  <br/> |Subnet 1 (Delhi)  <br/> |Subnet 2 (Hyderabad)  <br/> |
   
## Enable Location-Based Routing to Trunks
<a name="sectionSection1"> </a>

Before a trunk configuration can be enabled for Location-Based Routing, you need to create a trunk configuration for each trunk or each network site. Use the Lync Server Windows PowerShell command, New-CsTrunkConfiguration, to create a trunk configuration. If multiple trunks are associated with a given system (i.e. Gateway or PBX), each trunk configuration must be modified to enable Location-Based Routing restrictions.
  
```
New-CsTrunkConfiguration -Identity < trunk configuration ID>
```

For more information, see [New-CsTrunkConfiguration](new-cstrunkconfiguration.md).
  
For this example, the following Windows PowerShell commands illustrate creating one trunk configuration for each trunk in the deployment defined in this scenario.
  
```
New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 1 DEL-GW>"
New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 2 HYD-GW>"
New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 3 DEL-PBX>"
New-CsTrunkConfiguration -Identity Service:PstnGateway:"<Trunk 4 HYD-PBX>"
```

Once a trunk configuration is configured per trunk, you can use the the Lync Server Windows PowerShell command, Set-CsTrunkConfiguration, to enable Location-Based Routing to your trunks that must enforce routing restrictions. Enable Location-Based Routing to trunks that route calls to PSTN gateways that route calls to the PSTN, and associate the network site where the gateway is located. 
  
```
Set-CsTrunkConfiguration -Identity <trunk configuration ID> -EnableLocationRestriction $true -NetworkSiteID <site ID>
```

For more information, see [New-CsTrunkConfiguration](new-cstrunkconfiguration.md).
  
In this example, Location-Based Routing is enabled for each trunk that is associated to PSTN gateways in Delhi and Hyderabad:
  
```
Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 1 DEL-GW -EnableLocationRestriction $true -NetworkSiteID "Delhi"
Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 2 HYD-GW -EnableLocationRestriction $true -NetworkSiteID "Hyderabad"
```

Do not enable Location-Based Routing for trunks that do not route calls to the PSTN; however, you must still associate the trunk to the network site where the system is located as Location-Based Routing restrictions need to be enforced for PSTN calls reaching endpoints connected via this trunk. For this example, Location-Based Routing is not enabled for each trunk that is associated to PBX systems in Delhi and Hyderabad:
  
```
Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 3 DEL-PBX -EnableLocationRestriction $false -NetworkSiteID "Delhi"
Set-CsTrunkConfiguration -Identity Service:PstnGateway:Trunk 4 HYD-PBX -EnableLocationRestriction $false -NetworkSiteID "Hyderabad"
```

Endpoints that are connected to systems that do not route calls to the PSTN (i.e. a PBX) will have similar restrictions as Lync endpoints of users enabled for Location-Based Routing. This means that these users will be able to place and receive calls to and from Lync user regardless of the user's location. They will also be able to place an receive calls to and from other systems that do not route calls to the PSTN network (i.e. an endpoint connected to a different PBX) regardless of the network site to which the system is associated. All inbound calls, outbound calls, call transfers and call forwarding involving PSTN endpoints will be subject to Location-Based Routing enforcements. Such calls must use only PSTN gateways that are defined as local to such systems.
  
The following table illustrates the trunk configuration of four trunks in two different network sites: two connected to PSTN gateways and two connected to PBX systems.
  
****

|**Name**|**EnableLocationRestriction**|**NetworkSiteID**|
|:-----|:-----|:-----|
|PstnGateway:Trunk 1 DEL-GW  <br/> |True  <br/> |Site 1 (Delhi)  <br/> |
|PstnGateway:Trunk 2 HYD-GW  <br/> |True  <br/> |Site 2 (Hyderabad)  <br/> |
|PstnGateway:Trunk 3 DEL-PBX  <br/> |False  <br/> |Site 1 (Delhi)  <br/> |
|PstnGateway:Trunk 4 HYD-PBX  <br/> |False  <br/> |Site 2 (Hyderabad)  <br/> |
   
## Enable Location-Based Routing to Voice Policies
<a name="sectionSection2"> </a>

To enforce Location-Based Routing to specific users, configure those users' voice policy to prevent PSTN toll bypass. Use the Lync Server Windows PowerShell command, New-CsVoicePolicy, to create a new voice policy or Set-CsVoicePolicy, if using an existing policy, to enable Location-Based Routing by preventing PSTN toll bypass.
  
```
Set-CsVoicePolicy -Identity <voice policy ID> -PreventPSTNTollBypass <$true|$false>
```

For more information, see [New-CsVoicePolicy](new-csvoicepolicy.md).
  
For this example, the following table and Windows PowerShell commands illustrate enabling the prevention of PSTN toll bypass to the Delhi and Hyderabad voice policies defined in this scenario. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.
  
```
Set-CsVoicePolicy -Identity "Delhi voice policy" -PreventPSTNTollBypass $true
Set-CsVoicePolicy -Identity "Hyderabad voice policy" -PreventPSTNTollBypass $true
```

****

||**Voice policy 1**|**Voice policy 2**|
|:-----|:-----|:-----|
|Voice policy ID  <br/> |Delhi voice policy  <br/> |Hyderabad voice policy  <br/> |
|PSTN usages  <br/> |Delhi usage, PBX Del usage, PBX Hyd usage  <br/> |Hyderabad usage, PBX Hyd usage, PBX Del usage  <br/> |
|PreventPSTNTollBypass  <br/> |True  <br/> |True  <br/> |
   
## Enable Location-Based Routing in the routing configuration
<a name="sectionSection3"> </a>

Finally, globally enable Location-Based Routing to your routing configuration. Use the Lync Server Windows PowerShell command, New-CsRoutingConfiguration, to enable Location-Based Routing.
  
```
Set-CsRoutingConfiguration -EnableLocationBasedRouting $true
```

For more information, see [Set-CsRoutingConfiguration](set-csroutingconfiguration.md).
  
> [!NOTE]
> while Location-Based Routing must be enabled via a global configuration, the set of rules to be applied will only be enforced for the sites, users and trunks for which it has been configured as specified in this documentation. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Configuring Location-Based Routing in Lync Server 2013](configuring-location-based-routing.md)

