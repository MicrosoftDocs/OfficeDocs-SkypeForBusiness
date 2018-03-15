---
title: "Deployment process for Location-Based Routing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9e923e72-83fc-4a4f-8937-28a55739ed3e

description: "This topic provides an overview of the process involved in configuring Location-Based Routing. You must deploy Lync Server Enterprise Edition or Standard Edition with Enterprise Voice before you configure Location-Based Routing. The components required by Location-Based Routing are already installed and enabled when you deploy Enterprise Voice."
---

# Deployment process for Location-Based Routing in Lync Server 2013
[]
This topic provides an overview of the process involved in configuring Location-Based Routing. You must deploy Lync Server Enterprise Edition or Standard Edition with Enterprise Voice before you configure Location-Based Routing. The components required by Location-Based Routing are already installed and enabled when you deploy Enterprise Voice.
  
**Location-Based Routing Deployment Process**

|**Phase**|**Steps**|**Required groups and roles**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Deploy Enterprise Voice  <br/> | Configure Trunks  <br/>  Create Voice Policies  <br/>  Define Voice Routes  <br/> |CSVoiceAdmins          CsAdministrator          CsServerAdministrator  <br/> |Deploying Enterprise Voice  <br/> |
|Verify your Enterprise Voice deployment  <br/> ||CSVoiceAdmins          CsAdministrator          CsServerAdministrator  <br/> ||
|Configure network regions, sites, and subnets  <br/> | Create network regions  <br/>  Create network sites  <br/>  Associates subnets with network sites  <br/> |CSVoiceAdmins          CsAdministrator          CsServerAdministrator  <br/> |About Network Regions, Sites, and Subnets          Create or Modify a Network Region          Create or Modify a Network Site          Associate a Subnet with a Network Site  <br/> |
|Configure Location-Based Routing  <br/> | Create voice routing policies  <br/>  Define separate trunk configuration per trunk  <br/>  Modify voice policies  <br/>  Enable Location-Based Routing configuration  <br/> |CSVoiceAdmins          CsAdministrator          CsServerAdministrator  <br/> ||
   
## Sample Deployment

The following deployment is used to illustrate further the mechanisms enabled by Location-Based Routing.
  
![Location-Based Routing Topology](media/Plan_LyncServer_Voice_LBR_example_topology.png)
  
### Incoming PSTN calls

An administrator can enable the trunk defined to route calls to "Site 1 Gateway" for Location-Based Routing and associate the "Site 1 Gateway" to site 1. Once enabled, calls that are routed through "Site 1 Gateway" will only be routed to users that are located in site 1. All calls routed through the "Site 1 Gateway" trunk destined to users in a different site, such as site 2 will be blocked to prevent PSTN toll bypass.
  
All incoming PSTN calls through "Site 1 Gateway" will only be allowed to route to endpoints located in site 1. For example, when "Lync user 1" travels to site 2, all incoming PSTN calls through "Site 1 Gateway" will not be routed to "Lync user 1" endpoints located in site 2. The same routing rule applies if "Lync user 1" travels to an unknown network site where the user's location can't be determined.
  
The following table outlines the user experience of "Lync user 1" in this context.
  
****

||**Lync user 1 endpoints located in network site 1**|**Lync user 1 endpoints located in network site 2**|**Lync user 1 endpoints located in unknown network site**|
|:-----|:-----|:-----|:-----|
|Inbound PSTN calls to Lync user 1  <br/> |Calls are routed to endpoints in this location  <br/> |Calls are not routed to endpoints in this location  <br/> |Calls are not routed to endpoints in this location  <br/> |
   
### Outgoing PSTN calls

Voice routes are referenced in both Voice Policies assigned directly to users, and Voice Routing Policies assigned to network sites. Both policies contain references to routes, which can be used to route a call differently. For example, an administrator can define a Voice Routing Policy for all users located in network site 1 to route all outbound calls through the "Site 1 Gateway" while the Voice Policy of some users define a route for all outbound calls through the "Site 2 Gateway". While these users are located in network site 1, their outbound calls will be routed through the "Site 1 Gateway".
  
When a user is located in a network site configured for Location-Based Routing, the network site's Voice Routing Policy route overrides the user's Voice Policy route. This rule is particularly useful for users that temporarily move to a different site. In this particular case a user will always use a gateway that is local to his location; if "Lync user 3" is located at "Site 2", all his outbound calls will be routed via "Site 2 Gateway", but if he travels to site 1, all his outbound calls placed while he's at site 1 will be routed through "Site 1 Gateway".
  
The following table illustrates the user experience of Lync user 1 placing an outbound call from the following network sites.
  
****

||**Network site 1**|**Network site 2**|**Unknown network site or not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|Authorization of outbound calls  <br/> |Lync user 1 voice policy  <br/> |Lync user 1 voice policy  <br/> |Lync user 1 voice policy  <br/> |
|Routing of outbound calls  <br/> |Site 1 voice routing policy  <br/> |Site 2 voice routing policy  <br/> |User's voice policy and only to systems not enabled for Location-Based Routing  <br/> |
   
### Call transfers and forwards

When calls are transferred or forwarded, the routing of calls is affected by Location-Based Routing.
  
The following table depicts Lync user 1 transferring or forwarding a PSTN call to another Lync user.
  
****

|**User initiating call transfer or forward**|**Lync user 2**|**Lync user 4**|**Lync user in network site not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|Lync user 1  <br/> |Call forward or transfer is allowed  <br/> |Call forward or transfer is not allowed  <br/> |Call forward or transfer is not allowed  <br/> |
   
The following table illustrates how Location-Based Routing affects how the call is routed based on the location of the Lync user being transferred (Lync user 2, Lync user 4, etc) to a PSTN endpoint
  
****

|**Endpoint where call is transferred or forwarded to**|**Lync user 2**|**Lync user 4**|**Lync user in network site not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|PSTN endpoint  <br/> |Call forward or transfer is routed through site 1 voice routing policy and egress via Site 1 Gateway  <br/> |Call forward or transfer is routed through site 2 voice routing policy and egress via Site 2 Gateway  <br/> |Call forward or transfer is routed through the Lync user voice policy and egress via a gateway not enabled for location-based routing (if available)  <br/> |
   
### Simultaneous ringing

Once location-based routing is configured in the sample topology, the following interactions are enforced.
  
The following table illustrates whether Location-Based Routing allows simultaneous ringing for different Lync users (i.e. Lync user 2, Lync user 4, etc).
  
****

|**Incoming PSTN call target**|**Lync user 2**|**Lync user 4**|**Lync user in network site not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|Lync user 1  <br/> |Simultaneous ring is allowed  <br/> |Simultaneous ring is not allowed  <br/> |Simultaneous ring is not allowed  <br/> |
   
The following table illustrates whether Location-Based Routing allows simultaneous ringing to a PSTN endpoint from different Lync users (i.e. Lync user 2, Lync user 4, etc).
  
****

|**Simultaneous ring target**|**Lync user 2**|**Lync user 4**|**Lync user in network site not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|Lync user 1 mobile phone (PSTN endpoint)  <br/> |Call routed through network site 1's voice routing policy and egress via site 1 gateway  <br/> |Call routed through network site 2's voice routing policy and egress via site 2 gateway  <br/> |Call routed through the caller voice policy and will egress via a PSTN gateway not enabled for Location-Based Routing  <br/> |
   
## See also

#### 

[Planning for Location-Based Routing in Lync Server 2013](planning-for-location-based-routing.md)

