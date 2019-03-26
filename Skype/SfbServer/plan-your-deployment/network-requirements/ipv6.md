---
title: "Plan for IPv6 in Skype for Business"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 01f77196-38f4-4292-9480-2e2fbd57eabe
description: "Summary: Implement IPv6 before you install Skype for Business Server."
---

# Plan for IPv6 in Skype for Business
 
**Summary:** Implement IPv6 before you install Skype for Business Server.
  
Skype for Business Server includes support for IP version 6 (IPv6) addresses, along with continued support of IP version 4 (IPv4) addresses. 

IPv4 addresses are 32-bit addresses that allow a computer to communicate over the Internet. Due to the increasing number of devices worldwide, the available IPv4 addresses have run out. Because of this, many new devices are moving to using IPv6 addresses. IPv6 addresses perform the same function as IPv4 addresses (with some additional features), but instead of using only 32-bits, IPv6 addresses use 128-bits. This provides not only a new set of addresses, but also a much larger number of them. 

A typical IPv4 address looks something like this: 192.0.2.235, whereas an IPv6 address looks like this: 2001:0db8:85a3:0000:0000:8a2e:0370:7334. The change in formatting and functionality for devices that use IPv6 addresses requires several deployment and configuration considerations in your Skype for Business Server installation. 

This topic includes the following sections:
  
- [Overview of IP address types](ipv6.md#over)
    
- [Technical requirements for IPv6](ipv6.md#tech)
    
- [Migration and coexistence considerations for IPv6](ipv6.md#migration)
    
If you determine you will be using IPv6 addresses, refer to the [Configure IP address types in Skype for Business](ip-address-types.md) article.
  
## Overview of IP address types
<a name="over"> </a>

You have three options when configuring IP addresses in Skype for Business Server. You can configure Skype for Business Server to support only IP version 4 (IPv4), only IP version 6 (IPv6), or a combination of both (known as a dual stack). There are several issues to consider with each type of configuration:
  
- **IPv4 only** IPv6 was created because the world is running out of IPv4 addresses. Ultimately, IPv6 will be fully supported worldwide, but at this time, many companies and devices that your enterprise might need to communicate with do not yet support IPv6, and may not for some time. An IPv4-only configuration will help to ensure that your Skype for Business Server implementation can communicate with most existing devices.
    
- **IPv6 only** Conversely, a full IPv6 implementation will exclude communication with many existing devices.
    
- **Dual Stack** Dual stack is a network where both IPv4 and IPv6 addresses are enabled. This configuration is supported in Skype for Business Server because in most cases the transition from full-IPv4 to full-IPv6 will take several years.
    
The following sections outline the compatibility among these three configurations for various Skype for Business Server features.
  
> [!NOTE]
> Client or server configuration with IPv6 only is supported only for lab or validation purposes. IPv6 only configuration is not supported in the production deployment. 
  
### Client Registration
<a name="client"> </a>

|**Client endpoint network**|**Server network**|
|:-----|:-----|
|IPv4  <br/> |IPv4  <br/> |
|IPv4  <br/> |Dual stack  <br/> |
|Dual stack  <br/> |IPv4  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |
|Dual stack  <br/> |IPv6  <br/> |
|IPv6  <br/> |Dual stack  <br/> |
|IPv6  <br/> |IPv6  <br/> |
   
### Peer-to-Peer Client
<a name="peer"> </a>

Peer-to-peer communications include audio, audio/video, application sharing, and file transfer. After both clients have successfully registered, the following combinations are supported.
  
|**Client endpoint 1**|**Client endpoint 2**|
|:-----|:-----|
|IPv4  <br/> |IPv4  <br/> |
|IPv4  <br/> |Dual stack  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |
|IPv6  <br/> |Dual stack  <br/> |
|IPv6  <br/> |IPv6  <br/> |
   
### Conferencing
<a name="conf"> </a>

Conferencing includes audio/video, application sharing, and data collaboration applications like whiteboarding and file sharing.
  
|**Client endpoint network**|**Server network**|
|:-----|:-----|
|IPv4  <br/> |IPv4  <br/> |
|IPv4  <br/> |Dual stack  <br/> |
|Dual stack  <br/> |IPv4  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |
|Dual stack  <br/> |IPv6  <br/> |
|IPv6  <br/> |Dual stack  <br/> |
|IPv6  <br/> |IPv6  <br/> |
   
### Mediation Server/PSTN
<a name="med"> </a>

Skype for Business Server does not support media bypass for public switched telephone network (PSTN) calls if the traffic is through an IPv6 interface. If media bypass is required, we recommend that the PSTN gateway is configured to IPv4. 
  
|**Primary interface 1**|**PSTN interface (on Mediation Server)**|**PSTN gateway setting**|
|:-----|:-----|:-----|
|IPv4  <br/> |Dual stack  <br/> |IPv4  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |IPv4  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |IPv6  <br/> |
   
1. The primary interface is the interface that communicates with the Skype for Business Server components.
  
### Remote User Peer-to-Peer Communications
<a name="remote"> </a>

Peer-to-peer communications with remote users include instant messaging, audio/video, application sharing, and file transfer.
  
|**Remote user network**|**Edge server (External edge)**|
|:-----|:-----|
|IPv4  <br/> |IPv4  <br/> |
|Dual stack  <br/> |IPv4  <br/> |
|Dual stack  <br/> |Dual stack  <br/> |
|IPv6  <br/> |Dual stack  <br/> |
|IPv6  <br/> |IPv6  <br/> |
   
### Front End Pool and Edge Pool Configuration
<a name="FE_pool"> </a>

The following table shows the support matrix between the Front End Server pool and the internal Edge Server pool.
  
**Front End Pool and Edge Pool (Internal Edge) Matrix**

||**Edge Pool: IPv4** <br/> |**Edge Pool: Dual Stack** <br/> |**Edge Pool: IPv6** <br/> |
|:-----|:-----|:-----|:-----|
|**Front End Pool: IPv4** <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|**Front End Pool: Dual Stack** <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|**Front End Pool: IPv6** <br/> |No  <br/> |No  <br/> |Yes\*  <br/> |
   
\* Use this combination only in a lab environment.
  
The following table is a matrix of the supported combinations of internal and external edge interfaces.
  
**Edge Pool (Internal Edge) and Edge pool (External Edge) Matrix**

||**Edge Pool (External Edge) : IPv4** <br/> |**Edge Pool (External Edge): Dual Stack** <br/> |**Edge Pool (External Edge): IPv6** <br/> |
|:-----|:-----|:-----|:-----|
|**Edge Pool (Internal Edge): IPv4** <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|**Edge Pool (Internal Edge): Dual Stack** <br/> |No  <br/> |Yes  <br/> |No  <br/> |
|**Edge Pool (Internal Edge): IPv6** <br/> |No  <br/> |No  <br/> |Yes\*  <br/> |
   
\* Use this combination only in a lab environment.
  
### Advanced Enterprise Voice Support for IPv6
<a name="Ent_V"> </a>

Deployments that include call admission control (CAC), Enhanced 9-1-1 (E9-1-1), or media bypass must be configured as IPv4 only or as a dual-stacked implementation. Endpoints using only IPv6 cannot use any of these features.
  
> [!NOTE]
> In a dual-stacked deployment, even if a Skype for Business Server client connects to a Skype for Business Server by using IPv6, Skype for Business Server will make a best effort to map an appropriate IPv4 address to support E9-1-1. 
  
Location Information service with IPv6 addresses is not supported.
  
Exchange Unified Messaging (UM) does not support IPv6. For Exchange UM, be sure that DNS resolution does not return an IPv6 address. Using IPv6 may cause failure when calls are sent to voice mail. 
  
### Other Skype for Business Server Feature Support for IPv6
<a name="Ent_V"> </a>

In addition to the features and components mentioned previously, Skype for Business Server supports IPv6 for the following features:
  
- **Persistent Chat**
    
    You configure IPv6 for Persistent Chat by using Topology Builder. For details about configuring Persistent Chat, see the Deploying Persistent Chat Server documentation.
    
- **Quality of Experience (QoE) and call detail recording (CDR) reports**
    
    Monitoring reports include the IP address as it is stored in the Monitoring Server database, whether of type IPv4 or IPv6.
    
## Technical requirements for IPv6
<a name="tech"> </a>

If you plan to configure Skype for Business Server for IPv6, keep the following requirements in mind:
  
- To use IPv6 addresses with Skype for Business Server, you need to create domain name system (DNS) records for records that must be discovered and resolved to an IPv6 address. IPv6 DNS uses host AAAA (quad-A) records. If you use both IPv4 and IPv6 in your deployment, it is best to configure and maintain both host A records for IPv4 and host AAAA records for IPv6. Even when you fully transition your deployment to IPv6, you may still require IPv4 DNS host records for external users who still use IPv4.
    
    You can deploy IPv6 DNS host records before you start using IPv6. If the client or server doesn't use IPv6, the record will not be referenced. Transitional technologies will make the decision about which record to use, based on transition technology configuration and policies.
    
- Each IPv6 address has a scope. The three scopes that you can use for IPv6 addressing are IPv6 global addresses (similar to public IPv4 addresses), IPv6 unique local addresses (similar to the private IPv4 address ranges), and IPv6 link-local addresses (similar to automatic private IP addresses in Windows Server for IPv4). All the servers within a pool should have IPv6 addresses with the same scope. 
    
> [!IMPORTANT]
> IPv6 is a complex topic and requires careful planning with your networking team and your Internet provider to help ensure that the addresses that you assign at the Windows Server level and at the Skype for Business Server level work as expected. See the links at the end of this topic for additional resources on IPv6 addressing and planning. 
  
## Migration and coexistence considerations for IPv6
<a name="migration"> </a>

IP version 6 (IPv6) is not supported on Lync Server 2010 or Office Communications Server. For piloting purposes, you can test Lync Server 2010 and Skype for Business Server dual-stack coexistence. We recommend that all pools for a given central site are upgraded to Skype for Business Server before you enable IPv6 (dual-stack network) for any of the pools. If you need to configure a pool for IPv6 only, we recommend that you set up an IPv6-only pool in your lab environment for testing.
  
The following scenarios are supported during migration and coexistence:
  
- Skype for Business Server, Lync Server 2013, and Lync Server 2010 pools in IPv4 mode, coexisting with Skype for Business Server in dual-stack mode.
    
- Skype for Business Server pool in IPv6-only mode, if the IPv6-only pool is siloed.
    
## See also
<a name="migration"> </a>

[Configure IP address types in Skype for Business](ip-address-types.md)

[IP Version 6 Addressing Architecture](https://tools.ietf.org/html/rfc4291)
  
[IPv6 Global Unicast Address Format](https://tools.ietf.org/html/rfc3587)
  
[Unique Local IPv6 Unicast Addresses](https://tools.ietf.org/html/rfc4193)
