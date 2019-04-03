---
title: 'Lync Server 2013: Components and topologies for on-premises Unified Messaging'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Components and topologies for on-premises Unified Messaging
ms:assetid: 22fc87cf-a7e5-4c8c-bb9b-101e5380cdcf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425711(v=OCS.15)
ms:contentKeyID: 48183619
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Components and topologies for on-premises Unified Messaging in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-25_

This topic describes the Microsoft Exchange Server 2013 components required to provide Exchange Unified Messaging (UM) features to Lync Server 2013 deployment. It also describes the supported topologies for on-premises Exchange UM integration.

<div>

## Exchange Server Components

To provide the Exchange UM features and services described in [Features of integrated Unified Messaging and Lync Server 2013](lync-server-2013-features-of-integrated-unified-messaging.md) to Enterprise Voice users in your organization, you must deploy an Microsoft Exchange Mailbox server and Client Access server, which hosts user mailboxes and provides a single storage location for email and voice mail. Exchange UM runs as a service on Exchange Mailbox and Client Access servers.

For details about Exchange UM components in Microsoft Exchange Server 2007 and Microsoft Exchange Server 2010, see [Deploying on-premises Exchange UM to provide Lync Server 2013 voice mail](lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md) in the Deployment documentation.

</div>

<div>

## Supported Topologies

You can deploy Lync Server 2013 and Exchange Unified Messaging (UM) in the same forest or multiple forests. If the deployment spans multiple forests, you must perform the Exchange integration steps for each Exchange UM forest. Furthermore, you must configure each Microsoft Exchange forest to trust the Lync Server 2013 forest and the Lync Server 2013 forest to trust each Exchange UM forest. In addition to this forest trust, the Exchange UM settings for all users must be set on the user objects in the Lync Server 2013 forest.

Lync Server 2013 supports the following topologies for Exchange UM integration:

  - Single forest

  - Single domain (that is, a single forest with a single domain). Lync Server 2013, Microsoft Exchange, and users all reside in the same domain.

  - Multiple domain (that is, a root domain with one or more child domains). Lync Server 2013, and Microsoft Exchange servers are deployed in different domains from the domain where you create users. Exchange UM servers can be deployed in different domains from the Lync Server 2013 pool they support.

  - Multiple forest (that is, resource forest). Lync Server 2013 is deployed in a single forest, and then users are distributed across multiple forests. The users’ Exchange UM attributes must be replicated over to the Lync Server 2013 forest.
    
    <div>
    

    > [!NOTE]  
    > Exchange can be deployed in multiple forests. Each Exchange organization can provide Exchange UM to its users, or Exchange UM can be deployed in the same forest as Lync Server 2013.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

