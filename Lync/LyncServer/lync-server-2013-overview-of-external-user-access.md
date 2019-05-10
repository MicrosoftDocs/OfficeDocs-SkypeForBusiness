---
title: 'Lync Server 2013: Overview of external user access'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Overview of external user access
ms:assetid: 97aded6c-5fa3-4225-95a6-9ad094d61654
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398775(v=OCS.15)
ms:contentKeyID: 48184934
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Overview of external user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

In this documentation, we use the term *external user* to define a large category of users who communicate with your Lync Server 2013 and Lync 2013 users from outside the firewall. External users that you can authorize to communicate Lync Server 2013 with internal users (that is, users who sign in to Lync Server from inside the firewall) can include the following:

  - **Remote users**   Users of your organization who sign in to Lync Server from outside the firewall.

  - **Federated users**   Users who have an account with a trusted customer or partner organization, such as Lync Server 2010, Lync Server 2013 or Office Communications Server 2007 R2. Federated users can also be members of defined partner organizations using extensible messaging and presence protocol (XMPP) by way of the XMPP proxy on the Edge Server and XMPP gateway on the Front End Server or pool. A defined trust relationship, called a federation, is not related to or dependent upon an Active Directory Domain Services trust relationship.
    
    <div>
    

    > [!NOTE]  
    > An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Support for public instant messenger connectivity in Lync Server 2013</A>.

    
    </div>

  - **Public Instant Messaging Connectivity users**   Contacts that your users establish through public instant messaging connectivity services (Windows Live, Yahoo\! and AOL).

  - **Mobile users**   Users that are members of your organization that use a smart phone or tablet running a Lync Mobile client sign in to your internal deployment and are able to communicate with the other classes of users. The mobile user uses mobility services that are published through the reverse proxy to access the internal deployment. For details on features and capabilities available to Lync Mobile , see the Mobile Client Comparison Tables at [http://go.microsoft.com/fwlink/p/?LinkID=234777](http://go.microsoft.com/fwlink/p/?linkid=234777).

  - **Anonymous users**   Users who do not have a user account in your organization's Active Directory Domain Services or in a supported federated domain, but who have received invitations to participate remotely in an on-premises conference.

Your edge deployment provides external access for the following types of communication:

  - **IM and presence**   Authorized external users can participate in IM conversations and conferences, and they can get information about one another’s presence status. Users of public IM service providers can participate in IM conversations with individual Lync Server users in your organization and access presence information, but they cannot participate in IM multiparty conferences using Lync Server. It is strictly peer-to-peer communication. File transfer is not supported for users of public IM service providers, and audio/video in peer-to-peer communications is supported for Windows Messenger 2011 users, but not other users of public IM service providers.
    
    Both SIP and XMPP protocols are supported. To provide services for XMPP, see [Planning for SIP, XMPP federation, and public instant messaging in Lync Server 2013](lync-server-2013-planning-for-sip-xmpp-federation-and-public-instant-messaging.md).

  - **Web conferencing**   Authorized external users can participate in conferences that are hosted on your Lync Server deployment. Remote users, federated users, and anonymous users can be enabled for participation in web conferencing, but public IM users cannot participate in conferences. Depending on the options that you select, web conferencing-enabled users can participate in desktop and application sharing and can act as meeting organizers or presenters.

  - **A/V conferencing**   Authorized external users can participate in audio and video conferences that your Lync Server deployment hosts. Audio/video in peer-to-peer communications is supported for Windows Messenger 2011 users, but not for other users of public IM service providers.

In order to control communications, you can configure one or more policies that define how users inside and outside your organization communicate with each other. You can also configure settings and apply policies for individual internal users or for specific types of external users to control communications with external users.

Lync Server 2013 roles that are used to provide external access:

**Edge Server**   The Edge Server is a server or a pool of servers that run the services that allow external access to IM and presence, conferencing, audio/video, and other media (for example, file transfer) services. Optionally, you can configure the Edge Server to federate with other Lync Server or Office Communications Server 2007 R2 deployments, and other XMPP deployments. The optional public IM connectivity feature is enabled and configured through the Edge Server.

**Director**   The Director is an optional server or server pool running the Lync Server 2013 Director role that pre-authenticates user requests and routes requests to the users’ home Front End Server or Front End pool, but does not home any user accounts.

**Reverse Proxy**   A reverse proxy is a general term for specialized servers that publish resources available on the internal network and retrieve information for clients from the published resource. Lync Server 2013 uses the reverse proxy to publish a number of features, such as conferencing meetings, conference join locations, the address book, distribution list expansion, downloading meeting content, device updates, Mobility services, and more. Any reverse proxy that can meet the requirements for publishing the necessary resource locations can be used. Microsoft Forefront Threat Management Gateway (TMG) 2010 is used as an example for the purposes of illustrating the publishing rules necessary, but Forefront TMG 2010 is not required.

<div>


> [!IMPORTANT]  
> Lync Server 2013 supports both IPv4 and IPv6. Windows Server&nbsp;2008&nbsp;R2, Windows Server 2012, and Windows Server 2012 R2 use a dual stack that can use both IPv4 and IPv6 concurrently. This is important because of the transitional nature of a deployment moving from IPv4 to IPv6. IPv4 can be supported in some areas, where in other areas of the deployment, IPv6 can be used. This is especially important where the Internet and internal deployments are concerned. External clients must communicate through the reverse proxy to use services such as mobility, meetings, address book download, and others. Currently, Forefront Threat Management Gateway 2010 and Internet Security and Acceleration Server 2006 do not support IPv6 addressing, regardless of the operating system version that they are deployed on. You must plan accordingly in relation to your use of IPv6 and IPv4 as they relate to external clients.



</div>

</div>

<span> </span>

</div>

</div>

</div>

