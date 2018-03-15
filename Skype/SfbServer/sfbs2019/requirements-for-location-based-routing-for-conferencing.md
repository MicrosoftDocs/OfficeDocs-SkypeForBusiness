---
title: "Requirements for Location-Based Routing for conferencing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 766d9286-2c34-4faf-bb3e-f0ca478a70cf
description: "In this articleSupported ServersSupported ClientsMediation Server Requirements for Consultative Call TransfersCapabilities Not Supported by the Location-Based Routing Conferencing Application"
---

# Requirements for Location-Based Routing for conferencing in Lync Server 2013
[]
 **In this article**
  
[Supported Servers](#sectionSection0)
  
[Supported Clients](#sectionSection1)
  
[Mediation Server Requirements for Consultative Call Transfers](#sectionSection2)
  
[Capabilities Not Supported by the Location-Based Routing Conferencing Application](#sectionSection3)
  
The following are the requirements needed for the installation and configuration of the Location-Based Routing Conferencing application:
  
- Lync Server 2013 Cumulative Update 2 must be deployed on all servers or pools in your topology.
    
> [!NOTE]
>  If a Lync server or pool in your topology does not have Lync Server 2013 Cumulative Update 2 or higher installed, then enforcement of Location-Based Routing of Lync meetings cannot be guaranteed. 
  
- Lync Server 2013 Location-Based Routing is a pre-requisite for Location-Based Routing Conferencing application. For further information on configuring Lync Server 2013 Location-Based Routing, please refer to [Configuring Location-Based Routing](https://technet.microsoft.com/en-us/library/jj994036.aspx).
    
- Requirements of Location-Based Routing Conferencing application are the same as the requirements for Lync Server 2013 Location-Based Routing. For more information, please refer to [Planning for Location-Based Routing](https://technet.microsoft.com/en-us/library/jj994068.aspx).
    
## Supported Servers
<a name="sectionSection0"> </a>

The Location-Based Routing Conferencing application requires that Lync Server 2013 Cumulative Update 2 is deployed on all Front-End pools and Standard Edition Servers in your topology. If Lync Server 2013 Cumulative Update 2 is not installed on some Lync Servers in your topology, Location-Based Routing restrictions cannot be fully enforced on Lync meetings and consultative call transfers.
  
The following table identifies the combination of server roles and versions that support Location-Based Routing.
  
||||
|:-----|:-----|:-----|
|Front-End Pool version  <br/> |Mediation Server version  <br/> |Supported  <br/> |
|Lync Server 2013 Cumulative Update 2  <br/> |Lync Server 2013 Cumulative Update 2  <br/> |Yes  <br/> |
|Lync Server 2013 Cumulative Update 2  <br/> |Lync Server 2013 Cumulative Update 1  <br/> |No  <br/> |
|Lync Server 2013 Cumulative Update 2  <br/> |Lync Server 2010  <br/> |No  <br/> |
|Lync Server 2013 Cumulative Update 2  <br/> |Office Communications Server 2007 R2  <br/> |No  <br/> |
|Lync Server 2013 Cumulative Update 1  <br/> |Any  <br/> |No  <br/> |
|Lync Server 2010  <br/> |Any  <br/> |No  <br/> |
|Office Communications Server 2007 R2  <br/> |Any  <br/> |No  <br/> |
   
## Supported Clients
<a name="sectionSection1"> </a>

The Lync clients that support Location-Based Routing of Lync meetings are the same clients that support Lync Server 2013 Location-Based Routing. For more information, please refer to [Client and Server Support for Location-Based Routing](https://technet.microsoft.com/en-us/library/jj994024.aspx).
  
## Mediation Server Requirements for Consultative Call Transfers
<a name="sectionSection2"> </a>

The Location-Based Routing Conferencing application requires deploying stand-alone Mediation Servers in order to enforce Location-Based Routing restrictions on consultative call transfers. 
  
To enforce Location-Based Routing of consultative call transfers, the Mediation Server must be associated with only one Mediation Server peer (i.e. PBX, SIP gateway, etc) in network regions where Location-Based Routing is required. If additional Mediation Server peers are deployed in the same network region, the Mediation Server peer must be associated with a different Mediation Server . This Requirement is detailed as follows:
  
- Single Mediation Server per multiple Mediation Server peers When a consultative call transfer is routed to a Mediation Server peer through a Mediation Server that's configured with multiple SIP trunks to multiple peers (i.e. PBXs and gateways), the consultative call transfer is blocked to prevent PSTN toll bypass if the consultative call transfer is permitted through some SIP trunks but disallowed through other SIP trunks.
    
    For example, in the case of a single Mediation Server servicing a PSTN Gateway Mediation Server Peer and a PBX Mediation Server Peer, the following behavior will be observed:
    
  - When a Lync user from a given site (i.e. site 1) attempts to transfer a call with a PSTN endpoint to a Lync user from a different site (i.e. site 2) via consultative transfer, the call will be disallowed to prevent PSTN toll bypass.
    
  - When a Lync user from a given site (i.e. site 1) attempts to transfer a call with a PBX endpoint in the same site (site 1) to a Lync user from a different site (i.e. site 2) via consultative transfer, the call will be disallowed even if it doesn't incur in potential PSTN toll bypassing.
    
- Separate Mediation Servers per Mediation Server peer
    
    When a consultative transfer is targeted at a Mediation Server Peer, the consultative transfer will be evaluated against the single Mediation Server Peer serviced by the Mediation Server. The call will be disallowed or allowed based in its potential to incur in PSTN toll bypass regardless of all other Mediations Server Peers in the site as they're serviced by separate Mediation Servers.
    
    For example, in the case of a separate Mediation Servers servicing a PSTN Gateway Mediation Server Peer and a PBX Mediation Server Peer, the following behavior will be observed:
    
  - When a Lync user from a given site (i.e. site 1) attempts to transfer a call with a PSTN endpoint to a Lync user from a different site (i.e. site 2) via consultative transfer, the call will be disallowed to prevent PSTN toll bypass.
    
  - When a Lync user from a given site (i.e. site 1) attempts to transfer a call with a PBX endpoint in the same site (site 1) to a Lync user from a different site (i.e. site 2) via consultative transfer, the call will be allowed as it doesn't incur in potential PSTN toll bypassing.
    
## Capabilities Not Supported by the Location-Based Routing Conferencing Application
<a name="sectionSection3"> </a>

The following capabilities are not supported by the Location-Based Routing Conferencing application:
  
- Dial-in conferencing. Location-Based Routing cannot be enforced for Dial-in conferencing. Any dial-in request to a given conference will not be restricted by Location-Based Routing even if the conference organizer is a Lync user enabled for Location-Based Routing.
    
- It's recommended not to provision conferencing access numbers in regions where Location-Based Routing restrictions need to be enforced. 
    

