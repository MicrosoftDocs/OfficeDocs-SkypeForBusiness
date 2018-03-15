---
title: "Overview of IP address types for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ee9a695f-5cf5-441e-94fb-6adeca50e8d8
description: "In this articleClient RegistrationPeer-to-Peer ClientConferencingMediation Server/PSTNRemote User Peer-to-Peer CommunicationsFront End Pool and Edge Pool ConfigurationAdvanced Enterprise Voice Support for IPv6Other Lync Server 2013 Feature Support for IPv6"
---

# Overview of IP address types for Lync Server 2013
[]
 **In this article**
  
[Client Registration](#sectionSection0)
  
[Peer-to-Peer Client](#sectionSection1)
  
[Conferencing](#sectionSection2)
  
[Mediation Server/PSTN](#sectionSection3)
  
[Remote User Peer-to-Peer Communications](#sectionSection4)
  
[Front End Pool and Edge Pool Configuration](#sectionSection5)
  
[Advanced Enterprise Voice Support for IPv6](#sectionSection6)
  
[Other Lync Server 2013 Feature Support for IPv6](#sectionSection7)
  
You have three options when configuring IP addresses in Lync Server 2013. You can configure Lync Server 2013 to support only IP version 4 (IPv4), only IP version 6 (IPv6), or a combination of both (known as a dual stack). There are several issues to consider with each type of configuration:
  
- **IPv4 only** IPv6 was created because the world is running out of IPv4 addresses. Ultimately, IPv6 will be fully supported worldwide, but at this time, many companies and devices that your enterprise might need to communicate with do not yet support IPv6, and may not for some time. An IPv4-only configuration will help to ensure that your Lync Server implementation can communicate with most existing devices. 
    
- **IPv6 only** Conversely, a full IPv6 implementation, at this time, will exclude communication with many existing devices. 
    
- **Dual Stack** Dual stack is a network where both IPv4 and IPv6 addresses are enabled. This configuration is supported in Lync Server 2013 because in most cases the transition from full-IPv4 to full-IPv6 will take several years. 
    
The following sections outline the compatibility among these three configurations for various Lync Server features.
  
> [!NOTE]
> Client or server configuration with IPv6 only is supported only for lab or validation purposes. IPv6 only configuration is not supported in the production deployment. 
  
## Client Registration
<a name="sectionSection0"> </a>

|**Client endpoint network**|**Server network**|
|:-----|:-----|
|IPv4  <br/> |IPv4  <br/> |
|IPv4  <br/> |Dual stack  <br/> |
|Dual stack  <br/> |IPv4  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |
|Dual stack  <br/> |IPv6  <br/> |
|IPv6  <br/> |Dual stack  <br/> |
|IPv6  <br/> |IPv6  <br/> |
   
## Peer-to-Peer Client
<a name="sectionSection1"> </a>

Peer-to-peer communications include audio, audio/video, application sharing, and file transfer. After both clients have successfully registered, the following combinations are supported.
  
|**Client endpoint 1**|**Client endpoint 2**|
|:-----|:-----|
|IPv4  <br/> |IPv4  <br/> |
|IPv4  <br/> |Dual stack  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |
|IPv6  <br/> |Dual stack  <br/> |
|IPv6  <br/> |IPv6  <br/> |
   
## Conferencing
<a name="sectionSection2"> </a>

Conferencing includes audio/video, application sharing, and data collaboration (whiteboarding and file sharing).
  
|**Client endpoint network**|**Server network**|
|:-----|:-----|
|IPv4  <br/> |IPv4  <br/> |
|IPv4  <br/> |Dual stack  <br/> |
|Dual stack  <br/> |IPv4  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |
|Dual stack  <br/> |IPv6  <br/> |
|IPv6  <br/> |Dual stack  <br/> |
|IPv6  <br/> |IPv6  <br/> |
   
## Mediation Server/PSTN
<a name="sectionSection3"> </a>

Lync Server 2013 does not support media bypass for public switched telephone network (PSTN) calls if the traffic is through an IPv6 interface. If media bypass is required, we recommend that the PSTN gateway is configured to IPv4. 
  
|**Primary interface\***|**PSTN interface (on Mediation Server)**|**PSTN gateway setting**|
|:-----|:-----|:-----|
|IPv4  <br/> |Dual stack  <br/> |IPv4  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |IPv4  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |IPv6  <br/> |
   
\* The primary interface is the interface that communicates with the Lync Server components.
  
## Remote User Peer-to-Peer Communications
<a name="sectionSection4"> </a>

Peer-to-peer communications with remote users include instant messaging, audio/video, application sharing, and file transfer.
  
|**Remote user network**|**Edge server (External edge)**|
|:-----|:-----|
|IPv4  <br/> |IPv4  <br/> |
|Dual stack  <br/> |IPv4  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |
|IPv6  <br/> |Dual stack  <br/> |
|IPv6  <br/> |IPv6  <br/> |
   
## Front End Pool and Edge Pool Configuration
<a name="sectionSection5"> </a>

The following table shows the support matrix between the Front End Server pool and the internal Edge Server pool.
  
**Front End Pool and Edge Pool (Internal Edge) Matrix**

|||||
|:-----|:-----|:-----|:-----|
||**Edge Pool: IPv4** <br/> |**Edge Pool: Dual Stack** <br/> |**Edge Pool: IPv6** <br/> |
|**Front End Pool: IPv4** <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|**Front End Pool: Dual Stack** <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|**Front End Pool: IPv6** <br/> |No  <br/> |No  <br/> |Yes\*  <br/> |
   
\* Use this combination only in a lab environment.
  
The following table is a matrix of the supported combinations of internal and external edge interfaces.
  
**Edge Pool (Internal Edge) and Edge pool (External Edge) Matrix**

|||||
|:-----|:-----|:-----|:-----|
||**Edge Pool (External Edge) : IPv4** <br/> |**Edge Pool (External Edge): Dual Stack** <br/> |**Edge Pool (External Edge): IPv6** <br/> |
|**Edge Pool (Internal Edge): IPv4** <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|**Edge Pool (Internal Edge): Dual Stack** <br/> |No  <br/> |Yes  <br/> |No  <br/> |
|**Edge Pool (Internal Edge): IPv6** <br/> |No  <br/> |No  <br/> |Yes\*  <br/> |
   
\* Use this combination only in a lab environment.
  
## Advanced Enterprise Voice Support for IPv6
<a name="sectionSection6"> </a>

Deployments that include call admission control (CAC), Enhanced 9-1-1 (E9-1-1), or media bypass must be configured as IPv4 only or as a dual-stacked implementation. 
  
> [!NOTE]
> In a dual-stacked deployment, even if a Lync client connects to a Lync Server by using IPv6, Lync will make a best effort to map an appropriate IPv4 address to support E9-1-1. 
  
Location Information service with IPv6 addresses is not supported.
  
Exchange Unified Messaging (UM) does not support IPv6. For Exchange UM, be sure that DNS resolution does not return an IPv6 address. Using IPv6 may cause failure when calls are sent to voice mail. 
  
## Other Lync Server 2013 Feature Support for IPv6
<a name="sectionSection7"> </a>

In addition to the features and components mentioned previously, Lync Server 2013 supports IPv6 for the following features:
  
- **Persistent Chat**
    
    You configure IPv6 for Persistent Chat by using Topology Builder. For details about configuring Persistent Chat, see the Deploying Persistent Chat Server documentation.
    
- **Quality of Experience (QoE) and call detail recording (CDR) reports**
    
    Monitoring reports include the IP address as it is stored in the Monitoring Server database, whether of type IPv4 or IPv6.
    

