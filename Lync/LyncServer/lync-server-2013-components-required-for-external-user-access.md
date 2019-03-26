---
title: 'Lync Server 2013: Components required for external user access'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Components required for external user access
ms:assetid: 2d0f9817-14e7-4109-95dc-62420e3c29e2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425779(v=OCS.15)
ms:contentKeyID: 48183711
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Components required for external user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-29_

Most Edge components are deployed in a perimeter network. The following components make up the edge topology of the perimeter network. Except where noted, the components are part of the [Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md) and are in the perimeter network. Edge components include the following:

  - Edge Servers

  - Reverse proxies

  - Firewalls

  - Directors (optional, and logically located on the internal network)

  - Load balancing for Scaled Edge Topologies (either DNS load balancing or a hardware load balancer)
    
    <div>
    

    > [!IMPORTANT]  
    > Using DNS load balancing on one interface and hardware load balancing on the other is not supported. You must use hardware load balancing for both interfaces or DNS load balancing for both.

    
    </div>

<div>

## Edge Servers

The Edge Servers send and receive network traffic for the services offered by internal deployment by external users. The Edge Server runs the following services:

  - **Access Edge service**   The Access Edge service provides a single, trusted connection point for both outbound and inbound Session Initiation Protocol (SIP) traffic.

  - **Web Conferencing Edge service**   The Web Conferencing Edge service enables external users to join meetings that are hosted on your internal Lync Server 2013 deployment.

  - **A/V Edge service**   The A/V Edge service makes audio, video, application sharing, and file transfer available to external users. Your users can add audio and video to meetings that include external participants, and they can communicate using audio and/or video directly with an external user in point-to-point sessions. The A/V Edge service also provides support for desktop sharing and file transfer.

  - **XMPP Proxy service**   The XMPP Proxy service accepts and sends extensible messaging and presence protocol (XMPP) messages to and from configured XMPP Federated partners.

Authorized external users can access the Edge Servers in order to connect to your internal Lync Server 2013 deployment, but the Edge Servers do not provide a means for any other access to the internal network.

<div>


> [!NOTE]  
> Edge servers are deployed to provide connections for enabled Lync clients and other Microsoft Edge servers (as in federation scenarios). They are not designed to allow connections from other end point client or server types. The XMPP Gateway server can be deployed to allow connections with configured XMPP partners. The Edge server and XMPP Gateway can only support end point connections from these client and federation types.



</div>

</div>

<div>

## Reverse Proxy

The reverse proxy is required for the following:

  - To allow users to connect to meetings or dial-in conferences using simple URLs

  - To enable external users to download meeting content

  - To enable external users to expand distribution groups

  - To allow the user to obtain a user-based certificate for client certificate based authentication

  - To enable remote users to download files from the Address Book Server or to submit queries to the Address Book Web Query service

  - To enable remote users to obtain updates to client and device software

  - To enable mobile devices to automatically discover Front End Servers offering mobility services

  - To enable push notifications to mobile devices from the Office 365 or Apple push notification services

For additional information related to reverse proxies and the requirements that reverse proxies must meet, see the details in [Configuration requirements for reverse proxy in Lync Server 2013](lync-server-2013-configuration-requirements-for-reverse-proxy.md).

<div>


> [!NOTE]  
> External users do not need a virtual private network (VPN) connection to your organization in order to participate in communications using Lync Server 2013. If you have implemented VPN technology in your organization and your users use the VPN for Lync, media traffic (such as video conferencing) can be adversely affected. You should consider providing a means for media traffic to connect to the AV Edge service directly and bypass the VPN. For details, see the NextHop Blog article, “Enabling Lync Media to Bypass a VPN Tunnel,” at <A href="http://go.microsoft.com/fwlink/p/?linkid=256532">http://go.microsoft.com/fwlink/p/?LinkId=256532</A>.



</div>

</div>

<div>

## Firewall

You can deploy your edge topology with only an external firewall or both external and internal firewalls. The scenario architectures include two firewalls. Using two firewalls is the recommended approach because it ensures strict routing from one network edge to the other, and it protects your internal deployment behind two levels of firewall.

</div>

<div>

## Director

A Director is a separate, optional server role in Lync Server 2013 that does not home user accounts, or provide presence or conferencing services. It serves as an internal next hop server to which an Edge Server routes inbound SIP traffic destined for internal servers. The Director preauthenticates inbound requests and redirects them to the user’s home pool or server. By preauthenticating at the Director, you can drop requests from user accounts that are unknown to the deployment.

A Director helps insulate Standard Edition servers and Front End Servers in Enterprise Edition Front End pools from malicious traffic such as denial-of-service (DoS) attacks. If the network is flooded with invalid external traffic in such an attack, the traffic ends at the Director. For details about the use of Directors, see [Scenarios for the Director in Lync Server 2013](lync-server-2013-scenarios-for-the-director.md).

</div>

<div>

## See Also


[Hardware load balancer requirements for Lync Server 2013](lync-server-2013-hardware-load-balancer-requirements.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

