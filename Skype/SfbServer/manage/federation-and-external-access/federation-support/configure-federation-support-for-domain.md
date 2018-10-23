---
title: 'Configure federation support for a Skype for Business Online domain'
ms:assetid: 19d5d5be-cd7f-47b8-b6c5-651a3191def7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202166(v=OCS.15)
ms:contentKeyID: 48183530
mtps_version: v=OCS.15
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Learn how to configure federation support for a Skype for Business Online domain."
---


# Configure federation support for a Skype for Business Online domain in Skype for Business Server

Federating with a Skype for Business Online customer requires you to complete the following steps:

  - Configure support for the domain of the Skype for Business Online 2010 customer (for example, contoso.onmicrosoft.com). As specified in [Prerequisites for federating with a Skype for Business Online customer](prerequisites-for-federating.md), you should have already enabled federation for your organization. Enabling federation requires specifying the method to be used to control access by federated domains. If you configured your organization to use discovery, adding the domain to your organization’s allowed list is optional. If you did not enable domain discovery, then you must add the domain name of the Skype for Business Online customer to your allowed domains list. You can add a domain name either by using Skype for Business Server Control Panel or by running the **New-CSAllowedDomain** cmdlet. For details about using Skype for Business Server Control Panel, including enabling discovery of domains, see [Manage SIP federated providers for your organization in Skype for Business Server](../sip-providers/manage-sip-federated-providers-for-your-organization.md). For details about using the **New-CSAllowedDomain** cmdlet to add a domain, see [New-CsAllowedDomain](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsAllowedDomain).

    > [!NOTE]  
    > A Skype for Business Online customer can have multiple domains. If you want to federate with more than one of the domains, you must configure support for each individual domain with which you want to support federation, and the administrator of the Skype for Business Online customer must enable federation for each of the domains to be federated.


  - Configure support for the hosting provider of the Skype for Business Online customer domain with which you want to federate. Use the procedure in this section to configure support for hosting provider.


    > [!NOTE]  
    > This step is required only for federation with a domain of a Skype for Business Online customer, not for federation with any domain that is deployed on-premises at a federated partner’s location.


## To configure support for a hosting provider

1.  From a Front End Server, Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Management Shell**.

2.  Run the **New-CsHostingProvider** cmdlet to create and configure the hosting provider. For example, run:
    
        New-CsHostingProvider -Identity LyncOnline -ProxyFqdn "sipfed.online.lync.com" -VerificationLevel UseSourceVerification -Enabled $True -EnabledSharedAddressSpace $False -HostsOCSUsers $False -IsLocal $False
    
    The preceding example sets the following parameters:
    
      - **Identity** specifies a unique string value identifier for the hosting provider that you are creating. Note that the command will fail if an existing provider has already been configured with that Identity.
    
      - **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider. This value cannot be modified. If the hosting provider changes its proxy server you will need to delete and then recreate the entry for that provider.
    
      - **VerificationLevel** specifies how (or if) messages sent from a hosting provider are verified to ensure that they were sent from that provider.
    
      - **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. Messages cannot be exchanged between the two organizations until this value is set to **True**.
    
      - **EnabledSharedAddressSpace** indicates whether the hosting provider is being used in a shared SIP address space (split domain) scenario.
    
      - **HostsOCSUsers** indicates whether the hosting provider is used to host Skype for Business Server accounts. If **False**, the provider hosts other account types, such as Microsoft Exchange accounts.
    
      - **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Skype for Business Server topology.
    
    For details about using this cmdlet, see [New-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostingProvider).

