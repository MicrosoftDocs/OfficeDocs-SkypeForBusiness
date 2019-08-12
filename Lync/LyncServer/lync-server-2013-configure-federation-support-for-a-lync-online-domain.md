---
title: 'Lync Server 2013: Configure federation support for a Lync Online domain'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure federation support for a Lync Online domain
ms:assetid: 19d5d5be-cd7f-47b8-b6c5-651a3191def7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202166(v=OCS.15)
ms:contentKeyID: 48183530
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure federation support for a Lync Online domain in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Federating with a Microsoft Lync Online 2010 customer requires you to complete the following steps:

  - Configure support for the domain of the Lync Online 2010 customer (for example, contoso.onmicrosoft.com). As specified in the [Prerequisites for federating with a Lync Online customer in Lync Server 2013](lync-server-2013-prerequisites-for-federating-with-a-lync-online-customer.md) section of this documentation, you should have already enabled federation for your organization. Enabling federation requires specifying the method to be used to control access by federated domains. If you configured your organization to use discovery, adding the domain to your organization’s allowed list is optional. If you did not enable domain discovery, then you must add the domain name of the Lync Online customer to your allowed domains list. You can add a domain name either by using Lync Server Control Panel or by running the **New-CSAllowedDomain** cmdlet. For details about using Lync Server Control Panel, including enabling discovery of domains, see [Manage SIP federated providers for your organization in Lync Server 2013](lync-server-2013-manage-sip-federated-providers-for-your-organization.md) in the Operations documentation. For details about using the **New-CSAllowedDomain** cmdlet to add a domain, see [New-CsAllowedDomain](https://docs.microsoft.com/powershell/module/skype/New-CsAllowedDomain) in the Operations documentation.
    
    <div>
    

    > [!NOTE]  
    > A Lync Online customer can have multiple domains. If you want to federate with more than one of the domains, you must configure support for each individual domain with which you want to support federation, and the administrator of the Lync Online customer must enable federation for each of the domains to be federated.

    
    </div>

  - Configure support for the hosting provider of the Lync Online 2010 customer domain with which you want to federate. Use the procedure in this section to configure support for hosting provider.
    
    <div>
    

    > [!NOTE]  
    > This step is required only for federation with a domain of a Lync Online customer, not for federation with any domain that is deployed on-premises at a federated partner’s location.

    
    </div>

<div>

## To configure support for a hosting provider

1.  From a Front End Server, Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the **New-CsHostingProvider** cmdlet to create and configure the hosting provider. For example, run:
    
        New-CsHostingProvider -Identity LyncOnline -ProxyFqdn "sipfed.online.lync.com" -VerificationLevel UseSourceVerification -Enabled $True -EnabledSharedAddressSpace $False -HostsOCSUsers $False -IsLocal $False
    
    The preceding example sets the following parameters:
    
      - **Identity** specifies a unique string value identifier for the hosting provider that you are creating. Note that the command will fail if an existing provider has already been configured with that Identity.
    
      - **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider. This value cannot be modified. If the hosting provider changes its proxy server you will need to delete and then recreate the entry for that provider.
    
      - **VerificationLevel** specifies how (or if) messages sent from a hosting provider are verified to ensure that they were sent from that provider.
    
      - **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. Messages cannot be exchanged between the two organizations until this value is set to **True**.
    
      - **EnabledSharedAddressSpace** indicates whether the hosting provider is being used in a shared SIP address space (split domain) scenario.
    
      - **HostsOCSUsers** indicates whether the hosting provider is used to host Lync Server accounts. If **False**, the provider hosts other account types, such as Microsoft Exchange accounts.
    
      - **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Lync Server topology.
    
    For details about using this cmdlet, see [New-CsHostingProvider](https://docs.microsoft.com/powershell/module/skype/New-CsHostingProvider) in the Operations documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

