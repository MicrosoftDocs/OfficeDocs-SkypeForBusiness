---
title: "Deployment guidelines for Enterprise Voice in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8985bd93-7613-4cef-9c89-51df6049ed9b
description: "In this articleDeployment PrerequisitesPower, Network, or Telephone Service OutagesEnterprise Voice Depends on Server Availability and Voice Client and Hardware OperabilityAlternative Means of Accessing Emergency ServicesEmergency Calls and Multi-Line Telephone Systems"
---

# Deployment guidelines for Enterprise Voice in Lync Server 2013
[]
 **In this article**
  
[Deployment Prerequisites](#sectionSection0)
  
[Power, Network, or Telephone Service Outages](#sectionSection1)
  
[Enterprise Voice Depends on Server Availability and Voice Client and Hardware Operability](#sectionSection2)
  
[Alternative Means of Accessing Emergency Services](#sectionSection3)
  
[Emergency Calls and Multi-Line Telephone Systems](#sectionSection4)
  
This topic describes prerequisites and other guidelines to consider when you are planning to deploy Lync Server 2013 and the Enterprise Voice workload.
  
## Deployment Prerequisites
<a name="sectionSection0"> </a>

For an optimum experience when deploying Enterprise Voice, make sure that your IT infrastructure, network, and systems meet the following prerequisites:
  
- Lync Server 2013 Standard Edition or Enterprise Edition is installed and operational on your network. 
    
- All Edge Servers are deployed and operational in your perimeter network, including Edge Servers with Access Edge service, A/V Edge service, Web Conferencing Edge service, and a reverse proxy.
    
- One or more users have been created and enabled for Lync Server.
    
- Microsoft Exchange Server 2007 Service Pack 1 (SP1) or latest service pack, or Microsoft Exchange Server 2010 is installed. One of these is required for integrating Exchange Unified Messaging (UM) with Lync Server and to provide rich notifications and call log information to client endpoints.
    
- A unique primary phone number has been designated, normalized, and copied to the **msRTCSIP-line** attribute for each user who is to be enabled for Enterprise Voice. 
    
    > [!NOTE]
    > Lync Server supports E.164 numbers and non-Direct Inward Dialing (DID) numbers. Non-DID numbers can be represented in the format **\<E.164\>;ext=\<extension\>** or as a string of digits, with the requirement that the private extension is unique across the enterprise. For example, a private number of 1001 can be represented as **+1425550100;ext=1001**, or as **1001**. When represented as **1001**, the expectation is that this private number is unique across the enterprise. 
  
- Administrators who deploy Enterprise Voice should be members of the RTCUniversalServerAdmins group.
    
- At a minimum, Office Communicator 2007 is successfully deployed. To use features new to this release, Lync 2013 is deployed.
    
- Managed key infrastructure (MKI) is deployed and configured, using either a Microsoft or a third-party certification authority (CA) infrastructure.
    
- Each computer on which you install Mediation Server must be:
    
  - A member server of a domain, and prepared for Active Directory Domain Services. For Active Directory Domain Services preparation procedures, see [Preparing Active Directory Domain Services for Lync Server 2013](preparing-active-directory-domain-services-for-lync-server-2013.md) in the Deployment documentation. 
    
  - Running one of the following operating systems:
    
> The 64-bit edition of the Windows Server 2008 Standard operating system
    
> The 64-bit edition of the Windows Server 2008 Enterprise operating system
    
- If the connection to the public switched telephone network (PSTN) or private branch exchange (PBX) is by means of a Time Division Multiplexing (TDM) connection, one or more PSTN gateways are available for deployment. (If the connection is by means of a SIP trunk, a PSTN gateway is not required.)
    
## Power, Network, or Telephone Service Outages
<a name="sectionSection1"> </a>

If there is an outage, disruption, or other degradation of the power, network, or telephone services at your location, the voice, instant messaging, presence, and other features of Lync Server and any device connected to Lync Server may not work properly.
  
## Enterprise Voice Depends on Server Availability and Voice Client and Hardware Operability
<a name="sectionSection2"> </a>

Voice communications with Lync Server depend upon the availability of the server software and the proper functioning of the voice clients or the hardware phone devices connecting to the server software.
  
## Alternative Means of Accessing Emergency Services
<a name="sectionSection3"> </a>

For those locations where you install a voice client (for example, a PC running Lync client or an Lync Phone Edition device), we recommend that you maintain a backup option for users to call emergency services (for example, 911 or 999) in case of a power failure, network connectivity degradation, telephone service outage, or other issue that may inhibit operation of Lync Server, Lync, or Lync Phone Edition devices. Such alternative options could include a telephone connected to a standard public switched telephone network line or a cell phone.
  
## Emergency Calls and Multi-Line Telephone Systems
<a name="sectionSection4"> </a>

The use of a multiline telephone system (MLTS) may be subject to U.S state or federal laws or the laws of other countries/regions that require the MLTS to provide a caller's telephone number, extension, and/or physical location to applicable emergency services when a caller is placed to emergency services (for example, when dialing an emergency access number such as 911 or 999). In this release, Lync Server can be configured to provide a caller's physical location to an emergency services provider, as described in [Planning for emergency services (E9-1-1) in Lync Server 2013](planning-for-emergency-services-e9-1-1.md). Compliance with MLTS laws is the sole responsibility of the purchaser of Lync Server, Lync client, and Lync Phone Edition devices.
  

