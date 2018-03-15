---
title: "Planning for SIP, XMPP federation, and public instant messaging in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3b234d92-b9ff-4b1d-910e-084c6f17e751
description: "In this articleLync Server and Office Communications Server FederationPublic Instant Messaging ConnectivityExtensible Messaging and Presence Protocol (XMPP) Federation"
---

# Planning for SIP, XMPP federation, and public instant messaging in Lync Server 2013
[]
 **In this article**
  
[Lync Server and Office Communications Server Federation](#sectionSection0)
  
[Public Instant Messaging Connectivity](#sectionSection1)
  
[Extensible Messaging and Presence Protocol (XMPP) Federation](#sectionSection2)
  
Edge Servers can be configured to allow your internal and external users access to contacts at partner organizations or services. Federations, as these partner agreements are known, can provide any or all of the following to the contacts in your organization on the partner federation or contacts in the partner federation to yours:
  
- Instant messaging and presence
    
- Collaboration and conferencing, for example - Web conferencing
    
- Audio conferencing, video conferencing, or both
    
In some cases the communication, for example instant messaging (IM) and presence between a Microsoft Lync Server 2013 and an extensible messaging and presence protocol (XMPP) contact, is peer-to-peer only - supporting only you and the contact at the federated partner. In other cases, such as a Lync Server, Lync Server 2010 to Lync Server 2013 federation, multiple participants can be invited to join into the conversation.
  
## Lync Server and Office Communications Server Federation
<a name="sectionSection0"> </a>

Federation between Microsoft Lync Server 2013, Lync Server 2010 and Office Communications Server supports peer-to-peer and multi-party communications. Peer-to-peer conversations can be escalated to multi-party conversations, allowing for ad hoc meetings. Meetings - Web conferencing or audio/visual conferences - can be scheduled to include contacts inside your organization as well as contacts in partners that you federate with.
  
Federation first appeared in Microsoft Office Live Communications Server 2005 and supported one kind of federation, Direct Federation. Direct Federation required you to know the federation partner's session initiation protocol (SIP) domain and the fully qualified domain name (FQDN) of the partner's Edge Server. Live Communications Server 2005 with SP1 introduced additional federation types, all of which required domain name system (DNS) SRV records to be published by the federated partner to locate their Edge Server. The terminology for that release was:
  
- Open Enhanced Federation: Accept any SIP domain name and use DNS SRV to locate the partner Edge Server
    
- Enhanced Federation: Configure the partner's SIP domain name as a federation partner for your organization and use DNS SRV to find the partner Edge Server
    
- Direct Federation: Configure the partner's SIP domain name and the FQDN to the partner's Edge Server
    
- Server Allow List: Accept any domain, use DNS SRV to find the Edge Server of a hosting provider or a public instant messaging (IM) connectivity provider
    
Microsoft Office Communications Server 2007 introduced updated naming for federation types to better define what each federation type actually accomplished:
  
- Open Enhanced Federation became known as Discovered Partner Domain
    
- Enhanced Federation became known as Allowed Partner Domain
    
- Direct Federation became known as Allowed Partner Server
    
- Server Allow List became known as Hosting Provider and Public IM Provider
    
Microsoft Lync Server 2010 introduced a narrower definition of Hosting Provider in accordance with Microsoft Lync Online 2010 and Microsoft Office 365 and also made it subject to the same allowed list defined by the Allowed Partner Domain federation type.
  
Enabling federation between Microsoft Lync Server 2013, Lync Server 2010 and Office Communications Server uses the Edge Servers and reverse proxies to enforce the rules and allowed partner domains that you define. From a planning perspective, federating with other Lync Server, Office Communications Server requires the following:
  
- Enable federation in Topology Builder. For details, see the Deployment topic [Configuring SIP federation, XMPP federation and public instant messaging in Lync Server 2013](configuring-sip-federation-xmpp-federation-and-public-instant-messaging.md).
    
- Determine your requirements for federated domain discovery:
    
> For manual configuration of federation, you must have the fully qualified domain name (FQDN) of the partner's Edge Server and domain name, or online domain name, which is entered in the Lync Server Control Panel, **Federation and External Access**, **SIP Federated Domains**. Create a **New** policy or **Edit** an existing policy to either allow or block domains by FQDN. 
    
    > [!CAUTION]
    > Manual configuration of a federation partner's Edge Server is prone to failure in the event that the partner changes the IP address of their Edge Server. 
  
    > [!NOTE]
    > For **New SIP Federated Domains**, you must provide the **Domain name (or FQDN)** for Skype for Business Online, Microsoft Office 365. For Microsoft Lync Server 2013, Lync Server 2010 and Office Communications Server you must also provide an **Access Edge service (FQDN)**
  
> For discovered partner federation, where partners can discover your Edge Server, you create an SRV record in your external DNS - _sipfederationtls._tcp.contoso.com - which points to the port 5061 and the host (A) record of your Edge Server
    
    > [!IMPORTANT]
    > If you are supporting Microsoft Lync Mobile clients on either Windows Phone or Apple iPhone, iPad, or other Apple devices and are using the Push Notification Service or Push Notification Service, you must plan for _sipfederationtls._tcp.  _\<SIP domain\>_ SRV records for each SIP domain that you have Lync Mobile clients. Android and Nokia Symbian Lync Mobile do not use push notification and are not subject to this requirement. 
  
- Configure external user access policies to support federated domains
    
- Open firewall ports for session initiation protocol (SIP), web conferencing and audio/visual to accommodate the federation or contacts that you are enabling. For details, see: [Determine external A/V firewall and port requirements for Lync Server 2013](determine-external-a-v-firewall-and-port-requirements.md)
    
The following information will aid you in defining the certificate, port/protocol and DNS requirements for federation with Microsoft Lync Server 2013 and Lync Server 2010.
  
Planning for certificates, firewall and port/protocol requirements and DNS requirements is generally a straight forward process if you have planned or deployed your Microsoft Lync Server 2013 Edge Servers. Because federation is an additional feature that uses the existing Edge Server, the planning requirements are generally met by the Edge Server planning and deployment. You should use the following tables to determine that your requirements are met and make changes in port/protocol and DNS accordingly.
  
> [!IMPORTANT]
> If you have a pool of Edge Servers and are federating with Lync Server 2013 or Lync Server 2010 partners, then you can use either DNS load balancing or hardware load balancers on the internal and external facing sides of the Edge Servers. If you are federating with Office Communications Server 2007 or Office Communications Server 2007 R2, hardware load balancing will provide failover support in the event of an Edge Server. Office Communications Server 2007 and Office Communications Server 2007 R2 are not DNS load balancing aware. The partner Edge Servers will establish communication with the first Edge Server in your pool that responds. If that Edge Server fails, communication does not automatically failover. 
  
Certificate requirements are typically met through the planning of certificates for your chosen Edge Server or pooled Edge Server plan.
  
## Public Instant Messaging Connectivity
<a name="sectionSection1"> </a>

Public Instant Messaging Connectivity is a class of federation, and is configured to allow your internal and external Lync Server 2013 users to add contacts from any of the following:
  
- Messenger contacts 
    
- Yahoo! contacts
    
- America Online (AOL) contacts
    
> [!IMPORTANT]
>  As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License (PIC USL) is no longer available for the purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shutdown date (exact date is still to be decided, but no sooner than June 2013). >  The PIC USL is a per-user, per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft's ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which will not be renewed. >  More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people through IM and voice. 
  
This class of federation requires the following planning considerations:
  
- Windows Live Messenger users can have peer-to-peer audio/visual communication with Lync Server 2013 users, in addition to instant messaging. Your Edge Servers must meet specific port and protocol requirements. For details, see [Determine external A/V firewall and port requirements for Lync Server 2013](determine-external-a-v-firewall-and-port-requirements.md).
    
- Yahoo instant messaging has no unique requirements, other than those typically used in the planning and deployment of the typical Edge Server that is providing federation.
    
- America Online requires that your Edge Server certificate assigned to the Access Edge service has a client enhanced key usage (EKU).
    
## Extensible Messaging and Presence Protocol (XMPP) Federation
<a name="sectionSection2"> </a>

Previous versions of Lync Server and Office Communications Server provided an extensible messaging and presence protocol (XMPP) gateway that could be deployed as a separate server role to allow federating with XMPP deployments. In Microsoft Lync Server 2013, the XMPP functionality can be deployed as a feature. XMPP functionality is installed in two parts: an XMPP proxy that runs on the Edge Server and the XMPP gateway that runs on the Front End Servers.
  
Deployment and configuration of XMPP is covered in [Deploying external user access in Lync Server 2013](deploying-external-user-access.md) You plan for supporting XMPP in your organization by defining port and protocol rules on your firewall, configuration of certificates, and adding DNS records. The following topics in this section summarize the information that you will need to successfully plan XMPP federation for your deployment. 
  
> [!IMPORTANT]
> The XMPP capability of Lync Server 2013 is tested and supported by Microsoft for instant messaging federation with Google Talk. For any other XMPP systems contact the third-party vendor to verify that they support federation with Lync Server 2013, and for any deployment or troubleshooting recommendations. 
  
> [!IMPORTANT]
> XMPP federation is not supported for users who are homed on survivable branch appliances. This applies to both seeing presence information and exchanging IM messages. 
  
In the following topics contain guidance for defining certificates, firewall ports and DNS entries for the types of supported federation scenarios.
  
> [Certificate summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013](certificate-summarysip-xmpp-federation-and-public-instant-messaging.md)
    
> [Port summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013](port-summarysip-xmpp-federation-and-public-instant-messaging.md)
    
> [DNS summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013](dns-summarysip-xmpp-federation-and-public-instant-messaging.md)
    
## See also
<a name="sectionSection2"> </a>

#### 

[Configure policies to control federated user access in Lync Server 2013](configure-policies-to-control-federated-user-access.md)
#### 

[Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md)
  
[Determine external A/V firewall and port requirements for Lync Server 2013](determine-external-a-v-firewall-and-port-requirements.md)
  
[Determine DNS requirements for Lync Server 2013](determine-dns-requirements.md)
#### 

[Manage Access Edge Configuration for your organization in Lync Server 2013](manage-access-edge-configuration-for-your-organization.md)
  
[Manage SIP federated domains for your organization in Lync Server 2013](manage-sip-federated-domains-for-your-organization.md)
  
[Manage SIP federated providers for your organization in Lync Server 2013](manage-sip-federated-providers-for-your-organization.md)

