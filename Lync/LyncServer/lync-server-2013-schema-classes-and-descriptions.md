---
title: 'Lync Server 2013: Schema classes and descriptions'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Schema classes and descriptions
ms:assetid: 7d43b920-ac37-40cc-adfe-be289bda6e9e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398625(v=OCS.15)
ms:contentKeyID: 48184612
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Schema classes and descriptions in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-30_

This section describes all the schema classes used by Lync Server 2013.

<div>

## Schema Classes and Descriptions


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Class</th>
<th>Description</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mail-Recipient</p></td>
<td><p>Exchange Unified Messaging (UM) email recipient.</p></td>
<td><p>This auxiliary class is shared with Exchange UM.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationContacts</p></td>
<td><p>This class is a container for multiple application contacts and does not contain any attributes itself.</p></td>
<td><p>New in Microsoft Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationServer</p></td>
<td><p>This class holds the entry for the service control point for an instance of Unified Communications Application Services (UCAS).</p></td>
<td><p>New in Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationServerService</p></td>
<td><p>This class provides an association from a specific pool to its Application service.</p></td>
<td><p>New in Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationServerSettings</p></td>
<td><p>This auxiliary class to msRTCSIP-ApplicationServer holds attributes representing settings for instances of the Application service.</p></td>
<td><p>New in Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Archive (obsolete)</p></td>
<td><p>This auxiliary class to msRTCSIP-GlobalContainer holds all settings related to archiving.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchivingServer (obsolete)</p></td>
<td><p>This class represents a single instant messaging Archiving Server. An instance of this class is created when a computer is activated as an instant messaging Archiving Server, such as a computer with the Instant Messaging Archiving service installed.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ConferenceDirectories</p></td>
<td><p>This class is a container for multiple instances of conference directories and does not contain any attributes itself.</p></td>
<td><p>New in Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ConferenceDirectory</p></td>
<td><p>This class holds attributes representing settings for a specific conference directory.</p></td>
<td><p>New in Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ConnectionPoint</p></td>
<td><p>Generic service control point (SCP) to specify the computer as a server running Lync Server.</p></td>
<td><p>New in Lync 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultCWABank</p></td>
<td><p>This auxiliary class holds the settings for a Microsoft Lync Web App bank.</p></td>
<td><p>New in Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Domain</p></td>
<td><p>This class holds attributes that define the configured domains of the SIP Registrar.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EdgeProxy</p></td>
<td><p>This class container represents a single Access Edge service. Because an Access Edge service is deployed in the perimeter network and customers usually do not allow Active Directory Domain Services access from the perimeter network, instances of Access Edge service are not joined to the intranet’s Active Directory network. Therefore, Access Proxies are not automatically registered in AD DS. The administrator must manually configure the existence of each instance of Access Edge service in AD DS.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnterpriseMCUSettings</p></td>
<td><p>This auxiliary class to msRTCSIP-MCU holds attributes representing settings for Conferencing servers.</p></td>
<td><p>New in Microsoft Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EnterpriseMediationServerSettings</p></td>
<td><p>This auxiliary class to msRTCSIP-MediationServer holds attributes representing settings for Mediation Servers.</p></td>
<td><p>New in Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnterpriseServerSettings</p></td>
<td><p>This auxiliary class to msRTCSIP-Server holds attributes representing settings for SIP servers.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Federation</p></td>
<td><p>This auxiliary class to msRTCSIP-GlobalContainer holds all settings related to federation.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalContainer</p></td>
<td><p>This class holds all settings that apply throughout a Lync Server deployment.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-GlobalUserPolicy (obsolete)</p></td>
<td><p>This class represents a single Office Communications Server meeting policy.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalTopologySetting</p></td>
<td><p>The local global topology setting object.</p></td>
<td><p>New in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-GlobalTopologySettings</p></td>
<td><p>Container to hold global topology setting objects.</p></td>
<td><p>New in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocalNormalization</p></td>
<td><p>This class is a container that represents an instance of a location normalization rule.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocationContactMapping</p></td>
<td><p>This class is created by the Conferencing Attendant application and holds attributes used to categorize conference telephone numbers by region.</p></td>
<td><p>New in Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationContactMappings</p></td>
<td><p>This class is a container for multiple instances of location contact mappings and does not contain any attributes itself.</p></td>
<td><p>New in Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocationProfile</p></td>
<td><p>This class is a container that represents a specific location profile.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationProfiles (obsolete)</p></td>
<td><p>This class is a container for multiple location profiles and does not contain any attributes itself.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocalNormalizations (obsolete)</p></td>
<td><p>This class is a container for multiple local normalization rules and does not contain any attributes itself.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCU</p></td>
<td><p>This class represents a single Conferencing server.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactories</p></td>
<td><p>This class holds multiple msRTCSIP-MCUFactory classes and does not have attributes itself.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUFactory</p></td>
<td><p>This class is a container representing a Conferencing Server Factory for a single medium type. An instance of this class is created when the first Conferencing server for this particular type and vendor is activated.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactoryService</p></td>
<td><p>This class provides an association from a specific pool to its Conferencing Server Factory.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MediationServer</p></td>
<td><p>This class holds the entry for the service control point for a Mediation Server.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Meeting (obsolete)</p></td>
<td><p>This auxiliary class to msRTCSIP-GlobalContainer holds attributes representing configurable meeting settings.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Mobility</p></td>
<td><p>Container that stores the global mobility settings.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MonitoringServer</p></td>
<td><p>This class holds attributes that represent settings for a single Monitoring Server.</p></td>
<td><p>New in Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PhoneRoute (obsolete)</p></td>
<td><p>This class is a container representing an instance of a least cost route to a gateway or set of gateways. This information is used by all Enterprise pools or servers running Standard Edition to route outgoing calls to the public switched telephone network (PSTN) in the most cost effective way.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PhoneRoutes (obsolete)</p></td>
<td><p>This class is a container for multiple, least cost routes and does not contain any attributes itself.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Policies (obsolete)</p></td>
<td><p>This class holds multiple Lync Server policy classes and does not have any attributes itself.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Pool</p></td>
<td><p>This class represents a single Lync Server pool.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Pools</p></td>
<td><p>This class holds multiple Lync Server pools and does not have any attributes itself.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolService</p></td>
<td><p>This class represents the service control pointservice control point of a pool. Users hosted on a pool have their msRTCSIP-PrimaryHomeServer attribute point to an instance of this class.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Presence</p></td>
<td><p>Container that stores the global presence settings.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Registrar</p></td>
<td><p>This auxiliary class to msRTCSIP-GlobalContainer holds attributes representing user settings maintained by the SIP Registrar servers.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-RouteUsage (obsolete)</p></td>
<td><p>This class is a container representing an instance of a phone route usage. A phone route usage class consists of an attribute field and a description field. The attribute field defines a usage type. The description field allows administrators to describe the usage for this attribute in the phone route.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-RouteUsages (obsolete)</p></td>
<td><p>This class holds multiple instances of the msRTCSIP-RouteUsage class and does not have any attributes itself.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Search</p></td>
<td><p>This auxiliary class to msRTCSIP-GlobalContainer holds attributes that limit and control the scope of search results.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Server</p></td>
<td><p>This class represents a single server running Lync Server.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Service</p></td>
<td><p>This class holds the global settings container and msRTCSIP-Domain objects.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedMCU</p></td>
<td><p>This class holds attributes that represent settings for a trusted Conferencing server.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedMCUs</p></td>
<td><p>This class holds multiple instances of the msRTCSIP-TrustedMCU class and does not have any attributes itself.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedProxies</p></td>
<td><p>This class holds multiple msRTCSIP-TrustedProxy classes and does not contain any attributes itself.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedProxy</p></td>
<td><p>This class is a container representing a server running Proxy Server. An instance of this class is created when activating a new Proxy Server on a computer joined to AD DS.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServer</p></td>
<td><p>This class holds attributes that represent settings for a trusted server.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedService</p></td>
<td><p>This class is a container representing a trusted service that is routable using a Globally Routable User Agent URI (GRUU) address. An instance of this class is created when a new server that is trusted by Lync Server is activated. This trusted server must be joined to an Active Directory domain.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServices</p></td>
<td><p>This class is a container for multiple GRUU servers and does not contain any attributes itself.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedWebComponentsServer</p></td>
<td><p>This class holds attributes that represent the settings for a trusted web component.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedWebComponentsServers</p></td>
<td><p>This class holds multiple instances of the msRTCSIP-TrustedWebComponentServer class and does not have any attributes itself.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UnifiedCommunications (obsolete)</p></td>
<td><p>This auxiliary class to msRTCSIP-GlobalContainer holds attributes related to unified communications.</p></td>
<td><p>Obsolete in Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponents</p></td>
<td><p>This class holds the service control pointservice control point for Internet Information Server (IIS). It identifies a server as a web components server.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-WebComponentsService</p></td>
<td><p>This class provides an association from a specific pool to the web components that the pool will use.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponentSettings</p></td>
<td><p>This auxiliary class to msRTCSIP-WebComponents holds attributes representing settings for web components.</p></td>
<td><p>New in Communications Server 2007.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

