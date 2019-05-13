---
title: Verify Lync Server 2010 environment
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Verify Lync Server 2010 environment
ms:assetid: bfc7c620-556a-43cd-b1ed-2c268ec2b5cc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205231(v=OCS.15)
ms:contentKeyID: 48185301
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Verify Lync Server 2010 environment

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

Before deploying Lync Server 2013 in a coexistence state with Lync Server 2010, you need to verify that Lync Server 2010 services have been configured and started. It is important to identify key services and features that exist in your legacy environment, prior to deploying a Lync Server 2013 pilot pool. Before deploying Microsoft Lync Server 2013 XMPP in a coexistence state with a legacy XMPP deployment, you need to verify the legacy XMPP services have been configured and started, and identify which federated partner the legacy XMPP configuration is supporting. Verifying your legacy Lync Server 2010 deployment entails the following:

  - Verifying the Lync Server 2010 services are started

  - Reviewing the topology and users in Lync Server 2010.

  - Verifying the federation and Edge server settings.

  - Verifying XMPP services and federated partners.

**Verify Lync Server 2010 Services are started**

1.  From the Lync Server 2010 Front End Server, navigate to the Administrative Tools\\Services applet.

2.  Verify that the following services are running on the Front End Server:
    
    ![List of services running on Front End Server](images/JJ205231.639f2729-b759-4d8e-b4ad-59d7f68adcd2(OCS.15).jpg "List of services running on Front End Server")

**Review the Lync Server 2010 topology in Lync Server Control Panel**

1.  Log on to the Front End Server with an account that is a member of the RTCUniversalServerAdmins group or a member of the CsAdministrator or CsUserAdministrator administrative role.

2.  Open the Lync Server Control Panel.

3.  Select **Topology**. Verify that the various servers in your Lync Server 2010 deployment are listed.
    
    ![Lync Server 2010 Control Panel topology page](images/JJ205231.338ce4fb-2162-4176-a249-ec4ae021fa6a(OCS.15).jpg "Lync Server 2010 Control Panel topology page")

**To review Lync Server 2010 users in Lync Server Control Panel**

1.  Open the Lync Server Control Panel.

2.  Select **Users** and then click **Find**.

3.  Verify that the **Registrar Pool** column points to the Lync Server 2010 pool for each user listed.
    
    ![Lync Server 2010 Control Panel listing users](images/JJ205231.a9378c40-7a52-4c78-ad83-1463847c9edb(OCS.15).jpg "Lync Server 2010 Control Panel listing users")

**To verify Lync Server 2010 Edge and Federation Settings**

1.  Start Topology Builder.

2.  Select **Download Topology from existing deployment**.

3.  Choose a file name and save the topology with the default .tbxml file type.

4.  Expand the Lync Server 2010 node to reveal the various server roles in the deployment.

5.  Select the site node and verify if a **Site federation route assignment** value is set.
    
    ![Topology Builder, Site Federation Route](images/JJ205231.87de3735-af7e-4280-8d72-c42cb0ea1c05(OCS.15).jpg "Topology Builder, Site Federation Route")

6.  Next, select the Standard Edition Server or Enterprise Edition front end pool. Determine if an Edge pool has been configured for Media below **Associations**.
    
    ![Topology Builder showing servers and pools](images/JJ205231.5ad5ea3b-b122-44dd-8968-f1147d6d45f1(OCS.15).jpg "Topology Builder showing servers and pools")

7.  Finally, select the Edge pool and identify if a Next hop pool is configured below **Next hop selection**.
    
    ![Topology Builder, Next hop selection](images/JJ205231.3121e723-fba7-498e-a786-bde7be1a55e2(OCS.15).jpg "Topology Builder, Next hop selection")

**Verify legacy XMPP Federated Partner Configuration**

1.  From the legacy XMPP server, navigate to the Administrative Tools\\Services applet.

2.  Verify that the Office Communications Server XMPP Gateway service is started.
    
    ![Office Communications Server XMPP Gateway Service](images/JJ721906.23223724-3c4b-4cb9-ace2-1cab2c3c91c3(OCS.15).jpg "Office Communications Server XMPP Gateway Service")

</div>

<span> </span>

</div>

</div>

</div>

