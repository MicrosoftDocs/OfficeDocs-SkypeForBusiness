---
title: "Client and server support for Location-Based Routing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 26c2ca3d-026d-4dd7-94fa-15ebb4406953
description: "Location-Based Routing is enforced by Lync Server. Lync Server can identify the network sites where users are connecting from within the corporate network. Since remote users are outside the corporate network, their location is considered to be unknown."
---

# Client and server support for Location-Based Routing in Lync Server 2013
[]
Location-Based Routing is enforced by Lync Server. Lync Server can identify the network sites where users are connecting from within the corporate network. Since remote users are outside the corporate network, their location is considered to be unknown.
  
## Lync Server Support

Location-Based Routing requires that Lync Server 2013 CU1 is deployed on all Front End pools and Standard Edition servers in a given topology. If Lync Server 2013 CU1 is not installed on certain Lync components in the topology, Location-Based Routing restrictions cannot be fully enforced.
  
The following table identifies the combination of server roles and versions that is supported for Location-Based Routing.
  
****

|**Pool version**|**Mediation Server version**|**Supported**|
|:-----|:-----|:-----|
|Lync Server 2013 February 2013 Cumulative Update  <br/> |Lync Server 2013 February 2013 Cumulative Update  <br/> |yes  <br/> |
|Lync Server 2013 February 2013 Cumulative Update  <br/> |Lync Server 2013  <br/> |no  <br/> |
|Lync Server 2013 February 2013 Cumulative Update  <br/> |Lync Server 2010  <br/> |no  <br/> |
|Lync Server 2013 February 2013 Cumulative Update  <br/> |Office Communications Server 2007 R2  <br/> |no  <br/> |
|Lync Server 2013  <br/> |any  <br/> |no  <br/> |
|Lync Server 2010  <br/> |any  <br/> |no  <br/> |
|Office Communications Server 2007 R2  <br/> |any  <br/> |no  <br/> |
   
## Lync Client Support

The following table identifies the clients that Location-Based Routing supports.
  
****

|**Client type**|**Supported**|**Details**|
|:-----|:-----|:-----|
|Lync 2013  <br/> |yes  <br/> |Including Lync 2013 February 2013 Cumulative Update  <br/> |
|Lync 2010  <br/> |yes  <br/> ||
|Office Communicator 2007 R2  <br/> |no  <br/> ||
|Lync Phone Edition  <br/> |yes  <br/> ||
|Lync Attendant  <br/> |yes  <br/> ||
|Lync for Windows 8  <br/> |no  <br/> ||
|Lync Mobile 2013  <br/> |no  <br/> |VoIP must be disabled for Lync Mobile 2013 clients if used by users with Location-Based Routing enabled.  <br/> |
|Lync Mobile 2010  <br/> |yes  <br/> ||
   
> [!NOTE]
> To disable VoIP for Lync Mobile 2013 clients, assign a mobility policy with the setting, IP Audio/Video, disabled for all users enabled for Location Based Routing. For more details about mobility policy, see [New-CsMobilityPolicy](new-csmobilitypolicy.md). 
  
## See also

#### 

[Planning for Location-Based Routing in Lync Server 2013](planning-for-location-based-routing.md)

