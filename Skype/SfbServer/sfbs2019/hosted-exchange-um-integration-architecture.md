---
title: "Hosted Exchange UM integration architecture in Lync Server 2013"
ms.author: tonysmit
author: tonysmit
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0094d5dc-1836-441c-b6e2-f88e35203a8d
description: "The Lync Server 2013 ExUM Routing application supports integration with an on-premises Exchange Unified Messaging (UM) deployment, with Exchange UM hosted by a service provider, or with a combination of the two. The following diagram shows all three possibilities."
---

# Hosted Exchange UM integration architecture in Lync Server 2013
[]
The Lync Server 2013 ExUM Routing application supports integration with an on-premises Exchange Unified Messaging (UM) deployment, with Exchange UM hosted by a service provider, or with a combination of the two. The following diagram shows all three possibilities. 
  
**Integration with an on-premises Exchange UM deployment and two hosted Exchange providers**

![On-premises Lync Server Exchange UM Deployment](media/HEXUMArch.jpg)
  
The following modes are supported:
  
- **On-premises deployment**: Lync Server 2013 and Exchange UM are both deployed on local servers within your enterprise.
    
- **Cross-premises deployment**: Lync Server 2013 is deployed on local servers within your enterprise and Exchange UM is hosted in an online service provider's facility, such as a Microsoft Exchange Online data center.
    
- **Mixed deployment**: Your Lync Server 2013 deployment has some user mailboxes homed on local Exchange servers within your enterprise and some mailboxes homed in a hosted Exchange service data center.
    
    > [!NOTE]
    > The mixed deployment can be used as a transitional solution during evaluation and phased migration of users to hosted Exchange UM, or a permanent solution if you opt to keep some users' Exchange UM services on-premises after transferring others. 
  
## Shared SIP Address Space

To integrate Lync Server 2013 with an on-premises Exchange UM deployment, you grant Lync Server 2013 permission to read Exchange UM Active Directory Domain Services objects. This approach does not work for integration with hosted Exchange UM, however, because Lync Server 2013 and Exchange UM are installed in separate forests with no trust between them.
  
To integrate Lync Server 2013 with hosted Exchange UM, you must configure a shared SIP address space. In this configuration, the same SIP domain address space is available to both Lync Server 2013 and the hosted Exchange UM service provider.
  
> [!NOTE]
> Use of the shared SIP address space is similar to the approach used in a cross-premises Lync Server 2013 environment, in which some users are homed in the on-premises deployment and some are homed in a hosted deployment (such as Skype for Business Online). The SIP domain is split between them. When you integrate Lync Server 2013 with hosted Exchange UM, ensure that you include the Exchange UM service provider in the shared SIP address space. 
  
To configure the shared SIP address space for integrating with an Exchange UM service provider, you need to configure your Edge Server as follows:
  
1. Configure the Edge Server for federation by running the **Set-CsAccessEdgeConfiguration** cmdlet to set the following parameters: 
    
  - **UseDnsSrvRouting** specifies that Edge Servers will rely on DNS SRV records when sending and receiving federation requests. 
    
  - **AllowFederatedUsers** specifies whether internal users are allowed to communicate with users from federated domains. This property also determines whether internal users can communicate with users in a split domain scenario. 
    
  - **EnablePartnerDiscovery** specifies whether Lync Server 2013 will use DNS records to try to discover partner domains that are not listed in the Active Directory allowed domains list. If False, Lync Server 2013 will federate only with domains that are found on the allowed domains list. This parameter is required if you use DNS service routing. In most deployments, the value is set to false to avoid opening up federation to all partners. 
    
2. Replicate the Central Management store to the Edge Server and verify the replication. For details, see [Export your Lync Server 2013 topology and copy it to external media for edge installation](export-your-topology-and-copy-it-to-external-media-for-edge-installation.md) in the Deployment documentation. 
    
3. Configure a hosting provider on the Edge Server by running the **New-CsHostingProvider** cmdlet to set the following parameters: 
    
  - **Identity** specifies a unique string value identifier for the hosting provider that you are creating, for example, Hosted Exchange UM.
    
  - **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. Must be set to True.
    
  - **EnabledSharedAddressSpace** indicates whether the hosting provider will be used in a shared SIP address space scenario. Must be set to True.
    
  - **HostsOCSUsers** indicates whether the hosting provider is used to host Lync Server 2013 accounts. Must be set to False.
    
  - **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider, for example, proxyserver.fabrikam.com. Contact your hosting provider for this information. This value cannot be modified. If the hosting provider changes its proxy server, you will need to delete and then recreate the entry for that provider.
    
  - **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Lync Server 2013 topology. Must be set to **False**.
    

