---
title: 'Configuring Lync Server 2013 to work with Office Web Apps Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring Lync Server 2013 to work with Office Web Apps Server
ms:assetid: 6231e519-9010-4ff9-b5a6-b5859c2b3e11
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204944(v=OCS.15)
ms:contentKeyID: 48184288
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Lync Server 2013 to work with Office Web Apps Server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-04-22_

Before you can configure Lync Server 2013 to use Office Web Apps Server, Office Web Apps Server must be deployed and configured. See the document **Guide to Deploying Office Web Apps Server and Office Web Apps** for detail information on how to install and configure a single Office Web Apps Server, or for information on how to install and configure an Office Web Apps Server Farm for high availability.

After Office Web Apps Server has been successfully installed and your Web farm correctly configured, you must then configure Lync Server to communicate with the new server; this is done by adding the Office Web Apps Server discovery URL to your Lync Server topology. To add Office Web Apps Server to your topology, complete the following steps:

1.  Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In the **Topology Builder** dialog box, select **Download Topology from existing deployment** and then click **OK**.

3.  In the **Save Topology As** dialog box, type a name for your topology document (for example, **PreWebAppsServerTopology**) in the **File name** box and then click **Save**. This topology can later be retrieved and republished if you encounter problems with your new topology.

4.  In Topology Builder, expand **Lync Server 2013**, expand the name of your site, expand **Enterprise Edition Front End pools**, right-click the name of one of your pools, and then click **Edit Properties**.

5.  In the **Edit Properties** dialog box, on the **General** tab, find the heading **Associate Office Web Apps Server** and then click **New** (or select an existing Office Web Apps Server from the drop-down list).

6.  In the **Define New Office Web Apps Server** dialog box, type the fully qualified domain name (FQDN) of your Office Web Apps Server computer in the **Office Web Apps Server FQDN** box; when you do this, your Office Web Apps Server discovery URL should automatically be entered into the **Office Web Apps Server discovery URL** box.
    
    If the Office Web Apps Server is installed on-premises and in the same network zone as Lync Server 2013 then the option **Office Web Apps Server is deployed in an external network (that is, perimeter/Internet)** should not be selected.
    
    If the Office Web Apps Server is deployed outside your internal firewall, then select the option **Office Web Apps Server is deployed in an external network (that is, perimeter/Internet)**.

7.  In the **Define New Office Web Apps Server** dialog box, click **OK**, and then click **OK** in the **Edit Properties** dialog box. The Office Web Apps discovery URL will then be listed as one of the pool's Associations.

You will have to repeat this process for each pool that needs to be associated with your Office Web Apps Server.

After you have added the discovery URL to the topology you must then publish this updated topology. To do that in Topology Builder:

1.  Click **Action** and then click **Publish Topology**.

2.  In the Publish Topology wizard, on the **Publish the Topology** page, click **Next**.

3.  On the **Publishing wizard complete** page, click **Finish**.

4.  Close Topology Builder.

</div>

<span> </span>

</div>

</div>

</div>

