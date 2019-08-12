---
title: 'Configure the Edge Server for integration with hosted Exchange UM'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure the Edge Server for integration with hosted Exchange UM
ms:assetid: ede3f2f9-f412-418e-a705-8d8ec98176c5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399075(v=OCS.15)
ms:contentKeyID: 48185745
ms.date: 01/24/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure the Edge Server for integration with hosted Exchange UM

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-01-23_

To provide your Lync Server 2013 users with voice mail capabilities on hosted Exchange Unified Messaging (UM), you must perform the following configuration tasks on the Edge Server:

  - Configure the Edge Server for federation.

  - Replicate Central Management store data to the Edge Server and verify the replication.

  - Create a hosting provider on the Edge Server.

For details, see the Lync Server Management Shell documentation for the following cmdlets:

  - [Set-CsAccessEdgeConfiguration](https://technet.microsoft.com/en-us/library/Gg413017(v=OCS.15))

  - [New-CsHostingProvider](https://technet.microsoft.com/en-us/library/Gg398490(v=OCS.15))

<div>


> [!IMPORTANT]
> You must create an external DNS SRV record for the hosting Exchange service before you perform these steps. For details, see <A href="lync-server-2013-create-a-dns-srv-record-for-integration-with-hosted-exchange-um.md">Create a DNS SRV record for integration with hosted Exchange UM</A>.



</div>

<div>

## To configure the Edge Server for federation

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the Set-CsAccessEdgeConfiguration cmdlet to configure the server for federation. For example, run:
    
        Set-CsAccessEdgeConfiguration -UseDnsSrvRouting -AllowFederatedUsers 1 -EnablePartnerDiscovery 0
    
    The preceding example sets the following parameters:
    
      - **UseDnsSrvRouting** specifies that Edge Servers will rely on DNS SRV records when sending and receiving federation requests.
    
      - **AllowFederatedUsers** specifies whether internal users are allowed to communicate with users from federated domains. This property also determines whether internal users can communicate with users in a split domain scenario.
    
      - **EnablePartnerDiscovery** specifies whether Lync Server will use DNS records to try to discover partner domains not listed in the Active Directory allowed domains list. If False, Lync Server 2013 will only federate with domains found on the allowed domains list. This parameter is required if you use DNS service routing. In most deployments, the value is set to false to avoid opening up federation to all partners.

</div>

<div>

## To replicate data to the Edge Server and verify the replication

  - Verify that the replication to the Edge Server is complete. For the procedure, see [Verify connectivity between internal servers and Edge Servers in Lync Server 2013](lync-server-2013-verify-connectivity-between-internal-servers-and-edge-servers.md).

</div>

<div>

## To create a hosting provider on the Edge Server

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the **New-CsHostingProvider** cmdlet to configure the hosting provider. For example, run:
    
        New-CsHostingProvider -Identity Fabrikam.com -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $False -ProxyFQDN "proxyserver.fabrikam.com" -IsLocal $False -VerificationLevel UseSourceVerification
    
    The preceding example sets the following parameters:
    
      - **Identity** specifies a unique string value identifier for the hosting provider you are creating, in this example, **Fabrikam.com**. Note that the command will fail if an existing provider has already been configured with that Identity.
    
      - **Enabled** indicates whether the network connection between your domain and the hosting provider is enabled. Messages cannot be exchanged between the two organizations until this value is set to **True**.
    
      - **EnabledSharedAddressSpace** indicates whether the hosting provider is being used in a shared SIP address space (split domain) scenario.
        
        <div>
        

        > [!NOTE]
        > Before you set <CODE>EnableSharedAddressSpace</CODE> to True, try to resolve the Federation SRV record internally. If this record cannot be resolved internally, then you need to create the records, _sipfederationtls._tcp.&lt;domain&gt; and _sip._tls.&lt;domain&gt; in the internal DNS. These records should point to the external IP address of the Access Interface of the Edge Server.

        
        </div>
    
      - **HostsOCSUsers** indicates whether the hosting provider is used to host Lync Server 2013 accounts. If **False**, the provider hosts other account types, such as Microsoft Exchange accounts.
    
      - **ProxyFQDN** specifies the fully qualified domain name (FQDN) for the proxy server used by the hosting provider, in this example, **proxyserver.fabrikam.com**. This value cannot be modified. If the hosting provider changes its proxy server you will need to delete and then recreate the entry for that provider.
    
      - **IsLocal** indicates whether the proxy server used by the hosting provider is contained within your Lync Server 2013 topology.
    
      - **VerficationLevel** indicates the allowed verification level for messages sent to and from the hosted provider. Specify **UseSourceVerification**, which relies on the verification level included in messages sent from the hosting provider. If this level is not specified, then the message will be rejected as being unverifiable.

</div>

<div>

## See Also


[Export your Lync Server 2013 topology and copy it to external media for edge installation](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md)  


[Verify connectivity between internal servers and Edge Servers in Lync Server 2013](lync-server-2013-verify-connectivity-between-internal-servers-and-edge-servers.md)  


[New-CsHostingProvider](https://technet.microsoft.com/en-us/library/Gg398490(v=OCS.15))  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

