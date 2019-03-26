---
title: 'View Microsoft SIP Processing Language (MSPL) server applications'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: View Microsoft SIP Processing Language (MSPL) server applications
ms:assetid: b7df1323-b6bd-4925-8fe6-5241c91fe51b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182575(v=OCS.15)
ms:contentKeyID: 48185202
ms.date: 09/26/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# View Microsoft SIP Processing Language (MSPL) server applications in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-09-26_

A Microsoft SIP Processing Language (MSPL) server application is a script-only application that uses a scripting language instead of the Microsoft Lync 2010 API. MSPL provides more granular control over filtering and proxy behaviors, in addition to a facility for dispatching specific messages to transaction-based SIP applications. MSPL is used specifically for filtering and routing SIP messages. MSPL applications run in the same process as the UserServices module, while a program that is based on the Lync 2010 API runs in a separate process.

You can use the **Server Application** page in the **Topology** group of Lync Server Control Panel to see a list of MSPL server applications that run on Front End Servers in your Lync Server 2013 environment. The list shows the scripts that are available for each pool, as well as whether they are enabled or critical. The scripts run in the order they are listed.

These scripts include the following:

  - ClientVersionFilter provides the administrator with a way to specify the version of clients that are supported by a pool. The client version filter checks the client version and can either prevent the client from logging on or present the user with a message that indicates he or she is using a client that is not supported. The client version filter can also be configured to display a message to the user that contains the URL of the latest downloadable version of the client.

  - TranslationService translates a number that a user dials to an E.164 number according to the normalization rules defined by the administrator. For details, see [Translation rules in Lync Server 2013](lync-server-2013-translation-rules.md).

  - IncomingFederation enforces tenant-level federation validation for inter-tenant and incoming messages from external deployments.

  - UserServices is the SIP Registrar, presence, and conferencing component of a Front End Server. It provides closely integrated IM, presence, and conferencing features built on top of the SIP Proxy.

  - InterClusterRouting is responsible for routing calls to the callee’s primary Registrar pool. For details, see [Front End Server VoIP components for Lync Server 2013](lync-server-2013-front-end-server-voip-components.md).

  - IIMFilter (Intelligent IM Filter) blocks messages that contain clickable URLs or that attempt to initiate file transfers. IIMFilter also checks the client version on behalf of the server. IIMFilter affects file transfers that are initiated by using either Lync Server or Communicator. By default, clickable links are disabled by adding an underscore character before the first character of the link. An administrator can change this behavior so that the link is blocked, in which case messages that contain clickable URLs or that attempt to initiate a file transfer are blocked by the server from reaching their intended destinations. IIMFilter is installed on all servers running Lync Server except Proxy Servers and Archiving Servers.

  - UserPinService is used to verify user personal identification numbers (PINs) for dial-in conferencing.

  - DefaultRouting is the default routing application for servers running Lync Server. It is enabled by default. The routing application is installed on all Standard Edition and Enterprise Edition servers.

  - ExumRouting routes calls to Exchange Server Unified Messaging (UM). ExumRouting determines the appropriate Exchange UM server to route the call to when there is a new voice mail message to deposit. ExumRouting also handles some other Exchange UM integration aspects, including routing to Auto Attendant and Subscriber Access.

  - OutboundRouting determines the gateway that routes a call to a phone number according to the dialed number and the user’s dialing authorization. OutboundRouting also handles rerouting of calls if a gateway cannot process a call.

  - QoEAgent receives Quality of Experience (QoE) data reports from endpoints through SIP SERVICE requests, and sends the data to the destination queue on the Monitoring Server or to third-party consumers using HTTP POST. For details, see [Deploying monitoring in Lync Server 2013](lync-server-2013-deploying-monitoring.md).

  - OutgoingFederation enforces tenant-level federation validation for messages going to a targeted external deployment.

  - AcpRouting proxies INVITE requests destined for the audio conferencing provider to the audio conferencing provider gateway.

Scripts that run on Edge Servers include the following:

  - IIMFilter

  - OptionsHandler responds to incoming OPTIONS requests with **200 OK** if the request is destined for the current server. This is used for topology validation.

<div>

## See Also


[Enable or disable a Microsoft SIP Processing Language (MSPL) server application in Lync Server 2013](lync-server-2013-enable-or-disable-a-microsoft-sip-processing-language-mspl-server-application.md)  
[Mark a Microsoft SIP Processing Language (MSPL) application as critical or not critical in Lync Server 2013](lync-server-2013-mark-a-microsoft-sip-processing-language-mspl-application-as-critical-or-not-critical.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

