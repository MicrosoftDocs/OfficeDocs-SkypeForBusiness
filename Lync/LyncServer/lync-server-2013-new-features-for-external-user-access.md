---
title: 'Lync Server 2013: New features for external user access'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: New features for external user access
ms:assetid: 99da6bd5-ec14-4ad9-8f7d-37fbddf567dd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398794(v=OCS.15)
ms:contentKeyID: 48184884
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New features for external user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-17_

Lync Server 2013 introduces new features that extend the features and communications methods for your users. Also, Lync Server 2013 introduces changes to existing services to better integrate and extend the services that are available to your organization. Following is a summary of changes that may affect your planning and deployment of Lync Server 2013 Edge Server services.

  - **Support for IPv6 addressing**   Lync Server 2013 supports IPv6 addressing for all Edge Server services. If you have provided IPv6 addresses for the interfaces through configuration in Windows Server, you can use IPv6 addresses in your Edge Server configuration through the IP address configuration in Topology Builder.
    
    <div>
    

    > [!IMPORTANT]  
    > Use of IPv6 addresses in Lync Server 2013 depends on support of IPv6 in routers and firewalls that your organization deploys, as well as support through your Internet service provider.

    
    </div>

  - **Extensible Messaging and Presence Protocol (XMPP)**   Lync Server 2013 introduces a fully integrated XMPP proxy (deployed on the Edge Servers) and an XMPP gateway deployed on your Front End Servers. You can deploy XMPP federation as an optional component. Adding and configuring the XMPP proxy and XMPP gateway will allow your Microsoft Lync 2013 users to add contacts from XMPP-based partners for instant messaging (IM) and presence.
    
    <div>
    

    > [!NOTE]  
    > Currently, the XMPP services in Lync Server 2013 only provide instant messaging and presence between Lync clients and XMPP-based contacts.

    
    </div>

  - **Mobility services for Mobile clients**   Introduced in a customer update for Lync Server 2010, Mobility services in Lync Server 2013 allow Microsoft Lync Mobile clients on mobile phones and tablet devices using supported Apple iOS, Android, Windows Phone, or Nokia mobile devices to perform such activities as sending and receiving instant messages, viewing contacts, and viewing presence. In addition, mobile devices support some Enterprise Voice features, such as click to join a conference, Call via Work, single number reach, voice mail, and missed call notification.
    
    <div>
    

    > [!NOTE]  
    > The mobility services use the reverse proxy and published services that are deployed on your Front End Servers. No changes are required to Edge Servers.

    
    </div>

  - **Directors are an optional role**   The role of the Director server in the Lync Server 2013 topology has not changed. It still hosts web services, pre-authenticates incoming user requests, and directs external users to their home pool. Changing the Director from a recommended role to an optional role does not diminish the value of the Director, but emphasizes reducing server count and other hardware requirements (for example, hardware load balancers for the Director) requirements without compromising features and functionality. Because the Front End Servers can do the same job as the Director with no impact to services provided, you can optionally deploy Directors if you choose to. You can safely exclude the Director with confidence that the Front End Servers will provide the same services in their place.

<div>

## See Also


[Planning for and configuring IPv6 in Lync Server 2013](lync-server-2013-planning-for-and-configuring-ipv6.md)  


[Planning for external user access in Lync Server 2013](lync-server-2013-planning-for-external-user-access.md)  
[Planning for extensible messaging and presence protocol (XMPP) federation in Lync Server 2013](lync-server-2013-planning-for-extensible-messaging-and-presence-protocol-xmpp-federation.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

