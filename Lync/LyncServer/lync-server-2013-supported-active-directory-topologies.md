---
title: 'Lync Server 2013: Supported Active Directory topologies'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Supported Active Directory topologies
ms:assetid: 0c76b778-7652-4eb0-b161-86f2d4a94ccf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398173(v=OCS.15)
ms:contentKeyID: 48183391
ms.date: 10/02/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Supported Active Directory topologies in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-10-02_

Lync Server 2013 supports the same Active Directory Domain Services topologies as Microsoft Lync Server 2010 and Microsoft Office Communications Server 2007 R2. The following topologies are supported:

  - Single forest with single domain

  - Single forest with a single tree and multiple domains

  - Single forest with multiple trees and disjoint namespaces

  - Multiple forests in a central forest topology

  - Multiple forests in a resource forest topology

  - Multiple forests in a Lync resource forest topology with Exchange Online

The following figure identifies the icons used in the illustrations in this section.

**Key to topology illustrations**

![Key to topology illustrations](images/Gg398173.0c3cc89f-6c43-4bc8-b2ec-61d89e391ee9(OCS.15).jpg "Key to topology illustrations")

<div>

## Single Forest, Single Domain

The simplest Active Directory topology supported by Lync Server, a single domain forest, is a common topology.

The following figure illustrates a Lync Server deployment in a single domain Active Directory topology.

**Single domain topology**

![Single domain topology](images/Gg398173.258b3b3f-0558-4a36-a4c2-031be7299668(OCS.15).jpg "Single domain topology")

</div>

<div>

## Single Forest, Multiple Domains

Another Active Directory topology supported by Lync Server is a single forest that consists of a root domain and one or more child domains. In this type of Active Directory topology, the domain where you create users can be different from the domain where you deploy Lync Server. However, if you deploy a Front End pool, you must deploy all the Front End Servers in the pool within a single domain. Lync Server support for Windows universal administrator groups enables cross-domain administration.

The following figure illustrates a deployment in a single forest with multiple domains. In this figure, a user icon shows the domain where the user account is homed, and the arrow points to the domain where the Lync Server pool resides. User accounts include the following:

  - User accounts within the same domain as the Lync Server pool

  - User accounts in a different domain from the Lync Server pool

  - User accounts in a child domain of the domain with the Lync Server pool

**Single forest with multiple domains**

![Single forest with multiple domains](images/Gg398173.2b809c72-c3cd-4fad-afe6-8c2dae779750(OCS.15).jpg "Single forest with multiple domains")

</div>

<div>

## Single Forest, Multiple Trees

A multiple-tree forest topology consists of two or more domains that define independent tree structures and separate Active Directory namespaces.

The following figure illustrates a single forest with multiple trees. In this figure, a user icon shows the domain where the user account is homed, a solid line points to a Lync Server pool that resides in the same or a different domain, and a dashed line points to Lync Server pool that resides in a different tree. User accounts include the following:

  - User accounts within the same domain as the Lync Server pool

  - User accounts in a different domain from (but the same tree as) the Lync Server pool

  - User accounts in a different tree from the Lync Server pool

**Single forest with multiple trees**

![Single forest with multiple trees](images/Gg398173.db30fa49-174a-4974-8695-41dd78e39432(OCS.15).jpg "Single forest with multiple trees")

</div>

<div>

## Multiple Forests, Central Forest

Lync Server supports multiple forests that are configured in a central forest topology. Central forest topologies use contact objects in the central forest to represent users in the other forests. The central forest also hosts user accounts for any users in this forest. A directory synchronization product, such as Microsoft Identity Integration Server (MIIS), Microsoft Forefront Identity Manager (FIM) 2010, or Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1), manages the life cycle of user accounts within the organization: When a new user account is created in one of the forests or a user account is deleted from a forest, the directory synchronization product synchronizes the corresponding contact in the central forest.

A central forest has the following advantages:

  - Servers running Lync Server are centralized within a single forest.

  - Users can search for and communicate with other users in any forest.

  - Users can view presence of other users in any forest.

  - The directory synchronization product automates the addition and deletion of contact objects in the central forest as user accounts are created or removed.

The following figure illustrates a central forest topology. In this figure, there are two-way trust relationships between the domain that hosts Lync Server, which is in the central forest, and each user-only domain, which is in a separate forest. The schema in the separate user forests does not need to be extended.

**Central forest topology**

![Central forest topology](images/Gg398173.7feb049a-453b-4134-9128-873b83ee1755(OCS.15).jpg "Central forest topology")

</div>

<div>

## Multiple Forests, Resource Forest

In a resource forest topology, one forest is dedicated to running server applications, such as Microsoft Exchange Server and Lync Server. The resource forest hosts the server applications and a synchronized representation of the active user object, but it does not contain logon-enabled user accounts. The resource forest acts as a shared services environment for the other forests where user objects reside. The user forests have a forest-level trust relationship with the resource forest. When you deploy Lync Server in this type of topology, you create one disabled user object in the resource forest for every user account in the user forests. If Microsoft Exchange is already deployed in the resource forest, the disabled user accounts might already exist. A directory synchronization product, such as MIIS, Microsoft Forefront Identity Manager (FIM) 2010, or Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1), manages the life cycle of user accounts. When a new user account is created in one of the user forests or a user account is deleted from a forest, the directory synchronization product synchronizes the corresponding user representation in the resource forest.

This topology can be used to provide a shared infrastructure for services in organizations that manage multiple forests or to separate the administration of Active Directory objects from other administration. Companies that need to isolate Active Directory administration for security reasons often choose this topology.

This topology provides the benefit of limiting the need to extend the Active Directory schema to a single forest (that is, the resource forest).

The following diagram illustrates a resource forest topology.

**Resource forest topology**

![Active Directory Resource Forest Topology](images/Gg398173.54ab82f1-e9e5-40f0-a54e-86e340b65c2a(OCS.15).jpg "Active Directory Resource Forest Topology")

</div>

<div>

## Multiple forests in a Lync resource forest topology with Exchange Online

In this topology, one or more forests are located on-premises and are dedicated to hosting Active Directory user accounts. The resource forest is located off-premises and is maintained by a third-party hosting provider. The resource forest contains only the Lync Server deployment and a synchronized replication of the user accounts from the on-premises user accounts forest(s). It does not contain logon-enabled user accounts. Exchange is deployed either in the on-premises user account forest(s) integrated along with Exchange Online (Hybrid), or email services for the on-premises user accounts are provided exclusively by Exchange Online.

The resource forest acts as a shared services environment for the on-premises Active Directory forest(s) where user objects reside. The user account forest(s) have a one way forest-level trust relationship with the resource forest. When you deploy Lync Server in this type of topology, you create one disabled user object in the resource forest for every user account in the user forests. A directory synchronization product, such as MIIS, Microsoft Forefront Identity Manager (FIM) 2010, or Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1), manages the life cycle of user accounts. When a new user account is created in one of the user forests or a user account is deleted from a forest, the directory synchronization product synchronizes the corresponding user representation in the resource forest. For more information about configuring a multi-forest deployment, see [Deploying Lync in a Multi-Forest Architecture (Partner Hosted Lync with Exchange Hybrid)](http://go.microsoft.com/fwlink/p/?linkid=513216).

</div>

</div>

<span> </span>

</div>

</div>

</div>

