---
title: "DNS summary - Reverse proxy in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3073affa-4d92-4453-9974-3a82ca0c6445

description: ""
---

# DNS summary - Reverse proxy in Lync Server 2013
[]

You configure two network adapters in your reverse proxy as follows:
  
## Reverse Proxy Network Adapter Requirements

- **Network adapter 1 (Internal Interface)** example 
    
    Internal interface with 172.25.33.40 assigned.
    
    No default gateway is defined.
    
    Ensure there is a route from the network containing the reverse proxy internal interface to any networks that contain Lync Server Front End pool servers (for example, from 172.25.33.0 to 192.168.10.0).
    
- **Network adapter 2 (External Interface)** example 
    
    A minimum of one public IP address is assigned to this network adapter.
    
    Gateway is defined to point to the router or integrated firewall in your outer perimeter. (10.45.16.1 in the scenario examples)
    
**DNS Records Required for Reverse Proxy**

|**Location/TYPE/Port**|**FQDN**|**IP address**|**Maps to/comments**|
|:-----|:-----|:-----|:-----|
|External DNS/A  <br/> |webext.contoso.com  <br/> |Assigned listener for externally published resources  <br/> | External web services from the internal deployment. Additional records can be defined and created for all pools and single servers for any SIP domain that will use this reverse proxy, and has defined external web services.  <br/> |
|External DNS/A  <br/> |webdirext.contoso.com  <br/> |Assigned listener for externally published resources  <br/> |External web services for the Directors or Director pools in your deployment. You can define as many Directors as there are distinct Directors, of which may be associated with other SIP domains.  <br/> > [!IMPORTANT]> Defining the DNS records for and publishing the Directors is not an either the Front End pool or the Director decision. You must define and publish both the Director and the Front End pool external web services if you are using Directors. Specific traffic types (for authentication and other uses) will be sent to the Director first, if it is defined in the topology.           |
|External DNS/A  <br/> |dialin.contoso.com  <br/> |Assigned listener for externally published resources  <br/> |Dial-in conferencing published externally  <br/> |
|External DNS/A  <br/> |meet.contoso.com  <br/> |Assigned listener for externally published resources  <br/> |Conferences published externally  <br/> |
|External DNS/A  <br/> |officewebapps01.contoso.com  <br/> |Assigned listener for Office Web Apps Server  <br/> |Office Web Apps Server deployed internally or in the perimeter, and published for external client access  <br/> |
|External DNS/A  <br/> |lyncdiscover.contoso.com  <br/> |Assigned listener for externally published resources  <br/> |Lync Discover External record for externally published AutoDiscover, and includes Mobility, Microsoft Lync Web App, and scheduler Web app  <br/> |
   

