---
title: 'Lync Server 2013: Define a Mediation Server in Topology Builder'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Define a Mediation Server in Topology Builder
ms:assetid: 59d8f5ba-5064-4ea5-b4bf-2b9736e0fedd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398391(v=OCS.15)
ms:contentKeyID: 48184217
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Define a Mediation Server in Topology Builder in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Follow the steps in this topic to use Topology Builder to define a stand-alone Mediation Server or a pool collocated with a Front End pool at a site for which you did not previously deploy Enterprise Voice.

You can define a topology using an account that is a member of the Administrators group.

<div>

## Define Mediation Server collocated to a Front End pool

Follow the steps in this topic to use Topology Builder to define a Mediation Server collocated to a Front End pool in a site where Enterprise Voice has not been previously deployed.

<div>

## To Add a Mediation Server to a Front End pool

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In Topology Builder, in the console tree, expand the name of the site for which you want to define a Front End pool.

3.  In the console tree, right-click the type of Front End pool you want, and then click **New Front End pool..**.

4.  Navigate through the **Define New Front End Pool** wizard until you reach the **Select collocated server roles** page.

5.  In **Select collocated server roles**, check the option **Collocate Mediation Server**.
    
    <div>
    

    > [!NOTE]  
    > <UL>
    > <LI>
    > <P>If the type of Front End pool you selected is the Enterprise Edition, then the Mediation Server component will be installed on all the Front End Servers of that Front End pool.</P>
    > <LI>
    > <P>The <STRONG>Next hop pool</STRONG> used by the Mediation Server will be the Front End pool where the Mediation Server is collocated on.</P>
    > <LI>
    > <P>The <STRONG>Edge pool</STRONG> used by the Mediation Server will be the same Edge pool associated with the Front End pool where the Mediation Server is collocated on.</P></LI></UL>

    
    </div>

6.  Click **Make Default** to use this Front End pool to route calls from Microsoft Office Communications Server 2007 R2 to the PSTN.

7.  Click **Finish** when you are finished associating one or more peers to the Front End pool.
    
    <div>
    

    > [!NOTE]  
    > Before you proceed to the next step in the Enterprise Voice deployment process, make sure that the Mediation Server pool (i.e. Front End pool with the Mediation Server component collocated) is using the FQDNs that you specified.

    
    </div>

8.  Next, follow the procedures in [Publish the topology in Lync Server 2013](lync-server-2013-publish-the-topology.md) in the Deployment Guide documentation to add the Mediation Server to your topology before proceeding to the next step of modifying the listening ports of the Mediation Server if needed. You must publish your topology each time you use Topology Builder to define or modify your topology.

</div>

</div>

<div>

## Define stand-alone Mediation Server

Follow the steps in this topic to use Topology Builder to define a stand-alone Mediation Server or pool at a site where Enterprise Voice has not been previously deployed.

If you already deployed Mediation Servers collocated to Front End pools at this site, you can skip this section and [Install the files for Mediation Server in Lync Server 2013](lync-server-2013-install-the-files-for-mediation-server.md) before proceeding to [Configuring trunks in Lync Server 2013](lync-server-2013-configuring-trunks.md).

<div>


> [!NOTE]  
> This section assumes that you have already setup at least one Front End pool, as described in <A href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Define and configure a Front End pool or Standard Edition server in Lync Server 2013</A> and <A href="lync-server-2013-publish-the-topology.md">Publish the topology in Lync Server 2013</A> in the Deployment Guide documentation.



</div>

<div>

## To Add a Mediation Server

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In Topology Builder, in the console tree, expand the name of the site for which you want to define a Mediation Server.

3.  In the console tree, right-click the **Mediation pools** node, and then click **Mediation Server pool**.

4.  In **Define New Mediation Pool**, type the Mediation Server pool fully qualified domain name (FQDN).

5.  Next, do one of the following:
    
      - If you want to deploy multiple Mediation Servers in the pool to provide high availability, then select **Multiple computer pool**.
        
        <div>
        

        > [!NOTE]  
        > You must deploy DNS load balancing to support Mediation Server pools that have multiple Mediation Servers. For details, see the Using DNS Load Balancing on Mediation Server Pools section of <A href="lync-server-2013-dns-load-balancing.md">DNS load balancing in Lync Server 2013</A> in the Planning documentation.

        
        </div>
    
      - If you want to deploy only one Mediation Server in the pool because you do not require high availability, then select **Single computer pool**. Skip the following step.

6.  If you selected **Multiple computer pool** in the previous step, on the **Define the computers in this pool** item, click **Computer FQDN**, type the FQDN of each server in the pool, and then click **Add**. Repeat this step for all other Mediation Servers that you want to add to the pool. When you have defined all the computers in the pool, click **Next**.

7.  On the **Select the next hop** page, click **Next hop pool**, click the FQDN of the Front End pool that will use this Mediation Server pool, and then click **Next**.

8.  On the **Select an Edge Server** page, do one of the following:
    
      - If you want to provide PSTN connectivity to external users enabled for Enterprise Voice, under **Select Edge Pool used by this Mediation Server**, click the FQDN of the Edge Server pool that will use this Mediation Server pool to provide PSTN connectivity to those external users, and then click **Next**.
    
      - If you do not plan to enable external users for Enterprise Voice, or if you do not want to provide PSTN connectivity to users when they are outside the internal network, click **Next**.

9.  Next, follow the procedures in [Publish the topology in Lync Server 2013](lync-server-2013-publish-the-topology.md) in the Deployment documentation to add the Mediation Server to the topology. You must publish your topology each time you use Topology Builder to build or modify your topology so that the data can be used to install the files for servers that are running Lync Server. Then continue to the next steps to modify the listening ports on the Mediation Server, if necessary.

</div>

</div>

<div>

## Define the Mediation Server Listening Ports

Follow the steps in this topic to use Topology Builder to define the listening ports a Mediation Server or pool will accept incoming connections from a gateway peer.

<div>

## To Modify the Mediation Server Listening Ports

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In Topology Builder, in the console tree, expand the **Mediation pools** node, and right-click the Mediation Server previously created.

3.  By default, the SIP listening ports on the Mediation Server are 5070 for TLS traffic from Lync Server, 5067 for TLS traffic from peers (gateways, PBXes, or SBCs). TCP port is disabled by default. You must enable TCP port if you have gateways that do not support TLS.

4.  Specify the desired TLS or TCP listening port range the Mediation Server will accept incoming connections from PSTN gateways.
    
    <div>
    

    > [!NOTE]  
    > Entering a TCP port range is not required if <STRONG>Enable TCP port</STRONG> is not checked. This setting is optional.

    
    </div>

Next, [Define a gateway in Topology Builder in Lync Server 2013](lync-server-2013-define-a-gateway-in-topology-builder.md) and install the files on each Mediation Server in the pool by following the procedures in [Install the files for Mediation Server in Lync Server 2013](lync-server-2013-install-the-files-for-mediation-server.md).

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

