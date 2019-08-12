---
title: 'Lync Server 2013: Hosted Exchange UM integration architecture'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Hosted Exchange UM integration architecture
ms:assetid: 0094d5dc-1836-441c-b6e2-f88e35203a8d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398067(v=OCS.15)
ms:contentKeyID: 48183222
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Hosted Exchange UM integration architecture in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-25_

The Lync Server 2013 ExUM Routing application supports integration with an on-premises Exchange Unified Messaging (UM) deployment, with Exchange UM hosted by a service provider, or with a combination of the two. The following diagram shows all three possibilities.

**Integration with an on-premises Exchange UM deployment and two hosted Exchange providers**

![On-premises Lync Server Exchange UM Deployment](images/Gg398821.d6498eb9-87ee-40f3-8ecd-852f91546590(OCS.15).jpg "On-premises Lync Server Exchange UM Deployment")

The following modes are supported:

  - **On-premises deployment:** Lync Server 2013 and Exchange UM are both deployed on local servers within your enterprise.

  - **Cross-premises deployment:** Lync Server 2013 is deployed on local servers within your enterprise and Exchange UM is hosted in an online service provider’s facility, such as a Microsoft Exchange Online data center.

  - **Mixed deployment:** Your Lync Server 2013 deployment has some user mailboxes homed on local Exchange servers within your enterprise and some mailboxes homed in a hosted Exchange service data center.
    
    <div>
    

    > [!NOTE]  
    > The mixed deployment can be used as a transitional solution during evaluation and phased migration of users to hosted Exchange UM, or a permanent solution if you opt to keep some users’ Exchange UM services on-premises after transferring others.

    
    </div>

<div>

## Shared SIP Address Space

To integrate Lync Server 2013 with an on-premises Exchange UM deployment, you grant Lync Server 2013 permission to read Exchange UM Active Directory Domain Services objects. This approach does not work for integration with hosted Exchange UM, however, because Lync Server 2013 and Exchange UM are installed in separate forests with no trust between them.

To integrate Lync Server 2013 with hosted Exchange UM, you must configure a *shared SIP address space*. In this configuration, the same SIP domain address space is available to both Lync Server 2013 and the hosted Exchange UM service provider.

<div>


> [!NOTE]  
> Use of the shared SIP address space is similar to the approach used in a cross-premises Lync Server 2013 environment, in which some users are homed in the on-premises deployment and some are homed in a hosted deployment (such as Lync Online). The SIP domain is split between them. When you integrate Lync Server 2013 with hosted Exchange UM, ensure that you include the Exchange UM service provider in the shared SIP address space.



</div>

To configure the shared SIP address space for integrating with an Exchange UM service provider, you need to configure your Edge Server as follows:

1.  Configure the Edge Server for federation by running the **Set-CsAccessEdgeConfiguration** cmdlet to set the following parameters:
    
      - **UseDnsSrvRouting** specifies that Edge Servers will rely on DNS SRV records when sending and receiving federation requests.
    
      - **AllowFederatedUsers** specifies whether internal users are allowed to communicate with users from federated domains. This property also determines whether internal users can communicate with users in a split domain scenario.
    
      - **EnablePartnerDiscovery** specifies whether Lync Server 2013 will use DNS records to try to discover partner domains that are not listed in the Active Directory allowed domains list. If False, Lync Server 2013 will federate only with domains that are found on the allowed domains list. This parameter is required if you use DNS service routing. In most deployments, the value is set to false to avoid opening up federation to all partners.

2.  Replicate the Central Management store to the Edge Server and verify the replication. For details, see [Export your Lync Server 2013 topology and copy it to external media for edge installation](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md) in the Deployment documentation.

3.  Configure a *hosting provider* on the Edge Server by running the **New-CsHostingProvider** cmdlet to set the following parameters:
    
      - **Identity** specifies a unique string value identifier for the hosting provider that you are creating, for example, **Hosted Exchange UM**.
    
      - **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. Must be set to **True**.
    
      - **EnabledSharedAddressSpace** indicates whether the hosting provider will be used in a shared SIP address space scenario. Must be set to **True**.
    
      - **HostsOCSUsers** indicates whether the hosting provider is used to host Lync Server 2013 accounts. Must be set to **False**.
    
      - **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider, for example, **proxyserver.fabrikam.com**. Contact your hosting provider for this information. This value cannot be modified. If the hosting provider changes its proxy server, you will need to delete and then recreate the entry for that provider.
    
      - **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Lync Server 2013 topology. Must be set to **False**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

