---
title: 'Lync Server 2013: Changes in Lync Server that affect Edge Server planning'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Changes in Lync Server 2013 that affect Edge Server planning
ms:assetid: 66305160-c9b8-4bc4-9f24-8ee8d9a294f7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204965(v=OCS.15)
ms:contentKeyID: 48184378
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Changes in Lync Server 2013 that affect Edge Server planning

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

Lync Server 2013 introduces new features that extend the features and communications methods for your users. Also, Lync Server 2013 introduces changes to existing services to better integrate and extend the services that are available to your organization. Following is a summary of changes that may affect your planning and deployment of Lync Server 2013 Edge Server services.

<div>

## Support for IPv6 Addressing

Lync Server 2013 supports IPv6 addressing for all Edge Server services. If you have provided IPv6 addresses for the interfaces through configuration in Windows Server, you can use IPv6 addresses in your Edge Server configuration through the IP address configuration in Topology Builder. Additionally, the extensible messaging and presence protocol (XMPP) supports IPv6. No additional configuration is required. If IPv6 is configured in the topology, XMPP will use IPv6 (where required).

An added requirement to support IPv6 in Lync Server 2013 is to create domain name system records for records that must be discovered and resolved to an IPv6 address. IPv6 DNS uses host records that are defined as **AAAA** and called “quad-A”. Other record types are consistent with their IPv4 counterparts.

</div>

<div>

## Support for Extensible Messaging and Presence Protocol (XMPP) Deployment

Edge Server introduces a fully integrated XMPP proxy (deployed on the Edge Servers) and an XMPP gateway (deployed on your Front End Servers). You can deploy XMPP federation as an optional component. By adding and configuring the XMPP proxy and XMPP gateway, you can enable your Microsoft Lync 2013 users to add contacts from XMPP-based partners for instant messaging (IM) and presence.

<div>


> [!NOTE]  
> Currently, the XMPP services in Edge Server only provide IM and presence between Lync Server clients and XMPP-based contacts. Additionally, XMPP is hosted in only one site.



</div>

<div>


> [!IMPORTANT]  
> The XMPP capability of Lync Server 2013 is tested and supported by Microsoft for instant messaging federation with Google Talk. For any other XMPP systems contact the third-party vendor to verify that they support federation with Lync Server 2013, and for any deployment or troubleshooting recommendations.



</div>

</div>

<div>

## Support for Rolling Audio/Video Authentication and Server to Server Authentication Certificates

A certificate is used to generate tokens that are issued to clients and other consumers of the A/V Authentication service and for server to server authentication. The Audio/Video Authentication certificate is of type *AudioVideoAuthentication* and the Server to Server Authentication certificate is of type *OAuthTokenIssuer*.

For Audio/Video Authentication, tokens are used to authenticate port allocation requests, and the tokens are cached for up to 8 hours – the default lifetime of the token. Under normal operation, this is a very reliable method to create and distribute authentication material to the A/V consumers. However, certificates have a finite lifetime and expire on a predefined date and time (based on creation date and the policies enforced at the certification authority that created the certificate, typically 2 years for this type of certificate). When the certificate expires, any tokens created by the expired certificate and cached by consumers become not valid. Any attempts to use a token created with an expired certificate would result in failed Media Relay allocations and any current Audio/Video sessions will fail. The client would need to acquire a new token created by a valid certificate to resume normal Audio and Video functionality.

Server to Server Authentication is managed by a global certificate that is requested and applied to all servers in the deployment. The certificate is responsible for authenticating servers in Lync Server 2013 as well as authenticating to Exchange 2013 and Microsoft SharePoint Server 2013. For more information on how Server to Server Authentication works, see [Managing server-to-server authentication (OAuth) and partner applications in Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md). One very important difference between the Audio/Video Authentication process and the Server to Server Authentication process is the lifetime of the authentication, or tokens. For Audio/Video Authentication, the authentication expires after eight hours. Server-to-Server Authentication has a lifetime of 24 hours. You must plan accordingly for each of the certificate types.

New for Lync Server 2013 is the ability to stage a replacement Audio/Video Authentication certificate and Server to Server Authentication certificate in advance of the expiration of the current certificate. The new certificate is then used for generating new tokens or new authentication requests. but retains the old certificate for verifying the current sessions and authentications.. What this accomplishes is to effectively prevent nearly all failures due to token and certificate expirations. For details of this feature and how to configure it, see [Staging AV and OAuth certificates in Lync Server 2013 using -Roll in Set-CsCertificate](lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-https://docs.microsoft.com/powershell/module/skype/Set-CsCertificate)

</div>

<div>

## Reduced Reliance on Cookie-based Affinity

In previous versions of Lync Server and Office Communications Server, cookie-based affinity was used by the Web services to ensure that the client and Web services session state was maintained. Lync Server 2013 Web services use a built in affinity mechanism that eliminates most of the requirements for cookie-based affinity.

<div>


> [!WARNING]  
> The Microsoft Lync 2010 Mobile client must still use cookie-based affinity and will require configuration of cookie-based affinity until you have migrated all clients to the upcoming Microsoft Lync Mobile client (Date of release not yet determined).



</div>

For details about cookie-based affinity in Lync Server 2013, see [Components required for external user access in Lync Server 2013](lync-server-2013-components-required-for-external-user-access.md).

</div>

<div>

## AutoDiscover Enhancements

The autodiscover feature in Lync Server 2013 enables clients to locate additional features that are made available for communication. Autodiscover was first introduced in the cumulative update for Lync Server 2010: November 2011 for Mobility and Microsoft Lync 2010 Mobile. The autodiscover feature (also known by the DNS record names LyncDiscover and LyncDiscoverInternal) allows clients to locate and use mobility services (for Microsoft Lync 2010 Mobile clients), the Microsoft Lync Web App, and the Lync Web scheduler, as well as communications with Microsoft Exchange Server and SharePoint Server. Autodiscover is installed as normal part of the setup and deployment of your infrastructure and Lync Server 2013 servers. The Topology Builder and Lync Server Deployment Wizard eliminate most of the configuration tasks that were required in cumulative update for Lync Server 2010: November 2011.

</div>

<div>

## Services for Mobile Clients

Introduced in the cumulative update for Lync Server 2010: November 2011, mobility services in Lync Server 2013 enable mobile phones running Lync Mobile and tablet devices using supported Apple iOS, Android, Windows Phone, or Nokia mobile devices to perform activities such as sending and receiving instant messages, viewing contacts, and viewing presence. In addition, mobile devices support some Enterprise Voice features, such as click to join a conference, Call via Work, single number reach, voice mail, and missed call notification.

<div>


> [!NOTE]  
> The mobility services use the reverse proxy and published services that are deployed on your Front End Servers. No changes are required to Edge Servers. Minimally you need outbound SIP/TCP/5061from the server running the Lync Server Access Edge service.



</div>

</div>

<div>

## Director Role is Optional

The role of the Director server in the Lync Server 2013 topology has not changed. It still hosts web services, preauthenticates incoming user requests, and directs external users to their home pool. By changing the Director from a recommended role to an optional role, Microsoft does not intend to diminish the value of the Director. The intention is to reduce server count and other hardware requirements (for example, hardware load balancers for the Director) without compromising features and functionality. Because the Front End Servers can do the same job as the Director with no impact to services provided, you can deploy Directors if you choose to. You can safely exclude the Director with confidence that the Front End Servers will provide the same services in place of a Director.

</div>

</div>

<span> </span>

</div>

</div>

</div>

