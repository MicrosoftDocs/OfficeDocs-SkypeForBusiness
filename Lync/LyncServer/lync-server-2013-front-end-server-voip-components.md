---
title: 'Lync Server 2013: Front End Server VoIP components'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Front End Server VoIP components
ms:assetid: 310e81a7-da45-47d4-95d0-92837e386502
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425812(v=OCS.15)
ms:contentKeyID: 48183765
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Front End Server VoIP components for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

The VoIP components located on Front End Servers are as follows:

  - Translation Service

  - Inbound Routing component

  - Outbound Routing component

  - Exchange UM Routing component

  - Intercluster Routing component

  - [Mediation Server component in Lync Server 2013](lync-server-2013-mediation-server-component.md)

<div>

## Translation Service

The Translation Service is the server component that is responsible for translating a dialed number into the E.164 format or another format, according to the normalization rules that are defined by the administrator. The Translation Service can translate to formats other than E.164 if your organization uses a private numbering system or uses a gateway or PBX that does not support E.164.

</div>

<div>

## Inbound Routing Component

The Inbound Routing component handles incoming calls largely according to preferences that are specified by users on their Enterprise Voice clients. It also facilitates delegate ringing and simultaneous ringing, if configured by the user. For example, users specify whether unanswered calls are forwarded or simply logged for notification. If call forwarding is enabled, users can specify whether unanswered calls should be forwarded to another number or to a Exchange UM server that has been configured to provide call answering. The Inbound Routing component is installed by default on all Standard Edition server and Front End Servers.

</div>

<div>

## Outbound Routing Component

The Outbound Routing component routes calls to PBX or PSTN destinations. It applies call authorization rules, as defined by the user’s voice policy, to callers and determines the optimal PSTN gateway for routing each call. The Outbound Routing component is installed by default on all Standard Edition server and Front End Servers.

The routing logic that is used by the Outbound Routing component is in large measure configured by network or telephony administrators according to the requirements of their organizations.

</div>

<div>

## Exchange UM Routing Component

The Exchange UM routing component handles routing between Lync Server and servers running Exchange Unified Messaging (UM), to integrate Lync Server with Unified Messaging features.

The Exchange UM routing component also handles rerouting of voice mail over the PSTN if Exchange UM servers are unavailable. If you have Enterprise Voice users at branch sites that do not have a resilient WAN link to a central site, the Survivable Branch Appliance that you deploy at the branch site provides voice mail survivability for branch users during a WAN outage. When the WAN link is unavailable, the Survivable Branch Appliance does the following:

  - reroutes unanswered calls over the PSTN to the Exchange Unified Messaging server in the central site

  - provides the ability for a user to retrieve voice mail messages over the PSTN

  - queues missed call notifications, and then uploads them to the Exchange UM server when the WAN link is restored.

To enable voice mail rerouting, we recommend that your Exchange administrator configure Exchange UM Auto Attendant (AA) to accept messages only.

For details about these features, see [Planning for Exchange Unified Messaging integration in Lync Server 2013](lync-server-2013-planning-for-exchange-unified-messaging-integration.md) and [Planning for Enterprise Voice resiliency in Lync Server 2013](lync-server-2013-planning-for-enterprise-voice-resiliency.md), respectively.

</div>

<div>

## Intercluster Routing Component

The Intercluster routing component is responsible for routing calls to the callee’s primary Registrar pool. If that is unavailable, the component routes the call to the callee’s backup Registrar pool. If the callee’s primary and backup Registrar pools are unreachable over the IP network, the Intercluster routing component reroutes the call over the PSTN to the user’s telephone number.

</div>

<div>

## Other Front End Server Components Required for VoIP

Other components residing on the Front End Server or Director that provide essential support for VoIP, but are not themselves VoIP components, include the following:

  - **User Services.** Perform reverse number lookup on the destination phone number of each incoming call and match that number to the SIP URI of the destination user. Using this information, the Inbound Routing component distributes the call to that user’s registered SIP endpoints. User Services is a core component on all Front End Servers and Directors.

  - **User Replicator.** Extracts user phone numbers from Active Directory Domain Services and writes them to tables in the RTC database, where they are available to User Services and Address Book Server. User Replicator is a core component on all Front End Servers.

  - **Address Book Server.** Provides global address list information from Active Directory Domain Services to Lync Server clients. It also retrieves user and contact information from the RTC database, writes the information to the Address Book files, and then stores the files on a shared folder where they are downloaded by Lync clients. The Address Book Server writes the information to the RTCAb database, which is used by the Address Book Web Query service to respond to user search queries from Microsoft Lync 2010 Mobile. It optionally normalizes enterprise user phone numbers that are written to the RTC database for the purpose of provisioning user contacts in Lync. The Address Book service is installed by default on all Front End Servers. The Address Book Web Query service is installed by default with the Web services on each Front End Servers.

</div>

</div>

<span> </span>

</div>

</div>

</div>

