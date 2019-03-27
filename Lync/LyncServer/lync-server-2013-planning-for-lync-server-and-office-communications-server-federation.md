---
title: 'Planning for Lync Server and Office Communications Server federation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Planning for Lync Server and Office Communications Server federation
ms:assetid: c9eaf06b-054f-41a4-ad0c-499400d6c4c7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205335(v=OCS.15)
ms:contentKeyID: 48185640
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for Lync Server 2013 and Office Communications Server federation

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-13_

Federation between Microsoft Lync Server 2013, Lync Server 2010 and Office Communications Server supports peer-to-peer and multi-party communications. Peer-to-peer conversations can be escalated to multi-party conversations, allowing for ad hoc meetings. Meetings – Web conferencing or audio/visual conferences – can be scheduled to include contacts inside your organization as well as contacts in partners that you federate with.

Federation first appeared in Microsoft Office Live Communications Server 2005 and supported one kind of federation, Direct Federation. Direct Federation required you to know the federation partner’s session initiation protocol (SIP) domain and the fully qualified domain name (FQDN) of the partner’s Edge Server. Live Communications Server 2005 with SP1 introduced additional federation types, all of which required domain name system (DNS) SRV records to be published by the federated partner to locate their Edge Server. The terminology for that release was:

  - *Open Enhanced Federation*: Accept any SIP domain name and use DNS SRV to locate the partner Edge Server

  - *Enhanced Federation*: Configure the partner’s SIP domain name as a federation partner for your organization and use DNS SRV to find the partner Edge Server

  - *Direct Federation*: Configure the partner’s SIP domain name and the FQDN to the partner’s Edge Server

  - *Server Allow List*: Accept any domain, use DNS SRV to find the Edge Server of a hosting provider or a public instant messaging (IM) connectivity provider

Microsoft Office Communications Server 2007 introduced updated naming for federation types to better define what each federation type actually accomplished:

  - Open Enhanced Federation became known as *Discovered Partner Domain*

  - Enhanced Federation became known as *Allowed Partner Domain*

  - Direct Federation became known as *Allowed Partner Server*

  - Server Allow List became known as *Hosting Provider* and *Public IM Provider*

Microsoft Lync Server 2010 introduced a narrower definition of Hosting Provider in accordance with Microsoft Lync Online 2010 and Microsoft Office 365 and also made it subject to the same allowed list defined by the Allowed Partner Domain federation type.

Enabling federation between Microsoft Lync Server 2013, Lync Server 2010 and Office Communications Server uses the Edge Servers and reverse proxies to enforce the rules and allowed partner domains that you define. From a planning perspective, federating with other Lync Server, Office Communications Server requires the following:

  - Enable federation in Topology Builder. For details, see the Deployment topic [Configuring SIP federation, XMPP federation and public instant messaging in Lync Server 2013](lync-server-2013-configuring-sip-federation-xmpp-federation-and-public-instant-messaging.md).

  - Determine your requirements for federated domain discovery:
    
      - <span></span>  
        For manual configuration of federation, you must have the fully qualified domain name (FQDN) of the partner’s Edge Server and domain name, or online domain name, which is entered in the Lync Server Control Panel, **Federation and External Access**, **SIP Federated Domains**. Create a **New** policy or **Edit** an existing policy to either allow or block domains by FQDN.
        
        <div>
        

        > [!WARNING]
        > Manual configuration of a federation partner’s Edge Server is prone to failure in the event that the partner changes the IP address of their Edge Server.

        
        </div>
        
        <div>
        

        > [!NOTE]
        > For <STRONG>New SIP Federated Domains</STRONG>, you must provide the <STRONG>Domain name (or FQDN)</STRONG> for Microsoft Lync Online, Microsoft Office 365. For Microsoft Lync Server 2013, Lync Server 2010 and Office Communications Server you must also provide an <STRONG>Access Edge service (FQDN)</STRONG>

        
        </div>
    
      - <span></span>  
        For discovered partner federation, where partners can discover your Edge Server, you create an SRV record in your external DNS - \_sipfederationtls.\_tcp.contoso.com – which points to the port 5061 and the host (A) record of your Edge Server
        
        <div>
        

        > [!IMPORTANT]
        > If you are supporting Microsoft Lync Mobile clients on either Windows Phone or Apple iPhone, iPad, or other Apple devices and are using the Push Notification Service or Push Notification Service, you must plan for _sipfederationtls._tcp. &lt;SIP domain&gt; SRV records for each SIP domain that you have Lync Mobile clients. Android and Nokia Symbian Lync Mobile do not use push notification and are not subject to this requirement.

        
        </div>

  - Configure external user access policies to support federated domains

  - Open firewall ports for session initiation protocol (SIP), web conferencing and audio/visual to accommodate the federation or contacts that you are enabling. For details, see: [Determine external A/V firewall and port requirements for Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)

The following information will aid you in defining the certificate, port/protocol and DNS requirements for federation with Microsoft Lync Server 2013 and Lync Server 2010.

Planning for certificates, firewall and port/protocol requirements and DNS requirements is generally a straight forward process if you have planned or deployed your Microsoft Lync Server 2013 Edge Servers. Because federation is an additional feature that uses the existing Edge Server, the planning requirements are generally met by the Edge Server planning and deployment. You should use the following tables to determine that your requirements are met and make changes in port/protocol and DNS accordingly.

<div>


> [!IMPORTANT]
> If you have a pool of Edge Servers and are federating with Lync Server 2013 or Lync Server 2010 partners, then you can use either DNS load balancing or hardware load balancers on the internal and external facing sides of the Edge Servers. If you are federating with Office Communications Server 2007 or Office Communications Server 2007 R2, hardware load balancing will provide failover support in the event of an Edge Server. Office Communications Server 2007 and Office Communications Server 2007 R2 are not DNS load balancing aware. The partner Edge Servers will establish communication with the first Edge Server in your pool that responds. If that Edge Server fails, communication does not automatically failover.



</div>

Certificate requirements are typically met through the planning of certificates for your chosen Edge Server or pooled Edge Server plan.

<div>

## In This Section

  - [Certificate summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013](lync-server-2013-certificate-summary-sip-xmpp-federation-and-public-instant-messaging.md)

  - [Port summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013](lync-server-2013-port-summary-sip-xmpp-federation-and-public-instant-messaging.md)

  - [DNS summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013](lync-server-2013-dns-summary-sip-xmpp-federation-and-public-instant-messaging.md)

</div>

<div>

## See Also


[Configure policies to control federated user access in Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md)  


[Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md)  
[Determine external A/V firewall and port requirements for Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)  
[Determine DNS requirements for Lync Server 2013](lync-server-2013-determine-dns-requirements.md)  


[Manage Access Edge Configuration for your organization in Lync Server 2013](lync-server-2013-manage-access-edge-configuration-for-your-organization.md)  
[Manage SIP federated domains for your organization in Lync Server 2013](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)  
[Manage SIP federated providers for your organization in Lync Server 2013](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

