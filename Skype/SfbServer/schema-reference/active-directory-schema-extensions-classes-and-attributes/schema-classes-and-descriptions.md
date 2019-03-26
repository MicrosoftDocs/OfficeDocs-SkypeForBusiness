---
title: "Schema classes and descriptions in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 10/20/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7d43b920-ac37-40cc-adfe-be289bda6e9e
description: "This section describes all the schema classes used by Skype for Business Server ."
---

# Schema classes and descriptions in Skype for Business Server
 
This section describes all the schema classes used by Skype for Business Server . 
  
## Schema Classes and Descriptions

|**Class**|**Description**|**Comments**|
|:-----|:-----|:-----|
|Mail-Recipient  <br/> |Exchange Unified Messaging (UM) email recipient.  <br/> |This auxiliary class is shared with Exchange UM.  <br/> |
|msRTCSIP-ApplicationContacts  <br/> |This class is a container for multiple application contacts and does not contain any attributes itself.  <br/> |New in Microsoft Office Communications Server 2007 R2.  <br/> |
|msRTCSIP-ApplicationServer  <br/> |This class holds the entry for the service control point for an instance of Unified Communications Application Services (UCAS).  <br/> |New in Office Communications Server 2007 R2.  <br/> |
|msRTCSIP-ApplicationServerService  <br/> |This class provides an association from a specific pool to its Application service.  <br/> |New in Communications Server 2007 R2.  <br/> |
|msRTCSIP-ApplicationServerSettings  <br/> |This auxiliary class to msRTCSIP-ApplicationServer holds attributes representing settings for instances of the Application service.  <br/> |New in Communications Server 2007 R2.  <br/> |
|msRTCSIP-Archive (obsolete)  <br/> |This auxiliary class to msRTCSIP-GlobalContainer holds all settings related to archiving.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-ArchivingServer (obsolete)  <br/> |This class represents a single instant messaging Archiving Server. An instance of this class is created when a computer is activated as an instant messaging Archiving Server, such as a computer with the Instant Messaging Archiving service installed.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-ConferenceDirectories  <br/> |This class is a container for multiple instances of conference directories and does not contain any attributes itself.  <br/> |New in Communications Server 2007 R2.  <br/> |
|msRTCSIP-ConferenceDirectory  <br/> |This class holds attributes representing settings for a specific conference directory.  <br/> |New in Communications Server 2007 R2.  <br/> |
|msRTCSIP-ConnectionPoint  <br/> |Generic service control point (SCP) to specify the computer as a server running Skype for Business Server.  <br/> |New in Lync 2010.  <br/> |
|msRTCSIP-DefaultCWABank  <br/> |This auxiliary class holds the settings for a Skype for Business Web App bank.  <br/> |New in Communications Server 2007 R2.  <br/> |
|msRTCSIP-Domain  <br/> |This class holds attributes that define the configured domains of the SIP Registrar.  <br/> |-  <br/> |
|msRTCSIP-EdgeProxy  <br/> |This class container represents a single Access Edge service. Because an Access Edge service is deployed in the perimeter network and customers usually do not allow Active Directory Domain Services access from the perimeter network, instances of Access Edge service are not joined to the intranet's Active Directory network. Therefore, Access Proxies are not automatically registered in AD DS. The administrator must manually configure the existence of each instance of Access Edge service in AD DS.  <br/> |-  <br/> |
|msRTCSIP-EnterpriseMCUSettings  <br/> |This auxiliary class to msRTCSIP-MCU holds attributes representing settings for Conferencing servers.  <br/> |New in Microsoft Office Communications Server 2007.  <br/> |
|msRTCSIP-EnterpriseMediationServerSettings  <br/> |This auxiliary class to msRTCSIP-MediationServer holds attributes representing settings for Mediation Servers.  <br/> |New in Office Communications Server 2007.  <br/> |
|msRTCSIP-EnterpriseServerSettings  <br/> |This auxiliary class to msRTCSIP-Server holds attributes representing settings for SIP servers.  <br/> |-  <br/> |
|msRTCSIP-Federation  <br/> |This auxiliary class to msRTCSIP-GlobalContainer holds all settings related to federation.  <br/> |-  <br/> |
|msRTCSIP-GlobalContainer  <br/> |This class holds all settings that apply throughout a Skype for Business Server deployment.  <br/> |-  <br/> |
|msRTCSIP-GlobalUserPolicy (obsolete)  <br/> |This class represents a single Office Communications Server meeting policy.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-GlobalTopologySetting  <br/> |The local global topology setting object.  <br/> |New in Lync Server 2010.  <br/> |
|msRTCSIP-GlobalTopologySettings  <br/> |Container to hold global topology setting objects.  <br/> |New in Lync Server 2010.  <br/> |
|msRTCSIP-LocalNormalization  <br/> |This class is a container that represents an instance of a location normalization rule.  <br/> |-  <br/> |
|msRTCSIP-LocationContactMapping  <br/> |This class is created by the Conferencing Attendant application and holds attributes used to categorize conference telephone numbers by region.  <br/> |New in Communications Server 2007 R2.  <br/> |
|msRTCSIP-LocationContactMappings  <br/> |This class is a container for multiple instances of location contact mappings and does not contain any attributes itself.  <br/> |New in Communications Server 2007 R2.  <br/> |
|msRTCSIP-LocationProfile  <br/> |This class is a container that represents a specific location profile.  <br/> |-  <br/> |
|msRTCSIP-LocationProfiles (obsolete)  <br/> |This class is a container for multiple location profiles and does not contain any attributes itself.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-LocalNormalizations (obsolete)  <br/> |This class is a container for multiple local normalization rules and does not contain any attributes itself.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-MCU  <br/> |This class represents a single Conferencing server.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-MCUFactories  <br/> |This class holds multiple msRTCSIP-MCUFactory classes and does not have attributes itself.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-MCUFactory  <br/> |This class is a container representing a Conferencing Server Factory for a single medium type. An instance of this class is created when the first Conferencing server for this particular type and vendor is activated.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-MCUFactoryService  <br/> |This class provides an association from a specific pool to its Conferencing Server Factory.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-MediationServer  <br/> |This class holds the entry for the service control point for a Mediation Server.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-Meeting (obsolete)  <br/> |This auxiliary class to msRTCSIP-GlobalContainer holds attributes representing configurable meeting settings.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-Mobility  <br/> |Container that stores the global mobility settings.  <br/> |-  <br/> |
|msRTCSIP-MonitoringServer  <br/> |This class holds attributes that represent settings for a single Monitoring Server.  <br/> |New in Communications Server 2007 R2.  <br/> |
|msRTCSIP-PhoneRoute (obsolete)  <br/> |This class is a container representing an instance of a least cost route to a gateway or set of gateways. This information is used by all Enterprise pools or servers running Standard Edition to route outgoing calls to the public switched telephone network (PSTN) in the most cost effective way.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-PhoneRoutes (obsolete)  <br/> |This class is a container for multiple, least cost routes and does not contain any attributes itself.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-Policies (obsolete)  <br/> |This class holds multiple Lync Server policy classes and does not have any attributes itself.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-Pool  <br/> |This class represents a single Skype for Business Server pool.  <br/> |-  <br/> |
|msRTCSIP-Pools  <br/> |This class holds multiple Skype for Business Server pools and does not have any attributes itself.  <br/> |-  <br/> |
|msRTCSIP-PoolService  <br/> |This class represents the service control pointservice control point of a pool. Users hosted on a pool have their msRTCSIP-PrimaryHomeServer attribute point to an instance of this class.  <br/> |-  <br/> |
|msRTCSIP-Presence  <br/> |Container that stores the global presence settings.  <br/> |-  <br/> |
|msRTCSIP-Registrar  <br/> |This auxiliary class to msRTCSIP-GlobalContainer holds attributes representing user settings maintained by the SIP Registrar servers.  <br/> |-  <br/> |
|msRTCSIP-RouteUsage (obsolete)  <br/> |This class is a container representing an instance of a phone route usage. A phone route usage class consists of an attribute field and a description field. The attribute field defines a usage type. The description field allows administrators to describe the usage for this attribute in the phone route.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-RouteUsages (obsolete)  <br/> |This class holds multiple instances of the msRTCSIP-RouteUsage class and does not have any attributes itself.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-Search  <br/> |This auxiliary class to msRTCSIP-GlobalContainer holds attributes that limit and control the scope of search results.  <br/> |-  <br/> |
|msRTCSIP-Server  <br/> |This class represents a single server running Skype for Business Server.  <br/> |-  <br/> |
|msRTCSIP-Service  <br/> |This class holds the global settings container and msRTCSIP-Domain objects.  <br/> |-  <br/> |
|msRTCSIP-TrustedMCU  <br/> |This class holds attributes that represent settings for a trusted Conferencing server.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-TrustedMCUs  <br/> |This class holds multiple instances of the msRTCSIP-TrustedMCU class and does not have any attributes itself.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-TrustedProxies  <br/> |This class holds multiple msRTCSIP-TrustedProxy classes and does not contain any attributes itself.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-TrustedProxy  <br/> |This class is a container representing a server running Proxy Server. An instance of this class is created when activating a new Proxy Server on a computer joined to AD DS.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-TrustedServer  <br/> |This class holds attributes that represent settings for a trusted server.  <br/> |-  <br/> |
|msRTCSIP-TrustedService  <br/> |This class is a container representing a trusted service that is routable using a Globally Routable User Agent URI (GRUU) address. An instance of this class is created when a new server that is trusted by Skype for Business Server is activated. This trusted server must be joined to an Active Directory domain.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-TrustedServices  <br/> |This class is a container for multiple GRUU servers and does not contain any attributes itself.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-TrustedWebComponentsServer  <br/> |This class holds attributes that represent the settings for a trusted web component.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-TrustedWebComponentsServers  <br/> |This class holds multiple instances of the msRTCSIP-TrustedWebComponentServer class and does not have any attributes itself.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-UnifiedCommunications (obsolete)  <br/> |This auxiliary class to msRTCSIP-GlobalContainer holds attributes related to unified communications.  <br/> |Obsolete in Lync Server 2010.  <br/> |
|msRTCSIP-WebComponents  <br/> |This class holds the service control pointservice control point for Internet Information Server (IIS). It identifies a server as a web components server.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-WebComponentsService  <br/> |This class provides an association from a specific pool to the web components that the pool will use.  <br/> |New in Communications Server 2007.  <br/> |
|msRTCSIP-WebComponentSettings  <br/> |This auxiliary class to msRTCSIP-WebComponents holds attributes representing settings for web components.  <br/> |New in Communications Server 2007.  <br/> |
   

