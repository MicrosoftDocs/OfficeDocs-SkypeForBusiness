---
title: "Guidelines for integrating on-premises Unified Messaging and Lync Server 2013"
ms.author: tonysmit
author: tonysmit
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 829ac017-6907-40f9-be22-787a28eae0ac
description: "The following are guidelines and best practices to consider when you deploy Enterprise Voice:"
---

# Guidelines for integrating on-premises Unified Messaging and Lync Server 2013
[]
The following are guidelines and best practices to consider when you deploy Enterprise Voice:
  
> [!IMPORTANT]
> Exchange Unified Messaging (UM) supports IPv6 only if you are also using UCMA 4. 
  
- Deploy a Lync Server 2013 Standard Edition server or a Front End pool. For details about installation, see [Deploying Lync Server 2013](deploying-lync-server-2013.md) in the Deployment documentation. 
    
- Work with Exchange administrators to confirm which tasks each of you will perform to assure a smooth and successful integration.
    
- Deploy the Exchange Mailbox server roles in each Exchange Unified Messaging (UM) forest where you want to enable users for Exchange UM. For details about installing Exchange server roles, see the Microsoft Exchange Server 2013 documentation.
    
    > [!IMPORTANT]
    > When Exchange Unified Messaging (UM) is installed, it is configured to use a self-signed certificate. > The self-signed certificate, however, does not enable Lync Server 2013 and Exchange UM to trust each other, which is why it is necessary to request a separate certificate from a certification authority that both servers trust. 
  
- If Lync Server 2013 and Exchange UM are installed in different forests, configure each Exchange forest to trust the Lync Server 2013 forest and the Lync Server 2013 forest to trust each Exchange forest. Also, set the users' Exchange UM settings on the user objects in the Lync Server 2013 forest, typically by using a script or a cross-forest tool, such as Identity Lifecycle Manager (ILM).
    
- If necessary, install the Exchange Management Console to manage your Unified Messaging servers.
    
- Obtain valid phone numbers for Outlook Voice Access and auto attendant.
    
- If you are using a version of Exchange UM earlier than Microsoft Exchange Server 2010 Service Pack 1 (SP1), coordinate names for Exchange UM SIP URI dial plans and Enterprise Voice dial plans. 
    
## Deploying Redundant Exchange UM Servers

> [!IMPORTANT]
> We recommend that you deploy a minimum of two servers on which Exchange UM services is running for each Exchange UM SIP URI dial plan that you configure for your organization. In addition to providing expanded capacity, deploying redundant servers provides high availability. In the event of an server failure, Lync Server 2013 can be configured to fail over to another server. 
  
The following example configurations provide Exchange UM resiliency.
  
**Example 1: Exchange UM Resiliency**

![Exchange UM Example 1](media/Redundant_ExUM_Srvrs_Opt1.jpg)
  
In Example 1, Exchange UM servers 1 and 2 are enabled in the Tukwila data center, and Exchange UM servers 3 and 4 are enabled in the Dublin data center. In the event of an Exchange UM outage in Tukwila, the Domain Name System (DNS) A records for servers 1 and 2 should be configured to point to servers 3 and 4, respectively. In the event of an Exchange UM outage in Dublin, the DNS A records for servers 3 and 4 should be configured to point to servers 1 and 2, respectively.
  
> [!NOTE]
>  For Example 1, you should also assign one of following certificate on each Exchange UM server: >  Use a certificate with a wildcard in the Subject Alternative Name (SAN). >  Put the fully qualified domain name (FQDN) of each of the four Exchange UM servers in the SAN. 
  
**Example 2: Exchange UM Resiliency**

![Exchange UM Example 2](media/Redundant_ExUM_Srvrs_Opt2.jpg)
  
In Example 2, under ordinary operating conditions Exchange UM servers 1 and 2 are enabled in the Tukwila data center, and Exchange UM servers 3 and 4 are enabled in the Dublin data center. All four servers are included in the Tukwila users' SIP URI dial plan; however, servers 3 and 4 are disabled. In the event of an Exchange UM outage in Tukwila, for example, Exchange UM servers 1 and 2 should be disabled and Exchange UM servers 3 and 4 should be enabled so the Tukwila Exchange UM traffic will be routed to the servers in Dublin.
  
For details about how to enable or disable Unified Messaging on Exchange 2013, see "Integrate Exchange 2013 UM with Lync Server" at [https://go.microsoft.com/fwlink/p/?LinkId=265372](https://go.microsoft.com/fwlink/p/?LinkId=265372).
  
For details about how to enable or disable Unified Messaging on Microsoft Exchange Server 2010, see:
  
- "Enable Unified Messaging on Exchange 2010" at [https://go.microsoft.com/fwlink/p/?LinkId=204418](https://go.microsoft.com/fwlink/p/?LinkId=204418).
    
- "Disable Unified Messaging on Exchange 2010" at [https://go.microsoft.com/fwlink/p/?LinkId=204416](https://go.microsoft.com/fwlink/p/?LinkId=204416).
    
## See also

#### 

[Deployment process for integrating on-premises Unified Messaging and Lync Server 2013](deployment-process-for-integrating-on-premises-unified-messaging-and-lync-server.md)

