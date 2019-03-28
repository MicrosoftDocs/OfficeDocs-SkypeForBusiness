---
title: 'Lync Server 2013: Guidelines for integrating on-premises Unified Messaging'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Guidelines for integrating on-premises Unified Messaging and Lync Server
ms:assetid: 829ac017-6907-40f9-be22-787a28eae0ac
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398656(v=OCS.15)
ms:contentKeyID: 48184681
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Guidelines for integrating on-premises Unified Messaging and Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-25_

The following are guidelines and best practices to consider when you deploy Enterprise Voice:

<div>


> [!IMPORTANT]  
> Exchange Unified Messaging (UM) supports IPv6 only if you are also using UCMA 4.



</div>

  - Deploy a Lync Server 2013 Standard Edition server or a Front End pool. For details about installation, see [Deploying Lync Server 2013](lync-server-2013-deploying-lync-server.md) in the Deployment documentation.

  - Work with Exchange administrators to confirm which tasks each of you will perform to assure a smooth and successful integration.

  - Deploy the Exchange Mailbox server roles in each Exchange Unified Messaging (UM) forest where you want to enable users for Exchange UM. For details about installing Exchange server roles, see the Microsoft Exchange Server 2013 documentation.
    
    <div>
    

    > [!IMPORTANT]  
    > When Exchange Unified Messaging (UM) is installed, it is configured to use a self-signed certificate.<BR>The self-signed certificate, however, does not enable Lync Server 2013 and Exchange UM to trust each other, which is why it is necessary to request a separate certificate from a certification authority that both servers trust.

    
    </div>

  - If Lync Server 2013 and Exchange UM are installed in different forests, configure each Exchange forest to trust the Lync Server 2013 forest and the Lync Server 2013 forest to trust each Exchange forest. Also, set the users’ Exchange UM settings on the user objects in the Lync Server 2013 forest, typically by using a script or a cross-forest tool, such as Identity Lifecycle Manager (ILM).

  - If necessary, install the Exchange Management Console to manage your Unified Messaging servers.

  - Obtain valid phone numbers for Outlook Voice Access and auto attendant.

  - If you are using a version of Exchange UM earlier than Microsoft Exchange Server 2010 Service Pack 1 (SP1), coordinate names for Exchange UM SIP URI dial plans and Enterprise Voice dial plans.

<div>

## Deploying Redundant Exchange UM Servers

<div>


> [!IMPORTANT]  
> We recommend that you deploy a minimum of two servers on which Exchange UM services is running for each Exchange UM SIP URI dial plan that you configure for your organization. In addition to providing expanded capacity, deploying redundant servers provides high availability. In the event of an server failure, Lync Server 2013 can be configured to fail over to another server.



</div>

The following example configurations provide Exchange UM resiliency.

**Example 1: Exchange UM Resiliency**

![Exchange UM Example 1](images/Gg398656.3644b847-0847-4550-a989-e3fc51de5c4b(OCS.15).jpg "Exchange UM Example 1")

In Example 1, Exchange UM servers 1 and 2 are enabled in the Tukwila data center, and Exchange UM servers 3 and 4 are enabled in the Dublin data center. In the event of an Exchange UM outage in Tukwila, the Domain Name System (DNS) A records for servers 1 and 2 should be configured to point to servers 3 and 4, respectively. In the event of an Exchange UM outage in Dublin, the DNS A records for servers 3 and 4 should be configured to point to servers 1 and 2, respectively.

<div>


> [!NOTE]  
> For Example 1, you should also assign one of following certificate on each Exchange UM server: 
> <UL>
> <LI>
> <P>Use a certificate with a wildcard in the Subject Alternative Name (SAN).</P>
> <LI>
> <P>Put the fully qualified domain name (FQDN) of each of the four Exchange UM servers in the SAN.</P></LI></UL>



</div>

**Example 2: Exchange UM Resiliency**

![Exchange UM Example 2](images/Gg398656.15754273-306e-448d-b258-84bc2936a2e8(OCS.15).jpg "Exchange UM Example 2")

In Example 2, under ordinary operating conditions Exchange UM servers 1 and 2 are enabled in the Tukwila data center, and Exchange UM servers 3 and 4 are enabled in the Dublin data center. All four servers are included in the Tukwila users' SIP URI dial plan; however, servers 3 and 4 are disabled. In the event of an Exchange UM outage in Tukwila, for example, Exchange UM servers 1 and 2 should be disabled and Exchange UM servers 3 and 4 should be enabled so the Tukwila Exchange UM traffic will be routed to the servers in Dublin.

For details about how to enable or disable Unified Messaging on Exchange 2013, see “Integrate Exchange 2013 UM with Lync Server” at [http://go.microsoft.com/fwlink/p/?LinkId=265372](http://go.microsoft.com/fwlink/p/?linkid=265372).

For details about how to enable or disable Unified Messaging on Microsoft Exchange Server 2010, see:

  - "Enable Unified Messaging on Exchange 2010" at [http://go.microsoft.com/fwlink/p/?LinkId=204418](http://go.microsoft.com/fwlink/p/?linkid=204418).

  - "Disable Unified Messaging on Exchange 2010" at [http://go.microsoft.com/fwlink/p/?LinkId=204416](http://go.microsoft.com/fwlink/p/?linkid=204416).

</div>

<div>

## See Also


[Deployment process for integrating on-premises Unified Messaging and Lync Server 2013](lync-server-2013-deployment-process-for-integrating-on-premises-unified-messaging.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

