---
title: 'Lync Server 2013: Configuring Unified Messaging on Microsoft Exchange Server to work with Lync Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring Unified Messaging on Microsoft Exchange Server to work with Lync Server 2013
ms:assetid: 058da9c4-23af-4ddb-9f63-70133a8aafc6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398106(v=OCS.15)
ms:contentKeyID: 48183289
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Unified Messaging on Microsoft Exchange Server to work with Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-11_

<div>


> [!IMPORTANT]  
> If you want to use Exchange Unified Messaging (UM) to provide call answering, Outlook Voice Access, or auto-attendant services for Enterprise Voice users, read <A href="lync-server-2013-planning-for-exchange-unified-messaging-integration.md">Planning for Exchange Unified Messaging integration in Lync Server 2013</A> in the Planning documentation, and then follow the instructions in this section.



</div>

To configure Exchange Unified Messaging (UM) to work with Enterprise Voice, you’ll need to perform the following tasks:

  - Configure certificates on the server running Exchange Unified Messaging (UM) services
    
    <div>
    

    > [!NOTE]  
    > Add all Client Access and Mailbox servers to all UM SIP URI dial plans. If not, outbound call routing won’t work as expected.

    
    </div>

  - Create one or more UM SIP URI dial plans, along with the subscriber access phone numbers, as needed, and then create corresponding Lync Server dial plans.

  - Use the **exchucutil.ps1** script to:
    
      - Create UM IP gateways.
    
      - Create UM hunt groups.
    
      - Grant Lync Server 2013 permission to read UM Active Directory Domain Services objects.

  - Create a UM auto-attendant object.

  - Create a subscriber access object.

  - Create a SIP URI for each user and associating users with a UM SIP URI dial plan.

<div>

## Requirements and Recommendations

Before you begin, the documentation in this section assumes that you have deployed the following Exchange 2013 roles: Client Access and Mailbox. In Microsoft Exchange Server 2013, Exchange UM runs as a service on these servers.

For details about deploying Exchange 2013, see the Exchange 2013 TechNet Library at [http://go.microsoft.com/fwlink/p/?LinkId=266637](http://go.microsoft.com/fwlink/p/?linkid=266637)

Also note the following:

  - If Exchange UM is installed in multiple forests, the Exchange Server integration steps must be performed for each UM forest. In addition, each UM forest must be configured to trust the forest in which Lync Server 2013 is deployed, and the forest in which Lync Server 2013 is deployed must be configured to trust each UM forest.

  - Integration steps are performed on both the Exchange Server roles where Unified Messaging services are running, and on the server running Lync Server 2013. You should perform the Exchange Server Unified Messaging integration steps before you perform the Lync Server 2013 integration steps.
    
    <div>
    

    > [!NOTE]  
    > To see which integration steps are performed on which servers and by which administrator roles, see <A href="lync-server-2013-deployment-process-for-integrating-on-premises-unified-messaging.md">Deployment process for integrating on-premises Unified Messaging and Lync Server 2013</A>.

    
    </div>

The following tools must be available on each server running Exchange UM:

  - Exchange Management Shell

  - The script **exchucutil.ps1**, which performs the following tasks:
    
      - Creates a UM IP gateway for each Lync Server 2013.
    
      - Creates a hunt group for each gateway. The pilot identifier of each hunt group specifies the UM SIP URI dial plan used by the Front End pool or Standard Edition server that is associated with the gateway.
    
      - Grants Lync Server 2013 permission to read Exchange UM objects in Active Directory Domain Services.

</div>

<div>

## In This Section

  - [Configure certificates on the server running Microsoft Exchange Server Unified Messaging](lync-server-2013-configure-certificates-on-the-server-running-microsoft-exchange-server-unified-messaging.md)

  - [Configure Unified Messaging on Microsoft Exchange for Lync Server 2013](lync-server-2013-configure-unified-messaging-on-microsoft-exchange.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

