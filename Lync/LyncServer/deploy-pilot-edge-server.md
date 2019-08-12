---
title: Deploy pilot Edge Server
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Deploy pilot Edge Server
ms:assetid: dab345c0-8577-4c11-ac73-fe8b2a75f4cf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205306(v=OCS.15)
ms:contentKeyID: 48185559
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploy pilot Edge Server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

This topic highlights configuration settings you should be aware of prior to deploying your Lync Server 2013 Edge Server. The deployment and configuration processes for Lync Server 2013 are very similar to Lync Server 2010. This section only highlights key points you should consider as part of your pilot pool deployment. For detailed steps, see [Deploying external user access in Lync Server 2013](lync-server-2013-deploying-external-user-access.md) in the Deployment documentation, which describes the deployment process and also gives configuration information for external user access.

As you navigate through the **Define New Edge Pool** wizard, review the key configuration settings shown in the following steps. Note that only a few pages of the **Define New Edge Pool** wizard are shown.

**Define an Edge Pool**

1.  Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.

2.  Navigate to the Lync Server 2013 node. Right-click **Edge pools**, and click **New Edge pool**.
    
    ![Define the New Edge Pool dialog box](images/JJ205306.a90d388c-49ff-4620-a19d-42e2f1bb559c(OCS.15).jpg "Define the New Edge Pool dialog box")

3.  An Edge pool can be a **Multiple computer pool** or **Single computer pool**.
    
    ![Define the Edge Pool FQDN dialog box](images/JJ205306.4904fe8f-537c-4e66-a399-1bd8a316dc10(OCS.15).jpg "Define the Edge Pool FQDN dialog box")

4.  On the **Select features** page, do not enable federation or XMPP federation. Federation and XMPP federation are both currently routed through the legacy Lync Server 2010 Edge Server. These features will be configured in a later phase of migration.
    
    ![Select Features dialog box](images/JJ205306.cb0b45a4-2856-45ba-bd97-e49fafbb077e(OCS.15).jpg "Select Features dialog box")

5.  Next, continue completing the following wizard pages: **External FQDNs**, **Define the internal IP address**, and **Define the external IP address**.

6.  On the **Define the next hop** page, select the Director for the next hop of the Lync Server 2010 Edge pool.
    
    ![Define the Next Hop dialog box](images/JJ205306.11baf3ea-74f5-4eb7-8650-b03b3b190416(OCS.15).jpg "Define the Next Hop dialog box")

7.  On the **Associate Front End or Mediation pools** page, do not associate a pool with this Edge pool at this time. External media traffic is currently routed through the legacy Lync Server 2010 Edge Server. This setting will be configured in a later phase of migration.
    
    ![Associate Front End Pools dialog box](images/JJ205306.fe0da887-7b51-4564-afc5-d57da95a2eb6(OCS.15).jpg "Associate Front End Pools dialog box")

8.  Click **Finish** and then **Publish** the topology.

9.  Follow the steps in [Install Edge Servers for Lync Server 2013](lync-server-2013-install-edge-servers.md) in the Deployment documentation to install the files on the new Edge Server, configure certificates, and start the services.

It’s very important that you follow the guidelines in the topics [Deploying external user access in Lync Server 2013](lync-server-2013-deploying-external-user-access.md) in the Deployment documentation. This section merely provided some guidance on configuration settings when installing these server roles.

You should now have a legacy Lync Server 2010 Edge Server deployed in parallel with a Lync Server 2013 Edge server deployment. Verify that both deployments are running properly, services are started, and you can administer each deployment prior to moving to the next phase.

</div>

<span> </span>

</div>

</div>

</div>

